---
title: ワークスペース全体でデータセットの使用を制御する - Power BI
description: Power BI テナント内の情報のフローを制限する方法について説明します。
author: maggiesMSFT
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 04/30/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 6cc602b96207b1662f0738c0936ca816bbfd0a03
ms.sourcegitcommit: 4e347efd132b48aaef6c21236c3a21e5fce285cc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2020
ms.locfileid: "92681075"
---
# <a name="control-the-use-of-datasets-across-workspaces"></a>ワークスペース全体でデータセットの使用を制御する

ワークスペース全体でデータセットを使用することは、組織内でデータのカルチャとデータの民主化を推進するための強力な方法です。 それでも、Power BI の管理者であれば、Power BI テナント内の情報のフローを制限することがあります。 テナント設定の **[ワークスペース全体でデータセットを使用する]** を使用すると、セキュリティ グループごとにデータセットの再利用を完全にまたは部分的に制限できます。

![Power BI 管理者ワークスペースの設定](media/service-datasets-admin-across-workspaces/power-bi-admin-workspace-settings.png)

この設定をオフにした場合、レポート作成者には次の影響があります。

- ワークスペース間でレポートをコピーするボタンを使用できません。 
- 共有データセットに基づくレポートでは、 **[レポートの編集]** ボタンを使用できません。
- Power BI サービスの検出エクスペリエンスでは、現在のワークスペースのデータセットのみが表示されます。
- Power BI Desktop の検出エクスペリエンスでは、自分がメンバーになっているワークスペースのデータセットのみが表示されます。
- Power BI Desktop で、ユーザーが自分がメンバーであるワークスペース以外のデータセットに対して、ライブ接続を使用して .pbix ファイルを開くと、別のデータセットに接続するように求めるエラー メッセージが表示されます。

## <a name="provide-a-link-for-the-certification-process"></a>認証プロセスのリンクを提供する

Power BI 管理者の場合、 **[承認]** 設定ページに **詳細情報** のリンクの URL を提供することができます。  詳細については、「[コンテンツの認定を有効にする](../admin/service-admin-setup-certification.md)」を参照してください。 このリンクで、認定プロセスについてのドキュメントに移動できます。 **詳細情報** のリンクの宛先を指定しない場合は、既定で「[コンテンツを承認する](../collaborate-share/service-endorse-content.md)」が示されます。

![データセットの認定の詳細情報](media/service-datasets-admin-across-workspaces/service-admin-certification-setup-dialog.png)

## <a name="next-steps"></a>次の手順

- [ワークスペースをまたいでデータセットを使用](service-datasets-across-workspaces.md)
- わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
