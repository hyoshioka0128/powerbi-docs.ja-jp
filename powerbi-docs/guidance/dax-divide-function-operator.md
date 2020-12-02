---
title: DAX:DIVIDE 関数と除算演算子 (/)
description: DAX DIVIDE 関数を使用する場合のガイダンスです。
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 09/09/2019
ms.openlocfilehash: ece1c0d939ef521b20142acb753de7b7554e870a
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96394131"
---
# <a name="dax-divide-function-vs-divide-operator-"></a>DAX:DIVIDE 関数と除算演算子 (/)

データ モデラーとして、分子を分母で除算する DAX 式を記述する場合に、[DIVIDE](/dax/divide-function-dax) 関数または除算演算子 (/ - スラッシュ) を使用することを選択できます。

DIVIDE 関数を使用する場合は、分子と分母の式で渡す必要があります。 必要に応じて、_別の結果_ を表す値を渡すこともできます。

```dax
DIVIDE(<numerator>, <denominator> [,<alternateresult>])
```

DIVIDE 関数は、ゼロ除算を自動的に処理するように設計されています。 代替結果が渡されず、分母がゼロまたは空白の場合、関数は空白を返します。 代替結果が渡された場合は、BLANK の代わりにそれが返されます。

DIVIDE 関数では、最初に分母の値をテストする必要がないため、便利です。 この関数は、分母の値のテストにおいて、[IF](/dax/if-function-dax) 関数よりも最適化されています。 0 での除算のチェックは高コストであるため、パフォーマンスが大きく向上します。 さらに DIVIDE を使用することで、より簡潔で洗練された式になります。

## <a name="example"></a>例

次のメジャー式は安全な除算を行いますが、4 つの DAX 関数を使用します。

```dax
Profit Margin =
IF(
    OR(
        ISBLANK([Sales]),
        [Sales] == 0
    ),
    BLANK(),
    [Profit] / [Sales]
)
```

このメジャー式では、同じ結果が得られますが、より効率性が高く洗練されています。

```dax
Profit Margin =
DIVIDE([Profit], [Sales])
```

## <a name="recommendations"></a>推奨事項

分母がゼロまたは空白を返す _可能性がある_ 式である場合は常に、DIVIDE 関数を使用することをお勧めします。

分母が定数値の場合は、除算演算子を使用することをお勧めします。 この場合、除算は成功することが保証され、不要なテストを回避するため、式のパフォーマンスが向上します。

DIVIDE 関数で代替値を返す必要があるかどうかを慎重に検討してください。 メジャーの場合は通常、空白を返すため、より優れたデザインとなります。 空白を返すことが良いのは、集計が空白の場合、既定ではレポートのビジュアルでグループ化が削除されるためです。 これにより、データが存在するグループにビジュアルを集中させることができます。 必要に応じて、[[データのない項目を表示する]](../create-reports/desktop-show-items-no-data.md) オプションを有効にすることで、フィルター コンテキスト内の (値または空白を返す) すべてのグループを表示するようにビジュアルを構成できます。

## <a name="next-steps"></a>次の手順

この記事に関する詳細については、次のリソースを参照してください。

- [Data Analysis Expressions (DAX) リファレンス](/dax/)
- ラーニング パス:[Power BI Desktop で DAX を使用する](/learn/paths/dax-power-bi/)
- わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
- Power BI チームへのご提案は、 [Power BI を改善するためのアイデアをお寄せください](https://ideas.powerbi.com)