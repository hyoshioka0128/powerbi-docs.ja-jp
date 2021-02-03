---
title: レポート ページのドリルスルーの使用
description: レポート ページのドリルスルーを使用するためのガイド
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 11/28/2019
ms.openlocfilehash: d89e26c0e938504fe64e0f966d27c76e059949a6
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2021
ms.locfileid: "99085523"
---
# <a name="use-report-page-drillthrough"></a>レポート ページのドリルスルーの使用

この記事の対象読者は、Power BI レポートをデザインするレポート作成者です。 [レポート ページのドリルスルー](../create-reports/desktop-drillthrough.md)を作成するときの提案や推奨事項を提供します。

レポート ユーザーが次のフローを達成できるようにレポートをデザインすることをお勧めします。

1. レポート ページを表示します。
2. より深く分析する目的でビジュアル要素を識別します。
3. ドリルスルーするビジュアル要素を右クリックします。
4. 補足分析を実行します。
5. ソース レポート ページに戻ります。

## <a name="suggestions"></a>候補

次の 2 種類のドリルスルー シナリオを検討することをお勧めします。

- [追加の深度](#additional-depth)
- [より広範な分析観点](#broader-perspective)

### <a name="additional-depth"></a>追加の深度

レポート ページの結果の概要が表示されるとき、ドリルスルー ページでは、レポート ユーザーはトランザクションレベルの詳細に移動できます。 このデザイン手法では、補足となるトランザクションを必要なときだけ表示できます。

次の例では、レポート ユーザーが月間売上の概要からドリルスルーしたときの様子を示しています。 ドリルスルー ページには、特定の月を対象とする注文の詳細一覧が含まれます。

!["Sales Summary" というタイトルのマトリックス ビジュアルでは、行の年と月別に、かつ、列の国別に売上がグループ化されます。 ドリルスルー ページも表示されます。](media/report-drillthrough/suggestion-drillthrough-add-depth.png)

### <a name="broader-perspective"></a>より広範な分析観点

ドリルスルー ページでは、追加の深度の真逆のことを実行できます。 このシナリオは、全体的なビューにドリルスルーする場合に最適です。

次の例では、レポート ユーザーが郵便番号からドリルスルーしたときの様子を示しています。 ドリルスルー ページには、その郵便番号に関する全般情報が表示されます。

![あるテーブル ビジュアルに、Zip Code、Average of Violation Points、Average of Grade Rating という 3 つの列があります。 ドリルスルー ページも表示されます。](media/report-drillthrough/suggestion-drillthrough-broader-perspective.png)

## <a name="recommendations"></a>推奨事項

レポートのデザイン時は次の習慣をお勧めします。

- **スタイル:** ドリルスルー ページはレポートと同じテーマとスタイルでデザインすることを検討してください。 そうすることで、同じレポートを使用しているようにユーザーは感じます。
- **ドリルスルー フィルター:** ドリルスルー ページをデザインするとき、実際の結果をプレビューできるように、ドリルスルー フィルターを設定します。 このようなフィルターはレポートを公開する前に必ず削除してください。
- **その他の機能:** ドリルスルー ページはレポート ページのようなものです。 スライサーやフィルターなど、追加の対話機能で機能強化することもできます。
- **空白:** 空白を表示するようなビジュアルは追加しないでください。追加すると、ドリルスルー フィルターが適用されたとき、エラーが表示されます。
- **ページの表示:** ドリルスルー ページを非表示にすることを検討してください。 ドリルスルー ページが表示されている状態を維持することにする場合、以前に設定したドリルスルー フィルターをユーザーが消去するためのボタンを追加してください。 [ブックマーク](../create-reports/desktop-bookmarks.md)をボタンに割り当てます。 ブックマークはすべてのフィルターを削除するように設定してください。
- **戻るボタン:** ドリルスルー フィルターを割り当てると、戻る [ボタン](../create-reports/desktop-buttons.md)が自動的に追加されます。 このボタンを残しておくことをお勧めします。 そうすることで、レポート ユーザーはソース ページに簡単に戻ることができます。
- **気付いてもらう:** ドリルスルー ページに気付いてもらうために、ビジュアル ヘッダー アイコン テキストを設定するか、テキスト ボックスに指示を追加します。 オーバーレイをデザインすることもできます。詳細は[こちらのブログ投稿](https://alluringbi.com/2019/10/23/overlays-for-true-self-serve-reporting/)にあります。

> [!TIP]
> Power BI のページ番号付きレポートのドリルスルーを構成することもできます。 これを行うには、Power BI レポートのリンクを追加します。 リンクでは、[URL パラメーター](https://powerbi.microsoft.com/blog/url-parameters-for-paginated-reports-are-now-available/)を定義できます。

## <a name="next-steps"></a>次の手順

この記事に関する詳細については、次のリソースを参照してください。

- [Power BI Desktop でドリルスルーを使用する](../create-reports/desktop-drillthrough.md)
- わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
- Power BI チームへのご提案は、 [Power BI を改善するためのアイデアをお寄せください](https://ideas.powerbi.com/)
