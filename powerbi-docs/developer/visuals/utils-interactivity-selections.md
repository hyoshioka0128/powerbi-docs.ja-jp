---
title: 埋め込み BI 分析情報を向上させるための Power BI 埋め込み分析の Power BI ビジュアル インタラクティビティ ユーティリティ
description: この記事では、インタラクティビティ ユーティリティを使用して Power BI ビジュアルに選択項目を追加する方法について説明します。 Power BI 埋め込み分析を使用して、より優れた埋め込み BI インサイトを有効にします。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 02/24/2020
ms.openlocfilehash: 533cf90ed9192a8d9e595cdea6320207b841b559
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887778"
---
# <a name="power-bi-visuals-interactivity-utils"></a>Power BI ビジュアルのインタラクティビティ ユーティリティ

インタラクティビティ ユーティリティ (`InteractivityUtils`) は、クロス選択とクロス フィルタリングの実装を簡略化するために使用できる一連の関数およびクラスです。

> [!NOTE]
> インタラクティビティ ユーティリティの新しい更新プログラムでは、最新バージョンのツール (3.x.x 以上) のみがサポートされます。

## <a name="installation"></a>インストール

1. パッケージをインストールするには、現在の Power BI ビジュアル プロジェクトを使用して、ディレクトリ内で次のコマンドを実行します。

    ```bash
    npm install powerbi-visuals-utils-interactivityutils --save
    ```

2. バージョン 3.0 以降またはツールを使用している場合は、`powerbi-models` をインストールして依存関係を解決します。

    ```bash
    npm install powerbi-models --save
    ```

3. インタラクティビティ ユーティリティを使用するには、Power BI ビジュアルのソース コードに必要なコンポーネントをインポートします。

    ```typescript
    import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";
    ```

### <a name="including-the-css-files"></a>CSS ファイルを含める

Power BI ビジュアルにパッケージを使用するには、次の CSS ファイルを `.less` ファイルにインポートします。

`node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css`

Power BI ビジュアルのツールによって外部 CSS ルールがラップされるため、CSS ファイルを `.less` ファイルとしてインポートします。

```less
@import (less) "node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css";
```

## <a name="selectabledatapoint-properties"></a>SelectableDataPoint プロパティ

通常、データ ポイントには選択項目と値が含まれます。 このインターフェイスによって `SelectableDataPoint` インターフェイスが拡張されます。

以下に示すように、`SelectableDataPoint` にはプロパティが既に含まれています。

```typescript
  /** Flag for identifying that a data point was selected */
  selected: boolean;

  /** Identity for identifying the selectable data point for selection purposes */
  identity: powerbi.extensibility.ISelectionId;

  /*
   * A specific identity for when data points exist at a finer granularity than
   * selection is performed.  For example, if your data points select based
   * only on series, even if they exist as category/series intersections.
   */

  specificIdentity?: powerbi.extensibility.ISelectionId;
```

## <a name="defining-an-interface-for-data-points"></a>データ ポイントのインターフェイスを定義する

1. インタラクティビティ ユーティリティのインスタンスを作成し、そのオブジェクトをビジュアルのプロパティとして保存します。

    ```typescript
    export class Visual implements IVisual {
      // ...
      private interactivity: interactivityBaseService.IInteractivityService<VisualDataPoint>;
      // ...
      constructor(options: VisualConstructorOptions) {
          // ...
          this.interactivity = interactivitySelectionService.createInteractivitySelectionService(this.host);
          // ...
      }
    }
    ```

    ```typescript
    import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";

    export interface VisualDataPoint extends interactivitySelectionService.SelectableDataPoint {
        value: powerbi.PrimitiveValue;
    }
    ```

2. 基本動作クラスを拡張します。

    > [!NOTE]
    > `BaseBehavior` は、[5.6.x バージョンのインタラクティビティ ユーティリティ](https://www.npmjs.com/package/powerbi-visuals-utils-interactivityutils/v/5.6.0)で導入されました。 以前のバージョンを使用する場合は、次のサンプルから動作クラスを作成します。

3. 動作クラスのオプションのインターフェイスを定義します。

    ```typescript
    import { SelectableDataPoint } from "./interactivitySelectionService";

    import {
        IBehaviorOptions,
        BaseDataPoint
    } from "./interactivityBaseService";

    export interface BaseBehaviorOptions<SelectableDataPointType extends BaseDataPoint> extends IBehaviorOptions<SelectableDataPointType> {

    /** d3 selection object of the main elements on the chart */
    elementsSelection: Selection<any, SelectableDataPoint, any, any>;

    /** d3 selection object of some elements on backgroup, to hadle click of reset selection */
    clearCatcherSelection: d3.Selection<any, any, any, any>;
    }
    ```

4. `visual behavior` のクラスを定義します。 または、`BaseBehavior` クラスを拡張します。

    **`visual behavior` のクラスを定義する**

    このクラスを使用して、`click`、`contextmenu` マウス イベントの処理を行います。

    ユーザーがデータ要素をクリックすると、ビジュアルから選択ハンドラーが呼び出され、データ ポイントが選択されます。 ユーザーがビジュアルの背景要素をクリックすると、選択解除ハンドラーが呼び出されます。

    クラスには、次の対応するメソッドがあります。
    * `bindClick`
    * `bindClearCatcher`
    * `bindContextMenu`.

    ```typescript
    export class Behavior<SelectableDataPointType extends BaseDataPoint> implements IInteractiveBehavior {

        /** d3 selection object of main elements in the chart */
        protected options: BaseBehaviorOptions<SelectableDataPointType>;
        protected selectionHandler: ISelectionHandler;
    
        protected bindClick() {
          // ...
        }
    
        protected bindClearCatcher() {
          // ...
        }
    
        protected bindContextMenu() {
          // ...
        }
    
        public bindEvents(
            options: BaseBehaviorOptions<SelectableDataPointType>,
            selectionHandler: ISelectionHandler): void {
          // ...
        }
    
        public renderSelection(hasSelection: boolean): void {
          // ...
        }
    }
    ```

    **`BaseBehavior` クラスの拡張**

    ```typescript
    import powerbi from "powerbi-visuals-api";
    import { interactivitySelectionService, baseBehavior } from "powerbi-visuals-utils-interactivityutils";

    export interface VisualDataPoint extends interactivitySelectionService.SelectableDataPoint {
        value: powerbi.PrimitiveValue;
    }

    export class Behavior extends baseBehavior.BaseBehavior<VisualDataPoint> {
      // ...
    }
    ```

5. 要素のクリックを処理するには、*d3* 選択オブジェクトの `on` メソッドを呼び出します。 これは `elementsSelection` と `clearCatcherSelection` にも適用されます。

    ```typescript
    protected bindClick() {
      const {
          elementsSelection
      } = this.options;
    
      elementsSelection.on("click", (datum) => {
          const mouseEvent: MouseEvent = getEvent() as MouseEvent || window.event as MouseEvent;
          mouseEvent && this.selectionHandler.handleSelection(
              datum,
              mouseEvent.ctrlKey);
      });
    }
    ```

6. 選択マネージャーの `showContextMenu` メソッドを呼び出すには、`contextmenu` イベント用に同様のハンドラーを追加します。

    ```typescript
    protected bindContextMenu() {
        const {
            elementsSelection
        } = this.options;
    
        elementsSelection.on("contextmenu", (datum) => {
            const event: MouseEvent = (getEvent() as MouseEvent) || window.event as MouseEvent;
            if (event) {
                this.selectionHandler.handleContextMenu(
                    datum,
                    {
                        x: event.clientX,
                        y: event.clientY
                    });
                event.preventDefault();
            }
        });
    }
    ```

7. 関数をハンドラーに割り当てるには、インタラクティビティ ユーティリティから `bindEvents` メソッドを呼び出します。 `bindEvents` メソッドに次の呼び出しを追加します。
    * `bindClick`
    * `bindClearCatcher`
    * `bindContextMenu`

    ```typescript
      public bindEvents(
          options: BaseBehaviorOptions<SelectableDataPointType>,
          selectionHandler: ISelectionHandler): void {

          this.options = options;
          this.selectionHandler = selectionHandler;

          this.bindClick();
          this.bindClearCatcher();
          this.bindContextMenu();
      }
    ```

8. `renderSelection` メソッドを使用して、グラフ内の要素のビジュアル状態を更新します。 `renderSelection` の実装例を次に示します。

    ```typescript
    public renderSelection(hasSelection: boolean): void {
        this.options.elementsSelection.style("opacity", (category: any) => {
            if (category.selected) {
                return 0.5;
            } else {
                return 1;
            }
        });
    }
    ```

9. 最後のステップでは、`visual behavior` のインスタンスと、インタラクティビティ ユーティリティ インスタンスの `bind` メソッドの呼び出しを作成しています。

    ```typescript
    this.interactivity.bind(<BaseBehaviorOptions<VisualDataPoint>>{
        behavior: this.behavior,
        dataPoints: this.categories,
        clearCatcherSelection: select(this.target),
        elementsSelection: selectionMerge
    });
    ```

    * `selectionMerge` は *d3* 選択オブジェクトであり、ビジュアルの選択可能なすべての要素を表します。
    * `select(this.target)` は *d3* 選択オブジェクトであり、ビジュアルの主要な DOM 要素を表します。
    * `this.categories` は要素を持つデータ ポイントであり、インターフェイスは `VisualDataPoint` または `categories: VisualDataPoint[];` です。
    * `this.behavior` は、次に示すように、ビジュアルのコンストラクターで作成された `visual behavior` の新しいインスタンスです。

      ```typescript
      export class Visual implements IVisual {
        // ...
        constructor(options: VisualConstructorOptions) {
            // ...
            this.behavior = new Behavior();
        }
        // ...
      }
      ```
## <a name="next-steps"></a>次のステップ

* [ブックマークの切り替えで選択を処理する方法を確認する](bookmarks-support.md#visuals-with-selection)

* [ビジュアルのデータ ポイントのコンテキスト メニューを追加する方法を確認する](context-menu.md)

* [選択マネージャーを使用して Power BI ビジュアルに選択項目を追加する方法を確認する](selection-api.md)
