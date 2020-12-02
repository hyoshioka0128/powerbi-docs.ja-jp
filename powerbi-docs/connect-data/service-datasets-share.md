---
title: データセットを共有する
description: データセットの所有者として、データセットを作成し、他のユーザーが使用できるように共有することができます。 共有方法について説明します。
author: paulinbar
ms.author: painbar
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 04/30/2020
LocalizationGroup: Share your work
ms.openlocfilehash: c73c5b1b803b73742f6f13456b07a2060f5757e4
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410415"
---
# <a name="share-a-dataset"></a>データセットを共有する

Power BI Desktop の "*データ モデル*" の作成者であれば、Power BI サービスで配布できる "*データセット*" を作成します。 そのデータセットは、他のレポート作成者が自分のレポートの基礎として使用できます。 この記事では、データセットを共有する方法について説明します。 共有データセットへのアクセス権を付与したり、削除したりする方法については、「[データセットを共有する (プレビュー)](service-datasets-build-permissions.md)」を参照してください。

## <a name="steps-to-sharing-your-dataset"></a>データセットを共有する手順

1. まず、Power BI Desktop でデータ モデルを使用して .pbix ファイルを作成します。 他のユーザーがレポートを作成できるようにこのデータセットを提供する予定の場合、.pbix ファイルではレポートをデザインすることもできない可能性があります。

    ベスト プラクティスは、.pbix ファイルを Microsoft 365 グループに保存することです。

1. Power BI サービスの[新しいワークスペース エクスペリエンス](../collaborate-share/service-create-the-new-workspaces.md)に .pbix ファイルを発行します。
    
    既に、このワークスペースの他のメンバーは、このデータセットに基づいて他のワークスペースにレポートを作成できます。 ワークスペース コンテンツの一覧のデータセットで [権限の管理] オプションを使用すると、データセットへのアクセス権限が追加のユーザーに与えられます。 

1. このワークスペースから[アプリを発行](../collaborate-share/service-create-distribute-apps.md)することもできます。 このとき、 **[アクセス許可]** ページで、アクセス許可を持つユーザーと、実行できる内容を指定します。

    > [!NOTE]
    > **[組織全体]** を選択した場合、組織内の誰もビルド アクセス許可を持たなくなります。 これは既知の問題です。 代わりに、 **[特定の個人またはグループ]** にメール アドレスを指定します。  組織全体にビルド アクセス許可を持たせる場合は、組織全体のメール エイリアスを指定します。

    ![アプリのアクセス許可を設定する](media/service-datasets-build-permissions/power-bi-dataset-app-permission-new-look.png)

1. **[アプリの発行]** 、または既に発行されている場合は **[アプリの更新]** を選択します。

## <a name="track-your-dataset-usage"></a>データセットの使用状況を追跡する

ワークスペースに共有データセットがある場合、必要に応じて他のワークスペースのどのレポートがそれに基づいているかを確認できます。

1. [データセット] リスト ビューで、 **[関連の表示]** を選択します。

    ![[関連の表示] アイコン](media/service-datasets-build-permissions/power-bi-dataset-view-related-to-dataset.png)

1. **[関連コンテンツ]** ダイアログ ボックスには、すべての関連項目が表示されます。 このリストには、このワークスペースと **[その他のワークスペース]** の関連項目が表示されます。
 
    ![[関連コンテンツ] ダイアログ ボックス](media/service-datasets-build-permissions/power-bi-dataset-related-workspaces.png)

## <a name="limitations-and-considerations"></a>制限事項と考慮事項
データセットの共有について留意すべき事項:

* アクセス許可の管理、レポートまたはダッシュボードの共有、またはアプリの発行でデータセットを共有する場合、[行レベルのセキュリティ (RLS)](../admin/service-admin-rls.md) によってアクセスが制限されない限り、データセット全体へのアクセスが付与されます。 レポートの作成者は、列を非表示にする、ビジュアル上のアクションを制限するなど、レポートを表示したり、操作したりするときのユーザー エクスペリエンスをカスタマイズする機能を使用できます。 そのようなカスタマイズされたユーザー エクスペリエンスによって、データ ユーザーがデータセットでアクセスできる対象が制限されることはありません。 個人の資格情報によってアクセスできるデータが決定されるよう、データセットの[行レベルセキュリティ (RLS)](../admin/service-admin-rls.md) を使用します。

## <a name="next-steps"></a>次の手順

- [ワークスペースをまたいでデータセットを使用](service-datasets-across-workspaces.md)
- わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
