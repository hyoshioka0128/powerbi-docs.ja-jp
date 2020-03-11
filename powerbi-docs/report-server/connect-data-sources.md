---
title: Power BI Report Server でのページ分割されたレポート データ ソース
description: ページ分割されたレポート (.rdl) が Power BI Report Server で接続できるデータ ソースについて説明します。
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 05/17/2018
ms.author: maggies
ms.openlocfilehash: 7cb5772e6ccdc1e4036d70f65a3a28210a4f6df1
ms.sourcegitcommit: d55d3089fcb3e78930326975957c9940becf2e76
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2020
ms.locfileid: "78260717"
---
# <a name="paginated-report-data-sources--in-power-bi-report-server"></a>Power BI Report Server でのページ分割されたレポート データ ソース
Power BI Report Server での Reporting Services のページ分割されたレポートは、SQL Server Reporting Services でサポートされているものと同じデータ ソースをサポートします。 「[Reporting Services でサポートされるデータ ソース (SSRS)](https://docs.microsoft.com/sql/reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs)」の一覧をご覧ください。

## <a name="connect-to-oracle-data-sources-with-useinstalleduiculture"></a>UseInstalledUICulture を使用して Oracle データ ソースに接続する

Oracle データ ソースに接続するために、Power BI Report Server では、NLS に依存しない Oracle Data Provider for .NET (ODP.NET) が使用されます。

既定では、レポート サーバーでは ODP.NET を読み込むために、最初のクライアントの UI カルチャが使用されます。  その結果、そのレポート サーバーから Oracle への後続の接続は、サービスを再起動するまで、すべてその最初の UI カルチャになります。  この方法では、UI カルチャの書式設定の不一致により、レポートを表示するときに問題が発生する可能性があります。

Power BI Report Server のエクスペリエンスを向上させるために、UseInstalledUICulture という名前の構成設定が導入されました。 UseInstalledUICulture が true に設定されている場合、レポート サーバーでは、最初のクライアントのカルチャではなく、常にサーバーの UI カルチャで ODP.NET が読み込まれます。
この設定は、2 月のサービス リリースから Power BI Report Server で利用できます

この機能を有効にするには、ORACLE 拡張機能エントリの rsreportserver.config ファイルを次のように変更します。
```xml
<Extension Name="ORACLE" Type="Microsoft.ReportingServices.DataExtensions.OracleClientConnectionWrapper,Microsoft.ReportingServices.DataExtensions">
    <Configuration>
        <UseInstalledUICulture>true</UseInstalledUICulture>
    </Configuration>
</Extension>
```

## <a name="next-steps"></a>次の手順
データ ソースに接続したので、[ページ分割されたレポートを作成](quickstart-create-paginated-report.md)します。  


他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
