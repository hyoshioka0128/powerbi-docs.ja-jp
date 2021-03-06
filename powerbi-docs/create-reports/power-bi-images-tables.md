---
title: レポートのテーブルまたはマトリックスに画像を表示する
description: Power BI Desktop で、画像へのハイパーリンクを含む列を作成します。 次に、Power BI Desktop または Power BI サービスで、レポートのテーブル、マトリックス、スライサー、または複数行カードにそれらのハイパーリンクを追加して、画像を表示します。
author: maggiesMSFT
ms.reviewer: ''
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/11/2019
ms.author: maggies
LocalizationGroup: Visualizations
ms.openlocfilehash: 4aa10a08757b9d62d4d8c987aedbede47f936a00
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2020
ms.locfileid: "83344620"
---
# <a name="display-images-in-a-table-matrix-or-slicer-in-a-report"></a>レポートのテーブル、マトリックス、スライサーに画像を表示する

レポートを拡張するのによい方法は、画像を追加することです。 ページ上に静的な画像を表示するのが適した目的もいくつかあります。 しかし、レポート内のデータに関連する画像が必要になる場合もあります。 このトピックでは、テーブル、マトリックス、スライサー、または複数行カードに画像を表示する方法について説明します。 

![テーブル内の URL 画像](media/power-bi-images-tables/power-bi-url-images-table.png)

## <a name="add-images-to-your-report"></a>レポートに画像を追加する

1. 画像の URL を含む列を作成します。 要件については、後の「[考慮事項](#considerations)」を参照してください。

1. その列を選択します。 **[モデリング]** リボンの **[データ カテゴリ]** で、 **[イメージの URL]** を選択します。

    ![[データ カテゴリ] を [イメージの URL] に設定する](media/power-bi-images-tables/power-bi-set-url-image.png)

1. テーブル、マトリックス、スライサー、または複数行カードに列を追加します。

    ![画像が含まれるスライサー](media/power-bi-images-tables/power-bi-url-images-slicer.png)

## <a name="considerations"></a>考慮事項

- 画像のファイル形式は、.bmp、.jpg、.jpeg、.gif、.png、.svg のいずれかである必要があります。
- URL は、SharePoint などのサインインが必要なサイトのものではなく、匿名でアクセスできる必要があります。 ただし、画像が SharePoint または OneDrive でホストされている場合は、その画像を直接ポイントする埋め込みコードを取得できる場合があります。 


## <a name="next-steps"></a>次のステップ

[ページ レイアウトと書式設定](/learn/modules/visuals-in-power-bi/12-formatting)

[Power BI サービスのデザイナー向けの基本的な概念](../fundamentals/service-basic-concepts.md)

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。
