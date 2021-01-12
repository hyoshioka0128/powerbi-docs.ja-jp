---
title: 埋め込み BI 分析情報を向上させるための Power BI 埋め込み分析の supportsKeyboardFocus 機能
description: この記事では Power BI ビジュアルの supportsKeyboardFocus 機能の使用方法とその要件について説明します。 Power BI 埋め込み分析を使用して、より優れた埋め込み BI インサイトを有効にします。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 04/30/2020
ms.openlocfilehash: 5ba87db8118076de4bf13abc0280223f9f04f871
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887962"
---
# <a name="use-the-supportskeyboardfocus-feature"></a>supportsKeyboardFocus 機能を使用する

この記事では Power BI ビジュアルで `supportsKeyboardFocus` 機能を使用する方法について説明します。
`supportsKeyboardFocus` 機能を使用すると、キーボードのみを使用して、ビジュアルのデータ ポイントを移動できます。

ビジュアルのキーボード ナビゲーションの詳細については、「[キーボード ナビゲーション](../../create-reports/desktop-accessibility-consuming-tools.md#keyboard-navigation)」を参照してください。

## <a name="example"></a>例

`supportsKeyboardFocus` 機能を使用するビジュアルを開きます。 ビジュアル内の任意のデータ ポイントを選択し、Tab キーを押します。Tab キーを押すたびに、フォーカスが次のデータ ポイントに移動します。Enter キーを押して、強調表示されたデータ ポイントを選択します。

![Supports keyboard focus の例](./media/supportskeyboardfocus-feature/supports-keyboard-focus-example.png)

## <a name="requirements"></a>要件

この機能には、API v2.1.0 以上が必要です。

この機能は、画像ビジュアルを除くすべてのビジュアルに適用できます。

## <a name="usage"></a>使用

`supportsKeyboardFocus` 機能を使用するには、ビジュアルの *capabilities.json* ファイルに次のコードを追加します。
この機能により、キーボード ナビゲーションを使用してビジュアルにフォーカスを指定することができます。

```json
    {   
            ...
        "supportsKeyboardFocus": true
            ...
    }

```

## <a name="next-steps"></a>次の手順

アクセシビリティ機能の詳細については、「[アクセシビリティ対応の Power BI レポートを設計する](../../create-reports/desktop-accessibility-creating-reports.md)」を参照してください。

Power BI を開発してみるには、[Power BI の円形カード視覚化の開発](develop-circle-card.md)に関する記事を参照してください。
