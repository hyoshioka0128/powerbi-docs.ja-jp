---
title: Power BI アプリケーションを埋め込むために必要なアクセス許可トークンについて理解する
description: Power BI アプリケーションで Azure と Power BI サービスに対して認証を行うために必要なトークンについて説明します。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: amshuste
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/17/2021
ms.openlocfilehash: 4fd45adeabde402472b97cecce3475d8a6a490cc
ms.sourcegitcommit: cf3469295a33acf729a913ec135b4c5484910d2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2021
ms.locfileid: "102194827"
---
# <a name="embedded-analytics-application-tokens"></a>埋め込み分析アプリケーション トークン

Power BI のコンテンツを使用するには、アクセス トークンが必要です。 ソリューションに応じて、[Azure AD トークン](#azure-ad-token)または[埋め込みトークン](#embed-token)のいずれかをこのトークンに使用できます。

"*顧客向け埋め込み*" ソリューションを使用している場合、Web アプリのユーザーには、アプリケーションによって生成された "*埋め込みトークン*" に従って Power BI コンテンツ (レポート、ダッシュボード、タイルなど) へのアクセス権が付与されます。

>[!NOTE]
>"*顧客向け埋め込み*" ソリューションを使用する場合は、任意の認証方法を使用して、Web アプリへのアクセスを許可できます。

"*組織向け埋め込みソリューション*" を使用している場合は、Web アプリのユーザーは独自の資格情報を使用して Azure AD に対する認証を行います。 アプリのユーザーは、Power BI サービスでアクセスできる Power BI コンテンツにアクセスできます。

## <a name="azure-ad-token"></a>Azure AD トークン

"*顧客向け埋め込み*" と "*組織向け埋め込み*" のどちらのソリューションについても、[Azure AD トークン](/azure/databricks/dev-tools/api/latest/aad/)が必要です。 このトークンは、すべての [REST API](/rest/api/power-bi/) 操作に必要であり、1 時間後に有効期限が切れます。

* "*顧客向け埋め込み*" では、Azure AD トークンは "*埋め込みトークン*" を生成するために使用されます。

* "*組織向け埋め込み*" では、Azure AD トークンは Power BI にアクセスするために使用されます。

## <a name="embed-token"></a>埋め込みトークン

"*顧客向け埋め込み*" ソリューションを使用している場合は、ユーザーがアクセスできる Power BI コンテンツを Web アプリで認識する必要があります。 [埋め込みトークン](/rest/api/power-bi/embedtoken) REST API を使用して "*埋め込みトークン*" を生成し、そこでは次のものを指定します。

* Web アプリ ユーザーがアクセスできるコンテンツ。

* Web アプリ ユーザーのアクセス レベル (表示、作成、または編集)。

詳細については、「[埋め込みトークンを生成するときの考慮事項](generate-embed-token.md)」を参照してください。

## <a name="authentication-flows"></a>認証フロー

ここでは、"*顧客向け埋め込み*" と "*組織向け埋め込み*" の埋め込みソリューションの認証フローについて説明します。

### <a name="embed-for-your-customers"></a>顧客向けに埋め込む

"*顧客向け埋め込み*" ソリューションには、非対話型の認証フローが使用されます。 ユーザーは、Power BI にアクセスするために Azure AD にサインインする必要はありません。 代わりに、Web アプリで専用の Azure AD ID を使用して Azure AD に対する認証を行い、"*埋め込みトークン*" を生成します。 専用 ID には、次のいずれかを使用できます。

* **[サービス プリンシパル](embed-service-principal.md)**

    Web アプリで Azure AD の [サービス プリンシパル オブジェクト](/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object)を使用して Azure AD に対する認証を行い、"*アプリ専用の Azure AD トークン*" を取得します。 これは "*アプリ専用*" の認証方法であり、Azure AD によって推奨されます。

    "*サービス プリンシパル*" を使用する場合は、Power BI サービスの "*管理者*" の設定で、[Power BI API のアクセスを有効にする](embed-sample-for-customers.md#step-6---service-principal-api-access)必要があります。 これにより、Web アプリで Power BI REST API にアクセスできるようになります。 ワークスペースで API 操作を使用するには、"*サービス プリンシパル*" がワークスペースの "*メンバー*" または "*管理者*" である必要があります。

* **マスター ユーザー**

    Web アプリで、ユーザー アカウントを使用して Azure AD に対する認証を行い、"*Azure AD トークン*" を取得します。 "*マスター ユーザー*" は、[Power BI Pro](../../admin/service-admin-purchasing-power-bi-pro.md) または [Premium Per User (PPU)](../../admin/service-premium-per-user-faq.md) のライセンスを持っている必要があります。

    "*マスター ユーザー*" を使用する場合は、アプリの [委任されたアクセス許可](/azure/active-directory/develop/v2-permissions-and-consent) (スコープとも呼ばれます) を定義する必要があります。 "*マスター ユーザー*" または "*テナント管理者*" は、Power BI REST API を使用してこれらのアクセス許可を使用するための同意を付与する必要があります。

Azure AD に対する認証が成功した後は、Web アプリで[埋め込みトークン](/rest/api/power-bi/embedtoken)を生成し、特定の Power BI コンテンツへのアクセスをユーザーに許可します。

>[!NOTE]
>* "*顧客向け埋め込み*" ソリューションを使用して埋め込むには、A、EM、または P SKU の容量が必要です。
>* [運用を開始する](move-to-production.md)には、容量が必要です。

次の図は、"*顧客向け埋め込み*" ソリューションの認証フローを示したものです。

>[!div class="mx-imgBorder"]
>:::image type="content" source="media\embed-tokens\paas-authentiction.png" alt-text="顧客向け埋め込みの Power BI 埋め込み分析ソリューションにおける認証フローの図。":::

1. Web アプリのユーザーは、(指定されている認証方法を使用して) Web アプリに対する認証を行います。

2. Web アプリにより、"*サービス プリンシパル*" または "*マスター ユーザー*" を使用して、Azure AD に対する認証が行われます。

3. Web アプリにより、Azure AD から "*Azure AD トークン*" が取得され、それを使用して Power BI REST API へのアクセスが行われます。 Power BI REST API には、認証方法 ("*サービス プリンシパル*" または "*マスター ユーザー*") に従ってアクセスできるようになります。

4. Web アプリにより、[埋め込みトークン](/rest/api/power-bi/embedtoken) REST API 操作が呼び出され、"*埋め込みトークン*" が要求されます。 "*埋め込みトークン*" では、どの Power BI コンテンツを埋め込むことができるかが指定されています。

5. REST API から Web アプリに、"*埋め込みトークン*" が返されます。

6. Web アプリにより、埋め込みトークンがユーザーの Web ブラウザーに渡されます。

7. Web アプリのユーザーは、埋め込みトークンを使用して Power BI にアクセスします。

### <a name="embed-for-your-organization"></a>組織向けに埋め込む

"*組織向け埋め込み*" ソリューションでは、対話型の認証フローを使用します。 ユーザーは、Power BI の資格情報を使用して、Azure AD に対する認証を行います。 ユーザーは、Azure AD にアプリを登録するときに設定された API アクセス許可への同意を付与する必要があります。 同意は、Microsoft の *[要求されているアクセス許可]* ダイアログのポップアップ ウィンドウで付与します。 同意が付与されたら、Web アプリのユーザーがアクセスできるレポートやダッシュボードなどの Power BI コンテンツを、埋め込むことができます。

>[!div class="mx-imgBorder"]
>:::image type="content" source="media/embed-tokens/requested-premissions.png" alt-text="Power BI にアクセスするためのアクセス許可を付与するよう顧客に求める Microsoft の [要求されているアクセス許可] ポップアップ ウィンドウを示すスクリーンショット。":::

>[!NOTE]
>* "*組織向け埋め込み*" ソリューションでは、A SKU はサポートされていません。
>* [運用環境に移行する](move-to-production.md)には、次のいずれかの構成が必要です。
>    * Pro ライセンスを持つすべてのユーザー。
>    * PPU ライセンスを持つすべてのユーザー。
>    * [容量](embedded-capacity.md)。 この構成を使用すると、すべてのユーザーが無料ライセンスを持つことができます。

次の図は、"*組織向け埋め込み*" ソリューションの認証フローの例を示したものです。

>[!div class="mx-imgBorder"]
>:::image type="content" source="media/embed-tokens/saas-authentiction.png" alt-text="組織向け埋め込みの Power BI 埋め込み分析ソリューションにおける認証フローの図。":::

1. Web アプリのユーザーが Web アプリにアクセスします。

2. Web アプリにより、Web アプリのユーザーは Azure AD にリダイレクトされます。

3. Web アプリのユーザーは、自分の Power BI 資格情報を使用して、Azure AD に対する認証を行います。

4. Web アプリのユーザーは、Azure AD により、Azure AD トークンと共に Web アプリに再びリダイレクトされます (暗黙的な許可のシナリオでは、アクセス トークンはユーザーのブラウザーに返されます)。

5. Web アプリにより、Azure AD トークンがユーザーの Web ブラウザーに渡されます。

6. Power BI Web アプリにより、Azure AD トークンを使用して、Web アプリのユーザーがアクセス権を持っているレポートやダッシュボードなどの Power BI コンテンツが埋め込まれます。

## <a name="next-steps"></a>次のステップ

>[!div class="nextstepaction"]
>[埋め込みトークンを生成するときの考慮事項](generate-embed-token.md)

>[!div class="nextstepaction"]
>[Power BI Embedded の分析の容量と SKU](embedded-capacity.md)

>[!div class="nextstepaction"]
>[他にわからないことがある場合は、Power BI コミュニティで質問してみてください](https://community.powerbi.com/)