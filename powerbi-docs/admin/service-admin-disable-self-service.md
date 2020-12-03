---
title: セルフサービスでのサインアップと購入を有効または無効にする
description: ユーザーが Power BI サービスにサインアップしてライセンスを購入またはアップグレードする機能を管理者が無効にする方法について説明します。
author: mihart
ms.author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 04/08/2020
ms.custom: licensing support
LocalizationGroup: Administration
ms.openlocfilehash: ff695d49caeab7bed88b932cec6aaec11ec4df29
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96413681"
---
# <a name="enable-or-disable-self-service-sign-up-and-purchasing"></a>セルフサービスでのサインアップと購入を有効または無効にする

ほとんどの組織では、セルフサービスでのサインアップが既定で有効になっています。 組織内の個々のユーザーは、職場または学校のアカウントを使用して、Power BI にサインアップできます。 また、ユーザーが Power BI Pro を必要とする機能を使用しようとした場合に Pro ライセンスを直接購入するオプションが、ユーザーに提供されることもあります。 管理者は、セルフサービスでのサインアップを有効にするか無効にするかを決定します。 また、組織内のユーザーがセルフサービスでの購入を行って自分のライセンスを取得できるかどうかを制御することもできます。

> [!NOTE]
>Microsoft クラウド ソリューション プロバイダー (CSP) から Power BI を入手した場合、ユーザーが個別にサインアップできないようにするため、設定が無効になっている可能性があります。 CSP が組織のグローバル管理者として機能していて、この設定を変更するときは CSP に連絡して支援を求めるよう要求している場合があります。
>
>

セルフサービスでのサインアップと購入を制御する設定を変更するには、PowerShell のコマンドを使用します。 組織内のユーザーがセルフサービスでのサインアップまたはセルフサービスでの購入を行うことができるかを制御する設定は 2 つあります。

- セルフサービスでのサインアップをすべて無効にする場合は、Azure AD PowerShell コマンドを使用して、Azure Active Directory の **AllowAdHocSubscriptions** という名前の設定を変更します。 [セルフサービスでのサインアップを有効または無効にする](#enable-or-disable-self-service-signup)には、この記事の手順に従ってください。 このオプションを使用すると、Microsoft クラウドベースの "*すべて*" のアプリとサービスに対するセルフサービスでのサインアップが無効になります。

- ユーザーが独自に Pro ライセンスを購入できないようにするには、MSCommerce PowerShell コマンドを使用して **AllowSelfServicePurchase** の設定を変更します。 この設定を使うと、特定の製品のセルフサービスでの購入を無効にすることができます。 [Power BI Pro ライセンスのセルフサービスでの購入を有効または無効にする](#enable-or-disable-self-service-purchase)には、この記事の手順に従ってください。

## <a name="enable-or-disable-self-service-signup"></a>セルフサービスでのサインアップを有効または無効にする

セルフサービスでのサインアップが有効になっている場合、**AllowAdHocSubscriptions** の値は *true* です。 この設定を *false* に変更するとどうなるか見てみましょう。

- この設定を true から false に変更した場合、組織の新しいユーザーは個人としてサインアップすることができなくなります。 設定を変更する前に Power BI にサインアップしていたユーザーのライセンスは、そのまま保持されきます。

- 設定を false に変更した場合でも、Power BI Free ライセンスを既に所有していたユーザーは、個人用の Power BI Pro 試用版にサインアップできます。

- 管理者は、すべての Power BI ライセンスを、それを必要とする新規ユーザーに割り当てる必要があります。

### <a name="before-you-begin"></a>始める前に

以下の手順では、Azure Active Directory の PowerShell コマンドを使用して、**AllowAdHocSubscriptions** の設定の値を変更します。 これらのコマンドを使用するには、Azure AD PowerShell モジュールがインストールされている必要があります。 PowerShell の使用について詳しくは、「[Windows PowerShell ファースト ステップ ガイド](/powershell/scripting/getting-started/getting-started-with-windows-powershell?view=powershell-7)」をご覧ください。

Azure AD モジュールをインストールするには、管理者として Windows PowerShell を開始します。 ローカル実行ポリシーでスクリプトの実行が許可されていることを確認してください。 問題が発生した場合は、「[PowerShell 実行ポリシー](/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7#powershell-execution-policies)」を参照し、ローカル ポリシーを変更する方法を確認してください。

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

## <a name="enable-or-disable-self-service-purchase"></a>セルフサービスでの購入を有効または無効にする

セルフサービスでの購入が有効になっている場合は、**AllowSelfServicePurchase** の値は *true* です。 この設定を *false* に変更するとどうなるか見てみましょう。

- この設定を true から false に変更した場合、組織のユーザーは、独自に Power BI Pro ライセンスを購入できなくなります。 設定を変更する前にライセンスを購入していたユーザーのライセンスは、そのまま保持されきます。

- 設定を false に変更した場合、Power BI Free ライセンスを所有しているユーザーでも、個人用の Power BI Pro ライセンスを入手できません。 

- 管理者は、それが必要なすべてのユーザーに Pro ライセンスを割り当てる必要があります。

### <a name="before-you-begin"></a>始める前に

以下の手順では、MSCommerce PowerShell コマンドを使用して、**AllowSelfServicePurchase** の設定の値を変更します。 これらのコマンドを使用するには、MSCommerce PowerShell モジュールがインストールされている必要があります。 PowerShell の使用について詳しくは、「[Windows PowerShell ファースト ステップ ガイド](/powershell/scripting/getting-started/getting-started-with-windows-powershell?view=powershell-7)」をご覧ください。

MSCommerce モジュールをインストールするには、管理者として Windows PowerShell を開始します。 ローカル実行ポリシーでスクリプトの実行が許可されていることを確認してください。 問題が発生した場合は、「[PowerShell 実行ポリシー](/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7#powershell-execution-policies)」を参照し、ローカル ポリシーを変更する方法を確認してください。

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

## <a name="next-steps"></a>次の手順

Power BI および他の Power Platform におけるセルフサービスでの購入の詳細については、次の記事を参照してください。

- [セルフサービスでの購入に関してよくあるご質問](/microsoft-365/commerce/subscriptions/self-service-purchase-faq?view=o365-worldwide#admin-capabilities)
- [MSCommerce PowerShell モジュールに対して AllowSelfServicePurchase を使用する](/microsoft-365/commerce/subscriptions/allowselfservicepurchase-powershell?view=o365-worldwide)