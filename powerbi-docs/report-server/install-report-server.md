---
title: Power BI レポート サーバーのインストール
description: Power BI レポート サーバーのインストール方法について説明します。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 03/14/2021
ms.openlocfilehash: bd71981466eb44bc74a2b6a272b738885a7a18ab
ms.sourcegitcommit: 9fd7fbcc819bee4a242cb786aad9e675ea83e83d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104834455"
---
# <a name="install-power-bi-report-server"></a>Power BI レポート サーバーのインストール

Power BI レポート サーバーのインストール方法について説明します。

## <a name="download-power-bi-report-server"></a>Power BI Report Server のダウンロード

「[Power BI Report Server によるオンプレミスでのレポート作成](https://powerbi.microsoft.com/report-server/)」ページで **[無料試用版をダウンロードする]** を選択します。

PowerBIReportServer.exe ファイルを実行するときは、無料試用版を選択するか、ご自分のプロダクト キーを入力します。 詳細をお読みください。

## <a name="before-you-install"></a>インストールする前に

Power BI Report Server をインストールする前に、「[Power BI レポート サーバーをインストールするためのハードウェアとソフトウェアの要件](system-requirements.md)」を確認することをお勧めします。

 > [!IMPORTANT]
 > Power BI Report Server は、読み取り専用ドメイン コントローラー (RODC) がある環境にインストールできます。ただし、Power BI Report Server が正常に機能するためには、読み取り/書き込みドメイン コントローラーにアクセスできることが必要です。 Power BI Report Server が RODC にしかアクセスできない場合は、サービスを管理しようとしたときにエラーが発生する可能性があります。

### <a name="power-bi-report-server-product-key"></a>Power BI Report Server のプロダクト キー

Power BI Report Server のプロダクト キーは、次の 2 つの異なるソースから取得できます。

- Power BI Premium
- SQL Server Enterprise Software Assurance (SA)

詳細をお読みください。

#### <a name="power-bi-premium"></a>Power BI Premium

Power BI Premium を購入した場合は、Power BI 管理者ポータルの **[Premium 設定]** タブ内で、Power BI Report Server のプロダクト キーにアクセスできます。 管理ポータルを利用できるのは、グローバル管理者、または Power BI サービス管理者ロールが割り当てられているユーザーに限られます。

![Premium の設定](../report-server/media/install-report-server/pbirs-product-key.png "Premium 設定の Power BI Report Server キー")

**[Power BI Report Server キー]** を選択すると、プロダクト キーを含むダイアログが表示されます。 これをコピーして、インストールで使用することができます。

![プロダクト キー](../report-server/media/install-report-server/pbirs-product-key-dialog.png "Power BI Report Server のプロダクト キー")

#### <a name="sql-server-enterprise-software-assurance-sa"></a>SQL Server Enterprise Software Assurance (SA)

SQL Server Enterprise SA 契約がある場合は、[ボリューム ライセンス サービス センター](https://www.microsoft.com/Licensing/servicecenter/)からプロダクト キーを取得できます。

 > [!IMPORTANT]
 > スケールアウト シナリオのために Power BI Report Server を複数のサーバーにインストールしている場合は、すべてのサーバーで同じ Power BI Premium プロダクト キーまたは SQL Server Enterprise ソフトウェア アシュアランス (SA) プロダクト キーを使用する必要があります。

## <a name="install-your-report-server"></a>レポート サーバーのインストール

Power BI Report Server のインストールは簡単です。 ファイルのインストールはわずかな手順だけです。

インストール時に SQL Server データベース エンジン サーバーが使用可能になっている必要はありません。 インストール後に Reporting Services を構成する必要があります。

1. PowerBIReportServer.exe の場所を検索し、インストーラーを起動します。

2. **[Install Power BI Report Server]** \(Power BI レポート サーバーのインストール\) を選択します。

    ![Power BI レポート サーバーのインストール](media/install-report-server/pbireportserver-install.png)
3. インストールするエディションを選択し、 **[次へ]** を選択します。

    ![エディションの選択](media/install-report-server/pbireportserver-choose-edition.png)

    評価エディションまたは開発者エディションのいずれかを選択できます。

    ![エディション 2](media/install-report-server/pbireportserver-choose-edition2.png)

    それ以外の場合、Power BI サービスまたはボリューム ライセンス サービス センターから取得したプロダクト キーを入力します。 プロダクト キーを取得する方法の詳細については、前述の「[インストールする前に](#before-you-install)」セクションを参照してください。
4. ライセンス条件を読んで同意してから、 **[次へ]** を選択します。

    ![ライセンス条項](media/install-report-server/pbireportserver-eula.png)
5. レポート サーバー データベースを格納するためのデータベース エンジンを使用できる必要があります。 **[次へ]** を選択し、レポート サーバーのみをインストールします。

    ![ファイルのみをインストールする](media/install-report-server/pbireportserver-install-files-only.png)
6. レポート サーバーのインストール場所を指定します。 **[インストール]** を選択して続行します。

    ![インストール先のパスを指定する](media/install-report-server/pbireportserver-install-file-path.png)

    既定のパスは、C:\Program Files\Microsoft Power BI Report Server です。

7. 正常にセットアップした後で、 **[Configure Report Server]** \(レポート サーバーの構成\) を選択し、Reporting Services 構成マネージャーを起動します。

    ![レポート サーバーを構成する](media/install-report-server/pbireportserver-configure.png)

## <a name="configure-your-report-server"></a>自分のレポート サーバーを構成する

セットアップで **[レポート サーバーの構成]** を選択すると、Reporting Services Configuration Manager が表示されます。 詳細については、「[Reporting Services Configuration Manager](/sql/reporting-services/install-windows/reporting-services-configuration-manager-native-mode)」(Reporting Services 構成マネージャー) を参照してください。

Reporting Services の初期構成を完了するには、[レポート サーバー データベースを作成](/sql/reporting-services/install-windows/ssrs-report-server-create-a-report-server-database)します。 この手順を完了するには、SQL Server データベース サーバーが必要です。

### <a name="creating-a-database-on-a-different-server"></a>別のサーバーでデータベースを作成する

別のコンピューター上のデータベース サーバーでレポート サーバー データベースを作成する場合は、レポート サーバーのサービス アカウントをデータベース サーバー上で認識される資格情報に変更します。 

既定では、レポート サーバーは、仮想サービス アカウントを使用します。 別のサーバーにデータベースを作成しようとすると、接続の権限の適用手順で次のエラーが発生することがあります。

`System.Data.SqlClient.SqlException (0x80131904): Windows NT user or group '(null)' not found. Check the name again.`

エラーを回避するには、サービス アカウントをネットワーク サービスまたはドメイン アカウントのいずれかに変更できます。 ネットワーク サービスにサービス アカウントを変更すると、レポート サーバーのコンピューター アカウントのコンテキストで権限が適用されます。

![レポート サーバー サービス アカウントを構成する](media/install-report-server/pbireportserver-configure-account.png)

詳細については、[レポート サーバー サービス アカウントの構成](/sql/reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager)に関するページを参照してください。

## <a name="windows-service"></a>Windows サービス

Windows サービスは、インストールの一部として作成されます。 **Power BI レポート サーバー** として表示されます。 サービス名は **PowerBIReportServer** です。

![レポート サーバー Windows サービス](media/install-report-server/pbireportserver-windows-service.png)

![レポート サーバー Windows サービスのプロパティ](media/install-report-server/pbireportserver-windows-service2.png)

## <a name="default-url-reservations"></a>既定の URL 予約

URL 予約は、プレフィックス、ホスト名、ポート、および仮想ディレクトリから構成されます。

| パーツ | 説明 |
| --- | --- |
| プレフィックス |既定のプレフィックスは HTTP です。 以前に SSL (Secure Sockets Layer) 証明書をインストールした場合は、HTTPS プレフィックスを使用する URL 予約がセットアップで作成されます。 |
| ホスト名 |既定のホスト名は、厳密なワイルドカード (+) です。 これにより、コンピューターに対して解決されるあらゆるホスト名 (`https://<computername>/reportserver`、`https://localhost/reportserver`、`https://<IPAddress>/reportserver.`) の指定のポートで、レポート サーバーが HTTP 要求を受け付けるように指定されます。 |
| Port |既定のポートは 80 です。 ポート 80 以外のポートを使用する場合は、ブラウザー ウィンドウで Web ポータルを開くときに、それを URL に明示的に追加する必要があります。 |
| 仮想ディレクトリ |既定では、仮想ディレクトリは、レポート サーバー Web サービス用に ReportServer の形式で、Web ポータル用に Reports の形式で作成されます。 レポート サーバー Web サービスの場合、既定の仮想ディレクトリは **reportserver** です。 Web ポータルの場合、既定の仮想ディレクトリは **reports** です。 |

完全な URL 文字列の例は次のようになることがあります。

* `https://+:80/reportserver`、レポート サーバーへのアクセスを提供します。
* `https://+:80/reports` は、Web ポータルへのアクセスを提供します。

## <a name="firewall"></a>ファイアウォール

リモート コンピューターからレポート サーバーにアクセスする場合、ファイアウォールがある場合は、ファイアウォール規則を構成したことを確認します。

Web サービスの URL と Web ポータルの URL 用に構成した TCP ポートを開きます。 既定では、TCP ポート 80 に対して構成されます。

## <a name="additional-configuration"></a>追加の構成

* Power BI サービスとの統合を構成し、Power BI ダッシュボードにレポート アイテムを固定できるようにするには、「[Integrate with the Power BI service](/sql/reporting-services/install-windows/power-bi-report-server-integration-configuration-manager) 」(Power BI サービスとの統合) を参照してください。
* サブスクリプション処理の電子メールを構成するには、「[電子メールの設定 - Reporting Services のネイティブ モード (構成マネージャー)](/sql/reporting-services/install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager)」および[レポート サーバーの電子メール配信](/sql/reporting-services/subscriptions/e-mail-delivery-in-reporting-services)に関するページを参照してください。
* レポート コンピューターで Web ポータルにアクセスしてレポートを表示および管理できるように Web ポータルを構成するには、「[Configure a firewall for report server access](/sql/reporting-services/report-server/configure-a-firewall-for-report-server-access)」 (レポート サーバーにアクセスするためのファイアウォールを構成する) と「[Configure a Report Server for Remote Administration](/sql/reporting-services/report-server/configure-a-report-server-for-remote-administration)」 (リモート管理用にレポート サーバーを構成する) を参照してください。
* SQL Server Management Studio でのレポート サーバー システム プロパティの設定の詳細については、「[サーバーのプロパティの [詳細設定] ページ](/sql/reporting-services/tools/server-properties-advanced-page-reporting-services)」を参照してください。 特に指定しない限り、オプションは Power BI Report Server と SQL Server Reporting Services の両方に適用されます。

## <a name="next-steps"></a>次のステップ

[管理者の概要](admin-handbook-overview.md)  
[レポート サーバーのプロダクト キーを検索する方法](find-product-key.md)  
[Power BI Report Server 向け Power BI Desktop をインストールする](install-powerbi-desktop.md)  
[レポート サービスのインストールを確認する](/sql/reporting-services/install-windows/verify-a-reporting-services-installation)  
[レポート サーバー サービス アカウントを構成する](/sql/reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager)  
[レポート サーバーの URL を構成する](/sql/reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager)  
[レポート サーバー データベース接続を構成する](/sql/reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager)  
[レポート サーバーを初期化する](/sql/reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server)  
[レポート サーバーで SSL 接続を構成する](/sql/reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server)  
[Windows サービス アカウントとアクセス許可を構成する](/sql/database-engine/configure-windows/configure-windows-service-accounts-and-permissions)  
[Power BI レポート サーバーのブラウザーのサポート](browser-support.md)

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
