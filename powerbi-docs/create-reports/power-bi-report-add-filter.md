---
title: Power BI でのレポートへのフィルターの追加
description: Power BI でレポートにページ フィルター、視覚化フィルター、またはレポート フィルターを追加する
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 10/20/2019
LocalizationGroup: Reports
ms.openlocfilehash: 113370dd6b3aa19546f1facada6abc07c12b9d1a
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96389117"
---
# <a name="add-a-filter-to-a-report-in-power-bi"></a>Power BI でのレポートへのフィルターの追加

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

この記事では、Power BI でレポートにページ フィルター、視覚エフェクト フィルター、レポート フィルター、ドリルスルー フィルターを追加する方法を説明します。 この記事の例は、Power BI サービスのものです。 Power BI Desktop でも手順はほとんど同じです。

**ご存知でしたか?** Power BI には新しいフィルター エクスペリエンスがあります。 詳細については、[Power BI レポートの新しいフィルター エクスペリエンス](power-bi-report-filter.md)に関する記事をご覧ください。

![新しいフィルター エクスペリエンス](media/power-bi-report-add-filter/power-bi-filter-reading.png)

Power BI には、手動と自動からドリルスルーとパススルーまで、さまざまな種類のフィルターが多数用意されています。 [さまざまなフィルターの種類](power-bi-report-filter-types.md)に関する記事をご覧ください。

## <a name="filters-in-editing-view-or-reading-view"></a>編集ビューまたは読み取りビューでのフィルター
レポートの操作は、読み取りビューと編集ビューの 2 種類のビューで行うことができます。 使用できるフィルター処理機能は、どのビューを使用しているかによって異なります。 詳しくは、「[Power BI レポートのフィルターと強調表示について](power-bi-reports-filters-and-highlighting.md)」をご覧ください。

この記事では、レポートの **編集ビュー** でフィルターを作成する方法について説明します。  読み取りビューでのフィルターについて詳しくは、[レポートの読み取りビューのフィルターとの対話](../consumer/end-user-report-filter.md)に関する記事をご覧ください。

フィルターは "*永続的*" であるため、ユーザーがレポートから離れても、Power BI によってフィルター、スライサー、ユーザーが行ったその他のデータ ビューの変更は保持されます。 そのため、レポートに戻ったとき、前回終了したところから再開できます。 フィルターの変更を残さない場合は、上部のメニュー バーから **[既定値にリセット]** を選択します。

![永続的フィルター ボタン](media/power-bi-report-add-filter/power-bi-reset-to-default.png)

## <a name="levels-of-filters-in-the-filters-pane"></a>[フィルター] ウィンドウのフィルターのレベル
Desktop と Power BI サービスのどちらを使用しているかに関係なく、フィルター ウィンドウはレポート キャンバスの右側に表示されます。 フィルター ウィンドウが表示されない場合は、右上隅にある ">" アイコンを選択して展開してください。

レポートには、ビジュアル レベル フィルター、ページ レベル フィルター、レポート レベル フィルターの 3 つの異なるレベルでフィルターを設定できます。 また、ドリルスルー フィルターを設定することもできます。 この記事では、さまざまなレベルについて説明します。

![読み取りビューのフィルター ウィンドウ](media/power-bi-report-add-filter/power-bi-add-filter-reading-view.png)

## <a name="add-a-filter-to-a-visual"></a>ビジュアルにフィルターを追加する
ビジュアル レベル フィルターは、2 つの方法で特定のビジュアルに追加できます。 

* 視覚エフェクトによって既に使われているフィールドにフィルターを追加します。
* 視覚エフェクトによってまだ使われていないフィールドを識別し、そのフィールドを **ビジュアル レベル フィルター** バケットに直接追加します。


ところで、この手順では小売りの分析サンプルを使用するので、よろしければダウンロードして同じように操作してみてください。 [小売りの分析のサンプル](sample-retail-analysis.md#get-the-content-pack-for-this-sample) コンテンツ パックをダウンロードします。

### <a name="filter-the-fields-in-the-visual"></a>ビジュアルでフィールドをフィルター処理する

1. **[その他のオプション (...)]**  >  **[レポートの編集]** を選択して、編集ビューでレポートを開きます。
   
   ![レポートの編集ボタン](media/power-bi-report-add-filter/power-bi-edit-view.png)

2. 視覚化およびフィルター ウィンドウとフィールド ウィンドウがまだ開いていない場合は開きます。
   
   ![[視覚化]、[フィルター]、[フィールド] のウィンドウ](media/power-bi-report-add-filter/power-bi-display-panes.png)
3. ビジュアルを選んでアクティブにします。 ビジュアルで使用されているすべてのフィールドが **[フィールド]** ウィンドウに表示され、 **[フィルター]** ウィンドウの **[ビジュアル レベル フィルター]** の見出しにも一覧表示されます。
   
   ![ビジュアル レベル フィルターを選択](media/power-bi-report-add-filter/power-bi-default-visual-filter.png)
4. この時点で、視覚化によって既に使われているフィールドにフィルターを追加します。 
   
    **[ビジュアル レベル フィルター]** 領域まで下にスクロールし、矢印を選んでフィルター処理するフィールドを展開します。 この例では **StoreNumberName** をフィルター処理します。
     
    ![フィルターを展開する矢印](media/power-bi-report-add-filter/power-bi-visual-level-filter.png) 
    
    フィルター処理コントロールとして **基本**、**高度**、または **上位 N** を設定します。 この例では、基本フィルターで **cha** を検索し、これら 5 つのストアを選択します。
     
    ![基本フィルターでの検索](media/power-bi-report-add-filter/power-bi-search-filter.png) 
   
    ビジュアルに新しいフィルターが反映されます。 レポートをフィルターとともに保存すると、レポート閲覧者は、フィルター処理されたビジュアルが最初に表示され、読み取りビューでフィルターと対話して、値を選んだりクリアしたりすることができます。
     
    ![値のフィルター処理が反映された棒グラフのスクリーンショット。](media/power-bi-report-add-filter/power-bi-search-visual-filter-results.png)
    
    フィールドが集計される (sum、average、count など) ビジュアルで使用されるフィールドに対してフィルターを使用すると、各データ ポイントの "*集計*" 値に基づいてフィルター処理が行われます。 したがって、上記のビジュアルに "**今年の売上 > 500,000**" というフィルターを適用することは、**13 - Charleston Fashion Direct** データ ポイントのみが結果に表示されることを意味します。 [モデル メジャー](../transform-model/desktop-measures.md)に対するフィルターは、常にデータ ポイントの集計値に適用されます。

### <a name="filter-with-a-field-thats-not-in-the-visual"></a>ビジュアルに含まれていないフィールドでフィルター処理する

次に、新しいフィールドをビジュアル レベル フィルターとして視覚エフェクトに追加します。
   
1. [フィールド] ウィンドウで新しいビジュアル レベル フィルターとして追加するフィールドを選び、 **[ビジュアル レベル フィルター]** 領域までドラッグします。  この例では、**District Manager** を **[ビジュアル レベル フィルター]** バケットにドラッグし、「**an**」を検索して、それらの 3 人のマネージャーを選択します。
     
    ![[フィルター] ウィンドウにフィールドを追加](media/power-bi-report-add-filter/power-bi-search-add-visual-filter.png)

    **District Manager** は視覚エフェクト自体に追加されるのでは "*ない*" ことに注意してください。 視覚化はまだ **[StoreNumberName]** を軸とし、 **[This Year Sales (今年の売上)]** を値として構成されています。  
     
    ![フィールドはビジュアルに含まれていない](media/power-bi-report-add-filter/power-bi-visualization.png)

    また、視覚エフェクト自体は、指定した店舗でのこれらのマネージャーの今年の売上だけを表示するようにフィルター処理されます。
     
    ![新しいフィールドに基づいた値のフィルター処理が反映された棒グラフのスクリーンショット。](media/power-bi-report-add-filter/power-bi-search-visual-filter-results-2.png)

    レポートをフィルターとともに保存すると、レポート閲覧者は読み取りビューで **District Manager** フィルターを操作して、値を選んだりクリアしたりすることができます。
    
    "*数値列*" をフィルター ウィンドウにドラッグしてビジュアルレベルのフィルターを作成すると、フィルターは "*基になるデータの行*" に適用されます。 たとえば、**UnitCost** フィールドにフィルターを追加し、それを **UnitCost** > 20 に設定した場合、ビジュアルに表示されているデータ ポイントの合計単価に関係なく、単価が 20 を超えた製品行のデータのみが表示されます。

## <a name="add-a-filter-to-an-entire-page"></a>ページ全体にフィルターを追加する

ページ レベル フィルターを追加して、ページ全体をフィルター処理することもできます。

1. Power BI サービスで、小売りの分析レポートを開き、 **[District Monthly Sales]\(地区の毎月の売上\)** ページに移動します。 

2. **[...]**  >  **[レポートの編集]** を選択し、編集ビューでレポートを開きます。
   
   ![レポートの編集ボタン](media/power-bi-report-add-filter/power-bi-edit-view.png)
2. 視覚化およびフィルター ウィンドウとフィールド ウィンドウがまだ開いていない場合は開きます。
3. [フィールド] ウィンドウで新しいページ レベル フィルターとして追加するフィールドを選び、 **[ページ レベル フィルター]** 領域までドラッグします。  
4. フィルターを適用する値を選び、フィルター処理コントロールとして **基本** または **高度** を設定します。
   
   ページ上のすべての視覚化が、変更を反映するように再描画されます。
   
   ![フィルターを追加して値を選択](media/power-bi-report-add-filter/filterpage.gif)

    レポートをフィルターとともに保存すると、レポート閲覧者が読み取りビューでフィルターと対話でき、値を選んだりクリアしたりすることができます。

## <a name="add-a-drillthrough-filter"></a>ドリルスルー フィルターを追加する
Power BI サービスと Power BI Desktop のドリルスルーでは、サプライヤー、顧客、メーカーなど、特定のエンティティに注目した "*ドリルスルー先*" レポート ページを作成できます。 ユーザーは、他のレポート ページでそのエンティティのデータ ポイントを右クリックして、フォーカスされたページにドリルスルーできます。

### <a name="create-a-drillthrough-filter"></a>ドリルスルー フィルターを作成する
作業を進めるために、[お客様の収益性のサンプル](sample-customer-profitability.md#get-the-content-pack-for-this-sample)をダウンロードします。 Executive ビジネス領域に注目したページを作成します。

1. Power BI サービスで、小売りの分析レポートを開き、 **[District Monthly Sales]\(地区の毎月の売上\)** ページに移動します。

2. **[その他のオプション (...)]**  >  **[レポートの編集]** を選択して、編集ビューでレポートを開きます。
   
   ![レポートの編集ボタン](media/power-bi-report-add-filter/power-bi-edit-view.png)

1. レポートに新しいページを追加し、「**Team Executive**」という名前を付けます。 このページが "*ドリルスルー先*" になります。
2. チーム エグゼクティブ ビジネス分野の主要指標を追跡するための視覚化を追加します。    
3. **Executives** テーブルから、**Executive** をドリルスルー フィルター ウェルにドラッグします。    
   
    ![ドリルスルー フィルターに値を追加](media/power-bi-report-add-filter/power-bi-drillthrough-filter.png)
   
    レポート ページに戻る矢印が追加されることに注意してください。  戻る矢印を選ぶと、"*ドリルスルー元*" のレポート ページ (ドリルスルーを選んだときのページ) に戻ります。 編集ビューで、Ctrl キーを押しながら戻る矢印を選択します。
   
     ![戻る矢印](media/power-bi-report-add-filter/power-bi-back-arrow.png)

### <a name="use-the-drillthrough-filter"></a>ドリルスルー フィルターを使う
ドリルスルー フィルターのしくみを見てみましょう。

1. **[Team Scorecard]** レポート ページから始めます。    
2. Andrew Ma が自分のデータだけにフィルター処理された [Team Executive] レポート ページを見たいものとします。  左上の面グラフで任意の緑のデータ ポイントを右クリックして、[ドリルスルー] メニュー オプションを開きます。
   
    ![ドリルスルー アクションの開始](media/power-bi-report-add-filter/power-bi-drillthrough.png)
3. **[ドリルスルー] > [Team Executive]** を選んで、 **[Team Executive]** という名前のレポート ページにドリルスルーします。 このページは、右クリックしたデータ ポイント (この場合は Andrew Ma) に関する情報を表示するようにフィルター処理されています。 元のページのすべてのフィルターは、ドリルスルー レポート ページに適用されます。  
   
    ![ドリルスルー アクションの選択](media/power-bi-report-add-filter/power-bi-drillthrough-executive.png)

## <a name="add-a-report-level-filter-to-filter-an-entire-report"></a>レポート レベル フィルターを追加して、レポート全体をフィルター処理する

1. **[レポートの編集]** を選んで、編集ビューでレポートを開きます。
   
   ![レポートの編集ボタン](media/power-bi-report-add-filter/power-bi-edit-view.png)

2. [視覚化] と [フィルター] のウィンドウと [フィールド] ウィンドウをまだ開いていない場合は、開きます。
3. [フィールド] ウィンドウで新しいレポート レベル フィルターとして追加するフィールドを選び、 **[レポート レベル フィルター]** 領域までドラッグします。  
4. フィルターする値を選択します。

    アクティブ ページおよびレポート内のすべてのページ上のビジュアルに、新しいフィルターが反映されます。 レポートをフィルターとともに保存すると、レポート閲覧者が読み取りビューでフィルターと対話でき、値を選んだりクリアしたりすることができます。

1. 戻る矢印を選んで、前のレポート ページに戻ります。

## <a name="considerations-and-troubleshooting"></a>考慮事項とトラブルシューティング

- [フィールド] ウィンドウが表示されない場合は、レポートが[編集ビュー](service-interact-with-a-report-in-editing-view.md)になっていることを確認してください。    
- フィルターに多くの変更を加えた後で、レポート作成者の初期設定に戻す場合、一番上のメニュー バーから **[既定値にリセット]** を選択します。

## <a name="next-steps"></a>次のステップ
[レポート フィルター ウィンドウの使用方法](../consumer/end-user-report-filter.md)

[レポート内のフィルターと強調表示](power-bi-reports-filters-and-highlighting.md)

[Power BI で使用できるさまざまなフィルター](power-bi-report-filter-types.md)

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。
