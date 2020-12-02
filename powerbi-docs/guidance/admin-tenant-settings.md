---
title: テナント設定のガイダンス
description: Power BI のテナント設定に関するガイダンス。
author: paulinbar
ms.author: painbar
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/10/2020
ms.openlocfilehash: 66d721670f90efb17f6167aba3c074bdf6ea0ae1
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96394867"
---
# <a name="tenant-settings-guidance"></a>テナント設定のガイダンス

この記事は、組織内の Power BI 環境の設定と構成を担当する Power BI 管理者を対象としています。

Power BI エクスペリエンスの向上に役立つ特定のテナント設定に関するガイダンスを提供しますが、組織が危険にさらされる可能性もあります。 テナントは、常に組織のポリシーとプロセスに合わせて構成することをお勧めします。

[テナント設定](../admin/service-admin-portal.md#tenant-settings)は[管理ポータル](https://app.powerbi.com/admin-portal/tenantSettings)で管理され、[Power BI サービス管理者](../admin/service-admin-administering-power-bi-in-your-organization.md#administrator-roles-related-to-power-bi)によって構成できます。 多くのテナント設定では、限られたユーザーに機能を制限できます。 そのため、まず、必要なセキュリティ グループを計画するための設定について理解しておくことをお勧めします。 同じセキュリティ グループを複数の設定に適用できることがわかるでしょう。

## <a name="improve-power-bi-experience"></a>Power BI のエクスペリエンスを向上させる

### <a name="publish-get-help-information"></a>[ヘルプを表示] の情報を公開する

[Microsoft Teams](/microsoftteams)、またはその他のコラボレーション プラットフォームを使用して、内部の Power BI 関連サイトを設定することをお勧めします。 これらのサイトを使用して、トレーニング ドキュメントの保存、ディスカッションのホスト、ライセンス要求の作成、ヘルプへの応答を行うことができます。

これを行う場合は、"_組織全体で_" **["ヘルプの取得" に関する情報の発行]** 設定を有効にすることをお勧めします。 これは、 **[ヘルプとサポートの設定]** にあります。 次のものに URL を設定することができます。

- トレーニング ドキュメント
- ディスカッション フォーラム
- ライセンスの要求
- ヘルプ デスク

これらの URL は、Power BI のヘルプ メニューのリンクとして使用できるようになります。

> [!NOTE]
> **ライセンス要求** URL を指定することで、個々のユーザーは Power BI Pro ライセンスを購入できなくなります。 代わりに、ライセンスの取得方法についての情報が含まれた内部サイトにリダイレクトされます。 **[Allow users to try Power BI Pro]\(ユーザーが Power BI Pro を試せるようにする\)** 設定が既定で有効になっており、購入と試用を分離します。 これらの設定が連動するしくみについては、「[ユーザーが Power BI Pro を試せるようにする](../admin/service-admin-portal.md#allow-users-to-try-power-bi-pro)」を参照してください。
>
>

![[ヘルプとサポートの設定] を表示している Power BI Desktop のスクリーンショット。](media/admin-tenant-settings/publish-get-help-information.png)

詳細については、「[ヘルプとサポートの設定](../admin/service-admin-portal.md#help-and-support-settings)」を参照してください。

## <a name="manage-risk"></a>リスクの管理
リスクを管理するための設定は、Power BI テナントのガバナンス ポリシーを確立に役立ちます。 ただし、ガバナンス設定はセキュリティ対策ではないことにご留意ください。 たとえば、 **[データのエクスポート]** 設定を無効にすると、Power BI ユーザー インターフェイスからこの機能が削除され、組織のガバナンス ポリシーに沿って仕事をする Power BI ユーザーを支援しますが、他の選択肢を利用してデータをエクスポートすることにしたユーザーを止めるものではありません。 セキュリティの観点からは、データセットに読み取りアクセスできる Power BI ユーザーにはこのデータセットを照会するアクセス許可が与えられ、Power BI ユーザー インターフェイスに利用できる機能に関係なく、結果を保持できます。
### <a name="receive-email-notification-service-outages-or-incidents"></a>サービスの停止またはインシデントに関するメール通知を受け取る

ご利用のテナントがサービスの停止やインシデントの影響を受けた場合に、電子メールで通知を受け取ることができます。 こうすることで、インシデントに事前に対応できます。

**[Receive email notification service outages or incidents]\(サービスの停止またはインシデントに関するメール通知を受け取る\)** 設定を有効にすることをお勧めします。 これは、 **[ヘルプとサポートの設定]** にあります。 "_メールが有効な_" セキュリティ グループを 1 つ以上割り当てます。

![[サービスの停止またはインシデントに関するメール通知を受け取る] 設定を表示している Power BI Desktop のスクリーンショット。](media/admin-tenant-settings/receive-email-notifications-for-service-outages-or-incidents.png)

### <a name="information-protection"></a>情報の保護

Information Protection では、Power BI サービスからデータをエクスポートするときに、暗号化や透かしなどの保護設定を適用できます。

Information Protection に関連するテナント設定は 2 つあります。 既定では、両方の設定が組織全体で無効になっています。

機密データを処理して保護する必要がある場合は、これらの設定を有効にすることをお勧めします。 詳細については、「[Power BI におけるデータ保護](../admin/service-security-data-protection-overview.md)」を参照してください。

### <a name="create-workspaces"></a>ワークスペースを作成する

ユーザーによるワークスペースの作成を制限することができます。 これにより、組織内で作成された内容を管理できます。

> [!NOTE]
> 現在、古いワークスペース エクスペリエンスと新しいワークスペース エクスペリエンスの間に移行期間があります。 このテナント設定は、新しいエクスペリエンスにのみ適用されます。

既定では、組織全体に対して **[ワークスペースの作成]** 設定が有効になっています。 これは、 **[ワークスペースの設定]** にあります。

1 つまたは複数のセキュリティ グループを割り当てることをお勧めします。 これらのグループに、ワークスペースを作成するための権限を付与する、"_または拒否する_" ことができます。

ユーザー (ワークスペースの作成権限を持っていないユーザー) に新しいワークスペースを要求する手順をドキュメントに記載してお知らせください。

![[ワークスペースの作成] 設定を表示している Power BI Desktop のスクリーンショット。](media/admin-tenant-settings/create-workspaces.png)

### <a name="share-content-with-external-users"></a>外部ユーザーとコンテンツを共有する

ユーザーは、組織外のユーザーとレポートやダッシュボードを共有できます。

既定では、組織全体に対して **[外部ユーザーとコンテンツを共有する]** 設定が有効になっています。 これは、 **[エクスポートと共有の設定]** にあります。

1 つまたは複数のセキュリティ グループを割り当てることをお勧めします。 これらのグループに、外部ユーザーとコンテンツを共有するための権限を付与する、"_または拒否する_" ことができます。

![[外部ユーザーとコンテンツを共有する] 設定を表示している Power BI Desktop のスクリーンショット。](media/admin-tenant-settings/share-content-with-external-users.png)

### <a name="publish-to-web"></a>Web に公開

[[Web に公開]](../collaborate-share/service-publish-to-web.md) 機能を使用すると、Web 上でパブリック レポートを公開できます。 不適切に使用した場合、機密情報が Web 上で公開される危険性があります。

既定では、 **[Web に公開]** 設定が組織全体で有効になっていますが、管理者ユーザー以外が埋め込みコードを作成する機能は制限されています。 これは、 **[エクスポートと共有の設定]** にあります。

有効になっている場合、1 つまたは複数のセキュリティ グループを割り当てることをお勧めします。 これらのグループに、レポートを公開するための権限を付与する、"_または拒否する_" ことができます。

さらに、埋め込みコードの動作を選択するオプションもあります。 既定では、 **[既存のコードのみを許可する]** に設定されています。 これは、ユーザーが埋め込みコードを作成するには Power BI 管理者に連絡しなければならないことを意味します。

![[Web に公開] 設定を表示している Power BI Desktop のスクリーンショット。](media/admin-tenant-settings/publish-to-web.png)

定期的に [[Web に公開] の埋め込みコード](https://app.powerbi.com/admin-portal/embedCodes)を確認することもお勧めします。 個人情報や機密情報が公開される場合は、コードを削除します。

### <a name="export-data"></a>データのエクスポート

ユーザーがダッシュボード タイルまたはレポート ビジュアルからデータをエクスポートできないように制限することができます。

既定では、組織全体に対して **[データのエクスポート]** 設定が有効になっています。 これは、 **[エクスポートと共有の設定]** にあります。

1 つまたは複数のセキュリティ グループを割り当てることをお勧めします。 これらのグループに、レポートを公開するための権限を付与する、"_または拒否する_" ことができます。

> [!IMPORTANT]
> この設定を無効にすると、[[Excel で分析]](../collaborate-share/service-analyze-in-excel.md) および Power BI サービスの[ライブ接続](../connect-data/desktop-report-lifecycle-datasets.md#using-a-power-bi-service-live-connection-for-report-lifecycle-management)機能の使用も制限されます。

![[データのエクスポート] 設定を表示している Power BI Desktop のスクリーンショット。](media/admin-tenant-settings/export-data.png)

> [!NOTE]
> ユーザーがデータをエクスポートできるようにする場合は、[データ保護](../admin/service-security-data-protection-overview.md)を適用することにより、保護レイヤーを追加できます。 構成すると、承認されていないユーザーは、機密ラベルを含むコンテンツをエクスポートできなくなります。

### <a name="allow-external-guest-users-to-edit-and-manage-content-in-the-organization"></a>外部のゲスト ユーザーによる組織内のコンテンツの編集および管理を許可する

外部のゲスト ユーザーが Power BI コンテンツを編集および管理することができます。 詳細については、「[Azure AD B2B で外部ゲスト ユーザーに Power BI コンテンツを配布する](../admin/service-admin-azure-ad-b2b.md)」を参照してください。

既定では、組織全体に対して **[外部のゲスト ユーザーによる組織内のコンテンツの編集および管理を許可する]** 設定が無効になっています。 これは、 **[エクスポートと共有の設定]** にあります。

外部ユーザーによるコンテンツの編集と管理を承認する必要がある場合は、1 つまたは複数のセキュリティ グループを割り当てることをお勧めします。 これらのグループに、レポートを公開するための権限を付与する、"_または拒否する_" ことができます。

![[外部のゲスト ユーザーによる組織内のコンテンツの編集および管理を許可する] 設定を表示している Power BI Desktop のスクリーンショット。](media/admin-tenant-settings/allow-external-guest-users.png)

### <a name="developer-settings"></a>開発者の設定

[Power BI コンテンツの埋め込み](../developer/embedded/embedding.md)に関連するテナント設定は 2 つあります。 これらは次のとおりです。

- アプリにコンテンツを埋め込む (既定で有効)
- Power BI API の使用をサービス プリンシパルに許可 (既定で無効)

開発者用 API を使用してコンテンツを埋め込む予定がない場合は、これらを無効にすることをお勧めします。 または、この作業を実行する特定のセキュリティ グループのみを構成します。

![[開発者の設定] を表示している Power BI Desktop のスクリーンショット。](media/admin-tenant-settings/developer-settings.png)

## <a name="next-steps"></a>次の手順

この記事に関する詳細については、次のリソースを参照してください。

- [Power BI 管理とは](../admin/service-admin-administering-power-bi-in-your-organization.md)
- [管理ポータルでの Power BI の管理](../admin/service-admin-portal.md)
- わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
- Power BI チームへのご提案は、 [Power BI を改善するためのアイデアをお寄せください](https://ideas.powerbi.com)