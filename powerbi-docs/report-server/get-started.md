---
title: Power BI Report Server とは
description: Power BI Report Server の概要を読み、SQL Server Reporting Services (SSRS) やその他の Power BI とどのように適合するかについて理解してください。
author: maggiesMSFT
ms.author: maggies
keywords: ''
ms.date: 05/28/2020
ms.topic: overview
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.custom: mvc
ms.openlocfilehash: eba3038e654192ca0ae0ec381323762f80cf711a
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96397811"
---
# <a name="what-is-power-bi-report-server"></a>Power BI Report Server とは

Power BI Report Server は Web ポータルのあるオンプレミス レポート サーバーです。その Web ポータルでレポートや KPI を表示し、管理します。 Power BI レポート、ページ分割されたレポート、モバイル レポート、KPI を作成するためのツールを備えています。 ユーザーは、さまざまな方法でレポートにアクセスできます。Web ブラウザーやモバイル デバイスで表示したり、受信ボックスのメールとして表示したりすることができます。

![スクリーンショットには、Power BI Report Server の Web ポータルが表示されています。](media/get-started/power-bi-report-server-overview.png)

## <a name="comparing-power-bi-report-server"></a>Power BI Report Server の比較 
Power BI Report Server は、SQL Server Reporting Services と Power BI オンライン サービスの両方に似ていますが、さまざまな相違点があります。 Power BI サービスと同様に、Power BI Report Server には Power BI レポート (.pbix)、Excel ファイル、ページ分割されたレポート (.rdl) がホストされます。 Reporting Services と同様に、Power BI Report Server はオンプレミスです。 Power BI Report Server 機能は、Reporting Services のスーパーセットです。つまり、Reporting Services でできることはすべて Power BI Report Server でできる上に Power BI Report Server では Power BI レポートもサポートされています。 詳細については、「[Comparing Power BI Report Server and the Power BI service](compare-report-server-service.md)」(Power BI Report Server と Power BI サービスの比較) を参照してください。

## <a name="licensing-power-bi-report-server"></a>Power BI Report Server のライセンス
Power BI Report Server は、次の 2 種類のライセンスによって利用できます:[Power BI Premium](../admin/service-premium-what-is.md) とソフトウェア アシュアランス付きの SQL Server Enterprise Edition。 詳細については、[Microsoft ボリューム ライセンス](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=1&ShowArchived=True)をご覧ください。 Power BI Premium ライセンスがあれば、クラウドとオンプレミスを混在させたハイブリッド デプロイを作成できます。

Power BI Report Server に Power BI レポートを発行する場合、Power BI Pro ライセンスも必要です。 Power BI Report Server で Power BI レポートを表示したり、操作したりする場合、Power BI Pro ライセンスは必要ありません。

> [!NOTE]
> Power BI Premium の場合、Power BI Report Server は P SKU のみに含まれます。 EM SKU には含まれません。

## <a name="web-portal"></a>Web ポータル
Power BI Report Server のエントリ ポイントは、最新のブラウザーで表示できる安全な Web ポータルです。 ここで、すべてのレポートと KPI にアクセスします。 Web ポータル上のコンテンツは、従来のフォルダー階層で構成されています。 フォルダーでは、コンテンツは次の種類にグループ化されています:Power BI レポート、モバイル レポート、ページ分割されたレポート、KPI、Excel ブック。 共有データセットと共有データ ソースはそれぞれの専用フォルダーにあり、レポートの構成要素として使用されます。 お気に入りにタグを付けると、1 つのフォルダーで表示されます。 また、KPI は Web ポータルで直接作成します。 

![写真は、Power BI Report Server の Web ポータルが表示されたラップトップを示しています。](media/get-started/web-portal.png)

アクセス許可によっては、Web ポータルのコンテンツを管理できます。 レポート処理をスケジュールし、オンデマンドでレポートにアクセスし、発行したレポートにサブスクライブすることができます。 独自のカスタム [ブランド](/sql/reporting-services/branding-the-web-portal)を Web ポータルに適用することもできます。 

詳細については、[Power BI Report Server Web ポータル](/sql/reporting-services/web-portal-ssrs-native-mode)に関するページを参照してください。

## <a name="power-bi-reports"></a>Power BI レポート
Report Server 用に最適化された Power BI Desktop のバージョンで Power BI レポート (.pbix) を作成します。 次に、自分の環境の Web ポータルでレポートを発行して表示します。

![Power BI Report Server の Power BI レポート](media/get-started/powerbi-reports.png)

Power BI レポートは、データ モデルのマルチパースペクティブ表示で、視覚化によってデータ モデルからのさまざまな発見や洞察を表します。  レポートでは、単独の視覚化を使用することも、各ページでさまざまな視覚化を使用することもできます。 ロールによっては、他のユーザーの代わりに、レポートの閲覧やレポートの探索だけでなく、レポートの作成も実行することができます。

[Microsoft Power BI Desktop のインストール](install-powerbi-desktop.md)に関する記事をご覧ください。

## <a name="paginated-reports"></a>ページ分割されたレポート
ページ分割されたレポート (.rdl) は、視覚化されたドキュメント スタイルのレポートです。必要に応じてテーブルを水平方向と垂直方向に展開してすべてのデータを表示したり、複数のページにデータを連続表示したりすることができます。 これは、PDF や Word などでの印刷に最適化された固定レイアウトの完璧なピクセルのドキュメントを生成するのに適しています。 

![Power BI Report Server のページ分割されたレポート](media/get-started/paginated-reports.png)

[SQL Server Data Tools (SSDT)](/sql/reporting-services/tools/reporting-services-in-sql-server-data-tools-ssdt) で[レポート ビルダー](/sql/reporting-services/report-builder/report-builder-in-sql-server-2016)またはレポート デザイナーを使用して、ページ分割されたレポートを作成できます。

## <a name="reporting-services-mobile-reports"></a>Reporting Services のモバイル レポート
モバイル レポートはオンプレミス データに接続し、さまざまなデバイスとさまざまな保持方法に対応してレイアウトが調整されます。 モバイル レポートは SQL Server Mobile Report Publisher を使用して作成します。

詳細については、[Reporting Services のモバイル レポート](/sql/reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher)に関するページを参照してください。 

## <a name="report-server-programming-features"></a>Report Server のプログラミング機能
Power BI Report Server のプログラミング機能を利用すると、レポートを拡張してカスタマイズしたり、API を使用してデータとレポート処理をカスタム アプリケーションに統合または拡張したりできます。

詳細は、「[Report Server developer documentation](/sql/reporting-services/reporting-services-developer-documentation)」 (Report Server の開発者向けドキュメント) をご覧ください。

## <a name="next-steps"></a>次の手順
[Power BI レポート サーバーのインストール](install-report-server.md)  
[レポート ビルダーのダウンロード](https://www.microsoft.com/download/details.aspx?id=53613)  

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。