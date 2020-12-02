---
title: DAX:COUNT の代わりに COUNTROWS を使用する
description: COUNTROWS 関数を使用する場合のガイダンスです。
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 11/23/2019
ms.openlocfilehash: 1a2b8c6450cfd855a0018fb64dd385a0db6e350f
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96394200"
---
# <a name="dax-use-countrows-instead-of-count"></a>DAX:COUNT の代わりに COUNTROWS を使用する

データ モデル作成者は、テーブル行をカウントする DAX 式を記述する必要が生じることがあります。 テーブルは、モデル テーブル、またはテーブルを返す式である場合があります。

要件は次の 2 つの方法で満たすことができます。 [COUNT](/dax/count-function-dax) 関数を使用して列の値をカウントできます。または、[COUNTROWS](/dax/countrows-function-dax) 関数を使用してテーブル行をカウントできます。 どちらの関数でも、カウントされた列に BLANK が含まれていない場合、同じ結果が得られます。

次のメジャー定義は、その例を示しています。 これにより、**OrderDate** 列の値の数が計算されます。

```dax
Sales Orders =
COUNT(Sales[OrderDate])
```

**Sales** テーブルの粒度が販売注文ごとに 1 行であり、**OrderDate** 列に BLANK が含まれていない場合、メジャーによって正しい結果が返されます。

ただし、次のメジャー定義の方がソリューションとして適切です。

```dax
Sales Orders =
COUNTROWS(Sales)
```

2 番目のメジャー定義の方が優れている理由には次の 3 つがあります。

- より効率性が高いので、パフォーマンスが向上します。
- テーブルの列に含まれている BLANK は考慮されません。
- 自己記述される程度に、数式の目的がより明確です。

## <a name="recommendation"></a>推奨事項

テーブルの行をカウントする必要がある場合は、常に COUNTROWS 関数を使用することをお勧めします。

## <a name="next-steps"></a>次の手順

この記事に関する詳細については、次のリソースを参照してください。

- [Data Analysis Expressions (DAX) リファレンス](/dax/)
- ラーニング パス:[Power BI Desktop で DAX を使用する](/learn/paths/dax-power-bi/)
- わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
- Power BI チームへのご提案は、 [Power BI を改善するためのアイデアをお寄せください](https://ideas.powerbi.com)