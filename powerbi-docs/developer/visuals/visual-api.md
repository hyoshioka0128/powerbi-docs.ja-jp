---
title: 埋め込み BI 分析情報を向上させるための Power BI 埋め込み分析の ビジュアル API
description: この記事では Power BI ビジュアルで IVisual API を使用する方法について説明します。 Power BI 埋め込み分析を使用して、より優れた埋め込み BI インサイトを有効にします。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 03/19/2020
ms.openlocfilehash: 7b81ecfa1b97b202b6c1ff306cf858f2ea00acde
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888537"
---
# <a name="visual-api"></a>ビジュアル API
すべてのビジュアルは、`IVisual` インターフェイスを実装するクラスから開始されます。 `IVisual` インターフェイスを実装するクラスが 1 つしかない場合は、クラスに任意の名前を指定できます。

> [!NOTE]
> ビジュアル クラス名は、*pbiviz.json* ファイルで定義されているものと一致する必要があります。

実装する必要がある次のメソッドを含むサンプル ビジュアル クラスをご確認ください。

* `constructor` は、ビジュアルの状態を初期化するための標準コンストラクターです
* `update` は、ビジュアルのデータを更新します
* `enumerateObjectInstances` は、プロパティ ペイン (書式設定オプション) を設定するためのオブジェクトを返します。ここでは必要に応じてオプションを変更できます
* `destroy` は、クリーンアップ用の標準デストラクターです

```typescript
class MyVisual implements IVisual {
    
    constructor(options: VisualConstructorOptions) {
        //one time setup code goes here (called once)
    }
    
    public update(options: VisualUpdateOptions): void {
        //code to update your visual goes here (called on all view or data changes)
    }

    public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration {
        //returns objects to populate the property pane (called for each object defined in capabilities)
    }
    
    public destroy(): void {
        //one time cleanup code goes here (called once)
    }
}
```

## <a name="constructor"></a>コンストラクター

ビジュアル クラスのコンストラクターは、ビジュアルがインスタンス化されると呼び出されます。 ビジュアルに必要なすべての設定操作に使用できます。

```typescript
constructor(options: VisualConstructorOptions)
```

**VisualConstructorOptions**

* `element: HTMLElement` は、ビジュアルを格納する DOM 要素への参照です
* `host: IVisualHost` は、ビジュアル ホスト (Power BI) との対話に使用できるプロパティとサービスのコレクションです

   `IVisualHost` には、次のサービスが含まれています。

   ```typescript
   export interface IVisualHost extends extensibility.IVisualHost {
       createSelectionIdBuilder: () => visuals.ISelectionIdBuilder;
       : () => ISelectionManager;
       colorPalette: ISandboxExtendedColorPalette;
       persistProperties: (changes: VisualObjectInstancesToPersist) => void;
       applyJsonFilter: (filter: IFilter[] | IFilter, objectName: string, propertyName: string, action: FilterAction) => void;
       tooltipService: ITooltipService;
       telemetry: ITelemetryService;
       authenticationService: IAuthenticationService;
       locale: string;
       allowInteractions: boolean;
       launchUrl: (url: string) => void;
       fetchMoreData: () => boolean;
       instanceId: string;
       refreshHostData: () => void;
       createLocalizationManager: () => ILocalizationManager;
       storageService: ILocalVisualStorageService;
       eventService: IVisualEventService;
       switchFocusModeState: (on: boolean) => void;
   }
   ```
   * `createSelectionIdBuilder` は、ビジュアル内の選択可能な項目を表すメタデータを生成および格納します
   * `createSelectionManager` は、選択状態の変更について、ビジュアルのホストに通知を行うために使用される通信ブリッジを作成します。[選択 API](./selection-api.md) に関するページをご覧ください。
   * `createLocalizationManager` は、[ローカライズ](./localization.md)を支援するマネージャーを生成します
   * `allowInteractions: boolean` は、ビジュアルを対話形式にする必要があるかどうかのヒントを提供するブール型のフラグです
   * `applyJsonFilter` は、特定のフィルターの種類を適用します。[フィルター API](./filter-api.md) に関するページをご覧ください
   * `persistProperties` は、プロパティを保持し、ビジュアル定義と共に保存できるようにします。これによって、次回の再読み込み時にプロパティが利用可能になります
   * `eventService` は、**Render** イベントをサポートする [イベント サービス](./event-service.md)を返します
   * `storageService` は、ビジュアルで[ローカル ストレージ](./local-storage.md)を使用できるようにするためのサービスを返します
   * `authenticationService` は、ユーザー認証を支援するサービスを生成します
   * `tooltipService` は、ビジュアルでツールヒントを使用できるようにする[ツールヒント サービス](./add-tooltips.md)を返します
   * `launchUrl` は、次のタブで [URL を起動](./launch-url.md)する際に役立ちます
   * `locale` は、ロケール文字列を返します。[ローカライズ](./localization.md)に関するページをご覧ください
   * `instanceId` は、現在のビジュアル インスタンスを識別する文字列を返します
   * `colorPalette` は、データに色を適用するために必要な colorPalette を返します
   * `fetchMoreData` は、標準の制限 (1,000 行) を超えるデータの使用をサポートします
   * `switchFocusModeState` は、フォーカス モードの状態を変更する際に役立ちます

## <a name="update"></a>update

すべてのビジュアルでは、データまたはホスト環境が変更されるたびに呼び出されるパブリック更新メソッドを実装する必要があります。

```typescript
public update(options: VisualUpdateOptions): void
```

**VisualUpdateOptions**

* `viewport: IViewport` は、ビジュアルがレンダリングされる必要があるビューポートのディメンションです
* `dataViews: DataView[]` は、ビジュアルをレンダリングするために必要なすべてのデータを含む DataView オブジェクトです (ビジュアルは通常、DataView の下のカテゴリ プロパティを使用します)
* `type: VisualUpdateType` は、この更新の種類 (**Data** | **Resize** | **ViewMode** | **Style** | **ResizeEnd**) を示すフラグです
* `viewMode: ViewMode` は、ビジュアルのビュー モード (**View** | **Edit** | **InFocusEdit**) を示すフラグです
* `editMode: EditMode` は、ビジュアルの編集モード (**Default** | **Advanced**) を示すフラグです (ビジュアルが **AdvancedEditMode** をサポートしている場合、**editMode** が **Advanced** に設定されているときのみ、高度な UI コントロールがレンダリングされます。[高度な編集モード](./advanced-edit-mode.md)に関するページをご覧ください)
* `operationKind?: VisualDataChangeOperationKind` は、データ変更の種類 (**Create** | **Append**) を示すフラグです
* `jsonFilters?: IFilter[]` は、適用される JSON フィルターのコレクションです
* `isInFocus?: boolean` は、ビジュアルがフォーカス モードであるかどうかを示すフラグです
    
## <a name="enumerateobjectinstances-optional"></a>enumerateObjectInstances `optional`

このメソッドは、機能に示されているすべてのオブジェクトに対して呼び出されます。 オプション (現在は名前のみ) を使用すると、このプロパティを表示する方法に関する情報を含む `VisualObjectInstanceEnumeration` が返されます。

```typescript
enumerateObjectInstances(options:EnumerateVisualObjectInstancesOptions):VisualObjectInstanceEnumeration
```

**EnumerateVisualObjectInstancesOptions**

* `objectName: string` は、オブジェクトの名前です

## <a name="destroy-optional"></a>destroy `optional`

destroy 関数は、ビジュアルがアンロードされると呼び出され、イベント リスナーの削除などのクリーンアップ タスクに使用できます。

``` typescript
public destroy(): void
```

> [!Note]
> Power BI では、ビジュアルを含む IFrame 全体を削除する方が簡単であるため、通常は `destroy` が呼び出されることはありません。
