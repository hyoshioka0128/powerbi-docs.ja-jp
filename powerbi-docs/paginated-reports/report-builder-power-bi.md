---
title: Power BI レポート ビルダー
description: Power BI Report Builder は、ページ分割されたレポートを作成するためのツールです。
author: maggiesMSFT
ms.author: maggies
ms.date: 03/23/2021
ms.service: powerbi
ms.subservice: report-builder
featuredvideoid: 78TZeiEhveY
ms.topic: conceptual
ms.assetid: 55bf4f9c-d037-412f-ae57-3fc39ce32fa5
ms.openlocfilehash: 6897b495c48b54ed1e3736060e586077d6fa97e8
ms.sourcegitcommit: 644e5a3872f2a8e020fe44c4ec62a26ccc9a6a4e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2021
ms.locfileid: "105008215"
---
# <a name="power-bi-report-builder"></a>Power BI レポート ビルダー

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

Power BI Report Builder は、Power BI サービスに発行できるページ分割されたレポートを作成するためのツールです。  ページ分割されたレポートをデザインするときは、どのようなデータをどこから取得し、どのように表示するかの定義を作成します。 レポートを実行すると、指定したレポート定義がレポート プロセッサによって読み取られ、データが取得され、レポートのレイアウトと組み合わせることでレポートが生成されます。 レポート ビルダーでレポートをプレビューします。 その後、Power BI サービスにレポートを発行します。
 
作成を開始する準備ができましたか。 Microsoft ダウンロード センターから [Power BI Report Builder をインストールしましょう](https://go.microsoft.com/fwlink/?linkid=2086513)。

ビデオで学習する方がいいですか。 次のページを確認してください: [ビデオベースのコース: Power BI のページ分割されたレポートの 1 日コース](../learning-catalog/paginated-reports-online-course.md)

以下のページ分割されたレポートは、行と列のグループ、スパークライン、インジケーター、およびコーナーのセル内の概要円グラフがあるマトリックスと、色と円のサイズによって表現された 2 つの地理データ セットを示すマップで構成されています。  

![Power BI サービスにおけるページ分割されたレポート](media/report-builder-power-bi/report-builder-get-started-paginated-report.png)

## <a name="develop-reports-in-the-deployment-pipeline-tool"></a>配置パイプライン ツールでレポートを開発する

Power BI サービスでは、配置パイプライン ツールを使用して、ページ分割されたレポートを開発できます。 配置パイプラインを使用すると、Power BI のページ分割されたレポートを、ユーザーにリリースする前に開発およびテストできます。 このツールは、次の 3 つのステージを含むパイプラインです。
- 開発
- テスト
- Production

Power BI サービスで[配置パイプラインの使用を開始する](../create-reports/deployment-pipelines-get-started.md?tabs=paginated-reports)方法を参照してください。

## <a name="start-with-the-table-matrix-or-chart-wizard"></a>テーブル、マトリックス、またはグラフ ウィザードから開始する

データ ソース接続を作成し、フィールドをドラッグ アンド ドロップしてデータセット クエリを作成し、レイアウトとスタイルを選択して、レポートをカスタマイズします。  
  
## <a name="start-with-the-map-wizard"></a>マップ ウィザードから開始する

地図や幾何図形を背景として集計データを表示するレポートを作成します。 マップ データには、Transact-SQL クエリまたは Environmental Systems Research Institute, Inc.(ESRI) シェープファイルの空間データを使用できます。 Microsoft Bing マップ タイルの背景を追加することもできます。  

##  <a name="design-your-report"></a><a name="DesignRept"></a> レポートをデザインする  
  
-   **自由形式でレイアウトされたテーブル、マトリックス、グラフがあるページ分割されたレポートを作成する。** 列ベースのデータ向けのテーブル レポート、概要データ向けのマトリックス レポート (クロス集計レポートやピボットテーブル レポートなど)、グラフィカル データ向けのグラフ レポート、およびそれ以外のすべて向けの自由形式レポートを作成します。 他のレポートやグラフを、リスト、グラフィック、および動的な Web ベースのアプリケーション用のコントロールと共に、レポートに埋め込むことができます。  
  
-   **さまざまなデータ ソースからのレポート。** SQL Server、Analysis Services、Oracle、Power BI データセット、およびその他のデータベースのリレーショナル データと多次元データを使用するレポートを作成できます。  
  
-   **既存のレポートを変更する。** レポート ビルダーを使用して、SQL Server Data Tools (SSDT) レポート デザイナーで作成されたレポートをカスタマイズして更新できます。  
  
-   **データを変更する。** データのフィルター処理、グループ化、並べ替えを行ったり、数式や式を追加したりします。  

-   **グラフ、ゲージ、スパークライン、およびインジケーターを追加する。** データをビジュアル形式で要約し、大量の集計情報を一目で理解できるようにします。  
  
-   ドキュメント マップ、表示/非表示ボタン、サブレポートと詳細レポートへのドリルスルー リンクなどの **対話機能を追加します。** パラメーターとフィルターを使用し、データをフィルター処理してビューをカスタマイズします。  
  
-   画像や外部コンテンツなどの他のリソースを **埋め込んだり参照したりします。**  
  
##  <a name="manage-your-report"></a><a name="ManageRpt"></a> レポートを管理する  
  
-   コンピューターまたはレポート サーバーに **レポートの定義を保存** して、レポートの管理と他のユーザーとの共有を実行できます。  
  
-   レポートを開くとき、またはレポートを開いた後で **表示形式を選択します**。 Web 指向、ページ指向、およびデスクトップ アプリケーション形式を選択できます。 形式には、MHTML、PDF、XML、CSV、Word、および Excel が含まれます。  
  
-   **サブスクリプションを設定します。** Power BI サービスにレポートを発行した後、レポートを特定の時刻に実行し、電子メール サブスクリプションとして送信するように構成できます。  

## <a name="next-steps"></a>次の手順

- [Power BI Premium のページ分割されたレポートとは](paginated-reports-report-builder-power-bi.md)
- [ビデオベースのコース: Power BI のページ分割されたレポートの 1 日コース](../learning-catalog/paginated-reports-online-course.md)
