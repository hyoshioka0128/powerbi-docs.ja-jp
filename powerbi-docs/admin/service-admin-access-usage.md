---
title: サインインした Power BI ユーザーを見つける
description: ご自分が管理者であり、Power BI にサインインしたユーザーを確認したい場合は、Azure Active Directory アクセスと使用状況レポートを使用できます
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 09/25/2020
LocalizationGroup: Administration
ms.openlocfilehash: 84d4b0ab295f003c34937084bd93dd6f27992c31
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96409288"
---
# <a name="find-power-bi-users-that-have-signed-in"></a>サインインした Power BI ユーザーを見つける

ご自分が組織の管理者であり、Power BI にサインインしたユーザーを確認したい場合は、[Azure Active Directory アクセスと使用状況レポート](/azure/active-directory/reports-monitoring/concept-sign-ins)を使用してください。

> [!NOTE]
> **サインイン** レポートにより役に立つ情報が提供されますが、ユーザーごとのライセンスの種類は識別されません。 ライセンスを表示するには、Microsoft 365 管理センターを使用します。

## <a name="requirements"></a>要件

ユーザーは自分のサインインのレポートを表示できます。すべてのユーザーのレポートを表示するには、次のいずれかのロールを使用する必要があります: 全体管理者、セキュリティ管理者、セキュリティ閲覧者、全体閲覧者、またはレポート閲覧者。

## <a name="use-the-azure-active-directory-admin-center-to-view-sign-ins"></a>Azure Active Directory 管理センターを使用してサインインを表示する

サインイン アクティビティを表示するには、次の手順のようにします。

1. [Azure Active Directory 管理センター](https://aad.portal.azure.com)にサインインし、ポータル メニューから **[Azure Active Directory]** を選択します。

1. [リソース] メニューから、 **[監視]**  >  **[サインイン]** の順に選択します。
   
    ![[サインイン] オプションが強調表示されている Azure Active Directory 管理センターのスクリーンショット。](media/service-admin-access-usage/azure-portal-sign-ins.png)

1. 既定では、すべてのユーザーとすべてのアプリケーションについて、過去 24 時間のすべてのサインインが表示されます。 別の期間を選択するには、作業ウィンドウで **[日付]** を選択し、使用可能な時間間隔を選択します。 過去 7 日間の情報のみが利用できます。 Power BI へのサインインのみを表示するには、フィルターを追加します。 **[フィルターの追加]** を選択し、フィルター処理するフィールドとして **[アプリケーション]** を選択し、 **[適用]** を選択します。 作業ウィンドウの上部から **[次で始まるアプリケーション]** を選択し、アプリ名を入力します。 **[適用]** を選択します。

    **Microsoft Power BI** の場合は、サービスに関連するサインイン アクティビティにフィルター処理されます。 **Power BI Gateway** の場合は、オンプレミス データ ゲートウェイに固有のサインイン アクティビティにフィルター処理されます。
   
    ![[アプリケーション] フィールドが強調表示されているサインイン フィルターのスクリーンショット。](media/service-admin-access-usage/sign-in-filter.png)

## <a name="export-the-data"></a>データをエクスポートする

CSV ファイル形式または JSON ファイル形式で[サインイン レポートをダウンロード](/azure/active-directory/reports-monitoring/quickstart-download-sign-in-report)できます。

1. **[サインイン]** レポート用のコマンド バーで、 **[ダウンロード]** を選択してから、次のオプションのいずれかを選択します。

   * **[CSV]** : 現在フィルター処理されているデータの CSV ファイルをダウンロードします。

   * **[JSON]** : 現在フィルター処理されているデータの JSON ファイルをダウンロードします。

2. ファイル名を入力して、 **[ダウンロード]** を選択します。

![[ダウンロード] オプションが強調表示されているデータ エクスポートのスクリーンショット。](media/service-admin-access-usage/download-sign-in-data-csv.png)

## <a name="data-retention"></a>データ保持期間

組織が Azure AD Premium ライセンスを所有していない場合、サインインに関連するデータを利用できる期間は最大で 7 日です。 Azure AD Premium P1 または Azure AD Premium P2 を使用している場合、過去 30 日間のデータを表示できます。 詳しくは、「[Azure Active Directory レポートの保持ポリシー](/azure/active-directory/reports-monitoring/reference-reports-data-retention)」を参照してください。

## <a name="next-steps"></a>次の手順

[ユーザー アクティビティを監査する](service-admin-auditing.md)

その他の質問 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。