---
title: Power BI でスモール マルチプルと対話する (プレビュー)
description: この記事では、スモール マルチプル (または格子) と対話する方法について説明します。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: how-to
ms.date: 02/05/2021
LocalizationGroup: Visualizations
ms.openlocfilehash: 6d700d4a4bb7453f7630c76c5a3f265ee022e02a
ms.sourcegitcommit: f17acb16018752c234db6bff1f51f5130be12c58
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99628213"
---
# <a name="interact-with-small-multiples-in-power-bi-preview"></a>Power BI でスモール マルチプルと対話する (プレビュー)

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

スモール マルチプル (または格子) では、視覚エフェクトがそれ自体の複数のバージョンに分割されます。 この記事では、それらとの対話を最大限に活用する方法について説明します。

:::image type="content" source="media/power-bi-visualization-small-multiples/small-mulitple-sales-category-region.png" alt-text="カテゴリと地域に対するスモール マルチプルのスクリーンショット。":::

スモール マルチプルを作成する場合は、 「[Power BI でスモール マルチプルを作成する (プレビュー)](power-bi-visualization-small-multiples.md)」を参照してください。

## <a name="scroll-in-a-small-multiple"></a>スモール マルチプルをスクロールする

スモール マルチプルには、グリッドに収まるよりも多くの個別のグラフが含まれている場合があります。 その場合は、下にスクロールして残りのカテゴリを表示することができます。

カテゴリ X 軸に多くのカテゴリが含まれる場合は、その軸のコピーごとにスクロール バーも表示されます。 その軸をスクロールすると、すべてが一緒に移動します。 スクロール ホイールを使用している場合は、Shift キーを押しながらカテゴリ軸をスクロールします。

## <a name="select-data-to-cross-highlight"></a>クロス強調表示するデータを選択する

視覚エフェクトのさまざまな部分を選択すると、データのさまざまなサブセットを選択できます。

### <a name="select-data-points"></a>データ ポイントを選択する

1 つのマルチプル上のデータ ポイントにマウス ポインターを合わせると、そのマルチプルにツールヒントが表示されます。 また、折れ線グラフの X 軸にガイド線も表示されます。 そのデータ ポイントを選択すると、その軸の値とスモール マルチプルのカテゴリの両方によって他の視覚エフェクトがクロス強調表示され、その他のマルチプルが暗くなります。

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-select-data-point.png" alt-text="スモール マルチプルのデータ ポイントを選択します。":::

### <a name="select-a-categorical-axis-value"></a>カテゴリ軸の値を選択する

カテゴリ ラベルを選択して、その軸の値で他の視覚エフェクトをクロス強調表示します。

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-select-category-axis.png" alt-text="スモール マルチプルのカテゴリ軸を選択します。":::

### <a name="select-a-title"></a>タイトルを選択する

マルチプルのタイトルを選択すると、そのサブヘッダーのカテゴリによって他の視覚エフェクトがクロス強調表示されます。

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-select-title.png" alt-text="スモール マルチプルのタイトルを選択します。":::

### <a name="legend"></a>凡例

凡例のカテゴリを選択すると、他の視覚エフェクトがクロス強調表示され、他のマルチプルがクロス強調表示されます。

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-select-legend.png" alt-text="スモール マルチプルの凡例の項目を選択します。":::


## <a name="sort"></a>並べ替え

新しい並べ替え機能を使用すると、1 つの視覚エフェクトの複数の側面を一度に並べ替えることができます。 各マルチプルのカテゴリによって、また軸によって並べ替えます。 

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-sort.png" alt-text="スモール マルチプルを並べ替えます。":::

## <a name="next-steps"></a>次のステップ

[Power BI でスモール マルチプルを作成する (プレビュー)](power-bi-visualization-small-multiples.md)
