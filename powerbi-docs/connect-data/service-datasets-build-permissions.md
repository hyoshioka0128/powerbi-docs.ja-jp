---
title: 共有データセットのビルド アクセス許可
description: ビルド アクセス許可を使用して、データに対するアクセスを制御する方法について学習します。
author: paulinbar
ms.author: painbar
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 02/12/2021
LocalizationGroup: Share your work
ms.openlocfilehash: b646237bddeaae8b73ef809504ab3aea2257c0e6
ms.sourcegitcommit: 00e3eb2ec4f18d48a73cfd020bb42d08e859ad06
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/16/2021
ms.locfileid: "100531472"
---
# <a name="build-permission-for-shared-datasets"></a>共有データセットのビルド アクセス許可

Power BI Desktop でレポートを作成する場合、そのレポート内のデータは "*データ モデル*" に格納されます。 Power BI サービスにレポートをパブリッシュすると、データを "*データセット*" としてもパブリッシュすることになります。 他のユーザーにそのレポートに対する "*ビルド アクセス許可*" を付与すると、共有したデータセットを検出して再利用できるようにすることができます。 この記事では、ビルド アクセス許可を使用して、データに対するアクセスを制御する方法について説明します。

ビルド アクセス許可はデータセットに適用されます。 ユーザーにビルド アクセス許可を付与すると、レポート、ダッシュボード、Q&A のピン留めされたタイル、ページ分割されたレポート、Insights Discovery などの新しいコンテンツをデータセット上に構築できます。 

また、Power BI "*外*" のデータを操作するには、ユーザーはビルド アクセス許可も必要になります。

- 基になるデータをエクスポートする
- [[Excel で分析]](../collaborate-share/service-analyze-in-excel.md) などを使用して、データセットに新しいコンテンツを構築する
- XMLA エンドポイント経由でデータにアクセスする

## <a name="ways-to-give-build-permission"></a>ビルド アクセス許可を付与する方法

データセットに対するビルド アクセス許可は、次のいくつかの方法で付与します。

- 少なくとも共同作成者ロールを持つワークスペースのメンバーには、そのワークスペースのデータセットに対するビルド アクセス許可と、レポートをコピーするアクセス許可が自動的に付与されます。 詳細については、「[新しいワークスペースのロール](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces)」を参照してください。
 
- データセットが存在するワークスペースのメンバーは、アクセス許可センターの特定のユーザーまたはセキュリティ グループにアクセス許可を割り当てることができます。 ワークスペースのメンバーの場合、データセットの横にある **その他のオプション** (...)、 **[アクセス許可の管理]** の順に選択します。

    ![省略記号を選択する](media/service-datasets-build-permissions/power-bi-dataset-permissions-new-look.png)

    これで、そのデータセットのアクセス許可センターが開き、そこでアクセス許可を設定および変更できます。

    ![アクセス許可センター](media/service-datasets-build-permissions/power-bi-dataset-remove-permissions-no-callouts.png)

- データセットが存在するワークスペースの管理者またはメンバーは、アプリの発行時に、そのアプリに対するアクセス許可を持つユーザーは、基となるデータセットに対するビルド アクセス許可も取得することを決定できます。 詳細については、[データセットの共有](service-datasets-share.md)に関するページを参照してください。

- たとえば、データセットに対して再共有およびビルドのアクセス許可を持っているとします。 そのデータセットに基づいて構築されたレポートまたはダッシュボードを共有するとき、受信者が、基となるデータセットのビルド アクセス許可を取得するように指定できます。

    ![ビルド アクセス許可](media/service-datasets-build-permissions/power-bi-share-report-allow-users.png)

データセットに対するユーザーのビルド アクセス許可を削除できます。 そうした場合、共有データセットに基づいて構築されたレポートを表示することはできますが、編集することはできなくなります。 詳細については、次のセクションを参照してください。

## <a name="remove-build-permission-for-a-dataset"></a>データセットに対するビルド アクセス許可の削除

ある時点で、共有データセットの一部のユーザーに対するビルド アクセス許可の削除が必要になることがあります。 

1. ワークスペースで、 **[データセット]** リスト ページに移動します。 
1. データセットの横にある **その他のオプション** (...)、 **[アクセス許可の管理]** の順に選択します。

    ![アクセス許可の管理](media/service-datasets-build-permissions/power-bi-dataset-permissions-new-look.png)

1. 名前の横にある **その他のオプション** (...) を選択し、 **[ビルドの削除]** を選択します。

    ![ビルド アクセス許可の削除](media/service-datasets-build-permissions/power-bi-dataset-remove-build-permissions.png)

    共有データセットに基づいて構築されたレポートを引き続き表示することはできますが、編集することはできなくなります。

### <a name="remove-build-permission-for-a-dataset-in-an-app"></a>アプリ内のデータセットに対するビルド アクセス許可の削除

たとえば、ワークスペースからユーザーのグループにアプリを配布したとします。 後で、一部のユーザーに対するアプリへのアクセス権を削除することにします。 アプリへのアクセス権を削除しても、そのビルドが自動的に削除されることはなく、アクセス許可は再共有されます。 これは追加の手順です。 

1. ワークスペースのリスト ページで、 **[アプリを更新]** を選択します。 

    ![アプリを更新](media/service-datasets-build-permissions/power-bi-app-update.png)

1. **[アクセス許可]** タブで、 **[X]** を選択して人またはグループを削除します。 

    ![[X] の選択](media/service-datasets-build-permissions/power-bi-app-delete-user.png)
1. **[アプリを更新]** を選択します。

    既存のアクセス権を持つユーザーに対するビルド アクセス許可を削除するために、 **[アクセス許可の管理]** にアクセスする必要があることを示すメッセージが表示されます。 

    ![アクセス許可の管理に関するメッセージ](media/service-datasets-build-permissions/power-bi-dataset-app-remove-message.png)

1. **[更新]** を選択します。

1. ワークスペースで、 **[データセット]** リスト ページに移動します。 
1. データセットの横にある **その他のオプション** (...)、 **[アクセス許可の管理]** の順に選択します。

    ![アクセス許可の管理](media/service-datasets-build-permissions/power-bi-dataset-permissions-new-look.png)

1. 名前の横にある **その他のオプション** (...) を選択し、 **[ビルドの削除]** を選択します。

    ![ビルド アクセス許可の削除](media/service-datasets-build-permissions/power-bi-dataset-remove-build-permissions.png)

    共有データセットに基づいて構築されたレポートを引き続き表示することはできますが、編集することはできなくなります。

## <a name="more-granular-permissions"></a>より詳細なアクセス許可

Power BI では、既存のアクセス許可である読み取りと再共有を補完するものとして、2019 年 6 月にビルド アクセス許可が導入されました。 その時点で、アプリのアクセス許可、共有、またはワークスペースのアクセスによるデータセットの読み取りアクセス許可を既に持っていたすべてのユーザーが、その同じデータセットのビルド アクセス許可も取得しました。 ビルド アクセス許可が自動的に付与された理由は、読み取りアクセス許可によって、Excel の [分析] または [エクスポート] を使用してデータセットに基づいて新しいコンテンツを構築する権限が既に付与されていたためです。

このより詳細なビルド アクセス許可を使用すると、既存のレポートまたはダッシュボードのコンテンツのみを表示できるユーザーと、基となるデータセットに接続されたコンテンツを作成できるユーザーを選択できます。

データセットがデータセット ワークスペース以外のレポートで使用されている場合、そのデータセットを削除することはできません。 代わりに、エラー メッセージが表示されます。

ビルド アクセス許可を削除できます。 この場合、アクセス許可を取り消したユーザーは、引き続きレポートを表示できますが、レポートを編集したり、基になるデータをエクスポートしたりすることはできなくなります。 読み取りアクセス許可のみを持つユーザーは、集計データを引き続きエクスポートできます。 

## <a name="next-steps"></a>次の手順

- [ワークスペースをまたいでデータセットを使用](service-datasets-across-workspaces.md)
- わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
