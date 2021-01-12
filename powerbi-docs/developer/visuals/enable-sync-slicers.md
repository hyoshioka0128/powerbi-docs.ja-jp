---
title: 埋め込み BI 分析情報を向上させるため、Power BI 埋め込み分析で Power BI ビジュアルのスライサー同期機能を有効にします。
description: この記事では、Power BI ビジュアルにスライサーの同期機能を追加する方法を説明します。 Power BI 埋め込み分析を使用して、より優れた埋め込み BI インサイトを有効にします。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: bd69e05bba3e9449f9fb6f07bd9625dfb1ea0c08
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2021
ms.locfileid: "97885289"
---
# <a name="sync-slicers-in-power-bi-visuals"></a>Power BI ビジュアルでのスライサーの同期

[スライサーの同期](../../visuals/power-bi-visualization-slicers.md)機能をサポートするには、カスタム スライサー視覚化で API バージョン 1.13.0 以降を使用する必要があります。

さらに、次のコードで示すように、*capabilities.json* ファイルでオプションを有効にする必要があります。

```json
{
    ...
    "supportsHighlight": true,
    "suppressDefaultTitle": true,
    "supportsSynchronizingFilterState": true,
    "sorting": {
        "default": {}
    }
}
```

*capabilities.json* ファイルを更新した後は、カスタム スライサー ビジュアルを選択したときに、 **[スライサーの同期]** オプション ウィンドウを表示できます。

> [!NOTE]
> スライサーの同期機能では、複数のフィールドはサポートされていません。 スライサーに複数のフィールド (**カテゴリ** または **メジャー**) がある場合、機能は無効になります。

![[スライサーの同期] ウィンドウ](media/enable-sync-slicers/sync-slicers-panel.png)

**[スライサーの同期]** ウィンドウでは、スライサーの表示とそのフィルター処理を複数のレポート ページに適用できることがわかります。