---
title: Power BI でのレポートへのフィルターの追加
description: Power BI でレポートにページ フィルター、視覚化フィルター、またはレポート フィルターを追加する
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 02/12/2021
LocalizationGroup: Reports
ms.openlocfilehash: f7c17b810070a79c9f4a9f4a0756cbcaa8831f18
ms.sourcegitcommit: 00e3eb2ec4f18d48a73cfd020bb42d08e859ad06
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/16/2021
ms.locfileid: "100531809"
---
# <a name="add-a-filter-to-a-report-in-power-bi"></a>Power BI でのレポートへのフィルターの追加

この記事では、Power BI でレポートに視覚化フィルター、ページ フィルター、またはレポート フィルターを追加する方法について説明します。 フィルターを追加するには、レポートを編集できる必要があります。 この記事に含まれている例は Power BI サービスのものですが、手順は Power BI Desktop でもほぼ同じです。 概要については、 最初に「[Power BI レポートのフィルターと強調表示](power-bi-reports-filters-and-highlighting.md)」を参照してください。

![新しいフィルター エクスペリエンス](media/power-bi-report-add-filter/power-bi-filter-reading.png)

Power BI には、手動と自動からドリルスルーとパススルーまで、さまざまな種類のフィルターが多数用意されています。 [さまざまなフィルターの種類](power-bi-report-filter-types.md)に関する記事をご覧ください。

フィルターを追加した後は、望ましい外見と動作になるように [Power BI レポートでフィルターを書式設定する](power-bi-report-filter.md)ことができます。

## <a name="filters-in-editing-view-or-reading-view"></a>編集ビューまたは読み取りビューでのフィルター
2 つの異なるビューでレポートを操作できます。読み取りビューと編集ビューです。 この記事では、レポートの **編集ビュー** でフィルターを作成する方法について説明します。  読み取りビューでのフィルターについて詳しくは、[レポートの読み取りビューのフィルターとの対話](../consumer/end-user-report-filter.md)に関する記事をご覧ください。

フィルターは "*永続的*" であるため、ユーザーがレポートから離れても、Power BI によってフィルター、スライサー、ユーザーが行ったその他のデータ ビューの変更は保持されます。 そのため、レポートに戻ったとき、前回終了したところから再開できます。 フィルターの変更内容を残したくない場合は、上部のメニュー バーから **[既定値にリセット]** を選択します。

:::image type="content" source="../consumer/media/end-user-report-filter/power-bi-reset-icon.png" alt-text="[既定値にリセット] アイコン。":::

レポートの作成者がレポートと共に保存したすべてのフィルターは、すべてのレポート閲覧者に対して "*既定のフィルター状態*" になることに注意してください。 **[既定値にリセット]** を選択すると、その状態に戻ります。

## <a name="levels-of-filters-in-the-filters-pane"></a>[フィルター] ウィンドウのフィルターのレベル
Power BI Desktop と Power BI サービスのどちらを使用しているかに関係なく、[フィルター] ペインはレポート キャンバスの右側に表示されます。 フィルター ウィンドウが表示されない場合は、右上隅にある ">" アイコンを選択して展開してください。

レポートには、視覚化レベル、ページ レベル、レポート レベルという 3 つの異なるレベルでフィルターを設定できます。 この記事では、各レベルを設定する方法について説明します。

## <a name="add-a-filter-to-a-visual"></a>ビジュアルにフィルターを追加する
視覚化には、2 種類のフィルターがあります。
視覚化レベルのフィルターは、2 つの方法で視覚化に追加できます。 

* 視覚化内のフィールドは、自動的にその視覚化に対するフィルターになります。 
* レポート デザイナーは、まだ視覚化ではないフィールドを識別し、そのフィールドを **視覚化レベル フィルター** バケットに直接追加できます。
 
ところで、この記事では小売りの分析サンプルを使用するので、よろしければインストールして同じように操作してみてください。 [小売りの分析のサンプル](sample-retail-analysis.md#get-the-content-pack-for-this-sample) コンテンツ パックをインストールします。

### <a name="filter-with-a-field-thats-not-in-the-visual"></a>ビジュアルに含まれていないフィールドでフィルター処理する

1. Power BI サービスで、 **[その他のオプション (...)]**  >  **[編集]** を選択して、編集ビューでレポートを開きます。
   
   ![レポートの編集ボタン。](media/power-bi-report-add-filter/power-bi-edit-view.png)

2. まだ開いていない場合は、[視覚化]、[フィルター]、および [フィールド] ペインを開きます。
   
   ![[視覚化]、[フィルター]、[フィールド] のウィンドウ](media/power-bi-report-add-filter/power-bi-display-panes.png)

3. ビジュアルを選んでアクティブにします。 この場合は [Overview] ページの散布図です。 視覚エフェクト内のすべてのフィールドが **[視覚化]** ペインに表示されます。 それらは **[フィルター]** ペインの **[Filters on this visual]\(この視覚エフェクトでのフィルター\)** 見出しの下にも表示されます。
   
   ![ビジュアル レベル フィルターを選択](media/power-bi-report-add-filter/power-bi-default-visual-filter.png)
  
1. [フィールド] ウィンドウで新しいビジュアル レベル フィルターとして追加するフィールドを選び、 **[ビジュアル レベル フィルター]** 領域までドラッグします。  この例では、 **[Category]** を、 **[Filters on this visual]\(この視覚エフェクトでのフィルター\)** の下の **[ここにデータ フィールドを追加してください]** にドラッグします。
     
    ![[フィルター] ウィンドウにフィールドを追加](media/power-bi-report-add-filter/power-bi-search-add-visual-filter.png)

    **[Category]** は視覚エフェクト自体に追加されるのでは "*ない*" ことがわかります。
     
1. **Kids** を選択します。 散布図はフィルター処理されますが、他の視覚エフェクトは同じままです。
     
    ![新しいフィールドに基づいてフィルター処理された値が反映されている散布図のスクリーンショット。](media/power-bi-report-add-filter/power-bi-search-visual-filter-results-2.png)

    レポートをこのフィルターと共に保存すると、レポート閲覧者が読み取りビューで **Category** フィルターを操作して、値を選択したりクリアしたりできるようになります。
    
    "*数値列*" をフィルター ウィンドウにドラッグしてビジュアルレベルのフィルターを作成すると、フィルターは "*基になるデータの行*" に適用されます。 たとえば、**UnitCost** フィールドにフィルターを追加し、それを **UnitCost** > 20 に設定した場合、ビジュアルに表示されているデータ ポイントの合計単価に関係なく、単価が 20 を超えた製品行のデータのみが表示されます。

## <a name="add-a-filter-to-an-entire-page"></a>ページ全体にフィルターを追加する

ページ レベル フィルターを追加して、ページ全体をフィルター処理することもできます。

1. Power BI サービスで、小売りの分析レポートを開き、 **[District Monthly Sales]\(地区の毎月の売上\)** ページに移動します。 

2. **[...]**  >  **[レポートの編集]** を選択し、編集ビューでレポートを開きます。
   
   ![レポートの編集ボタン](media/power-bi-report-add-filter/power-bi-edit-view.png)

2. まだ開いていない場合は、[視覚化]、[フィルター]、および [フィールド] ペインを開きます。

3. [フィールド] ウィンドウで新しいページ レベル フィルターとして追加するフィールドを選び、 **[ページ レベル フィルター]** 領域までドラッグします。  
4. フィルターを適用する値を選び、フィルター処理コントロールとして **基本** または **高度** を設定します。
   
   ページ上のすべての視覚化が、変更を反映するように再描画されます。
   
    レポートをフィルターとともに保存すると、レポート閲覧者が読み取りビューでフィルターと対話でき、値を選んだりクリアしたりすることができます。

## <a name="add-a-report-level-filter-to-filter-an-entire-report"></a>レポート レベル フィルターを追加して、レポート全体をフィルター処理する

1. **[レポートの編集]** を選んで、編集ビューでレポートを開きます。
   
   ![レポートの編集ボタン](media/power-bi-report-add-filter/power-bi-edit-view.png)

2. [視覚化] と [フィルター] のウィンドウと [フィールド] ウィンドウをまだ開いていない場合は、開きます。
3. [フィールド] ウィンドウで新しいレポート レベル フィルターとして追加するフィールドを選び、 **[レポート レベル フィルター]** 領域までドラッグします。  
4. フィルターする値を選択します。

    アクティブ ページおよびレポート内のすべてのページ上のビジュアルに、新しいフィルターが反映されます。 レポートをフィルターとともに保存すると、レポート閲覧者が読み取りビューでフィルターと対話でき、値を選んだりクリアしたりすることができます。

1. 戻る矢印を選んで、前のレポート ページに戻ります。

## <a name="considerations-and-troubleshooting"></a>考慮事項とトラブルシューティング

- [フィールド] ペインが表示されない場合は、レポートが[編集ビュー](service-interact-with-a-report-in-editing-view.md)になっていることを確認してください。
- フィルターに多くの変更を加えた後で、既定の設定に戻す場合は、上部のメニュー バーから **[既定値にリセット]** を選択します。 覚えておいてください:レポート作成者がレポートを保存するときに適用されていたすべてのフィルターは、既定のフィルター設定に "*なります*"。

## <a name="next-steps"></a>次のステップ

[Power BI レポートでフィルターを書式設定する](power-bi-report-filter.md)

[レポート フィルター ウィンドウの使用方法](../consumer/end-user-report-filter.md)

[レポート内のフィルターと強調表示](power-bi-reports-filters-and-highlighting.md)

[Power BI で使用できるさまざまなフィルター](power-bi-report-filter-types.md)

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。
