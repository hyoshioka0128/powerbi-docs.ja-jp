---
title: Azure Portal での Power BI Embedded 容量の一時停止と開始 | Microsoft Docs
description: この記事では、Microsoft Azure で Power BI Embedded の容量を一時停止する方法と開始する方法について説明します。
author: KesemSharabi
ms.author: kesharab
services: power-bi-embedded
editor: ''
tags: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 09/28/2017
ms.openlocfilehash: 71d3536cdcda5c1b2970385887388ea60b4290af
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96417315"
---
# <a name="pause-and-start-your-power-bi-embedded-capacity-in-the-azure-portal"></a>Azure Portal での Power BI Embedded 容量の一時停止と開始

この記事では、Microsoft Azure で Power BI Embedded の容量を一時停止する方法と開始する方法について説明します。 Power BI Embedded 容量を作成していることが前提となります。 作成していない場合、「[Azure Portal での Power BI Embedded 容量の作成](azure-pbie-create-capacity.md)」を参照して作成してください。

Azure サブスクリプションをお持ちでない場合は、始める前に[無料アカウントを作成](https://azure.microsoft.com/free/)してください。

## <a name="pause-your-capacity"></a>容量を一時停止する

容量を一時停止することで課金が止まります。 一定期間容量を使用する必要がない場合、容量を一時停止することをお勧めします。 容量は次の手順で一時停止します。

> [!NOTE]
> 容量を一時停止すると、Power BI 内でコンテンツが利用できなくなることがあります。 中断を防ぐ目的で、一時停止する前に容量からワークスペースの割り当てを解除してください。

1. [Azure Portal ](https://portal.azure.com/)にサインインします。

2. **[すべてのサービス]**  >  **[Power BI Embedded]** の順に選択すると、容量が表示されます。

    ![Azure Portal 内のすべてのサービス](media/azure-pbie-pause-start/azure-portal-more-services.png)

3. 一時停止する容量を選択します。

    ![Azure Portal 内の Power BI Embedded 容量リスト](media/azure-pbie-pause-start/azure-portal-capacity-list.png)

4. 容量の詳細内で **[一時停止]** を選択します。

    ![容量を一時停止する](media/azure-pbie-pause-start/azure-portal-pause-capacity.png)

5. **[はい]** を選択し、容量を一時停止することを確認します。

    ![一時停止を確定する](media/azure-pbie-pause-start/azure-portal-confirm-pause.png)

## <a name="start-your-capacity"></a>容量を開始する

容量を開始することで使用を再開します。 容量を開始すると、請求も再開されます。

1. [Azure Portal ](https://portal.azure.com/)にサインインします。

2. **[すべてのサービス]**  >  **[Power BI Embedded]** の順に選択すると、容量が表示されます。

    ![Azure Portal 内のすべてのサービス](media/azure-pbie-pause-start/azure-portal-more-services.png)

3. 開始する容量を選択します。

    ![Azure Portal 内の Power BI Embedded 容量リスト](media/azure-pbie-pause-start/azure-portal-capacity-list.png)

4. 容量の詳細内で **[開始]** を選択します。

    ![容量を開始する](media/azure-pbie-pause-start/azure-portal-start-capacity.png)

5. **[はい]** を選択し、容量を開始することを確認します。

    ![開始の確認](media/azure-pbie-pause-start/azure-portal-confirm-start.png)

この容量にコンテンツが割り当てられている場合、開始後、利用可能になります。

## <a name="next-steps"></a>次のステップ

容量を拡大または縮小する場合、[Power BI Embedded 容量のスケーリング](azure-pbie-scale-capacity.md)に関するページを参照してください。

自分のアプリケーションに Power BI コンテンツを埋め込む方法については、[Power BI ダッシュボード、レポート、タイルを埋め込む方法](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding-content/)に関するページを参照してください。

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。