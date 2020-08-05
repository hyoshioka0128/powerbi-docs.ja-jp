---
title: レポート内のビジュアルをカスタマイズする
description: レポートを編集することなく、独自のビューを作成します。
author: mihart
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 05/21/2020
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: a731feb822fcda8fd6478094f8393faa34b6b2bf
ms.sourcegitcommit: 2131f7b075390c12659c76df94a8108226db084c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2020
ms.locfileid: "87537345"
---
# <a name="personalize-visuals-in-a-report"></a>レポート内のビジュアルをカスタマイズする

[!INCLUDE[consumer-appliesto-ynnn](../includes/consumer-appliesto-ynnn.md)]

すべてのユーザーの要件を満たす 1 つのビジュアルを作成するのは困難です。 しかし、同僚のレポートを共有している場合、その同僚に変更を行うよう依頼することなく、こちらでビジュアルを変更したくなることがあります。 

たとえば、軸の内容を入れ替えたり、ビジュアルの種類を変更したり、ツールヒントに何かを追加したりしたくなることがあります。 **このビジュアルのカスタマイズ**機能を使用すると、必要に応じて自分でビジュアルに変更を加え、後で表示できるようにブックマークとして保存することができます。 レポートに対する編集アクセス許可も必要ありません。

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


## <a name="personalize-visuals-in-the-power-bi-service"></a>Power BI サービスでビジュアルをカスタマイズする

ビジュアルをカスタマイズすることで、レポートの読み取りビューを離れることなく、さまざまな方法でデータを探索できます。 次の例では、ニーズに合わせて視覚化を変更するさまざまな方法を示します。 

1. Power BI サービスの読み取りビューでレポートを開きます。

2. ビジュアルのメニュー バーにある **[Personalize this visual]\(このビジュアルのカスタマイズ\)** ![[Personalize this visual]\(このビジュアルのカスタマイズ\) アイコン](media/end-user-personalize-visuals/power-bi-personalize-visual-icon.png) アイコンを選択します。 

3. **[個人用設定]** のフィールドをクリアするには、 **[その他のオプション] (...)** を選択し、 **[フィールドの削除]** を選択します。

### <a name="change-the-visualization-type"></a>視覚化の種類の変更

積み上げ縦棒グラフにした方が適切にデータが表示されると思われる場合は、 **視覚化の種類**を変更します。

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-change-visual-type.png" alt-text="視覚化の種類を変更する":::
 
### <a name="swap-out-a-measure-or-dimension"></a>メジャーまたはディメンションをスワップ アウトする
置換するフィールドを選択して X 軸に使用されているフィールドを置き換え、別のフィールドを選択します。

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-change-axis.png" alt-text="軸を変更する":::
 
### <a name="add-or-remove-a-legend"></a>凡例を追加または削除する
凡例を追加すると、カテゴリに基づいてビジュアルの色分けを設定できます。 この例では、会社名に基づいて色分けされています。 

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-change-legend.png" alt-text="凡例を追加または削除する":::

### <a name="compare-two-or-more-different-measures"></a>2 つ以上の異なるメジャーを比較する
[+] アイコンを使用してビジュアルの複数のメジャーを追加することにより、異なるメジャーの値を比較対照することができます。 メジャーを削除するには、 **[その他のオプション] (...)** を選択し、 **[フィールドの削除]** を選択します。

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-compare-measures.png" alt-text="メジャーを比較する":::

### <a name="change-aggregations"></a>集計を変更する
メジャーの計算方法を変更するには、 **[個人用設定]** ペインで集計を変更します。 **[その他のオプション] (...)** を選択し、使用する集計を選択します。

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-change-aggregation.png" alt-text="集計を変更する":::

### <a name="capture-changes"></a>変更をキャプチャする 
個人用ブックマークを使用して、カスタマイズされたビューに戻ることができるように変更をキャプチャします。 **[ブックマーク]**  >  **[個人用ブックマーク]** の順に選択し、ブックマークに名前を付けます。 

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-bookmark.png" alt-text="ブックマークを作成する":::
 
また、ブックマークを既定のビューに設定することもできます。

### <a name="share-changes"></a>変更を共有する 
読み取りと再共有のアクセス許可を持っている場合は、レポートを共有するときに、自分の変更内容を含めることを選択できます。

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-share-changes.png" alt-text="変更を共有する":::
 
### <a name="reset-all-your-changes-to-a-report"></a>レポートへのすべての変更をリセットする

レポート キャンバスの右上隅にある **[既定にリセット]** を選択します。 これにより、レポート内のすべての変更が削除され、作成者が最後に保存したレポート ビューに設定し直されます。

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-reset-all.png" alt-text="すべての変更をリセットする":::
 
### <a name="reset-all-your-changes-to-a-visual"></a>ビジュアルへのすべての変更をリセットする

ビジュアルのメニュー バーにある **[Reset this visual]\(このビジュアルをリセットする\)** を選択すると、特定のビジュアルに対するすべての変更が削除され、作成者が最後に保存したそのビジュアルのビューに設定し直しされます。

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-reset-visual.png" alt-text="すべてのビジュアルの変更をリセットする":::
 
### <a name="clear-recent-changes"></a>最近の変更をクリアする

消しゴムアイコンを選択すると、 **[個人用設定]** ペインを開いた後に加えた最近の変更がすべてクリアされます。  

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-revert-changes.png" alt-text="最近の変更を元に戻す":::

## <a name="limitations-and-known-issues"></a>制限事項と既知の問題

現在、この機能には注意すべきいくつかの制限事項があります。

- **[Personalize this visual]\(このビジュアルのカスタマイズ\)** は、レポート全体または特定のビジュアルに対して無効にできます。 ビジュアルをカスタマイズするオプションが表示されない場合は、テナント管理者またはレポート所有者に確認してください。 レポートの所有者の連絡先情報を表示するには、Power BI のメニュー バーでレポートの名前を選択します。
- ユーザー探索は自動的に保持されません。 変更をキャプチャするには、個人用ブックマークとしてビューを保存する必要があります。
- この機能は、iOS と Android タブレット用の Power BI モバイルアプリ、および Power BI Windows アプリでサポートされています。スマートフォン用の Power BI モバイル アプリではサポートされていません。 ただし、Power BI サービスの使用中に個人用ブックマークに保存した視覚エフェクトの変更は、すべての Power BI モバイル アプリに適用されます。

また、現在対処中のいくつかの既知の問題もあります。

- 階層の追加はサポートされていません。個々の子項目を追加する必要があります。
- 個人用ブックマークを使用すると、選択した順序によって、得られる結果が多少異なる場合があります。 不一致が発生する場合があるのは、レポートの完全な状態をキャプチャするのではなく、加えた変更のみキャプチャするためです。 回避策として、 **[既定値にリセット]** を選択した後、表示するブックマークを選択します。 

## <a name="next-steps"></a>次の手順
[レポートのビジュアルを静的画像としてコピーする](../visuals/power-bi-visualization-copy-paste.md)    
他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。

