---
title: Power BI Report Server でスケジュールされた更新をトラブルシューティングする
description: この記事では、Power BI Report Server でスケジュールされた更新に関する問題のトラブルシューティングに利用できるリソースについて説明します。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: troubleshooting
ms.date: 11/01/2017
ms.openlocfilehash: 8cb8bf4e6d67f01f7bbdc4370d8a60691dba5a63
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418281"
---
# <a name="troubleshoot-scheduled-refresh-in-power-bi-report-server"></a>Power BI Report Server でスケジュールされた更新をトラブルシューティングする
この記事では、Power BI Report Server でスケジュールされた更新に関する問題のトラブルシューティングに利用できるリソースについて説明します。

この記事は、問題が発生すると役立つ情報で更新されます。

## <a name="common-issues"></a>一般的な問題
レポートの更新をスケジュールするときに発生する一般的な問題を次に示します。 

### <a name="driver-related-problems"></a>ドライバーに関連する問題
異なるデータ ソースに正常に接続するには、サード パーティ製ドライバーのインストールが必要になる場合があります。 Power BI Desktop を使っているコンピューターにインストールする必要があるだけでなく、レポート サーバーにもドライバーをインストールする必要があります。

ドライバーは、32 ビットと 64 ビットの両方で提供される場合もあります。 Power BI Report Server は 64 ビットなので、64 ビットのドライバーをインストールしてください。

サード パーティ製ドライバーをインストールして構成する方法については、製造元にお問い合わせください。

### <a name="memory-pressure"></a>メモリ不足
レポートの処理と表示に多くのメモリが必要な場合、メモリ不足が発生する可能性があります。 レポートのスケジュールされた更新には、コンピューターで大量のメモリが必要になる場合があります。 大きいレポートの場合は特にそうです。 メモリ不足の結果として、レポートが失敗するだけでなく、レポート サーバー自体がクラッシュする可能性があります。

メモリ不足が頻繁に発生する場合は、レポート サーバーのデプロイをスケールアウトしてリソースの負荷を分散させると有効な場合があります。 rsreportserver.config の `IsDataModelRefreshService` の設定を使って、データ更新に特定のレポート サーバーが使われるように定義することもできます。この設定を使うと、1 台以上のサーバーをオンデマンド レポート処理用のフロントエンド サーバーとして定義し、他のサーバーをスケジュールされた更新だけに使うことができます。

Analysis Services インスタンスを監視する方法については、「[Monitor an Analysis Services Instance](/sql/analysis-services/instances/monitor-an-analysis-services-instance)」(Analysis Services インスタンスを監視する) をご覧ください。

Analysis Services 内のメモリ設定については、「[Memory Properties](/sql/analysis-services/server-properties/memory-properties)」(メモリのプロパティ) をご覧ください。

### <a name="kerberos-configuration"></a>Kerberos の構成
Windows 資格情報でデータ ソースに正常に接続するには、Kerberos の制約付き委任の構成が必要な場合があります。 Kerberos の制約付き委任を構成する方法については、「[Power BI レポートを使用するために Kerberos を構成する](configure-kerberos-powerbi-reports.md)」をご覧ください。

## <a name="known-issues"></a>既知の問題
既知の問題に関する情報が利用できるようになったときは、ここに掲載されます。

## <a name="configuration-settings"></a>構成の設定
次の設定を使って、スケジュールされた更新を制御できます。 SQL Server Management Studio (SSMS) で行った設定は、スケールアウト配置内のすべてのレポート サーバーに適用されます。 rsreportserver.config 内で構成されている設定は、それが設定されている特定のサーバーに対するものです。

**SSMS 内での設定:**

| 設定 | Description |
| --- | --- |
| MaxFileSizeMb |アップロードされるレポートの最大ファイル サイズです。 既定値は 1000 MB (1 GB) です。 最大値は 2000 MB (2 GB) です。 |
| ModelCleanupCycleMinutes |モデルをメモリから削除するかどうかを確認する頻度を定義します。 既定値は 15 分です。 |
| ModelExpirationMinutes |モデルが最後に使われてから期限切れになって削除されるまでの時間を定義します。 既定値は 60 分です。 |
| ScheduleRefreshTimeoutMinutes |モードのデータ更新にかける時間を定義します。 既定値は 120 分です。 上限はありません。 |

**rsreportserver.config 内での設定:**

```xml
<Configuration>
    <Service>
        <PollingInterval>10</PollingInterval>
        <IsDataModelRefreshService>false</IsDataModelRefreshService>
        <MaxQueueThreads>0</MaxQueueThreads>
    </Service>
</Configuration>
```

## <a name="tools-for-troubleshooting"></a>トラブルシューティングするためのツール
### <a name="logs-relevant-for-scheduled-refresh-of-power-bi-reports"></a>Power BI レポートのスケジュールされた更新に関連するログ
スケジュールされた更新に関する情報を保持するログ ファイルは、RSPowerBI_ log です。 このファイルは、レポート サーバーのインストール場所の LogFiles フォルダーにあります。 

```
C:\Program Files\Microsoft Power BI Report Server\PBIRS\LogFiles\RSPowerBI_*.log
```

**エラー状態**

```
2017-10-20 02:00:09.5188|ERROR|744|Error Processing Data Model Refresh: SessionId: e960c25e-ddd4-4763-aa78-0e5dceb53472, Status: Error Model can not be refreshed because not all the data sources are embedded, Exception Microsoft.PowerBI.ReportServer.AsServer.InvalidDataSourceException: Model can not be refreshed because not all the data sources are embedde
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.AnalysisServicesDataRefresh.CanModelRefresh(IEnumerable`1 dataSources)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<>c__DisplayClass7.<ExecuteActionWithLogging>b__5()
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<ExecuteFuncWithLogging>d__1`1.MoveNext()
```

"**_成功した更新_* _"

```
2017-10-25 15:23:41.9370|INFO|6|Handling event with data: TimeEntered: 10/25/2017 8:23:41 PM, Type: Event, SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, EventType: DataModelRefresh
2017-10-25 15:23:41.9370|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Data Refresh.
2017-10-25 15:23:41.9370|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Retrieving PBIX AsDatabaseInfo.
2017-10-25 15:23:42.7134|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Verifying all the data sources are embedded.
2017-10-25 15:23:42.7134|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Verifying connection strings are valid.
2017-10-25 15:23:42.7134|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Streaming model to Analysis Server.
2017-10-25 15:23:42.7603|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Refreshing the model.
2017-10-25 15:23:51.5258|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Removing credentials from the model.
2017-10-25 15:23:51.6508|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Saving model to the catalog.
```

_ *正しくない資格情報**

```
2017-10-20 08:22:01.5595|INFO|302|Processing Data Model Refresh: SessionId: 22cd9ec3-b21a-4eb1-81ae-15fac8d379ea, Status: Starting Refreshing the model.
2017-10-20 08:22:02.3758|ERROR|302|Error Processing Data Model Refresh: SessionId: 22cd9ec3-b21a-4eb1-81ae-15fac8d379ea, Status: Error Failed to refresh the model, Exception Microsoft.AnalysisServices.OperationException: Failed to save modifications to the server. Error returned: 'The credentials provided for the SQL source are invalid. (Source at rosecatalog;reportserver.). The exception was raised by the IDbCommand interface.
'.
   at Microsoft.AnalysisServices.Tabular.Model.SaveChanges(SaveOptions saveOptions)
   at Microsoft.PowerBI.ReportServer.AsServer.TOMWrapper.RefreshModel(Database database)
   at Microsoft.PowerBI.ReportServer.AsServer.AnalysisServicesServer.RefreshDatabase(String databaseName, IEnumerable`1 dataSources)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.AnalysisServicesDataRefresh.RefreshDatabase(AsDatabaseInfo asDatabaseInfo)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<>c__DisplayClass7.<ExecuteActionWithLogging>b__5()
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<ExecuteFuncWithLogging>d__1`1.MoveNext()
2017-10-20 08:22:02.4588|ERROR|302|Error Processing Data Model Refresh: SessionId: 22cd9ec3-b21a-4eb1-81ae-15fac8d379ea, Status: Error Failed Data Refresh, Exception Microsoft.AnalysisServices.OperationException: Failed to save modifications to the server. Error returned: 'The credentials provided for the SQL source are invalid. (Source at rosecatalog;reportserver.). The exception was raised by the IDbCommand interface.
'.
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.ExecuteActionWithLogging(Action methodToExecute, String description, String localizedDescription, String messageInFailure, RefreshInfo refreshInfo, DataAccessors dataAccessors, ReportEventType operation, Int64 size, Boolean isDataRetrieval, Boolean showInExecutionLog)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.AnalysisServicesDataRefresh.RefreshData(RefreshInfo refreshInfo)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<>c__DisplayClass7.<ExecuteActionWithLogging>b__5()
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<ExecuteFuncWithLogging>d__1`1.MoveNext()
```

#### <a name="enabling-verbose-logging"></a>詳細ログを有効にする
Power BI Report Server で詳細ログを有効にする方法は、SQL Server Reporting Services の場合と同じです。

1. `<install directory>\PBIRS\ReportServer\bin\ReportingServicesService.exe.config` を開きます。
2. `<system.diagnostics>` で、**DefaultTraceSwitch** を **4** に変更します。
3. `<RStrace>` で、**Components** を **all:4** に変更します。 

### <a name="executionlog"></a>ExecutionLog
Power BI レポートがレンダリングされるとき、またはスケジュールされた更新計画が実行されるときは常に、データベースの実行ログに新しいエントリが追加されます。 これらのエントリは、レポート サーバー カタログ データベースの **ExecutionLog3** ビューで使用できます。

Power BI レポートの実行ログのエントリは、他のレポート種類のエントリと異なります。

* TimeRendering 列は常に 0 です。 Power BI レポートのレンダリングは、サーバーではなくブラウザーで行われます。
* 2 つの要求の種類と後続の項目アクションがあります。
  * **Interactive**: レポートが表示されているとき。
    * **ASModelStream**: データ モデルがカタログから Analysis Services にストリーミングされているとき。
    * **ConceptualSchema**: ユーザーがレポートの表示をクリックしたとき。
    * **QueryData**: データがクライアントから要求されているとき。
  * **Refresh Cache**: スケジュールされた更新計画が実行されたとき。
    * **ASModelStream**: データ モデルがカタログから Analysis Services にストリーミングされているとき。
    * **DataRefresh**: データが 1 つまたは複数のデータ ソースから更新されているとき。
    * **SaveToCatalog**: データ モデルがカタログに保存されているとき。

## <a name="analysis-services"></a>Analysis Services
問題を診断するために Analysis Services を変更したり、メモリの制限を調整したりすることが必要な場合があります。

> [!IMPORTANT]
> これらの設定は、レポート サーバーをアップグレードするとリセットされます。 変更内容のコピーを保持し、必要な場合はそれらを再適用してください。
> 
> 

### <a name="install-location"></a>インストールの場所
Power BI Report Server および Analysis Services の既定の場所は次のとおりです。

`C:\Program Files\Microsoft Power BI Report Server\PBIRS\ASEngine`

### <a name="configuring-analysis-services-settings-msmdsrvini"></a>Analysis Services の設定を構成する (msmdsrv.ini)
`<install directory>\PBIRS\ASEngine` ディレクトリにある *msmdsrv.ini* ファイルを使って、Analysis Services のさまざまな設定を制御できます。 msmdsrv.ini ファイルを開くと、このファイルに期待されるすべての設定が含まれていないことがすぐにわかります。 

これは、Power BI Report Server によって実行される実際の Analysis Services プロセスは `<install directory>\PBIRS\ASEngine\workspaces` で起動されるためです。 そのフォルダーには完全な *msmdsrv.ini* ファイルがあります。 workspaces フォルダーのファイルは変更しないでください。このファイルは Analysis Services プロセスが開始するたびに書き換えられます。 設定を制御する場合は、`<install directory>\PBIRS\ASEngine` ディレクトリの msmdsrv.ini を変更してください。

次の設定は、Analysis Services プロセスが開始されるたびにリセットされます。 これらを変更しても無視されます。

* ConfigurationSettings\PrivateProcess
* ConfigurationSettings\DataDir
* ConfigurationSettings\LogDir
* ConfigurationSettings\TempDir
* ConfigurationSettings\BackupDir
* ConfigurationSettings\AllowedBrowsingFolders
* ConfigurationSettings\CrashReportsFolder
* ConfigurationSettings\ExtensionDir
* ConfigurationSettings\Port
* ConfigurationSettings\DeploymentMode
* ConfigurationSettings\ServerLocation
* ConfigurationSettings\TMCompatabilitySKU
* ConfigurationSettings\FlightRecorder\TraceDefinitionFile

### <a name="profiling-the-local-analysis-services-process"></a>ローカル Analysis Services プロセスのプロファイリング
診断のためにローカル Analysis Services プロセスで SQL Profiler トレースを実行できます。 ローカル Analysis Services インスタンスに接続するには、次のようにします。

SQL Server Profiler トレースは、[SQL Server Management Studio (SSMS) のダウンロード](/sql/ssms/download-sql-server-management-studio-ssms)に含まれます。

1. 管理者として **SQL Server Profiler** を開始します。
2. **[新しいトレース]** ボタンを選びます。
3. **[サーバーへの接続]** ダイアログで、 **[Analysis Services]** を選び、サーバー名に「**localhost:5132**」と入力します。
4. **[トレースのプロパティ]** ダイアログで、キャプチャするイベントを選び、 **[実行]** を選びます。

## <a name="lock-pages-in-memory-windows-privilege"></a>メモリ内のページのロック Windows 特権
Power BI レポートをレンダリングできない場合は、Power BI Report Server を実行しているサービス アカウントに **メモリ内のページのロック** 特権を割り当てると、解決する場合があります。 **メモリ内のページのロック** の構成方法については、「[Windows privileges assigned to the Analysis Services service account](/sql/analysis-services/instances/configure-service-accounts-analysis-services#bkmk_winpriv)」(Analysis Services サービス アカウントに割り当てられる Windows 特権) をご覧ください。

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。