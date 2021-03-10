---
title: Power BI Desktop の [分析] ウィンドウを使用する
description: Power BI Desktop でビジュアルの動的な参照線を作成します
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: how-to
ms.date: 01/10/2020
LocalizationGroup: Create reports
ms.openlocfilehash: e5ce7a274f1290e306b541d2d3e1fb6fdebb2310
ms.sourcegitcommit: f3669a5f68c9d646d86adcf77e589af4540042e3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2021
ms.locfileid: "102534667"
---
# <a name="use-the-analytics-pane-in-power-bi-desktop"></a>Power BI Desktop の [分析] ウィンドウを使用する

Power BI Desktop の **[分析]** ペインによって、動的な *参照線* をビジュアルに追加して、重要な傾向や情報に注目させることができます。 **[分析]** アイコンとペインは Power BI Desktop の **[視覚化]** 領域にあります。

![[分析] ペイン、視覚化、Power BI Desktop](media/desktop-analytics-pane/analytics-pane_1.png)

> [!NOTE]
> **[分析]** ウィンドウは、Power BI Desktop キャンバスでビジュアルを選択した場合にのみ表示されます。

## <a name="search-within-the-analytics-pane"></a>[分析] ウィンドウ内で検索する

Power BI Desktop の 2018 年 2 月リリースより (バージョン 2.55.5010.201 以降)、**[視覚化]** ペインの下位セクションである **[分析]** ペイン内で検索できます。 **[分析]** アイコンを選択すると、検索ボックスが表示されます。

![[検索] ボックス、[分析] ペイン、視覚化、Power BI Desktop](media/desktop-analytics-pane/analytics-pane_1b.png)

## <a name="use-the-analytics-pane"></a>[分析] ウィンドウを使用する

**[分析]** ペインを使うと、次の種類の動的参照線を作成できます。

* X 軸の定数線
* Y 軸の定数線
* 最小値線
* 最大値線
* 平均線
* 中央値線
* 百分位線
* 対称網掛け

> [!NOTE]
> すべての線をすべての種類のビジュアルで使用できるわけではありません。

次のセクションでは、**[分析]** ウィンドウと動的参照線を視覚化で使用する方法を説明します。

ビジュアルで使用可能な動的参照線を表示するには、次のようにします。

1. ビジュアルを選択または作成した後、**[視覚化]** セクションの **[分析]** アイコンを選択します。

    ![ビジュアル、[視覚化] ペイン、Power BI Desktop の分析を表示する](media/desktop-analytics-pane/analytics-pane_2.png)

2. 作成する線の種類を選択し、そのオプションを展開します。 この例では、**[平均線]** を選択します。

    ![平均線、[分析] ペイン、視覚化、Power BI Desktop](media/desktop-analytics-pane/analytics-pane_3.png)

3. 新しい線を作成するには、 **[+&nbsp;追加]** を選択します。 次に行の名前を指定します。 テキスト ボックスをダブルクリックし、名前を入力します。

    これで、線のすべての種類のオプションを使用できるようになりました。 **[色]**、**[透明度]** (パーセント)、**[線のスタイル]**、**[位置]** (ビジュアルのデータ要素との相対) を指定できます。 **[データ ラベル]** を含めるかどうかを選択することもできます。 線の基になるビジュアル メジャーを指定するには、**[メジャー]** ドロップダウン リストを選択します。このドロップダウン リストには、ビジュアルのデータ要素が自動的に設定されます。 ここでは、メジャーとして **[カルチャ]** を選択し、「*カルチャの平均*」というラベルを付け、その他のオプションをいくつかカスタマイズします。

    ![カルチャの平均線、[分析] ペイン、視覚化、Power BI Desktop](media/desktop-analytics-pane/analytics-pane_4.png)

4. データ ラベルが表示されるようにするには、**[データ ラベル]** を **[オフ]** から **[オン]** に変更します。 このスライダーをオンにすると、データ ラベルの他のオプションが表示されます。

    ![データ ラベルの設定、[分析] ペイン、視覚化、Power BI Desktop](media/desktop-analytics-pane/analytics-pane_5.png)

5. **[分析]** ウィンドウの **[平均線]** 項目の横に数字が表示されます。 この数字は、ビジュアルで現在有効になっている動的な線の数とその種類を示します。 **[Affordability]\(手ごろな価格\)** に **[最大値線]** を追加すると、**[分析]** ペインに **[最大値]** の動的参照線もこのビジュアルに適用されるようになります。

    ![最大値線と平均線の合計、[分析] ペイン、視覚化、Power BI Desktop](media/desktop-analytics-pane/analytics-pane_6.png)

選択したビジュアルに動的参照線を適用できない場合は (この例では **[マップ]** ビジュアル)、**[分析]** ペインを選択すると次のメッセージが表示されます。

![[マップ] ビジュアルの分析を使用できない、[分析] ペイン、視覚化、Power BI Desktop](media/desktop-analytics-pane/analytics-pane_7.png)

多数の関心のある分析情報を強調表示するには、**[分析]** ペインで動的参照行を作成します。

動的参照線を適用できるビジュアルを拡張するなど、特徴と機能の追加を計画しています。 頻繁にチェックして、新機能を確認してください。

## <a name="apply-forecasting"></a>予測を適用する

データ ソースに時間データがある場合は、"*予測*" 機能を使用できます。 ビジュアルを選択し、**[分析]** ペインの **[予測]** セクションを展開します。 **[予測の長さ]**、**[信頼区間]** など、予測を変更するための多数の入力を指定できます。 次の図は、予測が適用された基本的な線のビジュアルを示しています。 想像力を発揮して (また予測を試してみて)、モデルにどのように適用されるかを確認してください。

![予測機能、[分析] ペイン、視覚化、Power BI Desktop](media/desktop-analytics-pane/analytics-pane_8.png)

> [!NOTE]
> 予測機能は、折れ線グラフのビジュアルにのみ使用できます。

## <a name="limitations"></a>制限事項

動的参照線を使用できるかどうかは、使用されているビジュアルの種類によって決まります。 次の一覧では、これらの制限事項について具体的に説明します。

次のビジュアルでは、*X 軸の定数線*、*Y 軸の定数線*、および *対称網掛け* を使用できます。

* 散布図

*定数線*、*最小値線*、*最大値線*、*平均線*、*中央値線*、*百分位線* の使用は、次のビジュアルで使用できます。

* 面グラフ
* 集合横棒グラフ
* 集合縦棒グラフ
* 折れ線グラフ
* 散布図

次のビジュアルでは、 **[分析]** ウィンドウの *定数線* のみを使用できます。

* 積み上げ面グラフ
* 積み上げ横棒グラフ
* 積み上げ縦棒グラフ
* ウォーターフォール グラフ
* 100% 積み上げ横棒グラフ
* 100% 積み上げ縦棒グラフ

時間データがある場合、次のビジュアルには *傾向線* を使用できます。

* 面グラフ
* 集合縦棒グラフ
* 折れ線グラフ
* 折れ線集合縦棒グラフ
* 散布図

最後に、現在、以下を含む多くのビジュアルには動的線を適用できません。

* じょうごグラフ
* 折れ線集合縦棒グラフ
* 折れ線積み上げ縦棒グラフ
* リボン グラフ
* ドーナツ グラフ、ゲージ、マトリックス、円グラフ、テーブルなどのデカルト形式ではないビジュアル

百分位線を使用できるのは、*Power BI Desktop* でインポートされたデータを使用している場合、または **Analysis Services 2016** 以降を実行しているサーバー上のモデル、**Azure Analysis Services**、または Power BI サービス上のデータセットにライブ接続している場合のみです。

## <a name="next-steps"></a>次の手順

Power BI Desktop では、あらゆる種類の操作を実行できます。 そのような機能について詳しくは、次のリソースをご覧ください。

* [Power BI Desktop の新機能](../fundamentals/desktop-latest-update.md)
* [Power BI Desktop の取得](../fundamentals/desktop-get-the-desktop.md)
* [Power BI Desktop とは何ですか?](../fundamentals/desktop-what-is-desktop.md)
* [Power BI Desktop でのクエリの概要](desktop-query-overview.md)
* [Power BI Desktop でのデータ型](../connect-data/desktop-data-types.md)
* [Power BI Desktop でのデータの整形と結合](../connect-data/desktop-shape-and-combine-data.md)
* [Power BI Desktop での一般的なタスクの実行](desktop-common-query-tasks.md)
