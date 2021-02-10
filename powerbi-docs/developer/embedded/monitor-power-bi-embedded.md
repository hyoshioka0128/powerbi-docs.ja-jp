---
title: Power BI Embedded を監視する
description: Power BI Embedded の監視方法を学習する場合は、ここから開始してください。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.custom: subject-monitoring
ms.topic: how-to
ms.date: 01/14/2021
ms.openlocfilehash: 5cea43f4be9a3fee7c2fb0f99ef0acef99bb8364
ms.sourcegitcommit: f17acb16018752c234db6bff1f51f5130be12c58
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99616998"
---
# <a name="monitor-power-bi-embedded"></a>Power BI Embedded を監視する

Azure リソースに依存するクリティカルなアプリケーションとビジネス プロセスがある場合は、それらのリソースの可用性、パフォーマンス、操作を監視する必要があります。 この記事では、Power BI Embedded によって生成される監視データと、Azure Monitor の機能を使用してこのデータに対する分析とアラートを実行する方法について説明します。

## <a name="monitor-overview"></a>監視の概要

それぞれの *Power BI Embedded* インスタンスに対する Azure portal の **[概要]** ページには、次の情報が記載されています。

* **[リソース グループ]** - インスタンスが属している [リソース グループ](/azure/azure-resource-manager/management/overview#resource-groups)
* **[状態]** - Power BI Embedded インスタンスの状態
* **[場所]** - Power BI Embedded インスタンスの場所
* **[リソース名]** - Power BI Embedded インスタンスの名前
* **[SKU]** - Power BI Embedded インスタンスで使用している SKU
* **[サブスクリプション名]** - Power BI Embedded インスタンスのサブスクリプション名
* **[サブスクリプション ID]** - Power BI Embedded インスタンスのサブスクリプション ID

## <a name="what-is-azure-monitor"></a>Azure Monitor とは

*Power BI Embedded* では、監視データを作成するために [Azure Monitor](/azure/azure-monitor/overview) が使用されます。これは Azure のフル スタック監視サービスであり、Azure リソースおよび他のクラウドやオンプレミスのリソースを監視するための完全な機能セットが用意されています。

まず「[Azure Monitor を使用した Azure リソースの監視](/azure/azure-monitor/insights/monitor-azure-resource)」の記事にある次の概念の説明をお読みください。

- Azure Monitor とは
- 監視に関連するコスト
- Azure で収集される監視データ
- データ収集の構成
- 監視データの分析とアラート生成のための Azure の標準ツール

以下のセクションではこの記事を基にして、Power BI Embedded 用に収集される特定のデータについて説明します。また、Azure ツールを使用してデータ収集を構成し、そのデータを分析する例を示します。

## <a name="monitoring-data"></a>データの監視

Power BI Embedded では、[Azure リソースからの監視データ](/azure/azure-monitor/insights/monitor-azure-resource#monitoring-data-from-Azure-resources)に関する記事で説明されている他の Azure リソースと同じ種類の監視データが収集されます。

Power BI Embedded によって作成されるメトリックおよびログ メトリックの詳細については、「[*Power BI Embedded* 監視データのリファレンス](monitor-power-bi-embedded-reference.md)」を参照してください。

## <a name="collection-and-routing"></a>収集とルーティング

プラットフォーム メトリックとアクティビティ ログは自動的に収集および格納されますが、診断設定を使用して他の場所にルーティングすることもできます。  

リソース ログは、診断設定を作成して 1 つ以上の場所にルーティングするまでは収集および格納されません。

Azure portal、CLI、または PowerShell を使用して診断設定を作成するプロセスの詳細については、「[Azure でプラットフォーム ログとメトリックを収集するための診断設定を作成する](/azure/azure-monitor/platform/diagnostic-settings)」を参照してください。 診断設定を作成するときは、収集するログのカテゴリを指定します。 *Power BI Embedded* のカテゴリは、[Power BI Embedded 監視データのリファレンス](monitor-power-bi-embedded-reference.md#resource-logs)に記載されています。

### <a name="using-powershell-to-enable-diagnostics"></a>PowerShell を使用して診断を有効にする

PowerShell を使用してメトリックと診断ログを有効にするには、以下に記載するコマンドを使用します。 PowerShell を使用して診断を有効にする方法の詳細については、「[PowerShell を使用して Azure Monitor の Log Analytics ワークスペースを作成および構成する](/azure/azure-monitor/platform/powershell-workspace-configuration)」を参照してください。

* ストレージ アカウントへの診断ログの保存を有効にするには、次のコマンドを使用します。

    ```powershell
    Set-AzureRmDiagnosticSetting -ResourceId [your resource id] -StorageAccountId [your storage account id] -Enabled $true
    ```
    ストレージ アカウント ID は、ログを送信するストレージ アカウントのリソース ID です。

* イベント ハブに対して診断ログのストリーミングを有効にするには、次のコマンドを使用します。

    ```powershell
    Set-AzureRmDiagnosticSetting -ResourceId [your resource id] -ServiceBusRuleId [your service bus rule id] -Enabled $true
    ```
* Azure Service Bus ルール ID は、次の形式の文字列です。

    ```powershell
    {service bus resource ID}/authorizationrules/{key name}
    ```

* Log Analytics ワークスペースへの診断ログの送信を有効にするには、次のコマンドを使用します。

    ```powershell
        Set-AzureRmDiagnosticSetting -ResourceId [your resource id] -WorkspaceId [resource id of the log analytics workspace] -Enabled $true
    ```

* 次のコマンドを使用して、Log Analytics ワークスペースのリソース ID を取得できます。

    ```powershell
    (Get-AzureRmOperationalInsightsWorkspace).ResourceId
    ```

このパラメーターを組み合わせて、複数の出力オプションを有効にできます。

収集できるメトリックとログについては、次のセクションで説明します。

## <a name="analyzing-metrics"></a>メトリックの分析

*Power BI Embedded* のメトリックと他の Azure サービスからのメトリックを監視するには、 **[Azure Monitor]** メニューから **[メトリック]** を開いて、メトリックス エクスプローラーを使用します。 このツールの使用方法の詳細については、「[Azure メトリックス エクスプローラーの概要](/azure/azure-monitor/platform/metrics-getting-started)」を参照してください。

Power BI Embedded 用に収集されるプラットフォーム メトリックの一覧については、[「*Power BI Embedded* 監視データのリファレンス」の「メトリック」](monitor-power-bi-embedded-reference.md#metrics)を参照してください  

参考のために、[Azure Monitor でサポートされているすべてのリソース メトリック](/azure/azure-monitor/platform/metrics-supported)の一覧を確認できます。

## <a name="analyzing-logs"></a>ログの分析

Azure Monitor ログのデータはテーブルに格納され、各テーブルには独自の一意のプロパティ セットがあります。  

Azure Monitor 内のすべてのリソース ログには、同じフィールドの後にサービス固有のフィールドがあります。 共通のスキーマについては、[Azure Monitor リソース ログ スキーマ](https://docs.microsoft.com/azure/azure-monitor/platform/diagnostic-logs-schema#top-level-resource-logs-schema)に関する記事を参照してください。Power BI Embedded リソース ログのスキーマは、[Power BI Embedded データ リファレンス](monitor-power-bi-embedded-reference.md#schemas)に記載されています。

[アクティビティ ログ](/azure/azure-monitor/platform/activity-log)は、サブスクリプション レベルのイベントの分析情報を提供するプラットフォーム ログイン Azure です。 個別に表示できるほか、Azure Monitor ログにルーティングして、Log Analytics を使用してより複雑なクエリを実行することもできます。  

Power BI Embedded 用に収集されるリソース ログの種類の一覧については、[Power BI Embedded 監視データのリファレンス](monitor-power-bi-embedded-reference.md#resource-logs)を参照してください  

Azure Monitor ログによって使用され、Log Analytics によってクエリ可能なテーブルの一覧については、[Power BI Embedded 監視データのリファレンス](monitor-power-bi-embedded-reference.md#azure-monitor-logs-tables)を参照してください  

### <a name="sample-kusto-queries"></a>サンプル Kusto クエリ

> [!IMPORTANT]
> [Power BI Embedded] メニューから **[ログ]** を選択すると、クエリ スコープが現在の Power BI Embedded リソースに設定された状態で Log Analytics が開きます。 つまり、ログ クエリには、そのリソースからのデータのみが含まれます。 他の Power BI Embedded リソースからのデータや、他の Azure サービスからのデータを含むクエリを実行する場合は、 **[Azure Monitor]** メニューから **[ログ]** を選択します。 詳細については、「[Azure Monitor Log Analytics のログ クエリのスコープと時間範囲](/azure/azure-monitor/log-query/scope/)」を参照してください。

Power BI Embedded を監視するためのクエリの例を以下に示します。

* このクエリは、5 分 (300,000 ミリ秒) 以内に完了します。

    ```Kusto
        search *
        | where Type == "AzureDiagnostics"
        | where ( OperationName == "QueryEnd" )
        | where toint(Duration_s) < 300000   
    ```
* 容量の名前を特定します。

    ```Kusto
        search *
        | where Type == "AzureDiagnostics"
        | where ( OperationName == "QueryEnd" )
        | where toint(Duration_s) < 300000   
    ```

## <a name="alerts"></a>警告

Azure Monitor のアラートは、監視データで重要な状態が見つかると事前に通知します。 これにより、ユーザーが気付く前に、管理者が問題を識別して対処できます。 アラートは[メトリック](/azure/azure-monitor/platform/alerts-metric-overview)、[ログ](/azure/azure-monitor/platform/alerts-unified-log)、[アクティビティ ログ](/azure/azure-monitor/platform/activity-log-alerts)に対して設定できます。

## <a name="next-steps"></a>次のステップ

Azure リソースの診断ログについて、さらに詳しく学習することができます。

>[!div class="nextstepaction"]
>[Power BI Embedded 監視データのリファレンス](monitor-power-bi-embedded-reference.md)

>[!div class="nextstepaction"]
>[Azure Monitor を使用した Azure リソースの監視](/azure/azure-monitor/insights/monitor-azure-resource)
