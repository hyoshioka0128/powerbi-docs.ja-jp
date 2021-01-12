---
title: 埋め込み BI 分析情報を向上させるための、Power BI 埋め込み分析の Power BI ビジュアルでの SVG ユーティリティの使用の概要
description: この記事では、SVG ユーティリティを使用して、Power BI ビジュアルの SVG 操作を簡略化する方法について説明します。 Power BI 埋め込み分析を使用して、より優れた埋め込み BI インサイトを有効にします。
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: cf798ae13d874e354f6941d50982bfe26d73424d
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887755"
---
# <a name="svg-utils"></a>SVG ユーティリティ

SVGUtils は、Power BI ビジュアルの SVG 操作を簡略化するための一連の関数とクラスです。

## <a name="installation"></a>インストール

パッケージをインストールするには、現在のビジュアルを使用して、ディレクトリ内で次のコマンドを実行する必要があります。

```bash
npm install powerbi-visuals-utils-svgutils --save
```

## <a name="cssconstants"></a>CssConstants

`CssConstants` モジュールでは、クラス セレクターを操作するための特殊関数とインターフェイスが提供されます。

`powerbi.extensibility.utils.svg.CssConstants` モジュールでは、次の関数とインターフェイスが提供されます。

## <a name="classandselector"></a>ClassAndSelector

このインターフェイスでは、クラス セレクターの共通プロパティが記述されます。

```typescript
interface ClassAndSelector {
  class: string;
  selector: string;
}
```

### <a name="createclassandselector"></a>createClassAndSelector

この関数では、指定したクラス名で ClassAndSelector のインスタンスが作成されます。

```typescript
function createClassAndSelector(className: string): ClassAndSelector;
```

例:

```typescript
import { CssConstants } from "powerbi-visuals-utils-svgutils";
import createClassAndSelector = CssConstants.createClassAndSelector;
import ClassAndSelector = CssConstants.ClassAndSelector;

let divSelector: ClassAndSelector = createClassAndSelector("sample-block");

divSelector.selector === ".sample-block"; // returns: true
divSelector.class === "sample-block"; // returns: true
```

## <a name="manipulation"></a>manipulation

`manipulation` では、SVG の transform プロパティと共に使用するための文字列を生成する特殊関数がいくつか提供されます。

このモジュールには、次の関数が用意されています。

### <a name="translate"></a>translate

この関数では、SVG の transform プロパティと共に使用するための translate 文字列が作成されます。

```typescript
function translate(x: number, y: number): string;
```

例:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translate(100, 100);

// returns: translate(100,100)
```

### <a name="translatexwithpixels"></a>translateXWithPixels

この関数では、SVG の transform プロパティと共に使用するための translateX 文字列が作成されます。

```typescript
function translateXWithPixels(x: number): string;
```

例:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translateXWithPixels(100);

// returns: translateX(100px)
```

### <a name="translatewithpixels"></a>translateWithPixels

この関数では、SVG の transform プロパティと共に使用するための translate 文字列が作成されます。

```typescript
function translateWithPixels(x: number, y: number): string;
```

例:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translateWithPixels(100, 100);

// returns: translate(100px,100px)
```

### <a name="translateandrotate"></a>translateAndRotate

この関数では、SVG の transform プロパティと共に使用するための translate-rotate 文字列が作成されます。

```typescript
function translateAndRotate(
  x: number,
  y: number,
  px: number,
  py: number,
  angle: number
): string;
```

例:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translateAndRotate(100, 100, 50, 50, 35);

// returns: translate(100,100) rotate(35,50,50)
```

### <a name="scale"></a>scale

この関数では、CSS の transform プロパティと共に使用するための scale 文字列が作成されます。

```typescript
function scale(scale: number): string;
```

例:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.scale(50);

// returns: scale(50)
```

### <a name="transformorigin"></a>transformOrigin

この関数では、CSS の transform-origin プロパティと共に使用するための transform-origin 文字列が作成されます。

```typescript
function transformOrigin(xOffset: string, yOffset: string): string;
```

例:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.transformOrigin(5, 5);

// returns: 5 5
```

### <a name="flushalld3transitions"></a>flushAllD3Transitions

この関数では、D3 のすべての移行を強制的に完了させます。

```typescript
function flushAllD3Transitions(): void;
```

例:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.flushAllD3Transitions();

// forces every transition of D3 to complete
```

### <a name="parsetranslatetransform"></a>parseTranslateTransform

この関数では、値 "translate (x, y)" を使用して transform 文字列を解析します。

```typescript
function parseTranslateTransform(input: string): { x: string; y: string };
```

例:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.parseTranslateTransform("translate(100px,100px)");

// returns: { "x":"100px", "y":"100px" }
```

### <a name="createarrow"></a>createArrow

この関数では矢印が作成されます。

```typescript
function createArrow(
  width: number,
  height: number,
  rotate: number
): { path: string; transform: string };
```

例:

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.createArrow(10, 20, 5);

/* returns: {
    "path": "M0 0L0 20L10 10 Z",
    "transform": "rotate(5 5 10)"
}*/
```

## <a name="rect"></a>Rect

`Rect` モジュールでは、四角形を操作するための特殊関数がいくつか提供されます。

このモジュールには、次の関数が用意されています。

### <a name="getoffset"></a>getOffset

この関数では四角形のオフセットが返されます。

```typescript
function getOffset(rect: IRect): IPoint;
```

例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getOffset({ left: 25, top: 25, width: 100, height: 100 });

/* returns: {
    x: 25,
    y: 25
}*/
```

### <a name="getsize"></a>getSize

この関数では四角形のサイズが返されます。

```typescript
function getSize(rect: IRect): ISize;
```

例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getSize({ left: 25, top: 25, width: 100, height: 100 });

/* returns: {
    width: 100,
    height: 100
}*/
```

### <a name="setsize"></a>setSize

この関数では四角形のサイズが変更されます。

```typescript
function setSize(rect: IRect, value: ISize): void;
```

例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

let rectangle = { left: 25, top: 25, width: 100, height: 100 };

Rect.setSize(rectangle, { width: 250, height: 250 });

// rectangle === { left: 25, top: 25, width: 250, height: 250 }
```

### <a name="right"></a>right

この関数では四角形の右の位置が返されます。

```typescript
function right(rect: IRect): number;
```

例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.right({ left: 25, top: 25, width: 100, height: 100 });

// returns: 125
```

### <a name="bottom"></a>下

この関数では四角形の下の位置が返されます。

```typescript
function bottom(rect: IRect): number;
```

例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.bottom({ left: 25, top: 25, width: 100, height: 100 });

// returns: 125
```

### <a name="topleft"></a>topLeft

この関数では四角形の左上の位置が返されます。

```typescript
function topLeft(rect: IRect): IPoint;
```

例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.topLeft({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 25, y: 25 }
```

### <a name="topright"></a>topRight

この関数では四角形の右上の位置が返されます。

```typescript
function topRight(rect: IRect): IPoint;
```

例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.topRight({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 125, y: 25 }
```

### <a name="bottomleft"></a>bottomLeft

この関数では四角形の左下の位置が返されます。

```typescript
function bottomLeft(rect: IRect): IPoint;
```

例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.bottomLeft({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 25, y: 125 }
```

### <a name="bottomright"></a>bottomRight

この関数では四角形の右下の位置が返されます。

```typescript
function bottomRight(rect: IRect): IPoint;
```

### <a name="example"></a>例

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.bottomRight({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 125, y: 125 }
```

### <a name="clone"></a>clone

この関数では四角形のコピーが作成されます。

```typescript
function clone(rect: IRect): IRect;
```

例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.clone({ left: 25, top: 25, width: 100, height: 100 });

/* returns: {
    left: 25, top: 25, width: 100, height: 100}
*/
```

### <a name="tostring"></a>toString

この関数では、四角形が文字列に変換されます。

```typescript
function toString(rect: IRect): string;
```

例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.toString({ left: 25, top: 25, width: 100, height: 100 });

// returns: {left:25, top:25, width:100, height:100}
```

### <a name="offset"></a>offset

この関数では、指定されたオフセットが四角形に適用されます。

```typescript
function offset(rect: IRect, offsetX: number, offsetY: number): IRect;
```

例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.offset({ left: 25, top: 25, width: 100, height: 100 }, 50, 50);

/* returns: {
    left: 75,
    top: 75,
    width: 100,
    height: 100
}*/
```

### <a name="add"></a>add

この関数では、最初の四角形が 2 番目の四角形に追加されます。

```typescript
function add(rect: IRect, rect2: IRect): IRect;
```

例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.add(
  { left: 25, top: 25, width: 100, height: 100 },
  { left: 50, top: 50, width: 75, height: 75 }
);

/* returns: {
    left: 75,
    top: 75,
    height: 175,
    width: 175
}*/
```

### <a name="getclosestpoint"></a>getClosestPoint

この関数では、指定されたポイントに対して、四角形の最も近いポイントが返されます。

```typescript
function getClosestPoint(rect: IRect, x: number, y: number): IPoint;
```

例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getClosestPoint({ left: 0, top: 0, width: 100, height: 100 }, 50, 50);

/* returns: {
    x: 50,
    y: 50
}*/
```

### <a name="equal"></a>equal

この関数では、四角形が比較され、それらが同じである場合は true が返されます。

```typescript
function equal(rect1: IRect, rect2: IRect): boolean;
```

例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.equal(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 50, top: 50, width: 100, height: 100 }
);

// returns: false
```

### <a name="equalwithprecision"></a>equalWithPrecision

この関数では、値の有効桁数を考慮して、四角形が比較されます。

```typescript
function equalWithPrecision(rect1: IRect, rect2: IRect): boolean;
```

例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.equalWithPrecision(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 50, top: 50, width: 100, height: 100 }
);

// returns: false
```

### <a name="isempty"></a>isEmpty

この関数では、四角形が空であるかどうかが確認されます。

```typescript
function isEmpty(rect: IRect): boolean;
```

例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.isEmpty({ left: 0, top: 0, width: 0, height: 0 });

// returns: true
```

### <a name="containspoint"></a>containsPoint

この関数では、四角形にポイントが含まれているかどうかが確認されます。

```typescript
function containsPoint(rect: IRect, point: IPoint): boolean;
```

例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.containsPoint(
  { left: 0, top: 0, width: 100, height: 100 },
  { x: 50, y: 50 }
);

// returns: true
```

### <a name="isintersecting"></a>isIntersecting

この関数では、四角形が交差しているかどうかが確認されます。

```typescript
function isIntersecting(rect1: IRect, rect2: IRect): boolean;
```

例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.isIntersecting(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 0, top: 0, width: 50, height: 50 }
);

// returns: true
```

### <a name="intersect"></a>intersect

この関数では、四角形の交差部分が返されます。

```typescript
function intersect(rect1: IRect, rect2: IRect): IRect;
```

例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.intersect(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 0, top: 0, width: 50, height: 50 }
);

/* returns: {
    left: 0,
    top: 0,
    width: 50,
    height: 50
}*/
```

### <a name="combine"></a>combine

この関数では四角形が結合されます。

```typescript
function combine(rect1: IRect, rect2: IRect): IRect;
```

例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.combine(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 0, top: 0, width: 50, height: 120 }
);

/* returns: {
    left: 0,
    top: 0,
    width: 100,
    height: 120
}*/
```

### <a name="getcentroid"></a>getCentroid

この関数では四角形の中心点が返されます。

```typescript
function getCentroid(rect: IRect): IPoint;
```

例:

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getCentroid({ left: 0, top: 0, width: 100, height: 100 });

/* returns: {
    x: 50,
    y: 50
}*/
```

## <a name="pointer"></a>ポインター (pointer)

`pointer` モジュールでは、ポインターの位置を取得するための特殊関数が提供されます。

このモジュールでは、次の関数が提供されます。

### <a name="getcoordinates"></a>getCoordinates

この関数では、ポインターの位置が返されます。

```typescript
function getCoordinates(rootNode: Element, isPointerEvent: boolean): number[];
```

例:

```typescript
import { pointer } from "powerbi-visuals-utils-svgutils";

let bodySelection = d3.select("body");

bodySelection
  .append("div")
  .style({
    width: "100px",
    height: "100px",
    "background-color": "green"
  })
  .on("click", () => {
    pointer.getCoordinates(bodySelection.node(), true);
  });

// click element, after that you will get position of the pointer
```
