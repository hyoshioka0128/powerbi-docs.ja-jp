---
title: 埋め込み BI 分析情報を向上させるための、Power BI 埋め込み分析の Power BI ビジュアルでのテスト ユーティリティの使用の概要
description: この記事では、テスト ユーティリティを使用して、Power BI ビジュアルの単体テストでのモックと特定のメソッドの使用を簡略化する方法について説明します。 Power BI 埋め込み分析を使用して、より優れた埋め込み BI インサイトを有効にします。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 02/14/2020
ms.openlocfilehash: 4b2a846f4905c4cb28fe92043cf3c71750b40f11
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888054"
---
# <a name="power-bi-visuals-test-utils"></a>Power BI ビジュアルのテスト ユーティリティ

この記事では、Power BI ビジュアルのテスト ユーティリティをインストール、インポート、使用する方法について説明します。 これらのテスト ユーティリティは単体テストに使用でき、データ ビュー、選択、配色などの要素用のモックとメソッドが含まれます。

## <a name="requirements"></a>必要条件

このパッケージを使用するには、次のものをインストールする必要があります。

* [node.js](https://nodejs.org): LTS バージョンを使用することをお勧めします
* [npm](https://www.npmjs.com/): バージョン 3.0.0 以降
* [PowerBI-visuals-tools](https://github.com/Microsoft/PowerBI-visuals-tools) パッケージ

## <a name="installation"></a>インストール

テスト ユーティリティをインストールし、その依存関係を *package.json* に追加するには、Power BI ビジュアルのディレクトリから次のコマンドを実行します。

```bash
npm install powerbi-visuals-utils-testutils --save
```

以下では、テスト ユーティリティのパブリック API の説明と例を示します。

## <a name="visualbuilderbase"></a>VisualBuilderBase

単体テストで **VisualBuilder** によって使用されます。最も頻繁に使用されるメソッドは `build`、`update`、`updateRenderTimeout` です。 

`build` メソッドでは、ビジュアルの作成されたインスタンスが返されます。

`enumerateObjectInstances` および `updateEnumerateObjectInstancesRenderTimeout` メソッドは、バケットおよび書式設定のオプションでの変更を確認するために必要です。

```typescript
abstract class VisualBuilderBase<T extends IVisual> {
    element: JQuery;
    viewport: IViewport;
    visualHost: IVisualHost;
    protected visual: T;
    constructor(width?: number, height?: number, guid?: string, element?: JQuery);
    protected abstract build(options: VisualConstructorOptions): T;
     nit(): void;
    destroy(): void;
    update(dataView: DataView[] | DataView): void;
    updateRenderTimeout(dataViews: DataView[] | DataView, fn: Function, timeout?: number): number;
    updateEnumerateObjectInstancesRenderTimeout(dataViews: DataView[] | DataView, options: EnumerateVisualObjectInstancesOptions, fn: (enumeration: VisualObjectInstance[]) => void, timeout?: number): number;
    updateFlushAllD3Transitions(dataViews: DataView[] | DataView): void;
    updateflushAllD3TransitionsRenderTimeout(dataViews: DataView[] | DataView, fn: Function, timeout?: number): number;
    enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstance[];
}
```

> [!NOTE]
> その他の例については、[VisualBuilderBase の単体テストの作成](./unit-tests-introduction.md#create-a-visual-instance-builder)および [VisualBuilderBase の実際の使用のシナリオ](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/test/visualBuilder.ts)に関する記事をご覧ください。

## <a name="dataviewbuilder"></a>DataViewBuilder

**TestDataViewBuilder** によって使用されるこのモジュールでは、`createCategoricalDataViewBuilder` メソッドで使用される **CategoricalDataViewBuilder** クラスが提供されます。 また、単体テストでモックの **DataView** を操作するために必要なインターフェイスとメソッドも指定されています。

* `withValues` では静的な系列の列が追加され、`withGroupedValues` では動的な系列の列が追加されます

  ビジュアルの 1 つの **DataViewCategorical** で、動的な系列と静的な系列の両方を適用しないでください。 両方とも使用できるのは、**DataViewCategorical** クエリの中だけです。この場合は、**DataViewTransform** によって、それらがビジュアルの個別の **DataViewCategorical** オブジェクトに分割されるものと想定されます。

* `build` では、メタデータと DataViewCategorical を含む DataView が返されます

  パラメーターの組み合わせが無効である場合、`build` では **Undefined** が返されます。たとえば、ビジュアルの **DataView** を作成するときに、動的な系列と静的な系列の両方が含まれるような場合です。

```typescript
class CategoricalDataViewBuilder implements IDataViewBuilderCategorical {
    withCategory(options: DataViewBuilderCategoryColumnOptions): IDataViewBuilderCategorical;
    withCategories(categories: DataViewCategoryColumn[]): IDataViewBuilderCategorical;
    withValues(options: DataViewBuilderValuesOptions): IDataViewBuilderCategorical;
    withGroupedValues(options: DataViewBuilderGroupedValuesOptions): IDataViewBuilderCategorical;
    build(): DataView;
}

function createCategoricalDataViewBuilder(): IDataViewBuilderCategorical;
```

## <a name="testdataviewbuilder"></a>TestDataViewBuilder

単体テストで **VisualData** を作成するために使用されます。 データがデータフィールド バケットに配置されていると、Power BI により、そのデータに基づいてカテゴリに応じた **DataView** オブジェクトが生成されます。 **TestDataViewBuilder** は、カテゴリに応じた **DataView** の作成をシミュレートするのに役立ちます。

```typescript
abstract class TestDataViewBuilder {
    static DataViewName: string;
    private aggregateFunction;
    static setDefaultQueryName(source: DataViewMetadataColumn): DataViewMetadataColumn;
    static getDataViewBuilderColumnIdentitySources(options: TestDataViewBuilderColumnOptions[] | TestDataViewBuilderColumnOptions): DataViewBuilderColumnIdentitySource[];
    static getValuesTable(categories?: DataViewCategoryColumn[], values?: DataViewValueColumn[]): any[][];
    static createDataViewBuilderColumnOptions(categoriesColumns: (TestDataViewBuilderCategoryColumnOptions | TestDataViewBuilderCategoryColumnOptions[])[], valuesColumns: (DataViewBuilderValuesColumnOptions | DataViewBuilderValuesColumnOptions[])[], filter?: (options: TestDataViewBuilderColumnOptions) => boolean, customizeColumns?: CustomizeColumnFn): DataViewBuilderAllColumnOptions;
    static setUpDataViewBuilderColumnOptions(options: DataViewBuilderAllColumnOptions, aggregateFunction: (array: number[]) => number): DataViewBuilderAllColumnOptions;
    static setUpDataView(dataView: DataView, options: DataViewBuilderAllColumnOptions): DataView;
    protected createCategoricalDataViewBuilder(categoriesColumns: (TestDataViewBuilderCategoryColumnOptions | TestDataViewBuilderCategoryColumnOptions[])[], valuesColumns: (DataViewBuilderValuesColumnOptions | DataViewBuilderValuesColumnOptions[])[], columnNames: string[], customizeColumns?: CustomizeColumnFn): IDataViewBuilderCategorical;
    abstract getDataView(columnNames?: string[]): DataView;
}
```

  次のリストでは、`testDataView` を作成するときに最もよく使用されるインターフェイスを示します。

  ```typescript
  interface TestDataViewBuilderColumnOptions extends DataViewBuilderColumnOptions {
      values: any[];
  }

  interface TestDataViewBuilderCategoryColumnOptions extends TestDataViewBuilderColumnOptions {
      objects?: DataViewObjects[];
      isGroup?: boolean;
  }

  interface DataViewBuilderColumnOptions {
      source: DataViewMetadataColumn;
  }

  interface DataViewBuilderSeriesData {
      values: PrimitiveValue[];
      highlights?: PrimitiveValue[];
      /** Client-computed maximum value for a column. */
      maxLocal?: any;
      /** Client-computed maximum value for a column. */
      minLocal?: any;
  }

  interface DataViewBuilderColumnIdentitySource {
      fields: any[];
      identities?: CustomVisualOpaqueIdentity[];
  }
  ```
   
> [!NOTE]
> その他の例については、[TestDataViewBuilder の単体テストの作成](./unit-tests-introduction.md#how-to-add-static-data-for-unit-tests)および [TestDataViewBuilder の実際の使用のシナリオ](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/test/visualData.ts)に関する記事をご覧ください。

## <a name="mocks"></a>モック

### <a name="mockivisualhost"></a>MockIVisualHost

Power BI フレームワークなどの外部依存関係なしで Power BI ビジュアルをテストするための **IVisualHost** が実装されます。

便利なメソッドとして、`createSelectionIdBuilder`、`createSelectionManager`、`createLocalizationManager`、getter プロパティなどがあります。

```typescript
import powerbi from "powerbi-visuals-api";

import VisualObjectInstancesToPersist = powerbi.VisualObjectInstancesToPersist;
import ISelectionIdBuilder = powerbi.visuals.ISelectionIdBuilder;
import ISelectionManager = powerbi.extensibility.ISelectionManager;
import IColorPalette = powerbi.extensibility.IColorPalette;
import IVisualEventService = powerbi.extensibility.IVisualEventService;
import ITooltipService = powerbi.extensibility.ITooltipService;
import IVisualHost = powerbi.extensibility.visual.IVisualHost;

class MockIVisualHost implements IVisualHost {
      constructor(
          colorPalette?: IColorPalette,
          selectionManager?: ISelectionManager,
          tooltipServiceInstance?: ITooltipService,
          localeInstance?: MockILocale,
          allowInteractionsInstance?: MockIAllowInteractions,
          localizationManager?: powerbi.extensibility.ILocalizationManager,
          telemetryService?: powerbi.extensibility.ITelemetryService,
          authService?: powerbi.extensibility.IAuthenticationService,
          storageService?: ILocalVisualStorageService,
          eventService?: IVisualEventService);
      createSelectionIdBuilder(): ISelectionIdBuilder;
      createSelectionManager(): ISelectionManager;
      createLocalizationManager(): ILocalizationManager;
      colorPalette: IColorPalette;
      locale: string;
      telemetry: ITelemetryService;
      tooltipService: ITooltipService;
      allowInteractios: boolean;
      storageService: ILocalVisualStorageService;
      eventService: IVisualEventService;
      persistProperties(changes: VisualObjectInstancesToPersist): void;
}
```
   
- `createVisualHost` では、**IVisualHost** (実際には **MockIVisualHost**) のインスタンスが作成されて返されます
  ```typescript
  function createVisualHost(locale?: Object, allowInteractions?: boolean, colors?: IColorInfo[], isEnabled?: boolean, displayNames?: any, token?: string): IVisualHost;
  ```

    例
    ```typescript
    import { createVisualHost } from "powerbi-visuals-utils-testutils"

    let host: IVisualHost = createVisualHost();
    ```

> [!IMPORTANT]
> **MockIVisualHost** は **IVisualHost** の偽の実装であり、単体テストでのみ使用する必要があります。

### <a name="mockicolorpalette"></a>MockIColorPalette

Power BI フレームワークなどの外部依存関係なしで Power BI ビジュアルをテストするための **IColorPalette** が実装されます。

**MockIColorPalette** では、単体テストで配色やハイコントラスト モードをチェックするのに便利なプロパティが提供されます。

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import IColorPalette = powerbi.extensibility.ISandboxExtendedColorPalette;
  import IColorInfo = powerbi.IColorInfo;

  class MockIColorPalette implements IColorPalette {
      constructor(colors?: IColorInfo[]);
      getColor(key: string): IColorInfo;
      reset(): IColorPalette;
      isHighContrastMode: boolean;
      foreground: {value: string};
      foregroundLight: {value: string};
      ...
      background: {value: string};
      backgroundLight: {value: string};
      ...
      shapeStroke: {value: string};
  }
  ```
  - `createColorPalette` では、**IColorPalette** (実際には **MockIColorPalette**) のインスタンスが作成されて返されます
    ```typescript
    function createColorPalette(colors?: IColorInfo[]): IColorPalette;
    ```

    例
    ```typescript
    import { createColorPalette } from "powerbi-visuals-utils-testutils"

    let colorPalette: IColorPalette = createColorPalette();
    ```
    
> [!IMPORTANT]
> **MockIColorPalette** は **IColorPalette** の偽の実装であり、単体テストでのみ使用する必要があります。

### <a name="mockiselectionid"></a>MockISelectionId

Power BI フレームワークなどの外部依存関係なしで Power BI ビジュアルをテストするための **ISelectionId** が実装されます。

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import Selector = powerbi.data.Selector;
  import ISelectionId = powerbi.visuals.ISelectionId;

  class MockISelectionId implements ISelectionId {
      constructor(key: string);
      equals(other: ISelectionId): boolean;
      includes(other: ISelectionId, ignoreHighlight?: boolean): boolean;
      getKey(): string;
      getSelector(): Selector;
      getSelectorsByColumn(): Selector;
      hasIdentity(): boolean;
  }
  ```

  - `createSelectionId` では、**ISelectionId** (実際には **MockISelectionId**) のインスタンスが作成されて返されます
    ```typescript
    function createSelectionId(key?: string): ISelectionId;
    ```

    例
    ```typescript
    import { createColorPalette } from "powerbi-visuals-utils-testutils"

    let selectionId: ISelectionId = createSelectionId();
    ```
    
> [!NOTE]
> **MockISelectionId** は **ISelectionId** の偽の実装であり、単体テストでのみ使用する必要があります。

### <a name="mockiselectionidbuilder"></a>MockISelectionIdBuilder

Power BI フレームワークなどの外部依存関係なしで Power BI ビジュアルをテストするための **ISelectionIdBuilder** が実装されます。 

  ```typescript
  import DataViewCategoryColumn = powerbi.DataViewCategoryColumn;
  import DataViewValueColumn = powerbi.DataViewValueColumn;
  import DataViewValueColumnGroup = powerbi.DataViewValueColumnGroup;
  import DataViewValueColumns = powerbi.DataViewValueColumns;
  import ISelectionIdBuilder = powerbi.visuals.ISelectionIdBuilder;
  import ISelectionId = powerbi.visuals.ISelectionId;

  class MockISelectionIdBuilder implements ISelectionIdBuilder {
      withCategory(categoryColumn: DataViewCategoryColumn, index: number): this;
      withSeries(seriesColumn: DataViewValueColumns, valueColumn: DataViewValueColumn | DataViewValueColumnGroup): this;
      withMeasure(measureId: string): this;
      createSelectionId(): ISelectionId;
      withMatrixNode(matrixNode: DataViewMatrixNode, levels: DataViewHierarchyLevel[]): this;
      withTable(table: DataViewTable, rowIndex: number): this;
  }
  ```

  - `createSelectionIdBuilder` では、**ISelectionIdBuilder** (実際には **MockISelectionIdBuilder**) のインスタンスが作成されて返されます
    ```typescript
    function createSelectionIdBuilder(): ISelectionIdBuilder;
    ```

    例
    ```typescript
    import { selectionIdBuilder } from "powerbi-visuals-utils-testutils";

    let selectionIdBuilder = createSelectionIdBuilder();
    ```

> [!NOTE]
> **MockISelectionIdBuilder** は **ISelectionIdBuilder** の偽の実装であり、単体テストでのみ使用する必要があります。

### <a name="mockiselectionmanager"></a>MockISelectionManager

Power BI フレームワークなどの外部依存関係なしで Power BI ビジュアルをテストするための **ISelectionManager** が実装されます。 

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import IPromise = powerbi.IPromise;
  import ISelectionId = powerbi.visuals.ISelectionId;
  import ISelectionManager = powerbi.extensibility.ISelectionManager;

  class MockISelectionManager implements ISelectionManager {
      select(selectionId: ISelectionId | ISelectionId[], multiSelect?: boolean): IPromise<ISelectionId[]>;
      hasSelection(): boolean;
      clear(): IPromise<{}>;
      getSelectionIds(): ISelectionId[];
      containsSelection(id: ISelectionId): boolean;
      showContextMenu(selectionId: ISelectionId, position: IPoint): IPromise<{}>;
      registerOnSelectCallback(callback: (ids: ISelectionId[]) => void): void;
      simutateSelection(selections: ISelectionId[]): void;
  }
  ```

  - `createSelectionManager` では、**ISelectionManager** (実際には **MockISelectionManager**) のインスタンスが作成されて返されます
    ```typescript
    function createSelectionManager(): ISelectionManager
    ```

    例
    ```typescript
    import { createSelectionManager } from "powerbi-visuals-utils-testutils";

    let selectionManager: ISelectionManager = createSelectionManager();
    ```

> [!NOTE]
> **MockISelectionManager** は **ISelectionManager** の偽の実装であり、単体テストでのみ使用する必要があります。

### <a name="mockilocale"></a>MockILocale

  ロケールが設定され、単体テストのプロセスの間に必要に応じて変更されます。
  ```typescript
  class MockILocale {
      constructor(locales?: Object): void; // Default locales are en-US and ru-RU 
      locale(key: string): void;// setter property
      locale(): string; // getter property
  }
  ```
  - `createLocale` では、**MockILocale** のインスタンスが作成されて返されます
    ```typescript
    funciton createLocale(locales?: Object): MockILocale;
    ```

### <a name="mockitooltipservice"></a><a id="mockitooltipservice"></a> MockITooltipService
`TooltipService` がシミュレートされ、単体テストのプロセスの間に必要に応じて呼び出されます。
  ```typescript
  class MockITooltipService implements ITooltipService {
      constructor(isEnabled: boolean = true);
      enabled(): boolean;
      show(options: TooltipShowOptions): void;
      move(options: TooltipMoveOptions): void;
      hide(options: TooltipHideOptions): void;
  }
  ```
  - `createTooltipService` では、**MockITooltipService** のインスタンスが作成されて返されます
    ```typescript
    function createTooltipService(isEnabled?: boolean): ITooltipService;
    ```

### <a name="mockiallowinteractions"></a>MockIAllowInteractions

```typescript
export class MockIAllowInteractions {
    constructor(public isEnabled?: boolean); // false by default
}
```
  - `createAllowInteractions` では、**MockIAllowInteractions** のインスタンスが作成されて返されます
    ```typescript
    function createAllowInteractions(isEnabled?: boolean): MockIAllowInteractions;
    ```

### <a name="mockilocalizationmanager"></a><a id="mockilocalizationmanager"></a> MockILocalizationManager
単体テストに必要な **LocalizationManager** の基本的な機能が提供されます。
```typescript
class MockILocalizationManager implements ILocalizationManager {
    constructor(displayNames: {[key: string]: string});
    getDisplayName(key: string): string; // returns default or setted displayNames for localized elements
}
```
  - `createLocalizationManager` では、**ILocalizationManager** (実際には **MockILocalizationManager**) のインスタンスが作成されて返されます
    ```typescript
    function createLocalizationManager(displayNames?: any): ILocalizationManager;
    ```

    例
    ```typescript
    import { createLocalizationManager } from "powerbi-visuals-utils-testutils";
    let localizationManagerMock: ILocalizationManager = createLocalizationManager();
    ```

### <a name="mockitelemetryservice"></a>MockITelemetryService
**TelemetryService** の使用がシミュレートされます。
```typescript
class MockITelemetryService implements ITelemetryService {
    instanceId: string;
    trace(veType: powerbi.VisualEventType, payload?: string) {
    }
}
```
  `MockITelemetryService` の作成
    ```typescript
    function createTelemetryService(): ITelemetryService;
    ```
### <a name="mockiauthenticationservice"></a>MockIAuthenticationService
モックの AAD トークンを提供することによって、**AuthenticationService** の動作がシミュレートされます。
```typescript
class MockIAuthenticationService implements IAuthenticationService  {
    constructor(token: string);
    getAADToken(visualId?: string): powerbi.IPromise<string>
}
```
  - `createAuthenticationService` では、**IAuthenticationService** (実際には **MockIAuthenticationService**) のインスタンスが作成されて返されます
    ```typescript
    function createAuthenticationService(token?: string): IAuthenticationService;
    ```

### <a name="mockistorageservice"></a>MockIStorageService
**ILocalVisualStorageService** を **LocalStorage** と同じ動作で使用できます。
```typescript
class MockIStorageService implements ILocalVisualStorageService {
  get(key: string): IPromise<string>;
  set(key: string, data: string): IPromise<number>;
  remove(key: string): void;
}
```
  - `createStorageService` では、**ILocalVisualStorageService** (実際には **MockIStorageService**) のインスタンスが作成されて返されます
    ```typescript
    function createStorageService(): ILocalVisualStorageService;
    ```

### <a name="mockieventservice"></a>MockIEventService
```typescript
import powerbi from "powerbi-visuals-api";
import IVisualEventService = powerbi.extensibility.IVisualEventService;
import VisualUpdateOptions = powerbi.extensibility.VisualUpdateOptions;

class MockIEventService implements IVisualEventService {
      renderingStarted(options: VisualUpdateOptions): void;
      renderingFinished(options: VisualUpdateOptions): void;
      renderingFailed(options: VisualUpdateOptions, reason?: string): void;
}
```
  - `createEventService` では、**IVisualEventService** (実際には **MockIEventService**) のインスタンスが作成されて返されます
    ```typescript
    function createEventService(): IVisualEventService;
    ```

## <a name="utils"></a>ユーティリティ

ユーティリティには、色、数値、イベントに関連するヘルパーなど、Power BI ビジュアルの単体テスト用のヘルパー メソッドが含まれています。

- `renderTimeout` ではタイムアウトが返されます
  ```typescript
  function renderTimeout(fn: Function, timeout: number = DefaultWaitForRender): number
  ```

- `testDom` は単体テストでのフィクスチャの設定に役立ちます
  ```typescript
  function testDom(height: number | string, width: number | string): JQuery
  ```
  例
  ```typescript
  import { testDom }  from "powerbi-visuals-utils-testutils";
  describe("testDom", () => {
      it("should return an element", () => {
          let element: JQuery = testDom(500, 500);
          expect(element.get(0)).toBeDefined();
      });
  });
  ```

### <a name="color-related-helper-methods"></a>色関連のヘルパー メソッド

- `getSolidColorStructuralObject`
  ```typescript
  function getSolidColorStructuralObject(color: string): any
  ```
  次の構造が返されます。

  ```json
  { solid: { color: color } }
  ```

- `assertColorsMatch` では、入力文字列から解析された **RgbColor** オブジェクトが比較されます
  ```typescript
  function assertColorsMatch(actual: string, expected: string, invert: boolean = false): boolean
  ```

- `parseColorString` では、入力文字列から色が解析されて、指定したインターフェイス **RgbColor** で返されます
  ```typescript
  function parseColorString(color: string): RgbColor
  ```

### <a name="number-related-helper-methods"></a>数値関連のヘルパー メソッド

- `getRandomNumbers` では、最小値と最大値を使用して乱数が生成されます。 `exceptionList` を指定し、結果を変更するための関数を指定できます。
  ```typescript
  function getRandomNumber(
      min: number,
      max: number,
      exceptionList?: number[],
      changeResult: (value: any) => number = x => x): number
  ```

- `getRandomNumbers` では、指定した最小値と最大値から `getRandomNumber` メソッドによって生成されたランダムな数値の配列が提供されます
  ```typescript
  function getRandomNumbers(count: number, min: number = 0, max: number = 1): number[]
  ```

### <a name="event-related-helper-methods"></a>イベント関連のヘルパー メソッド
以下のメソッドは、単体テストで Web ページのイベントをシミュレートするために記述されています。

- `clickElement` では、指定した要素のクリックがシミュレートされます
  ```typescript
  function clickElement(element: JQuery, ctrlKey: boolean = false): void
  ```

- `createTouch` では、タッチ イベントをシミュレートするのに役立つ **Touch** オブジェクトが返されます
  ```typescript
  function createTouch(x: number, y: number, element: JQuery, id: number = 0): Touch
  ```

- `createTouchesList` では、シミュレートされた **Touch** イベントのリストが返されます
  ```typescript
  function createTouchesList(touches: Touch[]): TouchList
  ```

- `createContextMenuEvent` では、**MouseEvent** が返されます
  ```typescript
  function createContextMenuEvent(x: number, y: number): MouseEvent
  ```

- `createMouseEvent` では、**MouseEvent** が作成されて返されます
  ```typescript
  function createMouseEvent(
      mouseEventType: MouseEventType,
      eventType: ClickEventType,
      x: number,
      y: number,
      button: number = 0): MouseEvent
  ```

- `createTouchEndEvent`
  ```typescript
  function createTouchEndEvent(touchList?: TouchList): UIEvent
  ```

- `createTouchMoveEvent`
  ```typescript
  function createTouchMoveEvent(touchList?: TouchList): UIEvent
  ```

- `createTouchStartEvent`
  ```typescript
  function createTouchStartEvent(touchList?: TouchList): UIEvent
  ```

### <a name="d3-event-related-helper-methods"></a>D3 イベント関連のヘルパー メソッド

以下のメソッドは、単体テストで D3 イベントをシミュレートするために使用されます。

- `flushAllD3Transitions` では、すべての D3 遷移が強制的に完了されます

  ```typescript
  function flushAllD3Transitions()
  ```
  
  > [!NOTE]
  > 通常、ゼロ遅延の遷移では、瞬間的な遅延 (10 ミリ秒未満) の後で実行されますが、ブラウザーがページを 2 回レンダリングする場合は、わずかなちらつきが発生する可能性があります。 最初のイベント ループの最後に 1 回と、その直後に再び最初のタイマー コールバックのときです。
  >
  > これらのちらつきは、IE と Web ビューの数が多い場合に顕著になり、iOS には推奨されません。
  > 
  > 最初のイベント ループの最後でタイマー キューをフラッシュすることで、ゼロ遅延遷移をすぐに実行して、ちらつきを回避できます。

次のメソッドも含まれます。
```typescript
function d3Click(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseUp(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseDown(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseOver(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseMove(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseOut(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3KeyEvent(element: JQuery, typeArg: string, keyArg: string, keyCode: number): void
function d3TouchStart(element: JQuery, touchList?: TouchList): void
function d3TouchMove(element: JQuery, touchList?: TouchList): void
function d3TouchEnd(element: JQuery, touchList?: TouchList): void
function d3ContextMenu(element: JQuery, x: number, y: number): void
```

### <a name="helper-interfaces"></a>ヘルパー インターフェイス
ヘルパー関数では、次のインターフェイスと列挙型が使用されます。

```typescript
interface RgbColor {
    R: number;
    G: number;
    B: number;
    A?: number; 
}

enum ClickEventType {
    Default = 0,
    CtrlKey = 1,
    AltKey = 2,
    ShiftKey = 4,
    MetaKey = 8,
}

enum MouseEventType {
    click,
    mousedown,
    mouseup,
    mouseover,
    mousemove,
    mouseout,
}
```

## <a name="next-steps"></a>次のステップ

webpack ベースの Power BI ビジュアル用の単体テスト、および `karma` と `jasmine` を使用した単体テストの作成について、たとえば「[チュートリアル: Power BI のビジュアル プロジェクトの単体テストを追加する](./unit-tests-introduction.md)」をご覧ください。
