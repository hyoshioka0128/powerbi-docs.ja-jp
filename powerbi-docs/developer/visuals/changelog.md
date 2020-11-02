---
title: Power BI ビジュアル API の変更ログ
description: この記事では、Power BI ビジュアル API のさまざまなバージョンにおける主な変更点について説明します
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 03/13/2019
ms.openlocfilehash: c43542bc6c2bb0699403062f68024f9718bbbb60
ms.sourcegitcommit: 54e571a10b0fdde5cd6036017eac9ef228de5116
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501951"
---
# <a name="power-bi-visuals-api-changelog"></a>Power BI ビジュアル API の変更ログ
このページには、API バージョンの簡単な概要が含まれています。 ここに記載されているバージョンは安定バージョンと見なされ、変更されません。


## <a name="api-v340"></a>API v3.4.0
  * `fetchMoreData` : 新しい `aggregateSegments` パラメーター (既定で true)、集計のない fetchMoreData をサポートするため

## <a name="api-v320"></a>API v3.2.0
  * **[supportsMultiVisualSelection](./supportsmultivisualselection-feature.md)** のサポート

## <a name="api-v260"></a>API v2.6.0
  * 更新オプションに **isInFocus** を追加。ビジュアル ホストに **switchFocusModeState** メソッドを追加
  * **subtotals** のカスタマイズをサポート

## <a name="api-v250"></a>API v2.5.0
  * **[分析ペイン](./analytics-pane.md)** をサポート
  * `SelectionIdBuilder` の **withMatrixNode** および **withTable** メソッドをサポート
  * `DataRepetitionSelector` インターフェイスのサポートが終了し、`data.CustomVisualOpaqueIdentity` インターフェイスに置き換え

## <a name="api-v230"></a>API v2.3.0
  * **[ランディング ページ API](./landing-page.md)**
  * **[ローカル ストレージ API](./local-storage.md)**
  * **[タプル フィルター API (複数列フィルター)](./filter-api.md#the-tuple-filter-api-multi-column-filter)**
  * **[レンダリング イベント API](./event-service.md#render-events-in-power-bi-visuals)**

## <a name="api-v220"></a>API v2.2.0
  * **[DataView からの JSON フィルターの復元](./filter-api.md#restore-the-json-filter-from-the-data-view)** をサポート
  * **[ContextMenu API](./context-menu.md)**

## <a name="api-v210"></a>API v2.1.0
  * パフォーマンスの向上:
    * 読み込み時間の短縮
    * より小さなメモリ占有領域
    * 最適化されたデータおよびイベント トランザクション  

**リリース ノート**
* リファクタリングされたフィルター処理 API シリーズは API 2.2 で利用可能になり、API 2.1 ではサポートされません。
* ビジュアルは、その機能で宣言された dataView 型のみを受け取ります。 複数の dataView 型を使用しているビジュアルは、この更新の結果として中断されます。
* `DataViewScopeIdentity` インターフェイスのサポートが終了し、`data.DataRepetitionSelector` インターフェイスに置き換えられました。 `DataViewScopeIdentity` インターフェイスのキー プロパティを使用していた場合は、`JSON.stringify(identity)` に置き換えることができます
* `undefined` は dataView 内で `null` に置き換えられます。 `var item in myArray` を使用して配列を反復処理する場合、`undefined` はスキップされますが、`null` はスキップされません。 このパターンを使用するビジュアルは、この更新によって破損する可能性があります。 配列内の `null` を確認してください。
   ```typescript
   for (var item in myArray) {
     if (!item) {
       continue;
     }
     console.log(item);
   }
   ```
* `proto` プロパティでは、dataView 内に非表示のメタデータまたはデータが格納されなくなりました。 `proto` を介してプロパティにアクセスするビジュアルは、この更新によって破損する可能性があります。

## <a name="api-v1130"></a>API v1.13.0
* **[同期スライサー](./enable-sync-slicers.md)** をサポート。これは、PBI の現在のコード状態により、単一フィールド スライサーでのみ動作することに注意してください。 [詳細](../../visuals/power-bi-visualization-slicers.md)。
* アクセシビリティ:[ハイコントラストのサポート](./high-contrast-support.md) 
* アクセシビリティ:"キーボード フォーカスを許可する" フラグ

## <a name="api-v1120"></a>API v1.12.0
* テーマをサポート
* **[fetchMoreData](./fetch-more-data.md)** をサポート。 **"より多くのデータをフェッチ" API** が 30K のデータ ポイントのハード制限を克服していることに注意してください
* **[キャンバス ツールヒント API](./add-tooltips.md#add-report-page-tooltips)**

## <a name="api-v1110"></a>API v1.11.0
* **[FilterManager API](./filter-api.md)**
* **[ブックマーク](./bookmarks-support.md)** をサポート 

## <a name="api-v1100"></a>API v1.10.0
* `ILocalizationManager` を追加
* **認証 API**

## <a name="api-v190"></a>API v1.9.0
* **[launchUrl API](./launch-url.md)**

## <a name="api-v180"></a>API v1.8.0
* 機能スキーマで新しい型 **fillRule** (勾配) をサポート
* オブジェクト プロパティの機能スキーマで **rule** プロパティをサポート

## <a name="api-v170"></a>API v1.7.0
* **[RESJSON](./localization.md#resource-file)** をサポート

## <a name="api-v162"></a>API v1.6.2
* ビジュアルをビジュアル編集モードに移行する **[編集モード](./advanced-edit-mode.md)** をサポート
* html に基づく **[インタラクティブ (html) R Power BI ビジュアル](https://github.com/Microsoft/PowerBI-visuals/blob/master/RVisualTutorial/CreateRHTML.md)** をサポート

## <a name="api-v150"></a>API v1.5.0
* ビジュアル対話のための " **[ビジュアル対話を許可](./visuals-interactions.md)** " をサポート

## <a name="api-v140"></a>API v1.4.0
* **[ローカライズ](./localization.md)** をサポート

## <a name="api-v130"></a>API v1.3.0
* **[ツールヒント](./add-tooltips.md)** をサポート

## <a name="api-v120"></a>API v1.2.0
* **colorPalette** を追加して、ビジュアルで使用する色を管理します。
* **複数選択** をサポート。selectionManager は `SelectionId` の配列を受け入れることができます。
* R スクリプトを使用した **[R ビジュアル](https://github.com/Microsoft/PowerBI-visuals/blob/master/RVisualTutorial/CreateRHTML.md)** をサポート

## <a name="api-v110"></a>API v1.1.0
* iFrame 内のデバッグ ビジュアルをサポート
* iFrame の初期化を高速にする軽量のサンドボックスを追加
* [Capabilities.objects で "テキスト" 型がサポートされない](https://github.com/Microsoft/PowerBI-visuals-tools/issues/12)問題を修正
* ビジュアル API の型定義とスキーマを更新するための `pbiviz update` をサポート
* 特定の API バージョンでビジュアルを作成するための、`pbiviz new` の `--api-version` フラグをサポート
* API v1.2.0 のアルファ リリースをサポート

**ビジュアル ホスト**
* データ選択に使用される一意の識別子を作成するための **createSelectionIdBuilder** を追加
* ビジュアルの選択状態を管理し、ビジュアル ホストに変更を通知するための **createSelectionManager** を追加
* ビジュアルで使用する既定の **colors** の配列を追加

## <a name="api-v100"></a>API v1.0.0
* 最初の API リリース
