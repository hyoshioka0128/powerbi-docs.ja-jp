---
title: Power BI レポート ビルダー
description: Power BI Report Builder は、ページ分割されたレポートを作成するためのツールです。
ms.date: 11/27/2019
ms.service: powerbi
ms.subservice: report-builder
featuredvideoid: 78TZeiEhveY
ms.topic: conceptual
ms.assetid: 55bf4f9c-d037-412f-ae57-3fc39ce32fa5
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 0118bc427ce58f48d50b3e8ed4e918bf66c6e8fc
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "80621520"
---
# <a name="power-bi-report-builder"></a>Power BI レポート ビルダー

 Power BI Report Builder は、ページ分割されたレポートを作成するためのツールです。  ページ分割されたレポートをデザインするときは、どのようなデータをどこから取得し、どのように表示するかの定義を作成します。 レポートを実行すると、指定したレポート定義がレポート プロセッサによって読み取られ、データが取得され、レポートのレイアウトと組み合わせることでレポートが生成されます。 レポート ビルダーでレポートをプレビューします。 その後、Power BI サービスにレポートを発行します。

ビデオで学習する方がいいですか。 YouTube で、Power BI プリンシパル プログラム マネージャーの Chris Finlan による、Power BI のページ分割されたレポートに関するビデオ シリーズをご覧ください。

<iframe width="560" height="315" src="https://www.youtube.com/embed/78TZeiEhveY?list=PLx7LcKtN_gq-JVzM6L8xNNxX7kts-KflJ" frameborder="0" allowfullscreen></iframe>

以下のページ分割されたレポートは、行と列のグループ、スパークライン、インジケーター、およびコーナーのセル内の概要円グラフがあるマトリックスと、色と円のサイズによって表現された 2 つの地理データ セットを示すマップで構成されています。  

![Power BI サービスにおけるページ分割されたレポート](media/report-builder-power-bi/report-builder-get-started-paginated-report.png)

##  <a name="jump-start-report-creation"></a><a name="JumpStartReptCreation"></a> レポート作成のジャンプスタート  
 
-   **テーブル、マトリックス、またはグラフ ウィザードから開始します**。 データ ソース接続を作成し、フィールドをドラッグ アンド ドロップしてデータセット クエリを作成し、レイアウトとスタイルを選択して、レポートをカスタマイズします。  
  
-   **マップ ウィザードを使用して開始します**。地図や幾何図形を背景として集計データを表示するレポートを作成します。 マップ データには、Transact-SQL クエリまたは Environmental Systems Research Institute, Inc. (ESRI) シェープファイルの空間データを使用できます。 Microsoft Bing マップ タイルの背景を追加することもできます。  

##  <a name="design-your-report"></a><a name="DesignRept"></a> レポートをデザインする  
  
-   **テーブル、マトリックス、グラフ、および自由形式のレポート レイアウトの改ページ調整されたレポートを作成します。** 列ベースのデータ向けのテーブル レポート、概要データ向けのマトリックス レポート (クロス集計レポートやピボットテーブル レポートなど)、グラフィカル データ向けのグラフ レポート、およびそれ以外のすべて向けの自由形式レポートを作成します。 他のレポートやグラフを、リスト、グラフィック、および動的な Web ベースのアプリケーション用のコントロールと共に、レポートに埋め込むことができます。  
  
-   **さまざまなデータ ソースからレポートを作成します。** SQL Server、Analysis Services、Oracle、Power BI データセット、およびその他のデータベースのリレーショナル データと多次元データを使用するレポートを作成できます。  
  
-   **既存のレポートを変更します。** レポート ビルダーを使用して、SQL Server Data Tools (SSDT) レポート デザイナーで作成されたレポートをカスタマイズして更新できます。  
  
-   **データを変更する。** データのフィルター処理、グループ化、並べ替えを行ったり、数式や式を追加したりします。  

-   **グラフ、ゲージ、スパークライン、およびインジケーターを追加する。** データをビジュアル形式で要約し、大量の集計情報を一目で理解できるようにします。  
  
-   ドキュメント マップ、表示/非表示ボタン、サブレポートと詳細レポートへのドリルスルー リンクなどの**対話機能を追加します。** パラメーターとフィルターを使用し、データをフィルター処理してビューをカスタマイズします。  
  
-   画像や外部コンテンツなどの他のリソースを**埋め込んだり参照したりします。**  
  
##  <a name="manage-your-report"></a><a name="ManageRpt"></a> レポートを管理する  
  
-   コンピューターまたはレポート サーバーに**レポートの定義を保存**して、レポートの管理と他のユーザーとの共有を実行できます。  
  
-   レポートを開くとき、またはレポートを開いた後で**表示形式を選択します**。 Web 指向、ページ指向、およびデスクトップ アプリケーション形式を選択できます。 形式には、MHTML、PDF、XML、CSV、Word、および Excel が含まれます。  
  
-   **サブスクリプションを設定します。** Power BI サービスにレポートを発行した後、レポートを特定の時刻に実行し、電子メール サブスクリプションとして送信するように構成できます。  

## <a name="next-steps"></a>次のステップ

- [Power BI Premium のページ分割されたレポートとは](paginated-reports-report-builder-power-bi.md)
- YouTube で、Power BI プリンシパル プログラム マネージャーの Chris Finlan による、[Power BI のページ分割されたレポートに関するビデオ シリーズ](https://www.youtube.com/watch?v=78TZeiEhveY&list=PLx7LcKtN_gq-JVzM6L8xNNxX7kts-KflJ)をご覧ください