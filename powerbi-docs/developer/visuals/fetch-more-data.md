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
ms.openlocfilehash: 6d51a27bc5c0f18b7f784395dedd58813bfffbc0
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79380688"
---
# <a name="fetch-more-data-from-power-bi"></a>より多くのデータを Power BI からフェッチする

この記事では、30 KB のデータ ポイントのハード制限を回避して、より多くのデータを読み込む方法について説明します。 この方法では、データがチャンクで提供されます。 パフォーマンスを向上させるために、ユース ケースに合わせてチャンク サイズを構成できます。  

## <a name="enable-a-segmented-fetch-of-large-datasets"></a>大きいデータセットのセグメント化されたフェッチを有効にする

`dataview` セグメント モードでは、必要な dataViewMapping に対する dataReductionAlgorithm のウィンドウ サイズを、ビジュアルの *capabilities.json* ファイルで定義します。 `count` によってウィンドウ サイズが決定され、更新ごとに `dataview` に追加できる新しいデータ行の数が制限されます。

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

`dataView.metadata.segment` の存在を調べることによって、データが存在するかどうかを確認できます。

```typescript
    public update(options: VisualUpdateOptions) {
        const dataView = options.dataViews[0];
        console.log(dataView.metadata.segment);
        // output: __proto__: Object
    }
```

また、`options.operationKind` を調べることによって、それが最初の更新か、それとも 2 回目以降の更新かを確認することもできます。 次のコードで、`VisualDataChangeOperationKind.Create` では最初のセグメントが参照され、`VisualDataChangeOperationKind.Append` では後続のセグメントが参照されます。

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
        let request_accepted: bool = this.host.fetchMoreData();
        // handle rejection
        if (!request_accepted) {
            // for example, when the 100 MB limit has been reached
        }
    }
}
```

`this.host.fetchMoreData` メソッドの呼び出しに対する応答として、Power BI では新しいデータ セグメントを使用してビジュアルの `update` メソッドが呼び出されます。

> [!NOTE]
> クライアントのメモリ制約を回避するため、Power BI では現在、フェッチされるデータの合計が 100 MB に制限されています。 fetchMoreData() から `false` が返されることで、制限に達したことがわかります。
