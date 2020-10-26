---
title: Power BI Desktop で一般的なクエリ タスクを実行する
description: Power BI Desktop で一般的なクエリ タスクを実行する
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 01/09/2020
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 931c500cd2c2dbbf750eb3699ac5290a2977c21b
ms.sourcegitcommit: d153cfc0ce559480c53ec48153a7e131b7a31542
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/29/2020
ms.locfileid: "91526262"
---
# <a name="perform-common-query-tasks-in-power-bi-desktop"></a>Power BI Desktop で一般的なクエリ タスクを実行する

Power BI Desktop の Power Query エディター ウィンドウには、一般的に使用される多数のタスクがあります。 この記事では、それらの一般的なタスクについて説明し、追加情報へのリンクを示します。

ここでは、次の一般的なクエリ タスクについて説明します。

* データに接続する
* データの整形と結合
* 行のグループ化
* 列のピボット
* カスタム列の作成
* 数式のクエリ

これらのタスクを完了するために、いくつかのデータ接続を使用します。 これらのタスクの手順をユーザー自身で実行することもできるように、データはダウンロードや接続が可能になっています。

最初のデータ接続は [Excel ブック](https://download.microsoft.com/download/5/7/0/5701F78F-C3C2-450C-BCCE-AAB60C31051D/PBI_Edu_ELSi_Enrollment_v2.xlsx)です。ダウンロードしてローカルに保存できます。 もう 1 つは、他の Power BI Desktop 記事でも使用されている Web リソースです。

<https://www.bankrate.com/retirement/best-and-worst-states-for-retirement/>

一般的なクエリ タスクは、それら両方のデータ ソースへの接続に必要な手順から始まります。

## <a name="connect-to-data"></a>データに接続する

Power BI Desktop のデータに接続するには、 **[ホーム]** 、 **[データの取得]** の順に選択します。 Power BI Desktop は、最も一般的なデータ ソースのメニューを表示します。 Power BI Desktop が接続できるデータ ソースの完全な一覧を確認するには、メニューの末尾にある **[その他]** を選択します。 詳細については、「[Power BI Desktop のデータ ソース](../connect-data/desktop-data-sources.md)」を参照してください。

![[よく使われる] データ ソース メニュー、[データの取得] ボタン、Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_getdata.png)

まず **[Excel]** を選択し、前述の Excel ブックを指定して、 **[開く]** を選択します。 テーブルを選択すると、クエリによってブックが検査され、 **[ナビゲーター]** ダイアログ ボックスで見つかったデータが表示されます。

![Excel データ ソース、[ナビゲーター] ダイアログ ボックス、[データの取得]、Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_navigator.png)

Power BI Desktop に読み込む前に、 **[データの変換]** を選択してデータの編集、調整、または "*整形*" を行うことができます。 編集は、読み込む前に減らしておきたい大規模なデータセットを使用する場合に特に便利です。

さまざまな種類のデータに接続することは簡単です。 また、Web リソースに接続することもできます。 **[データの取得]**  >  **[詳細]** を選択し、 **[その他]**  >  **[Web]**  >  **[接続]** を選択します。

![Web データ ソース、[データの取得] ダイアログ ボックス、Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_getdata_other.png)

**[Web から]** ダイアログ ボックスが表示され、ここに Web ページの URL を入力できます。

![[Web から] ダイアログ ボックス、Web データ ソース、[データの取得]、Power BI Desktop](media/desktop-common-query-tasks/datasources_fromwebbox.png)

**[OK]** を選択します。 以前と同様に、Power BI Desktop によって Web ページ データが検査され、 **[ナビゲーター]** ダイアログ ボックスにプレビュー オプションが表示されます。 テーブルを選択すると、データのプレビューが表示されます。

その他のデータ接続も類似しています。 データ接続に認証が必要な場合、Power BI Desktop は適切なユーザーが資格情報を入力するように求めるダイアログを表示します。

Power BI Desktop 内のデータに接続する方法を示すステップごとの実例については、「[Power BI Desktop におけるデータへの接続](../connect-data/desktop-connect-to-data.md)」を参照してください。

## <a name="shape-and-combine-data"></a>データの整形と結合

Power Query エディターを使用すると、データの整形と結合を簡単に行うことができます。 このセクションでは、データを整形する方法を示すいくつかの例を示します。 データを整形および結合する方法を示す、より詳しい実例は、「[Power BI Desktop でのデータの整形と結合](../connect-data/desktop-shape-and-combine-data.md)」を参照してください。

前のセクションでは、Excel ブックと Web リソースという 2 組のデータに接続しました。 データが Power Query エディターに読み込まれたら、次に示すように、 **[クエリ]** ペインで使用できるクエリから Web ページ クエリを選択します。

![[クエリ] ペイン、Power Query エディター、Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_querypaneloaded.png)

データを整形するときには、データ ソースの形式と書式をユーザーの必要に合わせて変換します。

Power Query エディターのリボンとコンテキスト メニューには、多くのコマンドがあります。 たとえば、列を右クリックすると、コンテキスト メニューを使用して列を削除できます。 また、列を選択してから、リボンの **[ホーム]** タブから **[列の削除]** ボタンを選択することもできます。

![[列の削除] コマンド、Power Query エディター、Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_removecolumns.png)

このクエリでは、他のさまざまな方法でデータを整形できます。 上または下から任意の数の行を削除できます。 また、列の追加、列の分割、値の置換などの整形タスクを行うことができます。 これらの機能を使用すると、好みの方法でデータを取得するように Power Query エディターに指示できます。

## <a name="group-rows"></a>行のグループ化

Power Query エディターでは、複数行の値を 1 つの値にグループ化することができます。 この機能は、提供される製品の数、総売り上げ高、学生の数などを集計する際に便利です。

この例では、教育登録データ セット内の複数の行をグループ化します。 データは、Excel ブックのものです。 Power Query エディターでは、必要な列のみを取得し、テーブルの名前を変更し、他のいくつかの変換を行うように整形されます。

各州の機関の数を調べてみましょう  (機関には、学区や他の教育機関 (地域のサービス地区など) が含まれる可能性があります)。 **[Agency ID - NCES Assigned \[District\] Latest available year]\(機関 ID - NCES によって割り当てられた <地区> の最新の使用可能な年\)** 列を選択し、リボンの **[変換]** タブまたは **[ホーム]** タブの **[グループ化]** ボタンを選択します  ( **[グループ化]** は両方のタブで使用できます)。

![テーブル内の行をグループ化する方法を示すスクリーンショット。](media/desktop-common-query-tasks/commonquerytasks_groupby.png)

**[グループ化]** ダイアログ ボックスが表示されます。 Power Query エディターで行がグループ化されると、 **[グループ化]** の結果が格納される新しい列が作成されます。 **Group By** 操作は、次の方法で調整できます。

1. ラベルが付いていないドロップダウン リストで、グループ化する列を指定します。 Power Query エディターでは、選択した列にこの値が既定で設定されますが、テーブル内の任意の列に変更できます。
2. **新しい列名**:Power Query エディターからは、グループ化の対象の列に適用される操作に基づいて、新しい列の名前が提案されます。 ただし、新しい列には任意の名前を付けることができます。
3. **Operation**: **[合計]** 、 **[中央値]** 、 **[個別の行数のカウント]** など、Power Query エディターで適用される操作を選択できます。 既定値は **[行数のカウント]** です。
4. **[グループ化の追加]** と **[集計の追加]** :これらのボタンは、 **[詳細]** オプションを選択した場合にのみ使用できます。 1 回の操作で、多くの列に対してグループ化操作 ( **[グループ化]** アクション) を行い、これらのボタンを使用して複数の集計を作成できます。 このダイアログ ボックスでの選択に基づき、Power Query エディターによって複数の列に対して動作する新しい列が作成されます。

**[グループの追加]** または **[集計の追加]** を選択すると、 **[グループ化]** 操作にグループ化または集計を追加できます。 グループ化または集計を削除するには、行の右側にある省略記号アイコン ( **[...]** ) を選択し、 **[削除]** を選択します。 次に進み、既定値を使用して **[グループ化]** 操作を試して、何が起こるかを確認します。

![[グループ化の追加] と [集計の追加] に引き出し線が付けられた [グループ化] ダイアログ ボックスを示すスクリーンショット。](media/desktop-common-query-tasks/commonquerytasks_groupbynumbered.png)

**[OK]** を選択すると、クエリによって **[グループ化]** 操作が実行され、結果が返されます。 驚きの結果です。オハイオ州、イリノイ州、テキサス州、カリフォルニア州には、それぞれ 1,000 を超える数の機関があります。

![[カウント] 列、[グループ化] 操作、Power Query エディター、Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_groupedresult.png)

Power Query エディターを使うと、最後の整形操作をいつでも削除できます。 **[クエリの設定]** ペインの **[適用したステップ]** で、最近完了したステップの横にある **[X]** を選択するだけです。 では、試してみましょう。 結果が気に入らない場合は、Power Query エディターでデータが希望どおりに整形されるまでステップをやり直します。

## <a name="pivot-columns"></a>列のピボット

列をピボットして、列内の一意の値ごとの集計値を含むテーブルを作成できます。 たとえば、各製品カテゴリに含まれる異なる製品数を調べるために、それを行うテーブルをすばやく作成できます。

例を見てみましょう。 次の **Products_by_Categories** テーブルは、一意の各製品 (その名前) と、その製品が分類されるカテゴリだけを示すように整形されています。 (**CategoryName** 列に基づいて) 各カテゴリの製品数を示す新しいテーブルを作成するには、列を選択し、 **[変換]**  >  **[列のピボット]** を選択します。

![[列のピボット] コマンド、Power Query エディター、Power BI Desktop](media/desktop-common-query-tasks/pivotcolumns_pivotbutton.png)

**[列のピボット]** ダイアログ ボックスが表示され、新しい列 (1) の作成に使用される列の値がわかります  (**CategoryName** の目的の列名が表示されない場合は、ドロップダウン リストから選択します)。 **[詳細] オプション** (2) を展開すると、集計値 (3) に適用される関数を選択できます。

![[列のピボット] ダイアログ ボックス、Power Query エディター、Power BI Desktop](media/desktop-common-query-tasks/pivotcolumns_pivotdialog.png)

**[OK]** を選択すると、 **[列のピボット]** ダイアログ ボックスで指定された転送指示に従って、クエリによってテーブルが表示されます。

![[列のピボット] の結果、Power Query エディター、Power BI Desktop](media/desktop-common-query-tasks/pivotcolumns_pivotcomplete.png)

## <a name="create-custom-columns"></a>カスタム列の作成

Power Query エディターでは、テーブル内の複数の列に対して動作するカスタム数式を作成できます。 これで、そのような数式の結果を新しい (カスタム) 列に配置できるようになります。 Power Query エディターを使用すると、簡単にカスタム列を作成できます。

Power Query エディターで Excel ブックのデータを使用し、リボンの **[列の追加]** タブに移動し、 **[カスタム列]** を選択します。

![[カスタム列の追加] コマンド、Power Query エディター、Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_customcolumn.png)

次のダイアログ ボックスが表示されます。 この例では、英語学習者 (ELL) である合計学生数のパーセンテージを計算する、「*Percent ELL*」という名前のカスタム列を作成します。

![[カスタム列] ダイアログ ボックス、Power Query エディター、Power BI Desktop](media/desktop-common-query-tasks/customcolumn_addcustomcolumndialog.png)

Power Query エディターの他の適用されるステップと同様に、探しているデータが新しいカスタム列に表示されない場合は、そのステップを削除できます。 **[クエリの設定]** ペインの **[適用したステップ]** で、 **[追加されたカスタム]** ステップの横にある **[X]** を選択します。

![[適用したステップ]、[クエリの設定] ペイン、Power Query エディター、Power BI Desktop](media/desktop-common-query-tasks/customcolumn_addedappliedstep.png)

## <a name="query-formulas"></a>数式のクエリ

Power Query エディターによって生成される手順を編集できます。 また、カスタム式を作成することもできます。これを使うと、データに接続してより正確に整形できます。 Power Query エディターがデータに対してアクションを実行するたびに、アクションに関連付けられた数式が数式バーに表示されます。 数式バーを表示するには、リボンの **[表示]** タブに移動し、 **[数式バー]** を選択します。

![[数式バー] オプション、Power Query エディター、Power BI Desktop](media/desktop-common-query-tasks/queryformulas_formulabar.png)

Power Query エディターには、各クエリに適用されているすべてのステップが、表示や変更が可能なテキストとして保持されます。 **詳細エディター**を使用して、任意のクエリのテキストを表示または変更できます。 **[表示]** 、 **[詳細エディター]** の順に選択します。

![[詳細エディター] コマンド、Power Query エディター、Power BI Desktop](media/desktop-common-query-tasks/queryformulas_advancededitorbutton.png)

**USA\_StudentEnrollment** クエリに関連付けられたクエリ手順が表示されている、**詳細設定エディター**をここに示します。 これらの手順は、しばしば「*M*」と呼ばれる Power Query 数式言語で作成されています。詳細については、「[Power Query 数式の詳細について](https://support.office.com/article/learn-about-power-query-formulas-6bc50988-022b-4799-a709-f8aafdee2b2f)」を参照してください。 言語仕様そのものを確認するには、「[Power Query M 言語仕様](/powerquery-m/power-query-m-language-specification)」を参照してください。

![[詳細エディター] ダイアログ ボックス、Power Query エディター、Power BI Desktop](media/desktop-common-query-tasks/queryformulas_advancededitor.png)

Power BI Desktop には、数式カテゴリの幅広いセットが備わっています。 すべての Power Query エディターの数式の詳細と完全なリファレンスについては、「[Power Query M 関数参照](/powerquery-m/power-query-m-function-reference)」を参照してください。

## <a name="next-steps"></a>次の手順

Power BI Desktop では、あらゆる種類の操作を実行できます。 そのような機能の詳細については、次のリソースを参照してください。

* [Power BI Desktop とは何ですか?](../fundamentals/desktop-what-is-desktop.md)
* [Power BI Desktop でのクエリの概要](desktop-query-overview.md)
* [Power BI Desktop のデータ ソース](../connect-data/desktop-data-sources.md)
* [Power BI Desktop でデータに接続する](../connect-data/desktop-connect-to-data.md)
* [Power BI Desktop でのデータの整形と結合](../connect-data/desktop-shape-and-combine-data.md)
