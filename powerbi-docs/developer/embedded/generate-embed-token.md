---
title: 埋め込みトークンの生成に関する考慮事項
description: 埋め込みトークンの生成に関する考慮事項、制限事項、および必要なアクセス許可について説明します
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.custom: ''
ms.date: 10/15/2020
ms.openlocfilehash: cea97f16cf06e80b7b16ef7740fcf3103b2f1eb4
ms.sourcegitcommit: 9d033abd9c01a01bba132972497dda428d7d5c12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95513782"
---
# <a name="considerations-when-generating-an-embed-token"></a>埋め込みトークンを生成するときの考慮事項

[トークンの生成](/rest/api/power-bi/embedtoken)は、Web アプリまたはポータルに Power BI の項目を埋め込むためのトークンを生成できる REST API です。 トークンは、Power BI サービスに対する要求を承認するために使用されます。

トークンの生成 API により、アプリでのユーザーの資格情報 (有効な ID) に応じて、1 つの ID (マスター ユーザーまたはサービス プリンシパル) を使用して、個々のユーザーのトークンが生成されます。

認証が成功すると、関連データへのアクセスが許可されます。

>[!NOTE]
>トークンの生成は、"[*顧客用の埋め込み*](embed-sample-for-customers.md)" を行っている場合にのみ適用されます ("*アプリ所有データ*" シナリオとも呼ばれます)。

次の API を使用してトークンを生成できます。

* [ダッシュボード](/rest/api/power-bi/embedtoken/dashboards_generatetokeningroup)

* [データセット](/rest/api/power-bi/embedtoken/datasets_generatetokeningroup)

* [複数レポート用トークン生成](/rest/api/power-bi/embedtoken/generatetoken)


* [レポートの作成](/rest/api/power-bi/embedtoken/reports_generatetokenforcreateingroup)

* [レポート](/rest/api/power-bi/embedtoken/reports_generatetokeningroup)

* [タイル](/rest/api/power-bi/embedtoken/tiles_generatetokeningroup)

## <a name="workspace-versions"></a>ワークスペースのバージョン

Power BI には、"*クラシック*" ワークスペースと "*新しい*" ワークスペースの 2 つのワークスペース バージョンがあります。 これらのワークスペースの違いの詳細については、「[新しいワークスペースとクラシック ワークスペースの違い](../../collaborate-share/service-new-workspaces.md#new-and-classic-workspace-differences)」を参照してください。

埋め込みトークンを作成する場合、ワークスペースが異なると、考慮事項と必要なアクセス許可も異なります。

|                  |"*クラシック*" ワークスペース |"*新しい*" ワークスペース|
|------------------|---------|--------|
|**考慮事項**|<li>データセットと項目は、同じワークスペース内に存在する必要があります</li><li>サービス プリンシパルは使用できません</li>  |データセットと項目は、2 つの異なる "*新しい*" ワークスペース内に存在できます |
|**ワークスペースのアクセス許可**|マスター ユーザーは、ワークスペースの管理者である必要があります  |サービス プリンシパルまたはマスター ユーザーは、少なくとも両方のワークスペースのメンバーである必要があります |

>[!NOTE]
>* [マイ ワークスペース](../../consumer/end-user-workspaces.md#types-of-workspaces)に対する埋め込みトークンを作成することはできません。
>* "*項目*" という言葉は、ダッシュボード、タイル、Q&A、レポートなどの Power BI の項目を示します。

## <a name="securing-your-data"></a>データのセキュリティ保護

ソリューションを作成するときは、次の 2 つの方法でデータをセキュリティ保護することを検討します。

* [ワークスペースに基づく分離](embed-multi-tenancy.md#power-bi-workspace-based-isolation)

* [行レベルのセキュリティに基づく分離](embed-multi-tenancy.md#row-level-security-based-isolation)

RLS のアプローチを使用する場合は、この記事の最後にある [RLS に関する考慮事項と制限事項](generate-embed-token.md#row-level-security)を確認してください。

## <a name="token-permissions"></a>トークン アクセス許可

トークンの生成 API の *GenerateTokenRequest* セクションで、トークンのアクセス許可を記述します。

>[!NOTE]
>このセクションに列記されているトークンのアクセス許可は、[複数レポート用トークン生成](/rest/api/power-bi/embedtoken/generatetoken) API には適用されません。

### <a name="access-level"></a>アクセス レベル

ユーザーのアクセス レベルを決定するには、*accessLevel* パラメーターを使用します。

* **View** - ユーザーに表示アクセス許可を付与します。

* **Edit** - ユーザーに表示と編集のアクセス許可を付与します (レポート用の埋め込みトークンを生成する場合にのみ適用されます)。

    [複数レポート用トークン生成](/rest/api/power-bi/embedtoken/generatetoken) API を使用している場合は、*allowEdit* パラメーターを使用して、ユーザーに表示と編集のアクセス許可を付与します。

* **Create** - ユーザーにレポートを作成するためのアクセス許可を付与します (レポートを作成するための埋め込みトークンを生成する場合にのみ適用されます)。

    レポートを作成するには、*datasetId* パラメーターも指定する必要があります。

### <a name="saving-a-copy-of-the-report"></a>レポートのコピーの保存

ユーザーがレポートを新しいレポートとして保存できるようにするには、*allowSaveAs* ブール値を使用します。 この設定は、既定では *false* に設定されます。

このパラメーターは、レポート用の埋め込みトークンを生成する場合にのみ適用されます。

### <a name="row-level-security"></a>行レベルのセキュリティ

[行レベル セキュリティ (RLS)](embedded-row-level-security.md) を使用すると、トークンを生成しているサービス プリンシパルまたはマスター ユーザーの ID とは異なる ID を使用することを選択できます。 このオプションを使用すると、対象ユーザーに応じて埋め込まれた情報を表示できます。 たとえば、アプリケーションでユーザーにサインインを要求し、サインインしているユーザーが販売従業員である場合、販売情報のみが含まれるレポートを表示することができます。

RLS を使用している場合、状況によってはユーザーの ID (*EffectiveIdentity* パラメーター) を省略することができます。 これにより、トークンはデータベース全体にアクセスできるようになります。 この方法を使用すると、データセット全体を表示するアクセス許可を持つ管理者やマネージャーなどのユーザーにアクセス権を付与できます。 ただし、すべてのシナリオでこの方法を使用することはできません。 次の表では、さまざまな RLS の種類と、ユーザーの ID を指定せずに使用できる認証方法を示します。

また、表には、各 RLS の種類に適用される考慮事項と制限も示されています。

|RLS の種類  |有効なユーザー ID を指定せずに埋め込みトークンを生成できるか?  |考慮事項と制限事項  |
|---------|---------|---------|
|クラウド行レベル セキュリティ (クラウド RLS)      |✔ マスター ユーザー<br/>✖ サービス プリンシパル          |         |
|RDL (ページ分割されたレポート)     |✖ マスター ユーザー<br/>✔ サービス プリンシパル        |マスター ユーザーを使用して RDL 用の埋め込みトークンを生成することはできません。         |
|Analysis Services (AS) のオンプレミス ライブ接続    |✔ マスター ユーザー<br/>✖ サービス プリンシパル         |埋め込みトークンを生成するユーザーには、次のいずれかのアクセス許可も必要です。<li>ゲートウェイ管理者のアクセス許可</li><li>データソース借用のアクセス許可 (*ReadOverrideEffectiveIdentity*)</li>         |
|Analysis Services (AS) の Azure ライブ接続    |✔ マスター ユーザー<br/>✖ サービス プリンシパル         |埋め込みトークンを生成するユーザーの ID を、オーバーライドすることはできません。 カスタム データを使用して、動的な RLS またはセキュリティで保護されたフィルター処理を実装できます。<br/><br/>**注:** サービス プリンシパルは、有効な ID (RLS ユーザー名) としてそのオブジェクト ID を提供する必要があります。         |
|シングル サインオン (SSO)     |✔ マスター ユーザー<br/>✖ サービス プリンシパル         |明示的な (SSO) ID を、有効な ID オブジェクトの ID BLOB プロパティを使用して提供できます         |
|SSO とクラウド RLS     |✔ マスター ユーザー<br/>✖ サービス プリンシパル         |次のものを指定する必要があります。<li>有効な ID オブジェクトの ID BLOB プロパティの明示的な (SSO) ID</li><li>有効な (RLS) ID (ユーザー名)</li>         |

>[!NOTE]
>サービス プリンシパルは、常に次のものを提供する必要があります。
>* RLS データセットでの任意の項目に対する ID。
>* SSO データセットの場合、ユーザー名プロパティが定義されている有効な RLS ID。

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
>[サービス プリンシパルを使用した Power BI コンテンツの埋め込み](embed-service-principal.md)