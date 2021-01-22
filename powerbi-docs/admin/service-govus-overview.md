---
title: 米国政府顧客向け Power BI - 概要
description: 米国政府機関のお客様は、Power BI サブスクリプションを Microsoft 365 Government プランに追加できます。 このサービスの説明では、サインアップして接続し、利用可能な機能を確認する方法について説明します。
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 01/19/2021
ms.custom: gcc
LocalizationGroup: Get started
ms.openlocfilehash: e7100be7890673cecc77a8a1147a25a942fc4666
ms.sourcegitcommit: 96080432af4c8e3fe46c23274478ccffa0970efb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98597625"
---
# <a name="power-bi-for-us-government-customers"></a>米国政府顧客向け Power BI

この記事は、Microsoft 365 Government プランの一部として Power BI をデプロイする米国政府機関のお客様を対象としています。 Government プランは、米国のコンプライアンスとセキュリティ標準を満たする必要がある組織の固有のニーズに合うように設計されています。 米国政府機関のお客様向けに設計された Power BI サービスは、Power BI サービスの商用バージョンとは異なります。 これらの機能の相違点と能力について、以下のセクションで説明します。

## <a name="add-power-bi-to-your-microsoft-365-government-plan"></a>Microsoft 365 Government プランに Power BI を追加する

Power BI US Government サブスクリプションを取得してユーザーにライセンスを割り当てる前に、Microsoft 365 Government プランに登録する必要があります。 組織に既に Microsoft 365 Government プランがある場合は、「[政府機関のお客様向けの Power BI Pro サブスクリプションを購入する](#buy-a-power-bi-pro-subscription-for-government-customers)」に進んでください。

### <a name="enroll-in-a-microsoft-365-government-plan"></a>Microsoft 365 Government プランに登録する

新規のお客様は、Microsoft 365 Government プランにサインアップする前に、組織の資格を検証する必要があります。  [Microsoft 365 for Government 適格性検証フォーム](https://www.microsoft.com/microsoft-365/government/eligibility-validation)を完成させることから始めます。 組織に適したプランを確実に選択するには、[Microsoft 365 US Government サービスの説明](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/office-365-us-government)を参照してください。

> [!NOTE]
> Power BI を既に商用環境にデプロイ済みで、US Government クラウドに移行したい場合は、新しい Power BI Pro サブスクリプションを Microsoft 365 Government プランに追加する必要があります。 次に、米国政府向けの Power BI サービスに商用データをレプリケートし、商用ライセンスの割り当てをユーザー アカウントから削除してから、Power BI Pro Government ライセンスをユーザー アカウントに割り当てます。
>
>
### <a name="buy-a-power-bi-pro-subscription-for-government-customers"></a>政府機関のお客様向けの Power BI Pro サブスクリプションを購入する

Microsoft 365 のデプロイ後に、Power BI Pro サブスクリプションを追加できます。 [米国政府組織の登録](service-govus-signup.md)に関するページの詳細なガイダンスに従って、Power BI Pro Government サービスを購入します。 Power BI を使用する必要があるすべてのユーザーに割り当てできる数のライセンスを購入した後、ライセンスを個々のユーザー アカウントに割り当てます。

> [!IMPORTANT]
> Power BI US Government は、"*無料*" ライセンスとして利用することはできません。 Government Community Cloud にアクセスするには、各ユーザーに *Pro* ライセンスが割り当てられている必要があります。 ユーザー アカウントに無料ライセンスが割り当てられている場合、そのユーザーは商用クラウドへのアクセスのみが許可されるため、認証とアクセスの問題が発生します。 Power BI Premium を購入している場合は、ユーザー アクセスを有効にするために Pro ライセンスを割り当てる必要はありません。  組織内のユーザーは、レポートが Premium 容量に発行されている限り、ユーザー間で共有されているレポートにアクセスできます。 ライセンスの種類の違いを確認するには、「[Power BI サービスのライセンスの種類別機能](../fundamentals/service-features-license-type.md)」を参照してください。
>

## <a name="government-cloud-instances"></a>Government クラウドのインスタンス

Microsoft 365 には、政府機関のさまざまなコンプライアンス要件を満たすための複数の環境が用意されています。 各環境の詳細については、以下を参照してください。

* [Microsoft 365 Government Community Cloud (GCC)](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc) は、連邦政府、州政府、および地方自治体向けに設計されています。

* [Microsoft 365 Government Community Cloud High (GCC High)](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) は、連邦政府機関、軍需産業、航空宇宙産業、および機密扱いではないが統制している情報を保持しているその他の組織向けに設計されています。 この環境は、国際武器取引規則 (ITAR) のデータまたは国防省調達規則 (DFARS) に関する要件がある、国家安全保障に関わる組織と企業に適しています。

* [Microsoft 365 DoD 環境](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod)は、米国国防総省専用に設計されています。


## <a name="sign-in-to-power-bi-for-us-government"></a>米国政府向け Power BI にサインインする

Power BI に接続するための URL は、政府機関のユーザーと商用ユーザーの間で異なります。 Power BI にサインインするには、次の URL を使用します。

| 商用バージョン  | GCC  | GCC High | DoD |
| --- | --- | --- | --- |
| [https://app.powerbi.com/](https://app.powerbi.com) |[https://app.powerbigov.us](https://app.powerbigov.us) | [https://app.high.powerbigov.us](https://app.high.powerbigov.us) | [https://app.mil.powerbigov.us](https://app.mil.powerbigov.us) |

お使いのアカウントが、複数のクラウドで設定されている可能性があります。 アカウントがそのように設定されている場合は、Power BI Desktop にサインインするときに接続先のクラウドを選択できます。

## <a name="allow-connections-to-power-bi"></a>Power BI への接続を許可する

Power BI サービスを使用するには、インターネット上で必要なエンドポイントへの接続を許可する必要があります。 自分のネットワーク、Power BI、およびその他の依存サービスの間の通信を有効にするには、これらの宛先にアクセスできる必要があります。

次の表では、一般的なサイト使用目的で Power BI サービスへの接続を有効にするために、許可リストに追加する必要のあるエンドポイントを示します。 これらのエンドポイントは、米国政府のクラウドに固有のものです。 Power BI のサービスで必要なことは、リストに記載されているエンドポイントのために TCP ポート 443 を開いておくことだけです。 データの取得、ダッシュボードとレポートの統合、Power BI ビジュアル、およびその他のオプション サービスのエンドポイントは、米国政府のクラウドに固有のものではありません。 許可リストにこれらの URL も追加するには、「[Power BI URL を許可リストに追加する](power-bi-whitelist-urls.md)」を参照してください。

Power BI の認証、ID、管理は、Microsoft 365 サービスへの接続に依存します。 また、監査ログを表示するには Microsoft 365 に接続する必要があります。 これらのサービスのエンドポイントを識別するには、次の表の「Microsoft 365 統合」を参照してください。

### <a name="power-bi-urls-for-general-site-usage"></a>一般的なサイト使用のための Power BI URL

|  目的 | 宛先 |
| ---- | ----- |
| バックエンド API | **GCC**: api.powerbigov.us |
| | **GCC-High**: api.high.powerbigov.us |
| | **DoD**: api.mil.powerbi.gov.us |
| バックエンド API | **GCC**: *analysis.usgovcloudapi.net |
| | **GCC High**: *.high.analysis.usgovcloudapi.net |
| | **DoD**: *.mil.analysis.usgovcloudapi.net |
| バックエンド API | **すべて**: *.pbidedicated.usgovcloudapi.net |
| Content Delivery Network (CDN) | **GCC**: gov.content.powerapps.us |
| | **GCC High**: high.content.powerapps.us |
| | **DoD**: mil.content.powerapps.us |
| Microsoft 365 の統合 | **GCC**:[ワールドワイド エンドポイント](/microsoft-365/enterprise/urls-and-ip-address-ranges) |
| | **GCC High**:[US Government GCC High エンドポイント](/microsoft-365/enterprise/microsoft-365-u-s-government-gcc-high-endpoints) |
| | **DoD**:[US Government DOD エンドポイント](/microsoft-365/enterprise/microsoft-365-u-s-government-dod-endpoints) |
| ポータル |**GCC**: *.powerbigov.us |
| | **GCC-High**: *.high.powerbigov.us |
| | **DoD**: *.mil.powerbigov.us |
| サービスの利用統計情報 | **すべて**: dc.services.visualstudio.us |
| 情報メッセージ (省略可) | **すべて**: dynmsg.modpim.com |
| NPS 調査 (省略可) | **すべて**: nps.onyx.azure.net |

## <a name="connect-government-and-global-azure-cloud-services"></a>行政機関向け Azure クラウド サービスとグローバルな Azure クラウド サービスに接続する

Azure は複数のクラウドに分散されています。 既定では、クラウド固有のインスタンスへの接続を開くファイアウォール規則を有効にすることができますが、クラウド間ネットワークはこれとは異なります。  パブリック クラウド内のサービスと Government Community Cloud 内のサービスの間で通信を行うには、固有のファイアウォール規則を構成する必要があります。 たとえば、Power BI の政府機関向けクラウドのデプロイから SQL データベースのパブリック クラウド インスタンスにアクセスする場合は、SQL データベースのファイアウォール規則が必要です。 次のデータセンターの Azure Government クラウドへの接続を許可するには、SQL データベースの固有のファイアウォール規則を構成します。

* USGov アイオワ州
* USGov バージニア州
* USGov テキサス
* USGov アリゾナ
* US DoD East
* US DoD Central

US Government クラウドの IP 範囲を取得するには、「[Azure IP 範囲とサービス タグ - US Government クラウド](https://www.microsoft.com/download/details.aspx?id=57063)」でファイルをダウンロードしてください。 範囲は Power BI と Power Query の両方に対して示されます。

Microsoft Azure Government クラウド サービスの詳細については、[Azure Government のドキュメント](/azure/azure-government/)を参照してください。

SQL データベースのファイアウォールを設定するには、「[IP ファイアウォール規則の作成および管理](/azure/sql-database/sql-database-firewall-configure#create-and-manage-ip-firewall-rules)」を参照してください。

## <a name="power-bi-feature-availability"></a>Power BI の機能の利用可能性

Government クラウドのお客様の要件に対応するため、Government プランと商用プランにはいくつかの違いがあります。 私たちの目標は、一般提供から 30 日以内に、すべての機能を政府機関向けクラウドで使用できるようにすることです。 場合によっては、基になる依存関係によって機能が使用できなくなることがあります。 以下の一覧は、特定の政府環境ではまだ利用できない機能や、機能が制限されている機能を示しています。 この一覧では、次のキーが使用されています。

|Key |説明|
|-----|------|
|![利用可能](../media/yes.png)|この機能は、脚注で定義されている例外を除いて、この環境で使用できます。|
|![利用不可](../media/no.png)| この機能は、この環境では使用できません。また、配信時期の予定もありません。|

環境に対してリリースが予定されている場合は、公開予定時期の四半期を含めています。

|特徴 |GCC |GCC High |DoD|
|------|------|------|------|
|[政府機関と商用クラウド間の Azure B2B コラボレーション](service-admin-azure-ad-b2b.md)<sup>1</sup>|![利用可能](../media/yes.png)|![利用可能](../media/yes.png)|![利用可能](../media/yes.png)
|[テンプレート アプリ](../connect-data/service-template-apps-overview.md)<sup>2</sup>|![利用可能](../media/yes.png) |![利用可能](../media/yes.png)| ![利用可能](../media/yes.png)|
|[Power BI Web パーツを使用した SharePoint Online への埋め込み](/sharepoint/dev/spfx/web-parts/overview-client-side-web-parts)|![利用可能](../media/yes.png)|![利用可能](../media/yes.png)|![利用不可](../media/no.png)|
|[データ保護 (MIP ラベル)](service-security-sensitivity-label-overview.md)|![利用可能](../media/yes.png)|![利用可能](../media/yes.png) |2021 年第 1 四半期|
|[データフロー - 直接クエリ](../transform-model/dataflows/dataflows-configure-consume.md) | ![利用可能](../media/yes.png) |![利用可能](../media/yes.png)|未定 |
|[Teams での [Power BI] タブ](../collaborate-share/service-collaborate-microsoft-teams.md)<sup>3</sup>|![利用可能](../media/yes.png)|![利用不可](../media/no.png)|![利用不可](../media/no.png)|
|[大規模なモデル](service-premium-large-models.md) | 2021 年第 1 四半期 |2021 年第 1 四半期| 未定 |
|[データフロー - SQL コンピューティング エンジンの最適化](../transform-model/dataflows/dataflows-premium-features.md) | ![利用不可](../media/no.png) |![利用不可](../media/no.png)| ![利用不可](../media/no.png) |
|[Call Quality Data Connector](/microsoftteams/cqd-power-bi-connector)|![利用不可](../media/no.png)|![利用不可](../media/no.png)|![利用不可](../media/no.png)|
|[ストレージ持ち込み (Azure Data Lake Gen 2)](../transform-model/dataflows/dataflows-azure-data-lake-storage-integration.md)|![利用不可](../media/no.png)|![利用不可](../media/no.png)|![利用不可](../media/no.png)|

<sup>1</sup> B2B コラボレーションは GCC で利用できますが、その環境でのライセンスを外部ユーザーに発行する必要があります。 商用クラウド ライセンスは GCC では無効です。 米国政府機関向け B2B コラボレーションの既知の制限に関する詳細については、「[Azure Government とグローバル Azure の比較](/azure/azure-government/compare-azure-government-global-azure#azure-active-directory-premium-p1-and-p2)」を参照してください。

<sup>2</sup> Marketplace アプリが米国政府向けクラウド インスタンスでは使用できないため、テンプレート アプリはプライベートおよび組織アプリに限定されます。

<sup>3</sup> GCC 用の Teams の Power BI エクスペリエンスは限られており、従来のワークスペースでのみ機能します。また、「[Microsoft Teams に Power BI コンテンツを埋め込む](../collaborate-share/service-embed-report-microsoft-teams.md)」で説明されている拡張機能は含まれていません。

## <a name="next-steps"></a>次の手順

* [米国政府向け Power BI へのサインアップ](service-govus-signup.md)
* [Microsoft Power Apps US Government](/power-platform/admin/powerapps-us-government)
* [Power Automate US Government](/power-automate/us-govt)
* [米国政府向け Power BI のデモ](https://channel9.msdn.com/Blogs/Azure/Cognitive-Services-HDInsight-and-Power-BI-on-Azure-Government)
