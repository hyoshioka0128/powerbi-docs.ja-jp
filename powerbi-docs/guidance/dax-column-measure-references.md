---
title: DAX:列参照とメジャー参照
description: DAX 式でのメジャーの列の参照に関するガイダンス。
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/18/2019
ms.author: v-pemyer
ms.openlocfilehash: a98ee3ff33d21dd599ddfb11166a6870ad30e6e5
ms.sourcegitcommit: 2131f7b075390c12659c76df94a8108226db084c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2020
ms.locfileid: "87537575"
---
# <a name="dax-column-and-measure-references"></a>DAX:列参照とメジャー参照

データ モデラーとして、DAX 式ではモデル列とメジャーが参照されます。 列とメジャーは、常にモデル テーブルに関連付けられていますが、これらの関連付けはさまざまです。 そのため、式でそれらを参照する方法については、さまざまな推奨事項があります。

## <a name="columns"></a>列

列はテーブルレベル オブジェクトであり、列名はテーブル内で一意である必要があります。 そのため、同じ列名がモデル内で複数回使用され、これによって異なるテーブルに属する可能性があります。 もう 1 つルールがあります。列名は、同じテーブル内に存在するメジャー名または階層名と同じ名前にすることはできません。

一般に、DAX では、列への_完全修飾_参照を使用することが強制されません。 完全修飾参照は、列名の前にテーブル名が付いていることを意味します。

列名参照のみを使用した計算列の定義の例を次に示します。 **Sales** 列と **Cost** 列は、両方とも **Orders** という名前のテーブルに属しています。

```dax
Profit = [Sales] - [Cost]
```

完全修飾列参照を使用して、同じ定義を書き直すことができます。

```dax
Profit = Orders[Sales] - Orders[Cost]
```

ただし、Power BI によってあいまいさが検出された場合は、完全修飾列参照を使用する必要があります。 数式を入力すると、赤い波線とエラー メッセージが表示されます。 また、[LOOKUPVALUE](/dax/lookupvalue-function-dax) DAX 関数などの一部の DAX 関数では、完全修飾列を使用する必要があります。

常に列参照を完全修飾することをお勧めします。 その理由については、「[推奨事項](#recommendations)」セクションを参照してください。

## <a name="measures"></a>メジャー

メジャーは、モデルレベル オブジェクトです。 このため、メジャー名はモデル内で一意である必要があります。 ただし、 **[フィールド]** ウィンドウでは、1 つのモデル テーブルに関連付けられている各メジャーがレポート作成者に表示されます。 この関連付けは、見栄えの理由から設定されており、メジャーの**ホーム テーブル** プロパティを設定することで構成できます。 詳細については、[Power BI Desktop のメジャー (メジャーを整理する)](../transform-model/desktop-measures.md#organizing-your-measures) に関するページを参照してください。

式で完全修飾メジャーを使用することは可能です。 DAX intellisense であっても、提案が提供されます。 ただし、これは必須ではなく、推奨される方法でもありません。 メジャーのホーム テーブルを変更する場合は、それに対する完全修飾メジャー参照を使用するすべての式が中断されます。 次に、分割された各数式を編集して、メジャー参照を削除 (または更新) する必要があります。

メジャー参照を修飾しないことをお勧めします。 その理由については、「[推奨事項](#recommendations)」セクションを参照してください。

## <a name="recommendations"></a>推奨事項

推奨事項は、単純で、簡単に覚えられます。

- 常に完全修飾列参照を使用
- 完全修飾メジャー参照は使用しない

理由は次のとおりです。

- **数式の入力**: 解決すべきあいまいな参照がないため、式は受け入れられます。 また、完全修飾列参照を必要とするそれらの DAX 関数の要件を満たす必要があります。
- **堅牢性**: メジャーのホーム テーブル プロパティを変更しても、式は引き続き機能します。
- **読みやすさ**: 式がすばやく簡単に理解できるようになります。完全に修飾されているかどうかによって、列またはメジャーであることがすぐに確認できます。

## <a name="next-steps"></a>次の手順

この記事に関する詳細については、次のリソースを参照してください。

- [Data Analysis Expressions (DAX) リファレンス](/dax/)
- ラーニング パス:[Power BI Desktop で DAX を使用する](https://docs.microsoft.com/learn/paths/dax-power-bi/)
- わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
- Power BI チームへのご提案は、 [Power BI を改善するためのアイデアをお寄せください](https://ideas.powerbi.com)
