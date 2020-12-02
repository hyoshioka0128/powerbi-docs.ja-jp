---
title: 代替メール アドレスの使用
description: 代替メール アドレスの使用
author: mihart
ms.author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/23/2019
LocalizationGroup: Troubleshooting
ms.openlocfilehash: b03ecff1bcb74789adfea640c0279b568a09ffc7
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96409081"
---
# <a name="use-an-alternate-email-address"></a>代替メール アドレスの使用

Power BI にサインアップするときには、メール アドレスを入力します。 既定では、Power BI はこのアドレスを使用して、サービスのアクティビティに関する更新を送信します。 たとえば、他のユーザーから送信される共有の招待は、このアドレスに配信されます。

場合によっては、サインアップ時のものとは異なるメール アドレスにメールを配信してほしいことがありあります。 この記事では、Microsoft 365 および PowerShell で代替アドレスを指定する方法について説明します。 この記事では、Azure Active Directory (Azure AD) でのメール アドレスの解決方法についても説明します。

> [!NOTE]
> 代替アドレスを指定しても、電子メール サブスクリプション、サービス更新、ニュースレター、その他のプロモーション通信に Power BI で使用されるメール アドレスに影響はありません。 これらの通信は常に、Power BI へのサインアップ時に使用したメール アドレスに送信されます。

## <a name="use-microsoft-365"></a>Microsoft 365 を使用する

Microsoft 365 で代替アドレスを指定するには、次の手順に従います。

1. アカウントの[個人情報](https://portal.office.com/account/#personalinfo)ページを開きます。 アプリのプロンプトが表示されたら、Power BI に使用するメール アドレスとパスワードを使用してサインインします。

1. 左側のメニューで、 **[個人情報]** を選択します。

1. **[連絡先の詳細]** セクションで、 **[編集]** を選択します。

    詳細を編集できない場合は、ご自分のメール アドレスが管理者によって管理されていることを意味します。 管理者に連絡して、メール アドレスを更新してください。

    ![連絡用メール アドレスの指定方法を示している [連絡先の詳細] ダイアログのスクリーンショット。](media/service-admin-alternate-email-address-for-power-bi/contact-details.png)

1. **[連絡用メール アドレス]** フィールドに、Microsoft 365 で Power BI の更新用に使用されるメール アドレスを入力します。

## <a name="use-powershell"></a>PowerShell を使用する

PowerShell で代替アドレスを指定するには、[Set-AzureADUser](/powershell/module/azuread/set-azureaduser/) コマンドを使用します。

```powershell
Set-AzureADUser -ObjectId john@contoso.com -OtherMails "otheremail@somedomain.com"
```

## <a name="email-address-resolution-in-azure-ad"></a>Azure AD でのメール アドレスの解決

Power BI 用の Azure AD 埋め込みトークンをキャプチャするには、3 種類のメール アドレスのいずれかを使用できます。

* ユーザーの Azure AD アカウントに関連付けられている主なメール アドレス

* UserPrincipalName (UPN) メール アドレス

* "*その他のメール アドレス*" 配列属性

Power BI では、次の順序で使用するメール アドレスが選択されます。

1. Azure AD テナントのユーザー オブジェクトにメール属性が存在する場合、Power BI はそのメール属性をメール アドレスに使います。

1. UPN メールが **\*.onmicrosoft.com** ドメイン メール アドレス ("\@" 記号の後の情報) では *ない* 場合、Power BI ではそのメール属性をメール アドレスに使用します。

1. Azure AD ユーザー オブジェクトに "*他のメール アドレス*" 配列属性が存在する場合、Power BI では、そのリストの最初のメール (この属性にはメールのリストが存在する可能性があるため) が使われます。

1. 上記の条件のいずれも存在しない場合、Power BI では UPN アドレスが使用されます。

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。
