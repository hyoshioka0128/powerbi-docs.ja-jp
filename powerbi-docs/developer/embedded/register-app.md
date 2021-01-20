---
title: 埋め込み BI 分析情報を向上させるため、Power BI 埋め込み分析アプリケーションに Power BI コンテンツを埋め込むアプリを登録する
description: 埋め込みの Power BI コンテンツとともに使用するため、Azure Active Directory 内にアプリケーションを登録する方法を説明します。 Power BI 埋め込み分析を使用して、より優れた埋め込み BI インサイトを有効にします。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: nishalit
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 04/02/2019
ms.openlocfilehash: 624e0a2838a08d1cf68ae58223fe979a56312b48
ms.sourcegitcommit: 1cad78595cca1175b82c04458803764ac36e5e37
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2021
ms.locfileid: "98565924"
---
# <a name="register-an-azure-ad-application-to-use-with-power-bi"></a>Azure AD アプリケーションを登録して Power BI とともに使用する

Power BI 埋め込み分析を使用するには、Azure Active Directory (Azure AD) アプリケーションを Azure に登録する必要があります。 Azure AD アプリで Power BI REST リソースのアクセス許可を確立し、[Power BI REST API](/rest/api/power-bi/) にアクセスできるようにします。

## <a name="determine-your-embedding-solution"></a>埋め込みソリューションを決定する

アプリを登録する前に、次のソリューションのうちご自身に最も適しているものを決定します。

* 顧客向けに埋め込む
* 組織向けに埋め込む

### <a name="embed-for-your-customers"></a>顧客向けに埋め込む

顧客向けに設計されたアプリケーションの作成を計画している場合は、[顧客向けに埋め込む](embed-sample-for-customers.md)ソリューション ("*アプリ所有データ*" とも呼ばれます) を使用します。 ユーザーがアプリケーションを使用するには、Power BI にサインインすることも、Power BI ライセンスを持っていることも必要ありません。 アプリケーションで次のいずれかの方法を使用して、Power BI に対して認証を行います。

* **マスター ユーザー** アカウント (Power BI へのサインインに使用する Power BI Pro ライセンス)

* [サービス プリンシパル](embed-service-principal.md)

顧客向けに埋め込むソリューションは、通常、独立系ソフトウェア ベンダー (ISV) およびサードパーティ向けアプリケーションを作成する開発者によって使用されます。

### <a name="embed-for-your-organization"></a>組織向けに埋め込む

Power BI に対してユーザーが自分の資格情報を使用して認証する必要があるアプリケーションの作成を計画している場合は、[組織向けに埋め込む](embed-sample-for-your-organization.md)ソリューション ("*ユーザー所有データ*" とも呼ばれます) を使用します。

組織向けに埋め込むソリューションは、通常、企業や大規模な組織で使用され、内部ユーザーを対象としています。

## <a name="register-an-azure-ad-app"></a>Azure AD アプリの登録

Azure AD アプリを登録する最も簡単な方法は、[Power BI 埋め込みセットアップ ツール](https://app.powerbi.com/embedsetup)を使用することです。 そのツールには、単純なグラフィカル インターフェイスを使用した、両方の埋め込みソリューションの簡単な登録プロセスが用意されています。

"*組織向けに埋め込む*" アプリケーションを作成していて、Azure AD アプリをより詳細に制御する必要がある場合は、Azure portal に手動で登録することができます。

> [!IMPORTANT]
> Power BI アプリを登録する前に、[Azure Active Directory テナントと組織のユーザー](create-an-azure-active-directory-tenant.md)が必要です。

# <a name="embed-for-your-customers"></a>[顧客向けに埋め込む](#tab/customers)

これらの手順では、Power BI の[顧客向けに埋め込む](embed-sample-for-customers.md)ソリューション用に Azure AD アプリケーションを登録する方法について説明します。

[!INCLUDE[registration tool step 1](../../includes/register-tool-step-1.md)]

2. *[Choose an embedding solution]\(埋め込みソリューションを選択\)* セクションで、 **[Embed for your customers]\(顧客向けに埋め込む\)** を選択します。

[!INCLUDE[registration tool step 3](../../includes/register-tool-step-3.md)]

4. *[手順 2 - アプリケーションの登録]* で、次のフィールドに入力します。

    * **[アプリケーション名]** - アプリケーションに名前を付けます。

    * **[API アクセス]** - アプリケーションに必要な Power BI API (スコープとも呼ばれます) を選択します。 *[すべて選択]* を使用すると、すべての API を選択できます。 Power BI アクセス許可の詳細については、「[Microsoft ID プラットフォーム エンドポイントでのアクセス許可と同意](/azure/active-directory/develop/v2-permissions-and-consent)」を参照してください。

5. **[登録]** を選択します。

    Azure AD アプリの **アプリケーション ID** が *[概要]* ボックスに表示されます。 この値を後で使用するためにコピーします。

[!INCLUDE[registration tool steps 6-7](../../includes/register-tool-steps-6-7.md)]

8. *[手順 5 - アクセス許可の付与]* で、 **[アクセス許可の付与]** を選択し、ポップアップ ウィンドウで **[accept]\(承諾\)** を選択します。 これにより、Azure AD アプリから、サインインしているユーザーで選択した API (スコープとも呼ばれます) にアクセスできるようになります。 このユーザーは、**マスター ユーザー** とも呼ばれます。

9. (省略可能) Power BI ワークスペースを作成し、このツールを使用してそこにコンテンツをアップロードした場合は、ここで **[Download sample application]\(サンプル アプリケーションのダウンロード\)** を選択できます。 必ず *[概要]* ボックス内のすべての情報をコピーしてください。

[!INCLUDE[registration tool note](../../includes/register-tool-note.md)]

# <a name="embed-for-your-organization"></a>[組織向けの埋め込み](#tab/organization)

これらの手順では、Power BI の[組織向けに埋め込む](embed-sample-for-your-organization.md)ソリューション用に Azure AD アプリケーションを登録する方法について説明します。

[!INCLUDE[registration tool step 1](../../includes/register-tool-step-1.md)]

2. *[Choose an embedding solution]\(埋め込みソリューションを選択\)* セクションで、 **[Embed for your organization]\(組織向けに埋め込む\)** を選択します。

[!INCLUDE[registration tool step 3](../../includes/register-tool-step-3.md)]

4. *[手順 2 - アプリケーションの登録]* で、次のフィールドに入力します。

    * **[アプリケーション名]** - アプリケーションに名前を付けます。

    * **[ホーム ページ URL]** - ホーム ページの URL を入力します。

    * **[リダイレクト URL]** - サインイン時、アプリケーションが Azure から認証コードを受け取ったときに、アプリケーション ユーザーがこのアドレスにリダイレクトされます。 次のいずれかのオプションを選択します。

        * **[Use a default URL]\(既定の URL を使用する\)** - このオプションを使用すると、サンプルの埋め込み分析アプリケーションが自動的に作成されてダウンロードされます。 既定の URL は http://localhost:13526/ です。

        * **[Use a custom URL]\(カスタム URL を使用する\)** - 埋め込み分析アプリケーションが既に存在し、何をリダイレクト URL として使用するかを把握している場合は、このオプションを選択します。

    * **[API アクセス]** - アプリケーションに必要な Power BI API (スコープとも呼ばれます) を選択します。 *[すべて選択]* を使用すると、すべての API を選択できます。 Power BI アクセス許可の詳細については、「[Microsoft ID プラットフォーム エンドポイントでのアクセス許可と同意](/azure/active-directory/develop/v2-permissions-and-consent)」を参照してください。

5. **[登録]** を選択します。

    Azure AD アプリの **アプリケーション ID** および **アプリケーション シークレット** の値が、 *[概要]* ボックスに表示されます。 後で使用するために、これらの値をコピーします。

[!INCLUDE[registration tool steps 6-7](../../includes/register-tool-steps-6-7.md)]

8. (省略可能) Power BI ワークスペースを作成し、このツールを使用してそこにコンテンツをアップロードした場合は、ここで **[Download sample application]\(サンプル アプリケーションのダウンロード\)** を選択できます。 必ず *[概要]* ボックス内のすべての情報をコピーしてください。

[!INCLUDE[registration tool note](../../includes/register-tool-note.md)]

# <a name="manual-registration"></a>[手動登録](#tab/manual)

Azure AD 手動アプリ登録は、次のいずれかのソリューションを作成している場合にのみ使用します。

* "*組織向けの埋め込み*" アプリケーション。

* "*サービス プリンシパル*" を使用した、"*顧客向けの埋め込み*" アプリケーション。

    >[!NOTE]
    >このオプションを選択した場合は、Azure AD アプリを登録した後で、それに [Power BI アクセス許可を追加](#change-your-azure-ad-apps-permissions)する必要があります。

Azure Active Directory でアプリケーションを登録する方法の詳細については、[アプリを Azure Active Directory に登録する](/azure/active-directory/develop/quickstart-v2-register-an-app)方法に関するページを参照してください。

1. [Azure Portal](https://portal.azure.com) にサインインします。

2. ページの右上隅でご自分のアカウントを選択することで、ご自分の Azure AD テナントを選択します。

3. **[アプリの登録]** を選択します。 このオプションが表示されない場合は、検索してください。
 
4. *[アプリの登録]* で **[新しい登録]** を選択します。

5. 以下のフィールドを設定します。

    * **[名前]** - アプリケーションに名前を付けます。

    * **[Supported account type]\(サポートされているアカウントの種類\)** - だれがアプリケーションを使用できるかを選択します。

6. (省略可能) **[リダイレクト URI]** にダイレクト URL を追加します。

7. **[登録]** を選択します。 アプリが登録されると、アプリの概要ページが表示され、そこで *アプリケーション ID* を取得できます。

---

## <a name="change-your-azure-ad-apps-permissions"></a>Azure AD アプリのアクセス許可を変更する

アプリケーションを登録した後、そのアクセス許可を変更できます。 アクセス許可の変更は、プログラムまたは Azure portal で行うことができます。

>[!NOTE]
>Azure AD アプリのアクセス許可は、"*マスター ユーザー*" 認証方法を使用した、"*顧客向けの埋め込み*" ソリューションにのみ適用されます。

# <a name="azure"></a>[Azure](#tab/Azure)

Azure portal 上でアプリを表示し、そのアクセス許可を変更することができます。

1. [Azure Portal](https://portal.azure.com) にサインインします。

2. ページの右上隅でご自分のアカウントを選択することで、ご自分の Azure AD テナントを選択します。

3. **[アプリの登録]** を選択します。 このオプションが表示されない場合は、検索してください。

4. **[Owned applications]\(所有しているアプリケーション\)** タブから、アプリを選択します。 *[概要]* タブにアプリケーションが開き、そこで *アプリケーション ID* を確認できます。

5. **[API のアクセス許可]** タブを選択します。

6. アクセス許可を追加するには、これらの手順に従います。

    1. **[アクセス許可の追加]** を選択し、次に **[Power BI サービス]** を選択します。

    2. **[委任されたアクセス許可]** を選択し、必要な特定のアクセス許可を追加または削除します。

    3. 完了したら、 **[アクセス許可の追加]** を選択して変更を保存します。

7. アクセス許可を削除するには、これらの手順に従います。

    1. アクセス許可の右側にある省略記号 (...) を選択します。
    
    2. **[アクセス許可の削除]** を選択します。
    
    3. *[アクセス許可の削除]* ポップアップ ウィンドウで、 **[はい、削除します]** を選択します。

# <a name="http"></a>[HTTP](#tab/HTTP)

Azure AD アプリのアクセス許可をプログラムで変更するには、テナント内の既存のサービス プリンシパル (ユーザー) を取得する必要があります。 その方法については、「[servicePrincipal](/graph/api/resources/serviceprincipal)」を参照してください。

1. テナント内のすべてのサービス プリンシパルを取得するには、`{ID}` を使用せずに `Get servicePrincipal` API を呼び出します。

2. `appId` プロパティとしてアプリの *アプリケーション ID* を使用してサービス プリンシパルを確認します。

    ```json
    Post https://graph.microsoft.com/v1.0/servicePrincipals HTTP/1.1
    Authorization: Bearer ey..qw
    Content-Type: application/json
    {
    "accountEnabled" : true,
    "appId" : "{App_Client_ID}",
    "displayName" : "{App_DisplayName}"
    }
    ```

    >[!NOTE]
    >`displayName` はオプションです。

3. これらのいずれかの値を `consentType` に割り当てて、アプリに Power BI アクセス許可を付与します。

    * `AllPrincipals` - Power BI 管理者がテナント内のすべてのユーザーの代理でアクセス許可を付与するためにのみ使用できます。

    * `Principal` - 特定のユーザーの代理でアクセス許可を付与するために使用します。 このオプションを使用している場合は、`principalId={User_ObjectId}` プロパティを要求本文に追加します。

     ```json
     Post https://graph.microsoft.com/v1.0/OAuth2PermissionGrants HTTP/1.1
     Authorization: Bearer ey..qw
     Content-Type: application/json
     {
     "clientId":"{Service_Plan_ID}",
     "consentType":"AllPrincipals",
     "resourceId":"c78a3685-1ce7-52cd-95f7-dc5aea8ec98e",
     "scope":"Dataset.ReadWrite.All Dashboard.Read.All Report.Read.All Group.Read Group.Read.All Content.Create Metadata.View_Any Dataset.Read.All Data.Alter_Any",
     "expiryTime":"2018-03-29T14:35:32.4943409+03:00",
     "startTime":"2017-03-29T14:35:32.4933413+03:00"
     }
     ```

    >[!NOTE]
    >* **マスター ユーザー** を使用している場合、Azure AD による同意を求めるメッセージが表示されないようにするには、マスター アカウントにアクセス許可を付与する必要があります。
    >* `resourceId` *c78a3685-1ce7-52cd-95f7-dc5aea8ec98e* はテナントに依存し、ユニバーサルではありません。 この値は、Azure AD 内の "*Power BI サービス*" アプリケーションの *objectId* です。 Azure portal からこの値を取得するには、[[エンタープライズ アプリケーション] > [すべてのアプリケーション]](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/AllApps) に移動し、"*Power BI サービス*" を検索します。

4. `consentType` に値を割り当てることにより、アプリのアクセス許可を Azure AD に付与します。

    ```json
    Post https://graph.microsoft.com/v1.0/OAuth2PermissionGrants HTTP/1.1
    Authorization: Bearer ey..qw
    Content-Type: application/json
    {
    "clientId":"{Service_Plan_ID}",
    "consentType":"AllPrincipals",
    "resourceId":"61e57743-d5cf-41ba-bd1a-2b381390a3f1",
    "scope":"User.Read Directory.AccessAsUser.All",
    "expiryTime":"2018-03-29T14:35:32.4943409+03:00",
    "startTime":"2017-03-29T14:35:32.4933413+03:00"
    }
    ```

# <a name="c"></a>[C#](#tab/CSharp)

また、C# を使用して Azure AD アプリのアクセス許可を変更することもできます。 詳細については、[oAuth2PermissionGrant](/graph/api/oauth2permissiongrant-get) API に関するページを参照してください。 この方法は、プロセスの一部を自動化することを検討している場合に便利です。

HTTP 要求に関する詳細については、[[HTTP] タブ](register-app.md?tabs=customers%2CHTTP#change-your-azure-ad-apps-permissions)を参照してください。

```csharp
var graphClient = GetGraphClient();

currentState.createdApp = await graphClient.Applications
    .Request()
    .AddAsync(application);

System.Threading.Thread.Sleep(2000);

var passwordCredential = new PasswordCredential
{
    DisplayName = "Client Secret Created in C#"
};

currentState.createdSecret = await graphClient.Applications[currentState.createdApp.Id]
    .AddPassword(passwordCredential)
    .Request()
    .PostAsync();

var servicePrincipal = new ServicePrincipal
{
    AppId = currentState.createdApp.AppId
};

currentState.createdServicePrincipal = await graphClient.ServicePrincipals
    .Request()
    .AddAsync(servicePrincipal);

GraphServiceClient graphClient = new GraphServiceClient(authProvider);

// Use oAuth2PermissionGrant to change permissions
var oAuth2PermissionGrant = await graphClient.Oauth2PermissionGrants["{id}"]
               .Request()
               .GetAsync();
```

---

## <a name="next-steps"></a>次のステップ

>[!div class="nextstepaction"]
>[Power BI アプリケーション用の Azure AD アクセス トークンを取得する](get-azuread-access-token.md)

その他の質問 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。