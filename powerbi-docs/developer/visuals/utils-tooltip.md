---
title: Power BI ビジュアルでのツールヒント ユーティリティの使用の概要
description: この記事では、ツールヒント ユーティリティを使用して Power BI ビジュアルのツールヒントを簡単にカスタマイズする方法について説明します
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 02/14/2020
ms.openlocfilehash: 69650982bd3e71c235ffb09b00a99959bc02c231
ms.sourcegitcommit: 1428acb6334649fc2d3d8ae4c42cfbc17e8f7476
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/19/2020
ms.locfileid: "92197635"
---
# <a name="tooltip-utils"></a>ツールヒント ユーティリティ
この記事では、ツールヒント ユーティリティのインストール、インポート、使用について説明します。 このユーティリティは、Power BI ビジュアルのツールヒントをカスタマイズするのに役立ちます。

## <a name="requirements"></a>要件
パッケージを使用するには、次のものが必要です。
* [node.js](https://nodejs.org) (最新の LTS バージョンをお勧めします)
* [npm](https://www.npmjs.com/) (サポートされる最小バージョンは 3.0.0 です)
* [PowerBI-visuals-tools](https://www.npmjs.com/package/powerbi-visuals-tools) で作成されたカスタム ビジュアル

## <a name="installation"></a>インストール

パッケージをインストールするには、現在のビジュアルを使用して、ディレクトリ内で次のコマンドを実行する必要があります。

```bash
npm install powerbi-visuals-utils-tooltiputils --save
```
このコマンドを実行すると、パッケージがインストールされ、依存関係としてパッケージが ```package.json``` に追加されます

## <a name="usage"></a>使用法

> 使用ガイドでは、パッケージのパブリック API について説明されています。 パッケージの各パブリック インターフェイスについての説明といくつかの例が提供されています。

このパッケージには、ツールヒント アクションを処理するための `TooltipServiceWrapper` とメソッドを作成するための方法が用意されています。 ツールヒント インターフェイス `ITooltipServiceWrapper`、`TooltipEventArgs`、`TooltipEnabledDataPoint` を使用します。 

また、モバイル開発に関連する特定のメソッド (タッチ イベント ハンドラー) もあります (`touchEndEventName`、`touchStartEventName`、`usePointerEvents`)。

`TooltipServiceWrapper` では、ツールヒントを操作するための最も簡単な方法が提供されています。

このモジュールでは、次のインターフェイスと関数が提供されます。
* [ITooltipServiceWrapper](#itooltipservicewrapper)
  * [addTooltip](#itooltipservicewrapperaddtooltip)
  * [hide](#itooltipservicewrapperhide)

* "[インターフェイス](#interfaces)"
  * [TooltipEventArgs](#tooltipeventargs)
  * [TooltipEnabledDataPoint](#tooltipenableddatapoint)
  * [TooltipServiceWrapperOptions](#tooltipservicewrapperoptions)
* [タッチ イベント](#touch-events)

### `createTooltipServiceWrapper`
この関数では、ITooltipServiceWrapper のインスタンスが作成されます。

```typescript
function createTooltipServiceWrapper(tooltipService: ITooltipService, rootElement: Element, handleTouchDelay?: number,  getEventMethod?: () => MouseEvent): ITooltipServiceWrapper;
```

```ITooltipService``` は [IVisualHost](https://github.com/microsoft/PowerBI-visuals-tools/blob/master/templates/visuals/.api/v2.6.0/PowerBI-visuals.d.ts#L1335) で使用できます。

**例**

```typescript
import { createTooltipServiceWrapper } from "powerbi-visuals-utils-tooltiputils";

export class YourVisual implements IVisual {
    // implementation of IVisual.

    constructor(options: VisualConstructorOptions) {
        createTooltipServiceWrapper(
            options.host.tooltipService,
            options.element);

        // returns: an instance of ITooltipServiceWrapper.
    }
}
```

カスタム ビジュアルのコード例については、[こちら](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L391)を参照してください。

### `ITooltipServiceWrapper`
このインターフェイスでは、TooltipService のパブリック メソッドが記述されています。

```typescript
interface ITooltipServiceWrapper {
    addTooltip<T>(selection: d3.Selection<any, any, any, any>, getTooltipInfoDelegate: (args: TooltipEventArgs<T>) => powerbi.extensibility.VisualTooltipDataItem[], getDataPointIdentity?: (args: TooltipEventArgs<T>) => powerbi.visuals.ISelectionId, reloadTooltipDataOnMouseMove?: boolean): void;
    hide(): void;
}
```

#### `ITooltipServiceWrapper.addTooltip`

このメソッドでは、現在の選択範囲にツールヒントが追加されます。

```typescript
addTooltip<T>(selection: d3.Selection<any>, getTooltipInfoDelegate: (args: TooltipEventArgs<T>) => VisualTooltipDataItem[], getDataPointIdentity?: (args: TooltipEventArgs<T>) => ISelectionId, reloadTooltipDataOnMouseMove?: boolean): void;
```

**例**

```typescript
import { createTooltipServiceWrapper, TooltipEventArgs, ITooltipServiceWrapper, TooltipEnabledDataPoint } from "powerbi-visuals-utils-tooltiputils";

let bodyElement = d3.select("body");

let element = bodyElement
    .append("div")
    .style({
        "background-color": "green",
        "width": "150px",
        "height": "150px"
    })
    .classed("visual", true)
    .data([{
        tooltipInfo: [{
            displayName: "Power BI",
            value: 2016
        }]
    }]);

let tooltipServiceWrapper: ITooltipServiceWrapper = createTooltipServiceWrapper(tooltipService, bodyElement.get(0)); // tooltipService is from the IVisualHost.

tooltipServiceWrapper.addTooltip<TooltipEnabledDataPoint>(element, (eventArgs: TooltipEventArgs<TooltipEnabledDataPoint>) => {
    return eventArgs.data.tooltipInfo;
});

// You will see a tooltip if you mouseover the element.
```

カスタム ビジュアルのコード例については、[こちら](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L2931)を参照してください。

また、ガント カスタム ビジュアルでのツールヒントのカスタマイズに関する[こちら](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L573-L648)の例に注意してください

### `ITooltipServiceWrapper.hide`

このメソッドでは、ツールヒントが非表示にされます。

```typescript
hide(): void;
```

**例**

```typescript
import {createTooltipServiceWrapper} from "powerbi-visuals-utils-tooltiputils";

let tooltipServiceWrapper = createTooltipServiceWrapper(options.host.tooltipService, options.element); // options are from the VisualConstructorOptions.

tooltipServiceWrapper.hide();
```
### `Interfaces`
このインターフェイスは、TooltipServiceWrapper を作成して使用するときに使用されます。 また、[前のトピック](#itooltipservicewrapperaddtooltip)の例でも説明されています。

#### `TooltipEventArgs`
```typescript
interface TooltipEventArgs<TData> {
    data: TData;
    coordinates: number[];
    elementCoordinates: number[];
    context: HTMLElement;
    isTouchEvent: boolean;
}
```

#### `TooltipEnabledDataPoint`
```typescript
interface TooltipEnabledDataPoint {
    tooltipInfo?: powerbi.extensibility.VisualTooltipDataItem[];
}
```

#### `TooltipServiceWrapperOptions`
```typescript
interface TooltipServiceWrapperOptions {
    tooltipService: ITooltipService;
    rootElement: Element;
    handleTouchDelay: number;
    getEventMethod?: () => MouseEvent;
```

### `Touch events`

ツールヒント ユーティリティでは、複数のタッチ イベントを処理できるようになりました。これはモバイル開発に役ちます。

#### `touchStartEventName`
```typescript
function touchStartEventName(): string
```
このメソッドでは、タッチ開始イベント名が返されます。

#### `touchEndEventName`
```typescript
function touchEndEventName(): string
```
このメソッドでは、タッチ開始イベント名が返されます。

#### `usePointerEvents`
```typescript
function usePointerEvents(): boolean
```
このメソッドでは、ポインターに関連する、または関連しない、現在の touchStart イベントが返されます。
