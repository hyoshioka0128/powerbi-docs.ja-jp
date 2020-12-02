---
title: 病院の緊急時対応の意思決定支援ダッシュボードに接続する
description: COVID-19 の医療緊急用意思決定支援ダッシュボード テンプレート アプリを取得してインストールする方法、およびデータに接続する方法
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 05/13/2020
LocalizationGroup: Connect to services
ms.openlocfilehash: 823c8429c95a0b4d858540b2cf1183ca1c7caac7
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96403147"
---
# <a name="connect-to-the-hospital-emergency-response-decision-support-dashboard"></a>病院の緊急時対応の意思決定支援ダッシュボードに接続する
病院の緊急時対応の意思決定支援ダッシュボード テンプレート アプリは、[医療緊急時対応用 Microsoft Power Platform](https://powerapps.microsoft.com/blog/emergency-response-solution-a-microsoft-power-platform-solution-for-healthcare-emergency-response/) のレポート コンポーネントです。 ダッシュボードでは、非常事態担当マネージャーに対して、タイムリーに適切な意思決定を行うのに役立つヘルス システム全体の集計データが表示されます。

![病院の緊急時対応の意思決定支援ダッシュボード アプリ レポート](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-report.png)

この記事では、アプリをインストールする方法と、データ ソースに接続する方法について説明します。 このアプリで表示されるレポートの使用方法については、[病院の緊急時対応の意思決定支援ダッシュボードに関するドキュメント](/powerapps/sample-apps/emergency-response/deploy-configure#view-the-power-bi-dashboard)を参照してください。

テンプレート アプリをインストールし、データ ソースに接続した後、必要に応じてレポートをカスタマイズできます。 その後、組織内の同僚にアプリとして配布することができます。

## <a name="prerequisites"></a>前提条件

このテンプレート アプリをインストールする前に、まず、[病院の緊急時対応 Power Platform ソリューション](/powerapps/sample-apps/emergency-response/deploy-configure)をインストールして設定する必要があります。 このソリューションをインストールすると、アプリにデータを設定するために必要なデータソース参照が作成されます。

病院の緊急時対応 Power Platform ソリューションをインストールする場合は、[Common Data Service 環境インスタンスの URL](/powerapps/sample-apps/emergency-response/deploy-configure#publish-the-power-bi-dashboard) をメモしておいてください。 これは、テンプレート アプリをデータに接続するために必要になります。

## <a name="install-the-app"></a>アプリをインストールする

1. アプリにアクセスするには、次のリンクをクリックします: [病院の緊急時対応の意思決定支援ダッシュボード テンプレート アプリ](https://aka.ms/AppSource_Hospital_offer)

1. アプリの [AppSource] ページで、[ **[今すぐ入手する]**](https://aka.ms/AppSource_Hospital_offer) を選択します。

    [![AppSource の病院の緊急時対応の意思決定支援ダッシュボード アプリ](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-appsource-get-it-now.png)](https://aka.ms/AppSource_Hospital_offer)

1. **[One more thing]\(最後に\)** の情報を読み、 **[続行]** を選択します。

    ![病院の緊急時対応の意思決定支援ダッシュボード アプリ、[One more thing]\(最後に\)](media/service-connect-to-health-emergency-response/service-health-emergency-response-1-more-thing.png)

1. **[インストール]** を選択します。 

    ![病院の緊急時対応の意思決定支援ダッシュボード アプリをインストールする](media/service-connect-to-health-emergency-response/service-health-emergency-response-select-install.png)

    アプリがインストールされると、[アプリ] ページに表示されます。

   ![[アプリ] ページの病院の緊急時対応の意思決定支援ダッシュボード アプリ](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>データ ソースに接続する

1. [アプリ] ページでアイコンを選択して、アプリを開きます。

1. スプラッシュ スクリーンで、 **[探索]** を選択します。

   ![テンプレート アプリのスプラッシュ スクリーン](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-splash-screen.png)

   アプリが開き、サンプル データが表示されます。

1. ページの上部にあるバナーの **[データを接続]** リンクを選択します。

   ![病院の緊急時応答の意思決定支援ダッシュボード アプリの [データを接続] リンク](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-connect-data.png)

1. ダイアログ ボックスで、次のようにします。
   1. 組織名フィールドに、組織の名前 ("Contoso Health Systems" など) を入力します。 このフィールドは省略可能です。 この名前は、ダッシュボードの左上に表示されます。
   1. CDS_base_solution フィールドに、[Common Data Service 環境インスタンスの URL](/powerapps/sample-apps/emergency-response/deploy-configure#publish-the-power-bi-dashboard) を入力します。 たとえば、 https://[myenv].crm.dynamics.com です。 完了したら、 **[次へ]** をクリックします。

   ![病院の緊急時対応の意思決定支援アプリの URL ダイアログ](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-url-dialog.png)

1. 次に表示されるダイアログで、認証方法を **[OAuth2]** に設定します。 プライバシー レベルの設定については、何もする必要はありません。

   **[サインイン]** をクリックします。

   ![病院の緊急時対応の意思決定支援ダッシュボード アプリの認証ダイアログ](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-authentication-dialog.png)

1. Microsoft サインイン画面で、Power BI にサインインします。

   ![Microsoft サインイン画面](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-microsoft-login.png)

   サインインした後、レポートがデータ ソースに接続され、最新のデータが設定されます。 この間は、利用状況モニターが作動します。

   ![病院の緊急時対応の意思決定支援ダッシュボード アプリの進行中の更新](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-refresh-monitor.png)

## <a name="schedule-report-refresh"></a>レポート更新のスケジュールを設定する

データ更新が完了したら、レポート データを最新の状態に保つために、[更新スケジュールを設定](../connect-data/refresh-scheduled-refresh.md)します。

1. 上部のヘッダー バーで、 **[Power BI]** を選択します。

   ![Power BI の階層リンク](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-powerbi-breadcrumb.png)

1. 左側のナビゲーション ペインの **[ワークスペース]** の下で、病院の緊急時対応の意思決定支援ダッシュボード ワークスペースを見つけ、「[スケジュールされた更新の構成](../connect-data/refresh-scheduled-refresh.md)」記事に記載されている手順に従います。

## <a name="customize-and-share"></a>カスタマイズと共有

詳細については、「[アプリをカスタマイズして共有する](../connect-data/service-template-apps-install-distribute.md#customize-and-share-the-app)」を参照してください。 アプリを公開または配布する前に、必ず、[レポートの免責事項](../create-reports/sample-covid-19-us.md#disclaimers)を確認してください。

## <a name="next-steps"></a>次の手順
* [病院の緊急時対応レポートについて](/powerapps/sample-apps/emergency-response/deploy-configure#view-the-power-bi-dashboard)
* [Power Apps での危機通信のサンプル テンプレートのセットアップと学習](/powerapps/maker/canvas-apps/sample-crisis-communication-app)
* わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
* [Power BI テンプレート アプリとは](../connect-data/service-template-apps-overview.md)
* [組織でテンプレート アプリをインストールして配布する](../connect-data/service-template-apps-install-distribute.md)