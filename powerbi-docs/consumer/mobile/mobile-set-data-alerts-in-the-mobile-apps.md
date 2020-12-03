---
title: Power BI モバイル アプリでデータ アラートを設定する
description: ユーザーが設定した制限を超えてダッシュボードのデータが変化したときにユーザーに通知するように、Power BI モバイル アプリでアラートを設定する方法を説明します。
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 12/11/2019
ms.openlocfilehash: 4e9820b8ebff411434d9d6c408f36a36a644ea9d
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418005"
---
# <a name="set-data-alerts-in-the-power-bi-mobile-apps"></a>Power BI モバイル アプリでデータ アラートを設定する
適用対象:

| ![iPhone](./media/mobile-set-data-alerts-in-the-mobile-apps/iphone-logo-50-px.png) | ![iPad](./media/mobile-set-data-alerts-in-the-mobile-apps/ipad-logo-50-px.png) | ![Android フォン](./media/mobile-set-data-alerts-in-the-mobile-apps/android-phone-logo-50-px.png) | ![Android タブレット](./media/mobile-set-data-alerts-in-the-mobile-apps/android-tablet-logo-50-px.png) | ![Windows 10 デバイス。](./media/mobile-set-data-alerts-in-the-mobile-apps/win-10-logo-50-px.png) |
|:--- |:--- |:--- |:--- |:--- |
| iPhone |iPad |Android フォン |Android タブレット |Windows 10 デバイス |

アラートは、Power BI モバイル アプリと Power BI サービスのダッシュボードで設定できます。 アラートは、ユーザーが設定した制限を超えてタイルのデータが変化したことをユーザーに通知します。 アラートは、カードやゲージなどの単一の数値を含むタイルに対して動作しますが、ストリーミング データでは動作しません。 モバイル デバイスで設定したデータ アラートを Power BI サービスで見ることができます。また、その逆も可能です。 ダッシュボードやタイルのスナップショットを共有する場合でも、設定したデータ アラートのみを表示できます。

Power BI Pro のライセンスがある場合、または共有ダッシュボードが Premium 容量である場合は、タイルにアラートを設定できます。 

> [!WARNING]
> データ ドリブン アラート通知は、データに関する情報を提供します。 デバイスが盗まれた場合、Power BI サービスに移動し、すべてのデータ ドリブン アラート ルールをオフにすることをお勧めします。 
> 
> 詳しくは、[Power BI サービスのデータ アラートの管理](../../create-reports/service-set-data-alerts.md)に関するページを参照してください。
> 
> 

## <a name="data-alerts-on-an-iphone-or-ipad"></a>iPhone または iPad でのデータ アラート
### <a name="set-an-alert-on-an-iphone-or-ipad"></a>iPhone または iPad でアラートを設定する
1. ダッシュボード内の数値タイルまたはゲージ タイルをタップしてフォーカス モードで開きます。  
   
   ![フォーカス モードのゲージ タイルを示すダッシュボードのスクリーンショット。](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-card-visual.png)
2. ベルのアイコン :::image type="icon" source="media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-alert-icon.png" border="false"::: をタップして、アラートを追加します。  
3. **[アラート ルールの追加]** をタップします。
   
   ![アラートが設定されていないことを示す、アラート ルールのスクリーンショット。](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-add-alert-rule.png)
4. 上限値または下限値のどちらでアラートを受け取るかを選択し、値を設定します。
   
   ![アラートのタイトルと設定する値を示す、アラート設定のスクリーンショット](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-set-alert-threshold.png)
5. アラートの受け取りを 1 時間単位または 1 日単位のどちらにするか、およびアラートと共に電子メールも受信するかどうかを決定します。
   
   > [!NOTE]
   > 期間中にデータが実際に更新されない限り、毎時間または毎日アラートを受け取ることはありません。
   > 
   > 
6. アラートのタイトルも変更できます。
7. **[保存]** をタップします。
8. 1 つのタイルに、上限と下限両方のしきい値のアラートを設定できます。 **[アラートの管理]** で **[アラート ルールの追加]** をタップします。
   
   ![アラート ルールを追加するためのポインターを示す、[アラートの管理] のスクリーンショット。](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-add-another-alert-rule.png)

### <a name="manage-alerts-on-your-iphone-or-ipad"></a>iPhone または iPad でアラートを管理する
モバイル デバイスでは個別のアラートを管理できますが、[Power BI サービスではすべてのアラートを管理](../../create-reports/service-set-data-alerts.md)できます。

1. ダッシュボードで、アラートのある数値タイルまたはゲージ タイルをタップします。  
   
   ![アラートが表示されている数値タイルを示す iPhone または iPad のダッシュボードのスクリーンショット。](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-card-visual_has_alert.png)

2. ベルのアイコン :::image type="icon" source="media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-has-alert-icon.png" border="false"::: をタップします。  
3. アラートの名前をタップして編集するか、スライダーをタップして電子メール アラートをオフにするか、ごみ箱をタップしてアラートを削除します。
   
    ![アラート名、アラートを削除するためのゴミ箱、アラートをオフにするためのスライドを指している、アラートのスクリーンショット。](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-edit-delete-alert.png)

## <a name="data-alerts-on-an-android-device"></a>Android デバイスでのデータ アラート
### <a name="set-an-alert-on-an-android-device"></a>Android デバイスでアラートを設定する
1. Power BI ダッシュボードで、数値タイルまたはゲージ タイルをタップして開きます。  
2. ベルのアイコン :::image type="icon" source="media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-alert-icon.png" border="false"::: をタップして、アラートを追加します。  
   
   ![アラートが表示されている数値タイルを示す Android デバイスのダッシュボードのスクリーンショット。](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-tap-alert.png)
3. プラスのアイコン [+] をタップします。
   
   ![プラス記号アイコンを指すポインターが示されている、[アラートの管理] のスクリーンショット。](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-plus-alert.png)
4. 上限値または下限値のどちらでアラートを受け取るかを選択し、値を入力します。
   
   ![[保存] と [完了] を指すポインターが示されている、アラート設定のスクリーンショット。](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-tablet-set-alert-condition.png)
5. **[完了]** をタップします。
6. アラートの受け取りを 1 時間単位または 1 日単位のどちらにするか、およびアラートと共に電子メールも受信するかどうかを決定します。
   
   > [!NOTE]
   > 期間中にデータが実際に更新されない限り、毎時間または毎日アラートを受け取ることはありません。
   > 
   > 
7. アラートのタイトルも変更できます。
8. **[保存]** をタップします。

### <a name="manage-alerts-on-an-android-device"></a>Android デバイスでアラートを管理する
Power BI モバイル アプリでは個別のアラートを管理でき、[Power BI サービスではすべてのアラートを管理](../../create-reports/service-set-data-alerts.md)できます。

1. ダッシュボードで、アラートのあるカード タイルまたはゲージ タイルをタップします。  
2. 塗りつぶされたベルのアイコン :::image type="icon" source="media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-filled-alert-bell.png" border="false"::: をタップします。  
3. アラートをタップして、値を変更したり、オフにしたりします。
   
    ![アラートを追加するためのプラス記号アイコンを示す、[アラートの管理] タイルのスクリーンショット。](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-manage-alerts.png)
4. 同じタイルに別のアラートを追加するには、プラス記号アイコン (+) をタップします。
5. アラートをすべて削除するには、ゴミ箱アイコンをタップします ![ゴミ箱アイコン](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-android-delete-alert-icon.png).

## <a name="data-alerts-on-a-windows-device"></a>Windows デバイスでのデータ アラート

>[!NOTE]
>**Windows 10 Mobile を使用するスマートフォン** に対する Power BI モバイル アプリのサポートは、2021 年 3 月 16 日に廃止されます。 [詳細情報](/legal/powerbi/powerbi-mobile/power-bi-mobile-app-end-of-support-for-windows-phones)

### <a name="set-data-alerts-on-a-windows-device"></a>Windows デバイスでデータ アラートを設定する
1. ダッシュボード内の数値タイルまたはゲージ タイルをタップして開きます。  
2. ベルのアイコン :::image type="icon" source="media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-alert-bell-off.png" border="false"::: をタップして、アラートを追加します。  
   
   ![アラートが表示されている数値タイルを示す Windows デバイスのダッシュボードのスクリーンショット。](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-tap-alert.png)
3. プラスのアイコン [+] をタップします。
   
   ![アラートが設定されていないことを示す、[アラートの管理] のスクリーンショット。](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-no-alerts-yet.png)
4. 上限値または下限値のどちらでアラートを受け取るかを選択し、値を入力します。
   
   ![アラートを編集するためのエントリを示す、アラート設定のスクリーンショット。](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-set-alert.png)
5. アラートの受け取りを 1 時間単位または 1 日単位のどちらにするか、およびアラートと共に電子メールも受信するかどうかを決定します。
   
   > [!NOTE]
   > 期間中にデータが実際に更新されない限り、毎時間または毎日アラートを受け取ることはありません。
   > 
   > 
6. アラートのタイトルも変更できます。
7. チェック マークをタップします。
8. 1 つのタイルに、上限と下限両方のしきい値のアラートを設定できます。 **[アラートの管理]** でプラス記号 [+] をタップします。
   
   ![アラートを追加するためのプラス記号を示す、[アラートの管理] のスクリーンショット。](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-add-another-alert.png)

### <a name="manage-alerts-on-a-windows-device"></a>Windows デバイスでアラートを管理する
Power BI モバイル アプリでは個別のアラートを管理でき、[Power BI サービスではすべてのアラートを管理](../../create-reports/service-set-data-alerts.md)できます。

1. ダッシュボードで、アラートのあるカード タイルまたはゲージ タイルをタップします。  
2. ベルのアイコン :::image type="icon" source="media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-alert-bell-on.png" border="false"::: をタップします。  
   
   ![アラートが表示されている数値タイルを示すダッシュボードのスクリーンショット。](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-has-alerts.png)
3. アラートをタップして、値を変更したり、オフにしたりします。
   
    ![アラートを追加するためのプラス記号を示す、[アラートの管理] のスクリーンショット。](media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-windows-10-add-another-alert.png)
4. アラートをまとめて削除するには、右クリックまたは長押しして、 **[削除]** をタップします。

## <a name="receiving-alerts"></a>アラートの受信
モバイル デバイスの Power BI [通知センター](mobile-apps-notification-center.md)または Power BI サービスで、アラートと共に、他のユーザーによって共有するように設定された新しいダッシュボードについての通知を受信します。

データ ソースは多くの場合、毎日更新するように設定されますが、さらに頻繁に更新されるものもあります。 ダッシュボードのデータが更新されるとき、追跡対象データがユーザー設定のしきい値のいずれかに達した場合は、いくつかの処理が行われます。

1. Power BI は、(オプションの選択に応じて) 前回のアラート送信から 1 時間以上または 24 時間以上経過しているかどうかを確認します。
   
   データがしきい値を超えている場合に限り、1 時間ごと、または 24 時間ごとに、アラートを受け取ります。
2. 電子メールを送信するようにアラートを設定した場合は、次のようなメールを受信します。
   
   ![アラートを示す電子メール通知のスクリーンショット。](media/mobile-set-data-alerts-in-the-mobile-apps/powerbi-alerts-email.png)
3. Power BI により、[通知センター](mobile-apps-notification-center.md)にメッセージが追加され、タイトル バーのベル アイコン :::image type="icon" source="media/mobile-set-data-alerts-in-the-mobile-apps/powerbi-alert-tile-notification-icon.png" border="false"::: (iOS と Android の場合) または![グローバル ナビゲーション ボタン](./media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-alert-global-nav-button.png) (Windows 10 デバイスの場合) に、黄色い点が追加されます。


4. ベル アイコン :::image type="icon" source="media/mobile-set-data-alerts-in-the-mobile-apps/powerbi-alert-tile-notification-icon.png" border="false"::: またはグローバル ナビゲーション ボタン ![グローバル ナビゲーション ボタン](./media/mobile-set-data-alerts-in-the-mobile-apps/power-bi-iphone-alert-global-nav-button.png) をタップして、[**通知センター** を開き](mobile-apps-notification-center.md)、アラートの詳細を表示します。
   
     

> [!NOTE]
> アラートは更新されたデータでのみ動作します。 データが更新されると、Power BI はそのデータにアラートが設定されているかどうかを確認します。 データがアラートのしきい値に達した場合、アラートがトリガーされます。
> 
> 

## <a name="tips-and-troubleshooting"></a>ヒントとトラブルシューティング
* 現在、Bing タイルまたは日付/時刻メジャーを含むカード タイルについては、アラートがサポートされていません。
* アラートは、数値データでのみ機能します。
* アラートは更新されたデータでのみ動作します。 静的データでは動作しません。
* アラートは、ストリーミング データを含むタイルでは機能しません。

## <a name="next-steps"></a>次の手順
* [Power BI サービスでアラートを管理する](../../create-reports/service-set-data-alerts.md)
* [Power BI モバイル通知センター](mobile-apps-notification-center.md)
* わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。