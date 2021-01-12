---
title: 顧客向けにテンプレート アプリのインストールの構成を自動化する
description: テンプレート アプリのインストールの構成を自動化する方法について説明します。
author: paulinbar
ms.author: painbar
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 11/23/2020
ms.openlocfilehash: 33de464a1bb1389fadfbc7a85ded9365321e0a62
ms.sourcegitcommit: 932f6856849c39e34229dc9a49fb9379c56a888a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2021
ms.locfileid: "97926301"
---
# <a name="automated-configuration-of-a-template-app-installation"></a>テンプレート アプリのインストールの自動構成

テンプレート アプリは、顧客がデータから分析情報の取得を開始するのに最適な方法です。 テンプレート アプリをデータに接続することで、迅速に作業を開始できます。 テンプレート アプリにより、希望に応じてカスタマイズできる、事前に作成されたレポートが提供されます。

データへの接続方法の詳細に顧客が精通しているとは限りません。 テンプレート アプリをインストールするときにこれらの詳細を提供する必要があることは、彼らにとって問題になる可能性があります。

データ サービス プロバイダーとして、ご自身のサービスで顧客がデータを使い始めるのに役立つテンプレート アプリを作成している場合は、彼らがテンプレート アプリを簡単にインストールできるようにすることができます。 テンプレート アプリのパラメーターの構成を自動化できます。 顧客はポータルにサインインすると、準備された特別なリンクを選択します。 このリンクは:

- 必要な情報を収集するオートメーションを起動します。
- テンプレート アプリのパラメーターをあらかじめ構成します。
- アプリをインストールできる Power BI アカウントに顧客をリダイレクトします。

行う必要があるのは、 **[インストール]** を選択し、データ ソースに対して認証を行うことだけです。それで準備は完了です。

このカスタマー エクスペリエンスを次に示します。

![自動インストール アプリケーションを使用するユーザー エクスペリエンスの図。](media/template-apps-auto-install/high-level-flow.png)

この記事では、テンプレート アプリのインストールの構成を自動化するために必要な基本のフローと前提条件、および主な手順と API について説明します。 すぐに開始したい場合は、[チュートリアル](template-apps-auto-install-tutorial.md)に進んでください。Azure 関数を使用するように準備された簡単なサンプル アプリケーションを使用して、テンプレート アプリのインストールの構成を自動化できます。

## <a name="basic-flow"></a>基本のフロー

テンプレート アプリのインストールの構成を自動化するための基本のフローは、次のとおりです。

1. ユーザーは、ISV のポータルにログインして、指定されたリンクを選択します。 これにより、自動化されたフローが開始されます。 この段階で、ISV のポータルにより、ユーザー固有の構成が準備されます。

1. ISV は、ISV のテナントに登録されている [サービス プリンシパル (アプリ専用トークン)](../embedded/embed-service-principal.md) に基づいて、"*アプリ専用*" トークンを取得します。

1. ISV は、[Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/) を使用して、*インストール チケット* を作成します。この中には、ISV によって準備されたユーザー固有のパラメーター構成が含まれます。

1. ISV は、インストール チケットを含む ```POST``` リダイレクト メソッドを使用して、ユーザーを Power BI にリダイレクトします。

1. ユーザーは、インストール チケットを使用して Power BI アカウントにリダイレクトされ、テンプレート アプリをインストールするように求められます。 ユーザーが **[インストール]** を選択すると、テンプレート アプリが自動的にインストールされます。

>[!Note]
>パラメーター値は、インストール チケットの作成プロセス中に ISV によって構成されますが、データ ソース関連の資格情報は、インストールの最終段階でユーザーによってのみ提供されます。 この処理により、それらがサードパーティに公開されるのを防ぎ、ユーザーとテンプレート アプリのデータ ソースとの間にセキュリティで保護された接続を確保します。

## <a name="prerequisites"></a>前提条件

テンプレート アプリの事前構成済みのインストール エクスペリエンスを提供するには、次の前提条件が必要です。

* Power BI Pro ライセンス。 Power BI Pro にサインアップしていない場合は、[無料試用版にサインアップ](https://powerbi.microsoft.com/pricing/)してから始めてください。
* 独自の Azure Active Directory (Azure AD) テナントの設定。 その設定方法については、[Azure AD テナントの作成](https://docs.microsoft.com/power-bi/developer/embedded/create-an-azure-active-directory-tenant)に関するページを参照してください。
* 前述のテナントに登録されている **サービス プリンシパル (アプリ専用トークン)** 。 詳細については、「[サービス プリンシパルとアプリケーション シークレットを使用した Power BI コンテンツの埋め込み](https://docs.microsoft.com/power-bi/developer/embedded/embed-service-principal)」を参照してください。 必ず、アプリケーションを **サーバー側 Web アプリケーション** として登録してください。 アプリケーション シークレットを作成するには、サーバー側 Web アプリケーションを登録します。 以降の手順のために、このプロセスから "*アプリケーション ID*" (ClientID) と "*アプリケーション シークレット*" (ClientSecret) を保存する必要があります。
* インストール用に準備された、**パラメーター化されたテンプレート アプリ**。 テンプレート アプリは、Azure AD でアプリケーションを登録するのと同じテナント内に作成する必要があります。 詳細については、[テンプレート アプリのヒント](https://docs.microsoft.com/power-bi/connect-data/service-template-apps-tips)に関するページまたは「[Power BI でテンプレート アプリを作成する](https://docs.microsoft.com/power-bi/connect-data/service-template-apps-create)」を参照してください。 以降の手順のために、テンプレート アプリから次の情報をメモしておく必要があります。
     * アプリの作成時に [テンプレート アプリのプロパティを定義する](../../connect-data/service-template-apps-create.md#define-the-properties-of-the-template-app)プロセスの終わりの時点でインストール URL 内に表示される、"*アプリ ID*"、"*パッケージ キー*"、"*所有者 ID*"。 また、テンプレート アプリの [[リリース管理] ウィンドウ](../../connect-data/service-template-apps-create.md#manage-the-template-app-release)で **[リンクの取得]** を選択することでも同じリンクを取得できます。
    * テンプレート アプリのデータセットで定義されている "*パラメーター名*"。 パラメーター名は、大文字と小文字を区別する文字列であり、[テンプレート アプリのプロパティを定義する](../../connect-data/service-template-apps-create.md#define-the-properties-of-the-template-app)ときに **[Parameter Settings]\(パラメーターの設定\)** タブから、または Power BI のデータセット設定から取得することもできます。

    >[!NOTE]
    >AppSource でまだ一般公開されていない場合でも、テンプレート アプリをインストールする準備ができていれば、テンプレート アプリで、事前構成されたインストール アプリケーションをテストできます。 テナント外のユーザーが自動インストール アプリケーションを使用してテンプレート アプリをインストールできるようにするには、テンプレート アプリが [Power BI アプリ マーケットプレース](https://app.powerbi.com/getdata/services)で一般公開されている必要があります。 テンプレート アプリは、作成している自動インストール アプリケーションを使用して配布する前に、必ず[パートナー センター](https://docs.microsoft.com/azure/marketplace/partner-center-portal/create-power-bi-app-offer)に公開してください。

## <a name="main-steps-and-apis"></a>主な手順と API

以下のセクションでは、テンプレート アプリのインストールの構成を自動化するための主な手順と必要な API について説明します。 ほとんどの手順は、[Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/) を使用して実行されますが、ここで説明するコード例は .NET SDK を使用して作成されています。

## <a name="step-1-create-a-power-bi-client-object"></a>手順 1:Power BI クライアント オブジェクトを作成する

Power BI REST API を使用するには、Azure AD から [サービス プリンシパル](../embedded/embed-service-principal.md)の *アクセス トークン* を取得する必要があります。 [Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/) への呼び出しを行う前に、Power BI アプリケーションのための [Azure AD アクセス トークン](../embedded/get-azuread-access-token.md#access-token-for-non-power-bi-users-app-owns-data)を取得する必要があります。
アクセス トークンを使用して Power BI クライアントを作成するには、[Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/) とやり取りするための Power BI クライアント オブジェクトを作成する必要があります。 **AccessToken** を **Microsoft.Rest.TokenCredentials** オブジェクトでラップして、Power BI クライアント オブジェクトを作成します。

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.Rest;
using Microsoft.PowerBI.Api.V2;

var tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");

// Create a Power BI client object. It's used to call Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Your code goes here.
}
```

## <a name="step-2-create-an-install-ticket"></a>手順 2:インストール チケットを作成する

インストール チケットを作成します。これは、ユーザーを Power BI にリダイレクトするときに使用されます。 この操作に使用される API は、**CreateInstallTicket** API です。
* [Template Apps CreateInstallTicket](https://docs.microsoft.com/rest/api/power-bi/templateapps/createinstallticket)

テンプレート アプリのインストールと構成用のインストール チケット作成する方法を示すサンプルは、[サンプル アプリケーション](https://github.com/microsoft/Template-apps-examples/tree/master/Developer%20Samples/Automated%20Install%20Azure%20Function/InstallTemplateAppSample)内の [InstallTemplateApp/InstallAppFunction.cs](https://github.com/microsoft/Template-apps-examples/blob/master/Developer%20Samples/Automated%20Install%20Azure%20Function/InstallTemplateAppSample/InstallTemplateApp/InstallAppFunction.cs) ファイルから入手できます。


次のコード例は、テンプレート アプリ **CreateInstallTicket** REST API の使用方法を示しています。
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

// Issue the request to the REST API using .NET SDK.
InstallTicket ticketResponse = await client.TemplateApps.CreateInstallTicketAsync(request);
```

## <a name="step-3-redirect-users-to-power-bi-with-the-ticket"></a>手順 3:チケットを使用してユーザーを Power BI にリダイレクトする

インストール チケットを作成したら、それを使用してユーザーを Power BI にリダイレクトし、テンプレート アプリのインストールと構成を続行します。 要求本文にインストール チケットを含めた ```POST``` メソッドを使用して、テンプレート アプリのインストール URL にリダイレクトします。

```POST``` 要求を使用してリダイレクトを発行する方法については、さまざまな方法が文書化されています。 どれを選択するかは、シナリオと、ユーザーがポータルまたはサービスを操作する方法によって異なります。

主にテストの目的で使用される簡単な例では、非表示フィールドがあるフォームを使用します。これは、読み込み時に自動的に送信されます。

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

インストール チケットを保持し、ユーザーを自動的に Power BI にリダイレクトする[サンプル アプリケーション](https://github.com/microsoft/Template-apps-examples/tree/master/Developer%20Samples/Automated%20Install%20Azure%20Function/InstallTemplateAppSample)の応答の例を次に示します。 この Azure 関数の応答は、上記の HTML の例に見られる自動自己送信フォームと同じです。

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
>```POST``` ブラウザー リダイレクトを使用するには、さまざまな方法があります。 サービスのニーズと制限に応じて、常に最も安全な方法を使用する必要があります。 安全ではないリダイレクト形式によっては、ユーザーまたはサービスがセキュリティ上の問題にさらされる可能性があることに注意してください。

## <a name="step-4-move-your-automation-to-production"></a>手順 4.自動化を運用環境に移行する

設計した自動化の準備ができたら、必ず運用環境に移行してください。

## <a name="next-steps"></a>次のステップ

* シンプルな Azure 関数を使用してテンプレート アプリのインストールの構成を自動化する[チュートリアル](template-apps-auto-install-tutorial.md)を試してみてください。
* 他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
