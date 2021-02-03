---
title: DAX:フィルター引数として FILTER を使用しない
description: FILTER 関数をフィルター引数として使用する方法に関するガイダンス。
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 12/30/2019
ms.openlocfilehash: 74ddac5a3ac2fa5e6e0fae9f3fdf5c7f79ba22d3
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2021
ms.locfileid: "99088582"
---
# <a name="dax-avoid-using-filter-as-a-filter-argument"></a>DAX:フィルター引数として FILTER を使用しない

データ モデル作成者は、変更されたフィルター コンテキストで評価する必要がある DAX 式を記述することがよくあります。 たとえば、"高利益の商品" の売上を計算するメジャー定義を作成できます。 この計算については、この記事の後半で説明します。

> [!NOTE]
> この記事は、インポート テーブルにフィルターを適用するモデル計算に特に関連しています。

[CALCULATE](/dax/calculate-function-dax) と [CALCULATETABLE](/dax/calculatetable-function-dax) DAX 関数は、重要で便利な関数です。 これらを使用して、フィルターを削除または追加したり、リレーションシップ パスを変更したりする計算を作成できます。 これは、ブール式、テーブル式、または特殊なフィルター関数のいずれかであるフィルター引数を渡すことによって行います。 この記事では、ブール式とテーブル式についてのみ説明します。

テーブル式を使用して赤色の製品の売上を計算する次のメジャー定義について考えてみます。 これにより、**Product** テーブルに適用される可能性のあるすべてのフィルターが置き換えられます。

```dax
Red Sales =
CALCULATE(
    [Sales],
    FILTER('Product', 'Product'[Color] = "Red")
)
```

CALCULATE 関数で、[FILTER](/dax/filter-function-dax) DAX 関数によって返されるテーブル式を受け取り、**Product** テーブルの各行に対してフィルター式を評価します。 これにより、正しい結果 (赤色の製品の売上結果) を取得できます。 ただし、ブール式を使用すると、より効率的に実現できます。

テーブル式の代わりにブール式を使用した、強化されたメジャー定義を次に示します。 [KEEPFILTERS](/dax/keepfilters-function-dax) DAX 関数では、**Color** 列に適用されている既存のフィルターは保持され、上書きされることはありません。

```dax
Red Sales =
CALCULATE(
    [Sales],
    KEEPFILTERS('Product'[Color] = "Red")
)
```

可能な限り、フィルター引数をブール式として渡すことをお勧めします。 これは、インポート モデル テーブルがメモリ内の列ストアであるためです。 それらは、この方法で列を効率的にフィルター処理するように、明示的に最適化されます。

ただし、ブール式をフィルター引数として使用する場合に適用される制限があります。 それらは次のとおりです。

- 列を他の列と比較することはできません
- メジャーを参照することはできません
- 入れ子になった CALCULATE 関数は使用できません
- テーブルをスキャンまたは返す関数は使用できません

つまり、より複雑なフィルター要件にはテーブル式を使用することが必要になります。

ここで、別のメジャー定義を考えてみましょう。

```dax
High Margin Product Sales =
CALCULATE(
    [Sales],
    FILTER(
        'Product',
        'Product'[ListPrice] > 'Product'[StandardCost] * 2
    )
)
```

高利益の商品 (_high margin product_) の定義は、定価が標準コストの 2 倍を超えているものです。 この例では、FILTER 関数を使用する必要があります。 これは、フィルター式がブール式には複雑すぎるためです。

もう 1 つ別の例があります。 今回の要件は、利益を達成した月のみについて売上を計算することです。

```dax
Sales for Profitable Months =
CALCULATE(
    [Sales],
    FILTER(
        VALUES('Date'[Month]),
        [Profit] > 0)
    )
)
```

この例では、FILTER 関数をまた使用する必要があります。 これは、利益を達成できなかった月を除外するために、**Profit** メジャーを評価する必要があるためです。 ブール式をフィルター引数として使用する場合、ブール式の中でメジャーを使用することはできません。

## <a name="recommendations"></a>推奨事項

最適なパフォーマンスを得るには、可能な限り、ブール式をフィルター引数として使用することをお勧めします。

そのため、FILTER 関数は必要な場合にのみ使用してください。 それは複雑な列の比較のフィルター処理を行う場合に使用できます。 これらの列の比較には、次のものがあります。

- メジャー
- 他の列
- [OR](/dax/or-function-dax) DAX 関数、または OR 論理演算子 (| |) の使用

## <a name="next-steps"></a>次の手順

この記事に関する詳細については、次のリソースを参照してください。

- [Data Analysis Expressions (DAX) リファレンス](/dax/)
- [FILTER 関数 (DAX)](/dax/filter-function-dax)
- ラーニング パス:[Power BI Desktop で DAX を使用する](/learn/paths/dax-power-bi/)
- わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
- Power BI チームへのご提案は、 [Power BI を改善するためのアイデアをお寄せください](https://ideas.powerbi.com)