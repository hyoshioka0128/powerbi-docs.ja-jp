---
title: Xero コンテンツ パックの資格情報を更新する方法
description: Xero Power BI コンテンツ パックを使用している場合は、最近の Power BI サービス インシデントによって、コンテンツ パックの毎日の更新で問題が発生する可能性があります。
author: paulinbar
ms.author: painbar
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 08/10/2017
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 972340d4c9cca4507308aaac4c07f410ff8fc6fe
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96392107"
---
# <a name="how-to-refresh-your-xero-content-pack-credentials-if-refresh-failed"></a>更新が失敗した場合に Xero コンテンツ パックの資格情報を更新する方法
Xero Power BI コンテンツ パックを使用している場合は、最近の Power BI サービス インシデントによって、コンテンツ パックの毎日の更新で問題が発生する可能性があります。

以下のスクリーンショットに示すように、Xero データセットの前回の更新の状態を確認すると、コンテンツ パックが正常に更新されたかどうかを確認できます。

![Xero ダイアログのスクリーンショット。Xero データセットの更新の状態が表示されています。](media/service-refresh-xero-credentials/powerbi-xero-refresh-failed.png)

このように更新が失敗したことが示されている場合は、以下の手順に従ってコンテンツ パックの資格情報を更新してください。

1. Xero データセットの横にある **その他のオプション** (...) をクリックし、 **[更新のスケジュール設定]** をクリックします。 Xero コンテンツ パックの設定ページが開きます。
   
    ![Xero ダイアログのスクリーンショット。[更新のスケジュール設定] の選択が表示されています。](media/service-refresh-xero-credentials/powerbi-xero-schedule-refresh.png)
2. **[Settings for Xero]** (Xero の設定) ページで、 **[データ ソースの資格情報]**  >  **[資格情報を編集]** を選びます。
   
    ![[Xero Settings]\(Xero の設定\) ダイアログのスクリーンショット。[資格情報を編集] が選択された [Settings for Xero]\(Xero の設定\) が表示されています。](media/service-refresh-xero-credentials/powerbi-xero-settings-page.png)
3. 組織の名前を入力し、 **[次へ]** を選びます。
   
    ![[Configure Xero]\(Xero の構成\) ダイアログのスクリーンショット。組織の名前が表示されています。](media/service-refresh-xero-credentials/powerbi-xero-configure.png)
4. Xero アカウントでサインインします。
   
    ![Xero サインイン ダイアログのスクリーンショット。Xero アカウントにサインインする方法が示されています。](media/service-refresh-xero-credentials/powerbi-xero-welcome.png)
5. これで資格情報が更新されました。次に、更新スケジュールが毎日実行されるように設定されていることを確認しましょう。 Xero データセットの横にある **その他のオプション** (...) をクリックし、 **[更新のスケジュール設定]** をもう一度クリックして確認できます。
   
    ![[更新のスケジュール設定] ダイアログのスクリーンショット。更新頻度とタイムゾーンが表示されています。](media/service-refresh-xero-credentials/powerbi-xero-refresh-schedule.png)
6. 直ちにデータセットを更新することもできます。 Xero データセットの横にある **その他のオプション** (...) をクリックし、 **[今すぐ更新]** をクリックします。
   
    ![Xero ダイアログのスクリーンショット。[今すぐ更新] が選択されています。](media/service-refresh-xero-credentials/powerbi-xero-refresh-now.png)

更新の問題が解決しない場合は、[https://support.powerbi.com](https://support.powerbi.com) からお問い合わせください。 

Power BI 用 Xero コンテンツ パックの詳細については、[Xero コンテンツ パックのヘルプ ページ](service-connect-to-xero.md)を参照してください。

### <a name="next-steps"></a>次の手順
* 他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。

