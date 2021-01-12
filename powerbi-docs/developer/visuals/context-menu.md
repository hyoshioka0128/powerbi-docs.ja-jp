---
title: 埋め込み BI 分析情報を向上させるために、Power BI 埋め込み分析で Power BI ビジュアルにコンテキスト メニューを追加する
description: Power BI の視覚化にコンテキスト メニューを追加する方法について説明します。 Power BI 埋め込み分析を使用して、より優れた埋め込み BI インサイトを有効にします。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: 1c19ba94588628e002cdb9e65f59bd4182020e1c
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888698"
---
# <a name="add-context-menu-to-power-bi-visual"></a>Power BI ビジュアルにコンテキスト メニューを追加する

`selectionManager.showContextMenu()` とパラメーター `selectionId` と (`{x:, y:}` オブジェクトとしての) 位置を使用して、ビジュアル用のコンテキスト メニューを Power BI に表示させることができます。

> [!IMPORTANT]
> この `selectionManager.showContextMenu()` は、Visuals API 2.2.0 で導入されました。

通常は、参照用のサンプル BarChart に追加されている右クリック イベント (タッチ デバイスの場合は長押し) Context-Menu として追加されます。

```typescript
    public update(options: VisualUpdateOptions) {
        //...
        //handle context menu
        this.svg.on('contextmenu', () => {
            const mouseEvent: MouseEvent = d3.event as MouseEvent;
            const eventTarget: EventTarget = mouseEvent.target;
            let dataPoint = d3.select(eventTarget).datum();
            this.selectionManager.showContextMenu(dataPoint? dataPoint.selectionId : {}, {
                x: mouseEvent.clientX,
                y: mouseEvent.clientY
            });
            mouseEvent.preventDefault();
        });
```
