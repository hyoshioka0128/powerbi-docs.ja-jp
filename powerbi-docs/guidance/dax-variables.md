---
title: DAX:変数を使用して数式を改善する
description: DAX 式での変数の使用に関するガイダンス。
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 11/23/2019
ms.openlocfilehash: 2448ac8b94465872e4224738162c6a252cafe56c
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96393602"
---
# <a name="dax-use-variables-to-improve-your-formulas"></a>DAX:変数を使用して数式を改善する

データ モデル管理者にとって、DAX 計算の記述とデバッグは困難な場合があります。 複雑な計算の要件には、多くの場合、複合式または複雑な式を記述することが必要になります。 複合式では、多数の入れ子になった関数を使用することや、場合によっては式ロジックを再利用することがあります。

DAX の数式で変数を使用すると、複雑で効率的な計算を作成できます。 変数によって次のことが可能です。

- [パフォーマンスの向上](#improve-performance)
- [読みやすさの向上](#improve-readability)
- [デバッグの簡略化](#simplify-debugging)
- [複雑さの軽減](#reduce-complexity)

この記事では、前年比 (YoY) での売上の増加を表すメジャーの例を使用して、最初の 3 つの利点について説明します  2(YoY での売上増加を求める数式は、期間売上から昨年の同じ期間の売上を引いて、昨年の同じ期間の売上で "_割る_" というものです)。

まず、次のメジャー定義から始めましょう。

```dax
Sales YoY Growth % =
DIVIDE(
    ([Sales] - CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))),
    CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))
)
```

このメジャーによって正しい結果が生成されますが、それをどのように改善できるかを見ていきましょう。

## <a name="improve-performance"></a>パフォーマンスの向上

この数式では、"昨年の同じ期間" を計算する式が繰り返されることに注意してください。 この数式は、Power BI で同じ式を 2 回評価する必要があるため、非効率的です。 変数を使用すると、メジャー定義をより効率的に行うことができます。

次のメジャー定義には改善が表されています。 式を使用して、"昨年の同じ期間" の結果を **SalesPriorYear** という名前の変数に代入しています。 その後、その変数を RETURN 式で 2 回使用しています。

```dax
Sales YoY Growth % =
VAR SalesPriorYear =
    CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))
RETURN
    DIVIDE(([Sales] - SalesPriorYear), SalesPriorYear)
```

このメジャーで引き続き正しい結果が生成され、クエリ時間はおよそ半分になります。

## <a name="improve-readability"></a>読みやすさの向上

前のメジャー定義において、選んだ変数名によって RETURN 式が理解しやすくなっていることに注意してください。 式は短く、自己記述型です。

## <a name="simplify-debugging"></a>デバッグの簡略化

変数は、数式のデバッグにも役立ちます。 変数に割り当てられた式をテストするには、変数を出力するように RETURN 式を一時的に書き直します。

次のメジャー定義では、**SalesPriorYear** 変数のみが返されます。 意図した RETURN 式がどのようにコメントアウトされているかに注目してください。 この手法を使用すると、デバッグが完了した後に簡単に元に戻すことができます。

```dax
Sales YoY Growth % =
VAR SalesPriorYear =
    CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))
RETURN
    --DIVIDE(([Sales] - SalesPriorYear), SalesPriorYear)
    SalesPriorYear
```

## <a name="reduce-complexity"></a>複雑さの軽減

以前のバージョンの DAX では、変数はまだサポートされていませんでした。 新しいフィルター コンテキストが導入された複雑な式では、外側のフィルター コンテキストを参照するために、[EARLIER](/dax/earlier-function-dax) または [EARLIEST](/dax/earliest-function-dax) という DAX 関数を使用する必要がありました。 残念ながら、データ モデル管理者には、これらの関数を理解して使用することが難しいと感じられました。

変数は常に、RETURN 式が適用されるフィルターの外側で評価されます。 このため、変更されたフィルター コンテキスト内で変数を使用すると、EARLIEST 関数と同じ結果が得られます。 したがって、EARLIER 関数や EARLIEST 関数を使用せずに済みます。 それは、複雑さが少なく、理解しやすい数式を記述できるようになったことを意味します。

**Subcategory** テーブルに追加された次のような計算列の定義があるとします。 **Subcategory Sales** 列の値に基づいて、製品サブカテゴリごとに順位を評価しています。

```dax
Subcategory Sales Rank =
COUNTROWS(
    FILTER(
        Subcategory,
        EARLIER(Subcategory[Subcategory Sales]) < Subcategory[Subcategory Sales]
    )
) + 1
```

"_現在の行コンテキスト内_" で **Subcategory Sales** 列の値を参照するために、EARLIER 関数が使用されています。

EARLIER 関数ではなく変数を使用して計算列の定義を改善できます。 **CurrentSubcategorySales** 変数を使用して **Subcategory Sales** 列の値を "_現在の行コンテキスト内_" で格納し、RETURN 式によって、変更されたフィルター コンテキスト内でそれを使用します。

```dax
Subcategory Sales Rank =
VAR CurrentSubcategorySales = Subcategory[Subcategory Sales]
RETURN
    COUNTROWS(
        FILTER(
            Subcategory,
            CurrentSubcategorySales < Subcategory[Subcategory Sales]
        )
    ) + 1
```

## <a name="next-steps"></a>次の手順

この記事に関する詳細については、次のリソースを参照してください。

- [Data Analysis Expressions (DAX) リファレンス](/dax/)
- [VAR](/dax/var-dax) DAX に関する記事
- ラーニング パス:[Power BI Desktop で DAX を使用する](/learn/paths/dax-power-bi/)
- わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
- Power BI チームへのご提案は、 [Power BI を改善するためのアイデアをお寄せください](https://ideas.powerbi.com)