---
title: サービス プリンシパルとアプリケーション シークレットを使用した Power BI コンテンツの埋め込み
description: Azure Active Directory アプリケーション サービス プリンシパルとアプリケーション シークレットを使用して、埋め込み分析を認証する方法について説明します。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.custom: ''
ms.date: 11/23/2020
ms.openlocfilehash: 17c0a4d0809aa87f50225e0c59ca3962776bd2b1
ms.sourcegitcommit: 9d033abd9c01a01bba132972497dda428d7d5c12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95514484"
---
# <a name="embed-power-bi-content-with-service-principal-and-an-application-secret"></a>サービス プリンシパルとアプリケーション シークレットを使用した Power BI コンテンツの埋め込み

サービス プリンシパルとは、Azure AD アプリケーションが Power BI サービスのコンテンツと API にアクセスできるようにするための認証方法です。

Azure Active Directory (Azure AD) アプリを作成すると、[サービス プリンシパル オブジェクト](/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object)が作成されます。 サービス プリンシパル オブジェクト (単に "*サービス プリンシパル*" とも呼ばれる) を使用することで、Azure AD はご利用のアプリの認証を行うことができます。 認証が完了すると、アプリは Azure AD テナント リソースにアクセスできるようになります。

認証を行うために、サービス プリンシパルでは、Azure AD アプリの "*アプリケーション ID*" と次のいずれかが使用されます。

* Certificate
* アプリケーション シークレット

この記事では、"*アプリケーション ID*" と "*アプリケーション シークレット*" を使用したサービス プリンシパル認証について説明します。

>[!NOTE]
>Azure AD では、秘密キーではなく、証明書を使用してご利用のバックエンド サービスをセキュリティで保護することが推奨されています。
>* [秘密キーまたは証明書を使用して Azure AD からアクセス トークンを取得する方法の詳細を説明します](/azure/architecture/multitenant-identity/client-assertion)。
>* 証明書を使用してソリューションをセキュリティで保護するには、この記事の手順を完了し、「[サービス プリンシパルと証明書を使用した Power BI コンテンツの埋め込み](embed-service-principal-certificate.md)」に記載されている手順に従います。

## <a name="method"></a>メソッド

サービス プリンシパルとアプリケーション ID の埋め込み分析を使用するには、次の手順を行います。

1. [Azure AD アプリ](/azure/active-directory/manage-apps/what-is-application-management)を作成します。

    1. Azure AD アプリのシークレットを作成します。
    
    2. アプリの "*アプリケーション ID*" と "*アプリケーション シークレット*" を取得します。

    >[!NOTE]
    >これらの手順については **手順 1** で説明します。 Azure AD アプリの作成の詳細については、[Azure AD アプリの作成](/azure/active-directory/develop/howto-create-service-principal-portal)に関するページを参照してください。

2. Azure AD セキュリティ グループを作成します。

3. Power BI サービス管理者設定を有効にします。

4. サービス プリンシパルを、ご利用のワークスペースに追加します。

5. 自分のコンテンツを埋め込みます。

> [!IMPORTANT]
> Power BI でサービス プリンシパルを使用できるようにすると、アプリケーションの AD アクセス許可は無効になります。 アプリケーションのアクセス許可はその後、Power BI 管理ポータルを介して管理されます。

## <a name="step-1---create-an-azure-ad-app"></a>手順 1 - Azure AD アプリを作成する

次のいずれかの方法を使用して、Azure AD アプリを作成します。

* [Microsoft Azure portal でアプリを作成する](embed-service-principal.md#creating-an-azure-ad-app-in-the-microsoft-azure-portal)

* [PowerShell を使用してアプリを作成する](embed-service-principal.md#creating-an-azure-ad-app-using-powershell)

### <a name="creating-an-azure-ad-app-in-the-microsoft-azure-portal"></a>Microsoft Azure portal での Azure AD アプリの作成

1. [Microsoft Azure](https://ms.portal.azure.com/#allservices) にログインします。

2. **[アプリの登録]** を検索し、 **[アプリの登録]** リンクをクリックします。

    ![Azure アプリの登録](media/embed-service-principal/azure-app-registration.png)

3. **[新規登録]** をクリックします。

    ![新しい登録](media/embed-service-principal/new-registration.png)

4. 必要な情報を入力します。
    * **名前** - 自分のアプリケーションの名前を入力します
    * **サポートされているアカウントの種類** - サポートされているアカウントの種類を選択します
    * (省略可能) **リダイレクト URI** - 必要に応じて URI を入力します

5. **[登録]** をクリックします。

6. 登録した後、 **[概要]** タブで "*アプリケーション ID*" を使用できます。後で使用できるように、"*アプリケーション ID*" をコピーして保存します。

    ![[概要] タブのアプリケーション ID を取得する場所を示すスクリーンショット。](media/embed-service-principal/application-id.png)

7. **[証明書とシークレット]** タブをクリックします。

     ![Azure portal のアプリに対する [証明書とシークレット] ペインを示すスクリーンショット。](media/embed-service-principal/certificates-and-secrets.png)

8. **[新しいクライアント シークレット]** をクリックします

    ![[証明書とシークレット] ペインの [新しいクライアント シークレット] ボタンを示すスクリーンショット。](media/embed-service-principal/new-client-secret.png)

9. *[クライアント シークレットの追加]* ウィンドウで、説明を入力し、クライアント シークレットの有効期限を指定し、 **[追加]** をクリックします。

10. "*クライアント シークレット*" 値をコピーして保存します。

    ![[証明書とシークレット] ペインでぼかされたシークレット値を示すスクリーンショット。](media/embed-service-principal/client-secret-value.png)

    >[!NOTE]
    >このウィンドウから離れると、クライアント シークレットの値は非表示となり、再度表示することもコピーすることもできません。

### <a name="creating-an-azure-ad-app-using-powershell"></a>PowerShell を使用した Azure AD アプリの作成

このセクションには、[PowerShell](/powershell/azure/create-azure-service-principal-azureps) を使用して新しい Azure AD アプリを作成するためのサンプル スクリプトが含まれています。

```powershell
# The app ID - $app.appid
# The service principal object ID - $sp.objectId
# The app key - $key.value

# Sign in as a user that's allowed to create an app
Connect-AzureAD

# Create a new Azure AD web application
$app = New-AzureADApplication -DisplayName "testApp1" -Homepage "https://localhost:44322" -ReplyUrls "https://localhost:44322"

# Creates a service principal
$sp = New-AzureADServicePrincipal -AppId $app.AppId

# Get the service principal key
$key = New-AzureADServicePrincipalPasswordCredential -ObjectId $sp.ObjectId
```

## <a name="step-2---create-an-azure-ad-security-group"></a>手順 2 - Azure AD セキュリティ グループを作成する

ご利用のサービス プリンシパルには、Power BI コンテンツおよび API のいずれに対してもアクセス権がありません。 サービス プリンシパルにアクセス権を付与するには、Azure AD でセキュリティ グループを作成し、作成済みのサービス プリンシパルをそのセキュリティ グループに追加します。

Azure AD セキュリティ グループを作成するには、次の 2 つの方法があります。
* [手動 (Azure で)](embed-service-principal.md#create-a-security-group-manually)
* [PowerShell の使用](embed-service-principal.md#create-a-security-group-using-powershell)

### <a name="create-a-security-group-manually"></a>セキュリティ グループを手動で作成する

Azure セキュリティ グループを手動で作成するには、「[Azure Active Directory を使用して基本グループを作成してメンバーを追加する](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)」に記載の手順に従ってください。 

### <a name="create-a-security-group-using-powershell"></a>PowerShell を使用してセキュリティ グループを作成する

新しいセキュリティ グループを作成し、そのセキュリティ グループにアプリを追加するためのサンプル スクリプトを以下に示します。

>[!NOTE]
>組織全体に対してサービス プリンシパル アクセスを有効にする場合、この手順をスキップします。

```powershell
# Required to sign in as admin
Connect-AzureAD

# Create an Azure AD security group
$group = New-AzureADGroup -DisplayName <Group display name> -SecurityEnabled $true -MailEnabled $false -MailNickName notSet

# Add the service principal to the group
Add-AzureADGroupMember -ObjectId $($group.ObjectId) -RefObjectId $($sp.ObjectId)
```

## <a name="step-3---enable-the-power-bi-service-admin-settings"></a>手順 3 - Power BI サービス管理者設定を有効にする

Azure AD アプリから Power BI コンテンツおよび API にアクセスできるようにするには、Power BI 管理者が Power BI 管理ポータルでサービス プリンシパル アクセスを有効にする必要があります。

Azure AD で作成したセキュリティ グループを、 **[開発者向け設定]** の特定のセキュリティ グループのセクションに追加します。

>[!IMPORTANT]
>サービス プリンシパルには、それが有効にされたテナント設定へのアクセス権があります。 これには、ご利用の管理者設定に応じて、特定のセキュリティ グループまたは組織全体が含まれます。
>
>サービス プリンシパル アクセスを特定のテナント設定に限定するには、特定のセキュリティ グループへのアクセスのみを許可します。 あるいは、サービス プリンシパル専用のセキュリティ グループを作成し、それを目的のテナント設定から除外することもできます。

>[!div class="mx-imgBorder"]
>:::image type="content" source="media/embed-service-principal/admin-portal.png" alt-text="Power BI ポータルの管理オプションの開発者向け設定を示すスクリーンショット。":::

## <a name="step-4---add-the-service-principal-to-your-workspace"></a>手順 4 - サービス プリンシパルを、ご利用のワークスペースに追加します。

Power BI サービス内でレポート、ダッシュボード、データセットなどの Azure AD アプリのアクセス成果物を有効にするには、サービス プリンシパル エンティティ、またはサービス プリンシパルを含むセキュリティ グループをメンバーまたは管理者としてご利用のワークスペースに追加します。

>[!NOTE]
>このセクションでは、UI の手順について説明します。 また、[グループ - グループ ユーザー API の追加](/rest/api/power-bi/groups/addgroupuser)に関するページを参照して、サービス プリンシパルまたはセキュリティ グループをワークスペースに追加することもできます。

1. アクセスを有効にするワークスペースまでスクロールし、 **[その他]** メニューで、 **[ワークスペース アクセス]** を選択します。

    :::image type="content" source="media/embed-service-principal/workspace-access.png" alt-text="Power BI ワークスペースの [その他] メニューのワークスペース アクセス ボタンを示すスクリーンショット。":::

2. **[アクセス]** ペインのテキスト ボックスに、次のいずれかを追加します。

    * ご利用の **サービス プリンシパル**。 サービス プリンシパルの名前は、Azure AD アプリの [概要] タブに表示される、Azure AD アプリの "*表示名*" です。

    * サービス プリンシパルを含む **セキュリティ グループ**。

3. ドロップダウン メニューから、 **[メンバー]** または **[管理者]** を選択します。

4. **[追加]** を選択します。

## <a name="step-5---embed-your-content"></a>手順 5 - コンテンツを埋め込む

サンプル アプリケーション内にも、独自のアプリケーション内にも使用するコンテンツを埋め込むことができます。

* [サンプル アプリケーションを使用してコンテンツを埋め込む](embed-sample-for-customers.md#embed-content-using-the-sample-application)
* [自分のアプリケーション内にコンテンツを埋め込む](embed-sample-for-customers.md#embed-content-within-your-application)

使用するコンテンツが埋め込まれると、[運用開始](embed-sample-for-customers.md#move-to-production)の準備が整います。

>[!NOTE]
>証明書を使用してコンテンツをセキュリティで保護するには、「[サービス プリンシパルと証明書を使用した Power BI コンテンツの埋め込み](embed-service-principal-certificate.md)」に記載されている手順に従います。

## <a name="considerations-and-limitations"></a>考慮事項と制限事項

* サービス プリンシパルは、[新しいワークスペース](../../collaborate-share/service-create-the-new-workspaces.md)でのみ動作します。
* サービス プリンシパルを使用する場合は、**マイ ワークスペース** はサポートされません。
* 運用環境に移行するときは、容量が必要です。
* サービス プリンシパルを使用して Power BI ポータルにサインインすることはできません。
* Power BI 管理ポータル内の開発者向け設定でサービス プリンシパルを有効にするには、Power BI 管理者権限が必要です。
* [組織のアプリケーションへの埋め込み](embed-sample-for-your-organization.md)では、サービス プリンシパルを使用することはできません。
* [データフロー](../../transform-model/dataflows/dataflows-introduction-self-service.md)管理はサポートされていません。
* サービス プリンシパルでは現在、管理 API は一切サポートされていません。
* サービス プリンシパルを [Azure Analysis Services](/azure/analysis-services/analysis-services-overview) データ ソースと共に使用する場合、サービス プリンシパル自体に Azure Analysis Services インスタンスのアクセス許可が含まれている必要があります。 この目的のためのサービス プリンシパルを含むセキュリティ グループを使用することはできません。

## <a name="next-steps"></a>次のステップ

>[!div class="nextstepaction"]
>[アプリを登録する](register-app.md)

> [!div class="nextstepaction"]
>[顧客向けの Power BI Embedded](embed-sample-for-customers.md)

>[!div class="nextstepaction"]
>[サービス プリンシパルと証明書を使用して埋め込む](embed-service-principal-certificate.md)

>[!div class="nextstepaction"]
>[Azure Active Directory でのアプリケーション オブジェクトとサービス プリンシパル オブジェクト](/azure/active-directory/develop/app-objects-and-service-principals)

>[!div class="nextstepaction"]
>[サービス プリンシパルを使用するオンプレミス データ ゲートウェイを使用した行レベルのセキュリティ](embedded-row-level-security.md#on-premises-data-gateway-with-service-principal)