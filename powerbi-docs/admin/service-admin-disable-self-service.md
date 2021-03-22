---
title: セルフサービスでのサインアップと購入を有効または無効にする
description: ユーザーが Power BI サービスにサインアップしてライセンスを購入またはアップグレードする機能を管理者が無効にする方法について説明します。
author: mihart
ms.author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 03/12/2021
ms.custom: licensing support
LocalizationGroup: Administration
ms.openlocfilehash: 9db03ae13dab7c888042059b35b408c6f890df37
ms.sourcegitcommit: 0e3afa7653c992b09702ed67dac79a967a9dac3a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2021
ms.locfileid: "103413186"
---
# <a name="enable-or-disable-self-service-sign-up-and-purchasing"></a>セルフサービスでのサインアップと購入を有効または無効にする

## <a name="what-is-self-service"></a>セルフサービスとは

セルフサービスとは、組織 (職場または学校) 内の個人が、自分の代わりにアクションを実行することを組織に依頼することなく、組織のサブスクリプションによって支払いが行われているサービスを使用したり、無料のサービスを使用したりするために、サインアップできる機能のことです。 個人は Microsoft の Web サイトに移動し、組織が提供しているクラウド サービスを見つけて、組織のメール アドレスを使用してそのサービスにサインアップします。 

多くの場合、そのサービスへのサブスクリプションに対して組織が料金を支払っています。 そうでない場合は、その個人が最初のユーザーであり、サービスの管理者になります。 試用版または無料ライセンスの場合、購入の必要はありません。 ただし、Power BI Pro および Power BI Premium Per User ライセンスの場合、組織は月額料金を支払う責任があります。 

Microsoft 365 管理者は、試用版、ライセンス、およびサブスクリプションにサインアップしたユーザーを確認できます。

> [!NOTE]
> セルフサービスでのサインアップは、商用クラウドのお客様のみに適用され、国内クラウドまたは政府機関のお客様は対象外です。

## <a name="when-to-use-self-service-sign-up-and-purchase"></a>セルフサービスでのサインアップと購入を使用する場合

### <a name="self-service-is-a-good-idea"></a>セルフサービスが適している場合: 

- 大規模で分散型の組織 (職場または学校) の場合。そこでは多くの場合、自分で使用するために SaaS (サービスとしてのソフトウェア) ライセンスを購入する柔軟性が個人に与えられています。 
- 1 人または少人数の組織で、1 つの Power BI Pro ライセンスのみ、または少数のライセンスのみを購入する必要がある場合。
- 組織全体のサブスクリプションを購入する前に、個人で Power BI を試し、習熟することに関心がある場合。
- Power BI Free ライセンスを使用している現在のユーザーが、コンテンツを作成して共有する必要が生じて Power BI Pro 試用版にアップグレードする必要がある場合。 Power BI Pro ライセンスを既に持っているユーザーは、セルフサービスを使用して Power BI Premium Per User ライセンスにアップグレードすることもできます。

### <a name="you-may-want-to-disable-self-service-when"></a>セルフサービスを無効にしてかまわない場合:

- 組織に、コンプライアンス、規制、セキュリティ、ガバナンスのニーズを満たすための調達プロセスが確立されている。 すべてのライセンスが定義されたプロセスに従って承認および管理されるようにする必要があります。 
- 組織に、必須のトレーニングや、データ保護ポリシーのユーザーによる確認など、新しい Power BI Pro または Premium Per User ライセンスに対する要件がある。
- 組織が、データのプライバシーまたはその他の懸念を理由に Power BI サービスの使用を禁止していて、Power BI Free ライセンスの割り当てを非常に厳密に制御する必要がある。
- 交渉または割引されたライセンス料金を利用するために、すべての Power BI Pro または Premium Per User ライセンスがエンタープライズ契約に従っていることを確認する。
- Power BI Free ライセンスを使用している現在のユーザーが、Power BI Pro ライセンスを試用するか直接購入するかの確認を求められている。 セキュリティ、プライバシー、または費用を理由に、このようなユーザーがアップグレードすることを組織が望まない場合があります。

## <a name="enable-and-disable-self-service"></a>セルフサービスを有効または無効にする

管理者は、セルフサービスでのサインアップを有効にするか無効にするかを決定します。 また、組織内のユーザーがセルフサービスでの購入を行って自分のライセンスを取得できるかどうかを決定することもできます。 

セルフサービス サインアップを無効にすると、ユーザーはデータの視覚化と分析のために Power BI を探索できなくなります。 個々のサインアップをブロックする場合、組織用に Power BI Free ライセンスを取得して、すべてのユーザーに割り当てることができます。 

> [!NOTE]
>Microsoft クラウド ソリューション プロバイダー (CSP) から Power BI を入手した場合、ユーザーが個別にサインアップできないようにするために、設定が無効になっている可能性があります。 CSP が組織のグローバル管理者として機能していて、この設定を変更するときは CSP に連絡して支援を求めるよう要求している場合があります。
>


 セルフサービスでのサインアップと購入を制御する設定を変更するには、PowerShell のコマンドを使用します。 

- セルフサービスでのサインアップをすべて無効にする場合は、Azure AD PowerShell コマンドを使用して、Azure Active Directory の **AllowAdHocSubscriptions** という名前の設定を変更します。 [セルフサービスでのサインアップを有効または無効にする](#enable-or-disable-self-service-sign-up-for-your-organization)には、この記事の手順に従ってください。 このオプションを使用すると、Microsoft クラウドベースの "*すべて*" のアプリとサービスに対するセルフサービスでのサインアップが無効になります。

- ユーザーが独自に Pro ライセンスを購入できないようにするには、MSCommerce PowerShell コマンドを使用して **AllowSelfServicePurchase** の設定を変更します。 この設定を使うと、特定の製品のセルフサービスでの購入を無効にすることができます。 [Power BI Pro ライセンスのセルフサービスでの購入を有効または無効にする](#enable-or-disable-self-service-purchase-in-your-organization)には、この記事の手順に従ってください。

## <a name="enable-or-disable-self-service-sign-up-for-your-organization"></a>組織に対してセルフサービスでのサインアップを有効または無効にする

セルフサービスでのサインアップが有効になっている場合、**AllowAdHocSubscriptions** の値は *true* です。 この設定を *false* に変更するとどうなるか見てみましょう。

- 組織内の新規ユーザーは、個別にサインアップできなくなります。 設定を変更する前に Power BI にサインアップしていたユーザーのライセンスは、そのまま保持されます。

- Power BI Free ライセンスを既に所有しているユーザーは、引き続き個人用の Power BI Pro 試用版にサインアップできます。

- 管理者は、すべての Power BI ライセンスを、それを必要とする新規ユーザーに割り当てる必要があります。

### <a name="before-you-begin"></a>始める前に

以下の手順では、Azure Active Directory の PowerShell コマンドを使用して、**AllowAdHocSubscriptions** の設定の値を変更します。 これらのコマンドを使用するには、Azure AD PowerShell モジュールがインストールされている必要があります。 PowerShell の使用について詳しくは、「[Windows PowerShell ファースト ステップ ガイド](/powershell/scripting/getting-started/getting-started-with-windows-powershell)」をご覧ください。

Azure AD モジュールをインストールするには、管理者として Windows PowerShell を開始します。 ローカル実行ポリシーでスクリプトの実行が許可されていることを確認してください。 問題が発生した場合は、「[PowerShell 実行ポリシー](/powershell/module/microsoft.powershell.core/about/about_execution_policies#powershell-execution-policies)」を参照し、ローカル ポリシーを変更する方法を確認してください。

Azure AD モジュールをインストールするには、次のコマンドを実行します。

```powershell
Install-Module MSOnline
```

### <a name="change-the-self-service-signup-policy"></a>セルフサービスでのサインアップのポリシーを変更する

PowerShell で次のコマンドを実行して、Azure AD に接続します。

```powershell
Connect-MsolService
```

サインイン ダイアログで管理者の資格情報を入力し、必要に応じて、2 要素認証を完了します。 検証が済むと、PowerShell ウィンドウに戻ります。

現在の設定を表示するには、次のコマンドを実行します。 "fl" スイッチを使用することで、出力は書式設定されたリストにパイプされます。

```powershell
Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
```

現在の設定を変更するには、次のコマンドを実行します。

```powershell
Set-MsolCompanySettings -AllowAdHocSubscriptions $false
```

このコマンドを実行すると、すべてのユーザーに対してセルフサービスでのサインアップが無効になります。 有効に戻すには、このコマンドをもう一度実行して、値を $true に設定します。

## <a name="enable-or-disable-self-service-purchase-in-your-organization"></a>組織に対してセルフサービスでの購入を有効または無効にする

セルフサービスでの購入が有効になっている場合は、**AllowSelfServicePurchase** の値は *true* です。 この設定を *false* に変更するとどうなるか見てみましょう。

- 組織内のユーザーは、自分の Power BI Pro ライセンスを購入できなくなります。 設定を変更する前にライセンスを購入していたユーザーのライセンスは、そのまま保持されます。

- Power BI Free ライセンスを所有しているユーザーでも、個人用の Power BI Pro ライセンスを入手できません。 

- 管理者は、それが必要なすべてのユーザーに Pro ライセンスを割り当てる必要があります。

### <a name="before-you-begin"></a>始める前に

以下の手順では、MSCommerce PowerShell コマンドを使用して、**AllowSelfServicePurchase** の設定の値を変更します。 これらのコマンドを使用するには、MSCommerce PowerShell モジュールがインストールされている必要があります。 PowerShell の使用について詳しくは、「[Windows PowerShell ファースト ステップ ガイド](/powershell/scripting/getting-started/getting-started-with-windows-powershell)」をご覧ください。

MSCommerce モジュールをインストールするには、管理者として Windows PowerShell を開始します。 ローカル実行ポリシーでスクリプトの実行が許可されていることを確認してください。 問題が発生した場合は、「[PowerShell 実行ポリシー](/powershell/module/microsoft.powershell.core/about/about_execution_policies#powershell-execution-policies)」を参照し、ローカル ポリシーを変更する方法を確認してください。

MSCommerce モジュールをインストールするには、次のコマンドを実行します。

```powershell
Install-Module -name MSCommerce
```

### <a name="change-the-self-service-signup-policy"></a>セルフサービスでのサインアップのポリシーを変更する

PowerShell で次のコマンドを実行して接続します。

```powershell
Connect-MSCommerce
```

サインイン ダイアログで管理者の資格情報を入力し、必要に応じて、2 要素認証を完了します。 検証が済むと、PowerShell ウィンドウに接続が成功したことが表示されます。

現在の設定を表示するには、次のコマンドを実行します。 テキストが切り捨てられないようにするため、"fl" スイッチを使用して、出力を書式設定されたリストにパイプします。

```powershell
Get-MSCommercePolicy -PolicyId AllowSelfServicePurchase | fl
```

**ProductId** を指定することにより、個別の製品について、セルフサービスでの購入を許可する設定を無効にできます。 Power BI サービスの現在の設定を変更するには、次のコマンドを実行します。

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0L3PB -Enabled $False
```

このコマンドを実行すると、すべてのユーザーについて、Power BI のセルフサービスでの購入が無効になります。 有効に戻すには、このコマンドをもう一度実行して、値を $true に設定します。

## <a name="what-to-do-if-individuals-have-already-used-self-service"></a>個人が既にセルフサービスを使用している場合の対処方法

セルフサービスでのサインアップと購入は、どちらも既定で有効になっています。 このため、組織内の個人が Power BI のライセンスとサブスクリプションを既に所有している可能性があります。 アクションを実行するかどうかにかかわらず、既に存在するものを明確に把握しておく必要があります。

セルフ サービス サインアップでテナントに参加したユーザーには、管理ダッシュボードの [アクティブ ユーザー] ペインでフィルター処理することができる一意のライセンスが割り当てられます。 この新しいビューを作成するには、次の手順のようにします。

1. Microsoft 365 管理センターに移動します。

1. ナビ ペインで、 **[ユーザー]**  >  **[アクティブ ユーザー]** の順に選択します。

1. [ビュー] メニューの **[カスタム ビューの追加]** を選択します。

1. 新しいビューに名前を付け、 [割り当て済みの製品ライセンス] で、 [Power BI (無料)] または [Power BI Pro] を選択します。

    ビューごとにライセンスを 1 つだけ選択できます。 組織内に Power BI (無料) のライセンスと Power BI Pro のライセンスがある場合は、2 つのビューを作成できます。

1. 他の必要な条件を入力した後、 **[追加]** を選択します。

    新しく作成したビューは、 [ビュー] メニューから使用できます。


    > [!NOTE]
    > 組織に、電子メール ドメインに接続されている Microsoft 365 環境がない場合、セルフサービス ユーザーは新しいクラウド専用のユーザー ディレクトリに追加されています。 既に作成済みのテナントを検索、要求、および[引き継ぐ](/azure/active-directory/users-groups-roles/domains-admin-takeover)ことが必要になる場合があります。 

## <a name="next-steps"></a>次の手順

Power BI および他の Power Platform におけるセルフサービスでの購入の詳細については、次の記事を参照してください。

- [セルフサービスでの購入に関してよくあるご質問](/microsoft-365/commerce/subscriptions/self-service-purchase-faq#admin-capabilities)
- [MSCommerce PowerShell モジュールに対して AllowSelfServicePurchase を使用する](/microsoft-365/commerce/subscriptions/allowselfservicepurchase-powershell)