---
title: 埋め込み BI 分析情報を向上させるための Power BI 埋め込み分析での Power BI ビジュアルへの色の追加
description: この記事では、Power BI ビジュアルに色を追加する方法と、色付きのビジュアルのデータ ポイントを処理する方法について説明します。 Power BI 埋め込み分析を使用して、より優れた埋め込み BI インサイトを有効にします。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 03/27/2020
ms.openlocfilehash: e6b6fb1dbc1397b93ac12692c8610e6f36d0b8bf
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887985"
---
# <a name="add-colors-to-your-power-bi-visuals"></a>Power BI ビジュアルへの色の追加

この記事では、ビジュアルに色を追加する方法と、カラー ビジュアルのデータ ポイントを処理する方法について説明します。

`IVisualHost` は、そのサービスの 1 つとして色を公開します。
この記事のサンプル コードでは、[SampleBarChart ビジュアル](https://github.com/microsoft/PowerBI-visuals-sampleBarChart)を変更します。
ソース コードについては、[barChart.ts](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/master/src/barChart.ts) を参照してください。

視覚化の作成を始めるには、[Power BI の円形カード視覚化の開発](develop-circle-card.md)に関する記事を参照してください。

## <a name="add-color-to-data-points"></a>データ ポイントへの色の追加

各データ ポイントは、異なる色で表されます。
次の例のように、色を `BarChartDataPoint` インターフェイスに追加します。

```typescript
/**
 * Interface for BarChart data points.
 *
 * @interface
 * @property {number} value    - Data value for point.
 * @property {string} category - Corresponding category of data value.
 * @property {string} color    - Color corresponding to data point.
 */
interface BarChartDataPoint {
    value: number;
    category: string;
    color: string;
};
```

## <a name="use-the-color-palette-service"></a>カラー パレット サービスの使用

`colorPalette` サービスは、ビジュアルで使用する色を管理します。
サービスのインスタンスは `IVisualHost` で利用できます。

これを `update` メソッド内で定義します。

```typescript
constructor(options: VisualConstructorOptions) {
        this.host = options.host; // host: IVisualHost
        ...
    }

public update(options: VisualUpdateOptions) {

    let colorPalette: IColorPalette = host.colorPalette;
    ...
}
```

## <a name="assigning-color-to-data-points"></a>データ ポイントへの色の割り当て

次に、`dataPoints` を指定します。
この例では、`dataPoints` のそれぞれに、値、カテゴリ、および色が含まれています。
`dataPoints` には他のプロパティを含めることもできます。

`SampleBarChart` 内で、`visualTransform` メソッドは、`dataPoints` 計算をカプセル化します。
このメソッドは、横棒グラフ ビューモデルの一部です。
このメソッドは、`visualTransform` 内の `dataPoints` 計算を反復処理するため、次のコードのように色を割り当てるのに理想的な場所です。

```typescript

public update(options: VisualUpdateOptions) {
    ....
    let viewModel: BarChartViewModel = visualTransform(options, this.host);
    ....
}

function visualTransform(options: VisualUpdateOptions, host: IVisualHost): BarChartViewModel {
    let colorPalette: IColorPalette = host.colorPalette; // host: IVisualHost
    for (let i = 0, len = Math.max(category.values.length, dataValue.values.length); i < len; i++) {
        barChartDataPoints.push({
            category: category.values[i],
            value: dataValue.values[i],
            color: colorPalette.getColor(category.values[i]).value,
        });
    }
}
```

次に、`update` メソッド内で `dataPoints` からのデータを [d3](https://d3js.org/)-selection `barSelection` に適用します。

```typescript
// This code is actual for d3 v5
// in d3 v5 for this case we should use merge() after enter() and apply changes on barSelectionMerged
this.barSelection = this.barContainer
    .selectAll('.bar')
    .data(this.barDataPoints);

const barSelectionMerged = this.barSelection
    .enter()
    .append('rect')
    .merge(<any>this.barSelection);

barSelectionMerged.classed('bar', true);

barSelectionMerged
.attr("width", xScale.bandwidth())
.attr("height", d => height - yScale(<number>d.value))
.attr("y", d => yScale(<number>d.value))
.attr("x", d => xScale(d.category))
.style("fill", (dataPoint: BarChartDataPoint) => dataPoint.color)
.style("stroke", (dataPoint: BarChartDataPoint) => dataPoint.strokeColor)
.style("stroke-width", (dataPoint: BarChartDataPoint) => `${dataPoint.strokeWidth}px`);

this.barSelection
    .exit()
    .remove();
```

## <a name="next-steps"></a>次の手順

Power BI ビジュアルの詳細については、「[Power BI ビジュアルの機能とプロパティ](capabilities.md)」を参照してください。

Power BI ビジュアルの開発の詳細については、「[Power BI のビジュアルをデバッグする方法](visuals-how-to-debug.md)」および「[Power BI ビジュアルのトラブルシューティング](power-bi-custom-visuals-troubleshoot.md)」を参照してください。
