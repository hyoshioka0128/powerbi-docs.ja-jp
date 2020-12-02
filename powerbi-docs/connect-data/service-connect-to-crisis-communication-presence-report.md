---
title: 危機管理コミュニケーション プレゼンス レポートに接続する
description: COVID-19 危機管理コミュニケーション プレゼンス レポート テンプレート アプリを取得してインストールする方法、およびデータに接続する方法
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 04/06/2020
LocalizationGroup: Connect to services
ms.openlocfilehash: 7cce4f9e78fce27fedf795a4a0016593580f061a
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96403170"
---
# <a name="connect-to-the-crisis-communication-presence-report"></a>危機管理コミュニケーション プレゼンス レポートに接続する

この Power BI アプリは、危機管理コミュニケーション用の Microsoft Power Platform ソリューションのレポートやダッシュボードの成果物です。 危機管理コミュニケーション アプリ ユーザー用の worker の場所を追跡します。 このソリューションは、Power Apps、Power Automate、Teams、SharePoint および Power BI の機能を組み合わせたものです。 Web、モバイル、または Teams で使用できます。

![危機管理コミュニケーション プレゼンス レポートのアプリ レポート](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report.png)

ダッシュボードでは、非常事態担当マネージャーに対して、タイムリーに適切な意思決定を行うのに役立つヘルス システム全体の集計データが表示されます。

この記事では、アプリをインストールする方法と、データ ソースに接続する方法について説明します。 危機管理コミュニケーション アプリの詳細については、「[Power Apps での危機通信のサンプル テンプレートのセットアップと学習](/powerapps/maker/canvas-apps/sample-crisis-communication-app)」を参照してください

テンプレート アプリをインストールし、データ ソースに接続した後、必要に応じてレポートをカスタマイズできます。 その後、組織内の同僚にアプリとして配布することができます。

## <a name="prerequisites"></a>前提条件

このテンプレート アプリをインストールする前に、まず、[危機管理コミュニケーションのサンプル](/powerapps/maker/canvas-apps/sample-crisis-communication-app)をインストールして設定する必要があります。 このソリューションをインストールすると、アプリにデータを設定するために必要なデータソース参照が作成されます。

危機管理コミュニケーション サンプルをインストールする場合は、["CI_Employee Status" の SharePoint リスト フォルダーのパスとリスト ID](/powerapps/maker/canvas-apps/sample-crisis-communication-app#monitor-office-absences-with-power-bi) をメモしておいてください。

## <a name="install-the-app"></a>アプリをインストールする

1. アプリにアクセスするには、次のリンクをクリックします: [危機管理コミュニケーション プレゼンス レポート テンプレート アプリ](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.crisiscomms)

1. アプリの [AppSource] ページで、[ **[今すぐ入手する]**](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.crisiscomms) を選択します。

    [![AppSource の危機管理コミュニケーション プレゼンス レポート アプリ](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-appsource-get-it-now.png)](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.crisiscomms)

1. **[One more thing]\(最後に\)** の情報を読み、 **[続行]** を選択します。

    ![危機管理コミュニケーション プレゼンス レポート アプリ、[One more thing]\(最後に\)](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-1-more-thing.png)

1. **[インストール]** を選択します。 

    ![危機管理コミュニケーション プレゼンス レポート アプリをインストールする](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-select-install.png)

    アプリがインストールされると、[アプリ] ページに表示されます。

   ![[アプリ] ページの危機管理コミュニケーション プレゼンス レポート アプリ](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>データ ソースに接続する

1. [アプリ] ページでアイコンを選択して、アプリを開きます。

1. スプラッシュ スクリーンで、 **[探索]** を選択します。

   ![テンプレート アプリのスプラッシュ スクリーン](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-splash-screen.png)

   アプリが開き、サンプル データが表示されます。

1. ページの上部にあるバナーの **[データを接続]** リンクを選択します。

   ![危機管理コミュニケーション プレゼンス レポート アプリの [データを接続] リンク](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-connect-data.png)

1. ダイアログ ボックスで、次のようにします。
   1. SharePoint_Folder フィールドに、["CI_Employee Status" SharePoint リスト パス](/powerapps/maker/canvas-apps/sample-crisis-communication-app#monitor-office-absences-with-power-bi)を入力します。
   1. List_ID フィールドに、リスト設定から取得したリスト ID を入力します。 完了したら、 **[次へ]** をクリックします。

   ![危機管理コミュニケーション プレゼンス レポート アプリの URL ダイアログ](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-url-dialog.png)

1. 次に表示されるダイアログで、認証方法を **[OAuth2]** に設定します。 プライバシー レベルの設定については、何もする必要はありません。

   **[サインイン]** をクリックします。

   ![危機管理コミュニケーション プレゼンス レポート アプリの認証ダイアログ](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-authentication-dialog.png)

1. Microsoft サインイン画面で、Power BI にサインインします。

   ![Microsoft サインイン画面](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-microsoft-login.png)

   サインインした後、レポートがデータ ソースに接続され、最新のデータが設定されます。 この間は、利用状況モニターが作動します。

   ![危機管理コミュニケーション プレゼンス レポート アプリの進行中の更新](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-refresh-monitor.png)

## <a name="schedule-report-refresh"></a>レポート更新のスケジュールを設定する

データ更新が完了したら、レポート データを最新の状態に保つために、[更新スケジュールを設定](../connect-data/refresh-scheduled-refresh.md)します。

1. 上部のヘッダー バーで、 **[Power BI]** を選択します。

   ![Power BI の階層リンク](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-powerbi-breadcrumb.png)

1. 左側のナビゲーション ペインの **[ワークスペース]** の下で、病院の緊急時対応の意思決定支援ダッシュボード ワークスペースを見つけ、「[スケジュールされた更新の構成](../connect-data/refresh-scheduled-refresh.md)」記事に記載されている手順に従います。

## <a name="customize-and-share"></a>カスタマイズと共有

詳細については、「[アプリをカスタマイズして共有する](../connect-data/service-template-apps-install-distribute.md#customize-and-share-the-app)」を参照してください。 アプリを公開または配布する前に、必ず、[レポートの免責事項](../create-reports/sample-covid-19-us.md#disclaimers)を確認してください。

## <a name="next-steps"></a>次の手順
* [Power Apps での危機通信のサンプル テンプレートのセットアップと学習](/powerapps/maker/canvas-apps/sample-crisis-communication-app)
* わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
* [Power BI テンプレート アプリとは](../connect-data/service-template-apps-overview.md)
* [組織でテンプレート アプリをインストールして配布する](../connect-data/service-template-apps-install-distribute.md)