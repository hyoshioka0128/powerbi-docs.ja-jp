---
title: Power BI でサイズを変更することが可能なレスポンシブ スライサーの作成
description: レポートに合わせてサイズを変更できるレスポンシブ スライサーの作成方法について説明します。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 04/06/2020
LocalizationGroup: Create reports
ms.openlocfilehash: 5fde91f2cfabd1f5a7727d3ec8a80d8ecddc7fc6
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96393441"
---
# <a name="create-a-responsive-slicer-you-can-resize-in-power-bi"></a>Power BI でサイズを変更することが可能なレスポンシブ スライサーの作成

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

レスポンシブ スライサーは、レポート上の領域に合わせてサイズが変わります。 レスポンシブ スライサーでは、異なるサイズに変更したり、水平から正方形や垂直などの異なる図形に変更できます。また、スライサー内の値を変更することで、スライサー自体を並べ替えることができます。 Power BI Desktop と Power BI サービスでは、水平スライサーおよび日付/範囲スライサーをレスポンシブにできます。 日付/範囲スライサーのタッチ領域も向上しているため、指先で、より簡単に変更できるようになりました。 レスポンシブ スライサーは必要に応じて小さくまたは大きくすることができます。また、Power BI サービスと Power BI モバイル アプリのレポートにちょうど収まるように自動的にサイズ変更することもできます。 

![レスポンシブ スライサーは、さまざまな図形にすることができます。](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-0-slicer.gif)

## <a name="create-a-slicer"></a>スライサーの作成

動的スライサーを作成する最初の手順は、基本的なスライサーを作成することです。 

1. **[視覚化]** ウィンドウで **[スライサー]** アイコン ![スライサー アイコン](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-0-slicer-icon.png) を選択します。
2. フィルターを適用するフィールドを **[フィールド]** にドラッグします。

    ![スライサーにフィールドを追加する](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-1-create.png)

## <a name="convert-to-a-horizontal-slicer"></a>水平スライサーに変換する

1. スライサーを選択し、 **[視覚化]** ウィンドウで **[書式]** タブを選択します。
2. **[全般]** セクションを展開し、 **[方向]** で **[横]** を選択します。

    ![スライサーを水平に設定する](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-2-horizontal.png) 

1.  より多くの値を表示する場合は、幅を広げます。

     ![スライサーの幅を広げる](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-3-wider.png)

## <a name="make-it-responsive-and-experiment-with-it"></a>スライサーをレスポンシブにして試す

この手順は簡単です。 

1. **[書式]** タブの **[全般]** セクションの **[方向]** の下で、**[レスポンシブ]** を **[オン]** にスライドします。  

    ![スライサーがレスポンシブになりました](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-4-responsive-on.png)

1. これでレスポンシブ スライサーを試すことができます。 コーナーをドラッグして高さを変えたり、幅を変えたりします。 非常に小さくすると、フィルターのアイコンだけが表示されるようになります。

    ![レスポンシブ スライサーが非常に小さくてフィルターのアイコンだけが表示されている状態](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-5-mini-icon.png)

## <a name="add-it-to-a-phone-report-layout"></a>電話レポート レイアウトに追加する

Power BI Desktop では、レポートのページごとに電話レイアウトを作成することができます。 ページに電話レイアウトがある場合、携帯電話では縦長ビューで表示されます。 それ以外の場合、横長ビューで表示する必要があります。 

1. **[ビュー]** メニューで **[電話レイアウト]** を選択します。

     ![[電話レイアウト] アイコン、[ビュー] メニュー](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-6-phone-layout-button.png)
    
1. 電話レポートに必要なすべてのビジュアルをグリッドにドラッグします。 レスポンシブ スライサーをドラッグするときに、希望のサイズにします。このケースでは、フィルターのアイコンだけです。

    ![電話レポート レイアウトにスライサーを追加する](media/power-bi-slicer-filter-responsive/power-bi-slicer-filter-responsive-7-phone-slicer-icon.png)

詳細については、「[Power BI 電話アプリ用に最適化したレポートを作成する](desktop-create-phone-report.md)」をお読みください。

## <a name="make-a-time-or-range-slicer-responsive"></a>時間スライサーまたは範囲スライサーをレスポンシブにする

同じ手順に従って、時間スライサーまたは範囲スライサーをレスポンシブにすることができます。 **[レスポンシブ]** を **[オン]** に設定した後、次のことに注意してください。

- ビジュアルは、キャンバスで許容されるサイズに応じて、入力ボックスの順序を最適化します。 
- データ要素の表示は、スライサーをできるだけ使用できるようにするため、キャンバスで許容されるサイズに基づいて最適化されます。 
- スライダーの新しい丸いハンドルバーは、タッチ操作を最適化します。 
- ビジュアルが小さくなりすぎて役に立たない場合、その場所でビジュアルの種類を表すアイコンになります。 これを操作するには、ダブルタップしてフォーカス モードで開きます。 これにより、機能を失うことなく、レポート ページ上の貴重なスペースを節約できます。

## <a name="next-steps"></a>次のステップ

- [Power BI サービスのスライサー](../visuals/power-bi-visualization-slicers.md)
- 他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。