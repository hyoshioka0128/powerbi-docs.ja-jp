---
title: より多くのデータを Power BI からフェッチする
description: この記事では、Power BI ビジュアルに対する大きいデータセットのセグメント化されたフェッチを有効にする方法を説明します。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: b8be5b68603f818e26e7f731e4f163bc626b5053
ms.sourcegitcommit: 132b3f6ba6d2b1948ddc15969d64cf629f7fb280
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2020
ms.locfileid: "94483698"
---
# <a name="fetch-more-data-from-power-bi"></a>より多くのデータを Power BI からフェッチする

この記事では、`fetchMoreData` メソッドを使用することにより、30 KB のデータ ポイントのハード制限を回避して、より多くのデータを読み込む方法について説明します。 この方法では、データがチャンクで提供されます。 パフォーマンスを向上させるために、ユース ケースに合わせてチャンク サイズを構成できます。

## <a name="limitations-of-fetchmoredata"></a>fetchMoreData の制限

* ウィンドウのサイズは、2 から 30,000 の範囲に制限されています。
* データビューの合計行数は、1,048,576 行に制限されています。
* セグメント集計モードでは、データビューのメモリ サイズは 100 MB に制限されています。

## <a name="enable-a-segmented-fetch-of-large-datasets"></a>大きいデータセットのセグメント化されたフェッチを有効にする

`dataview` セグメント モードの場合、必要な `dataViewMapping` に対するビジュアルの *capabilities.json* ファイルで、`dataReductionAlgorithm` のウィンドウ サイズを定義します。 `count` によってウィンドウ サイズが決定され、更新ごとに `dataview` に追加できる新しいデータ行の数が制限されます。

次のコードを *capabilities.json* ファイルに追加します。

```typescript
"dataViewMappings": [
    {
        "table": {
            "rows": {
                "for": {
                    "in": "values"
                },
                "dataReductionAlgorithm": {
                    "window": {
                        "count": 100
                    }
                }
            }
    }
]
```

新しいセグメントが既存の `dataview` に追加され、`update` 呼び出しとしてビジュアルに提供されます。

## <a name="usage-in-the-power-bi-visual"></a>Power BI ビジュアルでの使用

Power BI では、既定のセグメント集計モードまたは増分更新モードで、`fetchMoreData` を使用できます。 

### <a name="using-segments-aggregation-mode-default"></a>セグメント集計モードの使用 (既定)

このモードでは、ビジュアルに提供されるデータビューに、前のすべての `fetchMoreData requests` の累積データが含まれます。 そのため、データビューのサイズは、更新ごとに増加すると予想されます。 たとえば、合計 100,000 行が予想され、ウィンドウ サイズが 10,000 に設定されている場合、最初の更新データビューには 10,000 行、2 番目の更新データビューには 20,000 行を含める必要があります。

このモードは、`aggregateSegments = true` で `fetchMoreData` を呼び出すと選択されます。

`dataView.metadata.segment` の存在を調べると、データが存在するかどうかを確認できます。

```typescript
    public update(options: VisualUpdateOptions) {
        const dataView = options.dataViews[0];
        console.log(dataView.metadata.segment);
        // output: __proto__: Object
    }
```

また、`options.operationKind` を調べると、それが最初の更新か、それとも 2 回目以降の更新かを確認することもできます。 次のコードで、`VisualDataChangeOperationKind.Create` では最初のセグメントが参照され、`VisualDataChangeOperationKind.Append` では後続のセグメントが参照されます。

実装のサンプルについては、次のコード スニペットを参照してください。

```typescript
// CV update implementation
public update(options: VisualUpdateOptions) {
    // indicates this is the first segment of new data.
    if (options.operationKind == VisualDataChangeOperationKind.Create) {

    }

    // on second or subsequent segments:
    if (options.operationKind == VisualDataChangeOperationKind.Append) {

    }

    // complete update implementation
}
```

次に示すように、UI イベント ハンドラーから `fetchMoreData` メソッドを呼び出すこともできます。

```typescript
btn_click(){
{
    // check if more data is expected for the current data view
    if (dataView.metadata.segment) {
        //request for more data if available; as a response, Power BI will call update method
        let request_accepted: bool = this.host.fetchMoreData(true);
        // handle rejection
        if (!request_accepted) {
            // for example, when the 100 MB limit has been reached
        }
    }
}
```

`this.host.fetchMoreData` メソッドの呼び出しに対する応答として、Power BI では新しいデータ セグメントを使用してビジュアルの `update` メソッドが呼び出されます。

> [!NOTE]
> クライアントのメモリ制約を回避するため、Power BI では現在、フェッチされるデータの合計が 100 MB に制限されています。 `fetchMoreData()` から `false` が返されることで、制限に達したことがわかります。

### <a name="using-incremental-updates-mode"></a>増分更新モードの使用

このモードでは、ビジュアルに提供されるデータビューには増分データのみが含まれます。 そのため、データビューのサイズは定義されたウィンドウ サイズを超えません。 たとえば、合計 101,000 行が予想され、ウィンドウ サイズが 10,000 に設定されている場合、ビジュアルはデータビューのサイズが 10,000 で 10 個の更新を取得し、1 つの更新のデータビューのサイズは 1,000 です。

このモードは、`aggregateSegments = false` で `fetchMoreData` を呼び出すと選択されます。

`dataView.metadata.segment` の存在を調べると、データが存在するかどうかを確認できます。

```typescript
    public update(options: VisualUpdateOptions) {
        const dataView = options.dataViews[0];
        console.log(dataView.metadata.segment);
        // output: __proto__: Object
    }
```

また、`options.operationKind` を調べると、それが最初の更新か、それとも 2 回目以降の更新かを確認することもできます。 次のコードで、`VisualDataChangeOperationKind.Create` では最初のセグメントが参照され、`VisualDataChangeOperationKind.Segment` では後続のセグメントが参照されます。

実装のサンプルについては、次のコード スニペットを参照してください。

```typescript
// CV update implementation
public update(options: VisualUpdateOptions) {
    // indicates this is the first segment of new data.
    if (options.operationKind == VisualDataChangeOperationKind.Create) {

    }

    // on second or subsequent segments:
    if (options.operationKind == VisualDataChangeOperationKind.Segment) {
        
    }

    // skip overlapping rows 
    const rowOffset = (dataView.table['lastMergeIndex'] === undefined) ? 0 : dataView.table['lastMergeIndex'] + 1;

    // Process incoming data
    for (var i = rowOffset; i < dataView.table.rows.length; i++) {
        var val = <number>(dataView.table.rows[i][0]); // Pick first column               
            
     }
     
    // complete update implementation
}
```

次に示すように、UI イベント ハンドラーから `fetchMoreData` メソッドを呼び出すこともできます。

```typescript
btn_click(){
{
    // check if more data is expected for the current data view
    if (dataView.metadata.segment) {
        //request for more data if available; as a response, Power BI will call update method
        let request_accepted: bool = this.host.fetchMoreData(false);
        // handle rejection
        if (!request_accepted) {
            // for example, when the 100 MB limit has been reached
        }
    }
}
```

`this.host.fetchMoreData` メソッドの呼び出しに対する応答として、Power BI では新しいデータ セグメントを使用してビジュアルの `update` メソッドが呼び出されます。

> [!NOTE]
> 異なる更新の間のデータビューのデータはほとんど排他的ですが、後続のデータビューの間にはいくつかのオーバーラップがあります。
> テーブルとカテゴリ データのマッピングでは、最初の N データビュー行に前のデータビューからコピーされたデータが含まれることが想定されます。
> N は、次のようにして決定できます: `(dataView.table['lastMergeIndex'] === undefined) ? 0 : dataView.table['lastMergeIndex'] + 1`