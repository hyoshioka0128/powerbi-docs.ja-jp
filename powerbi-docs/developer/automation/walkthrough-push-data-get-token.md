---
title: 埋め込み BI 分析情報を向上させるため、Power BI 埋め込み分析で認証アクセス トークンを取得する
description: データをプッシュするチュートリアル - 認証アクセス トークンを取得する。 Power BI 埋め込み分析を使用して、より優れた埋め込み BI インサイトを有効にします。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: madia
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: tutorial
ms.custom: has-adal-ref
ms.date: 05/29/2019
ms.openlocfilehash: 15110459fb710611781631c992d7699c2a8bff83
ms.sourcegitcommit: 13a150d1aa810f309421bf603fa8581718a4b299
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "101843230"
---
# <a name="step-2-get-an-authentication-access-token"></a>手順 2: 認証アクセス トークンを取得する

この記事は、シリーズ「[Power BI データセットにデータをプッシュする](walkthrough-push-data.md)」の 2 番目の手順です。

手順 1 では、[Azure AD でクライアント アプリを登録しました](../embedded/register-app.md)。 この手順では、認証アクセス トークンを取得します。 Power BI アプリは、Azure Active Directory と統合されることで、アプリにセキュリティで保護されたサインインと認証を提供します。 アプリでは、トークンを使って Azure AD に対して認証を行い、Power BI リソースにアクセスします。

## <a name="get-an-authentication-access-token"></a>認証アクセス トークンを取得する

開始する前に、「[Power BI データセットにデータをプッシュする](walkthrough-push-data.md)」シリーズの[前の手順](../embedded/register-app.md)を完了していることを確認してください。 

この手順では、Visual Studio 2015 以降が必要です。

1. Visual Studio で、新しい C# **コンソール アプリケーション** プロジェクトを作成します。

2. [Azure AD Authentication Library for .NET NuGet パッケージ](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/2.22.302111727)をインストールします。 .Net アプリでは、認証セキュリティ トークンを取得するために、このパッケージが必要です。 

     a. **[ツール]**  >  **[NuGet パッケージ マネージャー]**  >  **[パッケージ マネージャー コンソール]** の順に選択します。

     b. 「**Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612**」と入力します

     c. Program.cs に、`using Microsoft.IdentityModel.Clients.ActiveDirectory;` を追加します。

3. 次の手順の後に一覧表示されているサンプル コードを Program.cs に追加します。

4. "{ClientID}" を、[前のシリーズの記事](../embedded/register-app.md)で、アプリを登録したときに取得した **クライアント ID** で置き換えます。

5. コンソール アプリを実行し、Power BI アカウントにサインインします。 

   コンソール ウィンドウにトークン文字列が表示されます。

**認証セキュリティ トークンを取得するサンプル コード**

このコードを Program {...} に追加します。

* 操作を呼び出すためのトークン変数。 
  
  ```csharp
  private static string token = string.Empty;
  
  static void Main(string[] args)
  {
  }
  ```
* static void Main(string[] args) では、以下のように入力します。
  
  ```csharp
  static void Main(string[] args)
  {
    //Get an authentication access token
    token = GetToken();
  }
  ```
* GetToken() メソッドを追加します。

```csharp
       #region Get an authentication access token
       private static async Task<string> GetToken()
       {
           // TODO: Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612
           // and add using Microsoft.IdentityModel.Clients.ActiveDirectory

           //The client id that Azure AD created when you registered your client app.
           string clientID = "{Client_ID}";

           //RedirectUri you used when you register your app.
           //For a client app, a redirect uri gives Azure AD more details on the application that it will authenticate.
           // You can use this redirect uri for your client app
           string redirectUri = "https://login.live.com/oauth20_desktop.srf";

           //Resource Uri for Power BI API
           string resourceUri = "https://analysis.windows.net/powerbi/api";

           //OAuth2 authority Uri
           string authorityUri = "https://login.microsoftonline.com/common/";

           //Get access token:
           // To call a Power BI REST operation, create an instance of AuthenticationContext and call AcquireToken
           // AuthenticationContext is part of the Active Directory Authentication Library NuGet package
           // To install the Active Directory Authentication Library NuGet package in Visual Studio,
           //  run "Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory" from the nuget Package Manager Console.

           // AcquireToken will acquire an Azure access token
           // Call AcquireToken to get an Azure token from Azure Active Directory token issuance endpoint
           AuthenticationContext authContext = new AuthenticationContext(authorityUri);
           var token = authContext.AcquireTokenAsync(resourceUri, clientID, new Uri(redirectUri)).Result.AccessToken;

           Console.WriteLine(token);
           Console.ReadLine();

           return token;
       }

       #endregion
```

認証トークンを取得すると、任意の Power BI 操作を呼び出せます。

このシリーズの次の手順では、[Power BI でデータセットを作成する](walkthrough-push-data-create-dataset.md)方法について説明します。


## <a name="complete-code-listing"></a>完全なコード リスト

```csharp
using System;
using Microsoft.IdentityModel.Clients.ActiveDirectory;

namespace walkthrough_push_data
{
    class Program
    {
        private static string token = string.Empty;

        static void Main(string[] args)
        {

            //Get an authentication access token
            token = GetToken();

        }

        #region Get an authentication access token
        private static async Task<string> GetToken()
        {
            // TODO: Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612
            // and add using Microsoft.IdentityModel.Clients.ActiveDirectory

            //The client id that Azure AD created when you registered your client app.
            string clientID = "{Client_ID}";

            //RedirectUri you used when you register your app.
            //For a client app, a redirect uri gives Azure AD more details on the application that it will authenticate.
            // You can use this redirect uri for your client app
            string redirectUri = "https://login.live.com/oauth20_desktop.srf";

            //Resource Uri for Power BI API
            string resourceUri = "https://analysis.windows.net/powerbi/api";

            //OAuth2 authority Uri
            string authorityUri = "https://login.microsoftonline.com/common/";

            //Get access token:
            // To call a Power BI REST operation, create an instance of AuthenticationContext and call AcquireToken
            // AuthenticationContext is part of the Active Directory Authentication Library NuGet package
            // To install the Active Directory Authentication Library NuGet package in Visual Studio,
            //  run "Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory" from the nuget Package Manager Console.

            // AcquireToken will acquire an Azure access token
            // Call AcquireToken to get an Azure token from Azure Active Directory token issuance endpoint
            AuthenticationContext authContext = new AuthenticationContext(authorityUri);
            var token = authContext.AcquireTokenAsync(resourceUri, clientID, new Uri(redirectUri)).Result.AccessToken;

            Console.WriteLine(token);
            Console.ReadLine();

            return token;
        }

        #endregion

    }
}
```



## <a name="next-steps"></a>次のステップ

* このシリーズの次の記事は、「[Power BI でデータセットを作成する](walkthrough-push-data-create-dataset.md)」です
* [Power BI REST API の概要](overview-of-power-bi-rest-api.md)  
* [Power BI REST API](/rest/api/power-bi/)  

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。
