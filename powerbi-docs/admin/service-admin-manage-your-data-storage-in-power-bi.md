---
title: ワークスペースでデータ ストレージを管理する
description: レポートおよびデータセットを引き続き確実に発行できるように、個々のユーザーまたはワークスペース内のデータ記憶域を管理する方法について説明します。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 04/02/2021
LocalizationGroup: Administration
ms.openlocfilehash: 6a25cf9eb515bb4a2dacb615cb40cd758192a935
ms.sourcegitcommit: a3b1ccdd18ef705de960625a9715ad5bbc21b1b6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2021
ms.locfileid: "106227148"
---
# <a name="manage-data-storage-in-power-bi-workspaces"></a>Power BI ワークスペースでデータ ストレージを管理する

レポートやデータセットを発行し続けることができるように、個人またはワークスペースのデータ ストレージを管理する方法について説明します。

## <a name="capacity-limits"></a>容量制限

ワークスペースのストレージ制限は、マイ ワークスペースでもアプリのワークスペースでも、ワークスペースが[共有容量と Premium 容量](../fundamentals/service-basic-concepts.md#capacities)のどちらにあるかに依存します。

### <a name="shared-capacity-limits"></a>共有容量の制限
共有された容量のワークスペース 

- ワークスペースごとに 10 GB のストレージ制限があります。
- アプリ ワークスペースの場合、合計使用量は、テナントのストレージ上限 10 GB にテナント内の Pro または Premium Per User (PPU) のライセンスの数を掛けた値を超えることができません。

### <a name="premium-capacity-limits"></a>Premium 容量の制限
Premium 容量のワークスペースの場合:
- Premium 容量あたり 100 TB の制限があります。
- ユーザーごとの記憶域の制限はありません。
- ワークスペースが Premium 容量に割り当てられている場合、そのワークスペース ストレージの使用量は (次のスクリーンショットのように) 0 として示されます。 

  ![Premium 容量でのワークスペース ストレージの使用量](media/service-admin-manage-your-data-storage-in-power-bi/workspace-storage-usage-premium.png)


「[Power BI 料金モデル](https://powerbi.microsoft.com/pricing)」のその他の特徴もご覧ください。

## <a name="whats-included-in-storage"></a>ストレージに含まれるもの

データ記憶域には、ユーザー個人のデータセットと Excel レポートに加えて、他のユーザーと共有したデータセットと Excel レポートも含まれます。 データセットとは、アップロードまたは接続しているデータ ソースのことです。 使用中の Power BI Desktop ファイルや Excel ブックも含まれます。 データ容量には以下も含まれます。

* ダッシュボードにピン留めされた Excel の範囲。
* Power BI ダッシュボードにピン留めされた Reporting Services オンプレミス ビジュアル効果。
* アップロードされたイメージ。

共有ダッシュボードのサイズは、ピン留めされている項目に応じて異なります。 たとえば、2 つの異なるデータセットの一部である 2 つのレポートから項目をピン留めした場合は、2 つのデータセットがサイズに含まれます。

## <a name="manage-items-you-own"></a>自分が所有する項目を管理する

Power BI アカウントで使用しているデータ記憶域を確認して、アカウントを管理します。

1. 自分の記憶域を管理するには、ナビゲーション ペインの **[マイ ワークスペース]** に移動します。
   
    ![[マイワークスペース] が強調表示されているナビゲーション ペインのスクリーンショット。](media/service-admin-manage-your-data-storage-in-power-bi/pbi_myworkspace.png)

2. 右上隅にある![歯車アイコン](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png)、 **[個人の記憶域の管理]** の順に選択します。
   
    上部のバーに、記憶域の上限のうちの使用量が表示されます。
   
    ![記憶域の使用量が示されている、記憶域の上限を管理するスクリーンショット。](media/service-admin-manage-your-data-storage-in-power-bi/pbi_persnlstorage.png)
   
    データセットとレポートは、2 つのタブに分かれています。
   
    **自分の所有** 自分の Power BI アカウントに、Salesforce や Dynamics CRM などのサービス データセットを含む、これらのレポートやデータセットをアップロードしています。  

    **他のユーザーの所有:** 他のユーザーから共有を受けたレポートやデータセットです。
1. データセットやレポートを削除するには、ごみ箱のアイコン ![ごみ箱のアイコン](media/service-admin-manage-your-data-storage-in-power-bi/pbi_deleteicon.png).

データセットが、自分や他のユーザーが作成したレポートやダッシュボードの基になっている可能性があることにご注意ください。 そのデータセットを削除してしまうと、これらのレポートやダッシュボードは機能しなくなります。

## <a name="manage-your-workspace"></a>自分のワークスペースを管理する
1. **[ワークスペース]** の横にある矢印、ワークスペースの名前の順に選択します。
   
    ![Sales グループ ワークスペースを表示しているワークスペースの選択のスクリーンショット。](media/service-admin-manage-your-data-storage-in-power-bi/pbi_groupworkspaces.png)
2. 右上隅にある![歯車アイコン](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png)、 **[グループの記憶域の管理]** の順に選択します。
   
    上部のバーに、グループの記憶域の上限のうちの使用量が表示されます。
   
    ![Sales グループの記憶域の上限のうちの使用量が示されている、記憶域の管理のスクリーンショット。](media/service-admin-manage-your-data-storage-in-power-bi/pbi_groupstorage.png)
   
    データセットとレポートは、2 つのタブに分かれています。
   
    **わたしたちの所有:** 自分か他の誰かがグループの Power BI アカウントに、Salesforce や Dynamics CRM などのサービス データセットを含む、これらのレポートやデータセットをアップロードしています。

    **他のユーザーの所有:** 他のユーザーから自分のグループが共有を受けたレポートやデータセットです。

3. データセットやレポートを削除するには、ごみ箱のアイコン ![ごみ箱のアイコン](media/service-admin-manage-your-data-storage-in-power-bi/pbi_deleteicon.png).
   
   > [!NOTE]
   > データセットが、自分かグループ内の他のユーザーが作成したレポートやダッシュボードの基になっている可能性があることにご注意ください。 そのデータセットを削除してしまうと、これらのレポートやダッシュボードは機能しなくなります。
   
   管理者、メンバー、または共同作成者のいずれかのロールを持つワークスペースのメンバーは、ワークスペースからデータセットとレポートを削除するアクセス許可を持っています。

## <a name="dataset-limits"></a>データセットの制限
Power BI にインポートされるデータセットごとに 1 GB の制限があります。 データをインポートするのではなく、Excel でのエクスペリエンスを維持することを選択した場合、データセットは 250 MB に制限されます。

## <a name="what-happens-when-you-reach-a-limit"></a>上限に達したときの動作
利用できるデータ容量の上限に達すると、サービス内にメッセージが表示されます。 

歯車アイコン ![歯車アイコン](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png)を選択すると、データ容量の上限を超えていることを示す赤いバーが表示されます。

![上限に達したことを示すストレージ容量のスクリーンショット。](media/service-admin-manage-your-data-storage-in-power-bi/manage-storage-limit.png)

この上限は、 **[パーソナル ストレージの管理]** 内でも表示されます。

 ![Jane が上限に達したことを示すパーソナル ストレージ容量のスクリーンショット。](media/service-admin-manage-your-data-storage-in-power-bi/manage-storage-limit2.png)

 データ容量の上限を超えるアクションを実行しようとすると、上限を超えることを示すメッセージが表示されます。 [自分の記憶域を管理](#manage-items-you-own)し、記憶域の量を減らしたり、上限を超えたりできます。

 ![制限に達したことを示す [ストレージの上限を超えています] ダイアログのスクリーンショット。](media/service-admin-manage-your-data-storage-in-power-bi/powerbi-pro-over-limit.png)

 ## <a name="next-steps"></a>次の手順

 他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
