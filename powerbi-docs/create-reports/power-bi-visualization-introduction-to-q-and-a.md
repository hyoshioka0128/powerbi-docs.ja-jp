---
title: Power BI Q&A でビジュアルを作成する
description: 小売りの分析のサンプルを使用し、Power BI サービスの Q&A でビジュアルを作成する方法について説明します
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 05/13/2019
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 7eae93eb2b4594a180836f43a758c6bef7b3e90e
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415038"
---
# <a name="create-a-visual-with-power-bi-qa"></a>Power BI Q&A でビジュアルを作成する

自然言語を使用して質問するのが、データから回答を得る最も速い方法である場合があります。  この記事では、同じ視覚エフェクトを作成する 2 種類の方法に注目します。1 つは Q&A を使用して質問することによって作成する方法、2 つ目はレポートで作成する方法です。 ここでは Power BI サービスを使用してレポートにビジュアルを作成しますが、その手順は Power BI Desktop を使用する場合とほぼ同じです。

![Power BI によって作成されたグラフ](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-create-visual.png)

作業を進めるには、編集できるレポートが必要なので、Power BI で使用可能なサンプルの 1 つを使います。

## <a name="create-a-visual-with-qa"></a>Q&A でビジュアルを作成する

この折れ線グラフを Q&A を使用して作成するには、次のようにします。

1. Power BI ワークスペースから、 **[データの取得]** \> **[サンプル]** \> **[小売りの分析のサンプル]**  >  **[接続]** を選択します。

1. [小売りの分析のサンプル] ダッシュボードを開いて、Q&A ボックス ( **[データについて質問する]** ) にカーソルを置きます。

    ![Q&A ボックスにカーソルを置く](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-cursor-in-qna-box.png)

2. Q&A ボックスに、次のような質問を入力します。
   
    **this year sales and last year sales by month as area chart** (面グラフによる月別の今年度の売上高と前年度の売上高)
   
    質問を入力していくと、Q&A が回答を表示するために最適な視覚化を選択し、質問を変更するにつれ視覚化が動的に変化します。 また、Q&A は、候補機能、オートコンプリート、スペルの修正によって質問の形式を整えるようにユーザーを助けます。 言い回しにわずかな変更を加えた、"this year sales and last year sales by *time month* as area chart" が Q&A から提案されます。  

    ![Q&A によって修正された言い回し](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-corrected-create-filled-chart.png)

4. その文を選択して提案に同意します。 
   
   質問の入力が完了すると、結果はダッシュボードで確認したのと同じグラフになります。
   
   ![Q&A によって作成された面グラフ](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-create-filled-chart.png)

4. グラフをダッシュボードにピン留めするには、ピン アイコンを選択します。 ![ピン アイコンをクリックまたはタップします。](media/power-bi-visualization-introduction-to-q-and-a/pinnooutline.png) をタップします。

## <a name="create-a-visual-in-the-report-editor"></a>レポート エディターでビジュアルを作成する

1. 小売りの分析のサンプル ダッシュボードに戻ります。
   
2. ダッシュボードには、"Last Year Sales and This Year Sales (前年度の売上高と今年度の売上高)" を表す同じ面グラフ タイルがあります。  このタイルを選択します。 Q&A で作成したタイルは選択しないでください。 選択すると Q&A が表示されてしまいます。 元の面グラフ タイルがレポートで作成された場合は、この視覚化が含まれたページにレポートが表示されます。

    ![小売りの分析のサンプルのダッシュボード](media/power-bi-visualization-introduction-to-q-and-a/power-bi-dashboard.png)

1. **[レポートの編集]** を選択して、レポートを編集ビューで開きます。  レポートの所有者でない場合は、編集ビューでレポートを開くオプションはありません。
   
    ![レポートの編集ボタン](media/power-bi-visualization-introduction-to-q-and-a/power-bi-edit-report.png)
4. 面グラフを選択して、 **[フィールド]** ウィンドウで設定を確認します。  レポートの作成者は、これらの 3 つの値 (**Sales** テーブルの **[Last Year Sales]** と **[This Year Sales]** の値、および **Time** テーブルの **[FiscalMonth]** ) を選択して、それらを **[軸]** ウェルと **[値]** ウェルに編成して、このグラフを作成しました。
   
    ![視覚化ウィンドウ](media/power-bi-visualization-introduction-to-q-and-a/gnatutorial_3-new.png)

    最終的に同じビジュアルになっていることがわかります。 この方法でも、作成にさほど手間はかかりません。 ただし、Q&A を使用した方が簡単に作成できます。

## <a name="next-steps"></a>次のステップ

- [ダッシュボードとレポートで Q&A を使用する](power-bi-tutorial-q-and-a.md)  
- [コンシューマー向けの Q&A](../consumer/end-user-q-and-a.md)
- [データを Power BI の Q&A でうまく使う方法](service-prepare-data-for-q-and-a.md)

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。
