---
title: Power BI 用の Azure セキュリティ ベースライン
description: Power BI セキュリティ ベースラインでは、Azure セキュリティ ベンチマークで指定されているセキュリティに関する推奨事項を実装するための手順を記載したガイダンスおよびリソースを提供しています。
author: mbaldwin
ms.author: margoc
ms.service: powerbi
ms.subservice: pbi-security
ms.topic: conceptual
ms.date: 11/20/2020
ms.custom: subject-security-benchmark
ms.openlocfilehash: ef74b3bcddd981c9f63172fa2e641335a081836d
ms.sourcegitcommit: cb6e0202de27f29dd622e47b305c15f952c5769b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2020
ms.locfileid: "96577718"
---
# <a name="azure-security-baseline-for-power-bi"></a>Power BI 用の Azure セキュリティ ベースライン

このセキュリティ ベースラインでは、[Azure セキュリティ ベンチマーク バージョン 2.0](https://docs.microsoft.com/azure/security/benchmarks/overview) からのガイダンスを Power BI に適用します。 Azure セキュリティ ベンチマークには、Azure 上のクラウド ソリューションをセキュリティで保護する方法に関する推奨事項がまとめてあります。 Azure セキュリティ ベンチマークで定義されている **セキュリティ制御** および Power BI に適用できる関連のガイダンスによって、内容をグループ化しています。 Power BI に適用できない **制御** については除外しています。

Power BI を Azure セキュリティ ベンチマークに完全にマップする方法については、[完全な Power BI のセキュリティ ベースライン マッピング ファイル](https://github.com/MicrosoftDocs/SecurityBenchmarks/tree/master/Azure%20Offer%20Security%20Baselines)に関するページを参照してください。

## <a name="network-security"></a>ネットワークのセキュリティ

*詳細については、[Azure セキュリティ ベンチマークの「ネットワークのセキュリティ](/azure/security/benchmarks/security-controls-v2-network-security)」を参照してください。*

### <a name="ns-3-establish-private-network-access-to-azure-services"></a>NS-3: Azure サービスへのプライベート ネットワーク アクセスを確立する

**ガイダンス**: Power BI では、プライベート リンク エンドポイントへの Power BI テナントの接続、およびパブリック インターネット アクセスの無効化がサポートされています。

- [Power BI にアクセスするためのプライベート リンク](https://docs.microsoft.com/power-bi/admin/service-security-private-links)

**Azure Security Center の監視**: 適用なし

**責任**: 共有

## <a name="identity-management"></a>ID 管理

*詳細については、[Azure セキュリティ ベンチマークの「ID 管理](/azure/security/benchmarks/security-controls-v2-identity-management).* 」を参照してください。

### <a name="im-1-standardize-azure-active-directory-as-the-central-identity-and-authentication-system"></a>IM-1:Azure Active Directory を中央 ID および認証システムとして標準化する

**ガイダンス**: Power BI は、Azure の既定の ID およびアクセス管理サービスである Azure Active Directory (Azure AD) と統合されています。 組織の ID およびアクセス管理を管理するには、Azure AD を標準化する必要があります。

Azure AD を保護することは、組織のクラウド セキュリティ プラクティスの中で高い優先順位を持つ必要があります。 Azure AD では、Microsoft のベスト プラクティスの推奨事項を基準にした、お客様の ID セキュリティ体制を評価するために役立つ ID セキュリティ スコアが提供されます。 スコアを使用して、構成がベスト プラクティスの推奨事項とどの程度一致しているかを測定し、セキュリティ体制を強化します。

注意:Azure AD では外部 ID がサポートされています。これにより、Microsoft アカウントを持たないユーザーは、自分の外部 ID を使用して自分のアプリケーションおよびリソースにサインインすることができます。

- [Azure Active Directory のテナント](https://docs.microsoft.com/azure/active-directory/develop/single-and-multi-tenant-apps)

- [Azure AD インスタンスを作成して構成する方法](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-access-create-new-tenant)

- [アプリケーションに外部 ID プロバイダーを使用する](https://docs.microsoft.com/azure/active-directory/b2b/identity-providers)

- [Azure Active Directory の ID セキュリティ スコアとは](https://docs.microsoft.com/azure/active-directory/fundamentals/identity-secure-score)

**Azure Security Center の監視**: 適用なし

**責任**: Customer

### <a name="im-2-manage-application-identities-securely-and-automatically"></a>IM-2:アプリケーション ID を安全かつ自動的に管理する

**ガイダンス**: Power BI と Power BI Embedded では、サービス プリンシパルの使用がサポートされています。 Key Vault での Power BI の暗号化または Power BI へのアクセスに使用されるサービス プリンシパルの資格情報を格納し、適切なアクセス ポリシーをコンテナーに割り当てて、定期的にアクセス許可を確認します。

サービス プリンシパルを使用して Premium ワークスペースとデータセットのタスクを自動化する https://docs.microsoft.com/power-bi/admin/service-premium-service-principal

**Azure Security Center の監視**: 適用なし

**責任**: Customer

### <a name="im-3-use-azure-ad-single-sign-on-sso-for-application-access"></a>IM-3:アプリケーションのアクセスに Azure AD シングル サインオン (SSO) を使用する

**ガイダンス**: Power BI では Azure Active Directory を使用して、Azure リソース、クラウド アプリケーション、およびオンプレミスのアプリケーションに ID を付与し、アクセス管理を実現します。 これには、従業員などのエンタープライズ ID や、パートナー、ベンダー、サプライヤーなどの外部 ID も含まれます。 これにより、オンプレミスおよびクラウド内の組織のデータとリソースへのアクセスを管理し、セキュリティで保護するためのシングルサインオン (SSO) が可能になります。 すべてのユーザー、アプリケーション、デバイスを Azure AD に接続することで、シームレスで安全なアクセスを実現し、可視性と制御性を高めることができます。

- [Azure AD を使用したアプリケーションの SSO について理解する](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on)

**Azure Security Center の監視**: 適用なし

**責任**: Customer

### <a name="im-4-use-strong-authentication-controls-for-all-azure-active-directory-based-access"></a>IM-4:すべての Azure Active Directory ベースのアクセスに強力な認証制御を使用する

**ガイダンス**: Power BI は、Multi-Factor Authentication (MFA) を介した強力な認証制御および強力なパスワードなしの手法をサポートする Azure AD に統合されています。
- 多要素認証 - Azure AD MFA を有効にします。MFA セットアップでのベスト プラクティスについては Azure Security Center ID およびアクセス管理の推奨事項に従います。 MFA は、サインインの条件とリスク要因に基づいて、すべてのユーザー、選択されたユーザー、またはユーザー単位のレベルで適用できます。
- パスワードなし認証 – 次の 3 つのパスワードなし認証オプションを使用できます。Windows Hello for Business、Microsoft Authenticator アプリ、およびスマート カードなどのオンプレミスの認証方法。

管理者と特権ユーザーに対して最高レベルの強力な認証を使用するようにし、他のユーザーに対して適切な強力な認証ポリシーをロールアウトします。

注意:MFA を適用できるのは、Azure AD で有効になっているユーザー アカウントに限られます。 Power BI サービス プリンシパルでは、MFA の使用はサポートされていません。

- [Azure で MFA を有効にする方法](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-getstarted)

- [Azure Active Directory のパスワードレス認証オプションの概要](https://docs.microsoft.com/azure/active-directory/authentication/concept-authentication-passwordless)

**Azure Security Center の監視**: 適用なし

**責任**: Customer

### <a name="im-5-monitor-and-alert-on-account-anomalies"></a>IM-5:アカウントの異常を監視してアラートを出す

**ガイダンス**: 個別にスコープを指定できる Microsoft Cloud App Security で異常検出ポリシーを定義します。これにより、それらは対象として含めるユーザーおよびグループのみに適用されることになります。 このような異常検出ポリシーは、ユーザーによる Power BI へのアクセスおよびその使用に関連する動作の異常を検出して監視するのに役立ちます。

- [Power BI で Microsoft Cloud App Security の制御を使用する](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls)

**Azure Security Center の監視**: 適用なし

**責任**: Customer

### <a name="im-6-restrict-azure-resource-access-based-on-conditions"></a>IM-6:条件に基づいて Azure リソースへのアクセスを制限する

**ガイダンス**: Power BI では、Azure AD 条件付きアクセスがサポートされています。これを使用すれば、ユーザー定義の条件 (特定の IP 範囲からのユーザー ログインでは MFA を使用してログインする必要がある、など) に基づいて、よりきめ細かいアクセス制御を行うことができます。 さまざまなユース ケースに対してきめ細かな認証セッション管理ポリシーを使用することもできます。

- [Azure での条件付きアクセスの概要](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)

- [一般的な条件付きアクセス ポリシー](https://docs.microsoft.com/azure/active-directory/conditional-access/concept-conditional-access-policy-common)

- [条件付きアクセスを使用して認証セッション管理を構成する](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-conditional-access-session-lifetime)

- [Power BI で Microsoft Cloud App Security の制御を使用する](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls)

**Azure Security Center の監視**: 適用なし

**責任**: Customer

### <a name="im-7-eliminate-unintended-credential-exposure"></a>IM-7:意図しない資格情報の公開を排除する

**ガイダンス**: Power BI 埋め込みアプリケーションの場合、コード内にある資格情報を識別する資格情報スキャナーを実装することをお勧めします。 また、資格情報スキャナーを使うと、検出された資格情報を、Azure Key Vault などのより安全な場所に移動しやすくなります。

Key Vault での Power BI の暗号化または Power BI へのアクセスに使用される暗号化キーまたはサービス プリンシパルの資格情報を格納し、適切なアクセス ポリシーをコンテナーに割り当てて、定期的にアクセス許可を確認します。
 
GitHub の場合、ネイティブ シークレット スキャン機能を使用して、コード内で資格情報やその他の形式のシークレットを識別できます。

- [Power BI で独自の暗号化キーを使用する](https://docs.microsoft.com/power-bi/admin/service-encryption-byok)

 
資格情報を設定する方法
- [スキャナー](https://secdevtools.azurewebsites.net/helpcredscan.html) 

- [GitHub シークレット スキャン](https://docs.github.com/github/administering-a-repository/about-secret-scanning)

**Azure Security Center の監視**: 適用なし

**責任**: 共有

## <a name="privileged-access"></a>特権アクセス

*詳細については、[Azure セキュリティ ベンチマークの「特権アクセス](/azure/security/benchmarks/security-controls-v2-privileged-access)」を参照してください。*

### <a name="pa-1-protect-and-limit-highly-privileged-users"></a>PA-1:高い特権を持つユーザーを保護および制限する

**ガイダンス**: リスクを軽減し、最小の特権の原則に従うには、Power BI 管理者のメンバーシップを少数の人員に限定することをお勧めします。 これらの特権アクセス許可を持つユーザーは、場合によっては、組織のあらゆる管理機能にアクセスして変更することが可能です。 Microsoft 365 または Azure Active Directory を介して、グローバル管理者には、Power BI サービスの管理者権限も暗黙的に付与されます。

Power BI には、以下の高い特権が与えられたアカウントが用意されています。
- グローバル管理者
- 課金管理者
- ライセンス管理者
- ユーザー管理者
- Power BI 管理者
- Power BI Premium 容量管理者
- Power BI Embedded 容量管理者

条件付きアクセス ポリシーを有効にし、Power BI で使用されるセッションを Cloud App Security サービスを介してルーティングできるように、Power BI では Azure AD のセッション ポリシーがサポートされています。

M365 Privileged Access Management を使用して、Power BI 管理者アカウントに対して Just-In-Time (JIT) 特権アクセスを有効にします。

- [Power BI に関連する管理者ロール](https://docs.microsoft.com/power-bi/admin/service-admin-administering-power-bi-in-your-organization#administrator-roles-related-to-power-bi)

- [M365 Privileged Access Management](https://docs.microsoft.com/microsoft-365/compliance/privileged-access-management-overview?view=o365-worldwide&amp;preserve-view=true)

- [Power BI での Cloud App Security 制御](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls)

**Azure Security Center の監視**: 適用なし

**責任**: Customer

### <a name="pa-2-restrict-administrative-access-to-business-critical-systems"></a>PA-2:ビジネス クリティカルなシステムへの管理アクセスを制限する

**ガイダンス**: 高い特権を持つアカウント、または Power BI への昇格されたアクセスを持つロールの数を制限します。

[こちら](https://docs.microsoft.com/microsoft-365/compliance/privileged-access-management-overview?view=o365-worldwide&amp;preserve-view=true)の M365 Privileged Access Management のガイダンスを使用して、Just-In-Time (JIT) 特権アクセスを有効にすることができます。

詳細については、[こちら](https://aka.ms/PBIEnterpriseDeploymentWP)の Power BI のエンタープライズ展開に関するドキュメントの 183 ページを参照してください。

**Azure Security Center の監視**: 適用なし

**責任**: Customer

### <a name="pa-3-review-and-reconcile-user-access-regularly"></a>PA-3:ユーザー アクセスを定期的に確認して調整する

**ガイダンス**: Power BI サービス管理者は、Power BI アクティビティ ログに基づくカスタム レポートを使用して、テナント レベルですべての Power BI リソースの使用状況を分析できます。 アクティビティをダウンロードするには、REST API または PowerShell コマンドレットを使用します。 アクティビティ データは、日付の範囲、ユーザー、およびアクティビティの種類でフィルター処理することもできます。

Power BI アクティビティ ログにアクセスするには、次の要件を満たしている必要があります。
- グローバル管理者または Power BI サービス管理者のいずれかであること。
- [Power BI 管理コマンドレット](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt)をローカルにインストールしているか、Azure Cloud Shell で Power BI 管理コマンドレットを使用していること。

これらの要件が満たされたら、次のガイダンスに従って Power BI 内のユーザー アクティビティを追跡できます。

- [Power BI でユーザー アクティビティを追跡する](https://docs.microsoft.com/power-bi/admin/service-admin-auditing)

**Azure Security Center の監視**: 適用なし

**責任**: Customer

### <a name="pa-4-set-up-emergency-access-in-azure-ad"></a>PA-4:Azure AD で緊急アクセスを設定する

**ガイダンス**: Power BI は、そのリソースを管理するために Azure Active Directory と M365 に統合されています。 M365 テナントまたは Azure AD 組織から誤ってロック アウトされないようにするには、通常の管理者アカウントが使用できないときのアクセス用に緊急アクセス アカウントを設定します。 緊急アクセス用アカウントは高い特権を持っており、特定の個人に割り当てることはできません。 緊急アクセス用アカウントは、通常の管理者アカウントを使うことができない "緊急事態" に制限されます。

緊急アクセス用アカウントの資格情報 (パスワード、証明書、スマート カードなど) は安全に保管し、緊急時にのみそれらを使うことを許可された個人のみに知らせる必要があります。

- [Azure AD で緊急アクセス用アカウントを管理する](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-emergency-access)

- [M365 アカウントを保護する](https://docs.microsoft.com/microsoft-365/campaigns/m365-campaigns-protect-admin-accounts)

**Azure Security Center の監視**: 適用なし

**責任**: Customer

### <a name="pa-6-use-privileged-access-workstations"></a>PA-6:特権アクセス ワークステーションを使用する

**ガイダンス**:セキュリティで保護された分離したワークステーションは、管理者、開発者、重要なサービス オペレーターのような機密性の高い役割のセキュリティには非常に重要です。 Power BI の管理に関係する管理タスクの場合は、高度にセキュリティで保護されたユーザー ワークステーションや Azure Bastion を使用してください。 Azure Active Directory、Microsoft Defender Advanced Threat Protection (ATP)、または Microsoft Intune を使用して、管理タスクのためにセキュリティで保護されたマネージド ユーザー ワークステーションを展開します。 セキュリティで保護されたワークステーションを一元管理して、強力な認証、ソフトウェアとハードウェアのベースライン、制限された論理アクセスとネットワーク アクセスなどのセキュリティで保護された構成を実施できます。

特権アクセスについて
- [ワークステーション](https://docs.microsoft.com/azure/active-directory/devices/concept-azure-managed-workstation)

- [特権アクセス ワークステーションを展開する](https://docs.microsoft.com/azure/active-directory/devices/howto-azure-managed-workstation)

**Azure Security Center の監視**: 適用なし

**責任**: Customer

## <a name="data-protection"></a>データ保護

*詳細については、[Azure セキュリティ ベンチマークの「データ保護](/azure/security/benchmarks/security-controls-v2-data-protection)」を参照してください。*

### <a name="dp-1-discovery-classify-and-label-sensitive-data"></a>DP-1:機密データを検出、分類、ラベル付けする

**ガイダンス**: レポート、ダッシュボード、データセット、およびデータフローに対して、Microsoft Information Protection の秘密度ラベルを使用すれば、無許可のデータ アクセスや漏洩から秘密コンテンツを保護できます。

Microsoft Information Protection の秘密度ラベルを使用すれば、Power BI サービスでレポート、ダッシュボード、データセット、およびデータフローを分類およびラベル付けできるほか、コンテンツが Power BI サービスから Excel、PowerPoint、および PDF ファイルにエクスポートされるときに機密コンテンツを不正なデータ アクセスや漏洩から保護することができます。

- [Power BI で秘密度ラベルを適用する方法](https://docs.microsoft.com/power-bi/admin/service-security-apply-data-sensitivity-labels)

**Azure Security Center の監視**: 適用なし

**責任**: Customer

### <a name="dp-2-protect-sensitive-data"></a>DP-2:機密データを保護する

**ガイダンス**: Power BI は、機密データの保護のために Microsoft Information Protection の秘密度ラベルと統合されています。 詳細については、[Power BI の Microsoft Information Protection 秘密度ラベル](https://docs.microsoft.com/power-bi/admin/service-security-sensitivity-label-overview)に関するページを参照してください。

Power BI を使用すると、サービス ユーザーは独自のキーを使用して保存データを保護することができます。 詳細については、「[Power BI で独自の暗号化キーを使用する](https://docs.microsoft.com/power-bi/admin/service-encryption-byok)」を参照してください。

お客様には、クラウド サービスへのデータの露出を最小限に抑えるために、データ ソースをオンプレミスで維持し、直接クエリまたはライブ接続をオンプレミス データ ゲートウェイで利用するオプションが用意されています。 詳細については、「[オンプレミス データ ゲートウェイとは](https://docs.microsoft.com/data-integration/gateway/service-gateway-onprem)」を参照してください。

Power BI では行レベルのセキュリティがサポートされています。 詳細については、「[Power BI での行レベルのセキュリティ (RLS)](https://docs.microsoft.com/power-bi/admin/service-admin-rls)」をご覧ください。 RLS は、直接クエリ データ ソースにも適用できることに注目してください。この場合、PBIX ファイルは、セキュリティを有効にするためのプロキシとして機能します。

**Azure Security Center の監視**: 適用なし

**責任**: Customer

### <a name="dp-3-monitor-for-unauthorized-transfer-of-sensitive-data"></a>DP-3:機密データの不正転送を監視する

**ガイダンス**: この制御を部分的に実現するには、Power BI 用の Microsoft Cloud App Security サポートを使用します。

Power BI で Cloud App Security を使用すると、Power BI のレポート、データ、およびサービスを意図しない漏えいや侵害から保護することができます。 Cloud App Security では、Azure Active Directory (Azure AD) のリアルタイム セッション制御を使用して、組織のデータに対して条件付きアクセス ポリシーを作成すると、Power BI 分析を確実にセキュリティで保護することができます。 これらのポリシーを設定すると、管理者は、ユーザーのアクセスとアクティビティの監視、リアルタイムのリスク分析の実行、ラベル固有の制御の設定を行うことができます。

使用
- [Power BI での Microsoft Cloud App Security の制御](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls)

**Azure Security Center の監視**: 適用なし

**責任**: Customer

### <a name="dp-4-encrypt-sensitive-information-in-transit"></a>DP-4:転送中の機密情報を暗号化する

**ガイダンス**: HTTP トラフィックの場合、ご利用の Power BI リソースに接続するクライアントおよびデータソースがいずれも、TLS v1.2 以上とネゴシエートできるようにします。

- [TLS バージョンの使用の強制](https://docs.microsoft.com/power-bi/admin/service-admin-power-bi-security#enforcing-tls-version-usage)

- [TLS セキュリティに関する情報](https://docs.microsoft.com/security/engineering/solving-tls1-problem)

**Azure Security Center の監視**: 適用なし

**責任**: Customer

### <a name="dp-5-encrypt-sensitive-data-at-rest"></a>DP-5:保存データを暗号化する

**ガイダンス**: Power BI では、保存データと処理中のデータが暗号化されます。 既定では、Power BI で Microsoft マネージド キーを使用してデータを暗号化します。 組織は、レポート イメージから Premium 容量にインポートされたデータセットまで、Power BI 全体で保存時のユーザー コンテンツの暗号化に独自のキーを使用することを選択できます。

- [Power BI で bring-your-own-key を使用する](https://docs.microsoft.com/power-bi/admin/service-encryption-byok)

**Azure Security Center の監視**: 適用なし

**責任**: 共有

## <a name="asset-management"></a>アセット管理

*詳細については、[Azure セキュリティ ベンチマークの「アセット管理](/azure/security/benchmarks/security-controls-v2-asset-management)」を参照してください。*

### <a name="am-1-ensure-security-team-has-visibility-into-risks-for-assets"></a>AM-1:セキュリティ チームが資産のリスクを確実に可視化できるようにする

**ガイダンス**: Azure Sentinel を Power BI の Office 監査ログと共に使用することで、セキュリティ チームが Power BI 資産に対するリスクを確実に把握できるようにします。

- [Azure Sentinel に Office 365 のログを接続する](https://docs.microsoft.com/azure/sentinel/connect-office-365)

**Azure Security Center の監視**: 適用なし

**責任**: Customer

### <a name="am-2-ensure-security-team-has-access-to-asset-inventory-and-metadata"></a>AM-2:セキュリティ チームが資産インベントリとメタデータに確実にアクセスできるようにする

**ガイダンス**: 継続的に更新される、Power BI Embedded リソースのインベントリにセキュリティ チームが確実にアクセスできるようにします。 セキュリティ チームは、組織が新たなリスクにさらされる可能性を評価するため、および継続的なセキュリティ改善への入力として、このインベントリを必要とすることがよくあります。 

Azure Resource Graph を使用すると、ご利用のサブスクリプション内のすべての Power BI Embedded リソースを照会および検出することができます。  

タグと Azure の他のメタデータ (名前、説明、カテゴリ) を使用して、組織の分類に従って資産を論理的に整理します。  

- [Azure Resource Graph Explorer を使用してクエリを作成する方法](https://docs.microsoft.com/azure/governance/resource-graph/first-query-portal)

- [リソースの名前付けとタグ付けの意思決定ガイド](https://docs.microsoft.com/azure/cloud-adoption-framework/decision-guides/resource-tagging/?toc=/azure/azure-resource-manager/management/toc.json)

**Azure Security Center の監視**: 適用なし

**責任**: Customer

### <a name="am-3-use-only-approved-azure-services"></a>AM-3:承認された Azure サービスのみを使用する

**ガイダンス**: Power BI では Power BI Embedded の Azure Resource Manager ベースの展開がサポートされています。お客様はカスタム ポリシー定義を使用することで、該当するリソースの展開を Azure Policy を介して制限することができます。

Azure Policy を使用して、環境内でユーザーがプロビジョニングできるサービスを監査および制限します。 Azure Resource Graph を使用して、サブスクリプション内のリソースのクエリまたは検出を行います。 また、Azure Monitor を使用して、承認されていないサービスが検出されたときにアラートをトリガーするルールを作成することもできます。

- [Azure Policy を構成して管理する方法](https://docs.microsoft.com/azure/governance/policy/tutorials/create-and-manage)

特定のリソースの種類を拒否する方法
- [Azure Policy](https://docs.microsoft.com/azure/governance/policy/samples/built-in-policies#general)

Azure でクエリを作成する方法
- [Resource Graph エクスプローラー](https://docs.microsoft.com/azure/governance/resource-graph/first-query-portal)

**Azure Security Center の監視**: 適用なし

**責任**: Customer

## <a name="logging-and-threat-detection"></a>ログと脅威検出

*詳細については、[Azure セキュリティ ベンチマークの「ログと脅威検出](/azure/security/benchmarks/security-controls-v2-logging-threat-detection)」を参照してください。*

### <a name="lt-2-enable-threat-detection-for-azure-identity-and-access-management"></a>LT-2:Azure ID とアクセスの管理のために脅威検出を有効にする

**ガイダンス**: カスタム脅威検出を設定するのに使用できるログを Power BI から SIEM に転送します。 さらに、Power BI で Microsoft Cloud App Security (MCAS) 制御を使用すれば、[こちら](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls)のガイドに従って異常検出を有効にすることができます。

- [Power BI でユーザー アクティビティを追跡する](https://docs.microsoft.com/power-bi/admin/service-admin-auditing)

**Azure Security Center の監視**: 適用なし

**責任**: Customer

### <a name="lt-3-enable-logging-for-azure-network-activities"></a>LT-3:Azure ネットワーク アクティビティのログ記録を有効にする

**ガイダンス**: Power BI はフル マネージド SaaS オファリングであり、基になるネットワーク構成とログは Microsoft の責任となります。 プライベート リンクを利用しているお客様には、構成可能なログおよび監視が用意されています。

- [プライベート リンクのログおよび監視](https://docs.microsoft.com/azure/private-link/private-link-overview#logging-and-monitoring)

**Azure Security Center の監視**: 適用なし

**責任**: 共有

### <a name="lt-4-enable-logging-for-azure-resources"></a>LT-4:Azure リソースのログ記録を有効にする

**ガイダンス**: Power BI では、ユーザー アクティビティを追跡する 2 つのオプションがあります。Power BI アクティビティ ログと統合監査ログです。 どちらのログにも、Power BI 監査データの完全なコピーが含まれていますが、次にまとめられているように、いくつかの重要な違いがあります。
 
統合監査ログ:

 
- Power BI 監査イベントに加えて、SharePoint Online、Exchange Online、Dynamics 365、およびその他のサービスからのイベントが含まれます。

 
- View-Only Audit Logs (表示専用監査ログ) または監査ログのアクセス許可を持つユーザー (グローバル管理者や監査人など) のみがアクセス権を持ちます。

 
- グローバル管理者と監査者は、Microsoft 365 Security Center、および Microsoft 365 コンプライアンス センターを使用して、統合監査ログを検索できます。

 
- グローバル管理者と監査者は、Microsoft 365 Management API とコマンドレットを使用して、監査ログ エントリをダウンロードできます。

 
- 監査データは 90 日間保持されます。

 
- テナントが別の Azure リージョンに移動された場合でも、監査データは保持されます。
 
Power BI アクティビティ ログ:

 
- Power BI 監査イベントのみが含まれます。

 
 
- グローバル管理者と Power BI サービス管理者がアクセス権を持ちます。

 
- アクティビティ ログを検索するためのユーザー インターフェイスはまだありません。

 
- グローバル管理者と Power BI サービス管理者は、Power BI REST API および管理コマンドレットを使用して、アクティビティ ログ エントリをダウンロードできます。

 
- アクティビティ データは 30 日間保持されます。

 
- テナントが別の Azure リージョンに移動された場合、アクティビティ データは保持されません。

- [Power BI の監査データ](https://docs.microsoft.com/power-bi/admin/service-admin-auditing#operations-available-in-the-audit-and-activity-logs)

- [Power BI アクティビティ ログ](https://docs.microsoft.com/power-bi/admin/service-admin-auditing#use-the-activity-log)

- [Power BI 監査ログ](https://docs.microsoft.com/power-bi/admin/service-admin-auditing#use-the-audit-log)

**Azure Security Center の監視**: 適用なし

**責任**: 共有

### <a name="lt-5-centralize-security-log-management-and-analysis"></a>LT-5:セキュリティ ログの管理と分析を一元化する

**ガイダンス**: Power BI では、次の 2 か所でログを集中管理します: Power BI のアクティビティ ログおよび統合された監査ログ。 どちらのログにも、Power BI 監査データの完全なコピーが含まれていますが、次にまとめられているように、いくつかの重要な違いがあります。
 

統合監査ログ:

- Power BI 監査イベントに加えて、SharePoint Online、Exchange Online、Dynamics 365、およびその他のサービスからのイベントが含まれます。

- View-Only Audit Logs (表示専用監査ログ) または監査ログのアクセス許可を持つユーザー (グローバル管理者や監査人など) のみがアクセス権を持ちます。

- グローバル管理者と監査者は、Microsoft 365 Security Center、および Microsoft 365 コンプライアンス センターを使用して、統合監査ログを検索できます。

- グローバル管理者と監査者は、Microsoft 365 Management API とコマンドレットを使用して、監査ログ エントリをダウンロードできます。

- 監査データは 90 日間保持されます。

- テナントが別の Azure リージョンに移動された場合でも、監査データは保持されます。

 

Power BI アクティビティ ログ:

- Power BI 監査イベントのみが含まれます。

- グローバル管理者と Power BI サービス管理者がアクセス権を持ちます。

- アクティビティ ログを検索するためのユーザー インターフェイスはまだありません。

- グローバル管理者と Power BI サービス管理者は、Power BI REST API および管理コマンドレットを使用して、アクティビティ ログ エントリをダウンロードできます。

- アクティビティ データは 30 日間保持されます。

- テナントが別の Azure リージョンに移動された場合、アクティビティ データは保持されません。

- [Power BI の監査データ](https://docs.microsoft.com/power-bi/admin/service-admin-auditing#operations-available-in-the-audit-and-activity-logs)

- [Power BI アクティビティ ログ](https://docs.microsoft.com/power-bi/admin/service-admin-auditing#use-the-activity-log)

- [Power BI 監査ログ](https://docs.microsoft.com/power-bi/admin/service-admin-auditing#use-the-audit-log)

**Azure Security Center の監視**: 適用なし

**責任**: Customer

### <a name="lt-6-configure-log-storage-retention"></a>LT-6:ログの保持期間を構成する

**ガイダンス**: 自社のコンプライアンス、規制、およびビジネス要件に応じて、Office 監査ログに対するストレージ保持ポリシーを構成します。

- [Office 監査ログの保持ポリシー](https://docs.microsoft.com/microsoft-365/compliance/audit-log-retention-policies)

**Azure Security Center の監視**: 適用なし

**責任**: Customer

## <a name="incident-response"></a>インシデント対応

*詳細については、[Azure セキュリティ ベンチマークの「インシデント対応](/azure/security/benchmarks/security-controls-v2-incident-response)」を参照してください。*

### <a name="ir-1-preparation--update-incident-response-process-for-azure"></a>IR-1: 準備 – インシデント対応プロセスを Azure 用に更新する

**ガイダンス**:組織において、セキュリティ インシデントに対応するためのプロセスが用意されていること、Azure のこれらのプロセスが更新されていること、それらのプロセスを定期的に使用して準備されていることを確認します。

- [企業環境全体にセキュリティを実装する](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud)

- [インシデント対応のリファレンス ガイド](https://docs.microsoft.com/microsoft-365/downloads/IR-Reference-Guide.pdf)

**Azure Security Center の監視**: 適用なし

**責任**: Customer

### <a name="ir-2-preparation--setup-incident-notification"></a>IR-2: 準備 – インシデント通知をセットアップする

**ガイダンス**:Azure Security Center でセキュリティ インシデントの連絡先情報を設定します。 この連絡先情報は、Microsoft Security Response Center (MSRC) でユーザーのデータが違法または権限のないユーザーによってアクセスされたことが検出された場合に、Microsoft からの連絡先として使用されます。 また、インシデント対応のニーズに応じて、異なる Azure サービスでインシデント アラートと通知をカスタマイズするオプションもあります。 

- [Azure Security Center のセキュリティ連絡先を設定する方法](https://docs.microsoft.com/azure/security-center/security-center-provide-security-contact-details)

**Azure Security Center の監視**: 適用なし

**責任**: Customer

### <a name="ir-3-detection-and-analysis--create-incidents-based-on-high-quality-alerts"></a>IR-3: 検出と分析 – 高品質のアラートに基づいてインシデントを作成する

**ガイダンス**:高品質のアラートを作成し、アラートの品質を測定するプロセスがあることを確認します。 これにより、過去のインシデントから教訓を学び、アナリストに対するアラートに優先順位を付けることができるので、擬陽性に時間を無駄にすることがありません。

Microsoft Cloud App Security で Power BI に関連するアラートを監視します。 高品質のアラートは、過去のインシデントからの経験と、検証済みのコミュニティ ソースと、さまざまな信号ソースを融合して相互に関連付けることでアラートを生成およびクリーンアップするように設計されたツールに基づいて構築できます。

- [Cloud App Security でアラートを監視する](https://docs.microsoft.com/cloud-app-security/monitor-alerts)

**Azure Security Center の監視**: 適用なし

**責任**: Customer

### <a name="ir-4-detection-and-analysis--investigate-an-incident"></a>IR-4: 検出と分析 – インシデントを調査する

**ガイダンス**: 組織のインシデント対応ガイドを作成します。 定期的にシステムのインシデント対応機能をテストする演習を実施します。 弱点やギャップを特定し、必要に応じて計画を見直します。

要員のすべてのロールを定義するインシデント対応計画が記述されていることと、検出からインシデント後のレビューまでのインシデント対応/管理のフェーズがあることを確認します。

- [Microsoft Threat Protection でのインシデントの概要](https://docs.microsoft.com/microsoft-365/security/mtp/incidents-overview)

**Azure Security Center の監視**: 適用なし

**責任**: Customer

### <a name="ir-5-detection-and-analysis--prioritize-incidents"></a>IR-5: 検出と分析 – インシデントの優先順位を付ける

**ガイダンス**:アラートの重要度と資産の機密性に基づいて、最初に注目するインシデントについてのコンテキストをアナリストに提供します。 

 
Microsoft Threat Protection を使用すると、関連付け分析が適用され、さまざまな製品からの関連するアラートおよび調査結果が 1 つのインシデントに集約されます。 また、Microsoft Threat Protection を使用すると、Microsoft Threat Protection が備える資産および製品スイート全体にわたるエンドツーエンドの可視性によって、悪意のあるものとしか識別できないアクティビティに対して固有のアラートがトリガーされます。 そのような方法で、Microsoft Threat Protection によって、より広範な攻撃ストーリーが説明されます。これにより、セキュリティ運用アナリストは組織全体の複雑な脅威を理解し、対処できるようになります。

- [Microsoft Threat Protection でインシデントの優先度を設定する](https://docs.microsoft.com/microsoft-365/security/mtp/incident-queue?view=o365-worldwide&amp;preserve-view=true)

**Azure Security Center の監視**: 適用なし

**責任**: Customer

### <a name="ir-6-containment-eradication-and-recovery--automate-the-incident-handling"></a>IR-6: 包含、根絶、復旧 – インシデントの処理を自動化する

**ガイダンス**:手動による反復タスクを自動化して、応答時間を短縮し、アナリストの負担を軽減します。 手動タスクの実行には時間がかかり、各インシデントの速度が低下し、アナリストが処理できるインシデントの数が減少します。 手動タスクではアナリストの疲労も増加します。これにより、遅延が発生する人的エラーのリスクが増加し、複雑なタスクに効果的に焦点を当てるアナリストの能力が低下します。  
 
Microsoft Threat Protection のワークフロー オートメーション機能を使用すれば、受信セキュリティ アラートに応じて調査と修復を自動的にトリガーすることができます。 
 
- [Microsoft Threat Protection で自動化されている調査と応答](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-autoir)

**Azure Security Center の監視**: 適用なし

**責任**: Customer

## <a name="posture-and-vulnerability-management"></a>体制と脆弱性の管理

*詳細については、[Azure セキュリティ ベンチマークの「体制と脆弱性の管理](/azure/security/benchmarks/security-controls-v2-posture-vulnerability-management)」を参照してください。*

### <a name="pv-1-establish-secure-configurations-for-azure-services"></a>PV-1: Azure サービスのセキュリティで保護された構成を確立する 

**ガイダンス**: 自分が属する組織とセキュリティ スタンスに適した設定で Power BI サービスを構成します。 サービスとコンテンツにアクセスするための設定と、ワークスペースおよびアプリのセキュリティについては慎重に検討する必要があります。 Power BI のエンタープライズ展開に関するホワイトペーパーに記載された Power BI のセキュリティとデータ保護に関する内容を参照してください。

- [エンタープライズ展開に関するホワイトペーパー](https://aka.ms/PBIEnterpriseDeploymentWP)

**Azure Security Center の監視**: 適用なし

**責任**: Customer

### <a name="pv-2-sustain-secure-configurations-for-azure-services"></a>PV-2: Azure サービスのセキュリティで保護された構成を維持する

**ガイダンス**: Power BI 管理 REST API を使用して、Power BI インスタンスを監視します。

- [Power BI 管理 REST API](https://docs.microsoft.com/rest/api/power-bi/admin)

- [Power BI のエンタープライズ展開に関するホワイトペーパー](https://aka.ms/PBIEnterpriseDeploymentWP)

**Azure Security Center の監視**: 適用なし

**責任**: Customer

### <a name="pv-8-conduct-regular-attack-simulation"></a>PV-8: 定期的に攻撃シミュレーションを実施する

**ガイダンス**:必要に応じて、Azure リソースの侵入テストまたはレッド チーム アクティビティを実施し、セキュリティに関するすべての重大な調査結果が確実に修復されるようにします。

お客様の侵入テストが Microsoft のポリシーに違反しないように、Microsoft クラウド侵入テストの実施ルールに従ってください。 Microsoft が管理しているクラウド インフラストラクチャ、サービス、アプリケーションに対する Red Teaming およびライブ サイト侵入テストに関する Microsoft の戦略と実施を活用してください。

- [Azure での侵入テスト](https://docs.microsoft.com/azure/security/fundamentals/pen-testing)

- [侵入テストの実施ルール](https://www.microsoft.com/msrc/pentest-rules-of-engagement?rtc=1)

- [Microsoft Cloud Red Teaming](https://gallery.technet.microsoft.com/Cloud-Red-Teaming-b837392e)

**Azure Security Center の監視**: 適用なし

**責任**: 共有

## <a name="backup-and-recovery"></a>バックアップと回復

*詳細については、[Azure セキュリティ ベンチマーク: バックアップと回復](/azure/security/benchmarks/security-controls-v2-backup-recovery)に関するページを参照してください。*

### <a name="br-3-validate-all-backups-including-customer-managed-keys"></a>BR-3:カスタマー マネージド キーを含むすべてのバックアップを検証する

**ガイダンス**: Power BI で Bring Your Own Key (BYOK) 機能を使用している場合は、ご利用のカスタマー マネージド キーにアクセスしてそれを復元できることを定期的に検証する必要があります。

- [Power BI での BYOK](https://docs.microsoft.com/power-bi/admin/service-encryption-byok)

**Azure Security Center の監視**: 適用なし

**責任**: Customer

### <a name="br-4-mitigate-risk-of-lost-keys"></a>BR-4:キー紛失のリスクを軽減する

**ガイダンス**: Power BI で Bring Your Own Key (BYOK) 機能を使用している場合は、Power BI での BYOK に関する以下のドキュメントに記載されているガイダンスに従って、カスタマー マネージド キーを制御する Key Vault を確実に構成する必要があります。 Azure Key Vault で論理的な削除と消去保護を有効にして、キーが偶発的または悪意から削除されないようにします。

- [Power BI での BYOK](https://docs.microsoft.com/power-bi/admin/service-encryption-byok)

- [Key Vault で論理的な削除と消去保護を有効にする方法](https://docs.microsoft.com/azure/storage/blobs/storage-blob-soft-delete?tabs=azure-portal)

ゲートウェイのキー リソースについては、以下のゲートウェイ回復キーに関するドキュメントに記載されているガイダンスに確実に従ってください。

- [オンプレミス データ ゲートウェイ回復キー](https://docs.microsoft.com/data-integration/gateway/service-gateway-recovery-key)

**Azure Security Center の監視**: 適用なし

**責任**: Customer

## <a name="governance-and-strategy"></a>ガバナンスと戦略

*詳細については、[Azure セキュリティ ベンチマークの「ガバナンスと戦略](/azure/security/benchmarks/security-controls-v2-governance-strategy)」を参照してください。*

### <a name="gs-1-define-asset-management-and-data-protection-strategy"></a>GS-1: 資産の管理とデータ保護の戦略を定義する 

**ガイダンス**:システムとデータを継続的に監視および保護するための明確な戦略が文書化および伝達されるようにします。 ビジネスに不可欠なデータとシステムの検出、評価、保護、監視の優先順位を決定します。 

この戦略には、次の要素に関する文書化されたガイダンス、ポリシー、標準が含まれている必要があります。 

-   ビジネス リスクに応じたデータ分類標準

-   リスクと資産のインベントリに対するセキュリティ組織の可視性 

-   Azure サービスを使用するためのセキュリティ組織の承認 

-   ライフサイクルを通じた資産のセキュリティ

-   組織のデータ分類に従った必要なアクセス制御戦略

-   Azure ネイティブおよびサードパーティのデータ保護機能の使用

-   転送中および保存中のユース ケースのデータ暗号化要件

-   適切な暗号化標準

詳細については、次のリファレンスを参照してください。
- [Azure セキュリティ アーキテクチャに関する推奨事項 - ストレージ、データ、暗号化](https://docs.microsoft.com/azure/architecture/framework/security/storage-data-encryption?toc=/security/compass/toc.json&amp;bc=/security/compass/breadcrumb/toc.json)

- [Azure のセキュリティの基礎 - Azure のデータ セキュリティ、暗号化、ストレージ](https://docs.microsoft.com/azure/security/fundamentals/encryption-overview)

- [クラウド導入フレームワーク - Azure のデータ セキュリティと暗号化のベスト プラクティス](https://docs.microsoft.com/azure/security/fundamentals/data-encryption-best-practices?toc=/azure/cloud-adoption-framework/toc.json&amp;bc=/azure/cloud-adoption-framework/_bread/toc.json)

- [Azure セキュリティ ベンチマーク - アセット管理](https://docs.microsoft.com/azure/security/benchmarks/security-controls-v2-asset-management)

- [Azure セキュリティ ベンチマーク - データ保護](/azure/security/benchmarks/security-controls-v2-data-protection)

**Azure Security Center の監視**: 適用なし

**責任**: Customer

### <a name="gs-2-define-enterprise-segmentation-strategy"></a>GS-2: 企業のセグメント化戦略を定義する 

**ガイダンス**:ID、ネットワーク、アプリケーション、サブスクリプション、管理グループ、その他のコントロールを利用し、アセットへのアクセスをセグメント化する企業規模の戦略を確立します。

セキュリティ分離の必要性と、互いと通信し、データにアクセスする必要があるシステムの日常的操作を有効にするという必要性のバランスを慎重に取ります。

セグメント化戦略は、ネットワーク セキュリティ、ID とアクセス モデル、アプリケーション アクセス許可とアクセス モデル、人的プロセスの制御など、あらゆるコントロールの種類を対象として確実に一貫性をもって実装します。

- [Azure のセグメント化戦略に関するガイド (動画)](https://docs.microsoft.com/security/compass/microsoft-security-compass-introduction#azure-components-and-reference-model-2151)

- [Azure のセグメント化戦略に関するガイド (ドキュメント)](https://docs.microsoft.com/security/compass/governance#enterprise-segmentation-strategy)

- [ネットワークのセグメント化を企業のセグメント化戦略に合わせる](https://docs.microsoft.com/security/compass/network-security-containment#align-network-segmentation-with-enterprise-segmentation-strategy)

**Azure Security Center の監視**: 適用なし

**責任**: Customer

### <a name="gs-3-define-security-posture-management-strategy"></a>GS-3: セキュリティ態勢管理の戦略を定義する

**ガイダンス**:個々の資産とそれらがホストされている環境に対するリスクを継続的に測定し、軽減します。 高い価値を持つ資産と、攻撃に晒される可能性の高い部分 (公開されたアプリケーション、ネットワークのイングレス ポイントとエグレス ポイント、ユーザーと管理者のエンドポイントなど) を優先します。

- [Azure セキュリティ ベンチマーク - 体制と脆弱性の管理](https://docs.microsoft.com/azure/security/benchmarks/security-controls-v2-posture-vulnerability-management)

**Azure Security Center の監視**: 適用なし

**責任**: Customer

### <a name="gs-4-align-organization-roles-responsibilities-and-accountabilities"></a>GS-4: 組織の役割、責任、責務を整合させる

**ガイダンス**:セキュリティ組織における役割と責任に関する明確な戦略が文書化されて伝えられるようにします。 セキュリティに関する決定についてわかりやすく説明すること、共有される責任モデルについて全員に教育すること、クラウドをセキュリティで保護するテクノロジについて技術チームに教育することを優先とします。

- [Azure のセキュリティのベスト プラクティス 1 – 人: クラウド セキュリティに関する取り組みについてチームを教育する](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#1-people-educate-teams-about-the-cloud-security-journey)

- [Azure のセキュリティのベスト プラクティス 2 - 人: クラウド セキュリティ テクノロジについてチームを教育する](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#2-people-educate-teams-on-cloud-security-technology)

- [Azure のセキュリティのベスト プラクティス 3 - プロセス: クラウドのセキュリティに関する意思決定のアカウンタビリティを割り当てる](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud)

**Azure Security Center の監視**: 適用なし

**責任**: Customer

### <a name="gs-5-define-network-security-strategy"></a>GS-5: ネットワーク セキュリティ戦略を定義する

**ガイダンス**:組織全体のセキュリティ アクセス制御戦略の一環として、Azure ネットワーク セキュリティ アプローチを確立します。  

この戦略には、次の要素に関する文書化されたガイダンス、ポリシー、標準が含まれている必要があります。 

-   一元的なネットワーク管理とセキュリティ責任

-   エンタープライズ セグメント化戦略と一致する仮想ネットワーク セグメント化モデル

-   さまざまな脅威と攻撃のシナリオにおける修復戦略

-   インターネット エッジとイングレスおよびエグレス戦略

-   クラウドとオンプレミスのハイブリッド相互依存戦略

-   最新のネットワーク セキュリティ成果物 (例: ネットワーク図、参照ネットワーク アーキテクチャ)

詳細については、次のリファレンスを参照してください。
- [Azure のセキュリティのベスト プラクティス 11 - アーキテクチャ。単一の統合セキュリティ戦略](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#11-architecture-establish-a-single-unified-security-strategy)

- [Azure セキュリティ ベンチマーク - ネットワーク セキュリティ](/azure/security/benchmarks/security-controls-v2-network-security)

- [Azure のネットワーク セキュリティの概要](https://docs.microsoft.com/azure/security/fundamentals/network-overview)

- [エンタープライズ ネットワーク アーキテクチャ戦略](https://docs.microsoft.com/azure/cloud-adoption-framework/ready/enterprise-scale/architecture)

**Azure Security Center の監視**: 適用なし

**責任**: Customer

### <a name="gs-6-define-identity-and-privileged-access-strategy"></a>GS-6: ID と特権アクセス戦略を定義する

**ガイダンス**:組織全体のセキュリティ アクセス制御戦略の一環として、Azure の ID と特権アクセス アプローチを確立します。  

この戦略には、次の要素に関する文書化されたガイダンス、ポリシー、標準が含まれている必要があります。 

-   一元化された ID と認証システム、および他の内部および外部 ID システムとのその相互接続

-   さまざまなユース ケースおよび条件における強力な認証方法

-   高い特権を持つユーザーの保護

-   異常なユーザー アクティビティの監視と処理  

-   ユーザー ID とアクセスの確認と調整のプロセス

詳細については、次のリファレンスを参照してください。

- [Azure セキュリティ ベンチマーク - ID 管理](https://docs.microsoft.com/azure/security/benchmarks/security-controls-v2-identity-management)

- [Azure セキュリティ ベンチマーク - 特権アクセス](/azure/security/benchmarks/security-controls-v2-privileged-access)

- [Azure のセキュリティのベスト プラクティス 11 - アーキテクチャ。単一の統合セキュリティ戦略](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#11-architecture-establish-a-single-unified-security-strategy)

- [Azure ID 管理のセキュリティの概要](https://docs.microsoft.com/azure/security/fundamentals/identity-management-overview)

**Azure Security Center の監視**: 適用なし

**責任**: Customer

### <a name="gs-7-define-logging-and-threat-response-strategy"></a>GS-7: ログ記録と脅威対応戦略を定義する

**ガイダンス**:コンプライアンス要件を満たしながら脅威を迅速に検出して修復するための、ログ記録と脅威対応戦略を確立します。 アナリストが、統合や手動による手順ではなく、脅威の対応に集中できるように、質の高いアラートとシームレスなエクスペリエンスを提供することを優先してください。 

この戦略には、次の要素に関する文書化されたガイダンス、ポリシー、標準が含まれている必要があります。 

-   セキュリティ運用 (SecOps) 組織の役割と責任 

-   NIST または他の業界フレームワークと一致する、明確に定義されたインシデント対応プロセス 

-   脅威の検出、インシデント対応、コンプライアンスのニーズに対応するためのログのキャプチャと保持

-   SIEM、Azure のネイティブ機能、その他のソースを使用した、脅威に関する情報の一元的な可視化と関連付け 

-   顧客、サプライヤー、および関心を持つパブリック パーティに関するコミュニケーションと通知の計画

-   ログ記録と脅威の検出、フォレンジクス、攻撃の修復と根絶など、インシデント処理に対する Azure ネイティブおよびサードパーティのプラットフォームの使用

-   インシデントとインシデント発生後のアクティビティを処理するためのプロセス (教訓や証拠の保持など)

詳細については、次のリファレンスを参照してください。

- [Azure セキュリティ ベンチマーク - ログと脅威検出](/azure/security/benchmarks/security-controls-v2-logging-threat-detection)

- [Azure セキュリティ ベンチマーク - インシデント対応](/azure/security/benchmarks/security-controls-v2-incident-response)

- [Azure のセキュリティのベスト プラクティス 4 - プロセス: クラウドのインシデント対応プロセスを更新する](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud)

- [Azure 導入フレームワーク、ログ、およびレポートの決定ガイド](https://docs.microsoft.com/azure/cloud-adoption-framework/decision-guides/logging-and-reporting/)

- [Azure のエンタープライズ スケーリング、管理、監視](https://docs.microsoft.com/azure/cloud-adoption-framework/ready/enterprise-scale/management-and-monitoring)

**Azure Security Center の監視**: 適用なし

**責任**: Customer

## <a name="next-steps"></a>次のステップ

- 「[Azure セキュリティ ベンチマーク V2 の概要](/azure/security/benchmarks/overview)」を参照してください。
- [Azure セキュリティ ベースライン](/azure/security/benchmarks/security-baselines-overview)の詳細について学習する
