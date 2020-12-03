---
title: Power BI Windows アプリでオンプレミス レポートと KPI を表示する
description: Windows 10 用 Power BI モバイル アプリにより、タッチ対応のモバイルからオンプレミスの重要なビジネス情報に簡単にアクセスできるようになります。
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 05/19/2020
ms.openlocfilehash: eb6b86b2810609c0ad795190afc91c40677f5e70
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96413313"
---
# <a name="view-on-premises-reports-and-kpis-in-the-power-bi-windows-app"></a>Power BI Windows アプリでオンプレミス レポートと KPI を表示する
Windows 10 用 Power BI アプリを使って、タッチ対応のモバイルから、SQL Server 2016 Reporting Services のオンプレミスの重要なビジネス情報に簡単にアクセスできます。 

![Reporting Services のモバイル レポート](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report.png)

## <a name="first-things-first"></a>最初に行うこと
SQL Server 2016 Enterprise Edition Mobile Report Publisher で [Reporting Services のモバイル レポートを作成](/sql/reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher)し、[Reporting Services の Web ポータル](/sql/reporting-services/web-portal-ssrs-native-mode)にそのレポートを公開します。 KPI は Web ポータルで作成します。 作成したレポートと KPI を簡単に探せるように、フォルダーで整理したりお気に入りに追加したりします。 

Windows 10 用 Power BI アプリで、フォルダーやお気に入りに追加した KPS、モバイル レポート、Power BI レポートを表示します。 

> [!NOTE]
> デバイスで Windows 10 を実行している必要があります。 このアプリは、最低 1 GB RAM と 8 GB の内部記憶域を持つデバイスに適しています。

>[!NOTE]
>**Windows 10 Mobile を使用するスマートフォン** に対する Power BI モバイル アプリのサポートは、2021 年 3 月 16 日に廃止されます。 [詳細情報](/legal/powerbi/powerbi-mobile/power-bi-mobile-app-end-of-support-for-windows-phones)

## <a name="explore-samples-without-a-sql-server-2016-reporting-services-server"></a>SQL Server 2016 Reporting Services サーバーを使用せずにサンプルを参照する
Reporting Services の Web ポータルへのアクセス権がない場合でも、Reporting Services のモバイル レポートの機能を参照できます。

1. Windows 10 デバイスで Power BI アプリを開きます。
2. 左上隅にあるグローバル ナビゲーション ボタン ![グローバル ナビゲーション ボタン](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/powerbi_windows10_options_icon.png) をタップします。
3. **[設定]** アイコン ![[設定] アイコン](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-settings-icon.png) をタップし、 **[サーバーに接続]** を右クリックするかタップして長押しした後、 **[サンプルを表示]** をタップします。
   
   ![SSRS のサンプルを表示](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-win10-connect-ssrs-samples.png)
4. Retail Reports または Sales Reports フォルダーを開き、その KPI やモバイル レポートを調べます。
   
   ![KPI とモバイル レポートのサンプル](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-win10-ssrs-sample-kpis.png)

サンプルを参照して KPI とモバイル レポートを操作します。

## <a name="connect-to-a-reporting-services-report-server"></a>Reporting Services レポート サーバーに接続する
1. ナビ ペインの下部にある **[設定]** ![[設定] アイコン](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-settings-icon.png) をタップします
2. **[サーバーに接続]** をタップします。
3. サーバーのアドレス、ユーザー名、パスワードを入力します。 サーバーのアドレスには次の形式を使用します。
   
     `https://<servername>/reports` または `https://<servername>/reports`
   
   > [!NOTE]
   > 接続文字列の先頭に、**http** または **https** を含めてください。
   > 
   > 
   
    必要に応じて、 **[詳細オプション]** をタップしてサーバーの名前を指定します。
4. チェック マークをタップして接続します。 
   
   ナビ ペインに、サーバーが表示されます。
   
   ![ナビ ペインのサーバー](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-server.png)
   
   >[!TIP]
   >[グローバル ナビゲーション] ボタン ![[グローバル ナビゲーション] ボタン](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/powerbi_windows10_options_icon.png) をタップすると、Power BI サービスでいつでも Reporting Services のモバイル レポートとダッシュボードの間を行き来できます。 
   > 

   >[!NOTE]
   >カスタム ポートを使用して構成されたレポート サーバーはサポートされておらず、Power BI Windows アプリからはアクセスできません。 

## <a name="view-reporting-services-kpis-and-mobile-reports-in-the-power-bi-app"></a>Power BI アプリで Reporting Services の KPI とモバイル レポートを表示する
Reporting Services KPI、モバイル レポート、Power BI レポート (プレビュー) は、Reporting Services Web ポータル上で同じフォルダー内に表示されます。

![レポート フォルダー](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-folders.png)

* KPI をタップし、フォーカス モードで表示します。
  
    ![フォーカス モードの KPI](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-kpis.png)
* モバイル レポートをタップし、Power BI アプリを開いて対話します。
  
    ![Reporting Services のモバイル レポート](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report.png)

## <a name="view-your-favorite-kpis-and-reports"></a>お気に入りの KPI とレポートを表示する
Reporting Services Web ポータルで KPI、モバイル レポート、Power BI レポートをお気に入りに設定し、Power BI のお気に入りのダッシュボードやレポートと共に、Windows 10 デバイスの 1 つの便利なフォルダー内に表示できます。

* **[お気に入り]** をタップします。
  
   ![[お気に入り] アイコン](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-favorite-menu.png)
  
   Web ポータルでお気に入りに追加したアイテムは、すべてこのページに表示されます。
  
[Power BI モバイル アプリでのお気に入り](mobile-apps-favorites.md)の詳細については、こちらをご覧ください。

## <a name="remove-a-connection-to-a-report-server"></a>レポート サーバーへの接続を削除する
Power BI モバイル アプリから一度に接続できるのは、1 つのレポート サーバーだけです。 別のサーバーに接続する場合は、現在のサーバーを切断する必要があります。

1. ナビ ペインの下部にある **[設定]** ![[設定] アイコン](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-settings-icon.png) をタップします。
2. 接続を望まないサーバー名をタップしてそのまま押さえます。
3. **[サーバーの削除]** をタップします。
   
    ![サーバーの削除](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-windows-10-ssrs-remove-server-menu.png)

## <a name="create-reporting-services-mobile-reports-and-kpis"></a>Reporting Services のモバイル レポートと KPI を作成する
Power BI モバイル アプリでは、Reporting Services KPI とモバイル レポートを作成できません。 作成するには、SQL Server Mobile Report Publisher と SQL Server 2016 Reporting Services Web ポータルを使用します。

* [Reporting Services のモバイル レポートを作成](/sql/reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher)し、Reporting Services の Web ポータルに公開します。
* [Reporting Services の Web ポータルで KPI を作成](/sql/reporting-services/working-with-kpis-in-reporting-services)します

## <a name="next-steps"></a>次のステップ
* [Windows 10 用 Power BI モバイル アプリを使ってみる](mobile-windows-10-phone-app-get-started.md)  
* [Power BI とは?](../../fundamentals/power-bi-overview.md)  
* 疑問がある場合 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。