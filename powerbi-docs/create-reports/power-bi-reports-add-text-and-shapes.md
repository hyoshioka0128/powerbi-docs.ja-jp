---
title: Power BI レポート内のテキスト ボックスと図形
description: Microsoft Power BI サービスを使用してレポートにテキスト ボックスと図形を追加および作成します。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: _3q6VEBhGew
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 05/29/2019
LocalizationGroup: Visualizations
ms.openlocfilehash: 90c7489ad047be47a2a1f9ac9e814a9da5724f32
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96393556"
---
# <a name="add-text-boxes-and-shapes-to-power-bi-reports"></a>Power BI レポートにテキスト ボックスと図形を追加する
Power BI サービスと Power BI Desktop を使用すると、レポートにテキスト ボックスや図形を追加できます。 どちらの場合もレポートの編集アクセス許可が必要です。 Power BI サービスでレポートが自分と共有されている場合、編集アクセス許可はありません。 

Will が Power BI Desktop を使用して[静的な画像をレポートに追加](/learn/modules/visuals-in-power-bi/12-formatting)する様子をご覧ください。視聴後は下記の手順に従い、Power BI サービスを代わりに使用してご自身でお試しください。
> 
> <iframe width="560" height="315" src="https://www.youtube.com/embed/_3q6VEBhGew" frameborder="0" allowfullscreen></iframe>
> 

## <a name="add-a-text-box-to-a-report"></a>レポートにテキスト ボックスを追加する
1. レポートを編集ビューで開きます。

2. レポート キャンバス内の任意の空白の位置にカーソルを置いて、上部メニューから **[テキスト ボックス]** を選びます。
   
   ![テキスト ボックスを選ぶ](media/power-bi-reports-add-text-and-shapes/pbi_textbox.png)
3. テキスト ボックスにテキストを入力し、必要に応じて、書式のフォント、色、テキストの配置を設定します。 
   
   ![テキストを入力する](media/power-bi-reports-add-text-and-shapes/pbi_textbox2new.png)
4. テキスト ボックスを配置するには、上部にある灰色の領域を選んでドラッグします。 テキスト ボックスのサイズを変更するには、アウトライン ハンドルのいずれかを選んでドラッグします。 
   
   ![テキスト ボックスを配置する](media/power-bi-reports-add-text-and-shapes/textboxsmaller.gif)

5. テキスト ボックスを選択したまま、 **[視覚化]** ウィンドウでさらに書式設定を追加します。 この例では背景や罫線を書式設定しました。 サイズと位置を厳密に指定したテキスト ボックスを作成することもできます。  

   ![テキスト ボックスの書式設定](media/power-bi-reports-add-text-and-shapes/power-bi-borders.png)

6. テキスト ボックスを閉じるには、レポート キャンバス上の任意の空白領域を選びます。 

7. ピン留めアイコン  ![ピン アイコンをクリックまたはタップします。](media/power-bi-reports-add-text-and-shapes/pbi_pintile.png) を選んで、テキスト ボックスをダッシュボードにピン留めします。 

## <a name="add-a-shape-to-a-report"></a>レポートに図形を追加する
1. レポート キャンバス内の任意の位置にカーソルを置いて、 **[図形]** を選びます。
   
   ![図形を選択する](media/power-bi-reports-add-text-and-shapes/power-bi-shapes.png)
2. ドロップダウン リストで、レポート キャンバスに追加する図形を選択します。 この例では、合計売上の分散が最も高いバブルに注意を向ける矢印を追加してみましょう。 
   
   **[図形の書式設定]** ウィンドウで、図形をカスタマイズします。 この例では、90° 回転された暗い赤い境界線付きの赤い矢印を作成しました。
   
   ![図形をカスタマイズする](media/power-bi-reports-add-text-and-shapes/power-bi-arrrow.png)
3. 図形を配置するには、上部にある灰色の領域を選んでドラッグします。 図形のサイズを変更するには、アウトライン ハンドルのいずれかを選んでドラッグします。 テキスト ボックスと同様に、サイズと位置を厳密に指定した図形を作成することもできます。

   > [!NOTE]
   > 図形をダッシュボードにピン留めすることはできませんが、[ライブ ページをピン留め](service-dashboard-pin-live-tile-from-report.md)するときに図形をビジュアルの 1 つにすることはできます。 
   > 
   > 

## <a name="next-steps"></a>次のステップ

次の記事にも興味をもたれるかもしれません。

* [テキスト ボックスへのハイパーリンクの追加](service-add-hyperlink-to-text-box.md)
* [Power BI サービスのデザイナー向けの基本的な概念](../fundamentals/service-basic-concepts.md)
* [Power BI レポートの図形、画像、およびアイコンを使用した分析を改善するためのヒント](../guidance/report-tips-shapes-images-icons.md)
* 他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。
