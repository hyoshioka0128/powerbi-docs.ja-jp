---
title: 埋め込み BI 分析情報を向上させるための Power BI 埋め込み分析のパフォーマンスのベスト プラクティス
description: この記事では、Power BI 埋め込み分析のベスト プラクティスについて説明します。 Power BI 埋め込み分析を使用して、より優れた埋め込み BI インサイトを有効にします。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 12/12/2018
ms.openlocfilehash: f8bf41ae9a4b6f2e16aae2c05df8fa4448a0457c
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888790"
---
# <a name="power-bi-embedded-analytics-performance-best-practices"></a>Power BI 埋め込み分析のパフォーマンスのベスト プラクティス

この記事では、アプリケーションでレポート、ダッシュボード、タイルを短時間で表示するための推奨事項を紹介しています。

> [!Note]
> 読み込み時間は主に、レポートおよびデータ自体に関連する要素 (視覚化、データのサイズ、クエリとメジャーの複雑さなど) に依存していることに注意してください。 詳細については、[Power BI の最適化ガイド](../../guidance/power-bi-optimization.md)に関する記事をご覧ください。

## <a name="update-tools-and-sdk-packages"></a>ツールと SDK パッケージを更新する

ツールと SDK パッケージを最新の状態で維持します。

* 最新版の [Power BI Desktop](https://powerbi.microsoft.com/desktop/) を常に使用してください。

* 最新版の [Power BI クライアント SDK](https://github.com/Microsoft/PowerBI-JavaScript) をインストールします。 今後も拡張機能が追加リリースされます。折に触れて最新の状態に更新してください。

## <a name="embed-parameters"></a>埋め込みパラメーター

`powerbi.embed(element, config)` メソッドは、要素と構成を受け取ります。構成パラメーターには、パフォーマンスに影響するフィールドが含まれています。

### <a name="embed-url"></a>埋め込み URL

埋め込み URL を自分で生成することは避けてください。 その代わりに、[レポートの取得](/rest/api/power-bi/reports/getreportsingroup)、[ダッシュボードの取得](/rest/api/power-bi/dashboards/getdashboardsingroup)、[タイルの取得](/rest/api/power-bi/dashboards/gettilesingroup) API を呼び出す方法で埋め込み URL を用意してください。 **_config_** という名称の新しいパラメーターが URL に追加されました。これはパフォーマンス改善に使用されます。

### <a name="permissions"></a>アクセス許可

編集モードでレポートを埋め込まないのであれば、**表示** アクセス許可を与えます。 この方法では、編集モードで使用されるコンポーネントが埋め込みコードによって初期化されることがありません。

### <a name="filters-bookmarks-and-slicers"></a>フィルター、ブックマーク、スライサー

通常、レポート ビジュアルはデータをキャッシュすることで保存されます。 データのキャッシュはパフォーマンスの改善を体感させます。 レポートでは、クエリが実行される間、キャッシュされたデータがレンダリングされます。 フィルター、ブックマーク、またはスライサーが提供されている場合、キャッシュされたデータは関連がなく、ビジュアル クエリが終了した後でのみビジュアルはレンダリングされます。

同じフィルター、ブックマーク、スライサーを使用してレポートを埋め込み、パフォーマンスを向上させるには、既に適用されているフィルター、ブックマーク、スライサーと共にレポートを保存します。 これにより、フィルター、ブックマーク、スライサーを含むキャッシュされたデータでレポートがレンダリングされます。

## <a name="switching-between-reports"></a>レポート間の切り替え

複数のレポートを同じ iframe に埋め込む場合は、レポートごとに新しい iframe を生成しないようにします。 代わりに、異なる構成の `powerbi.embed(element, config)` を使用して、新しいレポートを埋め込みます。

> [!NOTE]
> 顧客向けの埋め込み時のレポートの切り替え ("アプリ所有データ"シナリオとも呼ばれます) では、すべてのレポートとデータセットにアクセスできる埋め込みトークンを使用する必要があります。 詳細については、[トークン API の生成](/rest/api/power-bi/embedtoken/generatetoken)に関する記事をご覧ください。

## <a name="query-caching"></a>クエリ キャッシュ

Power BI Premium 容量または Power BI Embedded 容量を使用する組織では、クエリ キャッシュを利用して、データセットに関連付けられたレポートを高速化できます。

[Power BI でのクエリ キャッシュの詳細について参照してください](../../connect-data/power-bi-query-caching.md)。

## <a name="preload"></a>事前読み込み

`powerbi.preload()` を使用して、エンドユーザーのパフォーマンスを向上させます。 `powerbi.preload()` メソッドによって、後でレポートを埋め込むために使用される javascript、css ファイル、およびその他の成果物がダウンロードされます。

レポートをすぐに埋め込まない場合は、`powerbi.preload()` を呼び出します。 たとえば、埋め込み Power BI コンテンツがホーム ページに表示されない場合は、`powerbi.preload()` を使って、コンテンツを埋め込むために使われる成果物のダウンロードとキャッシュを行います。

## <a name="bootstrapping-the-iframe"></a>iframe のブートストラップ

> [!NOTE]
> iframe をブートストラップするには、[Power BI クライアント SDK](https://github.com/Microsoft/PowerBI-JavaScript) バージョン 2.9 が必要です。

`powerbi.bootstrap(element, config)` を使うと、すべての必須パラメーターが使用可能になる前に埋め込みを開始できます。 ブートストラップ API により、iframe の準備と初期化が実行されます。
ブートストラップ API を使用する場合でも、同じ HTML 要素で `powerbi.embed(element, config)` を呼び出す必要があります。

たとえば、この機能のユースケースの 1 つは、iframe のブートストラップと埋め込みのバックエンド呼び出しを、並行して実行することです。
> [!TIP]
> エンド ユーザーに表示される前に iframe を生成することが可能な場合は、ブートストラップ API を使います。

[iframe ブートストラップの詳細を参照してください](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Bootstrap-For-Better-Performance)。

## <a name="measure-performance"></a>パフォーマンスの計測

### <a name="performance-events"></a>パフォーマンス イベント

埋め込みのパフォーマンスを測定するには、次の 2 つのイベントを使用できます。

1. 読み込み完了イベント: レポートが初期化されるまでの時間 (読み込みが完了すると、Power BI のロゴが表示されなくなります)。
2. レンダリング完了イベント: 実際のデータを使用して、レポートが完全にレンダリングされるまでの時間。 レポートが再度レンダリングされるたびに (フィルターの適用後など) レンダリング完了イベントが発生します。 レポートを計測するには、最初に発生したイベントで計算を行います。

使用可能な場合はキャッシュされたデータがレンダリングされますが、追加のイベントは生成されません。

[イベント処理の詳細を参照してください](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Handling-Events)。

### <a name="performance-analyzer"></a>パフォーマンス アナライザー

レポート要素のパフォーマンスを調べるには、Power BI Desktop でパフォーマンス アナライザーを使用することができます。
パフォーマンス アナライザーを使用すると、各レポート要素のパフォーマンスを測定するログを表示および記録できます。

[パフォーマンス アナライザーの詳細を参照してください](../../create-reports/desktop-performance-analyzer.md)。

> [!NOTE]
> 常に、埋め込まれたレポートのパフォーマンスと、powerbi.com でのパフォーマンスを比較してください。 これは、パフォーマンスの問題の原因を理解するのに役立つ可能性があります。

## <a name="next-steps"></a>次の手順

* [Power BI の最適化ガイド](../../guidance/power-bi-optimization.md)
* [Power BI 埋め込み分析の問題を解決する方法](embedded-troubleshoot.md)
* [Power BI 埋め込み分析の FAQ](embedded-faq.md)