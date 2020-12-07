---
title: 読み取り専用の管理 API に対してサービス プリンシパル認証を有効にする (プレビュー)
description: サービス プリンシパル認証を有効にして、読み取り専用の管理 API の使用を許可する方法について説明します。
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 12/01/2020
ms.author: painbar
ms.custom: ''
LocalizationGroup: Administration
ms.openlocfilehash: fb2d25b4cc000f0a7b9c659f25264ffd1ab936d7
ms.sourcegitcommit: 2fd64f96b5bfbc14ff47e5c892171e5c921fb525
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2020
ms.locfileid: "96506724"
---
# <a name="enable-service-principle-authentication-for-read-only-admin-apis-preview"></a>読み取り専用の管理 API に対してサービス プリンシパル認証を有効にする (プレビュー)

サービス プリンシパルとは、Azure Active Directory (Azure AD) アプリケーションが Power BI サービスのコンテンツと API にアクセスできるようにするための認証方法です。
Azure AD アプリを作成すると、[サービス プリンシパル オブジェクト](https://docs.microsoft.com/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object)が作成されます。 サービス プリンシパル オブジェクト (単にサービス プリンシパルとも呼ばれる) を使用することで、Azure AD によるご利用のアプリの認証が可能になります。 認証が完了すると、アプリは Azure AD テナント リソースにアクセスできるようになります。

## <a name="method"></a>Method

Power BI 読み取り専用 API のサービス プリンシパル認証を有効にするには、次の手順に従います。

1. [Azure AD アプリを作成します](https://docs.microsoft.com/azure/active-directory/develop/howto-create-service-principal-portal)。 使用する Azure AD アプリが既にある場合は、この手順を省略できます。 後の手順のために、アプリ ID をメモしておきます。 
2. Azure Active Directory に新しい **セキュリティ グループ** を作成します。 [Azure Active Directory を使用して基本グループを作成し、メンバーを追加する方法の詳細を参照してください](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)。 使用するセキュリティ グループが既にある場合は、この手順を省略できます。
    グループの種類として **[セキュリティ]** を選択してください。

    ![Azure portal の新しいグループの作成ダイアログのスクリーンショット。](media/read-only-apis-service-principal-auth/azure-portal-new-group-dialog.png)

3. 作成したセキュリティ グループのメンバーとして、使用するアプリ ID を追加します。 次の手順に従います。
    1. **Azure portal > [Azure Active Directory] > [グループ]** の順に移動して、手順 2 で作成したセキュリティ グループを選択します。
    1. **[メンバーの追加]** を選択します。
    注意:Azure portal で、使用するアプリに Power BI 管理者ロールが設定されていないことを確認してください。 これを確認するには: 
       * グローバル管理者、アプリケーション管理者、またはクラウド アプリケーション管理者として **Azure portal** にサインインします。 
        * **[Azure Active Directory]** を選択した後、 **[エンタープライズ アプリケーション ]** を選択します。 
        * Power BI へのアクセス権を付与するアプリケーションを選択します。 
        * **[アクセス許可]** を選択します。 このアプリケーションには、Power BI 管理者の同意が必要なアクセス許可が設定されていないことを確認してください。 詳細については、「[アプリケーションの同意の管理と同意要求の評価](https://docs.microsoft.com/azure/active-directory/manage-apps/manage-consent-requests)」を参照してください。 
4. Power BI サービス管理者設定を有効にします。 手順は次のとおりです。
    1. Power BI 管理ポータルにログインします。 テナントの設定ページを表示するには、Power BI 管理者である必要があります。
    1. **[開発者向け設定]** に、 **[読み取り専用 Power BI 管理 API の使用をサービス プリンシパルに許可 (プレビュー)]** が表示されます。 次の図に示すように、切り替えを [有効] に設定し、 **[特定のセキュリティ グループ]** ラジオ ボタンをオンにして、その下に表示されるテキスト フィールドに手順 2 で作成したセキュリティ グループを追加します。

        ![サービス プリンシパルのテナント設定を許可するスクリーンショット。](media/read-only-apis-service-principal-auth/allow-service-principals-tenant-setting.png)

 5. 読み取り専用管理 API の使用を開始します。 サポートされている API の一覧については、以下をご覧ください。

    >[!IMPORTANT]
    >Power BI でサービス プリンシパルを使用できるようにすると、アプリケーションの Azure AD アクセス許可は効果を持たなくなります。 アプリケーションのアクセス許可はその後、Power BI 管理ポータルを介して管理されます。

## <a name="considerations-and-limitations"></a>考慮事項と制限事項
* サービス プリンシパルを使用して Power BI ポータルにサインインすることはできません。
* Power BI 管理ポータルの開発者向け設定でサービス プリンシパルを有効にするには、Power BI 管理者権限が必要です。
* 現在、サービス プリンシパルでは次の API がサポートされています。
    * [GetGroupsAsAdmin](https://docs.microsoft.com/rest/api/power-bi/admin/groups_getgroupsasadmin) (dashboards、datasets、reports、dataflows の $expand と共に) 
    * [GetDashboardsAsAdmin](https://docs.microsoft.com/rest/api/power-bi/admin/dashboards_getdashboardsasadmin) ($expand tiles と共に)
    * [GetDatasourcesAsAdmin](https://docs.microsoft.com/rest/api/power-bi/admin/datasets_getdatasourcesasadmin) 
    * [GetDatasetToDataflowsLinksAsAdmin](https://docs.microsoft.com/rest/api/power-bi/admin/datasets_getdatasettodataflowslinksingroupasadmin)
    * [GetDataflowDatasourcesAsAdmin](https://docs.microsoft.com/rest/api/power-bi/admin/dataflows_getdataflowdatasourcesasadmin) 
    * [GetDataflowUpstreamDataflowsAsAdmin](https://docs.microsoft.com/rest/api/power-bi/admin/dataflows_getupstreamdataflowsingroupasadmin) 
    * [GetCapacitiesAsAdmin](https://docs.microsoft.com/rest/api/power-bi/admin/getcapacitiesasadmin)
    * [GetActivityLog](https://docs.microsoft.com/rest/api/power-bi/admin/getactivityevents)
    * GetModifiedWorkspaces
    * WorkspaceGetInfo
    * WorkspaceScanStatus
    * WorkspaceScanResult
