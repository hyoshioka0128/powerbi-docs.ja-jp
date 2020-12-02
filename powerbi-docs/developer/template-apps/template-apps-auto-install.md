---
title: 顧客向けにテンプレート アプリのインストールの構成を自動化する
description: テンプレート アプリのインストールの構成を自動化する方法について説明します。
author: paulinbar
ms.author: painbar
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 11/23/2020
ms.openlocfilehash: ca5db6ed7a07d5a6fb10133285378e8318527464
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96386094"
---
# <a name="automated-configuration-of-a-template-app-installation"></a>テンプレート アプリのインストールの自動構成

テンプレート アプリは、顧客がデータから分析情報の取得を開始するのに最適な方法です。 テンプレート アプリは、データに接続し、必要に応じてカスタマイズできる事前構築済みのレポートを提供することにより、すばやく起動して実行できます。

顧客は、データへの接続方法の詳細に精通しているとは限らないため、テンプレート アプリをインストールするときにこれらの詳細を提供する必要があることは、顧客にとって問題になる可能性があります。

あなたがデータ サービス プロバイダーであり、顧客がサービスでデータを使い始めるのに役立つテンプレート アプリを作成している場合は、テンプレート アプリのパラメーターの構成を自動化することで、顧客がテンプレート アプリを簡単にインストールできるようにすることができます。 顧客はポータルにログインすると、準備された特別なリンクをクリックします。 これにより、自動化が開始され、必要な情報の収集とテンプレート アプリのパラメーターの事前構成が行われ、アプリをインストールできる Power BI アカウントに顧客がリダイレクトされます。 行う必要があるのは、[インストール] をクリックし、データ ソースに対して認証を行うことだけで、準備は完了です。 

このカスタマー エクスペリエンスを次に示します。

![自動インストール アプリケーションを使用するユーザー エクスペリエンスの図。](media/template-apps-auto-install/high-level-flow.png)

この記事では、テンプレート アプリのインストールの構成を自動化するために必要な基本のフローと前提条件、および主な手順と API について説明します。 ただし、すぐに開始したい場合は、[チュートリアル](template-apps-auto-install-tutorial.md)に進んでください。Azure 関数を使用するように準備された簡単なサンプル アプリケーションを使用して、テンプレート アプリのインストールの構成を自動化できます。

## <a name="basic-flow"></a>基本のフロー

テンプレート アプリのインストールの構成を自動化するための基本のフローは、次のとおりです。

1. ユーザーは、ISV のポータルにログインして、指定されたリンクをクリックします。 これにより、自動化されたフローが開始されます。 この段階で、ISV のポータルにより、ユーザー固有の構成が準備されます。

2. ISV は、ISV のテナントに登録されている [サービス プリンシパル (アプリ専用トークン)](../embedded/embed-service-principal.md) に基づいて、**アプリ専用** トークンを取得します。

3. ISV は、[Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/) を使用して、**インストール チケット** を作成します。この中には、ISV によって準備されたユーザー固有のパラメーター構成が含まれます。

4. ISV は、インストール チケットを含む ```POST``` リダイレクト メソッドを使用して、ユーザーを Power BI にリダイレクトします。

5. ユーザーは、インストール チケットを使用して Power BI アカウントにリダイレクトされ、テンプレート アプリをインストールするように求められます。 ユーザーが [インストール] をクリックすると、テンプレート アプリが自動的にインストールされます。

>[!Note]
>パラメーター値は、インストール チケットの作成時に ISV によって構成されますが、データソース関連の資格情報は、インストールの最終段階でユーザーによってのみ提供されます。 これにより、サードパーティに公開されるのを防ぎ、ユーザーとテンプレート アプリのデータ ソース間のセキュリティで保護された接続が確保されます。

## <a name="prerequisites"></a>前提条件

テンプレート アプリの事前構成済みのインストール エクスペリエンスを提供するには、次の前提条件が必要です。

* **Power BI Pro ライセンス**。 Power BI Pro にサインアップしていない場合は、[無料試用版にサインアップ](https://powerbi.microsoft.com/pricing/)してから始めてください。

* 独自の **Azure Active Directory テナントのセットアップ**。 セットアップ方法については、[Azure Active Directory テナントの作成](https://docs.microsoft.com/power-bi/developer/embedded/create-an-azure-active-directory-tenant)に関するページを参照してください。

* 上記のテナントに登録されている **サービス プリンシパル (アプリ専用トークン)** 。 詳細については、「[サービス プリンシパルとアプリケーション シークレットを使用した Power BI コンテンツの埋め込み](https://docs.microsoft.com/power-bi/developer/embedded/embed-service-principal)」を参照してください。 必ず、アプリケーションを **サーバー側 Web アプリケーション** として登録してください。 アプリケーション シークレットを作成するには、サーバー側 Web アプリケーションを登録します。 以降の手順のために、このプロセスから "*アプリケーション ID*" (クライアント ID) と "*アプリケーション シークレット*" (クライアント シークレット) を保存する必要があります。

* インストール用に準備された、**パラメーター化されたテンプレート アプリ**。 テンプレート アプリは、Azure Active Directory (Azure AD) にアプリケーションを登録するものと同じテナント内に作成する必要があります。 詳細については、[テンプレート アプリのヒント](https://docs.microsoft.com/power-bi/connect-data/service-template-apps-tips.md)に関するページまたは「[Power BI でテンプレート アプリを作成する](https://docs.microsoft.com/power-bi/connect-data/service-template-apps-create)」を参照してください。 以降の手順のために、テンプレート アプリから、
     * アプリの作成時に [テンプレート アプリのプロパティを定義する](../../connect-data/service-template-apps-create.md#define-the-properties-of-the-template-app)プロセスの終了時にインストール URL 内に表示される "*アプリ ID*"、"*パッケージ キー*"、"*所有者 ID*" をメモしておく必要があります。 また、テンプレート アプリの [[リリース管理]](../../connect-data/service-template-apps-create.md#manage-the-template-app-release) で **[リンクの取得]** をクリックして、同じリンクを取得することもできます。

    * テンプレート アプリのデータセットで定義されている "*パラメーター名*"。 パラメーター名は、大文字と小文字を区別する文字列であり、[テンプレート アプリのプロパティを定義する](../../connect-data/service-template-apps-create.md#define-the-properties-of-the-template-app)ときに **[Parameter Settings]\(パラメーターの設定\)** タブから、または Power BI のデータセット設定から取得することもできます。

    >[!NOTE]
    >AppSource でまだ一般公開されていない場合でも、テンプレート アプリをインストールする準備ができていれば、テンプレート アプリで、アプリケーションの事前構成されたインストールをテストできます。 ただし、テナント外のユーザーが自動インストール アプリケーションを使用してテンプレート アプリをインストールできるようにするには、テンプレート アプリが [Power BI アプリ マーケットプレース](https://app.powerbi.com/getdata/services)で一般公開されている必要があります。 このため、作成している自動インストール アプリケーションを使用するテンプレート アプリは、配布する前に、必ず[パートナー センター](https://docs.microsoft.com/azure/marketplace/partner-center-portal/create-power-bi-app-offer)に公開してください。

## <a name="main-steps-and-apis"></a>主な手順と API

以下のセクションでは、テンプレート アプリのインストールの構成を自動化するための主な手順と必要な API について説明します。 ほとんどの手順は、[Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/) を使用して実行されますが、以下で説明するコード例は **.NET SDK** を使用して作成されています。

## <a name="step-1-create-a-power-bi-client-object"></a>手順 1:Power BI クライアント オブジェクトを作成する 

Power BI REST API を使用するには、**Azure AD** から [サービス プリンシパル](../embedded/embed-service-principal.md)の **アクセス トークン** を取得する必要があります。 [Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/) への呼び出しを行う前に、Power BI アプリケーションのための [Azure AD アクセス トークン](../embedded/get-azuread-access-token.md#access-token-for-non-power-bi-users-app-owns-data)を取得する必要があります。
**アクセス トークン** を使用して Power BI クライアントを作成するには、[Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/) と対話できる Power BI クライアント オブジェクトを作成する必要があります。 **AccessToken** を *_Microsoft.Rest.TokenCredentials_* オブジェクトでラップして、Power BI クライアント オブジェクトを作成します。

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.Rest;
using Microsoft.PowerBI.Api.V2;

var tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");

// Create a Power BI Client object. it's used to call Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Your code to goes here.
}
```

## <a name="step-2-create-an-install-ticket"></a>手順 2:インストール チケットを作成する

インストール チケットを作成します。これは、ユーザーを Power BI にリダイレクトするときに使用されます。 この操作に使用される API は、*CreateInstallTicket* API です。
* [Template Apps CreateInstallTicket](https://docs.microsoft.com/rest/api/power-bi/templateapps/createinstallticket)

テンプレート アプリのインストールと構成用のインストール チケット作成するサンプルは、[サンプル アプリケーション](https://github.com/microsoft/Template-apps-examples/tree/master/Developer%20Samples/Automated%20Install%20Azure%20Function/InstallTemplateAppSample)内の [InstallTemplateApp/InstallAppFunction.cs](https://github.com/microsoft/Template-apps-examples/blob/master/Developer%20Samples/Automated%20Install%20Azure%20Function/InstallTemplateAppSample/InstallTemplateApp/InstallAppFunction.cs) ファイルから入手できます。


テンプレート アプリ *CreateInstallTicket* REST API を使用するコード例を次に示します。
```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// Create Install Ticket Request.
InstallTicket ticketResponse = null;
var request = new CreateInstallTicketRequest()
{
    InstallDetails = new List<TemplateAppInstallDetails>()
    {
        new TemplateAppInstallDetails()
        {
            AppId = Guid.Parse(AppId),
            PackageKey = PackageKey,
            OwnerTenantId = Guid.Parse(OwnerId),
            Config = new TemplateAppConfigurationRequest()
            {
                Configuration = Parameters
                                    .GroupBy(p => p.Name)
                                    .ToDictionary(k => k.Key, k => k.Select(p => p.Value).Single())
            }
        }
    }
};

// Issue the request to the REST API using .NET SDK
InstallTicket ticketResponse = await client.TemplateApps.CreateInstallTicketAsync(request);
```

## <a name="step-3-redirect-users-to-power-bi-with-the-ticket"></a>手順 3:チケットを使用してユーザーを Power BI にリダイレクトする

インストール チケットを作成したら、それを使用してユーザーを Power BI にリダイレクトし、テンプレート アプリのインストールと構成を続行します。 このためには、要求本文にインストール チケットを含めた ```POST``` メソッドを使用して、テンプレート アプリのインストール URL にリダイレクトします。

```POST``` 要求を使用してリダイレクトを発行する方法については、さまざまな方法が文書化されています。 どれを選択するかは、シナリオと、ユーザーがポータルまたはサービスを操作する方法によって異なります。

主にテストの目的で使用される簡単な例では、非表示フィールドがあるフォームを利用します。これは、読み込み時に自動的に送信されます。

```javascript
<html>
    <body onload='document.forms["form"].submit()'>
        <!-- form method is POST and action is the app install URL -->
        <form name='form' action='https://app.powerbi.com/....' method='post' enctype='application/json'>
            <!-- value should be the new install ticket -->
            <input type='hidden' name='ticket' value='H4sI....AAA='>
        </form>
    </body>
</html>
```

インストール チケットを保持し、ユーザーを自動的に Power BI にリダイレクトする[サンプル アプリケーション](https://github.com/microsoft/Template-apps-examples/tree/master/Developer%20Samples/Automated%20Install%20Azure%20Function/InstallTemplateAppSample)の応答の例を次に示します。 この Azure 関数の応答は、実際には、上記の html の例に見られる自動自己送信フォームと同じです。

```csharp
...
    return new ContentResult() { Content = RedirectWithData(redirectUrl, ticket.Ticket), ContentType = "text/html" };
}

...

public static string RedirectWithData(string url, string ticket)
{
    StringBuilder s = new StringBuilder();
    s.Append("<html>");
    s.AppendFormat("<body onload='document.forms[\"form\"].submit()'>");
    s.AppendFormat("<form name='form' action='{0}' method='post' enctype='application/json'>", url);
    s.AppendFormat("<input type='hidden' name='ticket' value='{0}' />", ticket);
    s.Append("</form></body></html>");
    return s.ToString();
}
```

>[!Note]
>```POST```ブラウザー リダイレクトを使用するにはさまざまな方法がありますが、サービスのニーズと制限に応じて、常に最も安全な方法を使用する必要があります。 安全ではないリダイレクト形式によっては、ユーザーまたはサービスがセキュリティ上の問題にさらされる可能性があることに注意してください。

## <a name="step-4-move-your-automation-to-production"></a>手順 4.自動化を運用環境に移行する

設計した自動化の準備ができたら、必ず運用環境に移行してください。

## <a name="next-steps"></a>次のステップ

* [チュートリアル](template-apps-auto-install-tutorial.md)を試してみてください。ここでは、単純な Azure 関数を使用してテンプレート アプリのインストールの構成を自動化します。

* 他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
