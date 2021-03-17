---
title: 同僚の Power BI ホーム ページでコンテンツをおすすめに登録する
description: 組織内の同僚の Power BI ホーム ページで Power BI ダッシュボードとレポートをおすすめに登録する方法。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: nikhilga
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 02/10/2021
LocalizationGroup: Share your work
ms.openlocfilehash: 68c899ad24ad32783813340edaea090835ec19a5
ms.sourcegitcommit: 13a150d1aa810f309421bf603fa8581718a4b299
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "101843655"
---
# <a name="feature-content-on-colleagues-power-bi-home-page"></a>同僚の Power BI ホーム ページでコンテンツをおすすめに登録する

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)]

ダッシュボード、レポート、アプリをおすすめに登録し、同僚の Power BI ホーム ページの [おすすめ] セクションに表示させることができます。 コンテンツをおすすめに登録することは、新しい従業員を Power BI にオンボードする場合に特に役立ちます。 最初に表示されるコンテンツを決定します。 説明と小さいサムネイル画像を追加すると、ユーザーが目的のコンテンツを見つけやすくなります。 コンテンツは、新しいワークスペース内に存在している必要があります。

:::image type="content" source="media/service-featured-content/power-bi-featured-home.png" alt-text="ホーム上の Power BI おすすめコンテンツ":::

## <a name="who-can-feature-content"></a>コンテンツをおすすめに登録することができるユーザー

ダッシュボードとレポートをおすすめに登録するには、ワークスペース内での管理者ロール、メンバー ロール、または共同作成者ロールを持っている必要があります。 アプリ自体をおすすめに登録するには、ワークスペース内での管理者ロールまたはメンバー ロールを持っている必要があります。 詳細については、「[新しいワークスペースのロール](service-new-workspaces.md#roles-in-the-new-workspaces)」を参照してください。 Power BI Pro ライセンスを持っている必要があります。 

Power BI 管理者は、テナントのコンテンツをおすすめに登録する機能を無効にしたり、コンテンツをおすすめに登録できるユーザーを選択することができます。 詳細については、[管理ポータル](../admin/service-admin-portal.md#featured-content)に関する記事を参照してください。

## <a name="who-sees-featured-content"></a>おすすめに登録したコンテンツを見ることができるユーザー

ワークスペースからダッシュボードまたはレポートをおすすめに登録する場合、そのワークスペース内でのビューアー ロールを少なくとも持つユーザーに、それがおすすめとして表示されます。 アプリからダッシュボードまたはレポートを、またはアプリ自体をおすすめに登録することもできます。 その場合、アプリの配布先にそれがおすすめとして表示されます。

## <a name="feature-a-dashboard-or-report"></a>ダッシュボードまたはレポートをおすすめに登録する

ダッシュボードまたはレポートをおすすめに登録する手順は似ています。

1. ワークスペースの **[すべて]** または **[コンテンツ]** の一覧で、 **[その他のオプション (...)]**  >  **[設定]** を選択します。

    :::image type="content" source="media/service-featured-content/power-bi-settings-icon.png" alt-text="レポートの設定アイコン":::

2. **[設定]** ペインで、名前を確認または変更します。 必要に応じて、**説明** を追加し、**スナップショット** をアップロードします。 これらは、ユーザーがコンテンツを見つける際に役立つため、便利です。

3. **[ホームのおすすめ]** を選択します。

    :::image type="content" source="media/service-featured-content/power-bi-featured-content-settings.png" alt-text="おすすめコンテンツの設定":::

4. **[保存]** を選択します。

    これで、このダッシュボードまたはレポートへのアクセス権を持つすべてのユーザーが、 **[ホーム]** の **[おすすめ]** セクションで見ることができるようになります。

## <a name="feature-an-app"></a>アプリをおすすめに登録する

- アプリをおすすめに登録するには、アプリのワークスペースを開き、 **[オプション]** メニュー ( **...** ) > **[このアプリをホームでおすすめに登録する]** の順に選択します。

    :::image type="content" source="media/service-featured-content/power-bi-feature-app-home.png" alt-text="[このアプリをホームのおすすめに表示する] のスクリーンショット。":::

これで、このアプリへのアクセス権を持つ誰もが、 **[ホーム]** の **[おすすめ]** セクションでやはり見ることができるようになります。

## <a name="considerations"></a>考慮事項

アプリまたはレポートを昇格させて承認すると、 **[ホームのおすすめ]** チェックボックスが自動的にオンになります。 **[ホームのおすすめ]** は、いつでもオフにすることができます。 オフにした場合、承認を変更しても **[ホームのおすすめ]** は再度オンにはなりません。 詳細については、「[コンテンツを承認する](service-endorse-content.md#promote-content)」を参照してください。 

## <a name="next-steps"></a>次の手順

* [ダッシュボードとレポートを共有する方法](../collaborate-share/service-how-to-collaborate-distribute-dashboards-reports.md)
* [管理ポータルでおすすめコンテンツを管理する](../admin/service-admin-portal.md#manage-featured-content)
* わからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。
