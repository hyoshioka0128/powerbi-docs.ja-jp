---
title: Power BI で GitHub に接続する
description: Power BI 用 GitHub
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 05/19/2020
LocalizationGroup: Connect to services
ms.openlocfilehash: e92afdbad41f212ac93245583430ae44fe0abaf9
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410645"
---
# <a name="connect-to-github-with-power-bi"></a>Power BI で GitHub に接続する
この記事では、Power BI テンプレート アプリを使用して GitHub アカウントからデータをプルする手順について説明します。 このテンプレート アプリは、ダッシュボード、一連のレポート、およびデータセットを含むワークスペースを生成して、GitHub データの探索を可能にします。 Power BI 用の GitHub アプリは、投稿、問題、pull request、アクティブなユーザーなどに関するデータを含む、GitHub リポジトリ (リポジトリとも呼ばれます) の分析情報を示します。

![GitHub テンプレート アプリ](media/service-connect-to-github/service-github-app-report.png)

テンプレート アプリをインストールした後は、ダッシュボードとレポートを変更できます。 その後、組織内の同僚にアプリとして配布することができます。

[GitHub テンプレート アプリ](https://app.powerbi.com/groups/me/getapps/services/pbi-contentpacks.pbiapps-github)に接続するか、Power BI と [GitHub との統合](https://powerbi.microsoft.com/integrations/github)について詳細をお読みください。

[GitHub のチュートリアル](service-tutorial-connect-to-github.md)を試すこともできます。 この場合、Power BI のドキュメントのパブリック リポジトリに関する実際の GitHub データがインストールされます。

>[!NOTE]
>このテンプレート アプリを使用するには、GitHub アカウントがリポジトリにアクセスできる必要があります。 要件の詳細については、このあと説明します。
>
>このテンプレート アプリでは、GitHub Enterprise はサポートされていません。

## <a name="install-the-app"></a>アプリをインストールする

1. アプリにアクセスするには、次のリンクをクリックします: [GitHub テンプレート アプリ](https://app.powerbi.com/groups/me/getapps/services/pbi-contentpacks.pbiapps-github)

1. アプリの [AppSource] ページで、[ **[今すぐ入手する]**](https://app.powerbi.com/groups/me/getapps/services/pbi-contentpacks.pbiapps-github) を選択します。

    [![AppSource の GitHub テンプレート アプリ](media/service-connect-to-github/service-github-template-app-appsource-get-it-now.png)](https://app.powerbi.com/groups/me/getapps/services/pbi-contentpacks.pbiapps-github)

1. **[インストール]** を選択します。 

    ![GitHub テンプレート アプリをインストールする](media/service-connect-to-github/service-regional-emergency-response-select-install.png)

    アプリがインストールされると、[アプリ] ページに表示されます。

   ![[アプリ] ページの GitHub アプリ](media/service-connect-to-github/service-github-app-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>データ ソースに接続する

1. [アプリ] ページでアイコンを選択して、アプリを開きます。

1. スプラッシュ スクリーンで、 **[アプリを探索]** を選択します。

   ![テンプレート アプリのスプラッシュ スクリーン](media/service-connect-to-github/service-github-app-splash-screen.png)

   アプリが開き、サンプル データが表示されます。

1. ページの上部にあるバナーの **[データを接続]** リンクを選択します。

   ![GitHub アプリの [データを接続] リンク](media/service-connect-to-github/service-github-app-connect-data.png)

1. 表示されるダイアログ ボックスで、リポジトリの名前とリポジトリの所有者を入力します。 [これらのパラメーターの見つけ方](#FindingParams)について詳しくは、後述します。 完了したら、 **[次へ]** をクリックします。

   ![Power BI での GitHub リポジトリ名](media/service-connect-to-github/power-bi-github-app-tutorial-connect.png)

1. 次に表示されるダイアログで、認証方法が **[OAuth2]** に設定されていることを確認します。 プライバシーの設定については何もする必要はありません。 準備ができたら、 **[サインイン]** をクリックします。

   ![Power BI GitHub の認証方法](media/service-connect-to-github/power-bi-github-authentication.png)

1. ご自分の GitHub の資格情報を入力し、GitHub の認証プロセスに従います (ブラウザーで既にサインインしている場合は、この手順が省略される可能性があります)。

   ![Power BI GitHub の認証プロセス](media/service-connect-to-github/power-bi-github-authenticate-process.png)


サインインした後、レポートがデータ ソースに接続され、最新のデータが設定されます。 この間は、利用状況モニターが作動します。

![Power BI GitHub アプリの更新が進行中](media/service-connect-to-github/service-github-app-refresh-monitor.png)

レポート データは 1 日に 1 回自動的に更新されます (サインイン プロセス中にこれを無効にしていない限り)。 また、[独自の更新スケジュールを設定](./refresh-scheduled-refresh.md)し、必要に応じてレポート データを最新の状態に保つこともできます。

## <a name="customize-and-share"></a>カスタマイズと共有

アプリをカスタマイズしたり共有したりするには、ページの右上隅にある鉛筆アイコンを選択します。

![アプリの編集](media/service-template-apps-install-distribute/power-bi-template-app-edit-app.png)


ワークスペースでの成果物の編集については、以下を参照してください。
* [Power BI でのレポート エディターのツアー](../create-reports/service-the-report-editor-take-a-tour.md)
* [Power BI サービスのデザイナー向けの基本的な概念](../fundamentals/service-basic-concepts.md)

ワークスペースで成果物に必要な変更を行った後は、アプリを発行して共有することができます。 これを行う方法については、「[アプリを発行する](../collaborate-share/service-create-distribute-apps.md#publish-your-app)」を参照してください。

## <a name="whats-included-in-the-app"></a>アプリに含まれるもの
Power BI では、次のデータを GitHub から使用できます。     

| テーブル名 | Description |
| --- | --- |
| 貢献 |投稿物のテーブルは、共同作成者によって作成された追加、削除、コミットの合計を週ごとに集計して示します。 上位 100 人の共同作成者が含まれています。 |
| Issues |選択したリポジトリのすべての問題の一覧を表示します。問題が閉じられるまでの合計時間と平均時間、開かれている問題の合計、閉じられた問題の合計などの計算が含まれます。 リポジトリに問題がない場合、このテーブルは空になります。 |
| Pull requests |このテーブルには、リポジトリのすべての Pull Requests と、要求をプルした人が含まれています。 また、開かれている pull request、閉じられている pull request、pull request の合計、要求をプルするまでにかかった時間、pull request にかかった平均時間などに関する計算も含まれます。 リポジトリに pull request がない場合、このテーブルは空になります。 |
| ユーザー |このテーブルは、選択されたリポジトリで投稿を行った、問題をファイリングした、または pull request を解決した GitHub ユーザー (共同作成者) の一覧を示します。 |
| Milestones |これは、選択したリポジトリのすべてのマイルス トーンです。 |
| DateTable |このテーブルには本日から過去数年間の日付が含まれており、これによって日付ごとに GitHub のデータを分析できます。 |
| ContributionPunchCard |このテーブルは、選択したリポジトリの投稿物のパンチ カードとして使用できます。 曜日別および時間別のコミット数を示します。 このテーブルは、モデル内の他のテーブルに接続されていません。 |
| RepoDetails |このテーブルは、選択したリポジトリの詳細を説明します。 |

## <a name="system-requirements"></a>システム要件
* リポジトリにアクセスできる GitHub アカウント。  
* 初めてログインするときに Power BI for GitHub アプリに与えられるアクセス許可。 アクセスを取り消す方法については、下記の詳細を参照してください。  
* データのプルと更新に使用できる十分な API 呼び出し。
>[!NOTE]
>このテンプレート アプリでは、GitHub Enterprise はサポートされていません。

### <a name="de-authorize-power-bi"></a>Power BI の承認解除
Power BI と GitHub リポジトリとの接続の承認を解除するには、GitHub のアクセスを取り消します。 詳しくは、この [GitHub ヘルプ](https://help.github.com/articles/keeping-your-ssh-keys-and-application-access-tokens-safe/#reviewing-your-authorized-applications-oauth) トピックをご覧ください。

<a name="FindingParams"></a>
## <a name="finding-parameters"></a>パラメーターの見つけ方
GitHub 自体のリポジトリを見ることで、所有者とリポジトリを確認できます。

![リポジトリの名前と所有者](media/service-connect-to-github/github_ownerrepo.png)

最初の部分の "Azure" が所有者で、2 番目の部分の "azure-sdk-for-php" がリポジトリそのものです。  リポジトリの URL にこれらの同じ 2 つ項目が現れます。

```console
<https://github.com/Azure/azure-sdk-for-php> .
```

## <a name="troubleshooting"></a>トラブルシューティング
必要に応じて、GitHub の資格情報を確認することができます。  

1. 別のブラウザー ウィンドウで、GitHub の Web サイトに移動して GitHub にサインインします。 GitHub サイトの右上隅でログイン状態を確認できます。    
2. GitHub で、Power BI でアクセスしようとしているリポジトリの URL に移動します。 たとえば、 https://github.com/dotnet/corefx です。  
3. Power BI に戻って GitHub に接続します。 [GitHub の構成] ダイアログ ボックスで、その同じリポジトリの名前と所有者を使用します。  

## <a name="next-steps"></a>次の手順

* [チュートリアル: Power BI を使用して GitHub リポジトリに接続する](service-tutorial-connect-to-github.md)
* [Power BI で新しいワークスペースを作成する](../collaborate-share/service-create-the-new-workspaces.md)
* [Power BI にアプリをインストールし、使用する](../consumer/end-user-apps.md)
* [外部サービス用の Power BI アプリに接続する](service-connect-to-services.md)
* わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
