---
title: 基本的な面グラフ
description: 基本的な面グラフです。
author: msftrien
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/16/2020
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: 4cc08398821d019d55475e0d4ed66a7633c49ca1
ms.sourcegitcommit: 5ccab484cf3532ae3a16acd5fc954b7947bd543a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2020
ms.locfileid: "93411431"
---
# <a name="create-and-use-basic-area-charts"></a>基本的な面グラフの作成と使用

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

基本的な面グラフ (層グラフとも呼ばれます) は、折れ線グラフに基づいています。 軸と折れ線の間の領域は、量を示すために色で塗りつぶされます。 

面グラフは、時間の経過に伴う変化の大きさを強調し、トレンドの合計値に注目させるために使用できます。 たとえば、時間の経過に伴う利益を表すデータを面グラフにプロットして、総利益を強調することができます。

![基本的な面グラフ](media/power-bi-visualization-basic-area-chart/power-bi-chart-example.png)

> [!NOTE]
> Power BI を使用する同僚とレポートを共有するには、それぞれのユーザーが個別の Power BI Pro ライセンスを持っているか、レポートが Premium 容量に保存されている必要があります。

## <a name="when-to-use-a-basic-area-chart"></a>基本的な面グラフを使用すべきケース
基本的な面グラフを選ぶとよい状況を挙げます。

* 時系列全体にわたって量のトレンドを確認および比較する場合 
* 個々の系列が物理的に数えられる集合を表す場合

### <a name="prerequisites"></a>前提条件
このチュートリアルでは、[小売の分析のサンプル PBIX ファイル](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)を使用します。

1. メニューバーの左上にある **[ファイル]**  >  **[開く]** を選択します。
   
2. **小売の分析のサンプル PBIX ファイル** を探します。

1. **小売の分析のサンプル PBIX ファイル** をレポート ビュー ![レポート ビュー アイコンのスクリーンショット。](media/power-bi-visualization-kpi/power-bi-report-view.png) で開きます。

1. 選択 ![黄色のタブのスクリーンショット。](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) を選択して、新しいページを追加します。


## <a name="create-a-basic-area-chart"></a>基本的な面グラフの作成
 

1. これらの手順は、今年の売上と去年の売上を月ごとに表示する面グラフを作成する際に役立ちます。
   
   a. [フィールド] ウィンドウで、 **[Sales] \> [Last Year Sales]** を選択し、 **[This Year Sales] > [Value]** を選択します。

   ![面グラフのデータ値](media/power-bi-visualization-basic-area-chart/power-bi-bar-chart.png)

   b.  [視覚化] ウィンドウの [面グラフ] アイコンを選んで、グラフを基本的な面グラフに変換します。

   ![面グラフ アイコン](media/power-bi-visualization-basic-area-chart/convertchart.png)
   
   c.  **[時刻] \> [FiscalMonth]** の順に選択して、 **[軸]** に追加します。   
   ![面グラフの軸の値](media/power-bi-visualization-basic-area-chart/powerbi-area-chartnew.png)
   
   d.  月別にグラフを表示するには、(ビジュアルの右上隅にある) 省略記号を選択し、 **[Sort by month]** (月別に並べ替え) を選択します。 並べ替え順序を変更するには、省略記号をもう一度選び、 **[昇順で並べ替え]** または **[降順で並べ替え]** を選択します。

## <a name="highlighting-and-cross-filtering"></a>強調表示とクロス フィルター処理
[フィルター] ウィンドウの使用方法については、「[Power BI でのレポートへのフィルターの追加](../create-reports/power-bi-report-add-filter.md)」をご覧ください。

グラフ内の 1 つの特定の領域を強調表示するには、その領域または上部の境界を選びます。  他の視覚エフェクトの種類とは異なり、同じページに他の視覚エフェクトがある場合、基本的な面グラフを強調表示しても、レポート ページの他の視覚エフェクトはクロス フィルター処理されません。 ただし、面グラフは、レポート ページ上の他の視覚化によってトリガーされたクロス フィルター処理のターゲットになります。 

1. 面グラフを選択し、 **New Store Analysis (新しい店舗の分析)** レポート ページにコピーしてみてください (Ctrl + C キーとCtrl + V キー)。
2. 面グラフの網掛けされた領域の 1 つを選択し、もう 1 つの網掛けされた領域を選択します。 ページのその他の視覚化には、何も影響がないことがわかります。
1. 次に、要素を選択します。 面グラフの変化を確認してください。クロスフィルタリングされます。

    ![フィルターの例](media/power-bi-visualization-basic-area-chart/power-bi-area-chart-filters.gif) 

詳しくは、「[Power BI レポートでの視覚化の相互作用](../create-reports/service-reports-visual-interactions.md)」をご覧ください。


## <a name="considerations-and-troubleshooting"></a>考慮事項とトラブルシューティング   
* [障碍を持つユーザーのためにレポートをより使いやすくする](../create-reports/desktop-accessibility-overview.md)
* 基本的な面グラフは、複数層の面の重なりによって値がわかりにくくなるため、値の比較には有効ではありません。 Power BI では、面の重なりを示すために透過が使用されます。 ただし、透過は 2 つか 3 つの異なる面についてのみうまく機能します。 4 つ以上のメジャーとトレンドを比較する必要がある場合は、折れ線グラフを使用してみてください。 4 つ以上のメジャーと量を比較する必要がある場合は、ツリーマップを使用してみてください。

## <a name="next-step"></a>次のステップ
[Power BI のレポート](power-bi-visualization-card.md)  
