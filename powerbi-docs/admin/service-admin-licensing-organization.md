---
title: 組織のユーザーのための Power BI のライセンス
description: Power BI で使用できるさまざまなユーザー ライセンスの種類の概要と、管理者が組織のユーザーのためにライセンスを購入して管理する方法。
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 05/14/2020
ms.author: kfollis
ms.custom: licensing support
LocalizationGroup: Administration
ms.openlocfilehash: 5bac52e98830c97262945e1434880f9c178a0932
ms.sourcegitcommit: 3f864ec22f99ca9e25cda3a5abda8a5f69ccfa8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2020
ms.locfileid: "84159998"
---
# <a name="licensing-the-power-bi-service-for-users-in-your-organization"></a>組織のユーザーに Power BI サービスのライセンスを与える

Power BI サービスでユーザーが実行できる操作は、そのユーザーが持っているユーザーごとのライセンスの種類によって異なります。 各自のライセンスによって提供されるアクセス レベルは、アクセスしているワークスペースが Power BI Premium 容量に割り当てられているかどうかによって異なります。 Power BI サービスのすべてのユーザーにライセンスが必要です。

ユーザーがライセンスを取得する方法は 2 つあります。 ユーザーは、セルフサービス サインアップ機能と職場または学校アカウントを使用して、無料または Pro ライセンスを取得できます。 あるいは、管理者が Power BI サブスクリプションを取得し、ユーザーにライセンスを割り当てることができます。

この記事では、管理者の観点からのサービスの購入と、ユーザーごとのライセンスについて重点的に説明します。 ユーザーがライセンスを取得する方法の詳細については、「[個人として Power BI にサインアップする](../fundamentals/service-self-service-signup-for-power-bi.md)」を参照してください。

## <a name="who-can-purchase-and-assign-licenses"></a>ライセンスを購入して割り当てることができるユーザー

組織のライセンスを購入または割り当てるには、管理者ロールが割り当てられている必要があります。 管理者ロールは、Azure Active Directory 管理センターまたは Microsoft 365 管理センターを使用して割り当てられます。 次の表に、購入とライセンスに関連するタスクを実行するために必要なロールを示します。 Azure Active Directory での管理者ロールの詳細については、「[Azure Active Directory で管理者ロールを表示して割り当てる](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-manage-roles-portal)」を参照してください。 ベスト プラクティスなど、Microsoft 365 での管理者ロールの詳細については、「[管理者ロールについて」](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide)を参照してください。

| サービスとライセンスを購入できるユーザー | ユーザー ライセンスを管理できるユーザー |
| --------------- | --------------- |
| 課金管理者 | ライセンス管理者 |
| 全体管理者 | ユーザー管理者 |
|  | 全体管理者 |

これらのロールでは組織を管理します。 Power BI サービス管理者のロールについては、「[Power BI サービス管理者ロールについて](service-admin-role.md)」を参照してください。

## <a name="get-power-bi-for-your-organization"></a>組織の Power BI を取得する

グローバル管理者または課金管理者は、Power BI サービスにサインアップし、組織内のユーザーのライセンスを購入できます。 購入する準備ができていない場合は、Power BI Pro 試用版を選択してください。 25 個のライセンスを取得して、1 か月間ご利用いただけます。 サインアップの詳しい手順ついては、「[組織の Power BI サブスクリプションを取得する](service-admin-org-subscription.md)」を参照してください。

## <a name="about-self-service-sign-up"></a>セルフサービス サインアップについて

個々のユーザーは、職場または学校のアカウントでサインアップすることで、自分の Power BI ライセンスを取得できます。 無料ライセンスの場合、ユーザーはマイ ワークスペースを使用して Power BI の個人データの分析と視覚化を試すことができますが、他のユーザーと共有することはできません。 コンテンツを共有するには、Power BI Pro ライセンスが必要です。 ユーザーは、ライセンスの種類を Pro にアップグレードすることができます。また、組織で商用クラウドを使用している場合は、直接 Pro にサインアップすることができます。 Azure Government、Azure Germany、または Azure China 21Vianet クラウドにデプロイされた組織や教育機関では、Pro を直接購入したり、Pro にアップグレードしたりすることはできません。

組織内のユーザーがセルフサービス サインアップを使用できないようにする場合は、[セルフサービス サインアップの有効化または無効化](service-admin-disable-self-service.md)に関する記事を参照し、これをオフにする方法を確認してください。

組織内のどのユーザーが既にライセンスを所有している可能性があるかを確認する場合は、「[ユーザー ライセンスを表示および管理する](service-admin-manage-licenses.md)」を参照し、その方法を確認してください。

## <a name="license-types-and-capabilities"></a>ライセンスの種類と機能

Power BI ユーザーごとのライセンスには、無料と Pro の 2 種類があります。 ユーザーに必要なライセンスの種類は、コンテンツの格納場所とそのコンテンツとのやり取り方法によって決まります。 コンテンツを格納できる場所は、組織の[サブスクリプションの種類](#subscription-types)によって決まります。

サブスクリプションの種類の 1 つである、[Power BI Premium](service-admin-premium-purchase.md) では、無料ライセンスを持つユーザーが、Premium 容量に割り当てられているワークスペースのコンテンツを操作できます。 Premium 容量以外では、無料ライセンスを持つユーザーは、**マイ ワークスペース**内でデータに接続したり、レポートやダッシュボードを作成したりするためにのみ Power BI サービスを使用できます。 他のユーザーとコンテンツを共有したり、他のワークスペースにコンテンツを発行したりすることはできません。 ワークスペースの種類の詳細については、「[ワークスペースの種類](../consumer/end-user-workspaces.md#types-of-workspaces)」をご覧ください。

標準の Power BI サブスクリプションでは、共有容量が使用されます。 コンテンツが共有容量に格納されている場合、Power BI Pro ライセンスが割り当てられているユーザーは、他の Power BI Pro ユーザーとのみ共同作業できます。 他のユーザーが共有しているコンテンツの利用、アプリ ワークスペースへのコンテンツの発行、ダッシュボードの共有、ダッシュボードとレポートのサブスクライブを行うことができます。  ワークスペースが Premium 容量にある場合、Pro ユーザーは、Power BI Pro ライセンスを持っていないユーザーにコンテンツを配布できます。

以下の表は、各ライセンスの種類の基本的な機能をまとめたものです。 ライセンスの種類ごとの利用可能な機能の詳細については、「[ライセンスの種類別の機能](../fundamentals/service-features-license-type.md)」を参照してください。

| ライセンスの種類 | ワークスペースが共有容量にある場合の機能 | ワークスペースが Premium 容量にある場合のその他の機能 |
| --------- | ----------- | ----------- |
| Power BI (無料) | マイ ワークスペースのコンテンツにアクセスする | 共有されているコンテンツを使用する |
| Power BI Pro | 他のワークスペースへのコンテンツの発行、ダッシュボードの共有、ダッシュボードとレポートのサブスクライブ、Pro ライセンスを持つユーザーとの共有を行う | 無料ライセンスを持つユーザーにコンテンツを配布する |

## <a name="subscription-types"></a>サブスクリプションの種類

Microsoft からのすべてのユーザーベースの商用ライセンス サブスクリプションは、Azure Active Directory の ID に基づいています。 Power BI サービスを使用するには、商用ライセンス向けに Azure Active Directory でサポートされている ID を使用してサインインする必要があります。 ID サービスに Azure Active Directory が使用されている任意の Microsoft サブスクリプションに Power BI を追加することができます。 Office 365 E5 など、一部のサブスクリプションには Power BI Pro ライセンスが含まれているため、Power BI に対して個別のサインアップを行う必要はありません。

組織向けの Power BI サブスクリプションには、Standard と Premium の 2 種類があります。

標準のセルフサービス Power BI Pro サブスクリプションでは、管理者がユーザーごとのライセンスを割り当てます。 Power BI Pro ライセンスについては、ユーザーごとの月額料金が発生します。 このライセンスの種類では、コラボレーション、発行、共有、およびアドホック分析が可能になります。 コンテンツは、Microsoft によって完全に管理されている共有ストレージ容量に保存されます。

Power BI Premium サブスクリプションでは、組織に専用の容量が割り当てられます。 エンタープライズ BI、ビッグ データ分析、クラウドおよびオンプレミスのレポートに適しており、Premium では高度な管理とデプロイ制御が提供されます。 専用のコンピューティング リソースとストレージ リソースは、組織内の容量管理者によって管理されます。 この専用環境については、月額料金が発生します。 他の Premium の利点に加え、Premium 容量に格納されているコンテンツは、Power BI Pro ライセンスを持っていないユーザーがアクセスでき、それらのユーザーに配布することができます。 Premium を使用するには、少なくとも 1 人のユーザーに Power BI Pro ライセンスが割り当てられている必要があります。また、コンテンツ作成者と開発者には引き続き Power BI Pro ライセンスが必要です。

2 種類のサブスクリプションは相互に排他的ではありません。 Power BI Premium と Power BI Pro の両方を持つことができます。 この構成では、Premium 容量に格納されているコンテンツをすべてのユーザーと共有でき、共有容量も利用できます。 容量の制限については、「[Power BI ワークスペースでデータ ストレージを管理する](service-admin-manage-your-data-storage-in-power-bi.md)」を参照してください。

製品の機能と価格を比較する場合は、「[Power BI の価格](https://powerbi.microsoft.com/pricing)」を参照してください。

## <a name="guest-user-access"></a>ゲスト ユーザー アクセス

組織外のユーザーにコンテンツを配布することができます。 コンテンツをゲストとして表示するために招待することにより、外部ユーザーとコンテンツを共有することができます。 Azure Active Directory Business-to-Business (Azure AD B2B) を使用すると、外部のゲスト ユーザーと共有できます。 外部ユーザーと共有するには、次の前提条件を満たす必要があります。

- 外部ユーザーとコンテンツを共有する機能を有効にする必要があります

- ゲスト ユーザーは、共有コンテンツを表示するために適切なライセンスを取得している必要があります

ゲスト ユーザー アクセスの詳細については、「[Azure AD B2B で外部ゲスト ユーザーに Power BI コンテンツを配布する](service-admin-azure-ad-b2b.md)」を参照してください。

## <a name="purchase-power-bi-pro-licenses"></a>Power BI Pro ライセンスを購入する

管理者として、Microsoft 365 または Microsoft パートナーを通じて Power BI Pro ライセンスを購入します。 ライセンスを購入した後、それを個々のユーザーに割り当てます。 詳細については、「[Power BI Pro のライセンスを購入して割り当てる](service-admin-purchasing-power-bi-pro.md)」を参照してください。

### <a name="power-bi-pro-license-expiration"></a>Power BI Pro ライセンスの有効期限切れ

Power BI Pro ライセンスの有効期限切れ後には猶予期間があります。 ライセンスがボリューム ライセンス契約の一部である場合、猶予期間は 90 日です。 ライセンスを直接購入した場合、猶予期間は 30 日です。

Power BI Pro のサブスクリプション ライフサイクルは Microsoft 365 と同じです。 詳細については、[一般法人向け Microsoft 365 のサブスクリプションが終了したときにデータとアクセスはどうなるか](/microsoft-365/commerce/subscriptions/what-if-my-subscription-expires)に関する記事をご覧ください。


## <a name="next-steps"></a>次の手順

- [Power BI Pro のライセンスを購入して割り当てる](service-admin-purchasing-power-bi-pro.md)
- [ビジネス サブスクリプションと課金ドキュメント](/microsoft-365/commerce/?view=o365-worldwide)
- [サインインした Power BI ユーザーを見つける](service-admin-access-usage.md)
- 他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
