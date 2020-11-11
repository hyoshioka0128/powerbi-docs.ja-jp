---
title: Power BI の折れ線グラフ
description: Power BI の折れ線グラフ
author: msftrien
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/05/2020
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: acbd6e40a351885b8644aca48edf41db81462864
ms.sourcegitcommit: 5ccab484cf3532ae3a16acd5fc954b7947bd543a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2020
ms.locfileid: "93411983"
---
# <a name="line-charts-in-power-bi"></a>Power BI の折れ線グラフ

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

折れ線グラフでは、ドットで表された一連のデータ ポイントが直線で接続されています。 折れ線グラフには 1 つまたは複数の線を含めることができ、 X と Y 軸があります。 

![シンプルな折れ線グラフ](media/power-bi-line-charts/power-bi-line.png)



## <a name="create-a-line-chart"></a>折れ線グラフを作成する
以下の手順では、売上およびマーケティングのサンプル アプリを使って、今年の売上をカテゴリ別に表示する折れ線グラフを作成します。 作業を進めるために、appsource.com からサンプル アプリを取得します。

> [!NOTE]
> Power BI を使用する同僚とレポートを共有するには、それぞれのユーザーが個別の Power BI Pro ライセンスを持っているか、レポートが Premium 容量に保存されている必要があります。

1. 空のレポート ページで開始します。 Power BI サービスを使っている場合は、[編集ビュー](../create-reports/service-interact-with-a-report-in-editing-view.md)でレポートを開いていることを確認します。

2. [フィールド] ペインで、 **[SalesFact]** \> **[合計単位]** を選択し、 **[日付]**  >  **[月]** を選択します。  お使いのレポート キャンバスに縦棒グラフが作成されます。

    ![[フィールド] ウィンドウから選択する](media/power-bi-line-charts/power-bi-step1.png)

4. [視覚化] ウィンドウから折れ線グラフのテンプレートを選択して、折れ線グラフに変換します。 

    ![折れ線グラフに変換する](media/power-bi-line-charts/power-bi-convert-to-line.png)
   

4. 2012 ～ 2014 年のデータが表示されるように折れ線グラフをフィルター処理します。 [フィルター] ウィンドウが折りたたまれている場合は、ここで展開します。 [フィールド] ペインで **[日付]** \> **[年]** を選択し、[フィルター] ペインの上にドラッグします。 **[このビジュアルでのフィルター]** 見出しにドロップします。 
     
    ![[フィールド] ウィンドウの横にある折れ線](media/power-bi-line-charts/power-bi-year-filter.png)

    **[高度なフィルター]** を **[基本フィルター]** に変更し、 **[2012]** 、 **[2013]** 、および **[2014]** を選択します。

    ![年のフィルター](media/power-bi-line-charts/power-bi-filter-year.png)

6. 必要に応じて、[グラフのテキストの色とサイズを調整](power-bi-visualization-customize-title-background-and-legend.md)します。 

    ![フォント サイズを大きくして、Y 軸のフォントを変更する](media/power-bi-line-charts/power-bi-line-3years.png)

## <a name="add-additional-lines-to-the-chart"></a>折れ線をグラフに追加する
折れ線グラフには、さまざまな線を多数追加できます。 また、それぞれの折れ線の値の差が大きすぎて、一緒には上手く表示されないことがあります。 ここでは現在のグラフに折れ線を追加して、折れ線によって表される値の差が非常に大きいときに、グラフの書式を設定する方法について説明します。 

### <a name="add-additional-lines"></a>折れ線を追加する
グラフ上のすべてのリージョンの合計ユニット数を 1 本の折れ線で表すのではなく、合計ユニットをリージョン別に分割してみましょう。 **[Geo]**  >  **[リージョン]** を [凡例] ウェルにドラッグして、折れ線を追加します。

   ![リージョンごとに 1 本の折れ線](media/power-bi-line-charts/power-bi-line-regions.png)


### <a name="use-two-y-axes"></a>2 つの Y 軸を使用する
同じグラフで売上合計と合計ユニット数を確認したい場合は、どうしますか。 販売数がユニット数を大幅に上回っている場合、折れ線グラフは使用できません。 実際、合計ユニット数を示す赤色の線はゼロのように見えます。

   ![スクリーンショットでは、Y 軸を 1 つだけ使用した場合に、合計ユニット数が平らに表示され、売上高と比較できなくなる様子が示されています。](media/power-bi-line-charts/power-bi-diverging.png)

それぞれの値の差が大きい場合、その値を 1 つのグラフに表示するには、複合グラフを使用します。 複合グラフの詳細については、「[Power BI の複合グラフ](power-bi-visualization-combo-chart.md)」を参照してください。 以下の例では、2 つ目の Y 軸を追加することで、売上と合計ユニット数を 1 つのグラフに表示しています。 

   ![スクリーンショットでは、売上高を棒グラフにして Y 軸を左側に表示し、合計ユニット数を折れ線グラフにして Y 軸を右側に表示している様子が示されています。](media/power-bi-line-charts/power-bi-dual-axes.png)

## <a name="highlighting-and-cross-filtering"></a>強調表示とクロス フィルター処理
[フィルター] ウィンドウの使用方法については、「[Power BI でのレポートへのフィルターの追加](../create-reports/power-bi-report-add-filter.md)」をご覧ください。

折れ線グラフでデータ ポイントを選択すると、レポート ページ上の他の視覚化がクロス強調表示およびクロス フィルター処理されます。逆の場合も同様です。 作業を進めるには、 **[マーケット シェア]** タブを開きます。  

折れ線グラフでは、1 つのデータ ポイントが X 軸と Y 軸上の交差ポイントです。 データ ポイントを選択すると、マーカーが追加されます。このマーカーは、レポート ページの他のビジュアルで、クロス強調表示およびクロス フィルター処理のソースであるポイント (折れ線が 1 本の場合は 1 つのポイント、折れ線が複数の場合は複数のポイント) を示しています。 お使いのビジュアルの密度が非常に高い場合、ビジュアル上でクリックした場所に最も近いポイントが選択されます。

この例では、2014 年 7 月の R12 のユニット数マーケット シェア % 33.16 とユニット数マーケット シェア% 34.74 が含まれるデータ ポイントが選択されています。

![折れ線グラフで 1 つのデータ ポイントを選択](media/power-bi-line-charts/power-bi-single-select.png)

縦棒グラフがどのようにクロス強調表示され、ゲージがクロス フィルター処理されているかを確認してください。

グラフ相互間のクロスフィルター処理とクロス強調表示を管理するには、「[Power BI レポートでの視覚エフェクトの相互作用](../create-reports/service-reports-visual-interactions.md)」を参照してください。

## <a name="considerations-and-troubleshooting"></a>考慮事項とトラブルシューティング
* 1 つの折れ線グラフで 2 つの Y 軸を使用することはできません。  代わりに複合グラフを使用する必要があります。
* 上記の例のグラフでは、フォント サイズを増やし、フォントの色を変更して、軸のタイトルを追加しました。また、グラフのタイトルと凡例を中央に揃える、両方の軸を 0 で開始する、などの書式も設定しています。 [書式設定] ウィンドウ (ペイント ローラー アイコン) には、無限と思われるようなオプション セットがあり、ご自身のグラフの外観を自由に設定できます。 [書式設定] ウィンドウを開いて、書式を設定する方法を確認することをお勧めします。

## <a name="next-steps"></a>次の手順

[Power BI での視覚化の種類](power-bi-visualization-types-for-reports-and-q-and-a.md)





