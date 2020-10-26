---
title: Power BI ビジュアルの概念
description: この記事では、ビジュアルを Power BI と統合する方法と、ユーザーが Power BI でビジュアルを操作する方法について説明します。
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 94926ccf0fa214ca4c65808a7476842c22308359
ms.sourcegitcommit: 50b21718a167c2b131313b4135c8034c6f027597
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/14/2020
ms.locfileid: "92048857"
---
# <a name="power-bi-visuals-system-integration"></a>Power BI ビジュアルのシステム統合

この記事では、ビジュアルを Power BI と統合する方法と、ユーザーが Power BI でビジュアルを操作する方法について説明します。 

次の図は、ブックマークの選択など、ユーザーが行う一般的なビジュアルベースのアクションが Power BI でどのように処理されるかを示しています。

![Power BI ビジュアル アクションの図](media/power-bi-visuals-concept/visual-concept.svg)

## <a name="visuals-get-updates-from-power-bi"></a>ビジュアルで Power BI から更新を取得する

ビジュアルでは、`update` メソッドを呼び出して Power BI から更新を取得します。 `update` メソッドには、通常、ビジュアルの主要なロジックが含まれており、グラフの表示やデータの視覚化が行われます。

ビジュアルから `update` メソッドが呼び出されると、更新がトリガーされます。

## <a name="action-and-update-patterns"></a>アクションと更新のパターン

Power BI ビジュアルのアクションとそれに続く更新は、次の 3 つのパターンのいずれかで発生します。

* ユーザーが Power BI を介してビジュアルを操作する。
* ユーザーがビジュアルを直接操作する。
* ビジュアルと Power BI が対話する。

### <a name="user-interacts-with-a-visual-through-power-bi"></a>ユーザーが Power BI を介してビジュアルを操作する

* ユーザーがビジュアルの [プロパティ] パネルを開きます。

    ユーザーがビジュアルの [プロパティ] パネルを開くと、サポートされているオブジェクトとプロパティが Power BI によってビジュアルの *capabilities.json* ファイルから取得されます。 プロパティの実際の値を受け取るために、Power BI からビジュアルの `enumerateObjectInstances` メソッドが呼び出されます。 ビジュアルからは、プロパティの実際の値が返されます。

    詳細については、「[Power BI ビジュアルの機能とプロパティ](capabilities.md)」を参照してください。

* ユーザーは、[書式] パネルで[ビジュアルのプロパティを変更](../../visuals/power-bi-visualization-customize-title-background-and-legend.md)します。

    ユーザーが [書式] パネルでプロパティの値を変更すると、Power BI によってビジュアルの `update` メソッドが呼び出されます。 Power BI から新しい `options` オブジェクトが `update` メソッドに渡されます。 オブジェクトには、新しい値が格納されます。

    詳細については、「[Power BI ビジュアルのオブジェクトとプロパティ](objects-properties.md)」を参照してください。

* ユーザーがビジュアルのサイズを変更します。

    ユーザーがビジュアルのサイズを変更すると、Power BI によって新しい `options` オブジェクトを使用して `update` メソッドが呼び出されます。 `options` オブジェクトには、ビジュアルの新しい幅と高さを含む `viewport` オブジェクトが入れ子になっています。

* ユーザーは、レポート、ページ、またはビジュアル レベルでフィルターを適用します。

    Power BI では、フィルター条件に基づいてデータがフィルター処理されます。 Power BI では、ビジュアルの `update` メソッドが呼び出され、新しいデータでビジュアルが更新されます。

    入れ子になったオブジェクトのいずれかに新しいデータがある場合、ビジュアルには `options` オブジェクトの新しい更新が取得されます。 更新がどのように行われるかは、ビジュアルのデータ ビュー マッピング構成によって異なります。

    詳細については、「[Power BI ビジュアルでのデータ ビューのマッピングについて理解する](dataview-mappings.md)」を参照してください。

* ユーザーは、レポート内の別のビジュアルにあるデータ ポイントを選択します。

    ユーザーがレポート内の別のビジュアルにあるデータ ポイントを選択すると、Power BI では選択したデータ ポイントがフィルター処理されるか強調表示され、ビジュアルの `update` メソッドが呼び出されます。 ビジュアルによって、フィルター処理された新しいデータが取得されます。または、強調表示の配列を使用して同じデータが取得されます。

    詳細については、「[Power BI ビジュアルでデータ ポイントを強調表示する](highlight.md)」を参照してください。

* ユーザーは、レポートの [ブックマーク] パネルでブックマークを選択します。

    ユーザーがレポートの [ブックマーク] パネルでブックマークを選択すると、次の 2 つのアクションのいずれかが発生します。

    * `registerOnSelectionCallback` メソッドによって渡され、登録された関数が Power BI から呼び出されます。 コールバック関数によって、対応するブックマークの選択範囲の配列が取得されます。

    * Power BI によって、`options` オブジェクト内の対応する `filter` オブジェクトを使用して `update`メソッドが呼び出されます。

    いずれの場合でも、ビジュアルの状態は、常に受け取った選択または `filter` オブジェクトに従って変化します。

    ブックマークとフィルターの詳細については、「[Power BI ビジュアルでの Visual Filters API](filter-api.md)」を参照してください。

### <a name="user-interacts-with-the-visual-directly"></a>ユーザーがビジュアルを直接操作する

* ユーザーがデータ要素にマウス ポインターを合わせます。

    ビジュアルには、Power BI Tooltips API を介してデータ ポイントに関する詳細情報を表示できます。 ユーザーがビジュアル要素の上にマウスを移動すると、ビジュアルによってイベントが処理され、関連するツールヒント要素に関するデータが表示されます。 ビジュアルには、標準のツールヒントまたはレポート ページのツールヒントが表示されます。

    詳細については、「[Power BI ビジュアルのヒント](add-tooltips.md)」を参照してください。

* ユーザーがビジュアル プロパティを変更します (たとえば、ユーザーがツリーを展開し、ビジュアルの状態がビジュアル プロパティに保存されます)。

    Power BI API を使用してビジュアルにプロパティ値を保存できます。 たとえば、ユーザーがビジュアルを操作し、ビジュアルのプロパティ値を保存または更新する必要がある場合、ビジュアルから `presistProperties` メソッドを呼び出すことができます。

* ユーザーが URL を選択します。

    既定では、ビジュアルから URL を直接開くことはできません。 代わりに、新しいタブで URL を開くには、ビジュアルから `launchUrl` メソッドを呼び出し、URL をパラメーターとして渡す方法があります。

    詳細については、「[起動 URL を作成する](launch-url.md)」を参照してください。

* ユーザーがビジュアルを介してフィルターを適用します。

    ビジュアルから `applyJsonFilter` メソッドを呼び出し、条件を渡して他のビジュアルのデータをフィルター処理できます。 基本、詳細、タプル フィルターなど、いくつかの種類のフィルターを使用できます。

    詳細については、「[Power BI ビジュアルでの Visual Filters API](filter-api.md)」を参照してください。

* ユーザーがビジュアル内の要素を選択します。

    Power BI ビジュアルでの選択の詳細については、[Power BI ビジュアルの選択を使用して対話機能を追加する](selection-api.md)方法の記事を参照してください。

### <a name="visual-interacts-with-power-bi"></a>ビジュアルと Power BI が対話する

* ビジュアルを使うと、より多くのデータを Power BI に要求できます。

    ビジュアルでは、データが部分ごとに処理されます。 `fetchMoreData` API メソッドによって、データセット内のデータの次のフラグメントが要求されます。

    詳細については、「[より多くのデータを Power BI からフェッチする](fetch-more-data.md)」を参照してください。

* イベント サービスがトリガーされます。

    Power BI を使って、レポートを PDF にエクスポートすることや、メールでレポートを送信することができます (認定済みビジュアルにのみ適用されます)。 レンダリングが完了し、ビジュアルを PDF またはメールとしてキャプチャする準備ができたことを Power BI に通知するには、ビジュアルから Rendering Events API を呼び出す必要があります。

    詳細については、「[Power BI から PDF にレポートをエクスポートする](../../consumer/end-user-pdf.md)」を参照してください。

    イベント サービスの詳細については、「[Power BI ビジュアルでイベントをレンダリングする](event-service.md)」を参照してください。

## <a name="next-steps"></a>次の手順

視覚化の作成と Microsoft AppSource への追加に興味がある場合は 次の記事を参照してください。

* [Power BI の円形カード視覚化の開発](./develop-circle-card.md)
* [Power BI ビジュアルをパートナー センターに発行する](office-store.md)
