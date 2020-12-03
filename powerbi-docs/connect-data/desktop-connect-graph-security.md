---
title: Power BI Desktop の Microsoft Graph Security API に接続する
description: Power BI Desktop の Microsoft Graph Security API に簡単に接続する
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.custom: seojan19
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: conceptual
ms.date: 01/29/2019
LocalizationGroup: Connect to data
ms.openlocfilehash: b3aa9be7be6e2769367cd3337b78030d52bde0c7
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411427"
---
# <a name="connect-to-the-microsoft-graph-security-api-in-power-bi-desktop"></a>Power BI Desktop の Microsoft Graph Security API に接続する

Power BI Desktop の Microsoft Graph Security コネクタを使用して、[Microsoft Graph Security API](/graph/security-concept-overview) に接続します。 次に、ダッシュボードとレポートを構築することで、ご自分のセキュリティ関連の[アラート](/graph/api/resources/alert)および[セキュリティ スコア](/graph/api/resources/securescores)に対する分析情報を得ることができます。

Microsoft Graph Security API と、Microsoft およびそのパートナーからの[複数のセキュリティ ソリューション](/graph/api/resources/security-api-overview#alerts)とが接続されることで、アラートの関連付けが容易になります。 この組み合わせによって、豊富なコンテキスト情報にアクセスできるようになり、自動化が簡略化されます。 これにより、組織はコストの削減および複雑さの軽減を実施しながら、迅速に複数のセキュリティ製品にわたって分析情報を取得し活動することができます。

## <a name="prerequisites-to-use-the-microsoft-graph-security-connector"></a>Microsoft Graph Security コネクタを使用するための前提条件

Microsoft Graph Security コネクタを使用するには、Azure Active Directory (Azure AD) のグローバル管理者の同意を "*明示的に*" 取得する必要があります。 [Microsoft Graph Security 認証要件](/graph/security-authorization)に関するページを参照してください。
同意には、コネクタのアプリケーション ID と名前が必要です。それは次に示すようなものであり、[Azure portal](https://portal.azure.com) で確認できます。

| プロパティ | 値 |
|----------|-------|
| **アプリケーション名** | `MicrosoftGraphSecurityPowerBIConnector` |
| **アプリケーション ID** | `cab163b7-247d-4cb9-be32-39b6056d4189` |
| **リダイレクト URI** | `https://oauth.powerbi.com/views/oauthredirect.html` |
|||

コネクタに対して同意を付与するために、Azure AD グローバル管理者は、次のいずれかの方法を使用することができます。

* [Azure AD アプリケーションに対して同意を付与する](/azure/active-directory/develop/v2-permissions-and-consent)

* ご利用のロジック アプリが初めて実行されたときに[アプリケーション同意エクスペリエンス](/azure/active-directory/develop/application-consent-experience)を介して送信した要求に応答する
   
Microsoft Graph Security コネクタにサインインするユーザーが "*セキュリティ管理者*" ロールのメンバーでない **場合** は、そのアカウントに Azure AD Security 閲覧者ロールを割り当てる必要があります。 「[Assign Azure AD roles to users](/graph/security-authorization#assign-azure-ad-roles-to-users)」(Azure AD のロールをユーザーに割り当てる) を参照してください。

## <a name="using-the-microsoft-graph-security-connector"></a>Microsoft Graph Security コネクタを使用する

コネクタを使用するには、以下の手順に従ってください。

1. Power BI Desktop の **[ホーム]** リボンから **[データを取得]**  >  **[詳細]** の順に選択します。
2. ウィンドウの左側のカテゴリ リストから **[オンライン サービス]** を選択します。
3. **[Microsoft Graph Security (ベータ)]** を選択します。

    ![[データの取得] ダイアログ ボックス](media/desktop-connect-graph-security/GetData.PNG)
    
4. **[Microsoft Graph Security]** ウィンドウで、クエリを実行する Microsoft Graph API バージョンを選択します: **v1.0** または **ベータ**。

    ![[バージョンの選択] ダイアログ ボックス](media/desktop-connect-graph-security/selectVersion.PNG)
    
5. Azure Active Directory アカウントにサインインするように求められたら、サインインします。 このアカウントでは、前のセクションで述べたように *セキュリティ閲覧者* ロールまたは *セキュリティ管理者* ロールを用意する必要があります。

    ![サインイン](media/desktop-connect-graph-security/SignIn.PNG) 
    
6. あなたが管理者であり、"*かつ*" Microsoft Graph Security Power BI コネクタ (アプリケーション) にまだ同意していない場合、次のダイアログ ボックスが表示されます。 **[組織の代理として同意する]** を選択します。

    ![[管理者の同意] ダイアログ ボックス](media/desktop-connect-graph-security/AdminConsent.PNG)
    
7. サインインすると、認証されたことを示す次のダイアログ ボックスが表示されます。 **[接続]** を選択します。

    ![[現在、サインインしています] ダイアログ ボックス](media/desktop-connect-graph-security/SignedIn.PNG)
    
8. 接続すると、アラートやセキュリティ スコアなど、手順 4 で選択したバージョンの [Microsoft Graph Security API](/graph/security-concept-overview) で使用できるエンティティが **[ナビゲーター]** ウィンドウに表示されます。 Power BI Desktop にインポートして使用するエンティティを 1 つまたは複数選択します。 次に、 **[読み込む]** を選択して、手順 9 の後に表示される結果ビューを取得します。

    ![[ナビゲーター] ダイアログ ボックス](media/desktop-connect-graph-security/NavTable.PNG)
    
9. Microsoft Graph Security API で高度なクエリを使用する場合は、 **[Specify custom Microsoft Graph Security URL to filter results]\(カスタム Microsoft Graph Security URL を指定して結果を絞り込む\)** を選択します。 この機能を使用して、必須のアクセス許可を持つ Microsoft Graph Security API に対して [OData.Feed](./desktop-connect-odata.md) クエリを発行します。

   次の例では、`https://graph.microsoft.com/v1.0/security/alerts?$filter=Severity eq 'High'` *serviceUri* が使用されています。 クエリを作成してフィルター処理、並べ替え、または最近の結果の取得を行う方法を確認するには、[OData システム クエリ オプション](/graph/query-parameters)に関するページを参照してください。

   ![OdataFeed の例](media/desktop-connect-graph-security/ODataFeed.PNG)
    
   **[呼び出し]** を選択すると、**OData.Feed** 関数によって API が呼び出され、クエリ エディターが開きます。 使用するデータ セットをフィルター処理して絞り込みます。 次に、そのデータを Power BI Desktop に読み込みます。

ここで、クエリした Microsoft Graph Security エンティティの結果ウィンドウを示します。

   ![結果ウィンドウの例](media/desktop-connect-graph-security/Result.PNG)
    

これで、Microsoft Graph Security コネクタからインポートしたデータを Power BI Desktop で使用する準備ができました。 グラフィックスまたはレポートを作成することができます。 あるいは、Excel ブック、データベース、またはその他のデータ ソースからインポートした他のデータを操作することもできます。

## <a name="next-steps"></a>次のステップ
* このコネクタを使用する Power BI のサンプルやテンプレートについては、「[Microsoft Graph Security GitHub Power BI samples](https://aka.ms/graphsecuritypowerbiconnectorsamples)」 (Microsoft Graph Security GitHub Power BI のサンプル) を参照してください。

* ユーザー シナリオや追加情報については、[Microsoft Graph Security Power BI コネクタに関するブログ記事](https://aka.ms/graphsecuritypowerbiconnectorblogpost)を参照してください。

* Power BI Desktop を使用することで、あらゆる種類のデータに接続することができます。 詳細については、次のリソースをご覧ください。

    * [Power BI Desktop とは何ですか?](../fundamentals/desktop-what-is-desktop.md)
    * [Power BI Desktop のデータ ソース](desktop-data-sources.md)
    * [Power BI Desktop でのデータの整形と結合](desktop-shape-and-combine-data.md)
    * [Power BI Desktop で Excel ブックに接続する](desktop-connect-excel.md)
    * [Power BI Desktop にデータを直接入力する](desktop-enter-data-directly-into-desktop.md)