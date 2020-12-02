---
title: Microsoft Intune でモバイル アプリを構成する
description: Microsoft Intune で Power BI モバイル アプリを構成する方法。 これには、アプリケーションを追加する方法と、展開する方法が含まれます。 また、セキュリティを管理するためにモバイル アプリケーション ポリシーを作成する方法も含まれます。
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 09/25/2020
LocalizationGroup: Administration
ms.openlocfilehash: 6ca9b241fe2d6f2914a603e722f2dd2c216e05df
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96408782"
---
# <a name="configure-mobile-apps-with-microsoft-intune"></a>Microsoft Intune でモバイル アプリを構成する

Microsoft Intune を使うと、組織でデバイスとアプリケーションを管理できます。 iOS および Android 用の Power BI モバイル アプリケーションは、Intune と統合されます。 この統合により、デバイス上のアプリケーションを管理し、セキュリティを制御することができます。 構成ポリシーを利用すると、アクセス PIN の要求、アプリケーションによるデータの処理方法、アプリが使用されていないときのアプリケーション データの暗号化といったことを制御できます。

Microsoft Power BI モバイル アプリを使用すると、重要なビジネス情報にアクセスできます。 組織のすべてのマネージド デバイスとアプリのビジネス データについて、ダッシュボードとレポートを表示して、操作することができます。 サポートされている Intune アプリの詳細については、「[保護されている Microsoft Intune アプリ](/intune/apps/apps-supported-intune-apps)」を参照してください。

## <a name="general-mobile-device-management-configuration"></a>全般的なモバイル デバイス管理の構成

この記事では、Intune が適切に構成されていることと、Intune に登録したデバイスがあることを想定しています。 この記事は、Microsoft Intune の構成に関する完全なガイドではありません。 Intune について詳しくは、「[Intune とは何か](/intune/introduction-intune/)」をご覧ください。

Microsoft Intune は、Microsoft 365 内でモバイル デバイス管理 (MDM) と共存できます。 MDM を使用している場合、デバイスは MDM に登録されているように表示されますが、Intune でも管理できます。

エンド ユーザーが自分のデバイスで Power BI アプリを使用できるようにするには、Intune 管理者がアプリを Intune に追加し、さらにそのアプリをエンド ユーザーに割り当てる必要があります。

> [!NOTE]
> Intune を構成した後は、iOS または Android デバイス上の Power BI モバイル アプリに対するバックグラウンド データ更新はオフになります。 アプリに移動すると、Web 上の Power BI サービスからデータが更新されます。

## <a name="step-1-add-the-power-bi-app-to-intune"></a>手順 1:Power BI アプリを Intune に追加する

Power BI アプリを Intune に追加するには、次のトピックに記載されている手順に従います。
- [iOS ストア アプリを Microsoft Intune に追加する](/intune/apps/store-apps-ios)
- [Android ストア アプリを Microsoft Intune に追加する](/intune/apps/store-apps-android)

## <a name="step-2-assign-the-app-to-your-end-users"></a>手順 2:エンド ユーザーにアプリを割り当てる

Microsoft Intune に Power BI アプリを追加したら、アプリをユーザーとデバイスに割り当てることができます。 デバイスが Intune で管理されているかどうかにかかわらず、アプリをデバイスに割り当てることができることに注意することが重要です。

Power BI アプリをユーザーとデバイスに割り当てるには、「[Microsoft Intune を使用してアプリをグループに割り当てる](/intune/apps/apps-deploy)」に記載されている手順に従います。

## <a name="step-3-create-and-assign-app-protection-policies"></a>手順 3:アプリ保護ポリシーを作成して割り当てる

アプリ保護ポリシー (APP) は、組織のデータが安全な状態にあるか、またはマネージド アプリ内に格納されることを保証するルールです。 ポリシーの例としては、ユーザーが "企業" データへのアクセスまたは移動を試みた場合や、アプリ内で禁止または監視されている一連の操作を試みた場合に適用されるルールがあります。 管理対象アプリは、アプリ保護ポリシーが適用されたアプリであり、Intune で管理できます。

モバイル アプリケーション管理 (MAM) のアプリ保護ポリシーを使用すると、アプリケーション内の組織のデータを管理して保護することができます。 登録を必要としない MAM (MAM-WE) を使用すれば、機密データが含まれる職場または学校関連のアプリを、Bring Your Own Device (BYOD) シナリオにおける個人所有デバイスを含むほぼすべてのデバイスで管理できます。 詳しくは、「[アプリ保護ポリシーの概要](/intune/apps/app-protection-policy)」をご覧ください。

Power BI アプリのアプリ保護ポリシーを作成して割り当てるには、「[アプリ保護ポリシーを作成して割り当てる方法](/intune/apps/app-protection-policies)」に記載されている手順に従います。

## <a name="step-4-use-the-application-on-a-device"></a>手順 4.デバイスでアプリケーションを使用する

管理対象アプリとは、そのアプリでアクセス可能な会社のデータを保護できるよう会社のサポートがセットアップ可能なアプリです。 デバイスの管理対象アプリで会社のデータにアクセスすると、予期していたアプリの動作とは少し異なることがわかります。 たとえば、保護された会社のデータをコピーして貼り付けできない、またはそのデータを特定の場所に保存できない場合があります。

エンド ユーザーが自分のデバイスで Power BI アプリを使用する方法を理解するには、次の記事に記載されている手順を確認してください。
- [iOS デバイスで管理対象アプリを使用する](/intune-user-help/use-managed-apps-on-your-device-ios#how-do-i-get-managed-apps)
- [Android デバイスで管理対象アプリを使用する](/intune-user-help/use-managed-apps-on-your-device-android)

## <a name="next-steps"></a>次のステップ

[アプリ保護ポリシーを作成して割り当てる方法](/intune/app-protection-policies) 

[モバイル デバイス用 Power BI アプリ](../consumer/mobile/mobile-apps-for-mobile-devices.md)  

その他の質問 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。