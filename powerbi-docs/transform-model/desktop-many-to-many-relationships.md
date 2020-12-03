---
title: Power BI Desktop で多対多のリレーションシップ
description: Power BI Desktop で多対多カーディナリティのリレーションシップを使用します
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: conceptual
ms.date: 12/19/2019
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 5f64a9a896fbb5ea3e080e1d07f6cc7d980430b8
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415705"
---
# <a name="apply-many-many-relationships-in-power-bi-desktop"></a>Power BI Desktop で多対多リレーションシップを適用する

Power BI Desktop で "*多対多カーディナリティのリレーションシップ*" を使用すると、"*多対多*" のカーディナリティを使用するテーブルを結合できます。 2 つ以上のデータ ソースを含むデータ モデルを、より簡単かつ直感的に作成できます。 "*多対多カーディナリティのリレーションシップ*" は、Power BI Desktop のより大きな機能である "*複合モデル*" の一部です。

![[リレーションシップの編集] ペインの多対多リレーションシップ、Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

Power BI Desktop の "*多対多カーディナリティのリレーションシップ*" は、次の関連する 3 つの機能のいずれかで構成されます。

* **複合モデル**:"*複合モデル*" では、DirectQuery 接続やインポートなど、2 つ以上のデータ接続を任意の組み合わせでレポートに含めることができます。 詳細については、「[Power BI Desktop で複合モデルを使用する](desktop-composite-models.md)」を参照してください。

* **多対多カーディナリティのリレーションシップ**:複合モデルでは、テーブル間に "*多対多カーディナリティのリレーションシップ*" を確立することができます。 このアプローチでは、テーブル内の一意の値の要件が除外されます。 また、リレーションシップを作成するためだけに新しいテーブルを導入するなどの以前の回避策も除外されます。 この機能については、この記事で詳しく説明します。

* **ストレージ モード**:どのビジュアルでバックエンド データ ソースへのクエリが必要かを指定できるようになりました。 クエリを必要としないビジュアルは、それらが DirectQuery に基づいている場合でもインポートされます。 この機能はパフォーマンスの向上とバック エンドの負荷の軽減に役立ちます。 以前は、スライサーなどの、シンプルなビジュアルでも、バックエンド ソースに送信されるクエリが開始されました。 詳細については、「[Power BI Desktop のストレージ モード](desktop-storage-mode.md)」をご覧ください。

## <a name="what-a-relationship-with-a-many-many-cardinality-solves"></a>多対多カーディナリティのリレーションシップによって解決されるもの

"*多対多カーディナリティのリレーションシップ*" が利用可能になるまでは、2 つのテーブル間のリレーションシップは Power BI で定義されていました。 リレーションシップに関係する少なくとも 1 つのテーブルの列に、一意の値を含める必要がありました。 しかし多くの場合、一意の値を含む列はありませんでした。

たとえば、2 つのテーブルに Country というラベルが付いた列があるとします。 しかし、どちらのテーブルでも Country の値が一意ではありませんでした。 このようなテーブルを結合するには、回避策を用意する必要がありました。 1 つの回避策として、必要な一意の値を持つ追加のテーブルを導入することが考えられます。 "*多対多カーディナリティのリレーションシップ*" では、"*多対多*" のカーディナリティを持つリレーションシップを使用する場合に、このようなテーブルを直接結合することができます。

## <a name="use-relationships-with-a-many-many-cardinality"></a>多対多カーディナリティのリレーションシップを使用する

Power BI で 2 つのテーブル間のリレーションシップを定義する場合、リレーションシップのカーディナリティを定義する必要があります。 たとえば、ProductSales と Product の間のリレーションシップ &mdash;ProductSales[ProductCode] と Product[ProductCode] を使用する&mdash; は、"*多対一*" として定義されます。 リレーションシップをこのように定義するのは、各製品に対して多くの売上が存在し、Product テーブル内の列 (ProductCode) が一意であるためです。 リレーションシップのカーディナリティを "*多対一*"、"*一対多*"、または "*一対一*" として定義すると、Power BI によってそれが検証されるため、選択したカーディナリティが実際のデータと一致します。

たとえば、この画像のシンプルなモデルを見てみましょう。

![ProductSales および Product テーブル、リレーションシップ ビュー、Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_02.png)

ここで、**Product** (製品) で次の 2 つの行のみが表示されているとします。

![2 つの行を含む Product テーブルのビジュアル、Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_03.png)

また、Sales テーブルには、製品 C の行を含め、4 行しかないとします。参照整合性エラーのため、製品 C の行は **Product** テーブルには存在しません。

![4 つの行を含む Sales テーブルのビジュアル、Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_04.png)

**ProductName** と **Price** (**Product** テーブルからのもの)、および各製品の合計 **Qty** (ProductSales テーブルからのもの) は、次のように表示されます。

![製品名、価格、および数量が表示されたビジュアル、Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_05.png)

前の画像からわかるように、空白の **ProductName** 行は製品 C の売上に関連付けられています。この空白行は次のことを示しています。

* **Product** (製品) テーブルに対応する行が存在しない、**ProductSales** (製品売上) テーブルの任意の行がある。 この例の製品 C の場合のように、参照整合性の問題が存在する。

* 外部キー列が null である **ProductSales** (製品売上) テーブルの行がある。

これらの理由により、どちらの場合の空白行も、**ProductName** (製品名) と **Price** (価格) が不明な売上を示しています。

テーブルが 2 つの列で結合されていても、どちらの列も一意ではない場合があります。 たとえば、これらのテーブルについて考えてみます。

* **Sales** (売上) テーブルでは、**State** (州) 別の売上データが表示されており、各行にはその州の売上の種類が含まれています。 州はカリフォルニア州、ワシントン州、テキサス州などです。

    ![州別の売上が表示されている Sales テーブル、Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_06.png)

* **CityData** テーブルでは、人口や州 (カリフォルニア州、ワシントン州、テキサス州など) を含む、市区町村に関するデータが表示されています。

    ![市区町村、州、および人口が表示されている Sales テーブル、Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_07.png)

これで、**State** の列が両方のテーブルに含まれるようになりました。 州ごとの総売上と、各州の総人口の両方についてレポートすることをお勧めします。 しかし、問題があります。**State** 列がどちらのテーブルでも一意ではありません。

## <a name="the-previous-workaround"></a>以前の回避策

Power BI Desktop の 2018 年 7 月のリリースより前では、これらのテーブル間に直接のリレーションシップを作成することはできませんでした。 以下が一般的な回避策でした。

* 一意の State ID のみを含む 3 番目のテーブルを作成します。 テーブルには、次のいずれか、またはすべてを指定できます。
  * 計算テーブル (Data Analysis Expressions [DAX] を使用して定義されたもの)。
  * クエリ エディターで定義されたクエリに基づくテーブル。テーブルのいずれかから抽出された一意の ID を表示する場合があります。
  * 結合された完全なセット。

* 次に、一般的な "*多対一*" リレーションシップを使用して、2 つの元のテーブルをその新しいテーブルに関連付けます。

回避策テーブルは表示したままでかまいません。 または、回避策テーブルを非表示にして、 **[フィールド]** のリストに表示されないようにすることもできます。 テーブルを非表示にする場合、"*多対一*" リレーションシップが一般的に両方向にフィルター処理するように設定され、いずれのテーブルからでも State フィールドを使用できます。 この後のクロス フィルタリングは、もう 1 つのテーブルに反映されます。 このアプローチを次の図に示します。

![非表示の State テーブル、ProductSales ビュー、Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_08.png)

**State** (州) (**CityData** (市区町村データ) テーブル) と共に合計の **Population** (人口) と合計の **Sales** (売上) を表示するビジュアルは、次のようになります。

![State (州)、Population (人口)、Sales (売上) の各データを示すスクリーンショット。](media/desktop-many-to-many-relationships/many-to-many-relationships_09.png)

> [!NOTE]
> この回避策では **CityData** テーブルの州が使用されるため、そのテーブルの州のみがリストされます。したがって、テキサス州は除外されます。 また、"*多対一*" リレーションシップとは異なり、合計行にはすべての **Sales** (テキサス州のデータを含む) が含まれますが、このような不一致の行を対象とする空白行は含まれません。 同様に、**State** が null 値の **Sales** を対象とする空白行はありません。

また、そのビジュアルに City を追加するとします。 市区町村ごとの人口はわかっていますが、City に対して表示される **Sales** では、対応する **State** の **Sales** が単に繰り返されます。 このシナリオは通常、ここに示すように、列のグループ化が集計メジャーと関連付けられていない場合に発生します。

![州と都市の人口と売上、Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_10.png)

たとえば、ここですべての州の組み合わせとして新しい Sales テーブルを定義し、 **[フィールド]** リストに表示されるようにするとします。 同じビジュアルで、(新しいテーブルに) **State**、**Population** の合計、および **Sales** の合計が表示されます。

![州、人口、売上のビジュアル、Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_11.png)

ご覧のように、TX &mdash; **Sales** データはあるが "*Population*" データは不明 &mdash; と New York &mdash; **Population** データはわかっているが **Sales** データがない &mdash; が含まれます。 この回避策は最適ではなく、多くの問題を含んでいます。 多対多カーディナリティのリレーションシップの場合は、次のセクションで説明するように、発生する問題に対処します。

## <a name="use-a-relationship-with-a-many-many-cardinality-instead-of-the-workaround"></a>回避策ではなく、多対多カーディナリティのリレーションシップを使用する

2018 年 7 月バージョンの Power BI Desktop では、前に説明したもののようなテーブルを直接関連付けることができます。同様の回避策を利用する必要はありません。 リレーションシップのカーディナリティを "*多対多*" に設定できるようになりました。 この設定は、どちらのテーブルにも一意の値が含まれていないことを示しています。 そのようなリレーションシップでも、他のテーブルをフィルター処理するテーブルを制御できます。 または、テーブルで相互にフィルター処理を行う、双方向のフィルター処理を適用することができます。

Power BI Desktop では、いずれのテーブルにもリレーションシップ列に一意の値が含まれていないと判断された場合、カーディナリティは既定で "*多対多*" に設定されます。 このような場合は、リレーションシップの設定と、変更がデータの問題による意図しない結果ではないことを確認する警告メッセージが表示されます。

たとえば、CityData と Sales 間に直接リレーションシップを作成する &mdash;ここではフィルターのフローが CityData から Sales になるようにする必要があります&mdash; 場合、Power BI Desktop で **[リレーションシップの編集]** ダイアログ ボックスが表示されます。

![[リレーションシップの編集] ダイアログボックス、Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

その結果、 **[リレーションシップ]** ビューには、2 つのテーブル間に直接かつ多対多のリレーションシップが表示されるようになります。 **[フィールド]** リストでのテーブルの外観と、ビジュアルの作成時のその後の動作は、回避策を適用した場合と似ています。 回避策では、個別の State データを表示する追加のテーブルは表示されません。 前述のとおり、**State**、**Population**、および **Sales** データを表示するビジュアルが表示されます。

![State、Population、Sales のテーブル、Power BI Desktop](media/desktop-many-to-many-relationships/many-to-many-relationships_12.png)

"*多対多カーディナリティのリレーションシップ*" と、より一般的な "*多対一*" のリレーションシップの主な違いは、次のとおりです。

* 表示される値に、もう一方のテーブルの一致しない行を示す空白行が含まれません。 また、もう一方のテーブルのリレーションシップで使用される列が null である行を示す値も含まれません。
* 複数の行が関連する可能性があるため、`RELATED()` 関数を使用することはできません。
* テーブルに `ALL()` 関数を使用しても、多対多のリレーションシップによって関連付けられているもう一方のテーブルに適用されているフィルターは削除されません。 前の例では、以下に示すように定義されているメジャーでは、関連する CityData テーブルの列に対するフィルターは削除されません。

    ![スクリプトの例](media/desktop-many-to-many-relationships/many-to-many-relationships_13.png)

    **State**、**Sales**、および **Sales total** のデータを表示するビジュアルは、この図のようになります。

    ![テーブルのビジュアル](media/desktop-many-to-many-relationships/many-to-many-relationships_14.png)

前述の相違点に注意しながら、`ALL(<Table>)` を使用する計算 ("*合計に対する割合*" など) で、意図した結果が返されることを確認します。

## <a name="limitations-and-considerations"></a>制限事項と考慮事項

このリリースの "*多対多カーディナリティのリレーションシップ*" と複合モデルには、いくつかの制限事項があります。

次の Live Connect (多次元) ソースは、複合モデルでは使用できません。

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Power BI データセット
* Azure Analysis Services

DirectQuery を使用してこれらの多次元ソースに接続すると、別の DirectQuery ソースに接続することも、これをインポートしたデータと結合することもできません。

DirectQuery を使用する際の既存の制限は、"*多対多カーディナリティのリレーションシップ*" を使用する場合にも適用されます。 多くの制限事項が、テーブルのストレージ モードに応じて、テーブルごとに適用されるようになりました。 たとえば、インポートしたテーブルの計算列からは他のテーブルを参照できますが、DirectQuery テーブルの計算列からは引き続き同じテーブルの列しか参照できません。 モデル内のいずれかのテーブルが DirectQuery である場合、モデル全体に他の制限事項が適用されます。 たとえば、モデル内のいずれかのテーブルにストレージ モードの DirectQuery がある場合、そのモデルでは QuickInsights と Q&A 機能を使用できません。

## <a name="next-steps"></a>次の手順

複合モデルと DirectQuery について詳しくは、次の記事をご覧ください。
* [Power BI Desktop で複合モデルを使用する](desktop-composite-models.md)
* [Power BI Desktop のストレージ モード](desktop-storage-mode.md)
* [Power BI で DirectQuery を使用する](../connect-data/desktop-directquery-about.md)
* [Power BI データ ソース](../connect-data/power-bi-data-sources.md)
