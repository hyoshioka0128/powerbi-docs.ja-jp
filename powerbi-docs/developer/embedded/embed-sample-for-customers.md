---
title: 顧客用のアプリケーションにコンテンツを埋め込む
description: Power BI API を使って、アプリケーションに顧客向けの分析情報用のレポート、ダッシュボード、タイルを統合する (埋め込む) 方法について説明します。 埋め込み分析ソフトウェア、埋め込み分析ツール、または埋め込みビジネス インテリジェンス ツールを使って、ご自身のアプリケーションに Power BI を統合する方法について説明します。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.topic: tutorial
ms.service: powerbi
ms.subservice: powerbi-developer
ms.custom: seodec18
ms.date: 06/02/2020
ms.openlocfilehash: 9af0edbe63841f6fb0e0de2e628784c89a5e44f1
ms.sourcegitcommit: 02484b2d7a352e96213353702d60c21e8c07c6c0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/13/2020
ms.locfileid: "91983369"
---
# <a name="tutorial-embed-power-bi-content-into-an-application-for-your-customers"></a>チュートリアル:顧客向けのアプリケーションに Power BI コンテンツを埋め込む

**Azure の Power BI Embedded** または **Office での Power BI の埋め込み**を使用すると、アプリ所有データを使用して、レポート、ダッシュボード、またはタイルをアプリケーション内に埋め込むことができます。 **アプリ所有データ**がある場合、Power BI を埋め込み分析プラットフォームとして使用するアプリケーションが含まれます。 **ISV** または**開発者**は、完全に統合された対話型のアプリケーションにレポート、ダッシュボード、またはタイルを表示する Power BI コンテンツを作成できます。ユーザーに Power BI ライセンスは必要ありません。 このチュートリアルでは、Power BI .NET SDK と Power BI JavaScript API を使用して、アプリケーションにレポートを統合する方法を説明します。

![Power BI 埋め込みレポート](media/embed-sample-for-customers/embed-sample-for-customers-035.png)

このチュートリアルで学習する内容は次のとおりです。
> [!div class="checklist"]
> * Azure にアプリケーションを登録します。
> * Power BI レポートをアプリケーションに埋め込みます。

## <a name="prerequisites"></a>前提条件

始めるにあたり、必要なもの:

* [Power BI Pro アカウント](../../fundamentals/service-self-service-signup-for-power-bi.md) (Power BI Pro アカウントにサインインするためのユーザー名とパスワードとなるマスター アカウント) または[サービス プリンシパル (アプリ専用トークン)](embed-service-principal.md)。
* 独自の [Azure Active Directory テナント](create-an-azure-active-directory-tenant.md)のセットアップが必要です。

**Power BI Pro** にサインアップしていない場合は、[無料の試用版にサインアップ](https://powerbi.microsoft.com/pricing/)してください。

## <a name="set-up-your-embedded-analytics-development-environment"></a>埋め込み分析開発環境を設定する

アプリケーションへのレポート、ダッシュボード、タイルの埋め込みを開始する前に、使用している環境で Power BI での埋め込みが許可されていることを確認する必要があります。

[埋め込みセットアップ ツール](https://aka.ms/embedsetup/AppOwnsData)を使うと、環境の作成とレポートの埋め込みを段階的に行うのに役立つサンプル アプリケーションをすぐに使い始めたり、ダウンロードしたりできます。

ただし、手動で環境をセットアップする場合は、以下を続行できます。

### <a name="register-an-application-in-azure-active-directory-azure-ad"></a>Azure Active Directory (Azure AD) にアプリケーションを登録する

Azure Active Directory に[アプリケーションを登録する](register-app.md)と、アプリケーションは [Power BI REST API](/rest/api/power-bi/) にアクセスできるようになります。 アプリケーションを登録すると、アプリケーションの ID を設定し、[Power BI REST リソースへのアクセス許可](/azure/active-directory/develop/v2-permissions-and-consent)を指定することができます。 マスター アカウントを使うか、[サービス プリンシパル](embed-service-principal.md)を使うかによってアプリケーションの登録方法が決まります。

選択した方法によって、Azure に登録するアプリケーションの種類が変わります。

マスター アカウントを使用する場合、**ネイティブ** アプリの登録に進みます。 対話型ではないログインとなるため、ネイティブ アプリを使用することになります。

一方、サービス プリンシパルを使用する場合、**サーバー側 Web アプリケーション** アプリの登録に進む必要があります。 アプリケーション シークレットを作成するには、サーバー側 Web アプリケーションを登録します。

## <a name="set-up-your-power-bi-environment"></a>Power BI 環境を設定する

### <a name="create-a-workspace"></a>ワークスペースの作成

顧客向けのレポート、ダッシュボード、またはタイルを埋め込む場合は、コンテンツをワークスペース内に配置する必要があります。 設定可能なワークスペースには、[従来のワークスペース](../../collaborate-share/service-create-workspaces.md)と[新しいワークスペース](../../collaborate-share/service-create-the-new-workspaces.md)があります。 *マスター* アカウントを使用する場合、いずれのワークスペースを使用してもかまいません。 一方、" *[サービス プリンシパル](embed-service-principal.md)* " を使用してアプリケーションにサインインする場合、新しいワークスペースを使用する必要があります。 いずれの場合でも、"*マスター*" アカウントも "*サービス プリンシパル*" もアプリケーションに関連するワークスペースの管理者でなければなりません。

### <a name="create-and-publish-your-reports"></a>レポートを作成して発行する

Power BI Desktop を使用してレポートとデータセットを作成し、ワークスペースにこれらのレポートを発行できます。 この作業を実行するには 2 とおりの方法があります。エンド ユーザーは、マスター アカウント (Power BI Pro ライセンス) で従来のワークスペースにレポートを発行できます。 サービス プリンシパルを使用する場合、[Power BI REST API](/rest/api/power-bi/imports/postimportingroup) を使用し、新しいワークスペースにレポートを発行できます。

以下の手順で PBIX レポートを Power BI ワークスペースに発行できます。

1. GitHub からサンプルの [Blog Demo](https://github.com/Microsoft/powerbi-desktop-samples) をダウンロードします。

    ![レポートのサンプル](media/embed-sample-for-customers/embed-sample-for-customers-026-1.png)

2. **Power BI Desktop** でサンプルの PBIX レポートを開きます。

   ![PBI デスクトップ レポート](media/embed-sample-for-customers/embed-sample-for-customers-027.png)

3. **ワークスペース**に発行します。 このプロセスは、マスター アカウント (Power Pro ライセンス) を使用する場合とサービス プリンシパルを使用する場合で異なります。 マスター アカウントを使用する場合、Power BI Desktop からレポートを発行できます。  サービス プリンシパルを使用する場合、Power BI REST API を使用する必要があります。

## <a name="embed-content-using-the-sample-application"></a>サンプル アプリケーションを使用してコンテンツを埋め込む

このサンプルは実演目的から意図的に単純に作られています。 アプリケーション シークレットやマスター アカウント資格情報の保護は、お客様や開発者の責任となります。

次の手順に従い、サンプル アプリケーションを使用してコンテンツの埋め込みを開始します。

1. [Visual Studio](https://www.visualstudio.com/) (バージョン 2013 以降) をダウンロードします。 必ず最新の [NuGet パッケージ](https://www.nuget.org/profiles/powerbi)をダウンロードしてください。

2. 最初に、GitHub から [App Owns Data サンプル](https://github.com/Microsoft/PowerBI-Developer-Samples)をダウンロードします。

    ![App Owns Data アプリケーションのサンプル](media/embed-sample-for-customers/embed-sample-for-customers-026.png)

3. サンプル アプリケーションで **Web.config** ファイルを開きます。 アプリケーションを実行する目的で入力必須となるフィールドがあります。 **AuthenticationType** には **MasterUser** か **ServicePrincipal** を選択できます。 選択した認証方法によって入力するフィールドが異なります。

    > [!Note]
    > このサンプルの既定の **AuthenticationType** は MasterUser です。

    <center>

    | **MasterUser** <br> (Power BI Pro ライセンス) | **ServicePrincipal** <br> (アプリ専用トークン)|
    |---------------|-------------------|
    | [applicationId](#application-id) | [applicationId](#application-id) |
    | [workspaceId](#workspace-id) | [workspaceId](#workspace-id) |
    | [reportId](#report-id) | [reportId](#report-id) |
    | [pbiUsername](#power-bi-username-and-password) |  |
    | [pbiPassword](#power-bi-username-and-password) |  |
    |  | [applicationsecret](#application-secret) |
    |  | [tenant](#tenant) |

   </center>

    ![Web Config ファイル](media/embed-sample-for-customers/embed-sample-for-customers-030.png)

### <a name="application-id"></a>アプリケーション ID

この属性は AuthenticationTypes (マスター アカウントと[サービス プリンシパル](embed-service-principal.md)) の両方で必要です。

**applicationId** 情報には、**Azure** の**アプリケーション ID** を入力します。 **applicationId** は、アクセス許可を要求しているユーザーに対して、アプリケーションが自身を識別するために使用します。

**applicationId** を取得するには、次の手順に従います。

1. [Azure Portal ](https://portal.azure.com)にサインインします。

2. 左側のナビ ペインで、 **[すべてのサービス]** 、 **[アプリの登録]** の順に選択します。

    ![アプリの登録の検索](media/embed-sample-for-customers/embed-sample-for-customers-003.png)

3. **applicationId** を必要とするアプリケーションを選択します。

    ![アプリの選択](media/embed-sample-for-customers/embed-sample-for-customers-006.png)

4. **アプリケーション ID** が GUID として一覧表示されます。 この**アプリケーション ID** を、アプリケーションの **applicationId** として使用します。

    ![applicationId](media/embed-sample-for-customers/embed-sample-for-customers-007.png)

### <a name="workspace-id"></a>ワークスペース ID

この属性は AuthenticationTypes (マスター アカウントと[サービス プリンシパル](embed-service-principal.md)) の両方で必要です。

**workspaceId** 情報には、Power BI のワークスペース (グループ) の GUID を入力します。 この情報は、Power BI サービスにサインインしたときに URL から取得するか、PowerShell を使用して取得できます。

URL <br>

![workspaceId](media/embed-sample-for-customers/embed-sample-for-customers-031.png)

PowerShell <br>

```powershell
Get-PowerBIworkspace -name "App Owns Embed Test"
```

   ![PowerShell の workspaceId](media/embed-sample-for-customers/embed-sample-for-customers-031-ps.png)

### <a name="report-id"></a>レポート ID

この属性は AuthenticationTypes (マスター アカウントと[サービス プリンシパル](embed-service-principal.md)) の両方で必要です。

**reportId** には、Power BI からレポートの GUID を設定します。 この情報は、Power BI サービスにサインインしたときに URL から取得するか、PowerShell を使用して取得できます。

URL<br>

![reportId](media/embed-sample-for-customers/embed-sample-for-customers-032.png)

PowerShell <br>

```powershell
Get-PowerBIworkspace -name "App Owns Embed Test" | Get-PowerBIReport
```

![PowerShell の reportId](media/embed-sample-for-customers/embed-sample-for-customers-032-ps.png)

### <a name="power-bi-username-and-password"></a>Power BI のユーザー名とパスワード

これらの属性は、AuthenticationType がマスター アカウントの場合にのみ必要です。

[サービス プリンシパル](embed-service-principal.md)を使用して認証する場合、ユーザー名やパスワードを入力する必要はありません。

* **pbiUsername** には、Power BI マスター アカウントを設定します。
* **pbiPassword** には、Power BI マスター アカウントのパスワードを設定します。

### <a name="application-secret"></a>アプリケーション シークレット

この属性は、AuthenticationType が[サービス プリンシパル](embed-service-principal.md)の場合にのみ必要です。

**ApplicationSecret** は、**Azure** の **[アプリの登録]** セクションの **[キー]** セクションから設定します。  この属性は[サービス プリンシパル](embed-service-principal.md)の使用時に動作します。

**ApplicationSecret** を取得するには、次の手順に従います。

1. [Azure portal](https://portal.azure.com) にサインインします。

2. 左側のナビ ペインで、 **[すべてのサービス]** 、 **[アプリの登録]** の順に選択します。

    ![アプリの登録の検索](media/embed-sample-for-customers/embed-sample-for-customers-003.png)

3. **ApplicationSecret** を使用する必要があるアプリケーションを選択します。

    ![アプリを選択する](media/embed-sample-for-customers/embed-sample-for-customers-0038.png)

4. **[管理]** で **[証明書とシークレット]** を選択します。

5. **[新しいクライアント シークレット]** を選択します。

6. **[説明]** ボックスに名前を入力し、期間を選択します。 次に、 **[保存]** を選択して、アプリケーションの**値**を取得します。 キーの値を保存した後で **[キー]** ウィンドウを閉じると、値フィールドは非表示としてのみ表示されます。 その時点では、キー値を取得することはできません。 キー値をなくした場合は、Azure portal で新しいものを作成します。

    ![キー値](media/embed-sample-for-customers/embed-sample-for-customers-042.png)

### <a name="tenant"></a>テナント

この属性は、AuthenticationType が[サービス プリンシパル](embed-service-principal.md)の場合にのみ必要です。

**テナント**情報には Azure テナント ID を入力します。 この情報は Power BI サービスにサインインしたときに [Azure AD 管理センター](/onedrive/find-your-office-365-tenant-id)から取得するか、PowerShell を使用して取得できます。

### <a name="run-the-application"></a>アプリケーションの実行

1. **Visual Studio** で **[実行]** を選びます。

    ![アプリケーションの実行](media/embed-sample-for-customers/embed-sample-for-customers-033.png)

2. 次に、 **[Embed Report]** を選びます。 テスト対象に選んだコンテンツ (レポート、ダッシュボード、タイル) に応じて、アプリケーションでそのオプションを選びます。

    ![コンテンツの選択](media/embed-sample-for-customers/embed-sample-for-customers-034.png)

3. サンプル アプリケーションでレポートを表示できるようになります。

    ![アプリケーションの表示](media/embed-sample-for-customers/embed-sample-for-customers-035.png)

## <a name="embed-content-within-your-application"></a>自分のアプリケーション内にコンテンツを埋め込む

コンテンツを埋め込む手順は [Power BI REST API](/rest/api/power-bi/) で行いますが、この記事で説明するコード例は **.NET SDK** で作成されています。

アプリケーション内で顧客向けの埋め込みを行うには、**Azure AD** からマスター アカウントまたは[サービス プリンシパル](embed-service-principal.md)の**アクセス トークン**を取得する必要があります。 [Power BI REST API](/rest/api/power-bi/) への呼び出しを行う前に、Power BI アプリケーションのための [Azure AD アクセス トークン](get-azuread-access-token.md#access-token-for-non-power-bi-users-app-owns-data)を取得する必要があります。

**アクセス トークン**を使用して Power BI Client を作成するには、[Power BI REST API](/rest/api/power-bi/) とやりとりするための Power BI クライアント オブジェクトを作成する必要があります。 **AccessToken** を ***Microsoft.Rest.TokenCredentials*** オブジェクトでラップして、Power BI クライアント オブジェクトを作成します。

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.Rest;
using Microsoft.PowerBI.Api.V2;

var tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");

// Create a Power BI Client object. it's used to call Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Your code to embed items.
}
```

### <a name="get-the-content-item-you-want-to-embed"></a>埋め込むコンテンツ アイテムを取得する

Power BI クライアント オブジェクトを使って、埋め込むアイテムへの参照を取得できます。

指定したワークスペースから最初のレポートを取得する方法のコード例を次に示します。

*コンテンツ アイテムとしてレポート、ダッシュボード、タイルのいずれを埋め込む場合でも、それらを取得するサンプルは[サンプル アプリケーション](https://github.com/Microsoft/PowerBI-Developer-Samples)の Services\EmbedService.cs ファイル内にあります。*

```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// You need to provide the workspaceId where the dashboard resides.
ODataResponseListReport reports = await client.Reports.GetReportsInGroupAsync(workspaceId);

// Get the first report in the group.
Report report = reports.Value.FirstOrDefault();
```

### <a name="create-the-embed-token"></a>埋め込みトークンを作成する
JavaScript API から使うことができる埋め込みトークンを生成します。 API には 2 種類あります。1 つ目のグループには、それぞれが特定の項目の埋め込みトークンを生成する 5 つの API が含まれます。 2 番目のグループには、複数の項目を埋め込むために使用できるトークンを生成する API が 1 つ含まれます。

**特定の項目の埋め込みトークンを生成するための API**

これらの API で作成される埋め込みトークンは、埋め込む項目に固有のものです。 これらの API を使用して Power BI 項目 (レポート、ダッシュボード、タイルなど) を埋め込むときは常に、その項目用に新しい埋め込みトークンを作成する必要があります。
* [Dashboards GenerateTokenInGroup](/rest/api/power-bi/embedtoken/dashboards_generatetokeningroup)
* [Datasets GenerateTokenInGroup](/rest/api/power-bi/embedtoken/datasets_generatetokeningroup)
* [Reports GenerateTokenForCreateInGroup](/rest/api/power-bi/embedtoken/reports_generatetokenforcreateingroup)
* [Reports GenerateTokenInGroup](/rest/api/power-bi/embedtoken/reports_generatetokeningroup)
* [Tiles GenerateTokenInGroup](/rest/api/power-bi/embedtoken/tiles_generatetokeningroup)

レポート、ダッシュボード、またはタイル用の埋め込みトークンを作成するサンプルは、[サンプル アプリケーション](https://github.com/Microsoft/PowerBI-Developer-Samples)の次のファイルから入手できます。
* Services\EmbedService.cs
* Models\EmbedConfig.cs
* Models\TileEmbedConfig.cs

reports GenerateTokenInGroup 埋め込みトークン API を使用するためのコード例を次に示します。
```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// Generate Embed Token.
var generateTokenRequestParameters = new GenerateTokenRequest(accessLevel: "view");
EmbedToken tokenResponse = client.Reports.GenerateTokenInGroup(workspaceId, report.Id, generateTokenRequestParameters);

// Generate Embed Configuration.
var embedConfig = new EmbedConfig()
{
    EmbedToken = tokenResponse,
    EmbedUrl = report.EmbedUrl,
    Id = report.Id
};
```

**複数の項目の埋め込みトークンを生成するための API**<a id="multiEmbedToken"></a>

[Generate Token](/rest/api/power-bi/embedtoken/generatetoken) 埋め込み API は、複数の項目を埋め込むために使用できるトークンを生成します。

レポートを埋め込む際にデータセットを動的に選択するためにも使用できます。 この API の使用方法の詳細については、[動的バインド](embed-dynamic-binding.md)に関するページを参照してください。


この API の使用例を次に示します。
 
```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

var reports = new List<GenerateTokenRequestV2Report>()
{ 
    new GenerateTokenRequestV2Report()
    {
        AllowEdit = false,
        Id = report1.Id
    },
    new GenerateTokenRequestV2Report()
    {
        AllowEdit = true,
        Id = report2.Id
    }
};

var datasets= new List<GenerateTokenRequestV2Dataset>()
{
    new GenerateTokenRequestV2Dataset(dataset1.Id),
    new GenerateTokenRequestV2Dataset(dataset2.Id),
    new GenerateTokenRequestV2Dataset(dataset3.Id),
};

var targetWorkspaces = new List<GenerateTokenRequestV2TargetWorkspace>()
{
    new GenerateTokenRequestV2TargetWorkspace(workspace1.Id),
    new GenerateTokenRequestV2TargetWorkspace(workspace2.Id),
};

var request = new GenerateTokenRequestV2()
{
    Datasets = datasetsRequestDetails ?? null,
    Reports = reportsRequestDetails,
    TargetWorkspaces = targetWSRequestdetials ?? null,
};

var token = client.GetClient().EmbedToken.GenerateToken(request);
```

### <a name="load-an-item-using-javascript"></a>JavaScript を使ってアイテムを読み込む

JavaScript を使って、Web ページの div 要素にレポートを読み込むことができます。

JavaScript API を使用する完全なサンプルの場合、[Playground ツール](https://microsoft.github.io/PowerBI-JavaScript/demo)を使用できます。 プレイグラウンド ツールを使うと、さまざまな種類の Power BI Embedded のサンプルを簡単に試すことができます。 JavaScript API について詳しくは、[PowerBI-JavaScript wiki](https://github.com/Microsoft/powerbi-javascript/wiki) のページも参照してください。

**EmbedConfig** モデルと **TileEmbedConfig** モデルをレポートのビューと一緒に使用するサンプルを次に示します。

*レポート、ダッシュボード、またはタイルのビューを追加するサンプルは、[サンプル アプリケーション](#embed-content-using-the-sample-application)内の Views\Home\EmbedReport.cshtml, Views\Home\EmbedDashboard.cshtml ファイルまたは Views\Home\Embedtile.cshtml ファイルにあります。*

```javascript
<script src="~/scripts/powerbi.js"></script>
<div id="reportContainer"></div>
<script>
    // Read embed application token from Model
    var accessToken = "@Model.EmbedToken.Token";

    // Read embed URL from Model
    var embedUrl = "@Html.Raw(Model.EmbedUrl)";

    // Read report Id from Model
    var embedReportId = "@Model.Id";

    // Get models. models contains enums that can be used.
    var models = window['powerbi-client'].models;

    // Embed configuration used to describe what and how to embed.
    // This object is used when calling powerbi.embed.
    // This also includes settings and options such as filters.
    // You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
    var config = {
        type: 'report',
        tokenType: models.TokenType.Embed,
        accessToken: accessToken,
        embedUrl: embedUrl,
        id: embedReportId,
        permissions: models.Permissions.All,
        settings: {
            filterPaneEnabled: true,
            navContentPaneEnabled: true
        }
    };

    // Get a reference to the embedded report HTML element
    var reportContainer = $('#reportContainer')[0];

    // Embed the report and display it within the div container.
    var report = powerbi.embed(reportContainer, config);
</script>
```

## <a name="move-to-production"></a>運用開始

これでアプリケーションの開発が完了したため、容量を持つワークスペースに戻ります。

> [!Important]
> 運用を開始するには容量が必要です。 すべてのワークスペース (レポートまたはダッシュボードが含まれるワークスペースとデータセットが含まれるワークスペース) が容量に割り当てられている必要があります。

### <a name="create-a-capacity"></a>容量を作成する

容量を作成することで、お客様用のリソースを所有することができます。 選択できる容量には、次の 2 種類があります。
* **Power BI Premium** - 2 つの SKU ファミリ (*EM* および *P*) で利用可能なテナントレベルの Office 365 サブスクリプションです。Power BI コンテンツを埋め込む場合、このソリューションは "*Power BI 埋め込み*" と呼ばれます。 このサブスクリプションの詳細については、「[Power BI Premium とは](../../admin/service-premium-what-is.md)」を参照してください。
* **Azure Power BI Embedded** - [Microsoft Azure portal](https://portal.azure.com) で容量を購入できます。 このサブスクリプションは、*A* SKU を使用します。 Power BI Embedded 容量の作成方法の詳細については、「[Create Power BI Embedded capacity in the Azure portal](azure-pbie-create-capacity.md)」 (Azure Portal で Power BI Embedded 容量を作成する) をご覧ください。
> [!NOTE]
> A SKU の場合、無料 Power BI ライセンスでは Power BI コンテンツにアクセスできません。

次の表は、各 SKU のリソースと制限を示しています。 ニーズに最適な容量を判断するには、[シナリオに応じてどの SKU を購入すればよいか](./embedded-faq.md#which-solution-should-i-choose)をまとめた表を参照してください。

| 容量ノード | 合計 v コア数 | バックエンド v コア数 | RAM (GB) | フロントエンド v コア数 | DirectQuery/ライブ接続 (秒あたり) | モデル更新並列処理 |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0.5 | 2.5 | 0.5 | 3.75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7.5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| | | | | | | |

### <a name="development-testing"></a>開発テスト

開発テストでは、Pro ライセンスで埋め込み試用版トークンを使用できます。 運用環境に埋め込むには、容量を使用します。

Power BI サービス プリンシパルまたはマスター アカウントで生成できる埋め込み試用版トークンの数は制限されています。 [Available Features](/rest/api/power-bi/availablefeatures/getavailablefeatures) API を使用して、現在の埋め込みの使用率を確認します。 使用量は、サービス プリンシパルまたはマスター アカウントごとに表示されます。

テスト中に埋め込みトークンが不足した場合は、Power BI Embedded または Premium の[容量](embedded-capacity.md)を購入する必要があります。 容量で生成できる埋め込みトークンの数に制限はありません。


### <a name="assign-a-workspace-to-a-capacity"></a>容量にワークスペースを割り当てる

容量を作成した後、ワークスペースをその容量に割り当てることができます。

埋め込みコンテンツ (データセット、レポート、ダッシュボードを含む) に関連する Power BI リソースを含むすべてのワークスペースは、容量に割り当てられている必要があります。 たとえば、埋め込みレポートとそれにバインドされているデータセットが異なるワークスペースに存在する場合、両方のワークスペースを容量に割り当てる必要があります。

[サービス プリンシパル](embed-service-principal.md)を使用して容量をワークスペースに割り当てるには、[Power BI REST API](/rest/api/power-bi/capacities/groups_assigntocapacity) を使用します。 Power BI REST API の使用時は必ず[サービス プリンシパル オブジェクト ID](embed-service-principal.md) を使用してください。

以下の手順に従い、**マスター アカウント**を使用してワークスペースに容量を割り当てます。

1. **Power BI サービス**内でワークスペースを展開し、コンテンツを埋め込むために使用しているワークスペースの省略記号ボタンを選択します。 次に、 **[Edit workspaces]\(ワークスペースの編集\)** を選択します。

    ![ワークスペースの編集](media/embed-sample-for-customers/embed-sample-for-customers-036.png)

2. **[詳細]** を展開し、 **[容量]** を有効にして、作成した容量を選択します。 その後、 **[保存]** を選びます。

    ![容量を割り当てる](media/embed-sample-for-customers/embed-sample-for-customers-024.png)

3. **[保存]** を選択すると、ワークスペース名の横に**ひし形**が表示されます。

    ![容量に関連付けられたワークスペース](media/embed-sample-for-customers/embed-sample-for-customers-037.png)

## <a name="next-steps"></a>次の手順

このチュートリアルでは、顧客向けアプリケーションに Power BI コンテンツを埋め込む方法を説明しました。 組織向けの Power BI コンテンツの埋め込みを試すこともできます。

> [!div class="nextstepaction"]
>[組織向けの埋め込み](embed-sample-for-your-organization.md)

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。