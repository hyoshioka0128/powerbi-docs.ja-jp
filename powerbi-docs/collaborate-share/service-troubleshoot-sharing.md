---
title: ダッシュボードとレポートの共有に関するトラブルシューティング
description: 組織内の同僚や組織外のユーザーと Power BI のダッシュボードやレポートを共有する場合の問題を解決する方法。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: troubleshooting
ms.date: 06/23/2020
LocalizationGroup: Share your work
ms.openlocfilehash: 89d0ddbbcdd5caf47256fc85864590e55a1caa86
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96406667"
---
# <a name="troubleshoot-sharing-dashboards-and-reports"></a>ダッシュボードとレポートの共有に関するトラブルシューティング

ここでは、お客様がダッシュボードやレポートを共有している場合、または他のユーザーがお客様と共有している場合に発生する可能性のある一般的な問題をいくつか紹介します。 

## <a name="dashboard-recipients-see-a-lock-icon-in-a-tile"></a>ダッシュボードの受信者のタイルにロック アイコンが表示される

共有相手がレポートを表示しようとしたときに、ダッシュボードにロックされたタイルが表示されたり、"アクセス許可が必要です" というメッセージが表示されたりすることがあります。

![Power BI のロックされたタイル](media/service-share-dashboards/power-bi-locked_tile_small.png)

その場合は、基になるデータセットへのアクセス許可を共有相手に付与する必要があります。

1. コンテンツ リストの **[データセット]** タブに移動します。

1. データセットの横にある省略記号 ( **...** ) を選択してから、 **[アクセス許可の管理]** を選びます。

    ![アクセス許可の管理](media/service-share-dashboards/power-bi-sharing-manage-permissions.png)

1. **[ユーザーの追加]** を選びます。

    ![[ユーザーの追加] を選択](media/service-share-dashboards/power-bi-share-dataset-add-user.png)

1. 個々のユーザーの完全なメール アドレス、配布グループ、またはセキュリティ グループを入力します。 動的配布リストと共有することはできません。

    ![メール アドレスの追加](media/service-share-dashboards/power-bi-add-user-dataset.png)

1. **[追加]** を選択します。

## <a name="i-cant-share-a-dashboard-or-report"></a>ダッシュボードまたはレポートを共有できない

ダッシュボードまたはレポートを共有するには、基になるコンテンツ (つまり、関連するすべてのレポートやデータセット) を再共有するためのアクセス許可が必要です。 共有できないというメッセージが表示された場合は、レポートの作成者に、それらのレポートおよびデータセットを再共有するアクセス許可を依頼してください。

!["共有できません" メッセージ](media/service-share-dashboards/power-bi-sharing-unable-to-share.png)

## <a name="i-dont-have-access-to-a-dashboard-or-report"></a>ダッシュボードまたはレポートにアクセスできない

レポートまたはダッシュボードへのリンクを選択したときに "アクセス権の要求" メッセージが表示された場合、お客様はそれを表示するためのアクセス権を持っていません。 [アクセス権を要求する](service-request-access.md)必要があります。

## <a name="next-steps"></a>次の手順

- [Power BI ダッシュボードとレポートを仕事仲間や他のユーザーと共有する](service-share-dashboards.md)
- [ダッシュボードとレポートを共有する方法](service-how-to-collaborate-distribute-dashboards-reports.md)
-  [フィルター処理された Power BI レポートの共有](service-share-reports.md)
- わからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。
