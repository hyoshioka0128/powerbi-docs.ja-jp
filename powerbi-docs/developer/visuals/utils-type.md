---
title: 埋め込み BI 分析情報を向上させるための、Power BI 埋め込み分析の Power BI ビジュアルでのタイプ ユーティリティの使用の概要
description: この記事では、SVG ユーティリティを使用して、Power BI ビジュアルの基本的な種類を拡張する方法について説明します。 Power BI 埋め込み分析を使用して、より優れた埋め込み BI インサイトを有効にします。
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: 4f81f55f8d5cfc54020b3b4e02e8be55fb65b0d1
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888123"
---
# <a name="type-utils"></a>タイプ ユーティリティ

TypeUtils は、Power BI ビジュアルの基本的な種類を拡張するための一連の関数およびクラスです。

## <a name="installation"></a>インストール

パッケージをインストールするには、現在のカスタム ビジュアルを使用して、ディレクトリ内で次のコマンドを実行する必要があります。

npm install powerbi-visuals-utils-typeutils --save このコマンドでは、パッケージがインストールされ、パッケージが依存関係として package.json に追加されます

## <a name="double"></a>Double

`Double` では、数値の有効桁数を操作する機能が提供されます。

このモジュールには、次の関数が用意されています。

### <a name="pow10"></a>pow10

この関数では 10 の累乗が返されます。

```typescript
function pow10(exp: number): number;
```

例:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.pow10(25);

// returns: 1e+25
```

### <a name="log10"></a>log10

この関数では、10 を底とする数値の対数が返されます。

```typescript
function log10(val: number): number;
```

例:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.log10(25);

// returns: 1
```

## <a name="getprecision"></a>getPrecision

この関数では、数値の有効桁数を表す 10 の累乗が返されます。

```typescript
function getPrecision(x: number, decimalDigits?: number): number;
```

例:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.getPrecision(562344, 6);

// returns: 0.1
```

### <a name="equalwithprecision"></a>equalWithPrecision

この関数では、2 つの数値の差が、指定された有効桁数よりも小さいかどうかが確認されます。

```typescript
function equalWithPrecision(x: number, y: number, precision?: number): boolean;
```

例:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.equalWithPrecision(1, 1.005, 0.01);

// returns: true
```

### <a name="lesswithprecision"></a>lessWithPrecision

この関数では、最初の値が 2 番目の値より小さいかどうかが確認されます。

```typescript
function lessWithPrecision(x: number, y: number, precision?: number): boolean;
```

例:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.lessWithPrecision(0.995, 1, 0.001);

// returns: true
```

### <a name="lessorequalwithprecision"></a>lessOrEqualWithPrecision

この関数では、最初の値が 2 番目の値以下であるかどうかが確認されます。

```typescript
function lessOrEqualWithPrecision(x: number, y: number, precision?: number): boolean;
```

例:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.lessOrEqualWithPrecision(1.005, 1, 0.01);

// returns: true
```

### <a name="greaterwithprecision"></a>greaterWithPrecision

この関数では、最初の値が 2 番目の値より大きいかどうかが確認されます。

```typescript
function greaterWithPrecision(x: number, y: number, precision?: number): boolean;
```

例:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.greaterWithPrecision(1, 0.995, 0.01);

// returns: false
```

### <a name="greaterorequalwithprecision"></a>greaterOrEqualWithPrecision

この関数では、最初の値が 2 番目の値以上であるかどうかが確認されます。

```typescript
function greaterOrEqualWithPrecision(x: number, y: number, precision?: number): boolean;
```

例:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.greaterOrEqualWithPrecision(1, 1.005, 0.01);

// returns: true
```

### <a name="floorwithprecision"></a>floorWithPrecision

この関数では、数値が指定された有効桁数で切り下げられます。

```typescript
function floorWithPrecision(x: number, precision?: number): number;
```

例:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.floorWithPrecision(5.96, 0.001);

// returns: 5
```

### <a name="ceilwithprecision"></a>ceilWithPrecision

この関数では、数値が指定された有効桁数で切り上げられます (`ceils`)

```typescript
function ceilWithPrecision(x: number, precision?: number): number;
```

例:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.ceilWithPrecision(5.06, 0.001);

// returns: 6
```

### <a name="floortoprecision"></a>floorToPrecision

この関数では、数値が指定された有効桁数に切り下げられます。

```typescript
function floorToPrecision(x: number, precision?: number): number;
```

例:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.floorToPrecision(5.96, 0.1);

// returns: 5.9
```

### <a name="ceiltoprecision"></a>ceilToPrecision

この関数では、数値が指定された有効桁数に切り上げられます (`ceils`)

```typescript
function ceilToPrecision(x: number, precision?: number): number;
```

例:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.ceilToPrecision(-506, 10);

// returns: -500
```

### <a name="roundtoprecision"></a>roundToPrecision

この関数では、数値が指定された有効桁数に丸められます。

```typescript
function roundToPrecision(x: number, precision?: number): number;
```

例:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.roundToPrecision(596, 10);

// returns: 600
```

### <a name="ensureinrange"></a>ensureInRange

この関数では、最小と最大の間の数値が返されます。

```typescript
function ensureInRange(x: number, min: number, max: number): number;
```

例:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.ensureInRange(-27.2, -10, -5);

// returns: -10
```

### <a name="round"></a>round

この関数では数値が丸められます。

```typescript
function round(x: number): number;
```

例:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.round(27.45);

// returns: 27
```

### <a name="removedecimalnoise"></a>removeDecimalNoise

この関数では小数点のノイズが削除されます。

```typescript
function removeDecimalNoise(value: number): number;
```

例:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.removeDecimalNoise(21.493000000000002);

// returns: 21.493
```

### <a name="isinteger"></a>isInteger

この関数では、数値が整数であるかどうかが確認されます。

```typescript
function isInteger(value: number): boolean;
```

例:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.isInteger(21.493000000000002);

// returns: false
```

### <a name="toincrement"></a>toIncrement

この関数では、数値が指定された数だけ増やされ、丸められた数値が返されます。

```typescript
function toIncrement(value: number, increment: number): number;
```

例:

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.toIncrement(0.6383723, 0.05);

// returns: 0.65
```

## <a name="prototype"></a>プロトタイプ

`Prototype` では、オブジェクトを継承するための機能が提供されます。

このモジュールには、次の関数が用意されています。

## <a name="inherit"></a>inherit

この関数では、プロトタイプとしてオブジェクトが指定された新しいオブジェクトが返されます。

```typescript
function inherit<T>(obj: T, extension?: (inherited: T) => void): T;
```

例:

```typescript
import { prototype } from "powerbi-visuals-utils-typeutils";
// ...

let base = { Microsoft: "Power BI" };

prototype.inherit(base);

/* returns: {
    __proto__: {
        Microsoft: "Power BI"
    }
}*/
```

## <a name="inheritsingle"></a>inheritSingle

この関数では、プロトタイプが設定されていない場合に限り、プロトタイプとしてオブジェクトが指定された新しいオブジェクトが返されます。

```typescript
function inheritSingle<T>(obj: T): T;
```

例:

```typescript
import { prototype } from "powerbi-visuals-utils-typeutils";
// ...

let base = { Microsoft: "Power BI" };

prototype.inheritSingle(base);

/* returns: {
    __proto__: {
        Microsoft: "Power BI"
    }
}*/
```

## <a name="pixelconverter"></a>PixelConverter

`PixelConverter` では、ピクセルとポイント間の変換機能が提供されます。

このモジュールには、次の関数が用意されています。

## <a name="tostring"></a>toString

この関数では、ピクセル値が文字列に変換されます。

```typescript
function toString(px: number): string;
```

例:

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.toString(25);

// returns: 25px
```

## <a name="frompoint"></a>fromPoint

この関数では、指定されたポイント値がピクセル値に変換され、文字列の解釈が返されます。

```typescript
function fromPoint(pt: number): string;
```

例:

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.fromPoint(8);

// returns: 33.33333333333333px
```

## <a name="frompointtopixel"></a>fromPointToPixel

この関数では、指定されたポイント値がピクセル値に変換されます。

```typescript
function fromPointToPixel(pt: number): number;
```

例:

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.fromPointToPixel(8);

// returns: 10.666666666666666
```

## <a name="topoint"></a>toPoint

この関数では、ピクセル値がポイント値に変換されます。

```typescript
function toPoint(px: number): number;
```

例:

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.toPoint(8);

// returns: 6
```
