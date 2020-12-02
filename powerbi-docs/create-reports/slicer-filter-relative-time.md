---
title: Power BI で相対時間のスライサーまたはフィルターを使用する
description: Power BI で相対的な時間範囲を制限するスライサーまたはフィルターを使う方法について説明します。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 07/06/2020
LocalizationGroup: Create reports
ms.openlocfilehash: 4b12760584df2471bf02029be0fb428d1ab21e4c
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96387553"
---
# <a name="use-a-relative-time-slicer-and-filter-in-power-bi"></a>Power BI で相対時間のスライサーおよびフィルターを使用する

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

新しい高速更新シナリオでは、より小さな時間枠をフィルター処理する機能が便利な場合があります。 相対時間スライサーまたは相対時間フィルターを使用して、データ モデルの任意の日付列または時間列に時間ベースのフィルターを適用することができます。 たとえば、相対時間スライサーを使用すると、過去の数分または数時間以内のビデオ ビューのみを表示できます。 

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time.gif" alt-text="相対時間の例のスクリーンショット。":::

この機能は、[ページの自動更新](../create-reports/desktop-automatic-page-refresh.md)機能と一緒に使用する必要はありません。 ただし、多くの相対時間シナリオは、ページの自動更新機能と組み合わせてうまく使用できます。  

> [!NOTE]
> 相対時間のフィルターまたはスライサーをページ レベルまたはレポート レベルで適用するとき、共有 *アンカー* 日時を使用すると、そのページまたはレポートのすべてのビジュアルがまったく同じ時間範囲にフィルターされます。 ビジュアルの実行時間は多少異なる場合があるため、この共有アンカー日時によって、ページ全体またはレポート全体でビジュアルが確実に同期されます。 アンカー日時の詳細については、[こちらの](#understanding-anchor-time)記事を参照してください。

## <a name="create-a-relative-time-slicer-or-filter"></a>相対時間のスライサーまたはフィルターを作成する

この機能を有効にした後、日付または時間フィールドをスライサーのフィールド ウェルまたは [フィルター] ペインのドロップ ゾーンにドラッグ アンド ドロップできます。 

### <a name="create-a-slicer"></a>スライサーの作成

1. 日付または時刻のフィールドをキャンバスにドラッグします。

2. **[スライサー]** の視覚化の種類を選択します。

    :::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-create-slicer.png" alt-text="時間スライサーの作成のスクリーンショット。":::

### <a name="create-a-filter"></a>フィルターを作成する
 
- **このビジュアル**、**このページ**、または **すべてのページ** について、日付または時刻フィールドを [フィルター] ペインにドラッグします。

### <a name="set-relative-time"></a>相対時間を設定する 

次に、フィルターの種類を **[相対時間]** に変更します。

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-set.png" alt-text="相対時間への変更のスクリーンショット。":::
 
スライサーでは、次のようになります。

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-slicer.png" alt-text="スライサーでの相対時間のスクリーンショット。":::

フィルター カードでは、次のようになります。 

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-filter.png" alt-text="フィルターでの相対時間のスクリーンショット。":::
 
この新しいフィルターの種類を使用すると、 **[Last]\(前回\)** 、 **[Next]\(次回\)** 、または **[This]\(今回\) の期間** に基づいてフィルター処理できます。 

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-last-next.png" alt-text="[Last]\(前回\)、[Next]\(次回\)、または [This]\(今回\) の期間を選択するスクリーンショット。":::
 
整数と時間単位を使用して、時間枠を指定します。 **[分]** または **[時間]** を指定します。
 
:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-minutes-hours.png" alt-text="分または時間を選択するスクリーンショット。":::

キャンバス上のスペースを節約する必要がある場合は、[フィルター] ペインでフィルター カードとして相対時間フィルターを作成することもできます。

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-set-filter.png" alt-text="代わりにフィルターで相対時間を設定するスクリーンショット。":::
 
## <a name="understanding-anchor-time"></a>アンカー時間について

フィルターがページ レベルまたはレポート レベルで適用された場合、そのページまたはレポートのすべてのビジュアルは、正確に同じ時間範囲に同期されます。 これらのクエリは、*アンカー時間* と呼ばれる時間を基準としてすべて発行されます。 アンカー時間は、次の条件で自動的に更新されます。

- 最初のページ読み込み。
- 手動更新。
- 自動または変更の検出によるページ更新。
- モデルの変更。

### <a name="anchor-time-exceptions"></a>アンカー時間の例外

- Q&A ビジュアルを使用した相対時間フィルターは、Q&A ビジュアルを標準ビジュアルに変換しない限り、このアンカー時間を基準としません。 ただし、主要なインフルエンサや分解ツリーなどのその他の AI ビジュアルは、アンカー時間と同期されます。 
- また、相対日付フィルターやスライサーは、相対時間フィルターが存在しなければ、アンカー時間を基準としません。 相対日付フィルターと相対時間フィルターが同じページにある場合、相対日付フィルターはアンカー時間に従います。

## <a name="limitations-and-considerations"></a>制限と考慮事項

現在、相対時間スライサーおよびフィルターには、次の制限事項と考慮事項が適用されています。

- **タイム ゾーンの考慮**:Power BI のデータ モデルには、タイム ゾーン情報が含まれていません。 モデルは時間を保存できますが、タイム ゾーンの指定はありません。 スライサーとフィルターは、常に協定世界時 (UTC) に基づいています。 レポートでフィルターを設定して、別のタイム ゾーンにいる同僚に送る場合、双方とも同じデータが表示されます。 ご自分または同僚が UTC タイム ゾーンを使用していない場合は、両方が両者の間の時刻のずれを考慮する必要があります。 クエリ エディターを使用して、キャプチャされたデータを現地のタイム ゾーンから UTC に変換してください。
- この新しいフィルターの種類は、Power BI Desktop、Power BI サービス、Power BI Embedded、および Power BI モバイル アプリでサポートされています。 ただし、[Web に公開] ではサポートされていません。

- **クエリ キャッシュ**:クライアント キャッシュが使用されます。 たとえば、"最後の 1 分"、"最後の 5 分" を指定してから "最後の 1 分" に戻すとします。 その時点で、ページを更新したりページが自動的に更新されたりしない限り、最初に実行したときと同じ結果が表示されます。

## <a name="next-steps"></a>次のステップ

- [Power BI で相対日付のスライサーおよびフィルターを使用する](../visuals/desktop-slicer-filter-date-range.md)
- [Power BI のスライサー](../visuals/power-bi-visualization-slicers.md)
