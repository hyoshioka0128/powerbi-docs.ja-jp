---
title: 組織向けの埋め込み BI 分析情報を向上させるため、Power BI 埋め込み分析アプリケーションにコンテンツを埋め込む
description: 埋め込み分析ソフトウェア、埋め込み分析ツール、または埋め込みビジネス インテリジェンス ツールを使って、ご自身のアプリケーションに Power BI を統合する方法について説明します。 Power BI 埋め込み分析を使用して、より優れた埋め込み BI インサイトを有効にします。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: tutorial
ms.custom: seodec18
ms.date: 12/17/2020
ms.openlocfilehash: fbae63597ecf4ff36783ad83785f87c242359f90
ms.sourcegitcommit: 2e81649476d5cb97701f779267be59e393460097
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/02/2021
ms.locfileid: "99495000"
---
# <a name="tutorial-embed-power-bi-content-using-a-sample-embed-for-your-organization-application"></a>チュートリアル:"*組織向けの埋め込み*" サンプル アプリケーションを使用して Power BI コンテンツを埋め込む

Power BI 埋め込み分析を使用すると、レポート、ダッシュボードおよびタイルなどの Power BI コンテンツをアプリケーションに埋め込むことができます。

このチュートリアルでは、次の方法について説明します。

>[!div class="checklist"]
>* 埋め込み環境を設定する。
>* "*組織向けの埋め込み*" ("*ユーザー所有データ*" ともいう) サンプル アプリケーションを構成する。

アプリケーションを使用するために、ユーザーが Power BI にサインインする必要はありません。

組織向けに埋め込むソリューションは、通常、企業や大規模な組織で使用され、内部ユーザーを対象としています。

## <a name="code-sample-specifications"></a>コード サンプルの仕様

このチュートリアルには、次のフレームワークのいずれかで "*組織向けの埋め込み*" サンプル アプリケーションを構成する手順が含まれています。

* .NET Framework
* .NET Core
* React TypeScript

>[!NOTE]
>*.NET Core* と *.NET Framework* のサンプルを使用すると、エンド ユーザーは Power BI サービスでアクセスできる任意の Power BI ダッシュボード、レポートまたはタイルを表示できます。 *React TypeScript* のサンプルを使用すると、エンド ユーザーは Power BI サービスで既にアクセスできるレポートを 1 つだけ埋め込むことができます。

このコード サンプルでは次のブラウザーがサポートされています。

* Microsoft Edge
* Google Chrome
* Mozilla Firefox

## <a name="prerequisites"></a>前提条件

このチュートリアルを開始する前に、以下に一覧表示されている Power BI とコードの両方の依存関係があることを確認してください。

* **Power BI の依存関係**

    * 独自の [Azure Active Directory テナント](create-an-azure-active-directory-tenant.md)。

    * 次のいずれかのライセンス:

        * [Power BI Pro](../../admin/service-admin-purchasing-power-bi-pro.md)

        * [Premium Per User (PPU)](../../admin/service-premium-per-user-faq.md)

    >[!NOTE]
    >[運用環境に移行する](move-to-production.md)には、次のいずれかの構成が必要です。
    >* Pro ライセンスを持つすべてのユーザー。
    >* PPU ライセンスを持つすべてのユーザー。
    >* [容量](embedded-capacity.md)。 この構成を使用すると、すべてのユーザーが無料ライセンスを持つことができます。

* **コードの依存関係**

    # <a name="net-core"></a>[.NET Core](#tab/net-core)

    * [.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) (またはそれ以降)
    
    * 統合開発環境 (IDE)。 次のいずれかを使用することをお勧めします。

        * [Visual Studio](https://visualstudio.microsoft.com/)

        * [Visual Studio Code](https://code.visualstudio.com/)

    # <a name="net-framework"></a>[.NET Framework](#tab/net-framework)

    * [.NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/)
    
    * [Visual Studio](https://visualstudio.microsoft.com/)

    # <a name="react-typescript"></a>[React TypeScript](#tab/react)

    * テキスト エディター

    * コマンド ライン ターミナル (または PowerShell)

---

## <a name="method"></a>Method

"*組織向けの埋め込み*" サンプル アプリを作成するには、これらの手順に従います。

1. [Azure AD アプリケーションを登録します](#step-1---register-an-azure-ad-application)。

2. [Power BI ワークスペースを作成します](#step-2---create-a-power-bi-workspace)。

3. [Power BI レポートを作成して発行します](#step-3---create-and-publish-a-power-bi-report)。

4. [埋め込みパラメーター値を取得します](#step-4---get-the-embedding-parameter-values)。

5. [コンテンツを埋め込みます](#step-5---embed-your-content)。

## <a name="step-1---register-an-azure-ad-application"></a>手順 1 - Azure AD アプリケーションを登録する

Azure AD にアプリケーションを登録すると、アプリの ID を確立できます。

[!INCLUDE[Register Azure AD app](../../includes/embed-tutorial-register-app.md)]

## <a name="step-2---create-a-power-bi-workspace"></a>手順 2 - Power BI ワークスペースを作成する

[!INCLUDE[Create a Power BI workspace](../../includes/embed-tutorial-create-workspace.md)]

## <a name="step-3---create-and-publish-a-power-bi-report"></a>手順 3 - Power BI レポートを作成して発行する

[!INCLUDE[Create a Power BI report](../../includes/embed-tutorial-create-report.md)]

## <a name="step-4---get-the-embedding-parameter-values"></a>手順 4 - 埋め込みパラメーター値を取得する

コンテンツを埋め込むには、いくつかのパラメーター値を取得する必要があります。 必要になるパラメーター値は、使用するサンプル アプリケーションの言語によって異なります。 以下の表には、各サンプルに必要なパラメーター値が一覧表示されています。

|パラメーター  |.NET Core  |.NET Framework  |React TypeScript |
|---------|---------|---------|---------|
|[クライアント ID](#client-id) |![適用対象:](../../media/yes.png) |![適用対象:](../../media/yes.png)         |![適用対象:](../../media/yes.png) |
|[クライアント シークレット](#workspace-id) |![適用対象:](../../media/yes.png) |![適用対象:](../../media/yes.png) |![適用対象外](../../media/no.png) |
|[ワークスペース ID]() |![適用対象外](../../media/no.png) |![適用対象外](../../media/no.png) |![適用対象:](../../media/yes.png) |
|[レポート ID]() |![適用対象外](../../media/no.png) |![適用対象外](../../media/no.png) |![適用対象:](../../media/yes.png) |

### <a name="client-id"></a>クライアント ID

>[!TIP]
>**適用対象:** ![適用対象](../../media/yes.png) .NET Core ![適用対象](../../media/yes.png) .NET Framework ![適用対象](../../media/yes.png) React TypeScript

[!INCLUDE[Get the client ID](../../includes/embed-tutorial-client-id.md)]

### <a name="client-secret"></a>クライアント シークレット

>[!TIP]
>**適用対象:** ![適用対象](../../media/yes.png) .NET Core ![適用対象](../../media/yes.png) .NET Framework ![適用対象外](../../media/no.png) React TypeScript

[!INCLUDE[Get the client secret](../../includes/embed-tutorial-client-secret.md)]

### <a name="workspace-id"></a>ワークスペース ID

>[!TIP]
>**適用対象:** ![適用対象外](../../media/no.png) .NET Core ![適用対象外](../../media/no.png) .NET Framework ![適用対象](../../media/yes.png) React TypeScript

[!INCLUDE[Get the workspace ID](../../includes/embed-tutorial-workspace-id.md)]

### <a name="report-id"></a>レポート ID

>[!TIP]
>**適用対象:** ![適用対象外](../../media/no.png) .NET Core ![適用対象外](../../media/no.png) .NET Framework ![適用対象](../../media/yes.png) React TypeScript

[!INCLUDE[Get the report ID](../../includes/embed-tutorial-report-id.md)]

## <a name="step-5---embed-your-content"></a>手順 5 - コンテンツを埋め込む

Power BI の埋め込みサンプル アプリケーションを使用すると、Power BI の "*組織向けの埋め込み*" アプリを作成できます。

Power BI レポートを埋め込むには、これらの手順に従って、"*組織向けの埋め込み*" サンプル アプリケーションを変更します。

[!INCLUDE[Embedding steps](../../includes/embed-tutorial-embedding-steps.md)]

4. アプリケーションで使用する言語に応じて、次のいずれかのフォルダーを開きます。

    * .NET Core
    * .NET Framework
    * React-TS

    >[!NOTE]
    >"*組織向けの埋め込み*" サンプル アプリケーションでサポートされるのは、上に一覧表示されているフレームワークのみです。 *Java*、*Node JS* および *Python* のサンプル アプリケーションでサポートされるのは、" *[顧客向けの埋め込み](embed-sample-for-customers.md)* " ソリューションのみです。

# <a name="net-core"></a>[.NET Core](#tab/net-core)

### <a name="configure-your-azure-ad-app"></a>Azure AD アプリを構成する

[!INCLUDE[Configure the Azure AD authentication options](../../includes/embed-tutorial-org-azure-ad-app.md)]

5. "*プラットフォーム構成*" で、 *[Web]* プラットフォームを開き、 **[リダイレクト URI]** セクションで `https://localhost:5000/signin-oidc` を追加します。

    > [!NOTE]
    >**[Web]** プラットフォームがない場合は、 **[プラットフォームを追加]** を選択し、 *[プラットフォームの構成]* ウィンドウで **[Web]** を選択します。

6. 変更を保存します。

:::image type="content" source="media/embed-sample-for-your-organization/azure-ad-net-configurations.png" alt-text=".NET Core アプリ サンプル用の Web リダイレクト URI を含む、Azure AD アプリの認証構成を示すスクリーンショット。":::

### <a name="configure-the-sample-embedding-app"></a>埋め込みサンプル アプリを構成する

1. **[組織向けの埋め込み]** フォルダーを開きます。

2. これらのいずれかの方法を使用して、"*組織向けの埋め込みサンプル アプリ*" を開きます。

    * [Visual Studio](https://visualstudio.microsoft.com/) を使用する場合は、**UserOwnsData.sln** ファイルを開きます。

    * [Visual Studio Code](https://code.visualstudio.com/) を使用する場合は、**UserOwnsData** フォルダーを開きます。

3. **appsettings.json** を開き、次のパラメーター値を入力します。

    * `ClientId` - [クライアント ID](#client-id) の GUID を使用します

    * `ClientSecret` - [クライアント シークレット](#client-secret)を使用します

### <a name="run-the-sample-app"></a>サンプル アプリを実行する

1. 適切なオプションを選択してプロジェクトを実行します。

    * **Visual Studio** を使用する場合は、 **[IIS Express]** (再生) を選択します。

    * **Visual Studio Code** を使用する場合は、 **[実行]、[デバッグの開始]** の順に選択します。

[!INCLUDE[The embedded application sample app interface](../../includes/embed-tutorial-org-sample-app.md)]

# <a name="net-framework"></a>[.NET Framework](#tab/net-framework)

### <a name="configure-your-azure-ad-app"></a>Azure AD アプリを構成する

[!INCLUDE[Configure the Azure AD authentication options](../../includes/embed-tutorial-org-azure-ad-app.md)]

5. "*プラットフォーム構成*" で、次のように構成します。

    1. *[Web]* プラットフォームの **[リダイレクト URI]** セクションで、`https://localhost:44300/` を追加します。

        > [!NOTE]
        >**[Web]** プラットフォームがない場合は、 **[プラットフォームを追加]** を選択し、 *[プラットフォームの構成]* ウィンドウで **[Web]** を選択します。
    
    2. *[Implicit grant and hybrid flows]\(暗黙的な許可およびハイブリッド フロー\)* で、 **[ID トークン]** オプションを有効にします。
    
6. 変更を保存します。

:::image type="content" source="media/embed-sample-for-your-organization/azure-ad-framework-configurations.png" alt-text=".NET Framework アプリ サンプル用の Web リダイレクト URI と選択されたアクセス トークン オプションを含む、Azure AD アプリの認証構成を示すスクリーンショット。":::

### <a name="configure-the-sample-embedding-app"></a>埋め込みサンプル アプリを構成する

1. **[組織向けの埋め込み]** フォルダーを開きます。

2. [Visual Studio](https://visualstudio.microsoft.com/) を使用して、**UserOwnsData.sln** ファイルを開きます。

3. **Web.config** を開き、次のパラメーター値を入力します。

    * `clientId` - [クライアント ID](#client-id) の GUID を使用します

    * `clientSecret` - [クライアント シークレット](#client-secret)を使用します

### <a name="run-the-sample-app"></a>サンプル アプリを実行する

1. **[IIS Express]** (再生) を選択して、プロジェクトを実行します。

[!INCLUDE[The embedded application sample app interface](../../includes/embed-tutorial-org-sample-app.md)]

# <a name="react-typescript"></a>[React TypeScript](#tab/react)

### <a name="configure-your-azure-ad-app"></a>Azure AD アプリを構成する

[!INCLUDE[Configure the Azure AD authentication options](../../includes/embed-tutorial-org-azure-ad-app.md)]

5. "*プラットフォーム構成*" で、 **[Web]** プラットフォームを次のように構成します。

    1. **[リダイレクト URI]** で、`https://localhost:3000` を追加し、 **[構成]** を選択します。

        > [!NOTE]
        >**[Web]** プラットフォームがない場合は、 **[プラットフォームを追加]** を選択し、 *[プラットフォームの構成]* ウィンドウで **[Web]** を選択します。

    2. *[Implicit grant and hybrid flows]\(暗黙的な許可およびハイブリッド フロー\)* で、次の両方のオプションを有効にします。
        * **アクセス トークン**
        * **ID トークン**
    
6. 変更を保存します。

:::image type="content" source="media/embed-sample-for-your-organization/azure-ad-react-configurations.png" alt-text="localhost 3000 用に設定された Web リダイレクト URI を含む、Azure AD アプリの認証構成を示すスクリーンショット。":::

### <a name="configure-the-sample-embedding-app"></a>埋め込みサンプル アプリを構成する

1. **[組織向けの埋め込み]**  > **UserOwnsData** > **src** フォルダーの順に開きます。

2. テキスト エディターを使用して、**Config. ts** ファイルを開き、次のパラメーター値を入力します。

    * `clientId` - [クライアント ID](#client-id) の GUID を使用します

    * `workspaceId` - [ワークスペース ID](#client-secret) を使用します

    * `reportId` - [レポート ID](#report-id) を使用します

3. ファイルを保存します。

### <a name="run-the-sample-app"></a>サンプル アプリを実行する

1. ターミナルを開き、 **[組織向けの埋め込み]**  > **UserOwnsData** の順に移動します。

2. 次のコマンドを実行して、必要な依存関係をインストールします。

   `npm install`

3. 次のコマンドを実行して、アプリケーションを実行します。

   `npm run start`

    >[!NOTE]
    >最初のサインイン時に、アプリに対する Azure AD アクセス許可を許可するように求められます。

---

## <a name="developing-your-application"></a>アプリケーションの開発

"*顧客向けの埋め込み*" サンプル アプリケーションを構成して実行した後、独自のアプリケーションの開発を開始できます。

[!INCLUDE[Move to production](../../includes/embed-tutorial-production.md)]

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
>[運用環境への移行](move-to-production.md)

>[!div class="nextstepaction"]
>[顧客向けに埋め込む](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[顧客向けにページ分割されたレポートを埋め込む](embed-paginated-reports-customers.md)

> [!div class="nextstepaction"]
>[組織向けにページ分割されたレポートを埋め込む](embed-paginated-reports-organization.md)

>[!div class="nextstepaction"]
>[Power BI コミュニティに質問する](https://community.powerbi.com/)