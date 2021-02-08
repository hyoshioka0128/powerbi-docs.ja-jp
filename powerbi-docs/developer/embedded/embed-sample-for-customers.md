---
title: 顧客向けの埋め込み BI 分析情報を向上させるため、Power BI 埋め込み分析アプリケーションにコンテンツを埋め込む
description: Power BI 埋め込み分析サンプルにレポート、ダッシュボード、またはタイルを埋め込む方法について学習します。 Power BI 埋め込み分析を使用して、より優れた埋め込み BI インサイトを有効にします。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.topic: tutorial
ms.service: powerbi
ms.subservice: powerbi-developer
ms.custom: seodec18
ms.date: 12/22/2020
ms.openlocfilehash: 28081342763ca297648f67f953a29b46d02bf478
ms.sourcegitcommit: 2e81649476d5cb97701f779267be59e393460097
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/02/2021
ms.locfileid: "99494858"
---
# <a name="tutorial-embed-power-bi-content-using-a-sample-embed-for-your-customers-application"></a>チュートリアル:"*顧客向けの埋め込み*" サンプル アプリケーションを使用して Power BI コンテンツを埋め込む

**埋め込み分析** と **Power BI Embedded** (Azure プラン) を使用すると、レポート、ダッシュボードおよびタイルなどの Power BI コンテンツをアプリケーションに埋め込むことができます。

このチュートリアルでは、次の方法について説明します。

>[!div class="checklist"]
>* 埋め込み環境を設定する。
>* "*顧客向けの埋め込み*" ("*アプリ所有データ*" とも呼ばれます) サンプル アプリケーションを構成する。

アプリケーションを使用するために、ユーザーが Power BI にサインインしたり、Power BI ライセンスを持つ必要はありません。

独立ソフトウェア ベンダー (ISV) や開発者 (サード パーティ向けのアプリケーションを作成する必要がある) の場合は、"*顧客向けの埋め込み*" 方法を使用して Power BI コンテンツを埋め込むことをお勧めします。

## <a name="code-sample-specifications"></a>コード サンプルの仕様

このチュートリアルには、次のフレームワークのいずれかで "*顧客向けの埋め込み*" サンプル アプリケーションを構成する手順が含まれています。

* .NET Framework
* .NET Core
* Java
* Node JS
* Python

このコード サンプルでは次のブラウザーがサポートされています。

* Microsoft Edge
* Google Chrome
* Mozilla Firefox

## <a name="prerequisites"></a>前提条件

このチュートリアルを開始する前に、以下に一覧表示されている Power BI とコードの両方の依存関係があることを確認してください。

* **Power BI の依存関係**

    * 独自の [Azure Active Directory テナント](create-an-azure-active-directory-tenant.md)。

    * Power BI に対してアプリを認証するには、次のいずれかが必要です。

        * [サービス プリンシパル](embed-service-principal.md) - Azure Active Directory (Azure AD) の[サービス プリンシパル オブジェクト](/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object)。これを使用すると、Azure AD でアプリを認証できます。

        * [Power BI Pro](../../admin/service-admin-purchasing-power-bi-pro.md) ライセンス - これが **マスター ユーザー** になり、アプリでこれを使用して Power BI に対する認証を行います。

        * Power BI の [Premium Per User (PPU)](../../admin/service-premium-per-user-faq.md) ライセンス - これが **マスターユーザー** になり、アプリでこれを使用して Power BI に対する認証を行います。

    >[!NOTE]
    >[運用を開始する](move-to-production.md)には、[容量](embedded-capacity.md)が必要です。

* **コードの依存関係**

    # <a name="net-core"></a>[.NET Core](#tab/net-core)
    
    * [.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) (またはそれ以降)
    
    * 統合開発環境 (IDE)。 次のいずれかを使用することをお勧めします。
    
        * [Visual Studio](https://visualstudio.microsoft.com/)
    
        * [Visual Studio Code](https://code.visualstudio.com/)

    # <a name="net-framework"></a>[.NET Framework](#tab/net-framework)
    
    * [.NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/)
    
    * [Visual Studio](https://visualstudio.microsoft.com/)

    # <a name="java"></a>[Java](#tab/java)
    
    * [JDK (または JRE)](https://www.oracle.com/java/technologies/)
    
    * [Eclipse IDE](https://www.eclipse.org/downloads/packages/) - *Java EE 開発者向けの Eclipse* (Enterprise Edition) があることを確認します
    
    * [Apache Tomcat バイナリ ディストリビューション](https://tomcat.apache.org/)
    
    # <a name="node-js"></a>[Node JS](#tab/node-js)
    
    * [.NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/)
    
    * 統合開発環境 (IDE)。 次のいずれかを使用することをお勧めします。
    
        * [Visual Studio](https://visualstudio.microsoft.com/)
    
        * [Visual Studio Code](https://code.visualstudio.com/)
    
    # <a name="python"></a>[Python](#tab/python)
    
    * [Python 3](https://www.python.org/downloads/) (またはそれ以降)
    
        >[!NOTE]
        >* *Python* を初めてインストールする場合は、 **[Add Python to PATH]\(PATH に Python を追加\)** オプションを選択し、`PATH` 変数にインストールを追加します。
        >* 既に *Python* をインストールしている場合は、`PATH` 変数にそのインストール パスが含まれていることを確認します。 詳細については、「[Excursus:Setting environment variables](https://docs.python.org/3/using/windows.html#excursus-setting-environment-variables)」(補足: 環境変数の設定) という Python ドキュメント (このリンクは Python 3 に関するものです) を参照してください。
    
    * 統合開発環境 (IDE)。 次のいずれかを使用することをお勧めします。
    
        * [Visual Studio](https://visualstudio.microsoft.com/)
    
        * [Visual Studio Code](https://code.visualstudio.com/)
    
    ---

## <a name="method"></a>Method

"*顧客向けの埋め込み*" サンプル アプリを作成するには、これらの手順に従います。

1. [認証方法を選択します](#step-1---select-your-authentication-method)。

2. [Azure AD アプリケーションを登録します](#step-2---register-an-azure-ad-application)。

3. [Power BI ワークスペースを作成します](#step-3---create-a-power-bi-workspace)。

4. [Power BI レポートを作成して発行します](#step-4---create-and-publish-a-power-bi-report)。

5. [埋め込みパラメーター値を取得します](#step-5---get-the-embedding-parameter-values)。

6. [サービス プリンシパル API アクセス](#step-6---service-principal-api-access)
 
7. [ワークスペース アクセスを有効にします](#step-7---enable-workspace-access)。

8. [コンテンツを埋め込みます](#step-8---embed-your-content)。

## <a name="step-1---select-your-authentication-method"></a>手順 1 - 認証方法を選択する

埋め込みソリューションは、選択する認証方法によって異なります。 そのため、認証方法の違いを理解し、ソリューションに最適なものを決定することが重要です。

以下の表で、[サービス プリンシパル](embed-service-principal.md)と **マスター ユーザー** の認証方法のいくつかの主な違いについて説明します。

|考慮事項  |サービス プリンシパル  |マスター ユーザー  |
|---------|---------|---------|
|メカニズム     |Azure AD アプリの[サービス プリンシパル オブジェクト](/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object)を使用すると、Azure AD で Power BI に対して埋め込みソリューション アプリを認証できます。        |Azure AD アプリでは Power BI ユーザーの資格情報 (ユーザー名とパスワード) を使用して、Power BI に対して認証を行います。         |
|セキュリティ     |"*サービス プリンシパル*" は Azure AD で推奨される承認方法です。 サービス プリンシパルを使用する場合は、"*アプリケーション シークレット*" または "*証明書*" を使用して認証できます。</br></br>このチュートリアルでは、"*サービス プリンシパル*" と "*アプリケーション シークレット*" の使用についてのみ説明します。 "*サービス プリンシパル*" と "*証明書*" を使用して埋め込む場合は、[サービス プリンシパルと証明書](embed-service-principal-certificate.md)に関する記事を参照してください。         |この認証方法は、"*サービス プリンシパル*" を使用する場合と同じように安全とは見なされません。 これは、"*マスター ユーザー*" の資格情報 (ユーザー名とパスワード) に注意する必要があるためです。 たとえば、それらは埋め込みアプリケーションで公開できず、パスワードを頻繁に変更する必要があります。         |
|Azure AD のデリゲートされたアクセス許可 |必要なし。 |"*マスター ユーザー*" または管理者は、アプリから Power BI REST API への [アクセス許可](/azure/active-directory/develop/v2-permissions-and-consent) (スコープとも呼ばれます) に対する同意を付与する必要があります。 たとえば、*Report.ReadWrite.All* です。 |
|Power BI サービスへのアクセス |"*サービス プリンシパル*" を使用して、Power BI サービスにアクセスすることはできません。|Power BI サービスには、"*マスター ユーザー*" の資格情報を使用してアクセスできます。|
|ライセンス     |Pro ライセンスは必要ありません。 ご自分がメンバーまたは管理者であるすべてのワークスペースのコンテンツを使用できます。         |[Power BI Pro ライセンス](../../admin/service-admin-purchasing-power-bi-pro.md)が必要です。         |

## <a name="step-2---register-an-azure-ad-application"></a>手順 2 - Azure AD アプリケーションを登録する

Azure AD にアプリケーションを登録すると、次のことが可能になります。
> [!div class="checklist"]
>* アプリの ID を確立する
>* アプリから [Power BI REST API](/rest/api/power-bi/) にアクセスできるようにする
>* "*マスター ユーザー*" を使用する場合 - アプリの [Power BI REST アクセス許可](/azure/active-directory/develop/v2-permissions-and-consent)を指定します

[!INCLUDE[Register Azure AD app](../../includes/embed-tutorial-register-app.md)]

>[!NOTE]
>アプリケーションを登録する前に、使用する認証方法 ("*サービス プリンシパル*" または "*マスター ユーザー*") を決定する必要があります。

## <a name="step-3---create-a-power-bi-workspace"></a>手順 3 - Power BI ワークスペースを作成する

[!INCLUDE[Create a Power BI workspace](../../includes/embed-tutorial-create-workspace.md)]

## <a name="step-4---create-and-publish-a-power-bi-report"></a>手順 4 - Power BI レポートを作成して発行する

[!INCLUDE[Create a Power BI report](../../includes/embed-tutorial-create-report.md)]

## <a name="step-5---get-the-embedding-parameter-values"></a>手順 5 - 埋め込みパラメーター値を取得する

コンテンツを埋め込むには、特定のパラメーター値を取得する必要があります。 以下の表には必須の値が表示されており、"*サービス プリンシパル*" 認証方法、"*マスター ユーザー*" 認証方法、あるいはその両方に適用できるかどうかが示されています。

コンテンツを埋め込む前に、以下に一覧表示されているすべての値があることを確認してください。 一部の値は、使用する認証方法によって異なります。

|パラメーター   |サービス プリンシパル   |マスター ユーザー  |
|-------------------|---|---|
|[クライアント ID](#client-id) |![適用対象:](../../media/yes.png) |![適用対象:](../../media/yes.png) |
|[ワークスペース ID](#workspace-id)     |![適用対象:](../../media/yes.png) |![適用対象:](../../media/yes.png) |
|[レポート ID](#report-id)           |![適用対象:](../../media/yes.png) |![適用対象:](../../media/yes.png) |
|[クライアント シークレット](#client-secret) |![適用対象:](../../media/yes.png) |![適用対象外](../../media/no.png) |
|[テナント ID](#tenant-id)                 |![適用対象:](../../media/yes.png) |![適用対象外](../../media/no.png) |
|[Power BI ユーザー名](#power-bi-username-and-password)   |![適用対象外](../../media/no.png) |![適用対象:](../../media/yes.png) |
|[Power BI パスワード](#power-bi-username-and-password)   |![適用対象外](../../media/no.png) |![適用対象:](../../media/yes.png) |

### <a name="client-id"></a>クライアント ID

>[!TIP]
>**適用対象:** ![適用対象 ](../../media/yes.png)サービス プリンシパル ![適用対象 ](../../media/yes.png)マスター ユーザー

[!INCLUDE[Get the client ID](../../includes/embed-tutorial-client-id.md)]

### <a name="workspace-id"></a>ワークスペース ID

>[!TIP]
>**適用対象:** ![適用対象 ](../../media/yes.png)サービス プリンシパル ![適用対象 ](../../media/yes.png)マスター ユーザー

[!INCLUDE[Get the workspace ID](../../includes/embed-tutorial-workspace-id.md)]

### <a name="report-id"></a>レポート ID

>[!TIP]
>**適用対象:** ![適用対象 ](../../media/yes.png)サービス プリンシパル ![適用対象 ](../../media/yes.png)マスター ユーザー

[!INCLUDE[Get the report ID](../../includes/embed-tutorial-report-id.md)]

### <a name="client-secret"></a>クライアント シークレット

>[!TIP]
>**適用対象:** ![適用対象 ](../../media/yes.png)サービス プリンシパル ![適用対象外 ](../../media/no.png)マスター ユーザー

[!INCLUDE[Get the client secret](../../includes/embed-tutorial-client-secret.md)]

### <a name="tenant-id"></a>テナント ID

>[!TIP]
>**適用対象:** ![適用対象 ](../../media/yes.png)サービス プリンシパル ![適用対象外 ](../../media/no.png)マスター ユーザー

テナント ID GUID を取得するには、これらの手順に従います。

1. [Microsoft Azure](https://ms.portal.azure.com/#allservices) にログインします。

2. **[アプリの登録]** を検索し、 **[アプリの登録]** リンクを選択します。

3. Power BI コンテンツを埋め込むために使用する Azure AD アプリを選択します。

4. **[概要]** セクションで、 **[ディレクトリ (テナント) ID]** の GUID をコピーします。

### <a name="power-bi-username-and-password"></a>Power BI のユーザー名とパスワード

>[!TIP]
>**適用対象:** ![適用対象外 ](../../media/no.png) サービス プリンシパル ![適用対象 ](../../media/yes.png)マスター ユーザー

**マスター ユーザー** として使用する Power BI ユーザーの "*ユーザー名*" と "*パスワード*" を取得します。 これは、Power BI サービスで、ワークスペースを作成してレポートをアップロードするために使用したものと同じユーザーです。

## <a name="step-6---service-principal-api-access"></a>手順 6 - サービス プリンシパル API アクセス

>[!TIP]
>**適用対象:** ![適用対象 ](../../media/yes.png)サービス プリンシパル ![適用対象外 ](../../media/no.png)マスター ユーザー
>
>この手順は、"*サービス プリンシパル*" 認証方法を使用する場合にのみ関連します。 "*マスター ユーザー*" を使用する場合は、この手順を省略し、「[手順 7 - ワークスペース アクセスを有効にする](#step-7---enable-workspace-access)」に進んでください。

Azure AD アプリから Power BI コンテンツおよび API にアクセスできるようにするには、Power BI 管理者が Power BI 管理ポータルでサービス プリンシパル アクセスを有効にする必要があります。 テナントの管理者でない場合は、テナントの管理者に連絡し、 *[テナント設定]* を有効にしてもらってください。
        
1. "*Power BI サービス*" で、 **[設定]**  >  **[設定]**  >  **[管理ポータル]** の順に選択します。
        
    :::image type="content" source="media/embed-sample-for-customers/admin-settings.png" alt-text="Power BI サービスの [設定] メニューの管理設定メニュー オプションを示すスクリーンショット":::
        
2. **[テナント設定]** を選択してから、 **[開発者の設定]** セクションまで下にスクロールします。
        
3. **[Power BI API の使用をサービス プリンシパルに許可]** を展開し、このオプションを有効にします。
        
    :::image type="content" source="media/embed-sample-for-customers/developer-settings.png" alt-text="Power BI サービスで、[テナント設定] メニュー オプションの [開発者の設定] オプションを有効にする方法を示すスクリーンショット":::
        
>[!NOTE]
>"*サービス プリンシパル*" を使用する場合は、"*セキュリティ グループ*" を使用してテナント設定へのアクセスを制限することをお勧めします。 この機能の詳細については、[サービス プリンシパル](embed-service-principal.md)に関する記事のこれらのセクションを参照してください。
> * [Azure AD セキュリティ グループを作成する](embed-service-principal.md#step-2---create-an-azure-ad-security-group)
>* [Power BI サービス管理者設定を有効にする](embed-service-principal.md#step-3---enable-the-power-bi-service-admin-settings)

## <a name="step-7---enable-workspace-access"></a>手順 7 - ワークスペース アクセスを有効にする

Power BI サービスでレポート、ダッシュボードおよびデータセットなどの Azure AD アプリのアクセス成果物を有効にするには、"*サービス プリンシパル*" または "*マスター ユーザー*" を "*メンバー*" または "*管理者*" としてご利用のワークスペースに追加します。

1. Power BI サービスにサインインします。

2. アクセスを有効にするワークスペースまでスクロールし、 **[その他]** メニューで、 **[ワークスペース アクセス]** を選択します。

    :::image type="content" source="media/embed-service-principal/workspace-access.png" alt-text="Power BI ワークスペースの [その他] メニューのワークスペース アクセス ボタンを示すスクリーンショット。":::

3. **[アクセス]** ペインで、使用する認証方法に応じて、"*サービス プリンシパル*" または "*マスター ユーザー*" を **[メール アドレスの入力]** テキスト ボックスにコピーします。

    >[!NOTE]
    >"*サービス プリンシパル*" を使用する場合、その名前は Azure AD アプリに指定した名前になります。

4. **[追加]** を選択します。

## <a name="step-8---embed-your-content"></a>手順 8 - コンテンツを埋め込む

Power BI の埋め込みサンプル アプリケーションを使用すると、Power BI の "*顧客向けの埋め込み*" アプリを作成できます。

Power BI レポートを埋め込むには、これらの手順に従って、"*顧客向けの埋め込み*" サンプル アプリケーションを変更します。  

[!INCLUDE[Embedding steps](../../includes/embed-tutorial-embedding-steps.md)]

4. アプリケーションで使用する言語に応じて、次のいずれかのフォルダーを開きます。

    * .NET Core
    * .NET Framework
    * Java
    * Node JS
    * Python

    >[!NOTE]
    >"*顧客向けの埋め込み*" サンプル アプリケーションでサポートされるのは、上記の一覧にあるフレームワークのみです。 *React* サンプル アプリケーションでサポートされるのは、" *[組織向けの埋め込み](embed-sample-for-your-organization.md)* " ソリューションのみです。

5. **顧客向けの埋め込み** フォルダーを開きます。

# <a name="net-core"></a>[.NET Core](#tab/net-core)

6. これらのいずれかの方法を使用して、"*顧客向けの埋め込みサンプル アプリ*" を開きます。

    * [Visual Studio](https://visualstudio.microsoft.com/) を使用する場合は、**AppOwnsData.sln** ファイルを開きます。

    * [Visual Studio Code](https://code.visualstudio.com/) を使用する場合は、**AppOwnsData** フォルダーを開きます。

7. **appsettings.json** を開きます。

8. 認証方法に応じて、次のパラメーター値を入力します。

    |パラメーター            |サービス プリンシパル  |マスター ユーザー  |
    |---------------------|---------|---------|
    |`AuthenticationMode` |ServicePrincipal         |MasterUser         |
    |`ClientId`           |Azure AD アプリの[クライアント ID](#client-id)         |Azure AD アプリの[クライアント ID](#client-id)         |
    |`TenantId`           |Azure AD の[テナント ID](#tenant-id)         |該当なし         |
    |`PbiUsername`        |該当なし         |"*マスター ユーザー*" のユーザー名 (「[Power BI のユーザー名とパスワード](#power-bi-username-and-password)」を参照)         |
    |`PbiPassword`        |該当なし         |"*マスター ユーザー*" のパスワード (「[Power BI のユーザー名とパスワード](#power-bi-username-and-password)」を参照)         |
    |`ClientSecret`       |Azure AD の[クライアント シークレット](#client-secret)         |該当なし         |
    |`WorkspaceId`        |埋め込みレポートがあるワークスペースの ID (「[ワークスペース ID](#workspace-id)」を参照)          |埋め込みレポートがあるワークスペースの ID (「[ワークスペース ID](#workspace-id)」を参照)         |
    |`ReportId`           |埋め込むレポートの ID (「[レポート ID](#report-id)」を参照)            |埋め込むレポートの ID (「[レポート ID](#report-id)」を参照)         |

9. 適切なオプションを選択してプロジェクトを実行します。

    * **Visual Studio** を使用する場合は、 **[IIS Express]** (再生) を選択します。

    * **Visual Studio Code** を使用する場合は、 **[実行]、[デバッグの開始]** の順に選択します。

# <a name="net-framework"></a>[.NET Framework](#tab/net-framework)

6. [Visual Studio](https://visualstudio.microsoft.com/) を使用して、**AppOwnsData.sln** ファイルを開きます。

7. **Web.config** を開きます。

8. 認証方法に応じて、次のパラメーター値を入力します。

    |パラメーター            |サービス プリンシパル  |マスター ユーザー  |
    |---------------------|---------|---------|
    |`authenticationType` |ServicePrincipal         |MasterUser         |
    |`applicationId`           |Azure AD アプリの[クライアント ID](#client-id)         |Azure AD アプリの[クライアント ID](#client-id)         |
    |`workspaceId`        |埋め込みレポートがあるワークスペースの ID (「[ワークスペース ID](#workspace-id)」を参照)          |埋め込みレポートがあるワークスペースの ID (「[ワークスペース ID](#workspace-id)」を参照)         |
    |`reportId`           |埋め込むレポートの ID (「[レポート ID](#report-id)」を参照)            |埋め込むレポートの ID (「[レポート ID](#report-id)」を参照)         |
    |`pbiUsername`        |該当なし         |"*マスター ユーザー*" のユーザー名 (「[Power BI のユーザー名とパスワード](#power-bi-username-and-password)」を参照)         |
    |`pbiPassword`        |該当なし         |"*マスター ユーザー*" のパスワード (「[Power BI のユーザー名とパスワード](#power-bi-username-and-password)」を参照)         |
    |`applicationSecret`       |Azure AD の[クライアント シークレット](#client-secret)         |該当なし         |
    |`tenant`           |Azure AD の[テナント ID](#tenant-id)         |該当なし         |

9. **[IIS Express]** (再生) を選択して、プロジェクトを実行します。

# <a name="java"></a>[Java](#tab/java)

6. **Eclipse** を開き、以下で説明されている手順に従います。

    >[!NOTE]
    >Java の *顧客向けの埋め込みサンプル アプリ* の手順については、[Java EE 開発者向け Eclipse IDE](https://www.eclipse.org/downloads/packages/) (Enterprise Edition) に関するページを参照してください。 別のアプリケーションを使用する場合は、ご自分で設定する必要があります。

7. Tomcat サーバーを Eclipse に追加します。

    a. **[Window]\(ウィンドウ\)**  >  **[Show View]\(ビューの表示\)**  >  **[Servers]\(サーバー\)** の順に選択します。

    b. [Servers]\(サーバー\) タブで、 **[No servers are available.Click this link to create new server]\(使用可能なサーバーがありません。このリンクをクリックして新規サーバーを作成してください\)** を選択します。

    c. **[Define a New Server]\(新規サーバーの定義\)** ウィンドウで、 **[Apache]** を展開し、コンピューター上で実行する Tomcat サーバーを選択します。 たとえば、 *[Tomcat v9.0 Server]\(Tomcat v9.0 サーバー\)* です。

    d. **[次へ]** を選択します。

    e. **[Tomcat Server]\(Tomcat サーバー\)** ウィンドウで、 **[参照]** を選択し、Tomcat サーバーが格納されているフォルダーに移動します。

    f. **[Tomcat Server]\(Tomcat サーバー\)** ウィンドウで、 **[Installed JREs]\(インストール済みの JRE\)** を選択します。

    g. **[Installed JREs]\(インストール済みの JRE\)** ウィンドウで、使用可能な *jre* を選び、 **[Apply and Close]\(適用して閉じる\)** を選択します。

    h. **[Tomcat Server]\(Tomcat サーバー\)** ウィンドウで、 **[完了]** を選択します。 *[Servers]\(サーバー\)* タブで Tomcat サーバーを確認することができます。

8. Eclipse でプロジェクトを開きます。

    >[!IMPORTANT]
    >パス名が長すぎる場合、Eclipse で問題が発生する可能性があります。 この問題を回避するには、コンピューターのフォルダー構造内のサンプル アプリのフォルダーの入れ子のレベルが深すぎないかを確認します。

    a. **[ファイル]** を選択し、 **[Open Projects from File System]\(ファイル システムからプロジェクトを開く\)** を選びます。

    b. **[Import Projects form File System or Archive]\(ファイル システムまたはアーカイブからプロジェクトをインポート\)** ウィンドウで、 **[Directory]\(ディレクトリ\)** を選択し、**AppOwnsData** フォルダーを開きます。

    c. **[完了]** を選択します。

9. Tomcat サーバーをプロジェクトに追加します。

    a. **[Package Explorer]\(パッケージ エクスプローラー\)** ペインで、 **[AppOwnsData]** を右クリックし、 **[プロパティ]** を選択します。

    b. **AppOwnesData の [プロパティ]** ウィンドウで、 **[Targeted Runtimes]\(ターゲット ランタイム\)** を選択してから **[Apache Tomcat]** を選びます。 この選択には、使用する *Apache Tomcat* のバージョン (*Apache Tomcat v9.0* など) が含まれます。

    c. **[Apply and Close]\(適用して閉じる\)** を選択します。

10. 必須パラメーターを入力します

    a. **[Package Explorer]\(パッケージ エクスプローラー\)** で、 **[AppOwnsData]** プロジェクトを展開します。

    b. **[Java Resources]\(Java リソース\)** を展開します。

    c. **[src]** を展開します。

    d. **[com.embedsample.appoensdata.config]** を展開します。

    e. **Config.java** を開きます。

    f. 認証方法に応じて、次のパラメーター値を入力します。

    |パラメーター            |サービス プリンシパル  |マスター ユーザー  |
    |---------------------|---------|---------|
    |`authenticationType` |ServicePrincipal         |MasterUser         |
    |`workspaceId`        |埋め込みレポートがあるワークスペースの ID (「[ワークスペース ID](#workspace-id)」を参照)          |埋め込みレポートがあるワークスペースの ID (「[ワークスペース ID](#workspace-id)」を参照)         |
    |`reportId`           |埋め込むレポートの ID (「[レポート ID](#report-id)」を参照)            |埋め込むレポートの ID (「[レポート ID](#report-id)」を参照)         | 
    |`clientId`           |Azure AD アプリの[クライアント ID](#client-id)         |Azure AD アプリの[クライアント ID](#client-id)         |
    |`pbiUsername`        |該当なし         |"*マスター ユーザー*" のユーザー名 (「[Power BI のユーザー名とパスワード](#power-bi-username-and-password)」を参照)         |
    |`pbiPassword`        |該当なし         |"*マスター ユーザー*" のパスワード (「[Power BI のユーザー名とパスワード](#power-bi-username-and-password)」を参照)         |
    |`tenantId`           |Azure AD の[テナント ID](#tenant-id)         |該当なし         |
    |`appSecret`       |Azure AD の[クライアント シークレット](#client-secret)         |該当なし         |

11. プロジェクトを実行する

    a. **[Package Explorer]\(パッケージ エクスプローラー\)** で、 **[AppOwnesData]** を右クリックします。

    b. **[Run As]\(別のユーザーとして実行\)**   >  **[Run on Server]\(サーバーで実行\)** の順に選択します。

    c. **[Run on Server]\(サーバーで実行\)** ウィンドウで、 **[Choose an existing server]\(既存のサーバーを選択\)** を選択し、*Tomcat* サーバーを選びます。

    d. **[完了]** を選択します。

# <a name="node-js"></a>[Node JS](#tab/node-js)

6. お好きな IDE を使用して、**アプリ所有データ** フォルダーを開きます。 次のいずれかを使用することをお勧めします。

    * [Visual Studio](https://visualstudio.microsoft.com/)

    * [Visual Studio Code](https://code.visualstudio.com/)

7. ターミナルを開き、`npm install` を実行して、必要な依存関係をインストールします。

8. **Config** フォルダーを展開し、**config.json** を開きます。

9. 認証方法に応じて、次のパラメーター値を入力します。

    |パラメーター            |サービス プリンシパル  |マスター ユーザー  |
    |---------------------|---------|---------|
    |`authenticationMode` |ServicePrincipal         |MasterUser         |
    |`clientId`           |Azure AD アプリの[クライアント ID](#client-id)         |Azure AD アプリの[クライアント ID](#client-id)         |
    |`workspaceId`        |埋め込みレポートがあるワークスペースの ID (「[ワークスペース ID](#workspace-id)」を参照)          |埋め込みレポートがあるワークスペースの ID (「[ワークスペース ID](#workspace-id)」を参照)         |
    |`reportId`           |埋め込むレポートの ID (「[レポート ID](#report-id)」を参照)            |埋め込むレポートの ID (「[レポート ID](#report-id)」を参照)         |
    |`pbiUsername`        |該当なし         |"*マスター ユーザー*" のユーザー名 (「[Power BI のユーザー名とパスワード](#power-bi-username-and-password)」を参照)         |
    |`pbiPassword`        |該当なし         |"*マスター ユーザー*" のパスワード (「[Power BI のユーザー名とパスワード](#power-bi-username-and-password)」を参照)         |
    |`clientSecret`       |Azure AD の[クライアント シークレット](#client-secret)         |該当なし         |
    |`tenantId`           |Azure AD の[テナント ID](#tenant-id)         |該当なし         |

10. 次のようにして、プロジェクトを実行します。

    a. IDE ターミナルで、`npm start` を実行します。

    b. ブラウザーで新しいタブを開き、`http://localhost:5300` に移動します。

# <a name="python"></a>[Python](#tab/python)

6. **PowerShell** または **コマンド プロンプト** を開きます。

7. **Python** > **顧客向けの埋め込み** フォルダーの順に移動しており、そのフォルダー内に **requirements.txt** というファイルがあることを確認して、`pip3 install -r requirements.txt` を実行します。

8. お好きな IDE を使用して、**アプリ所有データ** フォルダーを開きます。 次のいずれかを使用することをお勧めします。

    * [Visual Studio](https://visualstudio.microsoft.com/)

    * [Visual Studio Code](https://code.visualstudio.com/)

9. **config.py** を開きます。

10. 認証方法に応じて、次のパラメーター値を入力します。

    |パラメーター            |サービス プリンシパル  |マスター ユーザー  |
    |---------------------|---------|---------|
    |`AUTHENTICATION_MODE` |ServicePrincipal         |MasterUser         |
    |`WORKSPACE_ID`        |埋め込みレポートがあるワークスペースの ID (「[ワークスペース ID](#workspace-id)」を参照)          |埋め込みレポートがあるワークスペースの ID (「[ワークスペース ID](#workspace-id)」を参照)         |
    |`REPORT_ID`           |埋め込むレポートの ID (「[レポート ID](#report-id)」を参照)            |埋め込むレポートの ID (「[レポート ID](#report-id)」を参照)         |
    |`TENANT_ID`           |Azure AD の[テナント ID](#tenant-id)         |該当なし         |
    |`CLIENT_ID`           |Azure AD アプリの[クライアント ID](#client-id)         |Azure AD アプリの[クライアント ID](#client-id)         |
    |`CLIENT_SECRET`       |Azure AD の[クライアント シークレット](#client-secret)         |該当なし         |
    |`POWER_BI_USER`        |該当なし         |"*マスター ユーザー*" のユーザー名 (「[Power BI のユーザー名とパスワード](#power-bi-username-and-password)」を参照)         |
    |`POWER_BI_PASS`        |該当なし         |"*マスター ユーザー*" のパスワード (「[Power BI のユーザー名とパスワード](#power-bi-username-and-password)」を参照)         |

11. ファイルを保存します。

12. 次のようにして、プロジェクトを実行します。

    a. **PowerShell** または **コマンド プロンプト** で、**Python** > **顧客向けの埋め込み** > **AppOwnesData** フォルダーの順に移動し、`flask run` を実行します。

    b. ブラウザーで新しいタブを開き、`http://localhost:5300` に移動します。

---

## <a name="developing-your-application"></a>アプリケーションの開発

"*顧客向けの埋め込み*" サンプル アプリケーションを構成して実行した後、独自のアプリケーションの開発を開始できます。

[!INCLUDE[Move to production](../../includes/embed-tutorial-production.md)]

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
>[運用環境への移行](move-to-production.md)

>[!div class="nextstepaction"]
>[組織向けの埋め込み](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
>[顧客向けにページ分割されたレポートを埋め込む](embed-paginated-reports-customers.md)

> [!div class="nextstepaction"]
>[組織向けにページ分割されたレポートを埋め込む](embed-paginated-reports-organization.md)

>[!div class="nextstepaction"]
>[Power BI コミュニティに質問する](https://community.powerbi.com/)