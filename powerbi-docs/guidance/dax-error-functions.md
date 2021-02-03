---
title: DAX:エラー関数の適切な使用方法
description: DAX エラー関数を使用する場合のガイダンスです。
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 09/26/2019
ms.openlocfilehash: c0766a989ea3dbfe42620fd53b4c49d6144b4c5f
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2021
ms.locfileid: "99088467"
---
# <a name="dax-appropriate-use-of-error-functions"></a>DAX:エラー関数の適切な使用方法

データ モデラーとして、評価時エラーを生成する可能性がある DAX 式を記述するときは、2 つの便利な DAX 関数の使用を検討してください。

- [ISERROR](/dax/iserror-function-dax) 関数。これは式を 1 つ受け取り、その式でエラーが発生すると TRUE を返します。
- [IFERROR](/dax/iferror-function-dax) 関数。これは 2 つの式を受け取ります。 最初の式でエラーが発生した場合は、2 つ目の式の値が返されます。 これは実際には、ISERROR 関数を [IF](/dax/if-function-dax) 関数内で入れ子にしたものをより最適化して実装したものになります。

しかしながら、これらの関数は便利であり、わかりやすい式を記述するときに役立ちますが、計算のパフォーマンスを大幅に下げる可能性もあります。 これらの関数により必要なストレージ エンジン スキャンの数が増えることが理由として考えられます。

評価時エラーのほとんどは、予期しない BLANK 値、ゼロ値、無効なデータ型変換によるものです。

## <a name="recommendations"></a>推奨事項

ISERROR 関数と IFERROR 関数の使用は避けることをお勧めします。 代わりに、モデルを開発し、式を記述するとき、防御的な方針を適用してください。 方針として考えられるもの:

- **質の高いデータがモデルに読み込まれるようにする:** Power Query 変換を使用して、無効な値または欠損値を削除または置換し、正しいデータ型を設定します。 Power Query 変換は、無効なデータ変換などのエラーが発生したとき、行をフィルター処理する目的でも利用できます。

    データ品質は、モデル列の **Is Nullable** プロパティをオフに設定しても制御できます。これにより、BLANK が見つかると、データ更新が失敗します。 このエラーが発生した場合、更新が成功した結果として読み込まれたデータはテーブル内に残ります。
- **IF 関数を使用する:** IF 関数の論理テスト式によりエラー結果が発生するかどうかを判断できます。 ISERROR 関数と IFERROR 関数と同様に、この関数も追加のストレージ エンジン スキャンを発生させる可能性はありますが、エラーを発生させる必要がないため、ISERROR 関数と IFERROR 関数よりもパフォーマンスが向上する可能性が高くなります。
- **エラートレラントな関数を使用する:** 一部の DAX 関数では、エラー状態がテストされ、補正が行われます。 そのような関数では、代わりに返される代替結果を入力できます。 たとえば、[DIVIDE](/dax/divide-function-dax) 関数があります。 この関数の追加のガイダンスについては、「[DAX: DIVIDE 関数と除算演算子 (/)](dax-divide-function-operator.md)」の記事をご覧ください。

## <a name="example"></a>例

次のメジャー式では、エラーが発生するかどうかがテストされます。 この場合 (IF 関数で value-if-false 式を指定しない場合)、BLANK が返されます。

```dax
Profit Margin
= IF(ISERROR([Profit] / [Sales]))
```

このメジャー式の次のバージョンは、IF 関数と ISERROR 関数の代わりに IFERROR 関数を使用することで改善されています。

```dax
Profit Margin
= IFERROR([Profit] / [Sales], BLANK())
```

ただし、このメジャー式の最終バージョンでも結果は同じになりますが、より効率的で、より洗練された方法になります。

```dax
Profit Margin
= DIVIDE([Profit], [Sales])
```

## <a name="next-steps"></a>次の手順

この記事に関する詳細については、次のリソースを参照してください。

- [Data Analysis Expressions (DAX) リファレンス](/dax/)

- ラーニング パス:[Power BI Desktop で DAX を使用する](/learn/paths/dax-power-bi/)
- わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
- Power BI チームへのご提案は、 [Power BI を改善するためのアイデアをお寄せください](https://ideas.powerbi.com)