---
title: Power BI Desktop での DirectQuery モデルのトラブルシューティング
description: DirectQuery モデルの問題をトラブルシューティングします。
author: davidiseminger
ms.author: davidi
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: troubleshooting
ms.date: 10/24/2019
ms.openlocfilehash: 943c8283d48b4281d2ddb5d7eeed0e69db4ee6fc
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96405309"
---
# <a name="troubleshoot-developing-directquery-models-in-power-bi-desktop"></a>Power BI Desktop での DirectQuery モデルの開発のトラブルシューティング

この記事の対象読者は、Power BI DirectQuery モデル (Power BI Desktop または Power BI サービスを使用して開発されるもの) を開発するデータ モデラーです。 パフォーマンスの問題を診断する方法や、レポートを最適化できるより詳細な情報を取得する方法について説明します。

## <a name="performance-analyzer"></a>パフォーマンス アナライザー

パフォーマンスの問題の診断は、Power BI (サービスまたは Power BI Report Server) ではなく Power BI Desktop で始めることを強くお勧めします。 一般に、パフォーマンスの問題は単に基になるデータ ソースのパフォーマンス レベルによるものであり、Power BI Desktop の分離環境で最初に特定のコンポーネント (Power BI ゲートウェイなど) を除外する方が、より簡単に問題を識別して診断できます。 Power BI Desktop にパフォーマンスの問題が存在しないことがわかった場合にのみ、Power BI でレポートの詳細に焦点を当てて調査する必要があります。 [パフォーマンス アナライザー](../create-reports/desktop-performance-analyzer.md)は、このプロセス全体で問題を特定するために便利なツールです。

同様に、ページにある多くの視覚エフェクトではなく、最初に個々の視覚エフェクトに問題を分離することをお勧めします。

このトピックの前の段落の手順を実施して、Power BI Desktop のページにある 1 つの視覚エフェクトの動作が遅いことがわかったものとします。 基になるソースに対し、Power BI Desktop からどのようなクエリが送信されているかは、パフォーマンス アナライザーを使用して特定できます。 基になるデータ ソースから出力される可能性があるトレースおよび診断情報を見ることもできます。 このようなトレースには、クエリの実行方法および改善方法の詳細に関する有用な情報も含まれることがあります。

さらに、ソースからのこのようなトレースがない場合であっても、次に示すように、実行時間に沿って Power BI によって送信されるクエリを表示することができます。

## <a name="review-trace-files"></a>トレース ファイルを確認する

既定では、Power BI Desktop は特定のセッションの間のイベントを **FlightRecorderCurrent.trc** という名前のトレース ファイルに記録します。

一部の DirectQuery ソースの場合、このログには基になるデータ ソースに送信されたすべてのクエリが含まれています (他の DirectQuery ソースは将来サポートされる可能性があります)。 ログにクエリを書き込むソースは次のとおりです。

- SQL Server
- Azure SQL Database
- Azure SQL Data Warehouse
- Oracle
- Teradata
- SAP HANA

トレース ファイルは、現在のユーザーの **AppData** フォルダーにあります ( _\\\<User>\AppData\Local\Microsoft\Power BI Desktop\AnalysisServicesWorkspaces_)。

このフォルダーに簡単にアクセスするには次のようにします。Power BI Desktop で _[ファイル] > [オプションと設定] > [オプション]_ の順に選択し、 **[診断]** ページを選択します。 次のダイアログ ウィンドウが表示されます。

![Power BI Desktop ウィンドウを開いて [グローバル] の [診断] ページを選択したところ。 [診断オプション] セクションには、[トレースを有効にする] と [ジオコーディング キャッシュのバイパス] の 2 つのプロパティがあります。 [トレースを有効にする] オプションが有効になっています。 [クラッシュ ダンプの収集] セクションには、[今すぐ有効にする] ボタンのほか、クラッシュ ダンプ (またはトレース) フォルダーを開くためのリンクが表示されます。](media/desktop-directquery-troubleshoot/desktop-directquery-troubleshoot-desktop-file-options-diagnostics.png)

[クラッシュ ダンプの収集] の **[クラッシュ ダンプ/トレース フォルダーを開く]** リンクを選択すると、 _\\\<User>\AppData\Local\Microsoft\Power BI Desktop\Traces_ というフォルダーが開きます。

そのフォルダーの親フォルダーに移動すると、_AnalysisServicesWorkspaces_ を含むフォルダーが表示され、これには Power BI Desktop の開いているインスタンスごとに 1 つのワークスペース フォルダーが含まれます。 これらのサブフォルダーは整数のサフィックスが付いた名前になっています (例: _AnalysisServicesWorkspace2058279583_)。

そのフォルダー内の _\Data_ サブフォルダーには、現在の Power BI セッションのトレース ファイル FlightRecorderCurrent.trc が含まれます。 関連する Power BI Desktop セッションが終了すると、対応するワークスペース フォルダーは削除されます。

トレース ファイルは、SQL Server Profiler ツールを使って開くことができます。このツールは、SQL Server Management Studio の一部として無料でダウンロードできます。 [この場所](/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-2017)から入手できます。

SQL Server Management Studio をダウンロードしてインストールした後、SQL Server Profiler を実行します。

![SQL Server Profiler を開いたところ。 まだトレースは追加されていません。](media/desktop-directquery-troubleshoot/desktop-directquery-troubleshoot-sql-server-profiler-trace.png)

トレース ファイルを開くには、次の手順のようにします。

1. SQL Server Profiler で、 _[ファイル] > [開く] > [トレース]_ ファイルの順に選択します。
2. 現在開いている Power BI セッションのトレース ファイルのパスを入力します。たとえば、 _\\\<User>\AppData\Local\Microsoft\Power BI Desktop\AnalysisServicesWorkspaces\AnalysisServicesWorkspace2058279583\Data_ です。
3. _FlightRecorderCurrent.trc_ を開く

現在のセッションのすべてのイベントが表示されます。 注釈付きの例を以下に示します。イベントのグループが強調表示されています。 各グループには次のものが含まれます。

- _Query Begin_ イベントと _Query End_ イベント。これらは、UI によって生成された DAX クエリの開始と終了を表します (たとえば、視覚エフェクトから、またはフィルター UI 内の値の一覧の作成から)。
- 1 つまたは複数の _DirectQuery Begin_ イベントと _DirectQuery End_ イベントのペア。これらは、DAX クエリの評価の一部として、基になるデータ ソースに送信されたクエリを表します

複数の DAX クエリを並列して実行できるので、異なるグループからのイベントが混在している可能性があることに注意してください。 ActivityID の値を使って、同じグループに属しているイベントを特定できます。

![SQL Server Profiler を開いたところ。 まだトレースは追加されていません。](media/desktop-directquery-troubleshoot/desktop-directquery-troubleshoot-sql-server-profiler-trace.png)

必要なその他の列は次のとおりです。

- **TextData:** イベントのテキスト形式の詳細です。 _Query Begin/End_ イベントの場合は、DAX クエリです。 _DirectQuery Begin/End_ イベントの場合は、基になるソースに送信された SQL クエリです。 現在選択されているイベントの _TextData_ 値は、下部の領域にも表示されます。
- **EndTime:** イベントが完了した日時です。
- **Duration:** DAX クエリまたは SQL クエリの実行にかかった時間です (ミリ秒単位)。
- **Error:** エラーが発生したかどうかを示します (発生した場合は、イベントも赤で表示されます)。

上の図では、重要な列がわかりやすいように、重要ではない列の表示が狭くなります。

潜在的なパフォーマンスの問題の診断に役立つトレースをキャプチャする推奨される方法は次のとおりです。

- 1 つの Power BI Desktop セッションを開きます (複数のワークスペース フォルダーで混乱するのを避けるため)。
- Power BI Desktop で関心のあるアクションのセットを実行します。 それ以外にいくつかの操作を実行し、目的のイベントがトレース ファイルにフラッシュされるようにします。
- SQL Server Profiler を開き、前述のようにトレースを確認します。 Power BI Desktop を閉じるとトレース ファイルが削除されることに注意してください。 また、Power BI Desktop でのその後の操作はすぐに表示されません。新しいイベントを表示するには、トレース ファイルいったん閉じてから再度開く必要があります。
- トレース ファイルを容易に解釈できるよう (および、トレース ファイルのサイズには制限があり、長いセッションでは前の方のイベントが破棄される可能性があるため)、個々のセッションを適度な小ささ (数百秒ではなく 10 秒くらいの操作) にします。

## <a name="understand-queries-sent-to-the-source"></a>ソースに送信されるクエリについて

Power BI Desktop によって生成されて送信されるクエリの一般的な形式では、参照されるモデル テーブルごとにサブクエリが使われます。サブクエリは、Power Query クエリによって定義されます。 たとえば、SQL Server のリレーショナル データベースに次のような TPC-DS テーブルがあるものとします。

![関連付けられた 4 つのテーブルを Power BI Desktop モデル ビュー ダイアグラムで表示したところ。 テーブルは、Item、Web_Sales、Customer、Date-dim です。](media/desktop-directquery-troubleshoot/desktop-directquery-troubleshoot-model-view-diagram.png)

次のビジュアルとその構成について考えてみます。**SalesAmount** メジャーは次の式で定義されていることに注目してください。

```dax

SalesAmount = SUMX(Web_Sales, [ws_sales_price] * [ws_quantity])

```

![カテゴリ別の売上高を表示する積み上げ縦棒グラフを含んだ Power BI Desktop レポート。 [フィルター] ペインを見ると、2000 年度を条件とするフィルターが設定されていることがわかります。](media/desktop-directquery-troubleshoot/desktop-directquery-troubleshoot-example-report.png)

このビジュアルを更新すると、以下 (次の段落) に示した T-SQL クエリが生成されます。 これを見ると、**Web_Sales**、**Item**、**Date_dim** の各モデル テーブルに対するサブクエリが 3 つあることがわかります。 ビジュアルによって実際に参照されている列は 4 つだけですが、各テーブルからはモデル テーブルのすべての列が返されます。 これらのサブクエリ (網掛けの部分) が、Power Query クエリの厳密な定義となります。 現時点で DirectQuery についてサポートされているデータ ソースに関しては、この方法でサブクエリを使っても、パフォーマンスに影響はないことがわかっています。 SQL Server などのデータ ソースでは、使用されない列への参照は最適化により除外されます。

Power BI でこのパターンが使われる理由の 1 つは、Power Query クエリを自分で定義して、特定のクエリ ステートメントを使用できるためです。 つまり、書き換えられることなく "そのまま" 使用されるのです。 このパターンでは、共通テーブル式 (CTE) とストアド プロシージャを使用するクエリ ステートメントの使用が制限されることに注意してください。 これらのステートメントをサブクエリで使用することはできません。

![モデル テーブルごとに 1 つの埋め込みサブクエリを示した、きわめて詳細な T-SQL クエリ。](media/desktop-directquery-troubleshoot/desktop-directquery-troubleshoot-example-query.png)

## <a name="gateway-performance"></a>ゲートウェイ パフォーマンス

ゲートウェイ パフォーマンスのトラブルシューティングについては、「[ゲートウェイのトラブルシューティング - Power BI](service-gateway-onprem-tshoot.md)」の記事を参照してください。

## <a name="next-steps"></a>次の手順

DirectQuery の詳細については、次のリソースを参照してください。

- [Power BI Desktop で DirectQuery を使用する](desktop-use-directquery.md)
- [Power BI Desktop での DirectQuery モデル](desktop-directquery-about.md)
- [Power BI Desktop の DirectQuery モデルのガイダンス](../guidance/directquery-model-guidance.md)
- わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
