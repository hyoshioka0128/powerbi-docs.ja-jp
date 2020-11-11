---
title: ユーザーを認証し、アプリケーション用の Azure AD アクセス トークンを取得する
description: 埋め込みの Power BI コンテンツと共に使用するため、Azure Active Directory にアプリケーションを登録する方法を説明します。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 06/04/2019
ms.openlocfilehash: 0743a7ac0d12cba8bbde54464a275a78f7c88eff
ms.sourcegitcommit: 37bd34053557089c4fbf0e05f78e959609966561
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/10/2020
ms.locfileid: "94396704"
---
# <a name="get-an-azure-ad-access-token-for-your-power-bi-application"></a>Power BI アプリケーション用の Azure AD アクセス トークンを取得する

この記事では、Power BI アプリケーションでユーザーを認証し、[Power BI REST API](/rest/api/power-bi/) で使うアクセス トークンを取得する方法について説明します。

アプリで REST API を呼び出す前に、Azure Active Directory (Azure AD) の **認証アクセス トークン** を取得する必要があります。 アプリではトークンを使用し、Power BI のダッシュボード、タイル、レポートにアクセスします。 詳細については、「[OAuth 2.0 コード付与フローを使用して Azure Active Directory Web アプリケーションへアクセスを承認する](/azure/active-directory/develop/v1-protocols-oauth-code)」を参照してください。

コンテンツの埋め込み方法により、アクセス トークンの取得方法が異なります。 この記事では、2 つの異なるアプローチを紹介します。

## <a name="access-token-for-power-bi-users-user-owns-data"></a>Power BI ユーザーのアクセス トークン (ユーザーがデータを所有している場合)

この例は、ユーザーが自分の組織サインインを使って Azure AD に手動でサインインする場合です。 このタスクは、Power BI サービスにアクセスできるユーザーに対してコンテンツを埋め込むときに使用されます。

### <a name="get-an-azure-ad-authorization-code"></a>Azure AD 認証コードを取得する

**アクセス トークン** を取得する最初の手順は、 **Azure AD** から認証コードを取得することです。 次のプロパティを持つクエリ文字列を作成し、 **Azure AD** にリダイレクトします。

#### <a name="authorization-code-query-string"></a>承認コードのクエリ文字列

```csharp
var @params = new NameValueCollection
{
    //Azure AD will return an authorization code. 
    //See the Redirect class to see how "code" is used to AcquireTokenByAuthorizationCode
    {"response_type", "code"},

    //Client ID is used by the application to identify themselves to the users that they are requesting permissions from.
    //You get the client id when you register your Azure app.
    {"client_id", Properties.Settings.Default.ClientID},

    //Resource uri to the Power BI resource to be authorized
    // https://analysis.windows.net/powerbi/api
    {"resource", Properties.Settings.Default.PowerBiAPI},

    //After user authenticates, Azure AD will redirect back to the web app
    {"redirect_uri", "https://localhost:13526/Redirect"}
};
```

クエリ文字列を構築した後、 **Azure AD** にリダイレクトして **認証コード** を取得します。  **認証コード** クエリ文字列を構築し、 **Azure AD** にリダイレクトするための完全な C# メソッドを以下に示します。 **認証コード** を取得したら、それを使用して **アクセス トークン** を取得します。

redirect.aspx.cs 内で、[AuthenticationContext.AcquireTokenByAuthorizationCode](/dotnet/api/microsoft.identitymodel.clients.activedirectory.authenticationcontext.acquiretokenbyauthorizationcodeasync#Microsoft_IdentityModel_Clients_ActiveDirectory_AuthenticationContext_AcquireTokenByAuthorizationCodeAsync_System_String_System_Uri_Microsoft_IdentityModel_Clients_ActiveDirectory_ClientCredential_System_String_) が呼び出され、トークンが生成されます。

#### <a name="get-authorization-code"></a>認証コードを取得する

```csharp
protected void signInButton_Click(object sender, EventArgs e)
{
    //Create a query string
    //Create a sign-in NameValueCollection for query string
    var @params = new NameValueCollection
    {
        //Azure AD will return an authorization code. 
        //See the Redirect class to see how "code" is used to AcquireTokenByAuthorizationCode
        {"response_type", "code"},

        //Client ID is used by the application to identify themselves to the users that they are requesting permissions from. 
        //You get the client id when you register your Azure app.
        {"client_id", Properties.Settings.Default.ClientID},

        //Resource uri to the Power BI resource to be authorized
        // https://analysis.windows.net/powerbi/api
        {"resource", Properties.Settings.Default.PowerBiAPI},

        //After user authenticates, Azure AD will redirect back to the web app
        {"redirect_uri", "https://localhost:13526/Redirect"}
    };

    //Create sign-in query string
    var queryString = HttpUtility.ParseQueryString(string.Empty);
    queryString.Add(@params);

    //Redirect authority
    //Authority Uri is an Azure resource that takes a client id to get an Access token
    // AADAuthorityUri = https://login.microsoftonline.com/common/
    string authorityUri = Properties.Settings.Default.AADAuthorityUri;
    var authUri = String.Format("{0}?{1}", authorityUri, queryString);
    Response.Redirect(authUri);
}
```

### <a name="get-an-access-token-from-authorization-code"></a>認証コードからアクセス トークンを取得する

**Azure AD** によって **認証コード** とともに Web アプリにリダイレクトされた後、それを使用してアクセス トークンを取得できます。 次に示す C# のサンプルは、リダイレクト ページと default.aspx ページの `Page_Load` イベントで使用できます。

**Microsoft.IdentityModel.Clients.ActiveDirectory** 名前空間は、 [Active Directory Authentication Library](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) NuGet パッケージから取得できます。

```powershell
Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory
```

#### <a name="redirectaspxcs"></a>Redirect.aspx.cs

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;

protected void Page_Load(object sender, EventArgs e)
{
    //Redirect uri must match the redirect_uri used when requesting Authorization code.
    string redirectUri = String.Format("{0}Redirect", Properties.Settings.Default.RedirectUrl);
    string authorityUri = Properties.Settings.Default.AADAuthorityUri;

    // Get the auth code
    string code = Request.Params.GetValues(0)[0];

    // Get auth token from auth code
    TokenCache TC = new TokenCache();

    AuthenticationContext AC = new AuthenticationContext(authorityUri, TC);
    ClientCredential cc = new ClientCredential
        (Properties.Settings.Default.ClientID,
        Properties.Settings.Default.ClientSecret);

    AuthenticationResult AR = AC.AcquireTokenByAuthorizationCode(code, new Uri(redirectUri), cc);

    //Set Session "authResult" index string to the AuthenticationResult
    Session[_Default.authResultString] = AR;

    //Redirect back to Default.aspx
    Response.Redirect("/Default.aspx");
}
```

#### <a name="defaultaspx"></a>Default.aspx

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;

protected void Page_Load(object sender, EventArgs e)
{

    //Test for AuthenticationResult
    if (Session[authResultString] != null)
    {
        //Get the authentication result from the session
        authResult = (AuthenticationResult)Session[authResultString];

        //Show Power BI Panel
        signInStatus.Visible = true;
        signInButton.Visible = false;

        //Set user and token from authentication result
        userLabel.Text = authResult.UserInfo.DisplayableId;
        accessTokenTextbox.Text = authResult.AccessToken;
    }
}
```

## <a name="access-token-for-non-power-bi-users-app-owns-data"></a>Power BI ユーザーではないユーザーのアクセス トークン (アプリがデータを所有している場合)

このアプローチは通常、アプリがデータへのアクセスを所有している独立系ソフトウェア ベンダー (ISV) タイプのアプリケーションに対して使われます。 ユーザーは必ずしも Power BI ユーザーではなく、アプリケーションによりユーザーの認証とアクセスが制御されます。

### <a name="access-token-with-a-master-account"></a>アクセス トークンとマスター アカウント

この手法では、Power BI Pro ユーザーである 1 つの *マスター* アカウントを使用します。 アカウント資格情報は、アプリケーションで保存されます。 アプリケーションは、これらの保存された資格情報を使用して Azure AD に対する認証を行います。 次に示すコード例は、[アプリ所有データ サンプル](https://github.com/guyinacube/PowerBI-Developer-Samples)のものです

### <a name="access-token-with-service-principal"></a>アクセス トークンとサービス プリンシパル

この手法では、 **アプリ専用** トークンである [サービス プリンシパル](embed-service-principal.md)を使用します。 アプリケーションは、サービス プリンシパルを使用して Azure AD に対する認証を行います。 次に示すコード例は、[アプリ所有データ サンプル](https://github.com/guyinacube/PowerBI-Developer-Samples)のものです

#### <a name="embedservicecs"></a>EmbedService.cs

```csharp
var AuthorityURL  = "https://login.microsoftonline.com/<TenantId>/"
var ResourceURL  = "https://analysis.windows.net/powerbi/api"
var authenticationContext = new AuthenticationContext(AuthorityUrl);
       AuthenticationResult authenticationResult = null;
       if (AuthenticationType.Equals("MasterUser"))
       {
              // Authentication using master user credentials
              var credential = new UserPasswordCredential(Username, Password);
              authenticationResult = authenticationContext.AcquireTokenAsync(ResourceUrl, ApplicationId, credential).Result;
       }
       else
       {
             // Authentication using app credentials
             var credential = new ClientCredential(ApplicationId, ApplicationSecret);
             authenticationResult = await authenticationContext.AcquireTokenAsync(ResourceUrl, credential);
       }


m_tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");
```

## <a name="troubleshoot"></a>トラブルシューティング

エラー メッセージ: "'AuthenticationContext' に 'AcquireToken' の定義が含まれておらず、型 'AuthenticationContext' の最初の引数を受け付けるアクセス可能な拡張メソッド 'AcquireToken' が見つかりませんでした。using ディレクティブまたはアセンブリ参照が不足していないことを確認してください"。

   このエラーが表示された場合、[Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/2.22.302111727) のダウンロードをお試しください。

## <a name="next-steps"></a>次のステップ

アクセス トークンを入手したので、Power BI REST API を呼び出してコンテンツを埋め込むことができます。 詳細については、[Power BI コンテンツを埋め込む方法](embed-sample-for-customers.md#embed-content-within-your-application)に関するページをご覧ください。

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。