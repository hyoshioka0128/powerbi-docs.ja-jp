---
title: Power BI 埋め込み分析についてよく寄せられる質問
description: Power BI 埋め込み分析についてよく寄せられる質問とその回答の一覧を参照します
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 01/14/2021
ms.openlocfilehash: dc67cabfdb7fcceab202b607e144c7c99f092bf0
ms.sourcegitcommit: 13a150d1aa810f309421bf603fa8581718a4b299
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "101842011"
---
# <a name="frequently-asked-questions-about-power-bi-embedded"></a>Power BI Embedded に関してよく寄せられる質問

* 他の質問がある場合は、[Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
* それでも解決しない場合は、 [Power BI のサポート ページ](https://powerbi.microsoft.com/support/)をご覧ください。

## <a name="general"></a>全般

### <a name="what-is-power-bi-embedded"></a>Power BI Embedded とは何ですか?

[Microsoft Power BI Embedded (PBIE)](azure-pbie-what-is-power-bi-embedded.md) を利用すれば、アプリケーション開発者は、完全にインタラクティブな優れたレポートをアプリケーションに埋め込むことができます。データの視覚エフェクトやコントロールを自分で一から構築する必要はありません。

### <a name="who-is-the-target-audience-for-power-bi-embedded"></a>Power BI Embedded の対象者は誰ですか?

アプリケーションをコーディングしている開発者やソフトウェア企業です。独立系ソフトウェア ベンダー (ISV) とも呼ばれます。

### <a name="how-is-power-bi-embedded-different-from-power-bi-the-service"></a>Power BI Embedded と Power BI サービスの違いは何ですか?

Power BI は、サービスとしてのソフトウェアの分析ソリューションです。組織はその最も重要なビジネス データを 1 つのビューで見ることができます。

Microsoft は、顧客が分析に関する決定を行うときに役立つビジュアルをアプリケーションに埋め込もうと考えている ISV のために Power BI Embedded を開発しました。 これにより、ISV は独自の分析ソリューションを自分で構築する必要がなくなります。 [埋め込み分析](embedding.md)を使用すると、ビジネス ユーザーはビジネス データにアクセスしてクエリを実行し、アプリケーション内で分析情報を生成できます。

### <a name="what-is-the-difference-between-power-bi-premium-and-power-bi-embedded"></a>Power BI Premium と Power BI Embedded の違いは何ですか?

Power BI Premium は、組織、パートナー、顧客、サプライヤーを 1 つのビューで見ることができる完全 BI ソリューションを望む企業向けです。 Power BI Premium は組織の意思決定に役立ちます。 Power BI Premium は SaaS 製品であり、ユーザーはモバイル アプリ、社内で開発したアプリを使用して、または Power BI ポータルでコンテンツを利用できます。

Power BI Embedded は、アプリケーションにビジュアルを埋め込むことを望む ISV 用です。 Power BI Embedded はアプリケーション開発者向けであり、そのアプリケーションを入手すれば、組織の内外を問わず、誰でも Power BI Embedded 容量に保存されているコンテンツを利用できます。Power BI Embedded は顧客の意思決定に役立ちます。 Power BI Embedded 容量に入っているコンテンツを、ワンクリック Web 公開やワンクリック SharePoint 公開で共有することはできません。

### <a name="what-is-power-bi-embedded-generation-2"></a>Power BI Embedded Generation 2 とは

最近、Power BI Embedded では新しいバージョン **Embedded Gen2** がリリースされました。 Embedded Gen2 を使用すると、埋め込み容量の管理が簡素化され、Power BI Embedded エクスペリエンスが向上します。 詳細については、[Power BI Embedded Generation 2](power-bi-embedded-generation-2.md) に関する記事を参照してください。

### <a name="what-is-the-microsoft-recommendation-for-when-a-customer-should-buy-power-bi-premium-vs-power-bi-embedded"></a>Power BI Premium と Power BI Embedded を比較して、どのような状況でどちらを購入するべきか、Microsoft は勧めていますか?

Microsoft は、企業に、エンタープライズ グレードのセルフサービス クラウド BI ソリューションである Power BI Premium を購入することをお勧めします。 ISV には、クラウドを利用した埋め込み分析コンポーネント用に Power BI Embedded の購入をお勧めします。 ただし、お客様が購入する製品に制限はありません。

ISV (通常は大規模) が、アプリの埋め込みに加えて、P SKU を使用し、事前パッケージ済みの Power BI サービスのメリットを組織内でさらに利用する場合もあります。 基幹業務アプリケーションを開発し、それに分析を埋め込みたいが、事前パッケージ済み Power BI サービスは必要としない企業が Azure の A SKU の利用を決める場合もあります。

### <a name="how-many-embed-tokens-can-i-create"></a>埋め込みトークンはいくつ作成できますか?

PRO ライセンスでの埋め込みトークンは、開発テストを意図したものであるため、Power BI マスター アカウントまたは[サービス プリンシパル](embed-service-principal.md)で生成できるトークンの数には制限があります。 運用環境で埋め込むには、[容量を購入](#technical)してください。 容量を購入する場合、生成できる埋め込みトークンの数に上限はありません。 現在の埋め込み使用パーセンテージを示す使用状況の値を確認するには、[使用可能な機能](/rest/api/power-bi/availablefeatures)に関するページに移動します。

## <a name="technical"></a>技術的な質問

### <a name="where-can-i-learn-more-about-capacity-and-skus-in-power-bi-embedded-analytics"></a>Power BI Embedded の分析の容量と SKU に関する詳細は、どこで確認できますか?

「[Power BI Embedded の分析の容量と SKU](embedded-capacity.md)」の記事を参照してください。

### <a name="what-are-the-prerequisites-for-creating-a-pbie-capacity-in-azure"></a>Azure で PBIE 容量を作成するための前提条件は何ですか?

* 組織のディレクトリにサインインします (Microsoft アカウントはサポートされていません)。
* Power BI テナントを用意する必要があります。つまり、ディレクトリの少なくとも 1 名のユーザーが Power BI にサインアップしている必要があります。 
* 組織のディレクトリに Azure サブスクリプションを用意する必要があります。

### <a name="how-can-i-monitor-power-bi-embedded-capacity-consumption"></a>Power BI Embedded の容量の消費はどのように監視できますか?

* [Power BI 管理ポータル](../../admin/service-admin-portal.md#power-bi-embedded)を使用します。

* Power BI で [metric app](../../admin/service-admin-premium-monitor-capacity.md) をダウンロードします。

* [Azure 診断ログ](./monitor-power-bi-embedded.md)を使用します。

### <a name="can-my-capacity-scale-automatically-to-adjust-to-my-app-consumption"></a>自分のアプリでの消費に合わせて調整するように容量を自動的にスケーリングできますか?

現在、自動的なスケーリングはありませんが、いつでもすべての API をスケーリングに利用できます。

### <a name="why-creatingscalingresuming-a-capacity-results-in-putting-the-capacity-into-a-suspended-state"></a>容量を作成、拡張、再開すると、容量が中断状態になります。なぜでしょうか?

容量のプロビジョニング (拡張、再開、作成) は失敗することがあります。 Get Details API を使って、容量の ProvisioningState を確認できます。[Capacities - Get Details](/rest/api/power-bi-embedded/capacities/getdetails) を使用します。

### <a name="can-i-only-create-power-bi-embedded-capacities-in-a-specific-region"></a>Power BI Embedded 容量は、特定のリージョンのみでしか使用できませんか?

[Multi-geo (プレビュー)](embedded-multi-geo.md) 機能では、Power BI ホーム テナントの場所とは異なるリージョンで [Power BI Embedded 容量](azure-pbie-create-capacity.md)を購入できます。

### <a name="why-cant-i-see-a-workspace-although-i-have-permissions"></a>アクセス許可があるのにワークスペースを表示できないのはなぜですか?

ユーザーがワークスペース、アプリ、または成果物へのアクセス許可を付与されても、API 呼び出しですぐに利用できない場合があります。
結果として、"GET" API の応答に成果物が含まれていなかったり、成果物を使おうとするとエラーが発生したりする可能性があります。
ユーザーは、ユーザーのアクセス許可を更新する [refreshUserPermissions API](/rest/api/power-bi/users/refreshuserpermissions) を呼び出すことによって、この問題を解決できます。


### <a name="how-can-i-find-my-pbi-tenant-region"></a>自分の PBI テナント リージョンを確認する方法はありますか?

PBI ポータルを使って、PBI テナント リージョンを確認できます。

`https://app.powerbi.com/` > ? > Power BI について

![Power BI について](media/embedded-faq/about-01.png)
![テナント リージョン](media/embedded-faq/tenant-location-01.png)

### <a name="what-does-the-cloud-solution-provider-csp-channel-support"></a>クラウド ソリューション プロバイダー (CSP) チャネルでは何がサポートされていますか?

* サブスクリプションの種類が CSP の場合、ご自身のテナントに対して PBIE を作成できます。
* パートナー アカウントは顧客テナントにサインインし、顧客テナントの代わりに PBIE を購入し、Power BI 容量の管理者として顧客テナント ユーザーを指定できます。

### <a name="why-do-i-get-an-unsupported-account-message"></a>アカウントがサポートされていませんというメッセージを受け取るのはなぜですか?

Power BI では、組織のアカウントでサインアップすることが求められます。 Microsoft アカウントを使って Power BI にサインアップする試みはサポートされていません。

### <a name="can-i-use-apis-to-create-and-manage-azure-capacities"></a>API を使って Azure の容量を作成し、管理することはできますか?

はい。PowerShell コマンドレットや Azure Resource Manager REST API を使用して、PBIE リソースを作成および管理できます。

* [REST API](/rest/api/power-bi-embedded/) 
* [PowerShell コマンドレット](/powershell/module/azurerm.powerbiembedded/)

### <a name="what-is-the-pbi-embedded-capacity-role-in-a-pbi-embedded-solution"></a>PBI Embedded ソリューションでは、PBI Embedded 容量はどのような役割を果たしますか?

[ソリューションを運用に昇格させる](move-to-production.md)には、アプリケーションで使う Power BI コンテンツ (ワークスペース) を、Power BI Embedded (A SKU) 容量に割り当てる必要があります。

### <a name="in-what-azure-regions-is-pbi-embedded-available"></a>PBI Embedded はどの Azure リージョンで利用できますか?

[PAM](https://ecosystemmanager.azurewebsites.net/home) (EcoManager) - Product Availability Manager を参照してください

利用できるリージョン (16 - Power BI と同じリージョン)

* 米国 (6) - 米国東部、米国東部 2、米国中北部、米国中南部、米国西部、米国西部 2
* ヨーロッパ (2) - 北ヨーロッパ、西ヨーロッパ
* アジア太平洋 (2) - 東南アジア、東アジア
* ブラジル (1) - ブラジル南部
* 日本 (1) - 東日本
* オーストラリア (1) - オーストラリア南東部
* インド (1) - インド西部
* カナダ (1) - カナダ中部
* 英国 (1) - 英国南部

### <a name="what-is-power-bi-embeddeds-authentication-model"></a>Power BI Embedded の認証モデルは何ですか?

Power BI Embedded では引き続き、マスター ユーザー (Power BI Pro のライセンスが与えられた指名ユーザー) の認証には Azure AD が使用され、Power BI 内のアプリケーションの認証には[サービス プリンシパル](embed-service-principal.md)が使用されます。  

 ISV は、アプリケーション用に独自の認証と認可を実装できます。

Azure AD テナントが既にある場合は、既存のディレクトリを使用できます。 埋め込みアプリケーション コンテンツのセキュリティ用に新しい Azure AD テナント作成することもできます。

AAD トークンを取得するには、[Azure Active Directory 認証ライブラリ](/azure/active-directory/develop/active-directory-authentication-libraries)のいずれかを使用できます。 複数のプラットフォームで利用可能なクライアント ライブラリがあります。

### <a name="my-application-already-uses-aad-for-user-authentication-how-can-we-use-this-identity-when-authenticating-to-power-bi-in-a-user-owns-data-scenario"></a>私はアプリケーションのユーザー認証に AAD を既に使用しています。 "ユーザーがデータを所有する" シナリオでは、Power BI に認証するとき、この ID をどのように利用できますか?

それは標準的な OAuth 代理フローです (<https://docs.microsoft.com/azure/active-directory/develop/web-api>)。 (必要なスコープの) Power BI サービスのアクセス許可を要求するようにアプリケーションを構成する必要があります。 アプリのユーザー トークンを入手したら、ユーザー アクセス トークンを使って ADAL API の AcquireTokenAsync を単に呼び出し、リソース ID として Power BI リソース URL を指定します。

```csharp
var context = new AD.AuthenticationContext(authorityUrl);
var userAssertion = new AD.UserAssertion(userAccessToken);
var clientAssertion = new AD.ClientAssertionCertificate(MyAppId, MyAppCertificate)
var authenticationResult = await context.AcquireTokenAsync(resourceId, clientAssertion, userAssertion);
```

### <a name="what-object-id-is-the-service-principal-object-id"></a>サービス プリンシパル オブジェクト ID はどのようなオブジェクト ID ですか?

登録済みアプリのメイン画面の "*オブジェクト ID*" が、アプリのオブジェクト ID です。

*[ローカル ディレクトリでのマネージド アプリケーション] > [プロパティ]* セクションで示されているオブジェクト ID が、使用する必要のあるサービス プリンシパル オブジェクト ID です。 このオブジェクト ID は、操作に対するサービス プリンシパルを参照するため、またはサービス プリンシパル オブジェクト ID を変更するためのものです。 ワークスペースに対する管理者としてのサービス プリンシパルの割り当てなどです。

### <a name="how-is-power-bi-embedded-different-from-other-azure-services"></a>Power BI Embedded とその他の Azure サービスの違いは何ですか?

Azure で Power BI Embedded を購入する前に、Power BI アカウントを用意する必要があります。 Power BI Embedded がデプロイされているリージョンによって、Power BI アカウントが決まります。 Azure の Power BI Embedded リソースを次の目的で管理します。

* 拡大/縮小
* 容量管理者の追加
* サービスの一時停止/再開

PowerBI.com を利用し、Power BI Embedded 容量のワークスペースの割り当て/割り当て解除を行います。

### <a name="what-content-pack-data-types-can-you-embed"></a>埋め込むことができるコンテンツ パック データの種類は何ですか?

コンテンツ パック データセットから構築された **ダッシュボード** と **タイル** を埋め込むことは "*できません*"。 ただし、コンテンツ パック データセットから構築された **レポート** を埋め込むことは "*できます*"。

### <a name="what-is-the-difference-between-using-row-level-security-rls-vs-javascript-filters"></a>行レベルセキュリティ (RLS) の使用とJavaScript のフィルターの違いは何ですか?

RLS と JavaScript フィルターをどのようなときに使うのかについて、しばしば混乱があります。1 つは特定のユーザーが表示できるものの制御に関する方法であり、もう 1 つはユーザーの表示の最適化に関するものであるためです。

RLS の場合、ISV の開発者が、モデルの作成と埋め込みトークンの生成の一部として、データのフィルター処理を制御します。 エンド ユーザーには、ISV によって表示が許可されているもののみが表示されます。 この場合、ユーザーはフィルター処理されているものより少なく表示することはできますが、RLS の構成をバイパスして許可されているものよりも多く表示することはできません。

クライアント側のフィルター処理 (JavaScript) の場合、ISV では最初のビューでエンド ユーザーに表示されるものを決める場合はありますが、ISV ではエンドユーザーがビュー自体に適用する可能性がある変更を制御することはできません。 ユーザーの JavaScript クライアント コードでバックエンドでのデータのフィルター処理をトリガーできるため、それは安全とは見なされません。

詳細については、[RLS と JavaScript のフィルター](embedded-row-level-security.md#using-rls-vs-javascript-filters)に関するページをご覧ください。

### <a name="how-do-i-manage-permissions-for-service-principals-with-power-bi"></a>Power BI では、どのような方法でサービス プリンシパルのアクセス許可を管理しますか?

Power BI で[サービス プリンシパル](embed-service-principal.md)を使用できるようにすると、アプリケーションの AD アクセス許可は無効になります。 アプリケーションのアクセス許可はその後、Power BI 管理ポータルを介して管理されます。

サービス プリンシパルは、対象セキュリティ グループの Power BI テナントのすべての設定のアクセス許可を継承します。 アクセス許可を制限するには、サービス プリンシパル専用のセキュリティ グループを作成し、関連する有効な Power BI 設定の **[特定のセキュリティ グループを除く]** リストに追加します。

このような状況は、新しいワークスペースに **管理者** としてサービス プリンシパルを追加するときに問題となります。 このタスクは [API](/rest/api/power-bi/groups/addgroupuser) または Power BI サービスを使用して管理できます。

### <a name="when-to-use-an-application-id-vs-a-service-principal-object-id"></a>アプリケーション ID とサービス プリンシパル オブジェクト ID はそれぞれどのような状況で使用しますか?

**[アプリケーション ID](embed-sample-for-customers.md#client-id)** ("*クライアント ID*" とも呼ばれます) は、認証のためにアプリケーション ID を渡すときに、アクセス トークンを作成する目的で使用されます。

ワークスペースに管理者としてサービス プリンシパルを適用するなど、サービス プリンシパルを各種操作または変更のために参照するには、 **[サービス プリンシパル オブジェクト ID](embed-service-principal.md)** を使用します。

### <a name="can-you-manage-an-on-premises-data-gateway-with-service-principal"></a>サービス プリンシパルでオンプレミス データ ゲートウェイを管理できますか?

マスター アカウントの場合のようにオンプレミス データ ゲートウェイ (データ ゲートウェイ) を管理することは、[サービス プリンシパル](embed-service-principal.md)ではできません。

マスター アカウントを利用すれば、データ ゲートウェイをインストールし、そのゲートウェイにユーザーを追加したり、データ ソースに接続したり、その他の管理タスクを実行したりできます。

サービス プリンシパルを利用すれば、SQL Server Analysis Services (SSAS) オンプレミス ライブ接続データ ソースを使用し、[行レベルセキュリティ (RLS)](embedded-row-level-security.md#on-premises-data-gateway-with-service-principal) を構成できます。 サービス プリンシパルを使用して **Power BI Embedded** と統合するとき、SSAS でユーザーとデータへのユーザー アクセスをこの方法で管理できます。

### <a name="can-you-sign-into-the-power-bi-service-with-service-principal"></a>サービス プリンシパルで Power BI サービスにサインインできますか?

いいえ - サービス プリンシパルを使用して Power BI にサインインすることはできません。

また、埋め込みトークンの生成時のみ、外部アプリケーション (SaaS 埋め込み) でユーザーとしてコンテンツを利用できません。

### <a name="what-are-the-best-practices-to-improve-performance"></a>パフォーマンスを向上するベスト プラクティスについては、次を参照してください。

[Power BI Embedded のパフォーマンス](embedded-performance-best-practices.md)

## <a name="licensing"></a>ライセンス

### <a name="how-do-i-purchase-power-bi-embedded"></a>Power BI Embedded の購入方法は?

Power BI Embedded は Azure からお買い求めいただけます。

### <a name="what-happens-if-i-already-purchased-power-bi-premium-and-now-i-want-some-power-bi-embedded-in-azure-benefits"></a>Power BI Premium を既に購入しているとき、Azure ベネフィットで Power BI Embedded の一部を利用したいと考えた場合、どうなりますか?

コンシューマーは、購入した既存の Power BI Premium を現在の契約期間の終了まで支払い続け、その時点で必要に応じて購入した Power BI Premium を切り替えることができます。

### <a name="do-i-still-have-to-buy-power-bi-premium-to-get-access-to-power-bi-embedded"></a>Power BI Embedded にアクセスするには Power BI Premium を購入する必要がありますか?

いいえ。Power BI Embedded には、ソリューションをデプロイし、顧客に配信するために必要な Azure ベースの容量が含まれています。

### <a name="whats-the-purchase-commitment-for-power-bi-embedded"></a>Power BI Embedded の購入コミットメントは何ですか?

顧客は時間単位で使用方法を変更できます。 Power BI Embedded サービスには、月または年単位のコミットメントはありません。

### <a name="how-does-the-usage-of-power-bi-embedded-show-up-on-my-bill"></a>Power BI Embedded の使用状況は請求書にどのように表示されますか?

Power BI Embedded は、デプロイしたノードの種類に基づき、予測可能な時間レートで課金されます。 リソースが有効である限り、使用していなくても課金されます。 課金を停止するには、リソースを一時停止する必要があります。

### <a name="who-needs-a-power-bi-pro-license-for-power-bi-embedded-and-why"></a>Power BI Embedded に Power BI Pro のライセンスを必要とするのはどのようなユーザーですか? また、その理由は?

REST API を使うには、Power BI Pro ライセンスまたは[サービス プリンシパル](embed-service-principal.md)が必要です。 アナリストが Power BI ワークスペースにレポートを追加するには、Power BI Pro のライセンスまたはサービス プリンシパルが必要です。 管理者が Power BI のテナントと容量を管理するには、Power BI Pro のライセンスが必要です。

Power BI Embedded では、埋め込みコンテンツの管理と検証に Power BI ポータルを利用できるため、PowerBI.com 内でアプリを認証し、正しいリポジトリのレポートにアクセスするには、Power BI Pro ライセンスが必要です。

ただし、自分のアプリケーション内で[埋め込みレポートを作成または編集する](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Create-Report-in-Embed-View)場合、エンド ユーザーは Power BI ユーザーである必要がないため、Pro ライセンスは必要ありません。

### <a name="can-i-get-started-for-free"></a>無料で始めることはできますか?

はい。Power BI Embedded の [Azure クレジット](https://azure.microsoft.com/free/)をご利用いただけます。

### <a name="can-i-get-a-trial-experience-for-power-bi-embedded-in-azure"></a>Azure で Power BI Embedded を試してみることはできますか?

Power BI Embedded は Azure の一部であるため、[Azure 登録時に受け取った $200 のクレジット](https://azure.microsoft.com/free/)を使ってサービスを利用することが可能です。

### <a name="is-power-bi-embedded-available-for-national-clouds-us-government-germany-china"></a>Power BI Embedded は国内クラウド (米国政府、ドイツ、中国) に利用できますか?

Power BI Embedded は[国内クラウド](embed-sample-for-customers-national-clouds.md)にも利用できます。

### <a name="is-power-bi-embedded-available-for-non-profits-and-educational"></a>非営利団体や教育機関は Power BI Embedded を利用できますか?

非営利団体や教育機関のための特別な Azure 料金はありません。

## <a name="power-bi-workspace-collection"></a>Power BI ワークスペース コレクション

### <a name="what-is-power-bi-workspace-collection"></a>Power BI ワークスペース コレクションとは何ですか?

**Power BI ワークスペース コレクション** (**Power BI Embedded** バージョン 1) は、**Power BI ワークスペース コレクション** Azure リソースに基づくソリューションです。 このソリューションを利用すると、**Power BI ワークスペース コレクション** ソリューションの下にある Power BI コンテンツ、専用 API、および Power BI に対してアプリケーションを認証するワークスペース コレクション キーを使って、顧客向けの **Power BI Embedded** アプリケーションを作成できます。

### <a name="can-i-migrate-from-power-bi-workspace-collection-to-power-bi-embedded"></a>Power BI ワークスペース コレクションから Power BI Embedded に移行できますか?

1. 移行ツールを使って、**Power BI ワークスペース コレクション** のコンテンツを Power BI に複製できます https://docs.microsoft.com/power-bi/developer/migrate-from-powerbi-embedded#content-migration 。

2. Power BI のコンテンツを使用する **Power BI Embedded** アプリケーション POC から始めます。

3. 運用する準備ができたら、**Power BI Embedded** の容量を購入し、その容量に Power BI のコンテンツ (ワークスペース) を割り当てます。

    > [!Note]
    > **Power BI Embedded** ソリューションを使って開発を行いながら、並行して **Power BI ワークスペース コレクション** を使い続けることができます。 準備ができたら、顧客を新しい **Power BI Embedded** ソリューションに移動し、**Power BI ワークスペース コレクション** ソリューションの使用を終了します。

詳しくは、「[Power BI Embedded に Power BI ワークスペース コレクション コンテンツを移行する方法](./migrate-from-powerbi-embedded.md)」をご覧ください。

### <a name="is-power-bi-workspace-collection-on-a-deprecation-path"></a>Power BI ワークスペース コレクションは非推奨パス上にありますか?

はい。ただし、**Power BI ワークスペース コレクション** ソリューションを既に使っているお客様は、非推奨になるまで引き続き使用できます。 お客様は、新しいワークスペース コレクション、および **Power BI ワークスペース コレクション** ソリューションをまだ使用する **Power BI Embedded** アプリケーションを作成することもできます。

ただし、これはどの **Power BI ワークスペース コレクション** ソリューションにも新しい機能が追加されないことも意味します。 お客様には、新しい **Power BI Embedded** ソリューションへの移行を計画することをお勧めします。

### <a name="when-is-power-bi-workspace-collection-support-discontinued"></a>Power BI ワークスペース コレクションのサポートはいつ終了しますか?

既に **Power BI ワークスペース コレクション** ソリューションを使っているお客様は、2018年 6 月末まで、またはサポート契約が終了するまで、引き続き使用できます。

### <a name="in-what-regions-can-i-create-a-pbi-workspace-collection"></a>PBI ワークスペース コレクションを作成できるリージョンはどこですか?

使用できるリージョンは、オーストラリア南東部、ブラジル南部、カナダ中部、米国東部 2、東日本、米国中北部、北ヨーロッパ、米国中南部、東南アジア、英国南部、西ヨーロッパ、インド西部、米国西部です。

### <a name="why-should-i-migrate-from-pbi-workspace-collection-to-power-bi-embedded"></a>PBI ワークスペース コレクションから Power BI Embedded に移行しなければならないのはなぜですか?

**Power BI Embedded** ソリューションには、**Power BI ワークスペース コレクション** では使用できない新機能がいくつかあります。

次のような機能です。
* PBI データ ソースはすべてサポートされています。 **Power BI ワークスペース コレクション** データ ソースは、2 つだけサポートされています。 
* Q&A、更新、ブックマーク、ダッシュボードとタイルの埋め込み、カスタム メニューなどの新機能は、**Power BI Embedded** ソリューションでのみサポートされます。
* 容量の課金モデル。

## <a name="embedding-setup-tool"></a>埋め込みセットアップ ツール

### <a name="what-is-the-embedding-setup-tool"></a>埋め込みのセットアップ ツールとは

[埋め込みのセットアップ ツール](https://app.powerbi.com/embedsetup)を使うと、サンプル アプリケーションを簡単にダウンロードして Power BI で埋め込みを開始することができます。

### <a name="which-solution-should-i-choose"></a>選択するソリューション

* [顧客向けの埋め込み](embedding.md#embedding-for-your-customers)では、Power BI のアカウントがないユーザーのためにダッシュボードとレポートを埋め込むことができます。 [埋め込みセットアップ ツール](https://app.powerbi.com/embedsetup)で、"*顧客向けの埋め込み*" ソリューションを実行します。
* [組織向けの埋め込み](embedding.md#embedding-for-your-organization)を使って、Power BI サービスを拡張することができます。 [埋め込みセットアップ ツール](https://app.powerbi.com/embedsetup)で、"*組織向けに埋め込む*" ソリューションを実行します。

### <a name="ive-downloaded-the-sample-app-which-solution-do-i-choose"></a>ダウンロードしたサンプル アプリのどのソリューションを選択するか

**顧客向けの埋め込み** エクスペリエンスを使用している場合、*PowerBI-Developer-Samples.zip* ファイルを保存して解凍します。 その後、*PowerBI-Developer-Samples-master\App Owns Data* フォルダーを開き、*PowerBIEmbedded_AppOwnsData.sln* ファイルを実行します。

**組織向けの埋め込み** エクスペリエンスを使用している場合、*PowerBI-Developer-Samples.zip* ファイルを保存して解凍します。 *PowerBI-Developer-Samples-master\User Owns Data\integrate-report-web-app* フォルダーを開き、*pbi-saas-embed-report.sln* ファイルを実行します。

### <a name="how-can-i-edit-my-registered-application"></a>登録済みアプリケーションを編集する方法

AAD 登録済みアプリケーションの編集方法については、「[クイック スタート:Azure Active Directory のアプリケーションを更新する](/azure/active-directory/develop/quickstart-v1-update-azure-ad-app)」をご覧ください。

### <a name="how-can-i-edit-my-power-bi-user-profile-or-data"></a>Power BI ユーザー プロファイルまたはデータを編集する方法

Power BI データの編集方法は、[こちら](../../fundamentals/service-basic-concepts.md)をご覧ください。

詳しくは、「[埋め込みアプリケーションのトラブルシューティング](embedded-troubleshoot.md)」をご覧ください。

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。