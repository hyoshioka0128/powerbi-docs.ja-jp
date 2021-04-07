---
title: Power BI Premium のページ分割されたレポートとは
description: ページ分割されたレポートを、Power BI サービスで使用できるようになりました。 SQL Server Reporting Services では、長い間、これらが標準のレポート形式でした。 これらのレポートは印刷または共有できます。 レポートのレイアウトを正確に制御できます。 たとえばテーブルが複数のページにまたがる場合でも、テーブルのすべてのデータが表示されます。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: jXTiYJKw1Rs
ms.service: powerbi
ms.subservice: report-builder
ms.topic: overview
ms.date: 03/23/2021
ms.openlocfilehash: 64d873ffa1ac3914e7b37edf12df4794b2db8f8b
ms.sourcegitcommit: 644e5a3872f2a8e020fe44c4ec62a26ccc9a6a4e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2021
ms.locfileid: "105007962"
---
# <a name="what-are-paginated-reports-in-power-bi-premium"></a>Power BI Premium のページ分割されたレポートとは

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

"*ページ分割されたレポート*" は、印刷または共有することを想定してデザインされています。 これらは、1 ページにちょうど収まるように設定されているため "*ページ分割された*" と呼ばれます。 テーブルが複数のページにまたがる場合でも、テーブルのすべてのデータが表示されます。 レポート ページのレイアウトを厳密に制御できるため、"*ピクセル単位で完璧*" と呼ばれることもあります。 Power BI Report Builder は、Power BI サービスのページ分割されたレポートを作成するためのスタンドアロン ツールです。 

始める準備ができている場合は、次のクイック リンクをご利用ください。

- [Microsoft ダウンロード センターから Power BI レポート ビルダーをインストールする](https://aka.ms/pbireportbuilder)
- [チュートリアル: ページ分割されたレポートを作成する](paginated-reports-quickstart-aw.md)
- [Power BI のページ分割されたレポートのサンプル](paginated-reports-samples.md)
- Power BI Report Server 向けの Report Builder や SQL Server Reporting Services に関する情報をお探しですか。 代わりに「[Report Builder をインストールする - Power BI Report Server](../report-server/install-report-builder.md)」をご覧ください。

ページ分割されたレポートには、多くのページが含まれる場合があります。 たとえば、このレポートは 563 ページです。 請求書ごとに 1 ページが使用されて、ヘッダーとフッターが繰り返されるように、各ページが正確にレイアウトされています。

![ページ分割された](media/paginated-reports-report-builder-power-bi/power-bi-paginated-wwi-report-page.png)

レポート ビルダーでレポートをプレビューした後、Power BI サービス (app.powerbi.com) に発行することができます。 サービスにレポートを発行するには、Power BI Pro ライセンスが必要です。 ワークスペースが Power BI Premium 容量に存在する限り、マイ ワークスペースまたはワークスペースにページ分割されたレポートを発行して共有できます。 また、Power BI 管理者は、Power BI 管理ポータルの [Premium 容量セクション](../admin/service-admin-premium-workloads.md#paginated-reports)で、ページ分割されたレポートを有効にする必要があります。 

## <a name="compare-power-bi-reports-and-paginated-reports"></a>Power BI レポートとページ分割されたレポートを比較する

ページ分割されたレポートの主な利点は、長さに関係なく、テーブル内のすべてのデータを印刷できることです。 Power BI レポートにテーブルを配置する画像。 ページのテーブルには行の一部が表示され、残りの部分を表示するにはスクロールバーを使用します。 そのページを印刷、または PDF にエクスポートすると、ページに表示されている行だけが出力されます。 

ここで、ページ分割されたレポートに同じテーブルを配置するとします。 これを印刷、または PDF にエクスポートすると、ページ分割されたレポートには、そのテーブル内のすべての行を印刷するために必要な数のページが含まれます。 

次のビデオでは、Microsoft Most Valued Professional である、Peter Myers (データ プラットフォーム) と、Chris Finlan (プリンシパル プログラム マネージャー) が、2 つのレポート形式で同様のテーブルを印刷する方法を紹介しています。 

<iframe width="560" height="315" src="https://www.youtube.com/embed/jXTiYJKw1Rs?list=PL1N57mwBHtN1icIhpjQOaRL8r9G-wytpT" frameborder="0" allowfullscreen></iframe>

このビデオは、8 つのモジュールで構成されるビデオベースのコース、「[Power BI Paginated Reports in a Day](../learning-catalog/paginated-reports-online-course.md)」(一日で学ぶ Power BI のページ分割されたレポート) の一部です。 このコースは、Power BI のページ分割されたレポートを作成、公開、および配布するために必要な技術知識を持つレポート作成者になれるよう支援することを目的としています。

## <a name="create-reports-in-power-bi-report-builder"></a>Power BI レポート ビルダーでレポートを作成する

ページ分割されたレポートには、専用のデザイン ツールである Power BI レポート ビルダーがあります。 それは新しいツールで、Power BI Report Server または SQL Server Reporting Services (SSRS) のページ分割されたレポートの作成にこれまで使われていたツールと同じ基盤を共有します。 実際、SSRS 2016 や 2017 または Power BI Report Server オンプレミス用に作成したページ分割されたレポートは、Power BI サービスと互換性があります。 Power BI サービスは下位互換性が維持されているので、レポートを上位バージョンに移行でき、以前のバージョンのページ分割されたレポートをアップグレードすることができます。 起動時は一部のレポート機能が利用できません。 詳細については、この記事の「[制限事項と考慮事項](#limitations-and-considerations)」を参照してください。

## <a name="develop-reports-in-the-deployment-pipeline-tool"></a>配置パイプライン ツールでレポートを開発する

Power BI サービスでは、配置パイプライン ツールを使用して、ページ分割されたレポートを開発できます。 配置パイプラインを使用すると、Power BI のページ分割されたレポートを、ユーザーにリリースする前に開発およびテストできます。 このツールは、次の 3 つのステージを含むパイプラインです。
- 開発
- テスト
- Production

Power BI サービスで[配置パイプラインの使用を開始する](../create-reports/deployment-pipelines-get-started.md?tabs=paginated-reports)方法を参照してください。

## <a name="report-from-a-variety-of-data-sources"></a>さまざまなデータ ソースからのレポート

1 つのページ分割されたレポートで、さまざまな異なるデータ ソースを使用できます。 Power BI レポートとは異なり、基になるデータ モデルはありません。 Power BI サービスでのページ分割されたレポートの初期リリースでは、レポート自体にデータ ソースとデータセットを埋め込みます。 現在のところ、共有データ ソースと共有データセットは使用できません。 ローカル コンピューター上のレポート ビルダーでレポートを作成します。 レポートでオンプレミスのデータに接続する場合は、レポートを Power BI サービスにアップロードした後、ゲートウェイを作成し、データ接続をリダイレクトする必要があります。 現時点で接続できるデータ ソースは次のとおりです。

- Azure SQL Database と Data Warehouse (Basic と oAuth 経由)
- Azure Analysis Services (SSO 経由)
- ゲートウェイ経由の SQL Server
- ゲートウェイ経由の SQL Server Analysis Services
- Power BI データセット
- Oracle
- Teradata

## <a name="design-your-report"></a>レポートをデザインする  

### <a name="create-paginated-reports-with-matrix-chart-and-free-form-layouts"></a>マトリックス、グラフ、および自由形式レイアウトでページ分割されたレポートを作成する

テーブル形式のレポートは、列ベースのデータで有効です。 クロス集計レポートやピボット テーブル レポートなどのマトリックス形式のレポートは、概要データに適しています。 グラフ形式のレポートはデータをグラフィカル形式で表示し、自由形式の "*リスト*" レポートは請求書などその他ほぼすべてのものを表示できます。 
  
いずれかのレポート ビルダー ウィザードを使用して始めることができます。 テーブル、マトリックス、およびグラフのウィザードでは、埋め込みデータ ソース接続と埋め込みデータセットを作成する手順が示されます。 その後、フィールドをドラッグ アンド ドロップしてデータセット クエリを作成し、レイアウトとスタイルを選択して、レポートをカスタマイズします。  
  
マップ ウィザードでは、地図や幾何図形を背景として集計データを表示するレポートを作成します。 マップ データには、Transact-SQL クエリまたは Environmental Systems Research Institute, Inc.(ESRI) シェープファイルの空間データを使用できます。 Microsoft Bing マップ タイルの背景を追加することもできます。  

### <a name="add-more-to-your-report"></a>レポートにさらに追加する

データのフィルター処理、グループ化、並べ替えを行って、または数式や式を追加して、データを変更します。 グラフ、ゲージ、スパークライン、インジケーターを追加して、データをビジュアル形式でまとめます。  パラメーターとフィルターを使用し、データをフィルター処理してビューをカスタマイズします。 外部コンテンツなど、画像や他のリソースを埋め込んだり参照したりします。  

レポート自体からすべてのテキスト ボックス、画像、テーブル、グラフまで、ページ分割されたレポート内のすべてのものには、レポートの外観を意図したとおりに設定できる一連のプロパティがあります。

## <a name="creating-a-report-definition"></a>レポート定義の作成

ページ分割されたレポートを設計するとき、実際には "*レポート定義*" を作成します。 それにデータは含まれません。 それでは、データを取得する場所、取得するデータ、データを表示する方法を指定します。 レポートを実行すると、指定したレポート定義がレポート プロセッサによって取得されて、データが取得され、レポートのレイアウトと組み合わせることでレポートが生成されます。 レポート定義は、Power BI サービス `https://app.powerbi.com` のマイ ワークスペースまたは同僚と共有しているワークスペースにアップロードします。 レポート データ ソースがオンプレミスにある場合は、レポートをアップロードした後、ゲートウェイを経由するようにデータ ソース接続をリダイレクトします。 

## <a name="view-your-paginated-report"></a>ページ分割されたレポートを表示する
ページ分割されたレポートは、ブラウザーの Power BI サービスまたは Power BI モバイル アプリで表示します。 Power BI サービスから、HTML、MHTML、PDF、XML、CSV、TIFF、Word、Excel など、さまざまな形式にレポートをエクスポートできます。 他のユーザーと共有することもできます。  

## <a name="create-a-subscription-to-your-report"></a>レポートへのサブスクリプションを作成する

Power BI サービスのページ分割されたレポートに対して自分および他のユーザー用の電子メール サブスクリプションを設定できるようになりました。 一般に、Power BI サービスのレポートおよびダッシュ ボードをサブスクライブする場合とプロセスは同じです。 サブスクリプションの設定時には、メールの受信頻度を次の中から選択します: 毎日、毎週、1 時間ごと。 サブスクリプションには、レポート出力全体の PDF 添付ファイルが含まれます。

詳しくは、記事「[Power BI サービスのページ分割されたレポートを自分および他のユーザーがサブスクライブする](../consumer/paginated-reports-subscriptions.md)」をご覧ください。 

## <a name="limitations-and-considerations"></a>制限事項と考慮事項

最初のリリースでは、次のような他のいくつかの機能がサポートされていません。

- レポート ページまたはビジュアルの Power BI ダッシュボードへのピン留め。 Power BI Report Server または Reporting Services のレポート サーバー上のオンプレミスのページ分割されたレポートから視覚エフェクトを Power BI ダッシュボードにピン留めすることは引き続き可能です。 詳しくは、[Reporting Services のアイテムの Power BI ダッシュボードへのピン留め](/sql/reporting-services/pin-reporting-services-items-to-power-bi-dashboards)に関するページをご覧ください。
- ドキュメント マップ。
- ドリルスルー レポート。  ドリルスルーのシナリオには、ページ分割されたレポートでの URL パラメーターの使用を検討してください。
- 共有データ ソースと共有データセット。

 
## <a name="next-steps"></a>次の手順

- [Microsoft ダウンロード センターから Power BI レポート ビルダーをインストールする](https://aka.ms/pbireportbuilder)
- [チュートリアル: ページ分割されたレポートを作成する](paginated-reports-quickstart-aw.md)
- [オンライン コース: Power BI のページ分割されたレポートの 1 日コース](../learning-catalog/paginated-reports-online-course.md)
- [Power BI のページ分割されたレポートのサンプル](paginated-reports-samples.md)
- [ページ分割されたレポートに直接データを入力する](paginated-reports-enter-data.md)
- [チュートリアル: 顧客向けのアプリケーションに Power BI のページ分割されたレポートを埋め込む](../developer/embedded/embed-paginated-reports-customers.md)
