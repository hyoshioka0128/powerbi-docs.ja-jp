---
title: Power BI Premium Capacity Metrics に接続する
description: Power BI Premium Capacity Metrics テンプレート アプリを取得してインストールする方法、およびデータに接続する方法
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 05/18/2020
LocalizationGroup: Connect to services
ms.openlocfilehash: f7bb6cdd3279ac15b2952d5e20b9c36a66a0c518
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410599"
---
# <a name="connect-to-power-bi-premium-capacity-metrics"></a>Power BI Premium Capacity Metrics に接続する

Premium 容量リソースを最適に利用するにはどうすればよいかを十分な情報に基づいて判断するには、ご利用の容量を監視することが不可欠です。 Power BI Premium Capacity Metrics アプリからは、ご利用の容量のパフォーマンスに関する非常に詳細な情報が提供されます。

![Power BI Premium Capacity Metrics アプリのレポート](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-report.png)

この記事では、アプリをインストールしてデータ ソースに接続する方法について説明します。 レポートの内容とその使用方法については、「[アプリで Premium 容量を監視する](../admin/service-admin-premium-monitor-capacity.md)」と [Premium Capacity Metrics アプリに関するブログ記事](https://powerbi.microsoft.com/blog/premium-capacity-metrics-app-new-health-center-with-kpis-to-explore-relevant-metrics-and-steps-to-mitigate-issues/)を参照してください。

アプリをインストールしてデータ ソースに接続した後は、必要に応じてレポートをカスタマイズできます。 その後、それを組織内の同僚に配布することができます。

> [!NOTE]
> テンプレート アプリをインストールするには[アクセス許可](./service-template-apps-install-distribute.md#prerequisites)が必要です。 十分なアクセス許可がないことがわかった場合は、Power BI 管理者にお問い合わせください。

## <a name="install-the-app"></a>アプリをインストールする

1. アプリにアクセスするには、次のリンクをクリックします: [Power BI Premium Capacity Metrics テンプレート アプリ](https://app.powerbi.com/groups/me/getapps/services/pbi_pcmm.capacity-metrics-dxt)

1. アプリの [AppSource] ページで、[ **[今すぐ入手する]**](https://app.powerbi.com/groups/me/getapps/services/pbi_pcmm.capacity-metrics-dxt) を選択します。

    [![AppSource での Power BI Premium Capacity Metrics アプリ](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-appsource-get-it-now.png)](https://app.powerbi.com/groups/me/getapps/services/pbi_pcmm.capacity-metrics-dxt)

1. **[インストール]** を選択します。 

    ![Power BI Premium Capacity Metrics アプリのインストール](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metric-select-install.png)

    > [!NOTE]
    > 以前にアプリをインストールしていた場合は、[そのインストールを上書きする](./service-template-apps-install-distribute.md#update-a-template-app)か、新しいワークスペースにインストールするかを確認するメッセージが表示されます。

    アプリがインストールされると、[アプリ] ページに表示されます。

   ![[アプリ] ページの Power BI Premium Capacity Metrics アプリ](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>データ ソースに接続する

1. [アプリ] ページでアイコンを選択して、アプリを開きます。

1. スプラッシュ スクリーンで、 **[探索]** を選択します。

   ![テンプレート アプリのスプラッシュ スクリーン](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-splash-screen.png)

   アプリが開き、サンプル データが表示されます。

1. ページの上部にあるバナーの **[データを接続]** リンクを選択します。

   ![Power BI Premium Capacity Metrics アプリの [データを接続] リンク](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-connect-data.png)

1. 表示されるダイアログ ボックスで、UTC オフセットを設定します。つまり、協定世界時とご自分の場所の時刻との差 (時間単位) です。 そして、 **[Next]** (次へ) をクリックします。
  
   ![Power BI Premium Capacity Metrics アプリの UTC 設定ダイアログ](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-setutc-dialog.png)
   **注意: 半時間の形式は、10 進数 (5.5、2.5 など) にする必要があります。**

1. 次に表示されるダイアログでは、何もする必要はありません。 単に **[サインイン]** を選択してください。

   ![Power BI Premium Capacity Metrics アプリの認証ダイアログ](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-authentication-dialog.png)

1. Microsoft サインイン画面で、Power BI にサインインします。

   ![Microsoft サインイン画面](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-microsoft-login.png)

   サインインした後、レポートがデータ ソースに接続され、最新のデータが設定されます。 この間は、利用状況モニターが作動します。

   ![Power BI Premium Capacity Metrics アプリの更新が進行中](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-refresh-monitor.png)

   レポート データは 1 日に 1 回自動的に更新されます (サインイン プロセス中にこれを無効にしていない限り)。 また、[独自の更新スケジュールを設定](./refresh-scheduled-refresh.md)し、必要に応じてレポート データを最新の状態に保つこともできます。

## <a name="customize-and-share"></a>カスタマイズと共有

アプリのカスタマイズを開始するには、右上隅にある鉛筆アイコンをクリックします。

 ![[編集] アイコン](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-customize.png)

詳細については、「[アプリをカスタマイズして共有する](./service-template-apps-install-distribute.md#customize-and-share-the-app)」を参照してください。

## <a name="next-steps"></a>次の手順
* [アプリで Premium 容量を監視する](../admin/service-admin-premium-monitor-capacity.md)
* [Premium Capacity Metrics アプリに関するブログ記事](https://powerbi.microsoft.com/blog/premium-capacity-metrics-app-new-health-center-with-kpis-to-explore-relevant-metrics-and-steps-to-mitigate-issues/)
* [Power BI テンプレート アプリとは](./service-template-apps-overview.md)
* [組織でテンプレート アプリをインストールして配布する](./service-template-apps-install-distribute.md)
* わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。