---
title: 政府機関向けクラウドおよび国内クラウド用のアプリケーションにコンテンツを埋め込む
description: Power BI API を使って、アプリケーションに顧客向けの分析情報用のレポート、ダッシュボード、タイルを統合する (埋め込む) 方法について説明します。 政府機関向けクラウドおよび国内クラウド用の埋め込み分析ソフトウェア、埋め込み分析ツール、または埋め込みビジネス インテリジェンス ツールを使って、ご自身のアプリケーションに Power BI を統合する方法について説明します。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: tutorial
ms.custom: seodec18, devx-track-js
ms.date: 02/05/2019
ms.openlocfilehash: faacbe602a8c80dc036583cca599b24b072df315
ms.sourcegitcommit: 702ababd71c38846303bf49990b51afc73f9ebb8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/28/2020
ms.locfileid: "92795660"
---
# <a name="tutorial-embed-a-power-bi-content-into-your-application-for-national-clouds"></a>チュートリアル:Power BI コンテンツを国内クラウド向けアプリケーションに埋め込む

分析コンテンツをご自身の国内クラウド向けのビジネス プロセス アプリケーション内に埋め込む方法について説明します。 Power BI .NET SDK と Power BI JavaScript API を使って、ご自身の Web アプリケーションにレポート、ダッシュボード、またはタイルを埋め込むことができます。

Power BI では[国内クラウド](/azure/active-directory/develop/authentication-national-cloud)もサポートされています。

各種の国内クラウドを次に示します。

* 米国Government Community Cloud (GCC)

* U. S. Government Community Cloud High (GCC High)

* U. S. Military Contractors (DoDCON)

* U. S. Military (DoD)

* Germany Cloud 向け Power BI

* China Cloud 向け Power BI

![埋め込まれたダッシュボード](media/embed-sample-for-customers/powerbi-embed-dashboard.png)

このチュートリアルを開始するには、 **Power BI** アカウントが必要です。 アカウントを設定していない場合、政府や国の種類に基づき、適切な国内クラウドを選択できます。 [U. S. Government Power BI アカウント](../../admin/service-govus-signup.md)、[Germany Cloud 向け Power BI アカウント](https://powerbi.microsoft.com/power-bi-germany/?ru=https%3A%2F%2Fapp.powerbi.de%2F%3FnoSignUpCheck%3D1)、または [China Cloud 向け Power BI アカウント](https://www.21vbluecloud.com/powerbi/)にサインアップできます。

> [!NOTE]
> 代わりに組織向けのダッシュボードを埋め込む場合は、 「[ダッシュボードを組織のアプリに統合する](embed-sample-for-your-organization.md)」をご覧ください。

ダッシュボードを Web アプリに統合するには、 **Power BI** API、および Azure Active Directory (AD) 承認 **アクセス トークン** を使って、ダッシュボードを取得します。 次に、埋め込んだトークンを使ってダッシュボードを読み込みます。 **Power BI** API では、特定の **Power BI** リソースへのプログラムによるアクセスが提供されます。 詳細については、[Power BI REST API](/rest/api/power-bi/)、[Power BI .NET SDK、[Power BI JavaScript API](https://github.com/Microsoft/PowerBI-JavaScript) に関するページをご覧ください。

## <a name="download-the-sample"></a>サンプルをダウンロードする

この記事では、GitHub の「[App Owns Data sample](https://github.com/Microsoft/PowerBI-Developer-Samples)」(アプリ所有データ サンプル) で使われているコードを示します。 このチュートリアルの手順を試してみるには、サンプルをダウンロードできます。 

![アプリ所有データ サンプル](media/embed-sample-for-customers-national-clouds/embed-sample-for-customers-026.png)

* Government Community Cloud (GCC):

    > [!NOTE]
    > Government Community Cloud (GCC) からの Power BI コンテンツの埋め込みは、Microsoft 365 SKU でのみ行うことができます。 その他の国内クラウドのお客様は、[Microsoft 365 または Azure SKU](embedded-faq.md) を使用できます。

1. Cloud.config ファイルを GCCCloud.config コンテンツで上書きします。

2. Web.config ファイルの applicationId (ネイティブ アプリ applicationId)、workspaceId、user (マスター ユーザー)、password を更新します。

3. 次のように、web.config ファイルに GCC パラメーターを追加します。

```xml
<add key="authorityUrl" value="https://login.microsoftonline.com/common/" />
<add key="resourceUrl" value="https://analysis.usgovcloudapi.net/powerbi/api" />
<add key="apiUrl" value="https://api.powerbigov.us/" />
<add key="embedUrlBase" value="https://app.powerbigov.us" />
```

* Military Contractors (DoDCON):

1. Cloud.config ファイルを TBCloud.config コンテンツで上書きします。

2. Web.config ファイルの applicationId (ネイティブ アプリ applicationId)、workspaceId、user (マスター ユーザー)、password を更新します。

3. 次のように、web.config ファイルに DoDCON パラメーターを追加します。

```xml
<add key="authorityUrl" value="https://login.microsoftonlineS.us/common/" />
<add key="resourceUrl" value="https://high.analysis.usgovcloudapi.net/powerbi/api" />
<add key="apiUrl" value="https://api.high.powerbigov.us/" />
<add key="embedUrlBase" value="https://app.high.powerbigov.us" />
```

* Military (DoD):

1. Cloud.config ファイルを PFCloud.config コンテンツで上書きします。

2. Web.config ファイルの applicationId (ネイティブ アプリ applicationId)、workspaceId、user (マスター ユーザー)、password を更新します。

3. 次のように、web.config ファイルに DoDCON パラメーターを追加します。

```xml
<add key="authorityUrl" value="https://login.microsoftonline.us/common/" />
<add key="resourceUrl" value="https://mil.analysis.usgovcloudapi.net/powerbi/api" />
<add key="apiUrl" value="https://api.mil.powerbigov.us/" />
<add key="embedUrlBase" value="https://app.mil.powerbigov.us" />
```

* Germany Cloud 向け Power BI のパラメーター

1. Cloud.config ファイルを Germany Cloud 向け Power BI コンテンツで上書きします。

2. Web.config ファイルの applicationId (ネイティブ アプリ applicationId)、workspaceId、user (マスター ユーザー)、password を更新します。

3. 次のように、web.config ファイルに Germany Cloud 向け Power BI のパラメーターを追加します。

```xml
<add key="authorityUrl" value="https://login.microsoftonline.de/common/" />
<add key="resourceUrl" value="https://analysis.cloudapi.de/powerbi/api" />
<add key="apiUrl" value="https://api.powerbi.de/" />
<add key="embedUrlBase" value="https://app.powerbi.de" />
```

* China Cloud 向け Power BI のパラメーター

1. Cloud.config ファイルを [China Cloud 向け Power BI](https://github.com/microsoft/PowerBI-Developer-Samples/blob/master/.NET%20Framework/Embed%20for%20your%20organization/CloudConfigs/Power%20BI%20operated%20by%2021Vianet%20in%20China/Cloud.config) コンテンツで上書きします。

2. Web.config ファイルの applicationId (ネイティブ アプリ applicationId)、workspaceId、user (マスター ユーザー)、password を更新します。

3. web.config ファイルに China Cloud 向け Power BI のパラメーターを次のように追加します。

```xml
<add key="authorityUrl" value="https://login.chinacloudapi.cn/common/" />
<add key="resourceUrl" value="https://analysis.chinacloudapi.cn/powerbi/api" />
<add key="apiUrl" value="https://api.powerbi.cn/" />
<add key="embedUrlBase" value="https://app.powerbi.cn" />
```

## <a name="step-1---register-an-app-in-azure-ad"></a>ステップ 1 - Azure AD にアプリを登録する

アプリケーションを Azure AD に登録して、REST API を呼び出します。 詳しくは、「[Azure AD アプリを登録して Power BI コンテンツを埋め込む](register-app.md)」をご覧ください。 国内クラウドにはさまざまな所属団体があるので、アプリケーションを登録するための URL もそれぞれ異なります。

* Government Community Cloud (GCC) - ```https://app.powerbigov.us/apps```

* Military Contractors (DoDCON) - ```https://app.high.powerbigov.us/apps```

* Military (DoD) - ```https://app.mil.powerbigov.us/apps```

* Germany Cloud 向け Power BI - ```https://app.powerbi.de/apps```

* China Cloud 向け Power BI - ```https://app.powerbi.cn/apps```

[顧客向けの埋め込みのサンプル](https://github.com/microsoft/PowerBI-Developer-Samples/tree/master/.NET%20Framework/Embed%20for%20your%20customers/PowerBIEmbedded_AppOwnsData)をダウンロードした場合、サンプルが Azure AD に対して認証を実行できるように、取得する **applicationId** を使います。 サンプルを構成するには、 *web.config* ファイルの **applicationId** を変更します。

## <a name="step-2---get-an-access-token-from-azure-ad"></a>ステップ 2 - Azure AD からアクセス トークンを取得する

アプリケーション内では、Power BI REST API の呼び出しを行う前に、Azure AD から **アクセス トークン** を取得する必要があります。 詳しくは、「[ユーザーを認証し、Power BI アプリ用の Azure AD アクセス トークンを取得する](get-azuread-access-token.md)」をご覧ください。 さまざまな国内クラウドの所属団体があるので、アプリケーションのアクセス トークンを取得するための URL はそれぞれ異なります。

* Government Community Cloud (GCC) - ```https://login.microsoftonline.com```

* Military Contractors (DoDCON) - ```https://login.microsoftonline.us```

* Military (DoD) - ```https://login.microsoftonline.us```

* Germany Cloud 向け Power BI - ```https://login.microsoftonline.de```

* China Cloud 向け Power BI - ```https://login.chinacloudapi.cn```

**Controllers\HomeController.cs** ファイルの各コンテンツ アイテム タスク内で、これらのアクセス トークンの例を確認できます。

## <a name="step-3---get-a-content-item"></a>ステップ 3 - コンテンツ アイテムを取得する

Power BI コンテンツを正しく埋め込むには、いくつかの作業が必要です。 すべての手順は REST API で直接行うことができますが、サンプル アプリケーションとここの例は .NET SDK で行われています。

### <a name="create-the-power-bi-client-with-your-access-token"></a>アクセス トークンを使って Power BI クライアントを作成する

Power BI API と対話できる Power BI クライアント オブジェクトをアクセス トークンで作成します。 AccessToken を *Microsoft.Rest.TokenCredentials* オブジェクトでラップして、Power BI クライアント オブジェクトを作成します。

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.Rest;
using Microsoft.PowerBI.Api.V2;

var tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");

// Create a Power BI Client object. This is used to call the Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Your code to embed items.
}
```

### <a name="get-the-content-item-you-want-to-embed"></a>埋め込むコンテンツ アイテムを取得する

Power BI クライアント オブジェクトを使って、埋め込むアイテムへの参照を取得します。 ダッシュボード、タイル、またはレポートを埋め込むことができます。 指定したワークスペースから最初のダッシュボード、タイル、またはレポートを取得する方法の例を次に示します。

サンプルは、「 [App Owns Data sample](https://github.com/microsoft/PowerBI-Developer-Samples/tree/master/.NET%20Framework/Embed%20for%20your%20customers/PowerBIEmbedded_AppOwnsData)」(アプリ所有データ サンプル) の **Controllers\HomeController.cs** にあります。

#### <a name="reports"></a>レポート

```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// You need to provide the workspaceId where the dashboard resides.
ODataResponseListReport reports = client.Reports.GetReportsInGroupAsync(workspaceId);

// Get the first report in the group.
Report report = reports.Value.FirstOrDefault();
```

#### <a name="dashboards"></a>ダッシュボード

```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// You need to provide the workspaceId where the dashboard resides.
ODataResponseListDashboard dashboards = client.Dashboards.GetDashboardsInGroup(workspaceId);

// Get the first report in the group.
Dashboard dashboard = dashboards.Value.FirstOrDefault();
```

#### <a name="tiles"></a>タイル

```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// To retrieve the tile, you first need to retrieve the dashboard.

// You need to provide the workspaceId where the dashboard resides.
ODataResponseListDashboard dashboards = client.Dashboards.GetDashboardsInGroup(workspaceId);

// Get the first report in the group.
Dashboard dashboard = dashboards.Value.FirstOrDefault();

// Get a list of tiles from a specific dashboard
ODataResponseListTile tiles = client.Dashboards.GetTilesInGroup(workspaceId, dashboard.Id);

// Get the first tile in the group.
Tile tile = tiles.Value.FirstOrDefault();
```

### <a name="create-the-embed-token"></a>埋め込みトークンを作成する

JavaScript API を使用して、埋め込みトークンを生成できます。 埋め込みトークンは、埋め込むアイテムに固有のものです。 Power BI コンテンツを埋め込むときは常に、そのための埋め込みトークンを新しく作成する必要があります。 使用する **accessLevel** など、詳しくは「 [Embed Token](/rest/api/power-bi/embedtoken)」 (埋め込みトークン) をご覧ください。

> [!IMPORTANT]
> 埋め込みトークンは開発テストのためのものです。そのため、Power BI マスター アカウントで生成できる埋め込みトークンの数には限りがあります。 運用環境で埋め込む場合、[容量を購入する](./embedded-faq.md#technical)必要があります。 容量を購入する場合、埋め込みトークンの生成数には上限がありません。

サンプルは、 [組織向けの埋め込みのサンプル](https://github.com/microsoft/PowerBI-Developer-Samples/tree/master/.NET%20Framework/Embed%20for%20your%20customers/PowerBIEmbedded_AppOwnsData)の **Controllers\HomeController.cs** にあります。

**EmbedConfig** および **TileEmbedConfig** のクラスが作成されます。 サンプルは、 **Models\EmbedConfig.cs** および **Models\TileEmbedConfig.cs** にあります。

#### <a name="reports"></a>レポート

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

#### <a name="dashboards"></a>ダッシュボード

```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// Generate Embed Token.
var generateTokenRequestParameters = new GenerateTokenRequest(accessLevel: "view");
EmbedToken tokenResponse = client.Dashboards.GenerateTokenInGroup(workspaceId, dashboard.Id, generateTokenRequestParameters);

// Generate Embed Configuration.
var embedConfig = new EmbedConfig()
{
    EmbedToken = tokenResponse,
    EmbedUrl = dashboard.EmbedUrl,
    Id = dashboard.Id
};
```

#### <a name="tiles"></a>タイル

```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// Generate Embed Token for a tile.
var generateTokenRequestParameters = new GenerateTokenRequest(accessLevel: "view");
EmbedToken tokenResponse = client.Tiles.GenerateTokenInGroup(workspaceId, dashboard.Id, tile.Id, generateTokenRequestParameters);

// Generate Embed Configuration.
var embedConfig = new TileEmbedConfig()
{
    EmbedToken = tokenResponse,
    EmbedUrl = tile.EmbedUrl,
    Id = tile.Id,
    dashboardId = dashboard.Id
};
```

## <a name="step-4---load-an-item-using-javascript"></a>ステップ 4 - JavaScript を使ってアイテムを読み込む

JavaScript を使用して、Web ページの div 要素にダッシュ ボードを読み込むことができます。 このサンプルでは、EmbedConfig/TileEmbedConfig モデルと、ダッシュボード、タイル、またはレポートのビューを使います。 JavaScript API の使用に関する完全なサンプルについては、「[Microsoft Power BI Embedded Sample](https://microsoft.github.io/PowerBI-JavaScript/demo)」(Microsoft Power BI Embedded のサンプル) をご覧ください。

アプリケーションのサンプルは、[組織向けの埋め込みのサンプル](https://github.com/microsoft/PowerBI-Developer-Samples/tree/master/.NET%20Framework/Embed%20for%20your%20customers/PowerBIEmbedded_AppOwnsData)にあります。

### <a name="viewshomeembeddashboardcshtml"></a>Views\Home\EmbedDashboard.cshtml

```csharp
<script src="~/scripts/powerbi.js"></script>
<div id="dashboardContainer"></div>
<script>
    // Read embed application token from Model
    var accessToken = "@Model.EmbedToken.Token";

    // Read embed URL from Model
    var embedUrl = "@Html.Raw(Model.EmbedUrl)";

    // Read dashboard Id from Model
    var embedDashboardId = "@Model.Id";

    // Get models. models contains enums that can be used.
    var models = window['powerbi-client'].models;

    // Embed configuration used to describe the what and how to embed.
    // This object is used when calling powerbi.embed.
    // This also includes settings and options such as filters.
    // You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
    var config = {
        type: 'dashboard',
        tokenType: models.TokenType.Embed,
        accessToken: accessToken,
        embedUrl: embedUrl,
        id: embedDashboardId
    };

    // Get a reference to the embedded dashboard HTML element
    var dashboardContainer = $('#dashboardContainer')[0];

    // Embed the dashboard and display it within the div container.
    var dashboard = powerbi.embed(dashboardContainer, config);
</script>
```

### <a name="viewshomeembedtilecshtml"></a>Views\Home\EmbedTile.cshtml

```csharp
<script src="~/scripts/powerbi.js"></script>
<div id="tileContainer"></div>
<script>
    // Read embed application token from Model
    var accessToken = "@Model.EmbedToken.Token";

    // Read embed URL from Model
    var embedUrl = "@Html.Raw(Model.EmbedUrl)";

    // Read tile Id from Model
    var embedTileId = "@Model.Id";

    // Read dashboard Id from Model
    var embedDashboardId = "@Model.dashboardId";

    // Get models. models contains enums that can be used.
    var models = window['powerbi-client'].models;

    // Embed configuration used to describe the what and how to embed.
    // This object is used when calling powerbi.embed.
    // This also includes settings and options such as filters.
    // You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
    var config = {
        type: 'tile',
        tokenType: models.TokenType.Embed,
        accessToken: accessToken,
        embedUrl: embedUrl,
        id: embedTileId,
        dashboardId: embedDashboardId
    };

    // Get a reference to the embedded tile HTML element
    var tileContainer = $('#tileContainer')[0];

    // Embed the tile and display it within the div container.
    var tile = powerbi.embed(tileContainer, config);
</script>
```

### <a name="viewshomeembedreportcshtml"></a>Views\Home\EmbedReport.cshtml

```csharp
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

    // Embed configuration used to describe the what and how to embed.
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

## <a name="next-steps"></a>次の手順

* GitHub でサンプル アプリケーションを入手して確認できます。 上の例はそのサンプルに基づいています。 詳細については、[組織向けの埋め込みのサンプル](https://github.com/microsoft/PowerBI-Developer-Samples/tree/master/.NET%20Framework/Embed%20for%20your%20customers/PowerBIEmbedded_AppOwnsData)をご覧ください。

* JavaScript API の詳細については、[Power BI JavaScript API](https://github.com/Microsoft/PowerBI-JavaScript) のページを参照してください。

* Germany Cloud 向け Power BI の詳細については、「[ドイツ クラウド顧客向け Power BI のよく寄せられる質問](../../admin/service-govde-faq.md)」を参照してください。

* [Power BI に Power BI ワークスペース コレクション コンテンツを移行する方法](migrate-from-powerbi-embedded.md)

考慮事項と制限事項

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。