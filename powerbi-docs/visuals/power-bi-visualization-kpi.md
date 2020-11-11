---
title: 主要業績評価指標 (KPI) ビジュアル
description: Power BI で主要業績評価指標 (KPI) ビジュアルを作成します
author: msftrien
ms.reviewer: mihart
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 01/30/2020
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: f272a760c016fa0d5fcfc9849eaa2a01fc77b9f9
ms.sourcegitcommit: 5ccab484cf3532ae3a16acd5fc954b7947bd543a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2020
ms.locfileid: "93412868"
---
# <a name="create-key-performance-indicator-kpi-visualizations"></a>主要業績評価指標 (KPI) ビジュアルを作成する

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

主要業績評価指標 (KPI) は、測定可能な目標に対する進捗状況を視覚的に伝える方法の 1 つです。 KPI の詳細については、「[PowerPivot の主要業績評価指標 (KPI)](https://support.office.com/en-us/article/Key-Performance-Indicators-KPIs-in-Power-Pivot-E653EDEF-8A21-40E4-9ECE-83A6C8C306AA)」を参照してください。


## <a name="when-to-use-a-kpi"></a>KPI を使用する場合

KPI は、次のような場合に最適です。

* 進行状況を測定する。 "目標より進んでいるか、または遅れているか" という疑問に答えます。

* 目標までの距離を測定する。 "どの程度進んでいるか、または遅れているか" という疑問に答えます。

## <a name="kpi-requirements"></a>KPI の要件

デザイナーは、特定のメジャーに対する KPI ビジュアルに基づきます。 KPI の目的は、定義済みのターゲットに対する現在の値とメトリックの状態を評価できるようにすることです。 KPI ビジュアルには、値に対して評価される " *基本* " メジャー、" *ターゲット* " となるメジャーまたは値、および " *しきい値* " または " *目標* " が必要です。

KPI データセットには KPI の目標値が含まれている必要があります。 データセットに目標値が含まれていない場合は、目標が含まれる Excel シートをデータ モデルまたは PBIX ファイルに追加することによって作成できます。

## <a name="prerequisites"></a>前提条件

このチュートリアルでは、[小売の分析のサンプル PBIX ファイル](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)を使用します。

1. メニューバーの左上にある **[ファイル]**  >  **[開く]** を選択します。

1. **小売の分析のサンプル PBIX ファイル** を探します。

1. **小売りの分析のサンプルの .PBIX ファイル** をレポート ビューで開きます。 ![レポート ビューのアイコンのスクリーンショット。](media/power-bi-visualization-kpi/power-bi-report-view.png)

1. 新しいページを追加するには **+** を選択します。 ![黄色のタブのスクリーンショット。](media/power-bi-visualization-kpi/power-bi-yellow-tab.png)

> [!NOTE]
> Power BI を使用する同僚とレポートを共有するには、それぞれのユーザーが個別の Power BI Pro ライセンスを持っているか、レポートが Premium 容量に保存されている必要があります。    

## <a name="how-to-create-a-kpi"></a>KPI を作成する方法

この例では、売上目標に対する進行状況を測定する KPI を作成します。

1. **[フィールド]** ウィンドウで、 **[Sales] > [Total Units This Year]** を選択します。  この値がインジケーターになります。

1. **[時間] > [FiscalMonth]** を追加します。  この値によって傾向が示されます。

1. ビジュアルの右上隅の省略記号を選択して、Power BI が列を **FiscalMonth** を基準として昇順に並べ替えたことを確認します。

    > [!IMPORTANT]
    > ビジュアルを KPI に変換すると、並べ替えオプションは **なくなります** 。 ここで正しく並べ替える必要があります。

    ![展開されて [昇順で並べ替え] と [FiscalMonth] が選択された状態の省略記号メニューのスクリーンショット。](media/power-bi-visualization-kpi/power-bi-ascending-by-fiscal-month.png)

    正しく並べ替えると、visual は次のようになります。

    ![正しく並べ替えられたビジュアルのスクリーン ショット。](media/power-bi-visualization-kpi/power-bi-chart.png)

1. **[視覚化]** ウィンドウから **[KPI]** アイコンを選択して、ビジュアルを KPI に変換します。

    ![KPI アイコンが強調された [視覚化] ウィンドウのスクリーンショット。](media/power-bi-visualization-kpi/power-bi-kpi-template.png)

1. 目標を追加するには、 **[Total Units Last Year]** を **[ターゲットにする目標]** フィールドにドラッグします。

    ![完成した KPI ビジュアルと値が示された [フィールド] ウィンドウのスクリーンショット。](media/power-bi-visualization-kpi/power-bi-kpi-done.png)

1. 必要に応じて、ペイント ローラー アイコンを選んで [形式] ウィンドウを開きます。

    * **インジケーター** - インジケーターの表示単位と小数点以下の表示桁数を制御します。

    * **トレンド軸** - **[オン]** に設定すると、ビジュアルにトレンド軸が KPI ビジュアルの背景として表示されます。  

    * **目標** - **[オン]** に設定すると、ビジュアルに目標、および目標からの距離がパーセンテージとして表示されます。

    * **[色の設定] > [方向]** - 一部の KPI では高い値が " *良好な* " 値と見なされ、別の KPI では低い値が " *良好な* " 値と見なされます。 たとえば、前者の例としては収益があり、後者の例としては待機時間があります。 通常、収益では高い値が良好であり、待機時間の高い値は逆の意味です。 **[高いと良好]** を選び、必要に応じて色の設定を変更します。

KPI は Power BI サービスとモバイル デバイスでも使用できます。 これにより、ビジネスの核心部分に常につながっていることができます。

## <a name="considerations-and-troubleshooting"></a>考慮事項とトラブルシューティング

KPI が上記のようにならない場合、 **FiscalMonth** で並べ替えられていない可能性があります。 KPI には並べ替えオプションはありません。 お使いのビジュアルを KPI に変換する *前* に、最初から **FiscalMonth** で並べ替える必要があります。

## <a name="next-steps"></a>次の手順

* [Power BI マップの視覚エフェクトに関するヒントとテクニック](power-bi-map-tips-and-tricks.md)

* [Power BI での視覚化の種類](power-bi-visualization-types-for-reports-and-q-and-a.md)

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。
