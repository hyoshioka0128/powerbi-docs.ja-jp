---
title: Power BI Embedded 監視データのリファレンス
description: Power BI Embedded を監視する際に必要となる重要なリファレンスです。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.custom: subject-monitoring
ms.date: 03/04/2021
ms.openlocfilehash: a0ea1b135de0cb2257d3d6f0477314fe26f54319
ms.sourcegitcommit: 89c349500dd0737d80a753403714bceb3fd0a3ef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2021
ms.locfileid: "102628463"
---
# <a name="monitoring-power-bi-embedded-data-reference"></a>Power BI Embedded 監視データのリファレンス

Power BI Embedded の監視データの収集と分析について詳しくは、「[Power BI Embedded を監視する](monitor-power-bi-embedded.md)」を参照してください。

## <a name="metrics"></a>メトリック

このセクションでは、Power BI Embedded 用に収集される、自動的に収集されるすべてのプラットフォーム メトリックを一覧表示します。  

|メトリックの種類 | リソース プロバイダー/種類の名前空間<br/> および個々のメトリックへのリンク |
|-------|-----|
| Capacities | [Microsoft.PowerBIDedicated/capacities](/azure/azure-monitor/platform/metrics-supported#microsoftpowerbidedicatedcapacities) |

### <a name="capacities"></a>Capacities

リソース プロバイダーと種類:[Microsoft.PowerBIDedicated/capacities](/azure/azure-monitor/platform/metrics-supported#microsoftpowerbidedicatedcapacities)

| 名前 | メトリック | ユニット | 説明 |
|:---|:-------|:-----|:------------|
|CPU (Gen2) |cpu_metric |Percent |CPU 使用率。 Power BI Embedded Generation 2 のリソースに対してのみサポートされます。 |
|オーバーロード (Gen2) |overload_metric |0/1 |リソース オーバーロード。リソースがオーバーロードになっている場合は 1。それ以外の場合は 0。 Power BI Embedded Generation 2 のリソースに対してのみサポートされます。 |
|メモリ (Gen1) |memory_metric               |バイト        |メモリ。 範囲: 0-3 GB (A1)、0-5 GB (A2)、0-10 GB (A3)、0-25 GB (A4)、0-50 GB (A5)、0-100 GB (A6)。 Power BI Embedded Generation 1 のリソースに対してのみサポートされます。 |
|メモリ スラッシング (データセット) (Gen1) |memory_thrashing_metric     |Percent      |平均的なメモリ スラッシング。 Power BI Embedded Generation 1 のリソースに対してのみサポートされます。 |
|高い QPU 使用率 (Gen1) |qpu_high_utilization_metric |Count        |過去 1 分間の高い QPU 使用率。QPU 使用率が高い場合は 1、それ以外の場合は 0。 Power BI Embedded Generation 1 のリソースに対してのみサポートされます。 |
|クエリ実行時間 (データセット) (Gen1) |QueryDuration               |ミリ秒 |最後の間隔での DAX クエリ実行時間。 Power BI Embedded Generation 1 のリソースに対してのみサポートされます。 |
|クエリ プールのジョブ キューの長さ (データセット) (Gen1) |QueryPoolJobQueueLength     |Count        |クエリ スレッド プールのキューに登録されているジョブの数。 Power BI Embedded Generation 1 のリソースに対してのみサポートされます。 |

## <a name="metric-dimensions"></a>メトリック ディメンション

メトリック ディメンションの詳細については、「[多次元メトリック](/azure/azure-monitor/platform/data-platform-metrics#multi-dimensional-metrics)」を参照してください。

Power BI Embedded には、ディメンションを含むメトリックはありません。

## <a name="resource-logs"></a>リソース ログ

このセクションでは、Power BI Embedded 用に収集できるリソース ログの種類の一覧を示します。

[Azure Monitorでサポートされているすべてのリソース ログのカテゴリの種類](/azure/azure-monitor/platform/resource-logs-schema)の一覧も参照してください。

このセクションでは、Power BI Embedded 用に収集されるすべてのリソース ログのカテゴリの種類を一覧表示します。  

|リソース ログの種類 | リソース プロバイダー/種類の名前空間<br/> および個々のメトリックへのリンク |
|-------|-----|
| Capacities | [Microsoft.PowerBIDedicated/capacities](/azure/azure-monitor/platform/resource-logs-categories#microsoftpowerbidedicatedcapacities) |

## <a name="azure-monitor-logs-tables"></a>Azure Monitor ログ テーブル

このセクションでは、Power BI Embedded に関連する、また Log Analytics でクエリに使用できる、すべての Azure Monitor ログ Kusto テーブルを示します。

|リソースの種類 | メモ |
|-------|-----|
| [Power BI Embedded](/azure/azure-monitor/reference/tables/tables-resourcetype#power-bi-embedded) |以下のテーブルの一覧を参照してください |

### <a name="power-bi-embedded"></a>Power BI Embedded

| テーブル |  説明 |
|:---------|:-------------|------------------|
| [AzureActivity](/azure/azure-monitor/reference/tables/azureactivity) | Azure で発生したサブスクリプション レベルまたは管理グループ レベルのイベントに関する分析情報を提供する、Azure のアクティビティ ログからのエントリ。    |                             |                                                   | 
| [AzureDiagnostics](/azure/azure-monitor/reference/tables/azurediagnostics)   | Azure Diagnostics モードを使用する Azure サービスのリソース ログが格納されます。 リソース ログには、Azure リソースの内部操作が記述されています。 |
| [AzureMetrics](/azure/azure-monitor/reference/tables/azuremetrics)   | Azure サービスによって生成される、その正常性とパフォーマンスを測定したメトリック データ。 |

すべての Azure Monitor ログ/Log Analytics テーブルのリファレンスについては、[Azure Monitor ログ テーブル リファレンス](/azure/azure-monitor/reference/tables/tables-resourcetype)に関するページを参照してください。

## <a name="activity-log"></a>アクティビティ ログ

**[エンジン]** と **[AllMetrics]** カテゴリを選択できます。

### <a name="engine"></a>エンジン

エンジン カテゴリによって、以下に示すイベントをログに記録するようにリソースに指示します。 イベントごとにプロパティが存在します。

|     イベント名     |     イベントの説明     |
|----------------------------|----------------------------------------------------------------------------------|
|    監査ログイン    |    追跡開始以降のエンジン イベントへの新しい接続を、すべて記録します。    |
|    セッションの初期化    |    追跡開始以降のセッション初期化イベントをすべて記録します。    |
|    Vertipaq クエリの開始    |    追跡開始以降の VertiPaq SE クエリの開始イベントを、すべて記録します。    |
|    クエリの開始    |    追跡開始以降のクエリの開始イベントを、すべて記録します。    |
|    クエリの終了    |    追跡開始以降のクエリの終了イベントを、すべて記録します。    |
|    Vertipaq クエリの終了    |    追跡開始以降の VertiPaq SE クエリの終了イベントを、すべて記録します。    |
|    監査ログアウト    |    追跡開始以降のエンジン イベントからの切断を、すべて記録します。    |
|    エラー    |    追跡開始以降のエンジン エラーのイベントを、すべて記録します。    |

#### <a name="event-example"></a>イベントの例

イベントの例を次の表に示します。

| プロパティ名 | Vertipaq クエリの終了の例 | [プロパティの説明] |
|---|---|---|
| EventClass | XM_SEQUERY_END | イベント クラスを使用してイベントを分類します。 |
| EventSubclass | 0 | イベントのサブクラスは、各イベント クラスに関する追加情報を提供します。 (たとえば、0: VertiPaq スキャン) |
| RootActivityId | ff217fd2-611d-43c0-9c12-19e202a94f70 | ルート アクティビティの ID です。 |
| CurrentTime | 2018-04-06T18:30:11.9137358Z | イベントが開始された時刻です (使用可能な場合)。 |
| StartTime | 2018-04-06T18:30:11.9137358Z | イベントが開始された時刻です (使用可能な場合)。 |
| JobID | 0 | 進行状況に対応するジョブ ID です。 |
| ObjectID | 464 | オブジェクト ID |
| ObjectType | 802012 | ObjectType |
| EndTime | 2018-04-06T18:30:11.9137358Z | イベントの終了時刻。 |
| 期間 | 0 | イベントの実行にかかった時間です (ミリ秒)。 |
| SessionType | User | セッションの種類です (操作の原因となったエンティティ)。 |
| ProgressTotal | 0 | 進行状況の合計です。 |
| IntegerData | 0 | 整数データ。 |
| Severity | 0 | 例外の重要度レベルです。 |
| Success | 1 | 1 = 成功。 0 = 失敗 (たとえば、1 は権限チェックの成功を表し、0 は失敗を表します)。 |
| エラー | 0 | 指定されたイベントのエラー番号です。 |
| ConnectionID | 3 | 一意な接続 ID です。 |
| DatasetID | 5eaa550e-06ac-4adf-aba9-dbf0e8fd1527 | ユーザーのステートメントが実行されているデータセットの ID です。 |
| SessionID | 3D063F66-A111-48EE-B960-141DEBDA8951 | セッション GUID。 |
| SPID | 180 | サーバー プロセス ID です。 これにより、ユーザー セッションを一意に識別します。 これは、XML/A によって使用されるセッション GUID と直接対応します。 |
| ClientProcessID | null | クライアント アプリケーションのプロセス ID。 |
| ApplicationName | null | サーバーへの接続を作成したクライアント アプリケーションの名前です。 |
| CapacityName | pbi641fb41260f84aa2b778a85891ae2d97 | Power BI Embedded 容量のリソースの名前です。 |

### <a name="allmetrics"></a>AllMetrics

**[AllMetrics]** オプションをオンにすると、Power BI Embedded リソースで使用できるすべてのメトリックのデータをログに記録します。

アクティビティ ログに作成される可能性のある、Power BI Embedded に関連する操作の一覧を次の表に示します。

## <a name="schemas"></a>スキーマ

Power BI Embedded では、**Power BI 専用** スキーマが使用されます。

## <a name="example-script-for-scaling-a-capacity"></a>容量スケーリングのスクリプト例

容量リソース容量をスケーリングする目的で、[ScaleUp-Automation-RunBook.ps1](https://github.com/microsoft/PowerBI-Developer-Samples/blob/master/PowerShell%20Scripts/ScaleUp-Automation-RunBook.ps1) PowerShell Runbook スクリプトを使用できます。

このスクリプトでは Power BI と ARM REST API が使用されます。Azure オートメーションで呼び出し、Azure アラートで始動させることができます。

[PowerBI-Developer-Samples](https://github.com/microsoft/PowerBI-Developer-Samples) リポジトリの一環としてスクリプトをコピーしたり、ダウンロードしたりできます。その際、緑の *[ダウンロード]* ボタンを押し、ZIP をダウンロードしてください。

## <a name="next-steps"></a>次のステップ

>[!div class="nextstepaction"]
>[Azure Power BI Embedded を監視する](monitor-power-bi-embedded.md)

>[!div class="nextstepaction"]
>[Azure リソースの診断ログ](/azure/monitoring-and-diagnostics/monitoring-overview-of-diagnostic-logs)

>[!div class="nextstepaction"]
>[Set-AzureRmDiagnosticSetting](/powershell/module/azurerm.insights/Set-AzureRmDiagnosticSetting)
