---
title: 組織向けの Power BI 埋め込み分析アプリケーションにコンテンツを埋め込む
description: Power BI API を使って、アプリケーションにご自身の組織向けの分析情報用のレポート (Power BI またはページ分割された)、ダッシュボード、タイルを統合する (埋め込む) 方法について説明します。 埋め込み分析ソフトウェア、埋め込み分析ツール、または埋め込みビジネス インテリジェンス ツールを使って、ご自身のアプリケーションに Power BI を統合する方法について説明します。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: tutorial
ms.custom: seodec18
ms.date: 02/04/2020
ms.openlocfilehash: 223495b68f160b637f5bcf40b37f1f1a1365fffd
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97098170"
---
# <a name="tutorial-embed-power-bi-content-into-an-application-for-your-organization"></a>チュートリアル:組織向けのアプリケーションに Power BI コンテンツを埋め込む

**Power BI** では、ユーザー所有データを使用して、レポート (Power BI またはページ分割された)、ダッシュボード、またはタイルをアプリケーションに埋め込むことができます。 **ユーザー所有データ** を使用すれば、アプリケーションで埋め込み分析を使用できるように Power BI サービスを拡張できます。 このチュートリアルでは、レポート (Power BI またはページ分割された) をアプリケーションに統合する方法を取り上げます。 Power BI .NET SDK と Power BI JavaScript API を使用して、組織向けのアプリケーションに Power BI を埋め込みます。

![Power BI 埋め込みレポート](media/embed-sample-for-your-organization/embed-sample-for-your-organization-035.png)

このチュートリアルでは、以下のタスクについて説明します。
> [!div class="checklist"]
> * Azure にアプリケーションを登録します。
> * Power BI テナントを使用して、Power BI またはページ分割されたレポートをアプリケーションに埋め込みます。

## <a name="prerequisites"></a>前提条件

始めるにあたり、必要なもの:

* [Power BI Pro アカウント](../../fundamentals/service-self-service-signup-for-power-bi.md)。
* [Microsoft Azure](https://azure.microsoft.com/) サブスクリプション。
* 独自の [Azure Active Directory テナント](create-an-azure-active-directory-tenant.md)のセットアップが必要です。
* ページ分割された SharePoint レポートを埋め込むためには、少なくとも P1 容量が必要です。「[ページ分割されたレポートに必要な Premium 容量のサイズはどれくらいですか。](../../paginated-reports/paginated-reports-faq.md#what-size-premium-capacity-do-i-need-for-paginated-reports)」を参照してください。

**Power BI Pro** にサインアップしていない場合は、[無料の試用版にサインアップ](https://powerbi.microsoft.com/pricing/)してください。

Azure サブスクリプションをお持ちでない場合は、始める前に[無料アカウントを作成](https://azure.microsoft.com/free/?WT.mc_id=A261C142F)してください。

>[!NOTE]
>[Premium Per User (PPU)](../../admin/service-premium-per-user-faq.md) はサポートされています。 ただし、PPU を使用している場合は、組織内の PPU ユーザーのみがソリューションにアクセスできるようになります。

## <a name="set-up-your-embedded-analytics-development-environment"></a>埋め込み分析開発環境を設定する

アプリケーションへのレポート、ダッシュボード、タイルの埋め込みを開始する前に、使用している環境で Power BI での埋め込みが許可されていることを確認する必要があります。

[埋め込みセットアップ ツール](https://app.powerbi.com/embedsetup)を使うと、環境の作成とレポートの埋め込みを段階的に行うのに役立つサンプル アプリケーションをすぐに使い始めたり、ダウンロードしたりできます。 ページ分割されたレポートを埋め込む場合、作成したワークスペースに少なくとも P1 容量を割り当てる必要があります。

手動で環境をセットアップする場合は、以下を続行できます。

### <a name="register-an-application-in-azure-active-directory"></a>Azure Active Directory にアプリケーションを登録する

Azure Active Directory に[アプリケーションを登録する](register-app.md)と、アプリケーションは [Power BI REST API](/rest/api/power-bi/) にアクセスできるようになります。 アプリケーションを登録すると、アプリケーションの ID を設定し、Power BI REST リソースへのアクセス許可を指定することができます。

>[!NOTE]
>独自のアプリケーションでは、 *[認証]* に移動して、 *[リダイレクト URI]* フィールドにリダイレクト アドレスを挿入する必要があります。
リダイレクトの詳細については、「[リダイレクト URI (応答 URL) に関する制約と制限](https://docs.microsoft.com/azure/active-directory/develop/reply-url)」を参照してください。

## <a name="set-up-your-power-bi-environment"></a>Power BI 環境を設定する

### <a name="create-a-workspace"></a>ワークスペースの作成

顧客向けのレポート、ダッシュボード、またはタイルを埋め込む場合は、コンテンツをワークスペース内に配置する必要があります。 設定可能なワークスペースには、[従来のワークスペース](../../collaborate-share/service-create-workspaces.md)と[新しいワークスペース](../../collaborate-share/service-create-the-new-workspaces.md)があります。

### <a name="create-and-publish-your-power-bi-reports"></a>Power BI レポートを作成して発行する

Power BI Desktop を使用して、レポートとデータセットを作成することができます。 その後、そのレポートをワークスペースに発行できます。 レポートを発行するエンド ユーザーには、ワークスペースに発行するための Power BI Pro ライセンスが必要です。

1. GitHub からサンプルの [Demo](https://github.com/Microsoft/powerbi-desktop-samples) をダウンロードします。

    ![デモをダウンロードする](media/embed-sample-for-your-organization/embed-sample-for-your-organization-026-1.png)

2. Power BI Desktop でサンプルの .pbix レポートを開きます。

   ![サンプルの Power BI Desktop レポート](media/embed-sample-for-your-organization/embed-sample-for-your-organization-027.png)

3. ワークスペースに発行します。

   ![Power BI Desktop レポートを発行する](media/embed-sample-for-your-organization/embed-sample-for-your-organization-028.png)

    Power BI サービスを使ってオンラインでレポートを表示できるようになります。

   ![Power BI Desktop レポートを表示する](media/embed-sample-for-your-organization/embed-sample-for-your-organization-029.png)
   
### <a name="create-and-publish-your-paginated-reports"></a>ページ分割されたレポートを作成して発行する

[Power BI レポート ビルダー](../../paginated-reports/paginated-reports-report-builder-power-bi.md#create-reports-in-power-bi-report-builder)を使用して、ページ分割されたレポートを作成できます。 その後、少なくとも P1 容量に割り当てられているワークスペースに[レポートをアップロード](../../paginated-reports/paginated-reports-quickstart-aw.md#upload-the-report-to-the-service)できます。 レポートをアップロードするエンドユーザーがワークスペースに発行するには、Power BI Pro ライセンスを持っている必要があります。
   
## <a name="embed-your-content-by-using-the-sample-application"></a>サンプル アプリケーションを使用してコンテンツを埋め込む

このサンプルは実演目的から意図的に単純に作られています。

次の手順に従い、サンプル アプリケーションを使用してコンテンツの埋め込みを開始します。

1. [Visual Studio](https://www.visualstudio.com/) (バージョン 2013 以降) をダウンロードします。 必ず最新の [NuGet パッケージ](https://www.nuget.org/profiles/powerbi)をダウンロードしてください。

2. 最初に、GitHub から [User Owns Data サンプル](https://github.com/Microsoft/PowerBI-Developer-Samples)をダウンロードします。

    ![User Owns Data アプリケーションのサンプル](media/embed-sample-for-your-organization/embed-sample-for-your-organization-026.png)

3. サンプル アプリケーションで **Cloud.config** ファイルを開きます。

    アプリケーションを実行する目的で入力必須となるフィールドがあります。

    | フィールド |
    |--------------------|
    | **[アプリケーション ID](#application-id)** |
    | **[ワークスペース ID](#workspace-id)** |
    | **[レポート ID](#report-id)** |
    | **[AADAuthorityUrl](#aadauthorityurl)** |

    ![Cloud.config ファイル](media/embed-sample-for-your-organization/embed-sample-for-your-organization-030.png)

### <a name="application-id"></a>アプリケーション ID

**applicationId** 情報には、**Azure** の **アプリケーション ID** を入力します。 **applicationId** は、アクセス許可を要求しているユーザーに対して、アプリケーションが自身を識別するために使用します。

**applicationId** を取得するには、次の手順に従います。

1. [Azure Portal ](https://portal.azure.com)にサインインします。

2. 左側のナビ ペインで、 **[すべてのサービス]** 、 **[アプリの登録]** の順に選択します。

3. **applicationId** を必要とするアプリケーションを選択します。

    ![アプリの選択](media/embed-sample-for-your-organization/embed-sample-for-your-organization-042.png)

4. **アプリケーション ID** が GUID として一覧表示されます。 この **アプリケーション ID** を、アプリケーションの **applicationId** として使用します。

    ![applicationId](media/embed-sample-for-your-organization/embed-sample-for-your-organization-043.png)

### <a name="workspace-id"></a>ワークスペース ID

**workspaceId** 情報には、Power BI のワークスペース (グループ) の GUID を入力します。 この情報は、Power BI サービスにサインインしたときに URL から取得するか、PowerShell を使用して取得できます。

URL <br>

![workspaceId](media/embed-sample-for-your-organization/embed-sample-for-your-organization-040.png)

PowerShell <br>

```powershell
Get-PowerBIworkspace -name "User Owns Embed Test"
```

   ![PowerShell の workspaceId](media/embed-sample-for-your-organization/embed-sample-for-your-organization-040-ps.png)

### <a name="report-id"></a>レポート ID

**reportId** には、Power BI からレポートの GUID を設定します。 この情報は、Power BI サービスにサインインしたときに URL から取得するか、PowerShell を使用して取得できます。

Power BI レポート URL <br>

![PBI reportId](media/embed-sample-for-your-organization/embed-sample-for-your-organization-041.png)


ページ分割されたレポートの URL<br>

![ページ分割されたレポートの ID](media/embed-sample-for-your-organization/paginated-reports-url.png)

PowerShell <br>

```powershell
Get-PowerBIworkspace -name "User Owns Embed Test" | Get-PowerBIReport
```

![PowerShell の reportId](media/embed-sample-for-your-organization/embed-sample-for-your-organization-041-ps.png)

### <a name="aadauthorityurl"></a>AADAuthorityUrl

組織のテナント内に埋め込むか、またはゲスト ユーザーに埋め込むことのできる URL を使用して、**AADAuthorityUrl** 情報を入力します。

組織のテナントに埋め込む場合は、URL - *https://login.microsoftonline.com/common/oauth2/authorize* を使用します。

ゲストに埋め込む場合は、URL - `https://login.microsoftonline.com/report-owner-tenant-id` を使用します。ここで、*report-owner-tenant-id* に置き換えて、レポート所有者のテナント ID を追加します。

### <a name="run-the-application"></a>アプリケーションの実行

1. **Visual Studio** で **[実行]** を選びます。

    ![アプリケーションの実行](media/embed-sample-for-your-organization/embed-sample-for-your-organization-033.png)

2. 次に、 **[Embed Report]** を選びます。 テスト対象に選んだコンテンツ (レポート、ダッシュボード、タイル) に応じて、アプリケーションでそのオプションを選びます。

    ![コンテンツを選択する](media/embed-sample-for-your-organization/embed-sample-for-your-organization-034.png)

3. サンプル アプリケーションでレポートを表示できるようになります。

    ![アプリケーションでレポートを表示する](media/embed-sample-for-your-organization/embed-sample-for-your-organization-035.png)

## <a name="embed-your-content-within-your-application"></a>アプリケーション内にコンテンツを埋め込む

コンテンツを埋め込む手順は [Power BI REST API](/rest/api/power-bi/) で行うことはできますが、この記事で説明するコード例は .NET SDK で作成されています。

Web アプリにレポートを統合するには、Power BI REST API または Power BI C# SDK を使用します。 Azure Active Directory 認証アクセス トークンを使用してレポートを取得することもできます。 その後、同じアクセス トークンを使ってレポートを読み込みます。 Power BI Rest API では、特定の Power BI リソースへのプログラムによるアクセスが提供されます。 詳細については、「[Power BI REST API](/rest/api/power-bi/)」 (Power BI REST API) と [Power BI JavaScript API](https://github.com/Microsoft/PowerBI-JavaScript) に関するページを参照してください。

### <a name="get-an-access-token-from-azure-ad"></a>Azure AD からアクセス トークンを取得する

アプリケーション内では、Power BI REST API の呼び出しを行う前に、Azure AD からアクセス トークンを取得する必要があります。 詳しくは、「[ユーザーを認証し、Power BI アプリ用の Azure AD アクセス トークンを取得する](get-azuread-access-token.md)」をご覧ください。

### <a name="get-a-report"></a>レポートを取得する

Power BI またはページ分割されたレポートを取得するには、[レポートの取得](/rest/api/power-bi/reports/getreports)操作を使用し、Power BI レポートとページ分割されたレポートの一覧を取得します。 レポートの一覧から、レポート ID を取得できます。

### <a name="get-reports-by-using-an-access-token"></a>アクセス トークンを使ってレポートを取得する

[レポートを取得する](/rest/api/power-bi/reports/getreports)操作により、レポートの一覧が返されます。 レポートの一覧から 1 つのレポートを取得できます。

REST API 呼び出しを行うには、*Authorization* ヘッダーを "*ベアラー {アクセス トークン}* " の形式で含める必要があります。

#### <a name="get-reports-with-the-rest-api"></a>REST API でレポートを取得する

以下のコード サンプルでは、REST API を使用してレポートを取得する方法を示します。

> [!Note]
> 埋め込むコンテンツ アイテムを取得するサンプルは、[サンプル アプリケーション](https://github.com/Microsoft/PowerBI-Developer-Samples)の Default.aspx.cs ファイルにあります。 たとえば、レポート、ダッシュボード、タイルです。

```csharp
using Newtonsoft.Json;

//Get a Report. In this sample, you get the first Report.
protected void GetReport(int index)
{
    //Configure Reports request
    System.Net.WebRequest request = System.Net.WebRequest.Create(
        String.Format("{0}/Reports",
        baseUri)) as System.Net.HttpWebRequest;

    request.Method = "GET";
    request.ContentLength = 0;
    request.Headers.Add("Authorization", String.Format("Bearer {0}", accessToken.Value));

    //Get Reports response from request.GetResponse()
    using (var response = request.GetResponse() as System.Net.HttpWebResponse)
    {
        //Get reader from response stream
        using (var reader = new System.IO.StreamReader(response.GetResponseStream()))
        {
            //Deserialize JSON string
            PBIReports Reports = JsonConvert.DeserializeObject<PBIReports>(reader.ReadToEnd());

            //Sample assumes at least one Report.
            //You could write an app that lists all Reports
            if (Reports.value.Length > 0)
            {
                var report = Reports.value[index];

                txtEmbedUrl.Text = report.embedUrl;
                txtReportId.Text = report.id;
                txtReportName.Text = report.name;
            }
        }
    }
}

//Power BI Reports used to deserialize the Get Reports response.
public class PBIReports
{
    public PBIReport[] value { get; set; }
}
public class PBIReport
{
    public string id { get; set; }
    public string reportType { get; set }
    public string name { get; set; }
    public string webUrl { get; set; }
    public string embedUrl { get; set; }
}
```

#### <a name="get-reports-by-using-the-net-sdk"></a>.NET SDK を使ってレポートを取得する

REST API を直接呼び出すのではなく、.NET SDK を使ってレポートの一覧を取得することもできます。 次のコード サンプルでは、レポートを一覧表示する方法を示します。

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

var tokenCredentials = new TokenCredentials(<ACCESS TOKEN>, "Bearer");

// Create a Power BI Client object. It is used to call Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Get the first report all reports in that workspace
    ODataResponseListReport reports = client.Reports.GetReports();

    Report report = reports.Value.FirstOrDefault();

    var embedUrl = report.EmbedUrl;
}
```

### <a name="load-a-report-by-using-javascript"></a>JavaScript を使ってレポートを読み込む

JavaScript を使って、Web ページの div 要素にレポートを読み込むことができます。 以下のコード サンプルでは、指定したワークスペースからレポートを取得する方法を示します。

> [!NOTE]  
> 埋め込むコンテンツ アイテムを読み込むサンプルは、[サンプル アプリケーション](https://github.com/Microsoft/PowerBI-Developer-Samples)の **Default.aspx** ファイルにあります。

```javascript
<!-- Embed Report-->
<div> 
    <asp:Panel ID="PanelEmbed" runat="server" Visible="true">
        <div>
            <div><b class="step">Step 3</b>: Embed a report</div>

            <div>Enter an embed url for a report from Step 2 (starts with https://):</div>
            <input type="text" id="tb_EmbedURL" style="width: 1024px;" />
            <br />
            <input type="button" id="bEmbedReportAction" value="Embed Report" />
        </div>

        <div id="reportContainer"></div>
    </asp:Panel>
</div>
```

#### <a name="sitemaster"></a>Site.master

```javascript
window.onload = function () {
    // client side click to embed a selected report.
    var el = document.getElementById("bEmbedReportAction");
    if (el.addEventListener) {
        el.addEventListener("click", updateEmbedReport, false);
    } else {
        el.attachEvent('onclick', updateEmbedReport);
    }

    // handle server side post backs, optimize for reload scenarios
    // show embedded report if all fields were filled in.
    var accessTokenElement = document.getElementById('MainContent_accessTokenTextbox');
    if (accessTokenElement !== null) {
        var accessToken = accessTokenElement.value;
        if (accessToken !== "")
            updateEmbedReport();
    }
};

// update embed report
function updateEmbedReport() {

    // check if the embed url was selected
    var embedUrl = document.getElementById('tb_EmbedURL').value;
    if (embedUrl === "")
        return;

    // get the access token.
    accessToken = document.getElementById('MainContent_accessTokenTextbox').value;

    // Embed configuration used to describe the what and how to embed.
    // This object is used when calling powerbi.embed.
    // You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
    var config = {
        type: 'report',
        accessToken: accessToken,
        embedUrl: embedUrl
    };

    // Grab the reference to the div HTML element that will host the report.
    var reportContainer = document.getElementById('reportContainer');

    // Embed the report and display it within the div container.
    var report = powerbi.embed(reportContainer, config);

    // report.on will add an event handler which prints to Log window.
    report.on("error", function (event) {
        var logView = document.getElementById('logView');
        logView.innerHTML = logView.innerHTML + "Error<br/>";
        logView.innerHTML = logView.innerHTML + JSON.stringify(event.detail, null, "  ") + "<br/>";
        logView.innerHTML = logView.innerHTML + "---------<br/>";
    }
  );
}
```

## <a name="using-a-power-bi-premium-capacity"></a>Power BI Premium 容量の使用

これでアプリケーションの開発が完了したため、容量を持つワークスペースに戻ります。

### <a name="create-a-capacity"></a>容量を作成する

容量を作成することにより、ワークスペース内のコンテンツに対してリソースを持つことができます。 ページ分割されたレポートの場合は、少なくとも P1 容量を使用してワークスペースをバックアップする必要があります。 [Power BI Premium](../../admin/service-premium-what-is.md) を使用して、容量を作成できます。

次の表は、[Microsoft 365](../../admin/service-admin-premium-purchase.md) で利用可能な Power BI Premium SKU の一覧です。

| 容量ノード | 仮想コアの合計<br/>(バックエンド + フロント エンド) | バックエンドの仮想コア | フロント エンドの仮想コア | DirectQuery/ライブ接続の制限 |
| --- | --- | --- | --- | --- | --- |
| EM1 |1 仮想コア |0.5 仮想コア、3 GB の RAM |0.5 仮想コア |1 秒あたり 3.75 |
| EM2 |2 仮想コア |1 仮想コア、5 GB の RAM |1 仮想コア |1 秒あたり 7.5 |
| EM3 |4 仮想コア |2 仮想コア、10 GB の RAM |2 仮想コア |1 秒あたり 15 |
| P1 |8 仮想コア |4 仮想コア、25 GB の RAM |4 仮想コア |1 秒あたり 30 |
| P2 |16 仮想コア |8 仮想コア、50 GB の RAM |8 仮想コア |1 秒あたり 60 |
| P3 |32 仮想コア |16 仮想コア、100 GB の RAM |16 仮想コア |1 秒あたり 120 |
| P4 |64 仮想コア |32 仮想コア、200 GB の RAM |32 仮想コア |1 秒あたり 240 |
| P5 |128 仮想コア |64 仮想コア、400 GB の RAM |64 仮想コア |1 秒あたり 480 |

> [!NOTE]
> - Microsoft Office アプリで埋め込もうとしている場合は、EM SKU を使用して、無料の Power BI ライセンスでコンテンツにアクセスできます。 しかし、Powerbi.com または Power BI Mobile を使用する場合、無料の Power BI ライセンスでコンテンツにアクセスすることはできません。
> - Powerbi.com または Power BI Mobile を使用して、Microsoft Office アプリで埋め込もうとしている場合は、無料の Power BI ライセンスでコンテンツにアクセスできます。

### <a name="assign-a-workspace-to-a-capacity"></a>容量にワークスペースを割り当てる

容量を作成した後、ワークスペースをその容量に割り当てることができます。 このプロセスを完了するには、次の手順に従います。

1. Power BI サービス内でワークスペースを展開し、コンテンツを埋め込むために使用しているワークスペースの省略記号を選択します。 次に、 **[Edit workspaces]\(ワークスペースの編集\)** を選択します。

    ![ワークスペースを編集する](media/embed-sample-for-your-organization/embed-sample-for-your-organization-036.png)

2. **[詳細]** を展開し、 **[容量]** を有効にします。 作成した容量を選択します。 その後、 **[保存]** を選びます。

    ![容量を割り当てる](media/embed-sample-for-your-organization/embed-sample-for-your-organization-024.png)

3. **[保存]** を選択すると、ワークスペース名の横にひし形が表示されます。

    ![容量に関連付けられたワークスペース](media/embed-sample-for-your-organization/embed-sample-for-your-organization-037.png)

## <a name="admin-settings"></a>管理者設定

グローバル管理者または Power BI サービス管理者は、テナントに対して REST API を使う機能を有効または無効にできます。 Power BI 管理者は、組織全体または個々のセキュリティ グループに対してこれを設定できます。 既定では組織全体に対して有効になります。 [Power BI 管理ポータル](../../admin/service-admin-portal.md)でこれらの変更を行うことができます。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、Power BI の組織アカウントを使用して、アプリケーションに Power BI コンテンツを埋め込む方法を説明しました。 これで、アプリを使用して、アプリケーションへの Power BI コンテンツの埋め込みを試すことができます。 また、顧客のために Power BI コンテンツを埋め込むことができます (ページ分割されたレポートの埋め込みにはまだ対応していません)。

> [!div class="nextstepaction"]
> [アプリからの埋め込み](embed-from-apps.md)

> [!div class="nextstepaction"]
>[顧客向けに埋め込む](embed-sample-for-customers.md)

さらに質問がある場合は、[Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。