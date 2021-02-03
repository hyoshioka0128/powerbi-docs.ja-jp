---
title: 双方向のリレーションシップのガイダンス
description: 双方向フィルター処理のモデル リレーションシップを開発するためのガイダンスです。
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 03/02/2020
ms.openlocfilehash: 65c00504a0f46e0ae8d5e6e1cf6cfcad33197a89
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2021
ms.locfileid: "99087248"
---
# <a name="bi-directional-relationship-guidance"></a>双方向のリレーションシップのガイダンス

この記事は、Power BI Desktop を操作するデータ モデラーを対象としています。 双方向のモデル リレーションシップを作成する条件についてのガイダンスを提供します。 双方向のリレーションシップとは、"_両方向_" にフィルター処理を行うリレーションシップです。

[!INCLUDE [relationships-prerequisite-reading](includes/relationships-prerequisite-reading.md)]

一般に、双方向のリレーションシップの使用は最小限に抑えることをお勧めします。 これらはモデルのクエリ パフォーマンスに悪影響を及ぼす場合があり、またレポート ユーザーに混乱をもたらす可能性があります。

双方向のフィルター処理によって特定の要件を解決できる 3 つのシナリオがあります。

- [特殊なモデル リレーションシップ](#special-model-relationships)
- ["データあり" のスライサー項目](#slicer-items-with-data)
- [ディメンション間の分析](#dimension-to-dimension-analysis)

## <a name="special-model-relationships"></a>特殊なモデル リレーションシップ

双方向のリレーションシップは、次の 2 つの特殊なモデル リレーションシップの種類を作成するときに重要な役割を果たします。

- **一対一**:すべての一対一のリレーションシップは双方向である必要があります。それ以外に構成することはできません。 一般に、この種類のリレーションシップを作成することはお勧めしません。 詳細な説明と代替設計については、「[一対一のリレーションシップのガイダンス](relationships-one-to-one.md)」をご覧ください。
- **多対多**:2 つのディメンションの種類のテーブルを関連付ける場合は、ブリッジング テーブルが必要です。 フィルターがブリッジング テーブルを越えて伝達されるようにするには、双方向のフィルターが必要です。 詳細については、[多対多のリレーションシップのガイダンス (多対多ディメンションを関連付ける)](relationships-many-to-many.md#relate-many-to-many-dimensions) に関する記事をご覧ください。

## <a name="slicer-items-with-data"></a>"データあり" のスライサー項目

双方向のリレーションシップにより、データが存在する場所に項目が制限されたスライサーを提供できます。 (Excel のピボットテーブルとスライサーに慣れている場合、これは Power BI データセットまたは Analysis Services モデルをデータのソースにするときの既定の動作です。)その意味を説明するために、まず次のモデル図について考えてみます。

![3 つのテーブルを含むモデルを示す図。 設計については、次の段落で説明します。](media/relationships-bidirectional-filtering/sales-model-diagram.png)

最初のテーブルには **Customer** という名前が付けられ、次の 3 つの列が含まれています:**Country-Region**、**Customer**、**CustomerCode**。 2 番目のテーブルには **Product** という名前が付けられ、次の 3 つの列が含まれています:**Color**、**Product**、**SKU**。 3 番目のテーブルには **Sales** という名前が付けられ、次の 4 つの列が含まれています:**CustomerCode**、**OrderDate**、**Quantity**、**SKU**。 **Customer** テーブルと **Product** テーブルはディメンションの種類のテーブルであり、それぞれが **Sales** テーブルに対して一対多のリレーションシップを持っています。 各リレーションシップでは、一方向にフィルター処理されます。

双方向のリレーションシップの動作のしくみを説明するのに役立つように、モデル図が変更されてテーブル行が表示されています。 この記事に含まれるすべての例は、このデータに基づいています。

> [!NOTE]
> Power BI Desktop モデル図にテーブル行を表示することはできません。 この記事では、わかりやすい例による説明をサポートするためにこのようにしています。

![モデルでテーブル行が表示されるようになったことを示す図。 行の詳細については、次の段落で説明します。](media/relationships-bidirectional-filtering/sales-model-diagram-rows.png)

3 つのテーブルの行の詳細については、次の箇条書きで説明します。

- **Customer** テーブルには、次の 2 つの行があります。
  - **CustomerCode** CUST-01、**Customer** 顧客 1、**Country-Region** 米国
  - **CustomerCode** CUST-02、**Customer** 顧客 2、**Country-Region** オーストラリア
- **Product** テーブルには、次の 3 つの行があります。
  - **SKU** CL-01、**Product** T シャツ、**Color** 緑
  - **SKU** CL-02、**Product** ジーンズ、**Color** 青
  - **SKU** AC-01、**Product** 帽子、**Color** 青
- **Sales** テーブルには、3 つの行があります。
  - **OrderDate** 2019 年 1 月 1 日、**CustomerCode** CUST-01、**SKU** CL-01、**Quantity** 10
  - **OrderDate** 2019 年 2 月 2 日、**CustomerCode** CUST-01、**SKU** CL-02、**Quantity** 20
  - **OrderDate** 2019 年 3 月 3 日、**CustomerCode** CUST-02、**SKU** CL-01、**Quantity** 30

ここで、次のレポート ページについて考えてみましょう。

![3 つのビジュアルを含むレポート ページを示す図。 その詳細については、次の段落で説明します。](media/relationships-bidirectional-filtering/sales-report-no-bi-directional-filter.png)

このページは、2 つのスライサーとカード ビジュアルで構成されています。 最初のスライサーは **Country-Region** 用です。これには次の 2 つの項目があります:オーストラリア、米国。 現在は、オーストラリアでスライスされています。 2 番目のスライサーは **Product** 用です。これには次の 3 つの項目があります:帽子、ジーンズ、T シャツ。 項目は選択されていません (つまり、フィルター処理されている "_製品はありません_")。 カード ビジュアルには、30 という数量が表示されています。

レポート ユーザーがオーストラリアでスライスするときに、**Product** スライサーを制限して、データがオーストラリアの売上に "_関連している_" 項目を表示するようにすることをお勧めします。 これが、"データあり" のスライサー項目を表示するという意味です。 この動作を実現するには、**Product** テーブルと **Sales** テーブル間のリレーションシップを構成して、双方向のフィルター処理を行います。

![Product および Sales テーブル間のリレーションシップが双方向になったモデルを示す図。](media/relationships-bidirectional-filtering/sales-model-diagram-rows-bi-directional-filter.png)

**Product** スライサーには、1 つの項目が表示されるようになりました。T シャツです。 この項目は、オーストラリアの顧客に販売された唯一の製品を表しています。

![3 つの視覚エフェクトが含まれ、Product が強調表示されているレポート ページを示す図。その詳細については、次の段落で説明します。](media/relationships-bidirectional-filtering/sales-report-bi-directional-filter.png)

まず、この設計がご自分のレポート ユーザーに適しているかどうかを慎重に検討することをお勧めします。 このエクスペリエンスはわかりにくいと考えるレポート ユーザーもいます。 このようなユーザーは、別のスライサーを操作するとスライサー項目が動的に表示されたり非表示になったりする理由を理解できません。

"データあり" のスライサー項目を表示することに決めた場合、双方向のリレーションシップは構成しないことをお勧めします。 双方向のリレーションシップでは、より多くの処理が必要になるため、クエリ パフォーマンスに悪影響を及ぼす可能性があります。モデル内の双方向のリレーションシップの数が増える場合は、特にそうです。

同じ結果を得ることができる、より優れた方法があります。双方向のフィルターを使用する代わりに、ビジュアル レベルのフィルターを **Product** スライサー自体に適用できます。

次に、**Product** テーブルと **Sales** テーブル間のリレーションシップが両方向にフィルター処理されなくなった場合を考えてみましょう。 また、次のメジャー定義が **Sales** テーブルに追加されています。

```dax
Total Quantity = SUM(Sales[Quantity])
```

**Product** の "データあり" のスライサー項目を表示するには、**Total Quantity** メジャーによって、"空白でない" 条件を使用してフィルター処理するだけです。

![Product スライサー用の [フィルター] ペインが、"合計数量が空ではない" によってフィルター処理されるようになったことを示す図。](media/relationships-bidirectional-filtering/filter-product-slicer-measure-is-not-blank.png)

## <a name="dimension-to-dimension-analysis"></a>ディメンション間の分析

双方向のリレーションシップを使用する別のシナリオでは、ファクトの種類のテーブルがブリッジング テーブルのように扱われます。 これにより、ディメンションの種類のテーブル データを、異なるディメンションの種類のテーブルのフィルター コンテキスト内で分析できるようになります。

この記事に含まれているモデルの例を使って、次の質問に答える方法を考えてみましょう。

- オーストラリアの顧客に販売された色の数はいくつですか?
- ジーンズを購入した国の数はいくつですか?

どちらの質問にも、ファクトの種類のブリッジング テーブルにデータを要約 "_することなく_" 答えることができます。 ただし、そのためには、ディメンションの種類のテーブル間でフィルターが伝達される必要があります。 ファクトの種類のテーブルを介してフィルターが伝達されれば、[DISTINCTCOUNT](/dax/distinctcount-function-dax) DAX 関数 (および、場合によっては [MIN](/dax/min-function-dax) および [MAX](/dax/max-function-dax) DAX 関数) を使用して、ディメンションの種類のテーブル列の要約を作成できます。

ファクトの種類のテーブルはブリッジング テーブルのように動作するため、多対多のリレーションシップのガイダンスに従って、2 つのディメンションの種類のテーブルを関連付けることができます。 両方向でフィルター処理を行うには、少なくとも 1 つのリレーションシップを構成する必要があります。 詳細については、[多対多のリレーションシップのガイダンス (多対多ディメンションを関連付ける)](relationships-many-to-many.md#relate-many-to-many-dimensions) に関する記事をご覧ください。

ただし、この記事で既に説明したように、この設計によってパフォーマンスや、["データあり" のスライサー項目](#slicer-items-with-data)に関連するユーザー エクスペリエンスの結果が悪影響を受ける可能性があります。 そのため、代わりに [CROSSFILTER](/dax/crossfilter-function) DAX 関数を使用することで、"_メジャーの定義で_" 双方向のフィルター処理をアクティブにすることをお勧めします。 CROSSFILTER 関数を使用すると、式の評価中にフィルターの方向を変更したり、さらにはリレーションシップを無効にしたりすることができます。

次のメジャーの定義が **Sales** テーブルに追加されているとします。 この例では、**Customer** テーブルと **Sales** テーブル間のモデル リレーションシップが、"_一方向_" でフィルター処理されるように構成されています。

```dax
Different Countries Sold =
CALCULATE(
    DISTINCTCOUNT(Customer[Country-Region]),
    CROSSFILTER(
        Customer[CustomerCode],
        Sales[CustomerCode],
        BOTH
    )
)
```

**Different Countries Sold** メジャー式の評価中に、**Customer** テーブルと **Sales** テーブル間のリレーションシップが両方向にフィルター処理されます。

次のテーブル ビジュアルは、販売された各製品の統計情報を表示しています。 **Quantity** 列は、単純に数量の合計です。 **Different Countries Sold** 列は、その製品を購入したすべての顧客の、国/地域の値の重複しない数を表します。

![テーブル ビジュアルに 2 つの製品が一覧表示されていることを示す図。 "Different Countries Sold" 列では、ジーンズは 1、T シャツは 2 です。](media/relationships-bidirectional-filtering/country-sales-crossfilter-function.png)

## <a name="next-steps"></a>次の手順

この記事に関する詳細については、次のリソースを参照してください。

- [Power BI Desktop でのモデル リレーションシップ](../transform-model/desktop-relationships-understand.md)
- [Power BI のスター スキーマおよび重要性について](star-schema.md)
- [一対一のリレーションシップのガイダンス](relationships-one-to-one.md)
- [多対多のリレーションシップのガイダンス](relationships-many-to-many.md)
- [リレーションシップのトラブルシューティング ガイダンス](relationships-troubleshoot.md)
- わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
- Power BI チームへのご提案は、 [Power BI を改善するためのアイデアをお寄せください](https://ideas.powerbi.com/)