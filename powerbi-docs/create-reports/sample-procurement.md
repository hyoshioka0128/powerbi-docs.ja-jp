---
title: '調達の分析のサンプル: 使ってみる'
description: 'Power BI の調達の分析のサンプル: 使ってみる'
author: maggiesMSFT
ms.author: maggies
ms.reviewer: amac
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 07/02/2019
LocalizationGroup: Samples
ms.openlocfilehash: 73384f2f2021d949fcaca26c5b9e55cd7f0407af
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96417545"
---
# <a name="procurement-analysis-sample-for-power-bi-take-a-tour"></a>Power BI の調達の分析のサンプル: 使ってみる

調達の分析のサンプル コンテンツ パックには、製造会社のベンダー支出をカテゴリと場所ごとに分析するダッシュボード、レポート、データセットが含まれています。 このサンプルでは、次の領域を調べます。

* 売上が最も高いベンダー
* 最も支出の多いカテゴリ
* 最も割引率が高かったベンダーとその時期

![調達の分析のサンプルのダッシュボード](media/sample-procurement/procurement1.png)

このサンプルは、ビジネス用のデータ、レポート、ダッシュボードを用いて Power BI を使う方法について説明するシリーズの一部です。 匿名化された実際のデータを使用し、[obviEnce](http://www.obvience.com/) によって作成されています。 データは複数の形式 (コンテンツ パック、Power BI Desktop の .pbix ファイル、Excel ブック) で使用できます。 [Power BI 用のサンプル](sample-datasets.md)を参照してください。 

このチュートリアルでは、Power BI サービス内の調達の分析のサンプル コンテンツ パックを調べます。 Power BI Desktop とサービスのレポート エクスペリエンスは似ているので、Power BI Desktop 内のサンプルの .pbix ファイルを使用して作業することもできます。 

Power BI Desktop 内でサンプルを調べるために Power BI ライセンスは不要です。 Power BI Pro ライセンスを持っていない場合は、Power BI サービス内で、マイ ワークスペースにサンプルを保存できます。 

## <a name="get-the-sample"></a>サンプルを入手する

このサンプルを使用するには、事前にサンプルを[コンテンツ パック](#get-the-content-pack-for-this-sample)、[.pbix ファイル](#get-the-pbix-file-for-this-sample)、または [Excel ブック](#get-the-excel-workbook-for-this-sample)としてダウンロードしておく必要があります。

### <a name="get-the-content-pack-for-this-sample"></a>このサンプルのコンテンツ パックを入手する

1. Power BI サービス (app.powerbi.com) を開いてサインインし、サンプルを保存するワークスペースを開きます。 

    Power BI Pro ライセンスを持っていない場合は、マイ ワークスペースにサンプルを保存できます。

2. 左下隅にある **[データを取得]** を選びます。

    ![[データを取得] を選択](media/sample-datasets/power-bi-get-data.png)
3. 表示された **[データを取得]** ページで、 **[サンプル]** を選びます。

4. **[調達の分析のサンプル]** を選択し、 **[接続]** を選択します。  
  
   ![サンプルに接続](media/sample-procurement/procurement1a.png)
   
5. Power BI によってコンテンツ パックがインポートされ、新しいダッシュボード、レポート、およびデータセットが現在のワークスペースに追加されます。
   
   ![調達の分析のサンプル エントリ](media/sample-procurement/procurement-entry.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>このサンプルの .pbix ファイルを取得する

あるいは、Power BI Desktop で使用するために設計された [.pbix ファイル](https://download.microsoft.com/download/D/5/3/D5390069-F723-413B-8D27-5888500516EB/Procurement%20Analysis%20Sample%20PBIX.pbix)として、調達の分析のサンプルをダウンロードすることもできます。 

### <a name="get-the-excel-workbook-for-this-sample"></a>このサンプルの Excel ブックを取得する

このサンプルのデータ ソースを確認する場合は、[Excel ブック](https://go.microsoft.com/fwlink/?LinkId=529784) として入手することもできます。 ブックには、表示および変更可能な Power View シートが含まれています。 生データを表示するには、データ分析アドインを有効にし、 **[PowerPivot] > [管理]** を選択します。 Power View および Power Pivot のアドインを有効にするための詳細については、[Excel での Excel のサンプルの確認](sample-datasets.md#explore-excel-samples-inside-excel)に関するセクションを参照してください。


## <a name="spending-trends"></a>支出傾向
まず、カテゴリと場所ごとの支出の傾向を見てみましょう。  

1. サンプルを保存したワークスペースで、 **[ダッシュボード]** タブを開き、 **[調達の分析のサンプル]** ダッシュボードを探してそれを選択します。 
2. ダッシュボード タイル **[Total Invoice by Country/Region]\(国または地域別の合計請求\)** を選びます。これにより、 **[調達の分析のサンプル]** レポートの **[支出の概要]** ページが開きます。

    ![[支出の概要] ページ](media/sample-procurement/procurement2.png)

次の詳細に注意します。

* **[Total Invoice by Month and Category]\(月およびカテゴリ別の合計請求\)** 折れ線グラフ内で、 **[直接]** カテゴリには安定した支出があり、 **[物流]** には 12 月にピーク、 **[その他]** には 2 月にスパイクがあります。
* **[Total Invoice by Country/Region]\(国または地域別の合計請求\)** マップでは、支出のほとんどは米国内です。
* **[サブ カテゴリ別の合計請求]** 縦棒グラフでは、 **[ハードウェア]** および **[間接的な商品およびサービス]** が最も大きな支出カテゴリです。
* **[層別の請求額合計]** 横棒グラフでは、当社のビジネスのほとんどは、第 1 層 (上位 10 社) のベンダーと行われています。 そうすることで、より優れたベンダー リレーションシップを管理できます。

## <a name="spending-in-mexico"></a>メキシコでの支出
メキシコでの支出分野を見てみましょう。

1. **[Total Invoice by Country/Region]\(国または地域別の合計請求\)** マップ内で、 **[メキシコ]** バブルを選択します。 **[サブ カテゴリ別の合計請求]** 縦棒グラフで、ほとんどの支出は **[間接的な商品およびサービス]** サブ カテゴリに含まれることに注目してください。

   ![[支出の概要] ページで [メキシコ] を選択する](media/sample-procurement/pbi_procsample_spendmexico.png)
2. **[Indirect Goods & Services]** (間接的な商品およびサービス) 列にドリルダウンします。

   * **[サブ カテゴリ別の合計請求]** グラフで、グラフの右上隅にあるドリルダウン矢印 ![ドリルダウン矢印](media/sample-procurement/pbi_drilldown_icon.png) を選択します。
   * **[Indirect Goods & Services]** (間接的な商品およびサービス) 列を選びます。

      ご覧のように、これまで最大の支出は **[販売とマーケティング]** サブカテゴリに対するものです。
   * マップで **[Mexico]** (メキシコ) をもう一度選びます。

      メキシコの場合、最大の支出は **[保守と修理]** サブカテゴリにあります。

      ![メキシコの [間接的な商品およびサービス] のドリルダウン](media/sample-procurement/pbi_procsample_drill_mexico.png)
3. グラフの左上隅にある上向きの矢印を選んで、ドリルダウン前の状態に戻ります。
4. もう一度ドリルダウン矢印を選んで、ドリルダウンをオフにします。  
5. 上部のナビ ペインで **[調達の分析のサンプル]** を選んでダッシュボードに戻ります。

## <a name="evaluate-different-cities"></a>異なる複数の市区町村の評価
強調表示を使用して、異なる複数の市区町村を評価することができます。

1. ダッシュボード タイル **[Total Invoice, Discount % By Month]\(月別の合計請求、割引率\)** を選びます。これにより、 **[調達の分析のサンプル]** レポートの **[割引の分析]** ページが開きます。
2. **[都市別の請求額合計]** ツリーマップで、各都市を順番に選んで比較します。 マイアミのほとんどすべての請求は、第 1 層のベンダーからであることに注目してください。

   ![都市と層別の割引率 %](media/sample-procurement/pbi_procsample_miamitreemap2.png)

## <a name="vendor-discounts"></a>ベンダーの割引
ベンダーから利用可能な割引と、最大の割引を得られる期間も見てみましょう。
* 割引は月ごとに異なるか、同じままか。
* ある市区町村では、他の市区町村よりも大きく割引するか。

![[割引の分析] ページ](media/sample-procurement/procurement4.png)

### <a name="discount-by-month"></a>月ごとの割引
**[月別の請求額合計と割引率 %]** 複合グラフを見ると、2 月が最も繁忙な月で、9 月が最も閑散な月であることがわかります。 

これらの月の割引率を見てください。量が増加すると割引が縮小され、量が少ないと割引が増加します。 割引を必要とすればするほど、取引内容が悪化します。

![[月別の請求額合計と割引率 %] グラフ](media/sample-procurement/procurement5.png)

### <a name="discount-by-city"></a>市区町村ごとの割引
探索するもう 1 つの領域は、市区町村ごとの割引です。 ツリーマップ内の各市区町村を順番に選び、他のグラフがどのように変化するかをご確認ください。

* セントルイスは、2 月に合計請求の大きなスパイクがあり、4 月に割引額で大きな落ち込みがあります。
* メキシコシティの割引率が最高で (11.05%)、アトランタの割引率 (0.08%) が最低です。

![メキシコシティの割引グラフ](media/sample-procurement/procurement6.png)

### <a name="edit-the-report"></a>レポートの編集
左上隅の **[レポートの編集]** を選んで、編集ビューを調べます。

* ページの構成をご確認ください。
* ページを追加し、同じデータに基づくグラフを追加します。
* グラフの視覚化の種類を変更します。たとえば、ツリーマップをドーナツ グラフに変更します。
* グラフをダッシュボードにピン留めします。

## <a name="next-steps-connect-to-your-data"></a>次の手順: データへの接続
変更内容を保存しないことを選択できるため、この環境で試してみるのは安全です。 一方、それらを保存した場合は、 **[データを取得]** を選択して、常にこのサンプルの新しいコピーを取得できます。

この記事から、Power BI ダッシュボード、Q&A、レポートからサンプル データの分析情報をどのように得られるかがご理解いただけたでしょうか。 次はあなたの番です。ご自分のデータに接続してみてください。 Power BI を使用すると、広範なデータ ソースに接続することができます。 詳細については、[Power BI サービスの概要](../fundamentals/service-get-started.md)に関するページを参照してください。
