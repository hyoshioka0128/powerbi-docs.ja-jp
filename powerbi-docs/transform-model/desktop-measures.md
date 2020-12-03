---
title: Power BI Desktop のメジャー
description: Power BI Desktop でクイック メジャーや DAX 構文などのメジャーを作成して使用する
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: how-to
ms.date: 01/29/2020
LocalizationGroup: Model your data
ms.openlocfilehash: 78c883c28323d34ef4583b6b3bd04736f9654cbc
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96414026"
---
# <a name="create-measures-for-data-analysis-in-power-bi-desktop"></a>Power BI Desktop でデータ分析用のメジャーを作成する

Power BI Desktop では、わずか数クリックで、データに対する洞察を作成できます。 しかし、場合によっては、最も重要な質問に答えるために必要なものが、データに含まれていないことがあります。 メジャーは、それを入手するために役立ちます。

メジャーは、最も一般的なデータ分析のいくつかに使用します。 合計、平均、最小値、最大値、カウントなどのシンプルな集計は、 **[フィールド]** ウェルで設定できます。 メジャーの計算結果は、ユーザーがレポートを操作するたびに変化するため、アドホック データ探索を高速で、また動的に実行できます。 詳しく見てみましょう。 詳細については、[メジャーの作成](/learn/modules/model-data-power-bi/4b-create-calculated-measures)に関するページを参照してください。

## <a name="understanding-measures"></a>メジャーについて

Power BI Desktop では、*レポート ビュー* または *データ ビュー* でメジャーを作成し、表示します。 ユーザーが自分で作成したメジャーは、**フィールド** リストに、計算機のアイコン付きで表示されます。 メジャーには任意の名前を付け、他のフィールドと同じように、新規または既存の視覚エフェクトを追加することができます。

![[フィールド] のメジャー フィールド](media/desktop-measures/measuresinpbid_measinfieldlist.png)

> [!NOTE]
> ダイアログ ボックスから選ぶことができる既製の *クイック メジャー* もあります。 これらはメジャーをすばやく作成することができ、自動的に作成される Data Analysis Expressions (DAX) 式を確認できるため DAX 構文の勉強にも適しています。 詳細については、[クイック メジャー](desktop-quick-measures.md)に関するページを参照してください。
> 
> 

## <a name="data-analysis-expressions"></a>Data Analysis Expressions (DAX)

メジャーは、数式の結果を計算します。 独自のメジャーを作成するときは、[Data Analysis Expressions](/dax/) (DAX) 数式言語を使用します。 DAX には 200 を超える関数、演算子、およびコンストラクトから成るライブラリが含まれています。 このライブラリは、メジャーを作成する際の柔軟性が非常に高く、データ分析に必要なほとんどすべての計算結果を得ることができます。

DAX の数式は、Excel の数式とよく似ています。 DAX には、`DATE`、`SUM`、`LEFT` など、Excel と同じ機能が多数用意されています。 ただし、DAX 関数は、Power BI Desktop で取り扱っているようなリレーショナル データを扱うことを意図しています。

## <a name="lets-look-at-an-example"></a>例を見てみましょう

Jan は、Contoso 社の営業マネージャーです。 Jan は、次の会計年度の販売店売上予測を提供するように依頼されました。 そこで、Jan は昨年度の売上高に基づき、今後 6 か月間に予定されている各種のプロモーションの成果として年率 6% の売上増加を見込んで予測を立てることにしました。

推定値を報告するため、Jan は Power BI Desktop に昨年度の売上データをインポートします。 Jan は、**Reseller Sales** テーブルに **SalesAmount** フィールドがあることを確認します。 インポートしたデータには昨年度の売上高だけが含まれているので、Jan は "**SalesAmount**" フィールドの名前を "*Last Years Sales*" に変更します。 その後、Jan は "**Last Years Sales**" をレポート キャンバスにドラッグします。 昨年度のすべての販売店の売上合計を示す単一の値として、グラフによる視覚エフェクトが表示されます。

Jan は計算を指定しなくても、自動的に 1 つ用意されたことに気付きます。 Power BI Desktop により、"**Last Years Sales**" に含まれるすべての値の合計を計算する独自のメジャーが作成されました。

しかし、次の会計年度の売上予測を計算するメジャーが必要です。このメジャーでは、事業に 6% の増加を見込んで、昨年度の売上に 1.06 を乗算して計算します。 この計算について、Jan はメジャーを作成します。 *[新しいメジャー]* 機能を使用して、Jan は新しいメジャーを作成し、次の DAX 式を入力します。

```dax
    Projected Sales = SUM('Sales'[Last Years Sales])*1.06
```

その後、Jan は新しい Projected Sales メジャーをグラフにドラッグします。

![新しい Projected Sales のビジュアル](media/desktop-measures/measuresinpbid_lastyearsales.png)

このように、Jan は迅速に、最小限の労力で、売上予測を計算するメジャーを作成できました。 Jan はさらに、特定の販売店をフィルター処理したり、レポートに他のフィールドを追加したりして、予測データをさらに分析することができます。

## <a name="data-categories-for-measures"></a>メジャー用のデータ カテゴリ

メジャー用のデータ カテゴリを選択することもできます。

特に、データ カテゴリでは、メジャーを使用して URL を動的に作成し、データ カテゴリを Web URL としてマークすることができます。

メジャーを Web URL として表示するテーブルを作成すれば、ご自分の選択内容に基づいて作成された URL をクリックすることができます。 この方法は特に、[URL フィルター パラメーター](../collaborate-share/service-url-filters.md)を使用して他の Power BI レポートにリンクする場合に役に立ちます。

## <a name="organizing-your-measures"></a>メジャーを整理する

メジャーには、フィールド リストのどこメジャーが表示されるかを定義する "*ホーム*" テーブルがあります。 その場所を変更するには、ご利用のモデル内のテーブルから場所を選択します。

![ご利用のメジャーに対してテーブルを選択する](media/desktop-measures/measures-03.png)

テーブル内のフィールドを "*表示フォルダー*" に入れて整理することもできます。 Power BI Desktop の左端から **[モデル]** を選択します。 **[プロパティ]** ペインで、使用可能なフィールドの一覧から移動するフィールドを選択します。 **[フォルダーの表示]** に新しいフォルダーの名前を入力して、フォルダーを作成します。 フォルダーを作成すると、選択したフィールドがそのフォルダーに移動されます。

![メジャー用のフィールドを作成する](media/desktop-measures/measures-04.gif)

バックスラッシュ記号を使用することで、サブフォルダーを作成することができます。 たとえば、"*財務\通貨*" の場合は、"*財務*" フォルダーが作成され、その中に "*通貨*" フォルダーが作成されます。

セミコロンを使用してフォルダー名を区切ることにより、1 つのフィールドを複数のフォルダーに表示することができます。 たとえば、"*製品\名前;部門*" の場合は、"*製品*" フォルダー内の "*部門*" フォルダーと "*名前*" フォルダー内にフィールドが表示されます。

メジャーのみを含む特殊なテーブルを作成できます。 このテーブルは、常に **[フィールド]** の先頭に表示されます。 これを行うには、列を 1 つだけ含むテーブルを作成します。 **[データの入力]** を使用すれば、そのテーブルを作成できます。 次に、ご自分のメジャーをそのテーブルに移動します。 最後に、作成した列 (テーブルではなく) を非表示にします。 **[フィールド]** の上部にある矢印をクリックして、フィールドの一覧を閉じて再度開き、変更内容を確認します。

![メジャーを整理し、それらを [フィールド リスト] の上部に保持する](media/desktop-measures/measures-05.png)

## <a name="learn-more"></a>詳細情報

ここでは、メジャーについて簡単に説明しました。 独自に作成する方法について、役立つ情報は他にもたくさんあります。 詳細については、「[チュートリアル:Power BI Desktop で独自のメジャーを作成する](desktop-tutorial-create-measures.md)」をご覧ください。 サンプル ファイルをダウンロードし、さまざまなメジャーを作成する方法についてステップ バイ ステップで学ぶことができます。  

DAX についてもう少し詳しく知るには、「[Power BI Desktop における DAX の基本事項](desktop-quickstart-learn-dax-basics.md)」をご覧ください。 「[Data Analysis Expressions (DAX) リファレンス](/dax/)」では、関数、構文、演算子、名前付け規則のそれぞれに関する詳しい記事を紹介しています。 Excel 内の Power Pivot および SQL Server Analysis Services で DAX が利用されるようになって数年が経ちます。 その他にも多くのリソースが利用可能になっています。 「[DAX リソース センター Wiki](https://social.technet.microsoft.com/wiki/contents/articles/1088.dax-resource-center.aspx)」をぜひご確認ください。ここでは、BI コミュニティで影響力を持つメンバーが DAX の知識を公開しています。
