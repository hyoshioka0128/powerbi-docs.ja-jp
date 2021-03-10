---
title: 埋め込み BI 分析情報を向上させるための Power BI 埋め込み分析のページ分割されたレポートのエクスポート API
description: ページ分割された埋め込み Power BI レポートをエクスポートする方法について説明します。
author: KesemSharabi
ms.author: kesharab
ms.topic: how-to
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 02/09/2021
ms.openlocfilehash: cbb1466ff0f9fdb0c2a8d86c3214a2f5ff0110c4
ms.sourcegitcommit: 13a150d1aa810f309421bf603fa8581718a4b299
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "101842632"
---
# <a name="export-paginated-report-to-file"></a>ページ分割されたレポートをファイルにエクスポートする

`exportToFile` API を使用すると、REST の呼び出しを使用して、ページ割り付けされた Power BI レポートをエクスポートできます。 次のファイル形式がサポートされています。
* **.pptx** (PowerPoint)
* **.pdf**
* **.xlsx** (Excel)
* **.dox** (Word)
* **.csv**
* **.xml**
* **.mhtml**
* **イメージ**
    * イメージにエクスポートする場合は、`OutputFormat` 形式設定を使用してイメージ形式を設定します。
    * サポートされている OutputFormat 値は、.bmp、.emf、.gif、.jpeg、.png、.tiff (既定値) です。

## <a name="usage-examples"></a>使用例

エクスポート機能は、さまざまな方法で使用できます。 いくつかの例を次に示します。

* **印刷に送信ボタン** - アプリケーションで、クリックされたらエクスポート ジョブをトリガーするボタンを作成します。 このジョブでは、表示されているレポートを .pdf または .pptx としてエクスポートできます。それが完了すると、ユーザーはファイルをダウンロードとして受け取ることができます。 レポート パラメーターと形式設定を使用して、フィルター処理されたデータ、カスタム ページ サイズ、その他の形式固有の設定など、特定の状態でレポートをエクスポートできます。 API は非同期であるため、ファイルが使用可能になるまでに時間がかかることがあります。

* **メールの添付ファイル** - .pdf レポートを添付して、設定された間隔で自動的にメールを送信します。 このシナリオは、週単位のレポートを役員に自動的に送信する場合に便利です。

## <a name="using-the-api"></a>API を使用する

API は非同期です。 [exportToFile](/rest/api/power-bi/reports/exporttofile) API を呼び出すと、エクスポート ジョブがトリガーされます。 エクスポート ジョブをトリガーした後は、[ポーリング](/rest/api/power-bi/reports/getexporttofilestatus)を使用して、ジョブが完了するまで追跡します。

エクスポートが完了すると、ポーリング API の呼び出しから、ファイルを取得するための [Power BI URL](/rest/api/power-bi/reports/getfileofexporttofile) が返されます。 その URL は 24 時間有効です。

## <a name="supported-features"></a>サポートされている機能

### <a name="format-settings"></a>形式の設定

ファイル形式ごとにさまざまな形式設定を指定できます。 サポートされているプロパティと値は、ページ割り付けされたレポートの URL パラメーターの[デバイス情報パラメーター](../../paginated-reports/report-builder-url-parameters.md#report-commands-rdl)と同じです。

ここでは、2 つの例を示します。1 つは、レポートのページ サイズを使用して、レポートの最初の 4 ページを .pptx ファイルにエクスポートする例で、もう 1 つは、レポートの 3 ページ目を .jpeg ファイルにエクスポートする例です。

**最初の 4 ページを .pptx にエクスポートする**

```json
{
      "format": "PPTX",
      "paginatedReportConfiguration":{
            "formatSettings":{
                  "UseReportPageSize": "true",
                  "StartPage": "1",
                  "EndPage": "4"
            }
      }
}
```

**3 ページ目を .jpeg にエクスポートする**

```json
{
      "format": "IMAGE",
      "paginatedReportConfiguration":{
            "formatSettings":{
                  "OutputFormat": "JPEG",
                  "StartPage": "3",
                  "EndPage": "3"
            }
      }
}
```

### <a name="report-parameters"></a>レポート パラメーター

`exportToFile` API を使用すると、プログラムで一連のレポート パラメーターを指定してレポートをエクスポートすることができます。 このためには、[レポート パラメーター](../../paginated-reports/paginated-reports-parameters.md)機能を使用します。

レポート パラメーターの値を設定する例を次に示します。

```json
{
      "format": "PDF",
      "paginatedReportConfiguration":{
            "parameterValues":[
                  {"name": "State", "value": "WA"},
                  {"name": "City", "value": "Seattle"},
                  {"name": "City", "value": "Bellevue"},
                  {"name": "City", "value": "Redmond"}
            ]
      }
}
```

### <a name="authentication"></a>認証

ユーザー (またはマスター ユーザー) または[サービス プリンシパル](embed-service-principal.md)を使用して認証できます。

### <a name="row-level-security-rls"></a>行レベル セキュリティ (RLS)

行レベル セキュリティ (RLS) が定義された Power BI データセットをデータ ソースとして使用する場合、データが特定のユーザーにのみ表示されるレポートをエクスポートできます。 たとえば、リージョンのロールで定義されている売上レポートをエクスポートする場合は、特定のリージョンのみが表示されるように、プログラムでレポートをフィルター処理できます。

RLS を使用してエクスポートするには、レポートでデータ ソースとして使用する Power BI データセットに対する読み取りアクセス許可が必要です。

RLS の有効なユーザー名を指定する例を次に示します。

```json
{
      "format": "PDF",
      "paginatedReportConfiguration":{
            "identities": [
                  {"username": "john@contoso.com"}
            ]
      }
}
```

### <a name="single-sign-on-sql-and-dataverse-sso"></a>シングル サインオンの SQL と Dataverse (SSO)

Power BI には、SSO で OAuth を設定するオプションがあります。 その場合、レポートを表示しているユーザーの資格情報が、データを取得するために使用されます。 要求ヘッダー内のアクセス トークンはデータへのアクセスに使用されません。このトークンは、POST 本文内の有効な ID を使用して渡す必要があります。

アクセス トークンに関して紛らわしい点は、アクセスするリソースに対して正しいアクセス トークンを取得することです。

- Azure SQL の場合、リソースは `https://database.windows.net` です。
- Dataverse の場合、リソースはお使いの環境の `https://` アドレスです。 たとえば、「 `https://contoso.crm.dynamics.com` 」のように指定します。

[AuthenticationContext.AcquireTokenAsync](/dotnet/api/microsoft.identitymodel.clients.activedirectory.authenticationcontext.acquiretokenasync) メソッドを使用して、トークン API にアクセスします。

アクセス トークンで有効なユーザー名を指定する例を次に示します。

```json
{
       "format":"PDF",
       "paginatedReportConfiguration":{
          "formatSettings":{
             "AccessiblePDF":"true",
             "PageHeight":"11in",
             "PageWidth":"8.5in",
             "MarginBottom":"2in"
          },
          "identities":[
             {
                "username":"john@contoso.com",
                "identityBlob": {
                "value": "eyJ0eX....full access token"
         }
        }
     ]
   }
}
```

## <a name="ppu-concurrent-requests"></a>PPU 同時要求数
`exportToFile` API で [Premium Per User (PPU)](../../admin/service-premium-per-user-faq.md) を使用すると、5 分間に 1 つの要求が許可されます。 5 分以内に複数の (1 を超える) 要求が発生すると、"*要求が多すぎる*" (429) エラーが発生します。

## <a name="code-examples"></a>コード例

このコード例で使用されている Power BI API SDK は、[こちら](https://www.nuget.org/packages/Microsoft.PowerBI.Api)からダウンロードできます。

エクスポート ジョブを作成するときは、3 つのステップに従って行います。

1. エクスポート要求の送信。
2. ポーリング。
3. ファイルの取得。

ここでは、各ステップの例を示します。

### <a name="step-1---sending-an-export-request"></a>ステップ 1 - エクスポート要求を送信する

最初のステップでは、エクスポート要求を送信します。 この例では、特定のページ範囲、サイズ、レポート パラメーター値のエクスポート要求を送信します。

```csharp
private async Task<string> PostExportRequest(
    Guid reportId,
    Guid groupId)
{
    // For documentation purposes the export configuration is created in this method
    // Ordinarily, it would be created outside and passed in
    var paginatedReportExportConfiguration = new PaginatedReportExportConfiguration()
    {
        FormatSettings = new Dictionary<string, string>()
        {
            {"PageHeight", "14in"},
            {"PageWidth", "8.5in" },
            {"StartPage", "1"},
            {"EndPage", "4"},
        },
        ParameterValues = new List<ParameterValue>()
        {
            { new ParameterValue() {Name = "State", Value = "WA"} },
            { new ParameterValue() {Name = "City", Value = "Redmond"} },
        },
    };

    var exportRequest = new ExportReportRequest
    {
        Format = FileFormat.PDF,
        PaginatedReportExportConfiguration = paginatedReportExportConfiguration,
    };

    var export = await Client.Reports.ExportToFileInGroupAsync(groupId, reportId, exportRequest);

    // Save the export ID, you'll need it for polling and getting the exported file
    return export.Id;
}
```

### <a name="step-2---polling"></a>ステップ 2 - ポーリングを行う

エクスポート要求を送信した後、ポーリングを使用して、待機しているエクスポート ファイルの準備ができたことを確認します。

```csharp
private async Task<Export> PollExportRequest(
    Guid reportId,
    Guid groupId,
    string exportId /* Get from the ExportToAsync response */,
    int timeOutInMinutes,
    CancellationToken token)
{
    Export exportStatus = null;
    DateTime startTime = DateTime.UtcNow;
    const int secToMillisec = 1000;
    do
    {
        if (DateTime.UtcNow.Subtract(startTime).TotalMinutes > timeOutInMinutes || token.IsCancellationRequested)
        {
            // Error handling for timeout and cancellations
            return null;
        }

        var httpMessage = 
            await Client.Reports.GetExportToFileStatusInGroupWithHttpMessagesAsync(groupId, reportId, exportId);
            
        exportStatus = httpMessage.Body;
        if (exportStatus.Status == ExportState.Running || exportStatus.Status == ExportState.NotStarted)
        {
            // The recommended waiting time between polling requests can be found in the RetryAfter header
            // Note that this header is only populated when the status is either Running or NotStarted
            var retryAfter = httpMessage.Response.Headers.RetryAfter;
            var retryAfterInSec = retryAfter.Delta.Value.Seconds;

            await Task.Delay(retryAfterInSec * secToMillisec);
        }
    }
    // While not in a terminal state, keep polling
    while (exportStatus.Status != ExportState.Succeeded && exportStatus.Status != ExportState.Failed);

    return exportStatus;
}
```

### <a name="step-3---getting-the-file"></a>ステップ 3 - ファイルを取得する

ポーリングから URL が返されたら、次の例を使用して受信したファイルを取得します。

```csharp
private async Task<ExportedFile> GetExportedFile(
    Guid reportId,
    Guid groupId,
    Export export /* Get from the GetExportStatusAsync response */)
{
    if (export.Status == ExportState.Succeeded)
    {
        var httpMessage = 
            await Client.Reports.GetFileOfExportToFileInGroupWithHttpMessagesAsync(groupId, reportId, export.Id);

        return new ExportedFile
        {
            FileStream = httpMessage.Body,
            ReportName = export.ReportName,
            FileExtension = export.ResourceFileExtension,
        };
    }

    return null;
}

public class ExportedFile
{
    public Stream FileStream;
    public string ReportName;
    public string FileExtension;
}
```

### <a name="end-to-end-example"></a>エンド ツー エンドの例

これは、レポートのエクスポートに関するエンド ツー エンドの例です。 この例には次のステージが含まれます。
1. [エクスポート要求の送信](#step-1---sending-an-export-request)。
2. [ポーリング](#step-2---polling)。
3. [ファイルの取得](#step-3---getting-the-file)。

```csharp
private async Task<ExportedFile> ExportPaginatedReport(
    Guid reportId,
    Guid groupId,
    int pollingtimeOutInMinutes,
    CancellationToken token)
{
    try
    {
        var exportId = await PostExportRequest(reportId, groupId);

        var export = await PollExportRequest(reportId, groupId, exportId, pollingtimeOutInMinutes, token);
        if (export == null || export.Status != ExportState.Succeeded)
        {
           // Error, failure in exporting the report
            return null;
        }

        return await GetExportedFile(reportId, groupId, export);
    }
    catch
    {
        // Error handling
        throw;
    }
}
```

## <a name="limitations"></a>制限事項

データ ソースとして Power BI データセットが含まれるページ分割されたレポートのエクスポートは、サービス プリンシパルではサポートされていません。

## <a name="next-steps"></a>次のステップ

顧客向けおよび自分の組織向けのコンテンツを埋め込む方法を確認します。

> [!div class="nextstepaction"]
>[レポートをファイルにエクスポートする](export-to.md)

> [!div class="nextstepaction"]
>[顧客向けに埋め込む](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[組織向けの埋め込み](embed-sample-for-your-organization.md)