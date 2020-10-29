---
title: Azure Active Directory B2B を使用して外部ゲスト ユーザーに Power BI コンテンツを配布する
description: Azure Active Directory B2B を使用して外部のゲストユーザーに Power BI を配布する方法について説明したホワイトペーパー
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/07/2019
ms.author: davidi
LocalizationGroup: Conceptual
ms.openlocfilehash: cc4387c3c1c0f83347823bbc6b95beb437b235e9
ms.sourcegitcommit: 4ac9447d1607dfca2e60948589f36a3d64d31cb4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2020
ms.locfileid: "92916891"
---
# <a name="distribute-power-bi-content-to-external-guest-users-using-azure-active-directory-b2b"></a>Azure Active Directory B2B を使用して外部ゲスト ユーザーに Power BI コンテンツを配布する

**概要:** これは、Azure Active Directory 企業間 Azure AD (B2B) との統合を使用して、組織外のユーザーにコンテンツを配布する方法を説明する技術ホワイトペーパーです。

**ライター:** Lukasz Pawlowski、Kasper de Jonge

**技術レビューアー:** Adam Wilson、Sheng Liu、Qian Liu、Sergei Gundorov、Jacob Grimm、Adam Saxton、Maya Shenhav、Nimrod Shalit、Elisabeth Olson

> [!NOTE]
> このホワイトペーパーを保存または印刷するには、ブラウザーから [ **印刷** ] を選択し、[ **PDF として保存** ] を選択します。

## <a name="introduction"></a>はじめに

Power BI によって、組織はビジネスの360度のビューを提供し、これらの組織のすべてのユーザーがデータを使用してインテリジェントな意思決定を行えるようにします。 これらの組織の多くは、外部のパートナー、クライアント、および請負業者との信頼関係が強固で信頼されています。 これらの組織は、これらの外部パートナーのユーザーに Power BI のダッシュボードやレポートへのセキュリティで保護されたアクセスを提供する必要があります。

Power BI は [Azure Active Directory 企業間 (AZURE AD B2B)](/azure/active-directory/b2b/what-is-b2b) と統合されているため、組織外のゲストユーザーに Power BI コンテンツを安全に配布できますが、内部データへのアクセスを制御し、管理することができます。

このホワイトペーパーでは、Azure Active Directory B2B との統合 Power BI を理解するために必要なすべての詳細について説明します。 最も一般的なユースケース、セットアップ、ライセンス、および行レベルのセキュリティについて説明します。

> [!NOTE]
> このホワイトペーパーでは、Azure AD として Azure Active Directory と、Azure AD B2B としての企業とビジネスの Azure Active Directory について説明します。

## <a name="scenarios"></a>シナリオ

Contoso は自動車メーカーであり、製造工程の実行に必要なすべてのコンポーネント、マテリアル、およびサービスを提供するさまざまなサプライヤーと連携しています。 Contoso は、サプライチェーンの物流を合理化し、Power BI を使用してサプライチェーンの主要なパフォーマンスメトリックを監視する計画を立てています。 Contoso は、安全で管理しやすい方法で外部サプライチェーンパートナーと共有したいと考えています。

Contoso では、Power BI と Azure AD B2B を使用して、外部ユーザーに対して次のエクスペリエンスを有効にすることができます。

### <a name="ad-hoc-per-item-sharing"></a>項目の共有ごとのアドホック

Contoso 社は、Contoso の自動車の仲介者として機能します。 多くの場合、Contoso の自動車のすべてのデータを使用して、放射の信頼性を最適化する必要があります。 Contoso 社のアナリストは、Power BI を使用して、サプライヤーのエンジニアと radiator の信頼性レポートを共有しています。 エンジニアは、レポートを表示するためのリンクを含む電子メールを受信します。

前述のように、このアドホック共有は必要に応じて、ビジネスユーザーによって実行されます。 外部ユーザーに Power BI によって送信されるリンクは、Azure AD B2B 招待リンクです。 外部ユーザーがリンクを開くと、ゲストユーザーとして Contoso の Azure AD 組織に参加するように求められます。 招待が承諾されると、特定のレポートまたはダッシュボードが開きます。 Azure Active Directory 管理者は、組織に外部ユーザーを招待するアクセス許可を委任し、このドキュメントの「ガバナンス」で説明されているように、招待を受け入れるとユーザーが実行できる操作を選択します。 Contoso アナリストは、ゲストユーザーを招待することができます。 Azure AD 管理者は、そのアクションと Power BI 管理者に対して、Power BI のテナント設定の内容を表示するゲストを招待することを許可したためです。

![AAD を使用して Power BI にゲストを招待する](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_01.png)

1. このプロセスは、ダッシュボードを共有する Contoso 内部ユーザー、または外部ユーザーとのレポートを使用して開始されます。 外部ユーザーがまだ Contoso 社の Azure AD のゲストでない場合は、招待されます。 Contoso 社の Azure AD への招待を含む電子メールアドレスに電子メールが送信されます。
2. 受信者は Contoso の Azure AD への招待を受け入れ、Contoso の Azure AD のゲストユーザーとして追加されます。
3. 受信者は、ユーザーに対して読み取り専用の Power BI ダッシュボード、レポート、またはアプリにリダイレクトされます。

Contoso のビジネスユーザーは、ビジネス上の目的で必要に応じて招待アクションを実行するため、このプロセスはアドホックと見なされます。 共有されている各アイテムは、外部ユーザーがコンテンツを表示するためにアクセスできる単一のリンクです。

外部ユーザーが Contoso のリソースにアクセスするように招待されると、Contoso Azure AD にシャドウアカウントが作成され、再度招待する必要がなくなります。  Power BI ダッシュボードのように Contoso のリソースに初めてアクセスしようとすると、招待を引き換え同意プロセスが実行されます。  同意しない場合、Contoso のコンテンツにはアクセスできません。  提供された元のリンクを使用して招待を利用できない場合は、Azure AD 管理者が特定の招待リンクを再送信して使用することができます。

### <a name="planned-per-item-sharing"></a>アイテムの共有ごとの予定

Contoso は、下請業者と協力して、放射型の信頼性分析を実行します。 下請業者は、Contoso の Power BI 環境のデータにアクセスする必要がある10人のユーザーのチームを持っています。 Contoso Azure AD 管理者は、すべてのユーザーを招待し、下請業者の変更で担当者として追加や変更を処理するために関与します。 Azure AD 管理者は、下請業者のすべての従業員のセキュリティグループを作成します。 Contoso の従業員は、セキュリティグループを使用して、レポートへのアクセスを簡単に管理し、必要なすべての下請業者の担当者がすべての必要なレポート、ダッシュボード、および Power BI アプリにアクセスできるようにすることができます。 Azure AD 管理者は、Contoso または下請業者の信頼された従業員に招待権限を委任することにより、招待プロセスに関与しないようにすることもできます。

一部の組織では、外部ユーザーを追加するタイミングをより細かく制御する必要があり、外部組織や多くの外部組織で多くのユーザーを招待しています。 このような場合、計画された共有を使用して、共有のスケールを管理したり、組織のポリシーを適用したり、信頼されたユーザーに権限を委任して外部ユーザーを招待および管理したりすることができます。 Azure AD B2B では、 [IT 管理者によって Azure portal から](/azure/active-directory/b2b/add-users-administrator)直接送信される予定の招待をサポートしています。または、 [招待マネージャー API を使用して](/azure/active-directory/b2b/customize-invitation-api) 、ユーザーのセットを1回の操作で招待することができます。 計画された招待方法を使用すると、組織はユーザーを招待して承認プロセスを実装できるユーザーを制御できます。 動的グループなどの高度な Azure AD 機能を使用すると、セキュリティグループのメンバーシップを自動的に管理しやすくなります。


![どのゲストがコンテンツを表示できるかを制御する](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_02.png)



1. プロセスは、IT 管理者によって、手動で、またはによって提供される API を使用して、ゲストユーザーを招待することによって開始され Azure Active Directory
2. ユーザーは、組織への招待を受け入れます。
3. ユーザーが招待を承諾すると、Power BI のユーザーは、レポートまたはダッシュボードを外部ユーザーまたはセキュリティグループと共有することができます。 Power BI の通常の共有と同様に、外部ユーザーはアイテムへのリンクを含む電子メールを受信します。
4. 外部ユーザーがリンクにアクセスすると、ディレクトリ内での認証は Contoso の Azure AD に渡され、Power BI コンテンツにアクセスするために使用されます。

### <a name="ad-hoc-or-planned-sharing-of-power-bi-apps"></a>Power BI アプリのアドホックまたは計画的な共有

Contoso には、1つまたは複数のサプライヤーと共有するために必要な一連のレポートとダッシュボードが用意されています。 必要なすべての外部ユーザーがこのコンテンツにアクセスできるようにするために、Power BI アプリとしてパッケージ化されます。 外部ユーザーは、アプリアクセスリストに直接追加するか、セキュリティグループを使用して追加されます。 Contoso のだれかが、電子メールなどのすべての外部ユーザーにアプリの URL を送信します。 外部ユーザーがリンクを開くと、すべてのコンテンツが単一のナビゲーションエクスペリエンスで表示されます。

Power BI アプリを使用すると、Contoso はサプライヤー向けの BI ポータルを簡単に作成できます。 1つのアクセスリストでは、必要なすべてのコンテンツへのアクセスを制御し、無駄な時間のチェックと項目レベルのアクセス許可の設定を減らします。 B2B Azure AD は、ユーザーが追加のログイン資格情報を必要としないように、サプライヤーのネイティブ id を使用してセキュリティアクセスを維持します。 セキュリティグループで計画された招待を使用している場合は、チームがプロジェクトを交代またはアウトするときに、アプリへのアクセス管理が簡略化されます。 手動または [動的グループ](/azure/active-directory/b2b/use-dynamic-groups)を使用したセキュリティグループのメンバーシップ。これにより、仕入先のすべての外部ユーザーが適切なセキュリティグループに自動的に追加されます。


![AAD を使用したコンテンツの制御](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_03.png)

1. プロセスは、Azure portal または PowerShell を使用して Contoso の Azure AD 組織に招待されているユーザーによって開始されます。
2. ユーザーは Azure AD のユーザーグループに追加できます。 静的または動的なユーザーグループを使用できますが、動的グループを使用すると手動作業を減らすことができます。
3. 外部ユーザーには、ユーザーグループを介して Power BI アプリへのアクセス権が付与されます。 アプリの URL は、外部ユーザーに直接送信するか、アクセス権のあるサイトに配置する必要があります。 Power BI を使用すると、外部ユーザーにアプリリンクを含む電子メールを送信することができますが、メンバーシップの変更が可能なユーザーグループを使用する場合、Power BI は、ユーザーグループを通じて管理されるすべての外部ユーザーに送信することはできません。
4. 外部ユーザーが Power BI アプリの URL にアクセスすると、その URL は Contoso の Azure AD によって認証され、ユーザーに対してアプリがインストールされ、ユーザーはアプリ内のすべての包含レポートとダッシュボードを表示できます。

アプリには、アプリの作成者がユーザーのアプリケーションを自動的にインストールできるようにする固有の機能もあります。これにより、ユーザーがログインするときにアプリケーションを使用できるようになります。 この機能は、アプリケーションが公開または更新されたときに Contoso の組織の一部である外部ユーザーに対してのみ、自動的にインストールされます。 したがって、計画された招待アプローチで最もよく使用され、ユーザーが Contoso の Azure AD に追加された後に発行または更新されるアプリによって異なります。 外部ユーザーは、アプリリンクを使用していつでもアプリをインストールできます。

### <a name="commenting-and-subscribing-to-content-across-organizations"></a>組織全体でコンテンツのコメント化とサブスクライブを行う

Contoso は、下請け業者やサプライヤーと協力して、Contoso のアナリストと密接に連携する必要があります。 Power BI には、ユーザーが使用できるコンテンツに関する情報をやり取りするためのコラボレーション機能がいくつか用意されています。 ダッシュボードコメント (およびすぐにレポートコメント) を使用すると、ユーザーに表示されるデータポイントについて話し合い、レポート作成者とやり取りして質問することができます。

現在、外部のゲストユーザーは、コメントを残して返信を読み取ることで、コメントに参加できます。 ただし、内部ユーザーとは異なり、ゲストユーザーは、 @mentioned コメントを受け取ったことを示す通知を受け取ることはできません。 ゲストユーザーは、書き込み時に Power BI 内のサブスクリプション機能を使用することはできません。 今後のリリースでは、これらの制限が解除され、ゲストユーザーにコメントが送信されたとき、 @mentions または Power BI のコンテンツへのリンクが記載された電子メールにサブスクリプションが配信されたときに、電子メールが送信されます。

### <a name="access-content-in-the-power-bi-mobile-apps"></a>Power BI モバイルアプリのコンテンツにアクセスする

今後のリリースでは、Contoso 社のユーザーがレポートまたはダッシュボードを外部のゲストと共有すると、Power BI はゲストに通知する電子メールを送信します。 ゲストユーザーがモバイルデバイスでレポートまたはダッシュボードへのリンクを開くと、デバイスのネイティブ Power BI モバイルアプリでコンテンツが開きます (インストールされている場合)。 ゲストユーザーは、外部テナントで共有されているコンテンツ間を移動し、ホームテナントから独自のコンテンツに戻ることができます。

> [!NOTE]
> ゲストユーザーは Power BI モバイルアプリを開き、外部テナントにすぐに移動することはできません。外部テナントのアイテムへのリンクから開始する必要があります。 一般的な回避策については、このドキュメントで後述 [する「親組織の Power BI のコンテンツへのリンクの配布](#distributing-links-to-content-in-the-parent-organizations-power-bi) 」を参照してください。

### <a name="cross-organization-editing-and-management-of-power-bi-content"></a>Power BI コンテンツのクロス組織の編集と管理

Contoso とそのサプライヤーおよび下請け業者は、密接に連携しています。 多くの場合、下請業者のアナリストは、Contoso が共有しているレポートに追加のメトリックまたはデータビジュアライゼーションを追加する必要があります。 データは Contoso の Power BI テナントに格納されている必要がありますが、外部ユーザーは、それを編集し、新しいコンテンツを作成し、適切なユーザーに配布することもできます。

Power BI には、外部の **ゲストユーザーが組織内のコンテンツを編集および管理できる** オプションが用意されています。 既定では、外部ユーザーには読み取り専用の使用状況指向のエクスペリエンスがあります。 ただし、この新しい設定により、Power BI 管理者は、自分の組織内のコンテンツを編集および管理できる外部ユーザーを選択できます。 外部ユーザーは、許可されると、レポート、ダッシュボード、アプリの発行または更新、ワークスペースでの作業、および使用するアクセス許可があるデータへの接続を行うことができます。

このシナリオの詳細については、このドキュメントの後半の「外部ユーザーがコンテンツを編集および管理できるようにする Power BI」を参照してください。

## <a name="organizational-relationships-using-power-bi-and-azure-ad-b2b"></a>Power BI と Azure AD B2B を使用した組織の関係

Power BI のすべてのユーザーが組織の内部にある場合、Azure AD B2B を使用する必要はありません。 ただし、2つ以上の組織がデータと洞察を共同作業する場合は、Power BI が Azure AD B2B をサポートすることで、簡単かつコスト効率が向上します。

通常、Power BI で Azure AD B2B スタイルのクロス組織コラボレーションに適した組織構造が検出されます。 Azure AD B2B はほとんどの場合に適していますが、状況によっては、このドキュメントの最後に記載されている一般的な代替方法を検討する価値があります。

### <a name="case-1-direct-collaboration-between-organizations"></a>ケース 1: 組織間の直接的な共同作業

Contoso とその radiator supplier の関係は、組織間の直接的な共同作業の一例です。 Contoso とそのサプライヤーには、radiator の信頼性情報へのアクセスを必要とするユーザーが比較的少ないため、Azure AD B2B ベースの外部共有を使用することをお勧めします。 簡単に使用でき、簡単に管理できます。 これはコンサルティングサービスの一般的なパターンでもあり、コンサルタントが組織のコンテンツを構築する必要がある場合があります。

![組織間で共有する](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_04.png)


通常、この共有は、アイテムの共有ごとにアドホックに使用します。 ただし、チームの成長や関係が増すにつれて、計画された項目ごとの共有アプローチは、管理オーバーヘッドを削減するために推奨される方法になります。 さらに、Power BI アプリのアドホックまたは計画された共有、組織全体のコンテンツのコメント化とサブスクライブ、モバイルアプリでのコンテンツへのアクセスが可能になります。また、組織をまたいで Power BI コンテンツを編集したり管理したりすることもできます。 重要な点として、両方の組織のユーザーがそれぞれの組織でライセンスを Power BI Pro している場合は、それらの Pro ライセンスを互いの Power BI 環境で使用できます。 これにより、招待側の組織が外部ユーザーの Power BI Pro ライセンスに対して支払う必要がない可能性があるため、有益なライセンスが提供されます。 詳細については、このドキュメントで後述する「ライセンス」を参照してください。

### <a name="case-2-parent-and-its-subsidiaries-or-affiliates"></a>ケース 2: 親とその関連会社または関連会社

一部の組織構造は、部分的または完全に所有する子会社、関連会社、または管理されたサービスプロバイダーの関係など、より複雑になります。 このような組織には、持ち株会社などの親組織がありますが、基になる組織は、地域要件が異なる場合によっては自律的に動作します。 これにより、各組織は独自の Azure AD 環境と個別の Power BI テナントを持つことになります。

![子会社の操作](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_05.png)


この構造では、通常、親組織は、標準化された洞察を子会社に配布する必要があります。 通常、この共有は、次の図に示すように、Power BI アプリのアドホックまたは計画された共有を使用して行われます。これは、標準化された権限のあるコンテンツを広範な対象ユーザーに配布できるためです。 実際には、このドキュメントで既に説明したすべてのシナリオを組み合わせて使用します。

![シナリオの結合](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_06.png)


これは、次のプロセスに従います。

1. 各子会社のユーザーが Contoso 社の Azure AD に招待されます。
2. その後、Power BI アプリが公開され、これらのユーザーは必要なデータにアクセスできるようになります。
3. 最後に、ユーザーは、レポートを表示するために指定されたリンクを使用してアプリを開きます。

この構造の組織では、いくつかの重要な課題が直面しています。

- 親組織の Power BI のコンテンツへのリンクを配布する方法
- 親組織でホストされているデータソースへのアクセスを、子会社のユーザーに許可する方法

#### <a name="distributing-links-to-content-in-the-parent-organizations-power-bi"></a>親組織の Power BI のコンテンツへのリンクの配布

リンクをコンテンツに配布するには、一般的に3つの方法が使用されます。 1つ目の最も基本的な方法は、アプリへのリンクを必要なユーザーに送信する方法と、それを開くことのできる SharePoint Online サイトに配置する方法です。 ユーザーは、ブラウザーでリンクをブックマークして、必要なデータにすばやくアクセスできます。

2番目の方法は、Power BI コンテンツ機能の組織間の編集と管理に依存しています。 親組織は、子会社のユーザーに Power BI へのアクセスを許可し、アクセス許可によってアクセスできる対象を制御します。 これにより、Power BI ホームにアクセスできるようになります。ここでは、子会社のユーザーが、親組織のテナントで共有されているコンテンツの包括的な一覧を確認できます。 その後、親組織の Power BI 環境への URL が、子会社のユーザーに与えられます。

最終的な方法では、各子会社の Power BI テナント内で作成された Power BI アプリを使用します。 Power BI アプリには [、[外部リンク] オプションを使用して構成さ](../create-reports/service-dashboard-edit-tile.md#hyperlink)れたタイルを含むダッシュボードが含まれています。 ユーザーがタイルを押すと、親組織の Power BI にある適切なレポート、ダッシュボード、またはアプリが表示されます。 このアプローチには、子会社のすべてのユーザーに対して自動的にアプリをインストールし、独自の Power BI 環境にサインインするたびにアプリケーションを使用できるという利点があります。 この方法の利点として、リンクをネイティブに開くことができる Power BI モバイルアプリに適しています。 また、これを2番目の方法と組み合わせて、Power BI 環境間での切り替えを容易にすることもできます。

#### <a name="allowing-subsidiary-users-to-access-data-sources-hosted-by-the-parent-organization"></a>親組織でホストされているデータソースへのアクセスを、子会社のユーザーに許可する

多くの場合、子会社のアナリストは、親組織によって提供されるデータを使用して独自の分析を作成する必要があります。 この場合、一般的なクラウドデータソースを使用して課題に対処します。

最初の方法では、次の図に示すように、 [Azure Analysis Services](/azure/analysis-services/analysis-services-overview) を利用して、親とその子会社全体でアナリストのニーズに対応するエンタープライズグレードのデータウェアハウスを構築します。 Contoso はデータをホストし、行レベルのセキュリティなどの機能を使用して、各子会社のユーザーが自分のデータにのみアクセスできるようにすることができます。 各組織のアナリストは、Power BI Desktop を通じてデータウェアハウスにアクセスし、その結果の分析をそれぞれの Power BI テナントに発行できます。

![Power BI テナントを使用した共有のしくみ](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_07.png)


2番目の方法では、 [Azure SQL Database](https://azure.microsoft.com/services/sql-database/) を利用して、データへのアクセスを提供するリレーショナルデータウェアハウスを構築します。 これは、Azure Analysis Services の方法と同様に機能しますが、行レベルのセキュリティなどの一部の機能は、複数の子会社にわたってデプロイおよび保守が困難な場合があります。

より高度な方法も使用できますが、上記の方法は最も一般的です。

### <a name="case-3-shared-environment-across-partners"></a>ケース 3: パートナー間の共有環境

Contoso は、対戦相手と提携して、共有組立ラインに自動車を建設することができますが、車両を別のブランドまたは異なる地域に分散させることができます。 これには、組織全体のデータ、インテリジェンス、および分析の広範なコラボレーションと共同所有権が必要です。 この構造は、コンサルタントチームがクライアントに対してプロジェクトベースの分析を行うことができるコンサルティングサービス業界にも共通しています。

![パートナー間の共有環境](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_08.png)



実際には、次の図に示すように、これらの構造は複雑であり、スタッフに管理を求める必要があります。 この構造を効果的にするには、組織が各自の Power BI テナント用に購入した Power BI Pro ライセンスを再利用できるようにするため、Power BI コンテンツ機能のクロス組織の編集と管理に依存します。

![ライセンスと共有組織のコンテンツ](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_09.png)



共有 Power BI テナントを確立するには、Azure Active Directory を作成する必要があり、その Active Directory 内のユーザーに対して少なくとも1つの Power BI Pro ユーザーアカウントを購入する必要があります。 このユーザーは、必要なユーザーを共有組織に招待します。 重要なのは、このシナリオでは、Contoso のユーザーが共有組織の Power BI 内で動作する場合、外部ユーザーとして扱われるということです。

このプロセスは次のとおりです。

1. 共有組織は新しい Azure Active Directory として確立され、少なくとも1つのユーザーアカウントが新しい組織に作成されます。 そのユーザーには Power BI Pro ライセンスが割り当てられている必要があります。
2. その後、このユーザーは Power BI のテナントを確立し、必要なユーザーを Contoso とパートナー組織から招待します。 また、ユーザーは Azure Analysis Services のような共有データ資産も確立します。 Contoso とパートナーのユーザーは、ゲストユーザーとして共有組織の Power BI にアクセスできます。 Power BI のコンテンツの編集と管理を許可されている場合は、外部ユーザーが Power BI ホームを使用したり、ワークスペースを使用したり、コンテンツをアップロードまたは編集したり、レポートを共有したりできます。 通常、共有されているすべての資産は、共有組織から格納およびアクセスされます。
3. パーティがどのように共同作業に同意するかによって、各組織は、共有データウェアハウス資産を使用して独自の独自のデータと分析を開発することができます。 内部 Power BI テナントを使用して、それらのユーザーをそれぞれの内部ユーザーに配布することができます。

### <a name="case-4-distribution-to-hundreds-or-thousands-of-external-partners"></a>ケース 4: 数百または数千の外部パートナーへの配布

Contoso は1つの業者に対して radiator の信頼性レポートを作成しましたが、Contoso 社は、数百のサプライヤー向けに標準化されたレポートのセットを作成することを希望しています。 これにより、Contoso は、すべてのサプライヤーが、改善のために必要な分析や、製造の欠陥の修正に必要な分析を確実に行えるようになります。

![多数のパートナーへの配布](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_10.png)


標準化されたデータと洞察を多数の外部ユーザーまたは組織に配布する必要がある場合は、Power BI アプリのアドホックまたは計画された共有のシナリオを使用して、開発コストのない BI ポータルをすばやく構築できます。 Power BI アプリを使用してこのようなポータルを構築するプロセスについては、このドキュメントで後述する Power BI + Azure AD B2B を使用した BI ポータルの構築に関するチュートリアルで説明します。

このケースの一般的な亜種は、組織が顧客と洞察を共有しようとしている場合です。特に、Power BI で Azure B2C を使用しようとしている場合です。 Power BI は、Azure B2C をネイティブでサポートしていません。 このケースのオプションを評価している場合は、このドキュメントの後半の「」セクションで別の方法2を使用することを検討してください。

## <a name="case-study-building-a-bi-portal-using-power-bi--azure-ad-b2b--step-by-step-instructions"></a>ケーススタディ: Power BI + Azure AD B2B を使用して BI ポータルを構築する-ステップバイステップの手順

Power BI の Azure AD B2B との統合により、Contoso はシームレスで手間のかからない方法で、ゲストユーザーに BI ポータルへのセキュリティで保護されたアクセスを提供します。 Contoso では、次の3つの手順でこれを設定できます。

![ポータルを構築する](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_11.png)


1. Power BI で BI ポータルを作成する

    Contoso の最初のタスクは、Power BI で BI ポータルを作成することです。 Contoso の BI ポータルは、多数の内部ユーザーとゲストユーザーが使用できるようにする、専用のダッシュボードとレポートのコレクションで構成されています。 Power BI でこれを行うには、Power BI アプリを構築することをお勧めします。 アプリの詳細について [は Power BI を](https://powerbi.microsoft.com/blog/distribute-to-large-audiences-with-power-bi-apps/)参照してください。

- Contoso の BI チームは、ワークスペースを作成し Power BI

    ![ワークスペース](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_12.png)
    

- 他の作成者がワークスペースに追加される

    ![作成者の追加](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_13.png)


- コンテンツはワークスペース内に作成されます

    ![ワークスペース内にコンテンツを作成する](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_14.png)


    コンテンツがワークスペースに作成されたので、Contoso は、このコンテンツを使用するパートナー組織のゲストユーザーを招待する準備ができました。

2. ゲスト ユーザーを招待する

    Contoso が Power BI で BI ポータルにゲストユーザーを招待するには、次の2つの方法があります。

    * 計画された招待
    * アドホック招待

    **計画された招待**

    このアプローチでは、Contoso がゲストユーザーを Azure AD に事前に招待し、Power BI コンテンツをそれらに配布します。 Contoso は、Azure portal または PowerShell を使用して、ゲストユーザーを招待できます。 Azure portal からゲストユーザーを招待するには、次の手順を実行します。

    - Contoso の Azure AD 管理者は **、新しいゲストユーザー > すべてのユーザー > ユーザーとグループに Azure portal > Azure Active Directory** に移動します。

    ![ゲスト ユーザー](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_15.png)


    - ゲストユーザーの招待メッセージを追加し、[招待] をクリックします。

    ![招待の追加](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_16.png)


    > [!NOTE]
    > Azure portal からゲストユーザーを招待するには、テナントの Azure Active Directory の管理者である必要があります。

    Contoso が多くのゲストユーザーを招待する場合は、PowerShell を使用してこれを行うことができます。 Contoso の Azure AD 管理者は、すべてのゲストユーザーの電子メールアドレスを CSV ファイルに保存します。 [B2B コラボレーションコードと PowerShell のサンプル](/azure/active-directory/b2b/code-samples)と手順については Azure Active Directory を参照してください。

    招待の後、ゲストユーザーは招待リンクを含む電子メールを受信します。

    ![招待のリンク](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_17.png)


    ゲストユーザーがリンクをクリックすると、Contoso Azure AD テナントのコンテンツにアクセスできるようになります。

    > [!NOTE]
    > [ここで](/azure/active-directory/active-directory-b2b-invitation-email)説明するように Azure AD ブランド化機能を使用して、招待メールのレイアウトを変更することができます。


    **アドホック招待**

    Contoso が事前に招待したいすべてのゲストユーザーを把握していない場合はどうすればよいですか。 また、BI ポータルを作成した Contoso のアナリストが、ゲストユーザーにコンテンツを配布する必要がある場合はどうでしょうか。 また、アドホック招待を使用した Power BI でもこのシナリオがサポートされます。

    アナリストは、アプリの発行時に、アプリのアクセスリストに外部ユーザーを追加するだけで済みます。 ゲストユーザーは招待を受け取り、承諾すると、Power BI のコンテンツに自動的にリダイレクトされます。

    ![外部ユーザーの追加](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_18.png)


    > [!NOTE]
    > 招待は、外部ユーザーが初めて組織に招待されたときにのみ必要です。


3. [ドライバー パッケージ]

    Contoso の BI チームが BI ポータルと招待されたゲストユーザーを作成したので、ゲストユーザーにアプリへのアクセスを許可して発行することによって、ポータルをエンドユーザーに配布することができます。 Power BI、Contoso テナントに既に追加されているゲストユーザーの名前をオートコンプリートします。 この時点で、他のゲストユーザーへのアドホック招待を追加することもできます。

    > [!NOTE]
    > セキュリティグループを使用して外部ユーザーのアプリへのアクセスを管理する場合は、計画された招待方法を使用して、アクセスする必要がある外部ユーザーに直接アプリリンクを共有します。 それ以外の場合、外部ユーザーは app._ 内からコンテンツをインストールまたは表示できない可能性があります。

    ゲストユーザーは、アプリへのリンクを含む電子メールを受け取ります。

    ![電子メール招待のリンク](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_19.png)


    このリンクをクリックすると、ゲストユーザーは自身の組織の id で認証するように求められます。

    ![サインイン ページ](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_20.png)


    正常に認証されると、Contoso の BI アプリにリダイレクトされます。

    ![共有コンテンツを表示](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_21.png)

    その後、ゲストユーザーは、電子メールのリンクをクリックするかリンクをブックマークすることで、Contoso のアプリにアクセスできます。 Contoso では、ゲストユーザーが既に使用している既存のエクストラネットポータルにこのリンクを追加することで、ゲストユーザーの作業を容易にすることもできます。

4. 次の手順

    Contoso は、Power BI アプリと Azure AD B2B を使用して、コードなしでサプライヤーの BI ポータルをすばやく作成できました。 これにより、標準化された分析を必要なすべてのサプライヤーに配布することが大幅に簡素化されました。

    この例では、1つの共通レポートをサプライヤー間で分散する方法を示しましたが、Power BI はさらに詳細になります。 各パートナーが自身に関連するデータのみを認識するように、行レベルセキュリティを簡単にレポートとデータモデルに追加できます。 このドキュメントで後述する「外部パートナー向けのデータセキュリティ」セクションでは、このプロセスについて詳しく説明します。

    多くの場合、個別のレポートとダッシュボードを既存のポータルに埋め込む必要があります。 この例に示されている多くの手法を再利用することもできます。 ただし、このような状況では、ワークスペースから直接レポートまたはダッシュボードを埋め込む方が簡単な場合があります。 [ユーザーの要求] にセキュリティ権限を割り当てるプロセスは同じままです。

## <a name="under-the-hood-how-is-lucy-from-supplier1-able-to-access-power-bi-content-from-contosos-tenant"></a>内部では、どのようにして Lucy が Contoso のテナントからのコンテンツに Power BI アクセスできるかどうかについて、どのようにしてますか。

Contoso がパートナー組織のゲストユーザーに Power BI コンテンツをシームレスに配布する方法について説明したので、ここではそのしくみについて詳しく見ていきましょう。

Contoso がディレクトリに招待すると [lucy@supplier1.com](mailto:lucy@supplier1.com) 、Azure AD によっ [Lucy@supplier1.com](mailto:Lucy@supplier1.com) てと contoso Azure AD テナントの間にリンクが作成されます。 このリンクを使用すると Lucy@supplier1.com 、が Contoso テナントのコンテンツにアクセスできることを Azure AD ことができます。

Lucy が Contoso の Power BI アプリにアクセスしようとすると、Azure AD が contoso テナントにアクセスできることを確認し、Lucy が Contoso テナントのコンテンツにアクセスするために認証されていることを示すトークン Power BI を提供します。 Power BI は、このトークンを使用して承認し、Lucy が Contoso の Power BI アプリにアクセスできるようにします。

![検証と承認](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_22.png)

Power BI の Azure AD B2B との統合は、すべての業務用電子メールアドレスと連携します。 ユーザーが Azure AD id を持っていない場合は、作成するように求めるメッセージが表示されることがあります。 次の図は、詳細なフローを示しています。

![統合フローチャート](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_23.png)


Azure AD アカウントが外部パーティの Azure AD で使用または作成されることを認識することが重要です。これにより、Lucy が独自のユーザー名とパスワードを使用できるようになります。また、組織が Azure AD を使用しているときに、その資格情報は自動的に他のテナントで動作を停止します。

## <a name="licensing"></a>ライセンス

Contoso は、サプライヤーおよびパートナー組織からのゲストユーザーのライセンスを取得して、Power BI コンテンツにアクセスできるようにする3つの方法のいずれかを選択できます。

> [!NOTE]
> _Azure AD B2B's free レベルでは、AZURE AD B2B で Power BI を使用するのに十分です。動的グループなどの高度な Azure AD B2B 機能では、追加のライセンスが必要になります。詳細については、Azure AD B2B のドキュメントを参照してください。_[_https://docs.microsoft.com/azure/active-directory/b2b/licensing-guidance_](/azure/active-directory/b2b/licensing-guidance)

### <a name="approach-1-contoso-uses-power-bi-premium"></a>方法 1: Contoso を使用する Power BI Premium

このアプローチでは、Contoso は Power BI Premium 容量を購入し、その BI ポータルコンテンツをこの容量に割り当てます。 これにより、パートナー組織のゲストユーザーは、Power BI ライセンスを使用せずに Contoso 社の Power BI アプリにアクセスできるようになります。

外部ユーザーは、Power BI Premium 内でコンテンツを使用するときに、Power BI の "無料" のユーザーに提供される使用量のみにも影響します。

Contoso では、更新率の増加、容量、大規模なモデルのサイズなど、アプリの他の Power BI premium 機能を利用することもできます。

![その他の機能](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_24.png)


### <a name="approach-2-contoso-assigns-power-bi-pro-licenses-to-guest-users"></a>方法 2: Contoso Power BI Pro ライセンスをゲストユーザーに割り当てます。

このアプローチでは、Contoso はパートナー組織のゲストユーザーに pro ライセンスを割り当てます。これは Contoso の Microsoft 365 管理センターから行うことができます。 これにより、パートナー組織のゲストユーザーは、ライセンスを購入しなくても Contoso 社の Power BI アプリにアクセスできるようになります。 これは、組織がまだ Power BI 採用していない外部ユーザーとの共有に適しています。

> [!NOTE]
> Contoso の pro ライセンスは、Contoso テナントのコンテンツにアクセスする場合にのみ、ゲストユーザーに適用されます。 Pro ライセンスを使用すると、Power BI Premium 容量以外のコンテンツにアクセスできます。 ただし、Pro ライセンスを持つ外部ユーザーは、既定で消費のみのエクスペリエンスに制限されています。 これは、このドキュメントで後述する「Power BI で _外部ユーザーがコンテンツを編集および管理できるようにする_ 方法」で説明されている方法を使用して変更できます。

![ライセンス情報](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_25.png)


### <a name="approach-3-guest-users-bring-their-own-power-bi-pro-license"></a>方法 3: ゲストユーザーが独自の Power BI Pro ライセンスを持ち込む

このアプローチでは、Supplier 1 は Power BI Pro ライセンスを Lucy に割り当てます。 その後、このライセンスで Contoso の Power BI アプリにアクセスできます。 Lucy は外部 Power BI 環境にアクセスするときに自身の組織の Pro ライセンスを使用できるため、この方法は _ライセンス_ 持ち込み (byol) と呼ばれることもあります。 両方の組織が Power BI を使用している場合は、分析ソリューション全体に対して有益なライセンスが提供され、外部ユーザーにライセンスを割り当てる際のオーバーヘッドが最小限に抑えられます。

> [!NOTE]
> Supplier 1 で Lucy に指定された pro ライセンスは、Lucy がゲストユーザーであるすべての Power BI テナントに適用されます。 Pro ライセンスを使用すると、Power BI Premium 容量以外のコンテンツにアクセスできます。 ただし、Pro ライセンスを持つ外部ユーザーは、既定で消費のみのエクスペリエンスに制限されています。 これは、このドキュメントで後述する「Power BI で _外部ユーザーがコンテンツを編集および管理できるようにする_ 方法」で説明されている方法を使用して変更できます。

![Pro ライセンスの要件](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_26.png)

## <a name="data-security-for-external-partners"></a>外部パートナー向けのデータセキュリティ

一般に、複数の外部業者を使用する場合、Contoso は、各供給業者が自社の製品に関するデータのみを認識するようにする必要があります。 ユーザーベースのセキュリティと動的な行レベルのセキュリティにより、Power BI で簡単に実行できます。

### <a name="user-based-security"></a>ユーザーベースのセキュリティ

Power BI の最も強力な機能の1つは行レベルセキュリティです。 この機能を使用すると、Contoso は1つのレポートとデータセットを作成できますが、ユーザーごとに異なるセキュリティ規則を適用できます。 詳細については、「 [行レベルのセキュリティ (RLS)](https://powerbi.microsoft.com/documentation/powerbi-admin-rls/)」を参照してください。

Power BI の Azure AD B2B との統合により、Contoso は contoso テナントに招待されるとすぐに行レベルセキュリティ規則をゲストユーザーに割り当てることができます。 前に説明したように、Contoso では、計画またはアドホック招待を通じてゲストユーザーを追加できます。 Contoso が行レベルのセキュリティを適用する場合は、計画された招待を使用して、ゲストユーザーを事前に追加し、コンテンツを共有する前にそれらをセキュリティロールに割り当てることを強くお勧めします。 Contoso がアドホック招待を使用する場合、ゲストユーザーがデータを表示できない期間が短時間である可能性があります。

> [!NOTE]
> アドホック招待を使用するときに、RLS によって保護されたデータにアクセスする際のこの遅延は、受信した電子メールで共有リンクを開いたときに、ユーザーに対して空白または破損したレポート/ダッシュボードが表示されるため、IT チームへの要求をサポートする可能性があります。 そのため、このシナリオでは、計画された招待を使用することを強くお勧めします。 * *

例を見てみましょう。

前述のように、Contoso 社には世界中のサプライヤーがいます。また、サプライヤー組織のユーザーが、その地域のデータから洞察を得られるようにしたいと考えています。  ただし、Contoso のユーザーはすべてのデータにアクセスできます。 Contoso は複数の異なるレポートを作成するのではなく、1つのレポートを作成し、そのデータを表示するユーザーに基づいてデータをフィルター処理します。

![共有コンテンツ](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_27.png)

Contoso が接続しているユーザーに基づいてデータをフィルター処理できるようにするために、Power BI desktop に2つのロールが作成されます。 1つは、SalesTerritory "ヨーロッパ" のすべてのデータをフィルター処理するためのもので、もう1つは "北米" を対象としています。

![ロールの管理](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_28.png)

レポートでロールが定義されている場合、ユーザーは、任意のデータにアクセスするために、特定のロールに割り当てられている必要があります。 ロールの割り当ては、Power BI サービス ( **データセット > セキュリティ** ) 内で行われます。

![セキュリティの設定](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_29.png)

これにより、作成した2つのロールを Contoso の BI チームが確認できるページが開きます。  Contoso の BI チームがロールにユーザーを割り当てることができるようになりました。

![行レベルのセキュリティ](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_30.png)

この例では、Contoso は、電子メールアドレスが "" のパートナー組織のユーザーを欧州ロールに追加してい [adam@themeasuredproduct.com](mailto:adam@themeasuredproduct.com) ます。

![行レベルのセキュリティ設定](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_31.png)

Azure AD によって解決されると、Contoso は、追加の準備が整ったウィンドウに名前が表示されることを確認できます。

![ロールの表示](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_32.png)

これで、共有されていたアプリをこのユーザーが開いたときに、ヨーロッパのデータを含むレポートのみが表示されるようになりました。

![ビューの内容](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_33.png)

### <a name="dynamic-row-level-security"></a>動的な行レベルのセキュリティ

もう1つの興味深いトピックは、動的な行レベルセキュリティ (RLS) が Azure AD B2B でどのように機能するかを確認することです。

つまり、動的な行レベルのセキュリティは、Power BI に接続しているユーザーのユーザー名に基づいてモデル内のデータをフィルター処理することによって機能します。 ユーザーのグループに複数のロールを追加するのではなく、モデル内のユーザーを定義します。 ここでは、パターンについて詳しく説明しません。 Kasper de Jong では、[このホワイトペーパー](https://download.microsoft.com/download/D/2/0/D20E1C5F-72EA-4505-9F26-FEF9550EFD44/Securing%20the%20Tabular%20BI%20Semantic%20Model.docx)に記載されている動的な[セキュリティ](https://www.kasperonbi.com/power-bi-desktop-dynamic-security-cheat-sheet/)情報のすべての種類の行レベル Power BI Desktop セキュリティについて詳細に説明しています。

例を見てみましょう。 Contoso には、グループ別の売上に関する単純なレポートがあります。

![サンプルコンテンツ](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_34.png)

このレポートを2人のゲストユーザーと内部ユーザーに共有する必要があります。内部ユーザーはすべてを表示できますが、ゲストユーザーはアクセス権のあるグループのみを表示できます。 これは、ゲストユーザーのデータのみをフィルター処理する必要があることを意味します。 データを適切にフィルター処理するために、Contoso はホワイトペーパーとブログの投稿で説明されているように動的 RLS パターンを使用します。 これは、Contoso がユーザー名をデータ自体に追加することを意味します。

![データ自体に対して RLS ユーザーを表示する](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_35.png)

次に、Contoso は適切なリレーションシップを使用してデータを適切にフィルター処理する適切なデータモデルを作成します。

![適切なデータが表示されます。](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_36.png)

ログインしているユーザーに基づいてデータを自動的にフィルター処理するために、Contoso は、接続しているユーザーを渡すロールを作成する必要があります。 この場合、Contoso は2つのロールを作成します。1つは、Power BI にログインしているユーザーの現在のユーザー名を使用して Users テーブルをフィルター処理する "securityrole" です (Azure AD B2B ゲストユーザーに対しても機能します)。

![ロールの管理](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_37.png)

Contoso は、すべてを表示できる、内部ユーザーに対して別の "AllRole" も作成します。このロールにはセキュリティ述語がありません。

Power BI desktop ファイルをサービスにアップロードした後、Contoso は "SecurityRole" にゲストユーザーを割り当てて、"AllRole" に内部ユーザーを割り当てることができます。

ゲストユーザーがレポートを開くと、グループ A からの売上のみが表示されるようになりました。

![グループ A からのみ](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_38.png)

右側のマトリックスでは、USERNAME () 関数と USERPRINCIPALNAME () 関数の結果が両方とも guest ユーザーの電子メールアドレスとして返されます。

これで、内部ユーザーがすべてのデータを表示できるようになりました。

![表示されるすべてのデータ](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_39.png)

ご覧のように、動的 RLS は内部ユーザーとゲストユーザーの両方で動作します。

> [!NOTE]
> このシナリオは、Azure Analysis Services でモデルを使用する場合にも使用できます。 通常、Azure Analysis Service は、Power BI と同じ Azure AD に接続されます。その場合、Azure Analysis Services Azure AD B2B 経由で招待されたゲストユーザーも認識しています。

## <a name="connecting-to-on-premises-data-sources"></a>オンプレミスデータソースへの接続

Power BI は、オンプレミス[データゲートウェイ](https://powerbi.microsoft.com/documentation/powerbi-gateway-onprem/)に対して直接、 [SQL Server Analysis Services](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/)や[SQL Server](https://powerbi.microsoft.com/documentation/powerbi-gateway-kerberos-for-sso-pbi-to-on-premises-data/)などのオンプレミスデータソースを利用する Contoso の機能を提供します。 Power BI で使用するのと同じ資格情報を使用して、これらのデータソースにサインオンすることもできます。

> [!NOTE]
> Power BI テナントに接続するためにゲートウェイをインストールする場合は、テナント内に作成されたユーザーを使用する必要があります。 外部ユーザーはゲートウェイをインストールして、tenant._ に接続することはできません

外部ユーザーの場合、外部ユーザーは通常、オンプレミスの AD で認識されていないため、より複雑になる可能性があります。 Power BI は、「 [データソースの管理-Analysis Services](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/)」で説明されているように、Contoso の管理者が外部ユーザー名を内部ユーザー名にマップできるようにすることで、この回避策を提供します。 たとえば、は [lucy@supplier1.com](mailto:lucy@supplier1.com) [lucy \_ supplier1 \_ com # EXT@contoso.com ](mailto:lucy_supplier1_com)にマップできます。

![ユーザー名のマッピング](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_40.png)

Contoso が少数のユーザーのみを持っている場合、または Contoso がすべての外部ユーザーを1つの内部アカウントにマップできる場合、この方法は問題ありません。 各ユーザーが独自の資格情報を必要とする複雑なシナリオでは、「[データソースの管理-Analysis Services](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/)」で説明されているように、[カスタム AD 属性](/previous-versions/windows/it-pro/windows-2000-server/cc961737(v=technet.10))を使用してマッピングを行うより高度なアプローチがあります。 これにより、Contoso の管理者は、Azure AD (外部 B2B ユーザー) のすべてのユーザーのマッピングを定義できるようになります。  これらの属性は、スクリプトまたはコードを使用して AD オブジェクトモデルを通じて設定できます。そのため、Contoso は招待またはスケジュールされたリズムでマッピングを完全に自動化できます。

## <a name="enabling-external-users-to-edit-and-manage-content-within-power-bi"></a>外部ユーザーが Power BI 内のコンテンツを編集および管理できるようにする

Contoso を使用すると、組織内でのコンテンツの投稿を外部ユーザーに許可することができます。これには、「組織内の組織内での Power BI コンテンツの編集と管理」セクションを参照してください。

> [!NOTE]
> 組織の Power BI 内のコンテンツを編集および管理するには、ユーザーは個人用ワークスペース以外のワークスペースで Power BI Pro ライセンスを持っている必要があります。 ユーザーは、このドキュメントの「 _ライセンス_ 」セクションで説明されているように Pro ライセンスを取得できます。

Power BI 管理ポータルでは、[外部のゲストユーザーがテナントの設定] の [組織] 設定 **でコンテンツを編集および管理できるように** します。 既定では、この設定は [無効] に設定されています。つまり、既定では、外部ユーザーは制限付きの読み取り専用のエクスペリエンスを利用できます。 この設定は、Azure AD で UserType が Guest に設定されているユーザーに適用されます。 次の表では、ユーザーの UserType に応じた動作と、設定の構成方法について説明します。

| **Azure AD のユーザーの種類** | **外部のゲストユーザーがコンテンツ設定を編集および管理することを許可する** | **動作** |
| --- | --- | --- |
| ゲスト | ユーザーに対して無効 (既定) | 項目ごとの消費専用ビュー。 ゲストユーザーに送信された URL を使用して表示するときに、レポート、ダッシュボード、およびアプリへの読み取り専用アクセスを許可します。 Power BI Mobile アプリは、ゲストユーザーに読み取り専用のビューを提供します。 |
| ゲスト | ユーザーに対して有効 | 外部ユーザーは、一部の機能を使用できない場合でも、完全な Power BI エクスペリエンスにアクセスできます。 外部ユーザーは、テナント情報が含まれている Power BI サービスの URL を使用して Power BI にログインする必要があります。 ユーザーはホームエクスペリエンス、個人用ワークスペースを取得し、アクセス許可に基づいてコンテンツを参照、表示、作成できます。 </br></br> Power BI Mobile アプリは、ゲストユーザーに読み取り専用のビューを提供します。 |

> [!NOTE]
> Azure AD の外部ユーザーを UserType Member に設定することもできます。 現時点では、これは Power BI ではサポートされていません。

Power BI 管理ポータルでは、次の図に設定が表示されます。

![管理者の設定](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_41.png)

ゲストユーザーは、読み取り専用の既定のエクスペリエンスを取得し、コンテンツを編集および管理できます。 既定値は無効です。つまり、すべてのゲストユーザーが読み取り専用のエクスペリエンスを持ちます。 Power BI 管理者は、組織内のすべてのゲストユーザーまたは Azure AD で定義されている特定のセキュリティグループの設定を有効にすることができます。 次の図では、Contoso Power BI 管理者が Azure AD でセキュリティグループを作成し、Contoso テナントのコンテンツを編集および管理できる外部ユーザーを管理しています。

これらのユーザーが Power BI にログインできるようにするには、テナントの URL を指定します。 テナントの URL を見つけるには、次の手順に従います。

1. Power BI サービスの上部のメニューで、[ヘルプ (?] を選択し **ます。** ) をクリックし、  **Power BI について説明** します。
2. [  **テナント URL** ] の横にある値を探します。 これは、ゲストユーザーと共有できるテナント URL です。

    ![テナントの URL](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_42.png)

[外部ゲストユーザーに組織内のコンテンツの編集と管理を許可する] を使用すると、指定したゲストユーザーは組織の Power BI にアクセスし、アクセス許可があるコンテンツを表示できます。 これらのユーザーは、ホームにアクセスしたり、コンテンツを参照してワークスペースに投稿したり、アクセスリストにあるアプリをインストールしたり、個人用ワークスペースを持ったりすることができます。 新しいワークスペース エクスペリエンスを使用するワークスペースを作成したり、その管理者になったりすることができます。

> [!NOTE]
> このオプションを使用する場合は、このドキュメントのガバナンスセクションを必ず確認してください。既定の Azure AD 設定を使用すると、ゲストユーザーはユーザーの選択などの特定の機能を使用できなくなるため、エクスペリエンスが低下する可能性があります。 * *

[外部ゲストユーザーに組織のテナントのコンテンツの編集および管理を許可する] 設定を使用して有効にしたゲストユーザーは、一部のエクスペリエンスを使用できません。 レポートを更新またはパブリッシュするには、ゲストユーザーは Power BI サービス web UI を使用する必要があります。たとえば、Power BI Desktop ファイルをアップロードするには、[データの取得] を使用します。 次のエクスペリエンスはサポートされていません。

- Power BI Desktop から Power BI サービスに直接発行することはできません。
- ゲスト ユーザーは、Power BI Desktop を使用して Power BI サービス内のサービス データセットに接続することができません。
- Microsoft 365 グループに関連付けられているクラシックワークスペース: Guest ユーザーは、これらのワークスペースを作成したり、管理者にすることはできません。 メンバーになることは可能です。
- ワークスペース アクセス リストに対して、アドホック招待の送信はサポートされていません。
- ゲスト ユーザーに対して、Power BI Publisher for Excel はサポートされていません。
- ゲスト ユーザーは、Power BI Gateway をインストールして組織に接続することができません。
- ゲスト ユーザーは、組織全体に発行されるアプリをインストールできません。
- ゲスト ユーザーは組織のコンテンツ パックを使用、作成、更新、またはインストールできません。
- ゲスト ユーザーは [Excel で分析] を使用できません。
- ゲストユーザーにコメントを設定することはできません @mentioned (この機能は今後のリリースで追加される予定です)
- ゲストユーザーはサブスクリプションを使用できません (この機能は今後のリリースで追加される予定です)
- この機能を使用するゲスト ユーザーには、職場または学校のアカウントが必要です。 個人アカウントを使用しているゲストユーザーは、サインインの制限により、より多くの制限が発生します。



## <a name="governance"></a>ガバナンス

### <a name="additional-azure-ad-settings-that-affect-experiences-in-power-bi-related-to-azure-ad-b2b"></a>Azure AD B2B に関連する Power BI のエクスペリエンスに影響する追加の Azure AD 設定

Azure AD B2B 共有を使用する場合、Azure Active Directory 管理者は外部ユーザーのエクスペリエンスの側面を制御します。 これらは、テナントの Azure Active Directory 設定内の [外部コラボレーション設定] ページで制御されます。

設定の詳細については、次を参照してください。

[https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations](/azure/active-directory/b2b/delegate-invitations)

> [!NOTE]
> 既定では、"ゲストユーザーのアクセス許可は制限されています" オプションが [はい] に設定されているので、Power BI 内のゲストユーザーは、特に、ユーザーが選択した Ui が機能しないユーザーに対して、特に共有をブロックします。 適切なエクスペリエンスを確保するために、次に示すように、Azure AD 管理者と協力して [いいえ] に設定することが重要です。 * *

![外部コラボレーションの設定](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_43.png)


### <a name="control-guest-invites"></a>ゲスト招待の制御

Power BI 管理者は、Power BI 管理ポータルにアクセスすることによって、Power BI 専用の外部共有を制御できます。 ただし、管理者は、さまざまな Azure AD ポリシーを使用して外部共有を制御することもできます。  これらのポリシーを使用すると、管理者は

- エンドユーザーによる招待をオフにする
- 管理者と、ゲストの招待元ロールのユーザーのみが招待できる
- 管理者、ゲストの招待元ロール、およびメンバーが招待できる
- ゲストを含むすべてのユーザーが招待できる

これらのポリシーの詳細については、「 [B2B コラボレーション Azure Active Directory の招待の委任](/azure/active-directory/active-directory-b2b-delegate-invitations)」を参照してください。

外部ユーザーによるすべての Power BI アクションも [、監査ポータルで監査](https://powerbi.microsoft.com/documentation/powerbi-admin-auditing/)されます。

### <a name="conditional-access-policies-for-guest-users"></a>ゲストユーザーの条件付きアクセスポリシー

Contoso テナントのコンテンツにアクセスするゲストユーザーに対して、条件付きアクセスポリシーを適用することができます。 詳細な手順については、「 [B2B コラボレーションユーザーの条件付きアクセス](/azure/active-directory/active-directory-b2b-mfa-instructions)」を参照してください。

## <a name="common-alternative-approaches"></a>一般的な代替アプローチ

B2B Azure AD 組織間でのデータとレポートの共有が容易になりますが、一般的に使用されるいくつかの方法があり、場合によってはより優れている場合があります。

### <a name="alternative-option-1-create-duplicate-identities-for-partner-users"></a>代替オプション 1: パートナーユーザーの id を重複して作成する

このオプションを使用すると、contoso は、次の図に示すように、Contoso テナントのパートナーユーザーごとに重複した id を手動で作成する必要がありました。 次に、Power BI 内で、Contoso は、割り当てられた id と適切なレポート、ダッシュボード、またはアプリを共有できます。

![適切なマッピングと名前の設定](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_44.png)

この代替手段を選択する理由:

- ユーザーの id は組織によって制御されるため、電子メール、SharePoint などの関連サービスも組織の管理下にあります。 IT 管理者は、これらのサービスのパスワードをリセットしたり、アカウントへのアクセスを無効にしたり、監査アクティビティを実行したりすることができます。
- 多くの場合、ビジネスに個人のアカウントを使用するユーザーは、特定のサービスへのアクセスが制限されているため、組織のアカウントが必要になることがあります。
- 一部のサービスは、組織のユーザーに対してのみ機能します。 たとえば、Intune を使用して、Azure B2B を使用する外部ユーザーの個人用またはモバイルデバイスでコンテンツを管理することはできません。

この代替手段を選択しない理由:

- パートナー組織のユーザーは、2組の資格情報を覚えておく必要があります。1つは自分の組織からコンテンツにアクセスし、もう1つは Contoso のコンテンツにアクセスするためのものです。 これは、これらのゲストユーザーにとって面倒であり、多くのゲストユーザーはこのエクスペリエンスに混乱を招きます。
- Contoso は、ユーザーごとのライセンスを購入し、これらのユーザーに割り当てる必要があります。 ユーザーが電子メールを受信するか、office アプリケーションを使用する必要がある場合は、Power BI でコンテンツを編集および共有する Power BI Pro など、適切なライセンスが必要です。
- Contoso では、内部ユーザーと比較して、より厳格な承認とガバナンスのポリシーを外部ユーザーに適用することが必要になる場合があります。 これを実現するには、Contoso は外部ユーザー向けの社内の用語を作成する必要があり、Contoso のすべてのユーザーはこの用語について教育を受ける必要があります。
- ユーザーが組織を離れると、Contoso の管理者がアカウントを手動で削除するまで、Contoso のリソースに引き続きアクセスできるようになります。
- Contoso の管理者は、作成、パスワードのリセットなど、ゲストの id を管理する必要があります。

### <a name="alternative-option-2-create-a-custom-power-bi-embedded-application-using-custom-authentication"></a>代替オプション 2: カスタム認証を使用してカスタム Power BI Embedded アプリケーションを作成する

Contoso のもう1つのオプションは、カスタム認証 (["アプリ所有データ"](../developer/embedded/embed-sample-for-customers.md)) を使用して、独自のカスタム埋め込み Power BI アプリケーションを作成することです。 多くの組織には、Power BI コンテンツを外部パートナーに配布するためのカスタムアプリケーションを作成するための時間やリソースがありませんが、組織によっては、これが最善の方法であり、非常に深刻な考慮事項です。

多くの場合、組織は既存のパートナーポータルを使用して、パートナーのすべての組織リソースへのアクセスを一元化し、組織の内部リソースから分離し、パートナーが多数のパートナーと個々のユーザーをサポートするための合理化されたエクスペリエンスを提供しています。

![多くのパートナーポータル](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_45.png)

上の例では、各サプライヤーのユーザーが、id プロバイダーとして AAD を使用する Contoso のパートナーポータルにログインしています。 AAD B2B、Azure B2C、ネイティブ id を使用することも、任意の数の他の id プロバイダーとフェデレーションすることもできます。 ユーザーは、Azure Web アプリまたは同様のインフラストラクチャを使用してログインし、パートナーポータルのビルドにアクセスします。

Web アプリ内では、Power BI レポートは Power BI Embedded 配置から埋め込まれます。 この web アプリは、サプライヤーと Contoso との対話を容易にすることを目的とした、統合されたエクスペリエンスでレポートと関連サービスへのアクセスを効率化します。 このポータル環境は、サプライヤーがこれらのリソースにアクセスできないようにするために、Contoso internal AAD と Contoso の内部 Power BI 環境から分離されています。 通常、データの分離を確保するために、データは別のパートナーデータウェアハウスに格納されます。 この分離には、組織のデータへの直接アクセスを許可する外部ユーザーの数を制限し、外部ユーザーが使用できる可能性があるデータを制限し、外部ユーザーとの偶発的な共有を制限するための利点があります。

Power BI Embedded を使用すると、ポータルは、アプリトークンまたはマスターユーザーと Azure モデルで購入した premium 容量を使用して、有益なライセンスを活用できます。これにより、エンドユーザーへのライセンスの割り当てに関する問題が簡単になり、予想される使用量に基づいてスケールアップ/スケールダウンすることができます。 パートナーは、パートナーのすべてのニーズを念頭に置いて設計された単一のポータルにアクセスするため、全体的な品質と一貫したエクスペリエンスを提供できます。 最後に、Power BI Embedded ベースのソリューションは、通常はマルチテナントとして設計されているため、パートナー組織間の分離を容易にすることができます。

この代替手段を選択する理由:

- パートナー組織の数が増えるにつれて管理が容易になります。 パートナーは Contoso の内部 AAD ディレクトリから分離された別のディレクトリに追加されるため、IT 部門のガバナンスを簡素化し、内部データを外部ユーザーに誤って共有するのを防ぐことができます。
- 一般的なパートナーポータルは、パートナー間で一貫したエクスペリエンスを提供し、一般的なパートナーのニーズに合わせて合理化されています。 そのため、必要なすべてのサービスを1つのポータルに統合することで、パートナーに対する全体的なエクスペリエンスを向上させることができます。
- Power BI Embedded 内のコンテンツの編集などの高度なシナリオのライセンスコストは、Azure で購入した Power BI Premium に含まれており、それらのユーザーに Power BI Pro ライセンスを割り当てる必要はありません。
- マルチテナントソリューションとして設計されている場合、パートナー間の分離性が向上します。
- パートナーポータルには、多くの場合、Power BI レポート、ダッシュボード、およびアプリ以外のパートナー向けの他のツールが含まれています。

この代替手段を選択しない理由:

- このようなポータルを構築、運用、保守するには、多大な労力が必要です。
- 複数のワークストリームで慎重に計画して実行する必要があるため、B2B 共有を使用する場合よりも時間がかかります。
- パートナーの数が少ない場合は、この代替に必要な労力が大きすぎて正当化できない可能性が高くなります。
- アドホック共有による共同作業は、組織が直面する主要なシナリオです。
- レポートとダッシュボードは、パートナーごとに異なります。 この方法では、パートナーと直接共有するだけではなく、管理オーバーヘッドが発生します。



## <a name="faq"></a>よく寄せられる質問

**Contoso は、自動的に引き換えされる招待を送信して、ユーザーが "準備完了" になるようにすることができます。または、ユーザーは常に引き換え URL をクリックする必要がありますか。**

エンドユーザーがコンテンツにアクセスするには、常に同意エクスペリエンスをクリックする必要があります。

多数のゲストユーザーを招待する場合は、 [リソース組織のゲスト招待元ロールにユーザーを追加](/azure/active-directory/active-directory-b2b-add-guest-to-role)して、コア Azure AD 管理者から委任することをお勧めします。 このユーザーは、サインイン UI、PowerShell スクリプト、または API を使用して、パートナー組織の他のユーザーを招待できます。 これにより、Azure AD 管理者がパートナー組織のユーザーに招待または再送信する際の管理負担が軽減されます。

**パートナーが多要素認証を使用していない場合、Contoso がゲストユーザーに対して multi-factor authentication を強制することはできますか。**

はい。 詳細については、「 [B2B コラボレーションユーザーの条件付きアクセス](/azure/active-directory/active-directory-b2b-mfa-instructions)」を参照してください。

**招待されたパートナーがフェデレーションを使用して独自のオンプレミス認証を追加するとき、B2B コラボレーションはどのように機能しますか?**

パートナーの Azure AD テナントがオンプレミス認証インフラストラクチャにフェデレーションされている場合、オンプレミスのシングル サインオン (SSO) が自動的に実行されます。 パートナーが Azure AD テナントを持っていない場合は、新しいユーザーに対して Azure AD アカウントを作成できます。

**コンシューマーの電子メールアカウントを使用してゲストユーザーを招待することはできますか。**

コンシューマー電子メールアカウントを使用してゲストユーザーを招待することは Power BI でサポートされています。 これには、hotmail.com、outlook.com、gmail.com などのドメインが含まれます。 ただし、これらのユーザーには、職場または学校アカウントを持つユーザー以外の制限が発生する可能性があります。