---
title: Microsoft 365 で Power BI サービスの正常性を追跡する
description: Microsoft 365 管理センターでサービスの現在および過去の正常性を表示する方法を説明します。
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 09/09/2019
LocalizationGroup: Administration
ms.openlocfilehash: 1aa873993cbc3384482f11086e775f41ddbe8917
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96408805"
---
# <a name="track-power-bi-service-health-in-microsoft-365"></a>Microsoft 365 で Power BI サービスの正常性を追跡する

Microsoft 365 管理センターでは、Power BI 管理者向けの重要なツールが提供されています。 そのツールには、サービスの正常性に関する最新の情報と履歴情報が含まれています。 サービス正常性情報にアクセスするには、次のどちらかのロールを割り当てられている必要があります。

* Power BI サービス管理者

* グローバル管理者

ロールについて詳しくは、「[Power BI に関連する管理者ロール](service-admin-administering-power-bi-in-your-organization.md#administrator-roles-related-to-power-bi)」をご覧ください。

1. [Microsoft 365 管理センター](https://portal.office.com/adminportal)にサインインします。

1. ナビ ペインで、 **[すべて表示]**  >  **[正常性]**  >  **[サービス正常性]** を選択します。 [サービス正常性] ページが表示されます。

    ![[正常性] と [サービス正常性] オプションが強調して示されている Microsoft 365 管理センターのスクリーンショット。](media/service-admin-health/service-health-tile.png)

1. **[すべてのサービス]** の一覧で、 **[アドバイザリ]** または **[インシデント]** を選択し、結果を確認します。 次のスクリーンショットでは、3 件のアクティブなアドバイザリのうちの 1 つが示されています。

    ![Power BI の 3 つのアドバイザリと [詳細の表示] オプションが強調して示されている [サービス正常性] ページのスクリーンショット。](media/service-admin-health/active-advisories.png)

1. 詳しい情報を見るには、項目の **[詳細の表示]** を選びます。 次のスクリーンショットでは、最新の状態の更新など、追加の詳細が表示されています。

    ![追加情報が表示されているアドバイザリの詳細のスクリーンショット。](media/service-admin-health/advisory-details.png)

    下にスクロールして他の情報を確認し、完了したらウィンドウを閉じます。

1. すべてのサービスの履歴情報を表示するには、 **[サービス正常性]** ページの右上隅で **[履歴の表示]** を選択します。 次に、 **[過去 7 日間]** または **[過去 30 日間]** を選びます。 

1. 現在のサービス正常性に戻るには、 **[現在の状態の表示]** を選びます。