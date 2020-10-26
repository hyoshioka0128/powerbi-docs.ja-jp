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
ms.date: 10/15/2020
ms.openlocfilehash: 6f6a13f239d1bcfa7731361f4efcd129da7e2031
ms.sourcegitcommit: 1428acb6334649fc2d3d8ae4c42cfbc17e8f7476
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/19/2020
ms.locfileid: "92197740"
---
# <a name="embed-power-bi-content-with-service-principal-and-an-application-secret"></a>サービス プリンシパルとアプリケーション シークレットを使用した Power BI コンテンツの埋め込み

[!INCLUDE[service principal overview](../../includes/service-principal-overview.md)]

この記事では、"*アプリケーション ID*" と "*アプリケーション シークレット*" を使用したサービス プリンシパル認証について説明します。

>[!NOTE]
>ご利用のバックエンド サービスは、秘密キーではなく、証明書を使用してセキュリティで保護することをお勧めします。
>* [秘密キーまたは証明書を使用して Azure AD からアクセス トークンを取得する方法の詳細を説明します](/azure/architecture/multitenant-identity/client-assertion)。
>* [サービス プリンシパルと証明書を使用した Power BI コンテンツの埋め込み](embed-service-principal-certificate.md)

## <a name="method"></a>メソッド

埋め込み分析でサービス プリンシパルとアプリケーション ID を使用するには、次の手順を行います。

1. [Azure AD アプリ](/azure/active-directory/manage-apps/what-is-application-management)を作成します。

    1. Azure AD アプリのシークレットを作成します。
    
    2. アプリの "*アプリケーション ID*" と "*アプリケーション シークレット*" を取得します。

    >[!NOTE]
    >これらの手順については**手順 1** で説明します。 Azure AD アプリの作成の詳細については、[Azure AD アプリの作成](/azure/active-directory/develop/howto-create-service-principal-portal)に関するページを参照してください。

2. Azure AD セキュリティ グループを作成します。

3. Power BI サービス管理者設定を有効にします。

4. サービス プリンシパルを、ご利用のワークスペースに追加します。

5. 自分のコンテンツを埋め込みます。

> [!IMPORTANT]
> Power BI でサービス プリンシパルを使用できるようにすると、アプリケーションの AD アクセス許可は無効になります。 アプリケーションのアクセス許可はその後、Power BI 管理ポータルを介して管理されます。

## <a name="step-1---create-an-azure-ad-app"></a>手順 1 - Azure AD アプリを作成する

次のいずれかの方法を使用して、Azure AD アプリを作成します。

* [Microsoft Azure portal でアプリを作成する](https://portal.azure.com/#allservices)

* [PowerShell](/powershell/azure/create-azure-service-principal-azureps) を使用してアプリを作成する

### <a name="creating-an-azure-ad-app-in-the-microsoft-azure-portal"></a>Microsoft Azure portal での Azure AD アプリの作成

[!INCLUDE[service create app](../../includes/service-principal-create-app.md)]

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
[!INCLUDE[service create steps two, three and four](../../includes/service-principal-create-steps.md)]

## <a name="step-5---embed-your-content"></a>手順 5 - コンテンツを埋め込む

サンプル アプリケーション内にも、独自のアプリケーション内にも使用するコンテンツを埋め込むことができます。

* [サンプル アプリケーションを使用してコンテンツを埋め込む](embed-sample-for-customers.md#embed-content-using-the-sample-application)
* [自分のアプリケーション内にコンテンツを埋め込む](embed-sample-for-customers.md#embed-content-within-your-application)

使用するコンテンツが埋め込まれると、[運用開始](embed-sample-for-customers.md#move-to-production)の準備が整います。

[!INCLUDE[service principal limitations](../../includes/service-principal-limitations.md)]

## <a name="next-steps"></a>次の手順

>[!div class="nextstepaction"]
>[アプリを登録する](register-app.md)

> [!div class="nextstepaction"]
>[顧客向けの Power BI Embedded](embed-sample-for-customers.md)

>[!div class="nextstepaction"]
>[Azure Active Directory でのアプリケーション オブジェクトとサービス プリンシパル オブジェクト](/azure/active-directory/develop/app-objects-and-service-principals)

>[!div class="nextstepaction"]
>[サービス プリンシパルを使用するオンプレミス データ ゲートウェイを使用した行レベルのセキュリティ](embedded-row-level-security.md#on-premises-data-gateway-with-service-principal)

>[!div class="nextstepaction"]
>[サービス プリンシパルと証明書を使用した Power BI コンテンツの埋め込み](embed-service-principal-certificate.md)