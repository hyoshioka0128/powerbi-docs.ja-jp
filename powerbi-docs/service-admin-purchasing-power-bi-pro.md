---
title: Power BI Pro のライセンスを購入して割り当てる
description: Power BI Pro のユーザー ライセンスを購入してユーザーに割り当てて、ユーザーが Power BI サービスのコンテンツにアクセスして他のユーザーと共同作業を行えるようにする方法を説明します。
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 01/16/2020
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 138173d30b9c37c04047c61dbd04cbd3101696aa
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2020
ms.locfileid: "76753193"
---
# <a name="purchase-and-assign-power-bi-pro-user-licenses"></a>Power BI Pro のユーザー ライセンスを購入して割り当てる

>[!IMPORTANT]
>Power BI Pro のライセンスにアップグレードする準備はできていますか? アカウントを設定するには、「[Power BI Pro を使ってみましょう](https://go.microsoft.com/fwlink/?LinkId=2106428&clcid=0x409&cmpid=pbidocs-purchasing-power-bi-pro)」に直接移動します。

Power BI Pro は、他のユーザーが Power BI サービスに発行したレポートやダッシュボードの読み取りと操作を行うことができるようにする個別のユーザー ライセンスです。 このライセンスの種類が割り当てられたユーザーは、他の Power BI Pro ユーザーとコンテンツを共有して共同作業を行うことができます。 コンテンツが Power BI Premium 容量でホストされている場合を除き、Power BI Pro ユーザーだけが、コンテンツを発行したり他のユーザーと共有したり、他のユーザーが作成したコンテンツを利用したりできます。 詳細については、「[Power BI の価格](https://powerbi.microsoft.com/pricing/)」の「_Power BI 機能の比較_」セクションを参照してください。

## <a name="purchase-power-bi-pro-user-licenses"></a>Power BI Pro ユーザー ライセンスを購入する

この記事では、Microsoft 365 管理センターで Power BI Pro ユーザー ライセンスを購入する方法について説明します。 ライセンスを購入した後、Microsoft 365 管理センターまたは Azure portal でユーザーに割り当てることができます。

> [!NOTE]
> 2020 年 1 月 14 日以降、米国の商用クラウドのお客様は、Power Platform 製品 (Power BI、Power Apps、および Power Automate) のセルフサービス購入、サブスクリプション、およびライセンス管理機能を利用できます。 組織でセルフサービス購入を有効または無効にする手順などの詳細については、「[セルフサービス購入に関する FAQ](https://docs.microsoft.com/microsoft-365/commerce/subscriptions/self-service-purchase-faq)」を参照してください。

### <a name="prerequisites"></a>前提条件

Microsoft 365 管理センターでライセンスを購入して割り当てるには、Microsoft 365 の **[グローバル管理者または課金管理者](https://support.office.com/article/about-office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d)** のどちらかのロールのメンバーであることが必要です。

Azure portal でライセンスの割り当てを行うユーザーは、Power BI が Azure Active Directory 参照で使用する Azure サブスクリプションの所有者である必要があります。

### <a name="purchase-licenses-in-microsoft-365"></a>Microsoft 365 でライセンスを購入する

Microsoft 365 管理センターで Power BI Pro ライセンスを購入するには、次の手順に従います。

1. [Microsoft 365 管理センター](https://admin.microsoft.com)にサインインします。

2. ナビゲーション メニューで、 **[課金]**  >  **[サービスの購入]** を選択します。

3. 検索またはスクロールして、購入するサブスクリプションを見つけます。 **Power BI** は、ページの下部の近くにある **[Other categories that might interest you]\(興味深いその他のカテゴリ\)** に表示されます。 リンクを選択すると、組織で利用可能な Power BI サブスクリプションが表示されます。

4. **[Power BI Pro]** を選択します。

5. **[サービスの購入]** ページで、 **[購入]** を選択します。

6. 支払い方法に応じて、 **[月払い]** または **[1 年分支払う]** を選択します。

7. **[ユーザーはいくつ必要ですか?]** に購入するライセンスの数を入力してから、 **[今すぐ支払う]** を選択してトランザクションを完了します。

8. 購入を確認するには、 **[課金]**  >  **[製品とサービス]** を参照し、 **[Power BI Pro]** を探します。

9. 後でライセンスを追加するには、 **[製品とサービス]** ページで **[Power BI Pro]** を見つけ、 **[ライセンスの追加/削除]** を選択します。

## <a name="assign-licenses-in-the-microsoft-365-admin-center"></a>Microsoft 365 管理センターでライセンスを割り当てる

Microsoft 365 管理センターでライセンスを割り当てる方法については、「[ユーザーにライセンスを割り当てる](/office365/admin/manage/assign-licenses-to-users)」を参照してください。

ゲスト ユーザーについては、「[[ライセンス] ページでユーザーにライセンスを割り当てる](/office365/admin/manage/assign-licenses-to-users#assign-licenses-to-users-on-the-licenses-page)」を参照してください。 ゲスト ユーザーに Pro ライセンスを割り当てる前に、Microsoft アカウントの担当者に連絡して、Microsoft との契約条件に準拠していることを確認してください。

## <a name="assign-licenses-in-the-azure-portal"></a>Azure portal でライセンスを割り当てる

次の手順に従って、個々のユーザー アカウントに Power BI Pro ライセンスを割り当てます。

1. [Azure portal](https://portal.azure.com/) にサインインします。

2. **Azure Active Directory** を検索して選択します。

3. **Azure Active Directory** リソース メニューで、 **[管理]** の下にある **[ライセンス]** を選択します。

4. **[ライセンス - 概要]** リソース メニューから **[すべての製品]** を選択します。次に **[Power BI Pro]** を選択して、ライセンス ユーザーの一覧を表示します。

5. コマンド バーで、 **[+ 割り当て]** を選択します。 **[ライセンスの割り当て]** ページで、まずユーザーを選択します。次に **[割り当てオプション]** を選択して、選択したユーザー アカウントの Power BI Pro ライセンスを有効にします。

## <a name="next-steps"></a>次の手順

ライセンスの割り当てが終わりました。Power BI Pro の詳細を確認してください。

[組織での Power BI のライセンス](service-admin-licensing-organization.md)

[サインインした Power BI ユーザーを見つける](service-admin-access-usage.md)

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
