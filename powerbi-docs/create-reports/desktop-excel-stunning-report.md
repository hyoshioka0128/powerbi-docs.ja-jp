---
title: チュートリアル:Power BI Desktop で Excel ブックから魅力的なレポートを作成する
description: このチュートリアルでは、Excel ブックから魅力的なレポートをすばやく作成する方法について説明します。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: tutorial
ms.date: 10/13/2020
LocalizationGroup: Data from files
ms.openlocfilehash: b984c0f6ebee6cdcc9982956701f3a112be74ab7
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96413198"
---
# <a name="tutorial-from-excel-workbook-to-stunning-report-in-power-bi-desktop"></a>チュートリアル:Power BI Desktop で Excel ブックから魅力的なレポートを作成する

このチュートリアルでは、開始から終了まで 20 分で美しいレポートを作成します。 

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-excel-formatted-report.png" alt-text="完成した Power BI レポートのスクリーンショット。"::: 

上司は、最新の売上高に関するレポートを見たいと考えています。 次の内容を含むエグゼクティブ サマリを要求してきました。 

- 最も利益が多かったのは、どの年のどの月か? 
- 会社が最も成功を収めたのは、どこ (国別) か? 
- 会社が投資を継続する必要があるのは、どの製品とセグメントか? 

サンプルの財務ブックを使用すると、このレポートを即座に作成できます。 最終的なレポートは次のようになります。 それでは始めましょう。 

このチュートリアルで学習する内容は次のとおりです。

> [!div class="checklist"]
> * サンプル データを 2 つの異なる方法でダウンロードする
> * 変換を数回行ってデータを準備する
> * タイトル、3 つのビジュアル、スライサーを含むレポートを作成する
> * 仕事仲間と共有できるように、レポートを Power BI サービスに発行する

## <a name="prerequisites"></a>前提条件

- 開始する前に、[Power BI Desktop をダウンロードする](https://powerbi.microsoft.com/desktop/)必要があります。
- レポートを Power BI サービスに発行する予定があり、まだサインアップしていない場合は、[無料試用版にサインアップ](https://app.powerbi.com/signupredirect?pbi_source=web)します。

## <a name="get-data"></a>データを取得する 

このチュートリアルのデータは、2 つの方法のいずれかを使用して取得できます。

### <a name="get-data-in-power-bi-desktop"></a>Power BI Desktop でデータを取得する

Power BI Desktop を開いたときに、空のキャンバスから **[Try a sample dataset]\(サンプル データセットを試す\)** を選択します。

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-desktop-canvas-sample-dataset.png" alt-text="キャンバスでの [Try a sample dataset]\(サンプル データセットを試す\) のスクリーンショット。"::: 

Power BI Desktop からこのチュートリアルに移動してきた場合は、 **[データの読み込み]** を選択します。

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-two-ways-load-data.png" alt-text="サンプル データを使用する 2 つの方法 > [データの読み込み] のスクリーンショット。":::

### <a name="download-the-sample"></a>サンプルのダウンロード

サンプル ブックを直接ダウンロードすることもできます。 

1. [財務サンプルの Excel ブック](https://go.microsoft.com/fwlink/?LinkID=521962)をダウンロードします。
1. Power BI Desktop を開きます。
1. **[ホーム]** リボンの **[データ]** セクションで、 **[Excel]** を選択します。
1. サンプルのブックを保存した場所に移動し、 **[開く]** を選択します。

## <a name="prepare-your-data"></a>データの準備 

**[ナビゲーター]** には、データを "*変換する*" または "*読み込む*" オプションがあります。 [ナビゲーター] には、データの範囲が正しいことを確認できるように、データのプレビューが表示されます。 数値データ型は斜体で示されます。 変更する必要がある場合は、データを読み込む前に変換します。 後で見やすいように視覚化するために、ここでデータを変換する必要があります。 変換を行うたびに、 **[クエリの設定]** の **[適用したステップ]** の一覧にそれが追加されます 

1. **[財務]** テーブルを選択し、 **[データの変換]** を選択します。 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-financial-navigator.png" alt-text="財務サンプル データを表示した Power BI ナビゲーターのスクリーンショット。"::: 

1. **[販売数]** 列を選択します。 **[ホーム]** タブで、 **[データ型]** を選択し、 **[整数]** を選択します。 **[現在のものを置換]** を選択して、列の型を変更します。 

    ユーザーが行うデータ クリーニングの手順で最も頻度が高いのは、データ型の変更です。 この場合、販売数は 10 進数形式です。 0\.2 や 0.5 の販売数は意味がありません。 では、それを整数に変更しましょう。 

    :::image type="content" source="media/desktop-excel-stunning-report/power-query-whole-number.png" alt-text="10 進数から整数に変更しているときのスクリーンショット。"::: 

1. **[セグメント]** 列を選択します。 **[変換]** タブで、 **[書式]** 、 **[大文字]** の順に選択します。

    さらに、後でグラフにしたときにセグメントを見やすくする必要があります。 では、[セグメント] 列の書式を設定しましょう。 

     :::image type="content" source="media/desktop-excel-stunning-report/power-query-upper-case.png" alt-text="見出しを小文字から大文字に変更しているときのスクリーンショット。":::

1. 次に、列名を **[月の名前]** から **[月]** に短縮します。 **[月の名前]** 列をダブルクリックして、列名を **[月]** に変更します。  

     :::image type="content" source="media/desktop-excel-stunning-report/power-query-month-name.png" alt-text="列名を短縮しているときのスクリーンショット。":::

1. **[製品]** 列で、ドロップダウンを選択し、 **[Montana]** の横にあるボックスをオフにします。 

     Montana 製品は先月に製造中止になっていることがわかっているので、混乱を避けるために、このデータをフィルター処理してレポートから除外する必要があります。 

     :::image type="content" source="media/desktop-excel-stunning-report/power-query-montana.png" alt-text="Montana の値を削除しているときのスクリーンショット。":::

1. 各変換が、 **[クエリの設定]** の **[適用したステップ]** の一覧に追加されたことがわかります。

    :::image type="content" source="media/desktop-excel-stunning-report/power-query-applied-steps.png" alt-text="[適用したステップ] の一覧のスクリーンショット。":::

1. **[ホーム]** タブに戻り、 **[閉じて適用]** を選択します。 データは、レポートを作成するための準備がほとんど整いました。 

    [フィールド] の一覧にシグマ記号が表示されているのがわかりますか? Power BI によって、これらのフィールドが数値であることが検出されました。 さらに、Power BI によって、カレンダー記号が付いたデータ フィールドも示されます。

     :::image type="content" source="media/desktop-excel-stunning-report/power-bi-fields-list-sigmas-date.png" alt-text="数値フィールドと日付フィールドを含む [フィールド] の一覧のスクリーンショット。":::

### <a name="extra-credit-write-a-measure-in-dax"></a>追加の手順: DAX でメジャーを作成する

*DAX* 数式言語による "*メジャー*" の作成は、非常に強力なデータ モデリングです。 DAX の詳細については、Power BI のドキュメントを参照してください。 ここでは、基本的なメジャーを作成して、2 つのテーブルを結合します。 

1. 左側にある **[データ ビュー]** を選択します。 
 
    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-data-view.png" alt-text="[データ ビュー] アイコンのスクリーンショット。":::

1. **[ホーム]** リボンで、 **[新しいテーブル]** を選択します。 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-new-table.png" alt-text="[新しいテーブル] アイコンのスクリーンショット。":::

1. 次のメジャーを入力して、2013 年 1 月 1 日から 2014 年 12 月 31 日までのすべての日付を含むカレンダー テーブルを作成します。  

    `Calendar = CALENDAR(DATE(2013,01,01),Date(2014,12,31))` 

2. チェック マークを選択してコミットします。

     :::image type="content" source="media/desktop-excel-stunning-report/power-bi-dax-expression.png" alt-text="DAX 式のスクリーンショット。":::

1. 左側にある **[モデル ビュー]** を選択します。 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-model-view.png" alt-text="[モデル ビュー] アイコンのスクリーンショット。":::

1. **[Date]** フィールドを財務テーブルからカレンダー テーブルの **[Date]** フィールドにドラッグして、テーブルを結合し、これらの間の "*リレーションシップ*" を作成します。  

     :::image type="content" source="media/desktop-excel-stunning-report/power-bi-date-relationship.png" alt-text="[Date] フィールド間のリレーションシップのスクリーンショット。":::

## <a name="build-your-report"></a>レポートの構築 

データの変換と読み込みが完了したので、次にレポートを作成します。 右側にある [フィールド] ウィンドウに、作成したデータ モデルのフィールドが表示されます。 

一度に 1 つずつビジュアルを作成して、最終的なレポートを完成させましょう。 

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-report-by-numbers.png" alt-text="レポートのすべての要素を番号で示したスクリーンショット。":::

### <a name="visual-1-add-a-title"></a>ビジュアル 1: タイトルの追加 

1. **[挿入]** リボンで、 **[テキスト ボックス]** を選択します。 "エグゼクティブ サマリ - 財務レポート" と入力します。 
1. 入力したテキストを選択します。 フォント サイズを 20 にして太字に設定します。 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-title-executive-summary.png" alt-text="タイトルの書式を設定しているときのスクリーンショット。":::

1. [視覚化] ウィンドウで、 **[背景]** を **[オフ]** に切り替えます。 
1. 1 行に収まるようにボックスのサイズを変更します。 

### <a name="visual-2-profit-by-date"></a>ビジュアル 2: 日付別利益 

利益が最も多かった月と年がわかるように折れ線グラフを作成します。 

1. [フィールド] ウィンドウの **[Profit]** フィールドをレポート キャンバスの空白領域にドラッグします。 Power BI では、既定により、縦棒が 1 つある縦棒グラフ (利益) が表示されます。 
1. **[Date]** フィールドを同じビジュアルにドラッグします。 Power BI によって、縦棒グラフが更新され、2 年分の利益が年別に表示されます。

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-column-year.png" alt-text="利益縦棒グラフのスクリーンショット。":::

1. [視覚化] ウィンドウの **[フィールド]** セクションで、 **[軸]** の値のドロップダウンを選択します。 **[日付]** を **[日付の階層]** から **[日付]** に変更します。

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-date-hierarchy.png" alt-text="[日付の階層] から [日付] に変更しているときのスクリーンショット。":::

    Power BI によって、縦棒グラフが更新され、毎月の利益が表示されます。

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-column-month.png" alt-text="月別の縦棒グラフのスクリーンショット。":::

1. [視覚化] ウィンドウで、視覚化の種類を **[折れ線グラフ]** に変更します。 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-profit-date-line-chart.png" alt-text="縦棒から横棒グラフへの変更を示すスクリーンショット。":::

    以上で、2014 年 12 月が最も利益が多かったことが簡単にわかるようになりました。

### <a name="visual-3-profit-by-country"></a>ビジュアル 3: 国別の利益 

どの国が最も利益が多かったかを示すマップを作成します。

1. [フィールド] ウィンドウの **[Country]** フィールドをレポート キャンバスの空白領域にドラッグして、マップを作成します。
1. **[Profit]** フィールドをマップにドラッグします。

    Power BI によって、各場所の相対的な利益を表すバブルの表示された地図ビジュアルが作成されます。 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-map-visual.png" alt-text="マップ チャートを作成しているときのスクリーンショット。":::

    ヨーロッパは、北米より好調であるように見えます。 

### <a name="visual-4-sales-by-product-and-segment"></a>ビジュアル 4: 製品およびセグメント別の売上 

投資する会社とセグメントを決定するための横棒グラフを作成します。

1. 作成した 2 つのグラフをドラッグして、キャンバスの上半分に横に並べて表示します。 キャンバスの左側に少しスペースを取っておきます。 
1. レポート キャンバスの下半分の空白領域を選択します。 

1. [フィールド] ウィンドウで、 **[Sales]** 、 **[Product]** 、 **[Segment]** フィールドを選択します。 

    Power BI によって、集合縦棒グラフが自動的に作成されます。 

1. 上の 2 つのグラフの下にあるスペースを埋めるのに十分な幅になるように、グラフをドラッグします。

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-clustered-column-chart.png" alt-text="集合縦棒グラフのスクリーンショット。":::

    会社は引き続き Paseo 製品に投資し、中小企業と政府のセグメントをターゲットにする必要があるように見えます。  

### <a name="visual-5-year-slicer"></a>ビジュアル 5: 年のスライサー 

スライサーは、レポート ページのビジュアルを特定の選択範囲にフィルター処理するための重要なツールです。 この場合、各月および年の業績を絞り込むためのスライサーを作成できます。  

1. [フィールド] ウィンドウで、 **[日付]** フィールドを選択し、キャンバスの左側の空白領域にドラッグします。 
2. [視覚化] ウィンドウで、 **[スライサー]** を選択します。 
3. [視覚化] ウィンドウの [フィールド] セクションで、 **[フィールド]** のドロップダウンを選択します。 [四半期] と [日] を削除して、[年] と [月] のみを残します。 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-date-hierarchy-trim.png" alt-text="[日付の階層] を変更しているときのスクリーンショット。":::

4. 各年を展開し、ビジュアルのサイズを変更して、すべての月が表示されるようにします。

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-hierarchy-date-slicer.png" alt-text="日付の階層スライサーのスクリーンショット。":::

以上で、上司が 2013 年のデータのみを表示するように要求した場合、スライサーを使用して、年を切り替えたり、各年の特定の月に切り替えたりすることができます。 

### <a name="extra-credit-format-the-report"></a>追加の手順: レポートを書式設定する

このレポートに対して何らかの淡色の書式設定を行って洗練さを高める必要がある場合、以下に簡単な手順をいくつか示します。 

**テーマ**

- **[表示]** リボンで、テーマを **[エグゼクティブ]** に変更します。  

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-theme-executive.png" alt-text="[エグゼクティブ] テーマを選択しているときのスクリーンショット。"::: 

**ビジュアルを整理する** 

[視覚化] ウィンドウの **[書式]** タブで、次の変更を行います。

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-format-tab-visualizations.png" alt-text="[視覚化] ウィンドウの [書式] タブのスクリーンショット。":::

1. ビジュアル 2 を選択します。 **[タイトル]** セクションで、 **[タイトルのテキスト]** を "月別および年別の利益" に変更し、 **[テキスト サイズ]** を **[16 pt]** に変更します。 **[影]** を **[オン]** に切り替えます。 

1. ビジュアル 3 を選択します。 **[マップ スタイル]** セクションで、 **[テーマ]** を **[グレースケール]** に変更します。 **[タイトル]** セクションで、タイトルの **[テキスト サイズ]** を **[16 pt]** に変更します。 **[影]** を **[オン]** に切り替えます。

1. ビジュアル 4 を選択します。 **[タイトル]** セクションで、タイトルの **[テキスト サイズ]** を **[16 pt]** に変更します。 **[影]** を **[オン]** に切り替えます。

1. ビジュアル 5 を選択します。 **[選択範囲のコントロール]** セクションで、 **[[すべて選択] オプションを表示する]** を **[オン]** に切り替えます。 **[スライサー ヘッダー]** セクションで、 **[テキスト サイズ]** を **[16 pt]** に増加します。 

**タイトルの背景図形を追加する**

1. **[挿入]** リボンで、 **[図形]**  >  **[四角形]** を選択します。 それをページの一番上に配置し、ページの幅とタイトルの高さに合わせて引き伸ばします。 
1. **[図形の書式設定]** ウィンドウの **[線]** セクションで、 **[透明度]** を **[100%]** に変更します。 
1. **[塗りつぶし]** セクションで、 **[塗りつぶしの色]** を **[テーマの色 5 #6B91C9]** (青) に変更します。 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-theme-color-5.png" alt-text="[テーマの色 5] のスクリーンショット。":::

1. **[書式]** タブで、 **[背面へ移動]**  >  **[最背面へ移動]** を選択します。 
1. ビジュアル 1 のテキスト、タイトルを選択し、フォントの色を **[白]** に変更します。 

**ビジュアル 2 および 3 の背景図形を追加する**

1. **[挿入]** リボンで、 **[図形]**  >  **[四角形]** を選択し、それを視覚エフェクト 2 および 3 の幅と高さに合わせて引き伸ばします。 
1. **[図形の書式設定]** ウィンドウの **[線]** セクションで、 **[透明度]** を **[100%]** に変更します。 
1. **[書式]** タブで、 **[背面へ移動]**  >  **[最背面へ移動]** を選択します。 

### <a name="finished-report"></a>完成したレポート

最終的な洗練されたレポートは次のようになります。  

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-excel-formatted-report.png" alt-text="書式設定された最終的なレポートのスクリーンショット。":::

手短に言えば、このレポートは、上司が最も関心のある質問に答えることができます。 

- 最も利益が多かったのは、どの年のどの月か? 

    2014 年 12 月 

- 会社が最も成功を収めたのは、どの国か? 

    ヨーロッパ、特にフランスとドイツ。 

- 会社が投資を継続する必要があるのは、どの製品とセグメントか? 

    会社は引き続き Paseo 製品に投資し、中小企業と政府のセグメントをターゲットにする必要があります。 

## <a name="save-your-report"></a>レポートの保存

- **[ファイル]** メニューで、 **[保存]** を選択します。

## <a name="publish-to-the-power-bi-service-to-share"></a>Power BI サービスに発行して共有する 

レポートを上司や仕事仲間と共有するには、Power BI サービスに発行します。 Power BI アカウントを持っている仕事仲間と共有する場合、仕事仲間はレポートを操作できますが、変更を保存することはできません。 

1. Power BI Desktop の **[ホーム]** リボンで、 **[発行]** を選択します。 

    Power BI サービスにサインインする必要がある場合があります。 まだアカウントを持っていない場合、[無料試用版にサインアップ](https://app.powerbi.com/signupredirect?pbi_source=web)できます。

1. [Power BI サービス] > **[選択]** で、 **[個人用ワークスペース]** などの宛先を選択します。
1. **[Power BI で 'ご利用のファイル名' を開く]** を選択します。

    :::image type="content" source="media/desktop-excel-stunning-report/open-power-bi.png" alt-text="Power BI サービスでレポートを開いたときのスクリーンショット。":::

    完成したレポートがブラウザーに表示されます。

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-excel-report-service.png" alt-text="Power BI サービスで完了した自分の Power BI レポートのスクリーンショット。"::: 

1. レポートの上部にある **[共有]** を選択して、レポートを他のユーザーと共有します。

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-share-report.png" alt-text="Power BI サービスからレポートを共有するときのスクリーンショット。":::

## <a name="next-steps"></a>次の手順

- [チュートリアル: Excel と OData フィードの売上データを分析する](../connect-data/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed.md)

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。
