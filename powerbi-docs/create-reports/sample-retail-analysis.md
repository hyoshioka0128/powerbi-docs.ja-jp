---
title: Power BI の小売りの分析のサンプル:ツアーを開始する
description: Power BI の小売りの分析のサンプル:ツアーを開始する
author: maggiesMSFT
ms.author: maggies
ms.reviewer: amac
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 07/02/2019
LocalizationGroup: Samples
ms.openlocfilehash: 1a3a4bc467299f7baeb12ca68af1d2730d5839f0
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96395994"
---
# <a name="retail-analysis-sample-for-power-bi-take-a-tour"></a>Power BI の小売りの分析のサンプル:ツアーを開始する

小売りの分析のサンプル コンテンツ パックには、複数の店舗や地区で販売された品目の小売り売上データを分析するダッシュボード、レポート、データセットが含まれています。 メトリックでは、新店舗の分析以外に、売上、出荷単位、粗利、差異の分野の本年度の業績と昨年度の業績が比較されます。 

![小売りの分析のサンプルのダッシュボード](media/sample-retail-analysis/retail1.png)

このサンプルは、ビジネス用のデータ、レポート、ダッシュボードを用いて Power BI を使う方法について説明するシリーズの一部です。 匿名化された実際のデータを使用し、[obviEnce](http://www.obvience.com/) によって作成されています。 データは複数の形式 (コンテンツ パック、Power BI Desktop の .pbix ファイル、Excel ブック) で使用できます。 [Power BI 用のサンプル](sample-datasets.md)を参照してください。 

このチュートリアルでは、Power BI サービス内の小売りの分析のサンプル コンテンツ パックを調べます。 Power BI Desktop とサービスのレポート エクスペリエンスは似ているので、Power BI Desktop 内のサンプルの .pbix ファイルを使用して作業することもできます。 

Power BI Desktop 内でサンプルを調べるために Power BI ライセンスは不要です。 Power BI Pro ライセンスを持っていない場合は、Power BI サービス内で、マイ ワークスペースにサンプルを保存できます。 

## <a name="get-the-sample"></a>サンプルを入手する

 このサンプルを使用するには、事前にサンプルを[コンテンツ パック](#get-the-content-pack-for-this-sample)、[.pbix ファイル](#get-the-pbix-file-for-this-sample)、または [Excel ブック](#get-the-excel-workbook-for-this-sample)としてダウンロードしておく必要があります。

### <a name="get-the-content-pack-for-this-sample"></a>このサンプルのコンテンツ パックを入手する

1. Power BI サービス (app.powerbi.com) を開いてサインインし、サンプルを保存するワークスペースを開きます。 

    Power BI Pro ライセンスを持っていない場合は、マイ ワークスペースにサンプルを保存できます。

2. 左下隅にある **[データを取得]** を選びます。

    ![[データを取得] を選択](media/sample-datasets/power-bi-get-data.png)
3. 表示された **[データを取得]** ページで、 **[サンプル]** を選びます。
   
4. **[小売りの分析のサンプル]** を選び、 **[接続]** を選びます。  
  
   ![サンプルに接続](media/sample-retail-analysis/retail16.png)
   
5. Power BI によってコンテンツ パックがインポートされ、新しいダッシュボード、レポート、およびデータセットが現在のワークスペースに追加されます。
   
   ![小売りの分析のサンプル エントリ](media/sample-retail-analysis/retail-entry.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>このサンプルの .pbix ファイルを取得する

あるいは、Power BI Desktop で使用するために設計された [.pbix ファイル](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)として、小売りの分析のサンプルをダウンロードすることもできます。 

### <a name="get-the-excel-workbook-for-this-sample"></a>このサンプルの Excel ブックを取得する

このサンプルのデータ ソースを確認する場合は、[Excel ブック](https://go.microsoft.com/fwlink/?LinkId=529778) として入手することもできます。 ブックには、表示および変更可能な Power View シートが含まれています。 生データを表示するには、データ分析アドインを有効にし、 **[PowerPivot] > [管理]** を選択します。 Power View および Power Pivot のアドインを有効にするための詳細については、[Excel での Excel のサンプルの確認](sample-datasets.md#explore-excel-samples-inside-excel)に関するセクションを参照してください。

## <a name="start-on-the-dashboard-and-open-the-report"></a>ダッシュボードを起動し、レポートを開く

1. サンプルを保存したワークスペースで、 **[ダッシュボード]** タブを開き、 **[小売りの分析のサンプル]** ダッシュボードを探してそれを選択します。 
2. ダッシュボード上で、**Total Stores New & Existing Stores\(新規店舗と既存の店舗の合計\)** タイルを選び、小売りの分析のサンプル レポートの **店舗売上の概要** ページを開きます。 

   ![[Total Stores] タイル](media/sample-retail-analysis/retail-analysis-7.png)  

   このレポートのページには、合計で 104 店舗が表示され、そのうち 10 店舗は新規です。 2 つの店舗チェーン、Fashions Direct と Lindseys があります。 Fashions Direct 店舗は、平均的により大規模です。
3. **[チェーン別の今年の売上]** 円グラフで、 **[Fashions Direct]** スライスを選択します。

   ![[チェーン別の今年の売上] グラフ](media/sample-retail-analysis/retail3.png)  

   **[総売上差異 %]** バブル チャート内の結果に注目してください。

   ![[総売上差異 %] グラフ](media/sample-retail-analysis/pbi_sample_retanlbubbles.png)  

   **FD-01** 地区は **1 平方フィートあたりの売上** の平均が最も高く、FD-02 は昨年に比べて **[総売上差異]** が最も小さくなっています。 FD-03 と FD-04 は全体的に業績が最低です。
4. 個々のバブルまたは他のグラフをクリックすると、クロス強調表示が表示され、選択箇所による影響が明らかになります。
5. ダッシュボードに戻るには、上部のナビ ペインから **[小売りの分析のサンプル]** を選びます。

   ![ナビゲーション バー](media/sample-retail-analysis/power-bi-breadcrumbs.png)
6. ダッシュボード上の **[This Year's Sales New & Existing Stores]\(新規と既存の店舗の今年度の売上\)** タイルで、[Q&A] 質問ボックスに "*今年の売上*" と入力します。

   ![[今年の売上] タイル](media/sample-retail-analysis/pbi_sample_retanlthisyrsales.png)

   Q&A の結果が表示されます。

   ![Q&A の [今年の売上]](media/sample-retail-analysis/retail7.png)

## <a name="review-a-tile-created-with-power-bi-qa"></a>Power BI の Q&A で作成されたタイルを確認する
さらに詳細を取得しましょう。

1. 質問を「_this year sales **by district**_ 」(地区別の今年の売上) に変更します。 結果を観察します。Q&A によって自動的に横棒グラフに結果が配置され、他の語句が提案されます。

   ![Q&A の地区別の今年の売上](media/sample-retail-analysis/retail8.png)
2. ここで、質問を「_this year sales **by zip and chain**_ 」(郵便番号とチェーン別の今年の売上) に変更します。

   入力した質問が Power BI によってどのように応答され、該当するグラフに表示されるかに注目してください。
3. その他の質問を入力して、どのような結果が得られるかを実験してください。
4. 次に進む準備ができたら、ダッシュボードに戻ります。

## <a name="dive-deeper-into-the-data"></a>データをさらに深く分析する
ここで、より詳細なレベルで地域の業績を見てみましょう。

1. ダッシュボード上で、 **[今年の売上、昨年の売上]** タイルを開きます。これにより、レポートの **[地区の毎月の売上]** ページが開きます。

   ![[今年の売上、昨年の売上] タイル](media/sample-retail-analysis/pbi_sample_retanlareacht.png)

   **[会計月別の総売上差異 %]** グラフで、昨年と比較した差異 % が大きく変動し、1 月、4 月、7 月に特に実績が大きく下がっていることに注目してください。

   ![[会計月別の総売上差異 %] グラフ](media/sample-retail-analysis/pbi_sample_retanlsalesvarcol.png)

   絞り込んで、どこに問題があるかを特定できるかどうかを見てみましょう。
2. バブル チャートで、 **[020-紳士服]** バブルを選択します。

   ![[020-紳士服] の選択](media/sample-retail-analysis/retail11.png)  

   ビジネス全体と比べて、紳士服のカテゴリの 4 月には深刻な影響がありませんが、1 月と 7 月は問題のある月であることに注目してください。
1. **[010-婦人服]** バブルを選択します。

   ![[010-婦人服] の選択](media/sample-retail-analysis/retail12.png)

   ビジネス全体と比べて、婦人服のカテゴリにおける業績はすべての月で非常に低く、ほとんどすべての月において、前年より悪くなっていることに注目してください。
1. フィルターをクリアするには、もう一度バブルを選択します。

## <a name="try-out-the-slicer"></a>スライサーを試す
特定の地域の実績を見てみましょう。

1. 左上の **[地区マネージャー]** スライサーで **[Allan Guinot]** を選択します。

   ![[Allan Guinot] の選択](media/sample-retail-analysis/retail13.png)

   昨年に比べて、Allan の地区が 3 月と 6 月に優れた業績を示していることにご注意ください。
2. **[Allan guinot]** がまだ選択されている状態で、バブル チャートの **[Womens-10]\(婦人服-10\)** バブルを選択します。

   ![[Allan guinot] と [Womens-10]\(婦人服-10\) を選択](media/sample-retail-analysis/power-bi-allan.png)

   [Womens-10]\(婦人服-10\) のカテゴリでは、Allan の地区は昨年度の量に一度も到達していないことに注目してください。
3. その他の地域のマネージャーとカテゴリを調べてください。どのような分析情報が見つかりますか。
4. 次に進む準備ができたら、ダッシュボードに戻ります。

## <a name="what-the-data-says-about-sales-growth-this-year"></a>データから今年度の売上成長についてわかること
調べる最後の領域は、今年度開店した新店舗を調べることによる成長です。

1. **[Stores Opened This Year by Open Month, Chain]\(開店月別の今年度開店した店舗、チェーン\)** タイルを選びます。これによりレポートの **[新しい店舗の分析]** ページが開きます。

   ![[新しい店舗の分析] ページ](media/sample-retail-analysis/retail15.png)

   タイルから明らかなとおり、今年度、Lindseys 店舗よりも Fashions Direct 店舗の方が多く開店しました。
2. **[名前別の平方フィート単位の売上]** グラフに注目してください。

   ![[名前別の平方フィート単位の売上] グラフ](media/sample-retail-analysis/retail14.png)

    平方フィートあたりの平均売上は、新店舗によって異なることに注目してください。
3. 右上の **開店月別、チェーン別の開店店舗数** グラフで、**Fashions Direct** 凡例項目を選択します。 同じチェーン店でも、最も業績の高い店舗 (Winchester Fashions Direct) と最も業績の低い店舗 (Cincinnati 2 Fashions Direct) では、それぞれ 21.22 ドルと 12.86 ドルと、大きな違いがあります。

   ![Fashions Direct を選択](media/sample-retail-analysis/power-bi-lindseys.png)
4. **[名前]** スライサーで **[Winchester Fashions Direct]** を選択し、折れ線グラフに注目します。 最初の販売数は 2 月に報告されました。
5. スライサーで **[Cincinnati 2 Fashions Direct]** を選択し、折れ線グラフから、開店したのは 6 月で、業績は最も低いらしいことを確認します。
6. 各グラフのその他の横棒、折れ線、バブルを選択して調べ、どのような分析情報が見つかるか確認してください。

## <a name="next-steps-connect-to-your-data"></a>次の手順:データへの接続
変更内容を保存しないことを選択できるため、この環境で試してみるのは安全です。 一方、それらを保存した場合は、 **[データを取得]** を選択して、常にこのサンプルの新しいコピーを取得できます。

この記事から、Power BI ダッシュボード、Q&A、レポートからサンプル データの分析情報をどのように得られるかがご理解いただけたでしょうか。 次はあなたの番です。ご自分のデータに接続してみてください。 Power BI を使用すると、広範なデータ ソースに接続することができます。 詳細については、[Power BI サービスの概要](../fundamentals/service-get-started.md)に関するページを参照してください。
