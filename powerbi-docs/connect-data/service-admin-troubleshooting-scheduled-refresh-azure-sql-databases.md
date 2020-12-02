---
title: Azure SQL Database のスケジュール設定された更新に関するトラブルシューティング
description: Power BI における Azure SQL Database のスケジュール設定された更新に関するトラブルシューティング
author: davidiseminger
ms.author: davidi
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: troubleshooting
ms.date: 09/04/2019
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: a9f69c8177766352d768d86903f15977ae0d8d1c
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410737"
---
# <a name="troubleshooting-scheduled-refresh-for-azure-sql-databases-in-power-bi"></a>Power BI における Azure SQL Database のスケジュール設定された更新に関するトラブルシューティング

更新の詳細については、「[Power BI でのデータの更新](refresh-data.md)」および「[スケジュールされた更新の構成](refresh-scheduled-refresh.md)」を参照してください。

Azure SQL データベースのスケジュール設定された更新を設定していて、資格情報の編集中にエラー コード 400 が発生した場合は、次の操作を試して適切なファイアウォール規則を設定します。

1. [Azure portal](https://portal.azure.com) にサインインする

1. 更新を構成している Azure SQL データベースにアクセスします。

1. **[概要]** ブレードの上部にある **[サーバー ファイアウォールの設定]** を選択します。

1. **[ファイアウォール設定]** ブレードで、 **[Azure サービスへのアクセスを許可]** が **[オン]** に設定されていることを確認します。

    ![Azure で使用できるサービス](media/service-admin-troubleshooting-scheduled-refresh-azure-sql-databases/azurerefresh.png)  

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。
