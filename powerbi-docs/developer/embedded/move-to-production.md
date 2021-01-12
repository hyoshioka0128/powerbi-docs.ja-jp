---
title: 埋め込み BI 分析情報を向上させるため、Power BI 埋め込み分析アプリケーションを運用環境に移行する
description: Power BI アプリケーションを運用環境に移行するために必要な手順について説明します。 Power BI 埋め込み分析を使用して、より優れた埋め込み BI インサイトを有効にします。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.topic: tutorial
ms.service: powerbi
ms.subservice: powerbi-developer
ms.custom: seodec18
ms.date: 06/02/2020
ms.openlocfilehash: 71eff0f09c0e34ffd8789f1b56347d754b6589bc
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2021
ms.locfileid: "97886674"
---
# <a name="move-your-embedded-app-to-production"></a>埋め込みアプリを運用環境に移行する

アプリケーションの開発が完了したら、運用環境に移行するために、容量を持つワークスペースに戻る必要があります。

> [!Important]
> すべてのワークスペース (レポートまたはダッシュボードが含まれるワークスペースとデータセットが含まれるワークスペース) が容量に割り当てられている必要があります。

## <a name="create-a-capacity"></a>容量を作成する

容量を作成することで、顧客用のリソースを所有することができます。 選択できる容量には、次の 2 種類があります。

* **Power BI Premium** - 2 つの SKU ファミリ (*EM* および *P*) で利用可能なテナントレベルの Microsoft 356 サブスクリプションです。Power BI コンテンツを埋め込む場合、このソリューションは "*Power BI 埋め込み*" と呼ばれます。 このサブスクリプションの詳細については、「[Power BI Premium とは](../../admin/service-premium-what-is.md)」を参照してください。

* **Azure Power BI Embedded** - [Microsoft Azure portal](https://portal.azure.com) で容量を購入できます。 このサブスクリプションは、*A* SKU を使用します。 Power BI Embedded 容量の作成方法の詳細については、「[Create Power BI Embedded capacity in the Azure portal](azure-pbie-create-capacity.md)」 (Azure Portal で Power BI Embedded 容量を作成する) をご覧ください。

    > [!NOTE]
    > A SKU の場合、無料 Power BI ライセンスでは Power BI コンテンツにアクセスできません。

### <a name="capacity-specifications"></a>容量仕様

次の表は、各 SKU のリソースと制限を示しています。 ニーズに最適な容量を判断するには、[シナリオに応じてどの SKU を購入すればよいか](./embedded-faq.md#which-solution-should-i-choose)をまとめた表を参照してください。

| 容量ノード | 合計 v コア数 | バックエンド v コア数 | RAM (GB) | フロントエンド v コア数 | DirectQuery/ライブ接続 (秒あたり) | モデル更新並列処理 |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0.5 | 2.5 | 0.5 | 3.75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7.5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| | | | | | | |

## <a name="development-testing"></a>開発テスト

開発テストでは、Pro ライセンスで埋め込み試用版トークンを使用できます。 運用環境に埋め込むには、容量を使用します。

Power BI "*サービス プリンシパル*" または "*マスター ユーザー*" (マスター アカウント) で生成できる埋め込み試用版トークンの数には制限があります。 [Available Features](/rest/api/power-bi/availablefeatures/getavailablefeatures) API を使用して、現在の埋め込みの使用率を確認します。 使用量は、サービス プリンシパルまたはマスター アカウントごとに表示されます。

テスト中に埋め込みトークンが不足した場合は、Power BI Embedded または Premium の[容量](embedded-capacity.md)を購入する必要があります。 容量で生成できる埋め込みトークンの数に制限はありません。

## <a name="assign-a-workspace-to-a-capacity"></a>容量にワークスペースを割り当てる

容量を作成した後、ワークスペースをその容量に割り当てることができます。

埋め込みコンテンツ (データセット、レポート、ダッシュボードを含む) に関連する Power BI リソースを含むすべてのワークスペースは、容量に割り当てられている必要があります。 たとえば、埋め込みレポートとそれにバインドされているデータセットが異なるワークスペースに存在する場合、両方のワークスペースを容量に割り当てる必要があります。

### <a name="assign-a-workspace-to-a-capacity-using-a-service-principal"></a>サービス プリンシパルを使用して容量にワークスペースを割り当てる

[サービス プリンシパル](embed-service-principal.md)を使用して容量をワークスペースに割り当てるには、[Power BI REST API](/rest/api/power-bi/capacities/groups_assigntocapacity) を使用します。 Power BI REST API の使用時は必ず[サービス プリンシパル オブジェクト ID](embed-service-principal.md) を使用してください。

### <a name="assign-a-workspace-to-a-capacity-using-a-master-user"></a>マスター ユーザーを使用して容量にワークスペースを割り当てる

以下の手順に従い、**マスター ユーザー** を使用してワークスペースに容量を割り当てます。

1. **Power BI サービス** でワークスペースを開き、次を選択します。 

1. **Power BI サービス** 内でワークスペースを展開し、コンテンツを埋め込むために使用しているワークスペースの省略記号ボタンを選択します。 次に、 **[Edit workspaces]\(ワークスペースの編集\)** を選択します。

    >[!div class="mx-imgBorder"]
    >:::image type="content" source="media/move-to-production/workspace-settings.png" alt-text="Power BI サービス ポータルの [ワークスペースの設定] メニューを示すスクリーンショット。":::

2. **[Premium]** タブを選択し、次の操作を行います。

    * **[容量]** を有効にします。

    * 作成した容量を選択します。

    * **[保存]** を選択します。

    >[!div class="mx-imgBorder"]
    >:::image type="content" source="media/move-to-production/premium-tab.png" alt-text="Power BI サービス ポータル内の [Premium] ワークスペースの設定メニューを示すスクリーンショット。":::

    容量にワークスペースを割り当てると、その横にひし形が表示されます。 

    >[!div class="mx-imgBorder"]
    >:::image type="content" source="media/move-to-production/premium-workspace.png" alt-text="Power BI サービス ポータル内の Premium 容量を持つワークスペースの横にあるひし形を示すスクリーンショット。":::

## <a name="next-steps"></a>次の手順

>[!div class="nextstepaction"]
>[Power BI Embedded の分析の容量と SKU](embedded-capacity.md)

>[!div class="nextstepaction"]
>[Power BI 埋め込み分析の容量計画](embedded-capacity-planning.md)

>[!div class="nextstepaction"]
>[埋め込みトークンを生成するときの考慮事項](generate-embed-token.md)