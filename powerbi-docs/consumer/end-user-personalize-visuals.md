---
title: レポート内のビジュアルをカスタマイズする
description: レポートを編集することなく、独自のビューを作成します。
author: mihart
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 10/13/2020
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 718363da3bd1f66de199db8d854d8d23d6de3eb5
ms.sourcegitcommit: eab5a02520c421a57019595c03e9ecfdb41d52ad
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/20/2020
ms.locfileid: "92256757"
---
# <a name="personalize-visuals-in-a-report"></a>レポート内のビジュアルをカスタマイズする

[!INCLUDE[consumer-appliesto-ynny](../includes/consumer-appliesto-ynny.md)]

すべてのユーザーの要件を満たす 1 つのビジュアルを作成するのは困難です。 しかし、同僚のレポートを共有している場合、その同僚に変更を行うよう依頼することなく、こちらでビジュアルを変更したくなることがあります。 

たとえば、軸の内容を入れ替えたり、ビジュアルの種類を変更したり、ツールヒントに何かを追加したりしたくなることがあります。 **[Personalize this visual]\(この視覚エフェクトのカスタマイズ\)** 機能を使用すると、必要に応じて自分で視覚エフェクトに変更を加え、後で表示できるように[ブックマーク](end-user-bookmarks.md)として保存することができます。 レポートに対する編集アクセス許可も必要ありません。

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize.png" alt-text="ビジュアルをカスタマイズする":::
 
## <a name="what-you-can-change"></a>変更できる内容

この機能を使用して Power BI レポートのビジュアルをアドホックに探索できるため、さらに深い分析情報を得ることができます。 変更できる内容の一部を次に示します。 使用可能なオプションは、ビジュアルの種類によって異なります。 

- 視覚化の種類の変更
- メジャーまたはディメンションをスワップ アウトする
- 凡例を追加または削除する
- 2 つ以上のメジャーを比較する
- 集計を変更する、など

この機能によって、新しい探索機能が使用できるようになるだけではなく、 加えた変更をキャプチャして共有する方法も含まれています。

- 変更をキャプチャする
- 変更を共有する
- レポートに対するすべての変更をリセットする
- ビジュアルに対するすべての変更をリセットする
- 最近の変更をクリアする

> [!IMPORTANT]
> 視覚エフェクトをカスタマイズする機能は、レポート "*デザイナー*" で有効にする必要があります。 **[Personalize this visual]\(この視覚エフェクトのカスタマイズ\)** ![[Personalize this visual]\(この視覚エフェクトのカスタマイズ\)](media/end-user-personalize-visuals/power-bi-personalize-visual-icon.png) アイコンが表示されない場合、レポート デザイナーは現在のレポートに対してこの機能を有効にしていません。 この機能を有効にするには、レポートの所有者または Power BI 管理者に確認してください。 レポートの所有者の連絡先情報を表示するには、Power BI のメニュー バーでレポートの名前を選択します。

## <a name="personalize-visuals-in-the-power-bi-service"></a>Power BI サービスでビジュアルをカスタマイズする

視覚エフェクトをカスタマイズすることで、[レポートの読み取りビュー](end-user-reading-view.md)を離れることなく、さまざまな方法でデータを探索できます。 次の例では、ニーズに合わせて視覚化を変更するさまざまな方法を示します。 

1. Power BI サービスの読み取りビューでレポートを開きます。

2. ビジュアルのメニュー バーにある **[Personalize this visual]\(このビジュアルのカスタマイズ\)** ![[Personalize this visual]\(このビジュアルのカスタマイズ\) アイコン](media/end-user-personalize-visuals/power-bi-personalize-visual-icon.png) アイコンを選択します。 

### <a name="change-the-visualization-type"></a>視覚化の種類の変更

積み上げ縦棒グラフにした方が適切にデータが表示されると思われる場合は、 **視覚化の種類**を変更します。

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-change-visual-type.png" alt-text="ビジュアルをカスタマイズする":::
 
### <a name="swap-out-a-measure-or-dimension"></a>メジャーまたはディメンションをスワップ アウトする
置換するフィールドを選択して X 軸に使用されているフィールドを置き換え、別のフィールドを選択します。

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-change-axis.png" alt-text="ビジュアルをカスタマイズする":::
 
### <a name="add-or-remove-a-legend"></a>凡例を追加または削除する
凡例を追加すると、カテゴリに基づいてビジュアルの色分けを設定できます。 この例では、会社名に基づいて色分けされています。 

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-change-legend.png" alt-text="ビジュアルをカスタマイズする":::

### <a name="change-the-placement-of-fields"></a>フィールドの配置を変更する

ドラッグ アンド ドロップを使用して、同じ視覚エフェクト プロパティ内で、または異なる視覚エフェクト プロパティ間でも、フィールドの配置を変更できます。 たとえば、凡例内のフィールドを視覚エフェクトの軸にすばやく移動できます。

:::image type="content" source="media/end-user-personalize-visuals/personalize-drag-and-drop.png" alt-text="ビジュアルをカスタマイズする":::

テーブルやマトリックスの列の順序をすばやく並べ替えることもできます。

:::image type="content" source="media/end-user-personalize-visuals/personalize-reorder-columns.png" alt-text="ビジュアルをカスタマイズする":::

### <a name="compare-two-or-more-different-measures"></a>2 つ以上の異なるメジャーを比較する
[+] アイコンを使用してビジュアルの複数のメジャーを追加することにより、異なるメジャーの値を比較対照することができます。 メジャーを削除するには、 **[その他のオプション] (...)** を選択し、 **[フィールドの削除]** を選択します。

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-compare-measures.png" alt-text="ビジュアルをカスタマイズする":::

### <a name="change-aggregations"></a>集計を変更する
メジャーの計算方法を変更するには、 **[個人用設定]** ペインで集計を変更します。 **[その他のオプション] (...)** を選択し、使用する集計を選択します。

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-change-aggregation.png" alt-text="ビジュアルをカスタマイズする":::

### <a name="capture-changes"></a>変更をキャプチャする 
個人用ブックマークを使用して、カスタマイズされたビューに戻ることができるように変更をキャプチャします。 **[ブックマーク]**  >  **[個人用ブックマーク]** の順に選択し、ブックマークに名前を付けます。 

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-bookmark.png" alt-text="ビジュアルをカスタマイズする":::
 
また、ブックマークを既定のビューに設定することもできます。

### <a name="share-changes"></a>変更を共有する 
読み取りと再共有のアクセス許可を持っている場合は、レポートを共有するときに、自分の変更内容を含めることを選択できます。

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-share-changes.png" alt-text="ビジュアルをカスタマイズする":::
 
### <a name="reset-all-your-changes-to-a-report"></a>レポートへのすべての変更をリセットする

レポート キャンバスの右上隅にある **[既定にリセット]** を選択します。 これにより、レポート内のすべての変更が削除され、作成者が最後に保存したレポート ビューに設定し直されます。

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-reset-all.png" alt-text="ビジュアルをカスタマイズする":::
 
### <a name="reset-all-your-changes-to-a-visual"></a>ビジュアルへのすべての変更をリセットする

ビジュアルのメニュー バーにある **[Reset this visual]\(このビジュアルをリセットする\)** を選択すると、特定のビジュアルに対するすべての変更が削除され、作成者が最後に保存したそのビジュアルのビューに設定し直しされます。

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-reset-visual.png" alt-text="ビジュアルをカスタマイズする":::
 
### <a name="clear-recent-changes"></a>最近の変更をクリアする

消しゴムアイコンを選択すると、 **[個人用設定]** ペインを開いた後に加えた最近の変更がすべてクリアされます。  

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-revert-changes.png" alt-text="ビジュアルをカスタマイズする":::

## <a name="limitations"></a>制限事項

現在、この機能には注意すべきいくつかの制限事項があります。

- **[Personalize this visual]\(このビジュアルのカスタマイズ\)** は、レポート全体または特定のビジュアルに対して無効にできます。 視覚エフェクトをカスタマイズするオプションが表示されない場合は、Power BI 管理者またはレポート所有者に確認してください。 レポートの所有者の連絡先情報を表示するには、Power BI のメニュー バーでレポートの名前を選択します。
- ユーザー探索は自動的に保持されません。 変更をキャプチャするには、個人用ブックマークとしてビューを保存する必要があります。
- この機能は、iOS と Android タブレット用の Power BI モバイルアプリ、および Power BI Windows アプリでサポートされています。スマートフォン用の Power BI モバイル アプリではサポートされていません。 ただし、Power BI サービスの使用中に個人用ブックマークに保存した視覚エフェクトの変更は、すべての Power BI モバイル アプリに適用されます。

## <a name="next-steps"></a>次の手順
[レポートのビジュアルを静的画像としてコピーする](../visuals/power-bi-visualization-copy-paste.md)    
他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。
