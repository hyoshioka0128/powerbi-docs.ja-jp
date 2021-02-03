---
title: Power BI でレポートのパフォーマンスを監視する
description: Power BI でレポートのパフォーマンスを監視する方法についてのガイダンスです。
author: peter-myers
ms.author: kfollis
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 01/14/2021
ms.openlocfilehash: 78c7b97cd926f3f98469d6e52aab5889f4e3daa3
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2021
ms.locfileid: "99088743"
---
# <a name="monitor-report-performance-in-power-bi"></a>Power BI でレポートのパフォーマンスを監視する

[パフォーマンス アナライザー](../create-reports/desktop-performance-analyzer.md)を使用して Power BI Desktop でレポートのパフォーマンスを監視し、[Power BI Premium Metrics アプリ](../admin/service-premium-metrics-app.md)を活用して所属組織の Power BI Premium 容量に展開されたコンテンツのパフォーマンスを監視します。 ボトルネックの場所、およびレポートのパフォーマンスを向上させる方法について説明します。

パフォーマンスの監視は、次のような状況に関連しています。

- インポート データ モデルの更新に時間がかかる。
- DirectQuery またはライブ接続のレポートの処理が遅い。
- モデルの計算に時間がかかる。

低速なクエリまたはレポート ビジュアルは、継続的な最適化の中心点にする必要があります。

## <a name="use-query-diagnostics"></a>クエリ診断を使用する

Power BI Desktop で[クエリ診断](/power-query/QueryDiagnostics)を使用して、クエリをプレビューまたは適用するときに Power Query によって実行されていることを特定します。 さらに、 _[ステップを診断する]_ 機能を使用して、クエリ ステップごとに詳細な評価情報を記録します。 その結果は Power Query で使用できるようになり、変換を適用してクエリの実行をより深く理解することができます。

> [!NOTE]
> 現在、クエリ診断はプレビュー機能であるため、 _[オプションと設定]_ で有効にする必要があります。 有効にすると、そのコマンドを [Power Query エディター] ウィンドウで、 **[ツール]** リボン タブから使用できるようになります。

![[Power Query エディター] の [ツール] リボン タブのスクリーンショット。[ステップを診断する] コマンド、[診断の開始] コマンド、および [診断の停止] コマンドが表示されています。](media/monitor-report-performance/power-query-diagnotics.png)

## <a name="use-performance-analyzer"></a>パフォーマンス アナライザーを使用する

Power BI Desktop で[パフォーマンス アナライザー](../create-reports/desktop-performance-analyzer.md)を使用して、レポートの各要素 (ビジュアルや DAX の数式など) がどのように動作しているかを確認できます。 これは、パフォーマンス上の問題に影響しているのが、クエリ、またはビジュアルのレンダリングのどちらであるかを判断する場合に特に役に立ちます。

## <a name="use-sql-server-profiler"></a>SQL Server プロファイラーを使用する

[SQL Server プロファイラー](/sql/tools/sql-server-profiler/sql-server-profiler)を使用して、低速なクエリを特定することもできます。

> [!NOTE]
> SQL Server プロファイラーは、[SQL Server Management Studio](/sql/ssms/download-sql-server-management-studio-ssms) の一部として使用できます。

データ ソースが次のいずれかである場合に SQL Server プロファイラーを使用します。

- SQL Server
- SQL Server Analysis Services
- Azure Analysis Services

> [!CAUTION]
> Power BI Desktop では、診断ポートへの接続がサポートされています。 診断ポートを使用すると、他のツールで接続を行い、診断目的のトレースを実行できます。 Power Desktop データ モデルに対する変更はサポートされていません。 データ モデルに変更を加えると、破損とデータ損失が発生する可能性があります。

SQL Server プロファイラー トレースを作成するには、次の手順に従います。

1. Power BI Desktop レポートを開きます (次の手順でポートを特定するのが容易になるように、その他の開いているレポートをすべて閉じます)。
1. Power BI Desktop によって使用されているポートを確認するために、(管理者特権を持つ) PowerShell、またはコマンド プロンプトで、次のコマンドを入力します。
    ```powershell
    netstat -b -n
    ```
    出力には、アプリケーションとその開いているポートの一覧が表示されます。 **msmdsrv.exe** によって使用されているポートを探し、後で使用するために記録しておきます。 これが使用している Power BI Desktop のインスタンスです。
1. SQL Server プロファイラーを Power BI Desktop レポートに接続するには:
    1. SQL Server プロファイラーを開きます。
    1. SQL Server プロファイラーの _[ファイル]_ メニューで、 _[新しいトレース]_ を選択します。
    1. **[サーバーの種類]** に _[Analysis Services]_ を選択します。
    1. **[サーバー名]** には、"_localhost:[前に記録したポート]_ " と入力します。
    1. _[実行]_ をクリックします。これで SQL Server プロファイラー トレースが有効になり、Power BI Desktop クエリがアクティブにプロファイリングされます。
1. Power BI Desktop クエリが実行されると、それぞれの期間と CPU 時間が表示されます。 データ ソースの種類によっては、クエリがどのように実行されたかを示す他のイベントが表示されることがあります。 この情報を使用して、どのクエリがボトルネックであるかを特定できます。

SQL Server プロファイラーを使用する利点は、SQL Server (リレーショナル) データベースのトレースを保存できることです。 このトレースは、[データベース エンジン チューニング アドバイザー](/sql/relational-databases/performance/start-and-use-the-database-engine-tuning-advisor)に対する入力にすることができます。 このようにして、データ ソースのチューニング方法に関する推奨事項を受け取ることができます。

## <a name="monitor-premium-metrics"></a>Premium Metrics を監視する

Power BI Premium 容量では、**Power BI Premium Metrics アプリ** を使用して、Power BI Premium サブスクリプションの正常性と容量を監視することができます。 詳細については、「[Power BI Premium Metrics アプリ](../admin/service-premium-metrics-app.md)」をご覧ください。

## <a name="next-steps"></a>次の手順

この記事に関する詳細については、次のリソースを参照してください。

- [クエリ診断](/power-query/QueryDiagnostics)
- [パフォーマンス アナライザー](../create-reports/desktop-performance-analyzer.md)
- [Power BI でのレポートのパフォーマンスのトラブルシューティング](report-performance-troubleshoot.md)
- [Power BI Premium Metrics アプリ](../admin/service-premium-metrics-app.md)
- わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
- Power BI チームへのご提案は、 [Power BI を改善するためのアイデアをお寄せください](https://ideas.powerbi.com/)
