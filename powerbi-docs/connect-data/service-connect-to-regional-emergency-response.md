---
title: 地域的緊急応答ダッシュボードに接続する
description: COVID-19 の地域的緊急応答用意思決定支援ダッシュボード テンプレート アプリを取得してインストールする方法、およびデータに接続する方法
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 04/24/2020
LocalizationGroup: Connect to services
ms.openlocfilehash: b8cb2be15d084bba3fc2a70152165ce3b2909dab
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410553"
---
# <a name="connect-to-the-regional-emergency-response-dashboard"></a>地域的緊急応答ダッシュボードに接続する
地域的緊急応答ダッシュボードは、[Microsoft Power Platform 地域的緊急応答ソリューション](/powerapps/sample-apps/regional-emergency-response/overview)のレポート コンポーネントです。 地域組織の管理者は、Power BI テナントのダッシュボードを表示して、効率的な意思決定を行うのに役立つ重要なデータとメトリックをすばやく確認することができます。

![地域的緊急応答ダッシュボード アプリ レポート](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-report.png)

この記事では、地域的緊急応答ダッシュボード テンプレート アプリを使用して地域的緊急応答アプリをインストールする方法と、データ ソースに接続する方法について説明します。

ダッシュボードに表示される情報の詳細については、「[分析情報の取得](/powerapps/sample-apps/regional-emergency-response/portals-admin-reporting#get-insights)」を参照してください。

テンプレート アプリをインストールし、データ ソースに接続した後、必要に応じてレポートをカスタマイズできます。 その後、組織内の同僚にアプリとして配布することができます。

## <a name="prerequisites"></a>前提条件

このテンプレート アプリをインストールする前に、まず、[地域的緊急応答ソリューション](/powerapps/sample-apps/regional-emergency-response/deploy)をインストールして設定する必要があります。 このソリューションをインストールすると、アプリにデータを設定するために必要なデータソース参照が作成されます。

地域的緊急応答ソリューションをインストールする場合は、[Common Data Service 環境インスタンスの URL](/powerapps/sample-apps/regional-emergency-response/deploy#step-5-configure-and-publish-power-bi-dashboard) をメモしておいてください。 これは、テンプレート アプリをデータに接続するために必要になります。

## <a name="install-the-app"></a>アプリをインストールする

1. アプリにアクセスするには、次のリンクをクリックします: [地域的緊急応答ダッシュボード テンプレート アプリ](https://appsource.microsoft.com/product/power-bi/powerapps_cxo.regional_response)

1. アプリの [AppSource] ページで、[ **[今すぐ入手する]**](https://appsource.microsoft.com/product/power-bi/powerapps_cxo.regional_response) を選択します。

    [![AppSource の地域的緊急応答ダッシュボード アプリ](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-appsource-get-it-now.png)](https://appsource.microsoft.com/product/power-bi/powerapps_cxo.regional_response)

1. **[インストール]** を選択します。 

    ![地域的緊急応答ダッシュボード アプリをインストールする](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-select-install.png)

    アプリがインストールされると、[アプリ] ページに表示されます。

   ![[アプリ] ページの地域的緊急応答ダッシュボード アプリ](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>データ ソースに接続する

1. [アプリ] ページでアイコンを選択して、アプリを開きます。

1. スプラッシュ スクリーンで、 **[探索]** を選択します。

   ![テンプレート アプリのスプラッシュ スクリーン](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-splash-screen.png)

   アプリが開き、サンプル データが表示されます。

1. ページの上部にあるバナーの **[データを接続]** リンクを選択します。

   ![地域的緊急応答ダッシュボード アプリの [データを接続] リンク](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-connect-data.png)

1. 表示されるダイアログボックスに、[Common Data Service 環境インスタンスの URL](/powerapps/sample-apps/emergency-response/deploy-configure#publish-the-power-bi-dashboard) を入力します。 たとえば、 https://[myenv].crm.dynamics.com です。 完了したら、 **[次へ]** をクリックします。

   ![地域的緊急応答ダッシュボード アプリの URL ダイアログ](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-url-dialog.png)

1. 次に表示されるダイアログで、認証方法を **[OAuth2]** に設定します。 プライバシー レベルの設定については、何もする必要はありません。

   **[サインイン]** をクリックします。

   ![地域的緊急応答ダッシュボード アプリの認証ダイアログ](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-authentication-dialog.png)

1. Microsoft サインイン画面で、Power BI にサインインします。

   ![Microsoft サインイン画面](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-microsoft-login.png)

   サインインした後、レポートがデータ ソースに接続され、最新のデータが設定されます。 この間は、利用状況モニターが作動します。

   ![地域的緊急応答ダッシュボード アプリの更新が進行中](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-refresh-monitor.png)

## <a name="schedule-report-refresh"></a>レポート更新のスケジュールを設定する

データ更新が完了したら、レポート データを最新の状態に保つために、[更新スケジュールを設定](../connect-data/refresh-scheduled-refresh.md)します。

1. 上部のヘッダー バーで、 **[Power BI]** を選択します。

   ![Power BI の階層リンク](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-powerbi-breadcrumb.png)

1. 左側のナビゲーション ペインの **[ワークスペース]** の下で、地域的緊急応答ダッシュボード ワークスペースを見つけ、「[スケジュールされた更新の構成](../connect-data/refresh-scheduled-refresh.md)」記事に記載されている手順に従います。

## <a name="customize-and-share"></a>カスタマイズと共有

詳細については、「[アプリをカスタマイズして共有する](../connect-data/service-template-apps-install-distribute.md#customize-and-share-the-app)」を参照してください。 アプリを公開または配布する前に、必ず、[レポートの免責事項](/powerapps/sample-apps/regional-emergency-response/overview#disclaimer)を確認してください。

## <a name="next-steps"></a>次の手順
* [地域的緊急応答ダッシュボードについて](/powerapps/sample-apps/regional-emergency-response/portals-admin-reporting#get-insights)
* [Power Apps での危機通信のサンプル テンプレートのセットアップと学習](/powerapps/maker/canvas-apps/sample-crisis-communication-app)
* わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
* [Power BI テンプレート アプリとは](../connect-data/service-template-apps-overview.md)
* [組織でテンプレート アプリをインストールして配布する](../connect-data/service-template-apps-install-distribute.md)