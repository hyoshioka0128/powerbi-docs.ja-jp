---
title: Power BI 埋め込み分析の埋め込み BI で使用する Azure Active Directory テナントを作成する
description: カスタムの埋め込み分析アプリケーション用に新しい Azure Active Directory (Azure AD) テナントを作成する方法について説明します。このアプリケーションは、Power BI REST API を呼び出し、顧客のために埋め込み BI インテリジェンスを有効にします。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 05/28/2019
ms.openlocfilehash: 24e1d8678234b7b355d99985f8e8a567954d6211
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888997"
---
# <a name="create-an-azure-active-directory-tenant-to-use-with-power-bi"></a>Power BI で使用する Azure Active Directory テナントを作成する

[Power BI REST API](../automation/rest-api-reference.md) を呼び出すカスタム アプリケーション用に新しい Azure Active Directory (Azure AD) テナントを作成する方法を説明します。

テナントは、Azure Active Directory 内の組織を表します。 これは、組織が Azure、Microsoft Intune、Microsoft 365 などの Microsoft のクラウド サービスにサインアップする際に、受け取って所有する Azure AD サービスの専用インスタンスです。 各 Azure AD テナントは独立しており、他の Azure AD テナントとは切り離されています。

Azure AD テナントを作成すると、アプリケーションを定義して、それにアクセス許可を割り当てて、[Power BI REST API](../automation/rest-api-reference.md) を呼び出せるようにすることができます。

組織にはアプリケーションに使用できる Azure AD テナントが既にある場合があります。 アプリケーション専用の新しいテナントを作成することもできます。 この記事では、新しいテナントを作成する方法を説明します。

## <a name="create-an-azure-active-directory-tenant"></a>Azure Active Directory テナントを作成する

カスタム アプリケーションに Power BI を統合するには、Azure AD 内で、Azure AD ディレクトリを必要とするアプリケーションを定義する必要があります。 このディレクトリが、*テナント* です。 組織で Power BI または Microsoft 365 を使用していないためにまだテナントがない場合は、[開発環境を設定する必要があります](/azure/active-directory/develop/active-directory-howto-tenant)。 また、アプリケーションを組織のテナントと混在させたくない場合にも、テナントを作成して、分離させる必要があります。 または、テスト目的でテナントを作成することもできます。

新しい Azure AD テナントを作成するには:

1. [Azure Portal](https://portal.azure.com) を参照し、Azure サブスクリプションを持つアカウントを使用してサインインします。

2. **プラスのアイコン (+)** を選択し、**Azure Active Directory** を検索します。

    ![プラス アイコン (+)](media/create-an-azure-active-directory-tenant/new-directory.png)

3. 検索結果で **Azure Active Directory** を選択します。

    ![AAD の検索](media/create-an-azure-active-directory-tenant/new-directory2.png)

4. **[作成]** を選択します。

5. **組織の名前** と **初期ドメイン名** を指定します。 **[作成]** を選択します。 ディレクトリが作成されます。

    ![組織とドメイン](media/create-an-azure-active-directory-tenant/organization-and-domain.png)

   > [!NOTE]
   > 初期ドメインは、onmicrosoft.com の一部になります。 他のドメイン名は、後で追加することができます。 テナントのディレクトリには、複数のドメインを割り当てることができます。

6. ディレクトリの作成が完了したら、新しいディレクトリを管理する情報ボックスを選択します。

次に、テナントのユーザーを追加します。

## <a name="create-azure-active-directory-tenant-users"></a>Azure Active Directory テナントのユーザーを作成する

ディレクトリができたので、少なくとも 2 人のユーザーを作成してみましょう。 1 人はテナントのグローバル管理者となり、もう 1 人は埋め込み用のマスター ユーザーとなります。 後者はサービス アカウントとして考えることができます。

1. Azure portal で Azure Active Directory のフライアウトが表示されていることを確認します。

    ![Azure AD のフライアウト](media/create-an-azure-active-directory-tenant/aad-flyout.png)

    そうでない場合は、左側のサービス ナビゲーションから Azure Active Directory アイコンを選択します。

    ![Azure AD アイコン](media/create-an-azure-active-directory-tenant/aad-service.png)

2. **[管理]** で、 **[ユーザー]** を選択します。

    ![Azure AD のユーザーとグループ](media/create-an-azure-active-directory-tenant/users-and-groups.png)

3. **[すべてのユーザー]** 、 **[+ 新しいユーザー]** の順に選択します。

4. テナントのグローバル管理者の **[名前]** と **[ユーザー名]** を指定します。 **[ディレクトリ ロール]** を **[グローバル管理者]** に変更します。 また、一時パスワードを表示することもできます。 完了したら、 **[作成]** を選択します。

    ![Azure AD グローバル管理者](media/create-an-azure-active-directory-tenant/global-admin.png)

5. 通常のテナント ユーザーに対して同じ操作を行います。 このアカウントは、マスター埋め込みアカウントに使用できます。 今回は、 **[ディレクトリ ロール]** は **[ユーザー]** のままにします。 パスワードをメモし、 **[作成]** を選択します。

    ![Azure AD ユーザー](media/create-an-azure-active-directory-tenant/pbiembed-user.png)

6. 手順 5 で作成したユーザー アカウントで Power BI にサインアップします。 [powerbi.com](https://powerbi.microsoft.com/get-started/) に移動し、 **[Power BI - クラウド コラボレーションおよび共有]** の下で **[無料試用版]** を選択します。

    ![テナントの作成](media/create-an-azure-active-directory-tenant/try-powerbi-free.png)

    サインアップすると、Power BI Pro の 60 日間の無料体験を勧められます。 それを選択して Pro ユーザーになることができます。それにより、[埋め込みソリューションの開発を開始する](embed-sample-for-customers.md)オプションが表示されます。

   > [!NOTE]
   > ユーザー アカウントの電子メール アドレスでサインアップしてください。

## <a name="next-steps"></a>次の手順

これで、Azure AD テナントが作成されたので、このテナントを使用して、Power BI 内の項目をテストできます。 また、Power BI ダッシュボードやレポートをアプリケーションに埋め込むこともできます。 詳細については、[Power BI ダッシュボード、レポート、およびタイルを埋め込む方法](embed-sample-for-customers.md)に関するページを参照してください。

[Azure Active directory とは](/azure/active-directory/active-directory-whatis) 
 
[クイック スタート:開発環境の設定](/azure/active-directory/develop/active-directory-howto-tenant)  

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。