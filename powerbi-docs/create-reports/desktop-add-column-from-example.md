---
title: Power BI Desktop で例から列を追加する
description: Power BI Desktop で既存の列を例として使って新しい列を簡単に作成します。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 01/16/2019
LocalizationGroup: Create reports
ms.openlocfilehash: f33a9f5656875825b70c7e51202431ba268fe86a
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96414509"
---
# <a name="add-a-column-from-examples-in-power-bi-desktop"></a>Power BI Desktop で例から列を追加する
Power Query エディターの "*例から列を追加する*" で、新しい列に 1 つ以上の例の値を指定するだけで、データ モデルに新しい列を追加できます。 選択範囲から新しい列の例を作成したり、テーブル内の既存のすべての列に基づいて入力を指定したりできます。

![Power Query エディターのスクリーンショット。Power BI Desktop で例から列を追加する方法を示しています。](media/desktop-add-column-from-example/add-column-from-example_01.png)

"*例から列を追加する*" を使用すると、新しい列をすばやく簡単に作成でき、次のような場合に最適です。

- 新しい列に設定するデータはわかっているものの、それを実現する変換、または変換のコレクションがわからない。
- 必要な変換は既にわかっているものの、それを実行するために UI のどこを選択すればよいかわからない。
- *M* 言語の "*カスタム列*" 式を使って行う必要がある変換についてはすべてわかっているものの、そのような式の 1 つ (または複数) が UI で表示されていない。

例からの列の追加はわかりやすく、簡単です。 次のセクションでは、それがいかに簡単かを説明します。

## <a name="add-a-new-column-from-examples"></a>例から新しい列を追加する

Wikipedia からサンプル データを取得するには、Power BI Desktop リボンの **[ホーム]** タブから **[データを取得]**  >  **[Web]** を選択します。 

![Web からデータを取得する](media/desktop-add-column-from-example/add-column-from-example_02.png)

表示されるダイアログに次の URL を貼り付け、 **[OK]** を選択します。 

*https:\//wikipedia.org/wiki/List_of_states_and_territories_of_the_United_States*

**[ナビゲーター]** ダイアログ ボックスで、 **[States of the United States of America]** のテーブルを選択し、 **[データの変換]** を選択します。 テーブルが Power Query エディターで開きます。

または、Power BI Desktop から既に読み込まれているデータを開くには、リボンの **[ホーム]** タブで **[クエリを編集]** を選択します。 データが Power Query エディターで開きます。 

![Power BI Desktop で [クエリを編集] を選択する](media/desktop-add-column-from-example/add-column-from-example_05.png)

Power Query エディターでサンプル データが開いたら、リボンで **[列の追加]** を選択し、 **[例からの列]** を選択します。 **[例からの列]** アイコン自体を選択して、既存のすべての列から列を作成するか、ドロップダウンの矢印で **[すべての列から]** または **[選択範囲から]** のどちらかを選択します。 このチュートリアルでは、 **[すべての列から]** を使用します。

![例からの列の追加を選択する](media/desktop-add-column-from-example/add-column-from-example_03.png)

## <a name="add-column-from-examples-pane"></a>[例から列を追加する] ペイン
**[列の追加]**  >  **[例からの列]** を選択すると、 **[例から列を追加する]** ペインがテーブルの上部に表示されます。 新しい **[列 1]** が既存の列の右側に表示されます (すべてを表示するにはスクロールする必要がある場合があります)。 **[列 1]** の空白セルに例の値を入力すると、Power BI が例に合ったルールと変換を作成し、それらを使用して列の残りの部分を塗りつぶします。

**[例からの列]** は、 **[クエリの設定]** ペインの **[Applied Step]\(適用されたステップ\)** としても表示されます。 Power Query エディターは通常どおり変換ステップを記録し、それを順番にクエリに適用します。

![[例から列を追加する] ペイン](media/desktop-add-column-from-example/add-column-from-example_04.png)

新しい列に例を入力すると、Power BI は作成された変換に基づいて、残りの列がどのように表示されるかのプレビューを表示します。 たとえば、テーブルの最初の列の **Alabama** という値に対応する「*Alabama*」を最初の行に入力します。 Power BI では、Enter キーを押すとすぐに、最初の列の値に基づいて新しい列の残りの部分が入力され、列に **[Name & postal abbreviation[12] - Copy]** という名前が付けられます。

次に、新しい列の **[Massachusetts[E]]** 行に移動して、文字列の **[E]** 部分を削除します。 Power BI は変更を検出し、例を使って変換を作成します。 Power BI の **[例から列を追加する]** ペインに変換について示され、列の名前は **[区切り記号の前のテキスト]** に変更されます。 

![例から変換された列](media/desktop-add-column-from-example/add-column-from-example_06.png)

Power Query エディターは、入力された例を変換に追加します。 問題がなければ、 **[OK]** を選んで変更をコミットします。 

列見出しをダブルクリックするか、右クリックして **[名前の変更]** を選択すると、新しい列を任意の名前に変更することができます。 

次のビデオで、サンプル データ ソースを使用して実際に **例から列を追加する** 方法をご覧ください。 

[Power BI Desktop: 例から列を追加する](https://www.youtube.com/watch?v=-ykbVW9wQfw)。 

## <a name="list-of-supported-transformations"></a>サポートされている変換の一覧
**[例から列を追加する]** を使用する場合、多くの変換が使用できますが、そのすべてではありません。 以下の一覧は、サポートされている変換です。

**[全般]**

- 条件列

**参照**
  
- 特定の列の参照 (トリム、クリーン、および大文字小文字の変換を含みます)

**Text 変換**

- 結合 (リテラル文字列と列全体の値の組み合わせをサポートしています)
- 置換
- 長さ
- 抽出   
  - 最初の文字
  - 最後の文字
  - 範囲
  - 区切り記号の前のテキスト
  - 区切り記号の後のテキスト
  - 区切り記号の間のテキスト
  - 長さ
  - 文字の削除
  - 文字の保持

> [!NOTE]
> すべての *Text* 変換では、列の値のトリミング、クリーン、または大文字小文字変換の適用の必要性が考慮されます。

**Date 変換**

- 日
- 週の通算日
- 曜日の名前
- 年の通算日
- 月
- 月の名前
- 年の四半期
- 月の通算週
- 年の通算週
- 年
- 年齢
- 年の開始日
- 年の最終日
- 月の開始日
- 月の最終日
- 四半期の開始日
- 月内の日数
- 四半期の最終日
- 週の開始日
- 週の最終日
- 月の日付
- 一日の開始時刻
- 最終日

**Time 変換**

- Hour
- 分
- Second  
- 現地時刻への変換

> [!NOTE]
> すべての *Date* および *Time* 変換では、列の値を *Date*、*Time*、または *DateTime* に変換する必要性が考慮されます。

**Number 変換** 

- 絶対値
- アークコサイン
- アークサイン
- アークタンジェント
- Number への変換
- コサイン
- キューブ
- 除算
- 指数
- 階乗
- 整数除算
- 偶数
- 奇数
- Ln
- 底が 10 の対数
- 剰余
- 乗算
- 切り捨て
- 切り上げ
- 符号
- Sin
- 平方根
- 2 乗
- 減算
- 合計
- タンジェント
- バケット/範囲
