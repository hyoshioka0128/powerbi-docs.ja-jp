---
title: Power BI と Microsoft 365 でワークスペースを管理する
description: Power BI のワークスペースは、Microsoft 365 グループに基づいて構築されたコラボレーション エクスペリエンスです。 Power BI および Microsoft 365 でワークスペースを管理します。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukasz
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 04/02/2021
LocalizationGroup: Share your work
ms.openlocfilehash: 122543b11c2939ff124e130f139d98e49651d13c
ms.sourcegitcommit: a3b1ccdd18ef705de960625a9715ad5bbc21b1b6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2021
ms.locfileid: "106228970"
---
# <a name="manage-your-workspace-in-power-bi-and-microsoft-365"></a>Power BI と Microsoft 365 でワークスペースを管理する

Microsoft 365 または [Power BI でのワークスペース](service-create-distribute-apps.md)の作成者または管理者は、Power BI でワークスペースの一部の側面を管理します。 その他の側面は、Microsoft 365 で管理します。

> [!NOTE]
> 新しいワークスペース エクスペリエンスでは、Power BI ワークスペースと Microsoft 365 グループ間の関係が変わります。 新しいワークスペースのいずれかを作成するたびに、Microsoft 365 グループが自動的に作成されることはありません。 新しいワークスペースの作成については、[こちら](service-create-the-new-workspaces.md)を参照してください。

**Power BI** では、次のことができます。

* ワークスペース メンバーを追加または削除します (ワークスペース メンバーを管理者にすることもできます)。
* ワークスペース名を編集します。
* ワークスペースを削除します。これにより、Microsoft 365 グループも削除されます。

**Microsoft 365** では、次の操作を実行できます。

* ワークスペースのグループ メンバーを追加または削除します (メンバーを所有者にする操作も含まれます)。
* グループ名、画像、説明、およびその他の設定を編集します。
* グループの電子メール アドレスを参照します。
* グループを削除します。

ワークスペースの管理者またはメンバーになるには、[Power BI Pro または Premium Per User (PPU) のライセンス](../fundamentals/service-features-license-type.md)が必要です。 ワークスペースが Power BI Premium 容量にない場合は、アプリ ユーザーにも Power BI Pro または Premium Per User (PPU) のライセンスが必要です。 詳しくは、[Power BI Premium](../admin/service-premium-what-is.md) に関するページをご覧ください。

## <a name="edit-your-workspace-in-power-bi"></a>Power BI でワークスペースを編集する

1. Power BI サービスで、 **[ワークスペース]** の横にある矢印を選択し、目的のワークスペース名の横にある **その他のオプション** (...) を選択して、 **[このワークスペースを編集]** を選択します。

   ![[ワークスペース] が選択され、[詳細オプション] メニューから [このワークスペースを編集] が選択されている Power BI の [ホーム] を示すスクリーンショット。](media/service-manage-app-workspace-in-power-bi-and-office-365/power-bi-app-ellipsis.png)

   > [!NOTE]
   > ワークスペース管理者の場合は、 **[このワークスペースを編集]** のみが表示されます。

1. ここでは、ワークスペースの名前の変更、メンバーの追加または削除、またはワークスペースの削除を行うことができます。

   ![[ワークスペースの編集] ダイアログ ボックス](media/service-manage-app-workspace-in-power-bi-and-office-365/power-bi-app-edit-workspace.png)

1. **[保存]** または **[キャンセル]** を選びます。

## <a name="edit-power-bi-workspace-properties-in-microsoft-365"></a>Microsoft 365 で Power BI ワークスペースのプロパティを編集する

Microsoft 365 の Outlook でワークスペースの側面を直接編集することもできます。

### <a name="edit-the-members-of-the-workspace-group"></a>ワークスペース グループのメンバーを編集する

1. Power BI サービスで、 **[ワークスペース]** の横にある矢印を選択し、目的のワークスペース名の横にある **その他のオプション** (...) を選択して、 **[メンバー]** を選択します。

   ![[ワークスペース] が選択され、[詳細オプション] メニューから [メンバー] が選択されている Power BI の [ホーム] を示すスクリーンショット。](media/service-manage-app-workspace-in-power-bi-and-office-365/power-bi-app-ellipsis-members.png)

   これにより、Microsoft 365 の Outlook でワークスペースのグループ ビューが開きます。 会社のアカウントにサインインする必要があります。

1. チームメイト名の横にあるロールを選択して、その人を **メンバー** または **所有者** にします。 **[X]** を選択して、グループからその人を削除します。

   ![Microsoft 365 でのグループの編集](media/service-manage-app-workspace-in-power-bi-and-office-365/pbi_managegroupo365.png)

### <a name="add-an-image-and-set-other-workspace-properties"></a>イメージを追加してその他のワークスペースのプロパティを設定する

ワークスペースからアプリを配布するときに、ここで追加したイメージがアプリのイメージになります。 **新しいワークスペースの作成** に関する記事の [Microsoft 365 ワークスペースへの画像の追加](service-create-workspaces.md#add-an-image-to-your-microsoft-365-workspace-optional)に関するセクションをご覧ください。

1. Microsoft 365 の Outlook のワークスペース ビューで、 **[バージョン情報]** タブにアクセスし、 **[編集]** を選択します。

    ![[グループの編集] アイコン](media/service-manage-app-workspace-in-power-bi-and-office-365/pbi_editgroupo365.png)
1. グループ関連の通知の名前、説明、および言語を編集できます。 ここでは、画像を追加したり、その他のプロパティを設定することもできます。

   ![[グループの編集] ダイアログ ボックス](media/service-manage-app-workspace-in-power-bi-and-office-365/pbi_editgrpo365dialog.png)

1. **[保存]** または **[破棄]** を選択します。

## <a name="next-steps"></a>次の手順

* [Power BI でアプリを発行する](service-create-distribute-apps.md)

* 他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。
