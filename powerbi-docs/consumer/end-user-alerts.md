---
title: 'チュートリアル: Power BI サービス ダッシュボードでデータ アラートを設定する'
description: このチュートリアルでは、Microsoft Power BI サービスで設定した制限を超えてダッシュボード内のデータが変更された場合に通知されるように、アラートを設定する方法について説明します。
author: mihart
ms.author: mihart
ms.reviewer: mihart
featuredvideoid: removed
ms.service: powerbi
ms.subservice: pbi-explore
ms.topic: how-to
ms.date: 08/05/2020
LocalizationGroup: Dashboards
ms.openlocfilehash: be3ed6d8a836b626ba26e5e9acce7f0f2df3c6ea
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96391992"
---
# <a name="tutorial-set-alerts-on-power-bi-dashboards"></a>チュートリアル:Power BI ダッシュボードでアラートを設定する

[!INCLUDE[consumer-appliesto-yynn](../includes/consumer-appliesto-yynn.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

設定した制限を上回って、または下回ってダッシュボードのデータが変化したときにユーザーに通知するように、Power BI サービスでアラートを設定します。 アラートは、レポートのビジュアルからピン留めされたタイルでのみ、ゲージ、KPI、カードに対してだけ設定できます。 

![タイル、カード、KPI](media/end-user-alerts/card-gauge-kpi.png)

アラートは次のダッシュボード上で作成できます。
- 作成し、**マイ ワークスペース** に保存したダッシュボード。
- [Premium 容量](end-user-license.md)で共有しているダッシュボード。 
- Power BI Pro ライセンスを持っている場合、アクセスできる任意のワークスペースにあるダッシュボード。    

アラートは更新されたデータでのみ動作します。 データが更新されると、Power BI はそのデータにアラートが設定されているかどうかを確認します。 データがアラートのしきい値に達した場合、アラートがトリガーされます。 

この機能は進化し続けているため、[次の「ヒントとトラブルシューティング」セクション](#tips-and-troubleshooting)を参照してください。



ダッシュボードを共有している場合であっても、見ることができるのは自分で設定したアラートだけです。 データ アラートはプラットフォーム間で完全に同期されます。[Power BI モバイル アプリ](mobile/mobile-set-data-alerts-in-the-mobile-apps.md)および Power BI サービスで、データ アラートを設定して表示できます。 

> [!WARNING]
> これらのアラートは、データに関する情報を提供します。 モバイル デバイスで Power BI データを参照していて、そのデバイスが盗まれた場合、Power BI サービスを使用してすべてのアラートをオフにすることをお勧めします。
> 

このチュートリアルでは、以下について説明します。
> [!div class="checklist"]
> * 通知を設定できるユーザー
> * アラートをサポートするビジュアル
> * アラートが表示される対象のユーザー
> * Power BI Desktop およびモバイルでアラートを操作する
> * アラートの作成方法
> * アラートを受信する場所

## <a name="prerequisites"></a>必須コンポーネント

Power BI にサインアップしていない場合は、[無料の試用版にサインアップ](https://app.powerbi.com/signupredirect?pbi_source=web)してください。

1. この例では、営業とマーケティングのサンプルのダッシュボード カード タイルを使用しています。 Power BI service (app.powerbi.com) を開き、サインインし、 **[マイ ワークスペース]** を開きます。    
    ![マイ ワークスペースを開く](media//end-user-alerts/power-bi-my-workspace.png)

2. 左下隅にある **[データの取得]** を選びます。

    ![[データを取得] を選択](media//end-user-alerts/power-bi-get-data.png)

3. 表示された [データを取得] ページで、 **[サンプル]** を選択します。

4. [売上およびマーケティングのサンプル] を選択し、 **[接続]** を選択します。

    ![売上およびマーケティングのサンプルをダウンロードする](media//end-user-alerts/power-bi-sample.png)

5. Power BI がサンプルに接続されたら、表示されたダイアログから **[ダッシュボードに移動]** を選択します。     
    ![売上およびマーケティングのサンプルを開く](media//end-user-alerts/power-bi-go-to-dashboard.png)

## <a name="add-an-alert-to-a-dashboard-tile"></a>ダッシュボード タイルにアラートを追加する

1. ダッシュボードのゲージ、KPI、またはカード タイルで、省略記号を選びます。
   
   ![カード タイル](media/end-user-alerts/power-bi-card.png)

2. アラートのアイコン ![アラート アイコン](media/end-user-alerts/power-bi-alert-icon.png)、または **[アラートの管理]** を選択して、 **[マーケット シェア]** カードに 1 つまたは複数のアラートを追加します。

   ![省略記号が選択されているカード タイル](media/end-user-alerts/power-bi-manage.png)

   
1. **[アラートの管理]** ウィンドウで、 **[+ アラート ルールの追加]** を選択します。  スライダーが **[オン]** に設定されていることを確認し、アラートのタイトルを指定します。 タイトルは、アラートの内容を簡単に理解するために役立ちます。
   
   ![[アラート ルールの追加] ウィンドウ](media/end-user-alerts/power-bi-alert-manage.png)
4. 下にスクロールして、アラートの詳細を入力します。  この例では、市場シェアが 40 以上になった場合に 1 日に 1 回通知するアラートを作成します。 アラートは[通知センター](end-user-notification-center.md)に表示されます。 電子メールの送信も設定します。
   
   ![アラート管理ウィンドウ、しきい値の設定](media/end-user-alerts/power-bi-manage-alert-detail.png)

5. **[保存して閉じる]** を選びます。
 


   > 

## <a name="receiving-alerts"></a>アラートの受信
追跡対象データがユーザー設定のしきい値のいずれかに達した場合は、いくつかの処理が行われます。 最初に、最後のアラートが送信されてから 1 時間以上または 24 時間以上 (選択したオプションによって異なる) 経過しているかどうかが確認されます。 データがしきい値を超えている場合に限り、アラートを受け取ります。

次に、Power BI によりアラートが通知センターに送信され、さらにオプションで電子メールでもアラートが送信されます。 各アラートにはデータへの直接リンクが含まれています。 リンクを選択して、関連するタイルを表示します。  

1. 電子メールを送信するようにアラートを設定した場合は、次のようなメールを受信します。 これは、 **[センチメント]** カードに設定したアラートです。
   
   ![アラート メール](media/end-user-alerts/power-bi-email.png)
2. Power BI からは **通知センター** にメッセージも追加されます。
   
   ![Power BI サービスの通知アイコン](media/end-user-alerts/power-bi-task.png)
3. アラートの詳細を見るには通知センターを開きます。
   
    ![アラートを読む](media/end-user-alerts/power-bi-notifications.png)
   
  

## <a name="managing-alerts"></a>アラートの管理

アラートを管理するには多くの方法があります。ダッシュボードのタイル自体、Power BI の [設定] メニュー、[iPhone の Power BI モバイル アプリ](mobile/mobile-set-data-alerts-in-the-mobile-apps.md)または [Windows 10 用の Power BI モバイル アプリ](mobile/mobile-set-data-alerts-in-the-mobile-apps.md)の個別のタイルなどで管理できます。

### <a name="from-the-tile-itself"></a>タイル自体から

1. タイルのアラートを変更または削除する必要がある場合は、アラートのアイコン ![アラート アイコン](media/end-user-alerts/power-bi-alert-icon.png) を選択して **[アラートの管理]** ウィンドウを再び開きます。 そのタイルに設定されているすべてのアラートが表示されます。
   
    ![アラート管理ウィンドウ](media/end-user-alerts/power-bi-manage-alert.png).
2. アラートを変更するには、アラート名の左側にある矢印を選択します。
   
    ![アラート名の横の矢印](media/end-user-alerts/power-bi-alert-modify.png).
3. アラートを削除するには、アラート名の右側にあるごみ箱を選択します。
   
      ![選択されたごみ箱アイコン](media/end-user-alerts/power-bi-delete.png)

### <a name="from-the-power-bi-settings-menu"></a>Power BI の [設定] メニューから

1. Power BI のメニュー バーで歯車アイコンを選択します。
   
    ![歯車アイコン](media/end-user-alerts/power-bi-gear-icon.png).
2. **[設定]** の **[アラート]** を選択します。
   
    ![[設定] ウィンドウの [アラート] タブ](media/end-user-alerts/power-bi-settings.png)
3. ここからは、アラートをオンまたはオフにしたり、 **[アラートの管理]** ウィンドウを開いて変更を行ったり、アラートを削除したりできます。

## <a name="tips-and-troubleshooting"></a>ヒントとトラブルシューティング 

* ゲージ、KPI、またはカードに対してアラートを設定できない場合、Power BI 管理者または IT ヘルプ デスクに問い合わせてください。 ダッシュボードまたは特定の種類のダッシュボード タイルでは、アラートがオフになっているか、使用できないことがあります。
* アラートは更新されたデータでのみ動作します。 静的データでは動作しません。 Microsoft が提供する多くのサンプルは、静的なものです。 
* 共有コンテンツを受け取ったり、表示したりするには、Power BI Pro または Premium ライセンスが必要です。 詳細については、[お使いのライセンスの種類](end-user-license.md)に関するページを参照してください。
* アラートは、レポートからダッシュボードにピン留めされたストリーミング データセットから作成されたビジュアルに対して設定できます。 **[タイルの追加]**  >  **[カスタム ストリーミング データ]** を使用して、ダッシュボード上に直接作成されたストリーミング タイルにアラートを設定することはできません。


## <a name="clean-up-resources"></a>リソースをクリーンアップする
アラートを削除する手順については、上記で説明しています。 手短に言えば、Power BI のメニュー バーで歯車アイコンを選択します。 **[設定]** で **[アラート]** を選択し、アラートを削除します。

> [!div class="nextstepaction"]
> [モバイル デバイスでデータ アラートを設定する](mobile/mobile-set-data-alerts-in-the-mobile-apps.md)


