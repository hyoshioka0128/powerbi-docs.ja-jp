---
title: レポート内のビジュアルの相互作用について理解する
description: レポート ページでビジュアルがどのように相互作用するかについて説明する Power BI エンド ユーザー向けドキュメント。
author: mihart
ms.author: mihart
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: pbi-explore
ms.topic: how-to
ms.date: 09/11/2020
LocalizationGroup: Reports
ms.openlocfilehash: bfb96a6c4d078744bdd285f07ea5cf88a55aab25
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96399881"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>Power BI のレポート内でビジュアルがどのように相互作用するか

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

Power BI の優れた機能の 1 つは、レポート ページ上のすべてのビジュアルが相互接続される方法です。 ビジュアルのいずれかのデータ ポイントを選択すると、そのデータを含むページ上の他のすべてのビジュアルが選択に基づいて変化します。 

![ビジュアルの相互作用のビデオ](media/end-user-interactions/interactions.gif)

## <a name="how-visuals-interact-with-each-other"></a>ビジュアルの相互作用のしくみ

既定では、レポート ページ上の 1 つのビジュアルでデータ ポイントを選択すると、そのページ上の他のビジュアルに対してクロスフィルター処理またはクロス強調表示が行われます。 ページ上のビジュアルがどのように相互作用するかは、レポート *デザイナー* によって設定されます。 *デザイナー* には、視覚的な相互作用のオンとオフを切り替えるオプションと、既定のクロスフィルター処理、クロス強調表示、および [詳細表示](end-user-drill.md)の動作を変更するオプションがあります。 

階層または詳細表示を目にしたことがない場合、[Power BI でのドリル ダウン](end-user-drill.md)に関する記事を読んで詳細を学ぶことができます。 

### <a name="cross-filtering-and-cross-highlighting"></a>クロスフィルター処理とクロス強調表示

データに含まれる 1 つの値が他の値にどのように貢献しているかを確認するには、クロスフィルター処理およびクロス強調表示が役立ちます。 *クロスフィルター処理* と *クロス強調表示* という用語は、ここで説明する動作を、 **[フィルター]** ウィンドウを使ってビジュアルのフィルター処理と強調表示を行う場合の動作と区別するために使用しています。  

以下のレポート ページで確認しながら、これらの用語を定義してみましょう。 "セグメント別カテゴリ数量合計" ドーナツ グラフには、"モデレーション " と "利便性" の 2 つの値があります。 

![レポート ページ](media/end-user-interactions/power-bi-interactions-before.png)

1. **[モデレーション]** を選択するとどうなるかを見てみましょう。

    ![ドーナツ グラフで [モデレーション] セグメントを選択した後のレポート ページ](media/end-user-interactions/power-bi-interactions-after.png)

2. **クロスフィルター処理** では、該当しないデータが削除されます。 ドーナツ グラフで **[モデレーション]** を選択すると、折れ線グラフがクロスフィルター処理されます。 折れ線グラフには、[モデレーション] セグメントのデータ ポイントのみが表示されるようになります。 

3. **クロス強調表示** では元のすべてのデータ ポイントが保持されますが、ご自分で選択した部分以外の部分は淡色表示になります。 ドーナツ グラフで **[モデレーション]** を選択すると、縦棒グラフがクロス強調表示されます。 縦棒グラフでは、利便性セグメントに該当するすべてのデータが淡色表示され、[モデレーション] セグメントに該当するすべてのデータが強調表示されます。 


## <a name="considerations-and-troubleshooting"></a>考慮事項とトラブルシューティング
- [詳細表示](end-user-drill.md)に対応しているビジュアルがレポートに含まれる場合、既定では、あるビジュアルに詳細表示を適用してもレポート ページの他のビジュアルは変更されません。 ただし、レポート "*デザイナー*" はこの動作を変更できます。そのため、詳細表示できるビジュアルをチェックして、レポート "*デザイナー*" によって **[他の視覚化に詳細なフィルターを適用する]** が有効にされているかどうかを確認してください。
    
- レポート ページ上のその他のビジュアルをクロスフィルター処理およびクロス強調表示するとき、ビジュアルレベル フィルターは保持されます。 したがって、VisualA にレポート デザイナーまたはユーザーが適用したビジュアル レベルのフィルターがあり、visualA を使用して visualB と相互作用する場合、visualA のビジュアル レベル フィルターが visualB に適用されます。

    ![既に設定されているフィルターが表示されたレポート ページ](media/end-user-interactions/power-bi-visual-filters.png)

## <a name="next-steps"></a>次の手順
[レポート フィルターの使用方法](../consumer/end-user-report-filter.md)


[フィルター処理と強調表示について](end-user-report-filter.md)
