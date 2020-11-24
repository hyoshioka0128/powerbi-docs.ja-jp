---
title: Power BI レポートをエクスポートする API
description: 埋め込まれた Power BI レポートをエクスポートする方法について説明します
author: KesemSharabi
ms.author: kesharab
ms.topic: how-to
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 10/01/2020
ms.openlocfilehash: 8ff1fe1657e22b1e0812bddf6a0842b3c32b8822
ms.sourcegitcommit: bd133cb1fcbf4f6f89066165ce065b8df2b47664
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94668582"
---
# <a name="export-power-bi-report-to-file-preview"></a>Power BI レポートをファイルにエクスポートする (プレビュー)

`exportToFile` API を使用すると、REST の呼び出しを使用して Power BI レポートをエクスポートできます。 次のファイル形式がサポートされています。
* **.pptx** (PowerPoint)
* **.pdf**
* **.png**
    * .png にエクスポートすると、複数ページのレポートは .zip ファイルに圧縮されます
    * .zip 内の各ファイルは、レポートのページを表します
    * ページ名は、[ページ取得](/rest/api/power-bi/reports/getpages) API または[グループ内のページ取得](/rest/api/power-bi/reports/getpagesingroup) API の戻り値と同じです

## <a name="usage-examples"></a>使用例

エクスポート機能は、さまざまな方法で使用できます。 いくつかの例を次に示します。

* **印刷に送信ボタン** - アプリケーションで、クリックされたらエクスポート ジョブをトリガーするボタンを作成します。 ジョブでは表示されているレポートを .pdf または .pptx としてエクスポートでき、完了したら、ユーザーはファイルをダウンロードとして受け取ることができます。 ブックマークを使用すると、構成済みのフィルター、スライサー、追加の設定など、レポートを特定の状態でエクスポートできます。 API は非同期であるため、ファイルが使用可能になるまでに時間がかかることがあります。

* **メールの添付ファイル** - .pdf レポートを添付して、設定された間隔で自動的にメールを送信します。 このシナリオは、週単位のレポートを役員に自動的に送信する場合に便利です。

## <a name="using-the-api"></a>API を使用する

API を使用する前に、次の[管理者テナント設定](../../admin/service-admin-portal.md#tenant-settings)が有効になっていることを確認します。
* **[PowerPoint プレゼンテーションまたは PDF ドキュメントとしてレポートをエクスポート]** - 既定で有効になります。
* **[画像ファイルとしてレポートをエクスポート]** - *.png* の場合にのみ必要で、既定では無効になります。

API は非同期です。 [exportToFile](/rest/api/power-bi/reports/exporttofile) API を呼び出すと、エクスポート ジョブがトリガーされます。 エクスポート ジョブをトリガーした後は、[ポーリング](/rest/api/power-bi/reports/getexporttofilestatus)を使用して、ジョブが完了するまで追跡します。

ポーリングの間、API からは完了した作業量を表す数値が返されます。 各エクスポート ジョブの作業量は、レポートに含まれるページ数に基づいて計算されます。 すべてのページに同じ重みが設定されます。 たとえば、10 ページのレポートをエクスポートしていて、ポーリングから 70 が返された場合は、API によりエクスポート ジョブで 10 ページのうち 7 ページが処理されたことを意味します。

エクスポートが完了すると、ポーリング API の呼び出しから、ファイルを取得するための [Power BI URL](/rest/api/power-bi/reports/getfileofexporttofile) が返されます。 その URL は 24 時間有効です。

## <a name="supported-features"></a>サポートされている機能

### <a name="selecting-which-pages-to-print"></a>印刷するページの選択

[ページ取得](/rest/api/power-bi/reports/getpages)または[グループ内のページ取得](/rest/api/power-bi/reports/getpagesingroup)の戻り値に従って、印刷するページを指定します。 エクスポートするページの順序を指定することもできます。

### <a name="bookmarks"></a>ブックマーク

[ブックマーク](../../consumer/end-user-bookmarks.md)を使用すると、適用されているフィルターやレポートの視覚エフェクトの状態など、特定の構成のレポートを保存できます。 [exportToFile](/rest/api/power-bi/reports/exporttofile) API を使用して、次の 2 つの方法でレポートのブックマークをプログラムでエクスポートできます。

* **既存のブックマークをエクスポートする**

    既存の[レポート ブックマーク](../../consumer/end-user-bookmarks.md#report-bookmarks)をエクスポートするには、[Bookmarks JavaScript API](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Bookmarks) を使用して取得できる一意の (大文字と小文字が区別される) 識別子である `name` プロパティを使用します。

* **レポートの状態をエクスポートする**

    レポートの現在の状態をエクスポートするには、`state` プロパティを使用します。 たとえば、ブックマークの `bookmarksManager.capture` メソッドを使用すると、特定のユーザーがレポートに対して行った変更をキャプチャし、`capturedBookmark.state` を使用して現在の状態でそれをエクスポートできます。

>[!NOTE]
>[個人用ブックマーク](../../consumer/end-user-bookmarks.md#personal-bookmarks)と[永続的フィルター](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/)はサポートされていません。

### <a name="authentication"></a>認証

ユーザー (またはマスター ユーザー) または[サービス プリンシパル](embed-service-principal.md)を使用して認証できます。

### <a name="row-level-security-rls"></a>行レベル セキュリティ (RLS)

[行レベル セキュリティ (RLS)](embedded-row-level-security.md) では、特定のユーザーのみが見ることのできるデータが表示されるレポートをエクスポートできます。 たとえば、リージョンのロールで定義されている売上レポートをエクスポートする場合は、特定のリージョンのみが表示されるように、プログラムでレポートをフィルター処理できます。

RLS を使用してエクスポートするには、次のアクセス許可を持っている必要があります。
* レポートが接続されているデータセットに対する書き込み権限と再共有権限
* レポートが v1 ワークスペースに存在する場合は、ワークスペース管理者である必要があります
* レポートが v2 ワークスペースに存在する場合は、ワークスペースのメンバーまたは管理者である必要があります

### <a name="data-protection"></a>データ保護

.pdf と .pptx 形式では、[機密ラベル](../../admin/service-security-sensitivity-label-overview.md)がサポートされています。 機密ラベルが設定されたレポートを .pdf または .pptx にエクスポートすると、エクスポートされたファイルでは、レポートとその機密ラベルが表示されます。

機密ラベルが設定されたレポートは、[サービス プリンシパル](embed-service-principal.md)を使用して .pdf または .pptx にエクスポートすることはできません。

### <a name="localization"></a>ローカライズ

`exportToFile` API を使用すると、目的のローカルを渡すことができます。 ローカライズの設定は、選択したローカルに応じた書式設定の変更など、レポートの表示方法に影響します。

## <a name="concurrent-requests"></a>同時要求数

`exportToFile` では、同時エクスポート ジョブ要求がサポートされます。 次の表では、レポートが存在する SKU に応じて、同時に実行できるジョブの数を示します。 同時要求は、レポートのページ数を表します。 たとえば、A6 SKU では、1 つのエクスポート要求に 20 ページが含まれる場合は同時に処理されます。 これにかかる時間は、1 ページずつ 20 回に分けてエクスポート要求を送信する場合とほぼ同じです。

ジョブが同時要求の数を超えても終了することはありません。 たとえば、A1 SKU で 3 ページをエクスポートした場合、最初のジョブが実行され、後の 2 つは次の 2 つの実行サイクルを待機します。

>[!NOTE]
>`exporToFile` API を使用して Power BI レポートをファイルにエクスポートすることは、[Premium Per User (PPU)](../../admin/service-premium-per-user-faq.md) ではサポートされていません。 

|Azure SKU  |Office SKU  |最大同時実行レポート ページ数  |
|-----------|------------|-----------|
|A1         |EM1         |1          |
|A2         |EM2         |2          |
|A3         |EM3         |3          |
|A4         |P1          |6          |
|A5         |P2          |12         |
|A6         |P3          |24         |

## <a name="limitations"></a>制限事項

* エクスポートするレポートは、Premium または Embedded の容量に存在している必要があります。
* エクスポートするレポートのデータセットは、Premium または Embedded の容量に存在している必要があります。
* パブリック プレビューの場合、1 時間あたりのエクスポートされる Power BI レポートのページ数は、容量ごとに 50 に制限されています。
* エクスポートされたレポートのファイル サイズは 250 MB を超えてはなりません。
* .png にエクスポートする場合、機密ラベルはサポートされません。
* エクスポートされるレポートに含めることができるページ数は 50 です。 レポートに含まれるページがそれより多い場合、API はエラーを返し、エクスポート ジョブは取り消されます。
* [個人用ブックマーク](../../consumer/end-user-bookmarks.md#personal-bookmarks)と[永続的フィルター](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/)はサポートされていません。
* 次に示す Power BI のビジュアルはサポートされていません。 これらのビジュアルを含むレポートをエクスポートすると、これらのビジュアルが含まれるレポートの部分は表示されず、エラー記号が表示されます。
    * 認められていない Power BI ビジュアル
    * R ビジュアル
    * PowerApps
    * Python のビジュアル
    * Visio

## <a name="code-examples"></a>コード例

エクスポート ジョブを作成するときは、3 つのステップに従って行います。

1. [エクスポート要求の送信](#step-1---sending-an-export-request)。
2. [ポーリング](#step-2---polling)。
3. [ファイルの取得](#step-3---getting-the-file)。
4. [ファイル ストリームの使用](#step-4---using-the-file-stream)。

ここでは、各ステップの例を示します。

### <a name="step-1---sending-an-export-request"></a>ステップ 1 - エクスポート要求を送信する

最初のステップでは、エクスポート要求を送信します。 この例では、特定のページに対するエクスポート要求が送信されます。

```csharp
private async Task<string> PostExportRequest(
    Guid reportId,
    Guid groupId,
    FileFormat format,
    IList<string> pageNames = null /* Get the page names from the GetPages REST API */)
{
    var powerBIReportExportConfiguration = new PowerBIReportExportConfiguration
    {
        Settings = new ExportReportSettings
        {
            Locale = "en-us",
        },
        // Note that page names differ from the page display names
        // To get the page names use the GetPages REST API
        Pages = pageNames?.Select(pn => new ExportReportPage(Name = pn)).ToList(),
    };

    var exportRequest = new ExportReportRequest
    {
        Format = format,
        PowerBIReportConfiguration = powerBIReportExportConfiguration,
    };

    // The 'Client' object is an instance of the Power BI .NET SDK
    var export = await Client.Reports.ExportToFileInGroupAsync(groupId, reportId, exportRequest);

    // Save the export ID, you'll need it for polling and getting the exported file
    return export.Id;
}
```

### <a name="step-2---polling"></a>ステップ 2 - ポーリングを行う

エクスポート要求を送信した後、ポーリングを使用して、待機しているエクスポート ファイルの準備ができたことを確認します。

```csharp
private async Task<HttpOperationResponse<Export>> PollExportRequest(
    Guid reportId,
    Guid groupId,
    string exportId /* Get from the PostExportRequest response */,
    int timeOutInMinutes,
    CancellationToken token)
{
    HttpOperationResponse<Export> httpMessage = null;
    Export exportStatus = null;
    DateTime startTime = DateTime.UtcNow;
    const int c_secToMillisec = 1000;
    do
    {
        if (DateTime.UtcNow.Subtract(startTime).TotalMinutes > timeOutInMinutes || token.IsCancellationRequested)
        {
            // Error handling for timeout and cancellations 
            return null;
        }

        // The 'Client' object is an instance of the Power BI .NET SDK
        httpMessage = await Client.Reports.GetExportToFileStatusInGroupWithHttpMessagesAsync(groupId, reportId, exportId);
        exportStatus = httpMessage.Body;

        // You can track the export progress using the PercentComplete that's part of the response
        SomeTextBox.Text = string.Format("{0} (Percent Complete : {1}%)", exportStatus.Status.ToString(), exportStatus.PercentComplete);
        if (exportStatus.Status == ExportState.Running || exportStatus.Status == ExportState.NotStarted)
        {
            // The recommended waiting time between polling requests can be found in the RetryAfter header
            // Note that this header is not always populated
            var retryAfter = httpMessage.Response.Headers.RetryAfter;
            var retryAfterInSec = retryAfter.Delta.Value.Seconds;
            await Task.Delay(retryAfterInSec * c_secToMillisec);
        }
    }
    // While not in a terminal state, keep polling
    while (exportStatus.Status != ExportState.Succeeded && exportStatus.Status != ExportState.Failed);

    return httpMessage;
}
```

### <a name="step-3---getting-the-file"></a>ステップ 3 - ファイルを取得する

ポーリングから URL が返されたら、次の例を使用して受信したファイルを取得します。

```csharp
private async Task<ExportedFile> GetExportedFile(
    Guid reportId,
    Guid groupId,
    Export export /* Get from the PollExportRequest response */)
{
    if (export.Status == ExportState.Succeeded)
    {
        // The 'Client' object is an instance of the Power BI .NET SDK
        var fileStream = await Client.Reports.GetFileOfExportToFileAsync(groupId, reportId, export.Id);
        return new ExportedFile
        {
            FileStream = fileStream,
            FileSuffix = export.ResourceFileExtension,
        };
    }
    return null;
}

public class ExportedFile
{
    public Stream FileStream;
    public string FileSuffix;
}
```

### <a name="step-4---using-the-file-stream"></a>ステップ 4 - ファイル ストリームの使用

ファイル ストリームがある場合は、ご自身のニーズに最も合った方法で処理できます。 たとえば、メールで送信したり、エクスポートされたレポートをダウンロードするために使用したりできます。

### <a name="end-to-end-example"></a>エンド ツー エンドの例

これは、レポートのエクスポートに関するエンド ツー エンドの例です。 この例には次のステージが含まれます。
1. [エクスポート要求の送信](#step-1---sending-an-export-request)。
2. [ポーリング](#step-2---polling)。
3. [ファイルの取得](#step-3---getting-the-file)。

```csharp
private async Task<ExportedFile> ExportPowerBIReport(
    Guid reportId,
    Guid groupId,
    FileFormat format,
    int pollingtimeOutInMinutes,
    CancellationToken token,
    IList<string> pageNames = null  /* Get the page names from the GetPages REST API */)
{
    const int c_maxNumberOfRetries = 3; /* Can be set to any desired number */
    const int c_secToMillisec = 1000;
    try
    {
        Export export = null;
        int retryAttempt = 1;
        do
        {
            var exportId = await PostExportRequest(reportId, groupId, format, pageNames);
            var httpMessage = await PollExportRequest(reportId, groupId, exportId, pollingtimeOutInMinutes, token);
            export = httpMessage.Body;
            if (export == null)
            {
                // Error, failure in exporting the report
                return null;
            }
            if (export.Status == ExportState.Failed)
            {
                // Some failure cases indicate that the system is currently busy. The entire export operation can be retried after a certain delay
                // In such cases the recommended waiting time before retrying the entire export operation can be found in the RetryAfter header
                var retryAfter = httpMessage.Response.Headers.RetryAfter;
                if(retryAfter == null)
                {
                    // Failed state with no RetryAfter header indicates that the export failed permanently
                    return null;
                }

                var retryAfterInSec = retryAfter.Delta.Value.Seconds;
                await Task.Delay(retryAfterInSec * c_secToMillisec);
            }
        }
        while (export.Status != ExportState.Succeeded && retryAttempt++ < c_maxNumberOfRetries);

        if (export.Status != ExportState.Succeeded)
        {
            // Error, failure in exporting the report
            return null;
        }

        var exportedFile = await GetExportedFile(reportId, groupId, export);

        // Now you have the exported file stream ready to be used according to your specific needs
        // For example, saving the file can be done as follows:
        /*
            var pathOnDisk = @"C:\temp\" + export.ReportName + exportedFile.FileSuffix;

            using (var fileStream = File.Create(pathOnDisk))
            {
                exportedFile.FileStream.CopyTo(fileStream);
            }
        */

        return exportedFile;
    }
    catch
    {
        // Error handling
        throw;
    }
}
```

## <a name="next-steps"></a>次のステップ

顧客向けおよび自分の組織向けのコンテンツを埋め込む方法を確認します。

> [!div class="nextstepaction"]
>[ページ分割されたレポートをファイルにエクスポートする](export-paginated-report.md)

> [!div class="nextstepaction"]
>[顧客向けに埋め込む](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[組織向けの埋め込み](embed-sample-for-your-organization.md)
