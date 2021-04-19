---
title: データフローの更新の理解および最適化
description: Power BI でデータフローの更新を使用および最適化する方法
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-dataflows
ms.topic: how-to
ms.date: 03/25/2021
LocalizationGroup: Data from files
ms.openlocfilehash: 8201c50c23ae396f794e82f963d7461cbf5a0ec9
ms.sourcegitcommit: 8cccc80f30ee5a4138ce48e44d3442a5ec6bce54
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2021
ms.locfileid: "107220444"
---
# <a name="understanding-and-optimizing-dataflows-refresh"></a>データフローの更新の理解および最適化

Power BI データフローを使用すると、下流の分析のために、データに接続して、変換、結合、および配布を行うことができます。 データフローの重要な要素は、更新プロセスです。これにより、データフロー内に作成した変換ステップが適用され、成果物自体のデータが更新されます。 

実行時間、パフォーマンス、および最大限にデータフローを活用しているかどうかを把握するために、データフローが更新された後に更新履歴をダウンロードできます。

## <a name="understanding-refreshes"></a>更新について

データフローに適用できる更新は、2 種類あります。

* **完全**。これは、データの完全なフラッシュと再読み込みを実行します。

* **増分 (Premium のみ)** 。これは、フィルターとして表現される、時間ベースの規則に基づいてデータのサブセットを処理します。この規則は、自分で構成します。 Power BI サービスで日付列のフィルターを使用して、複数の範囲にデータを動的にパーティション分割します。 増分更新を構成すると、データフローによって、クエリが日付によるフィルタリングを含むように自動的に変更されます。 Power Query の **詳細エディター** を使用して、自動生成されたクエリを編集し、更新を微調整またはカスタマイズすることができます。 独自の Azure Data Lake Storage を使用する場合は、設定した更新ポリシーに基づいてデータのタイム スライスを表示できます。

    > [!NOTE]
    > [増分更新](https://docs.microsoft.com/power-query/dataflows/incremental-refresh)とそのしくみについて詳細を確認できます。
    
Power BI の大規模なデータフローの増分更新には、次の利点があります。

* 次の理由で、最初の更新後の更新が高速になる。

    * Power BI によって、ユーザーが指定した最後の *N* 個のパーティション (パーティションは日、週、月など) が更新されます。または、次のようになります。
    * Power BI によって、更新する必要があるデータのみが更新されます。 たとえば、10 年間のデータセットの最近の 5 日間のみを更新します。
    * 変更がないかチェックする列を指定している限り、変更されたデータのみが Power BI によって更新されます。

* 更新の信頼性が高くなる - 揮発性のソース システムへの長時間の接続を維持する必要がありません。
* リソースの使用が減る - 更新するデータが少ないと、メモリや他のリソースの全体的な使用が減少します。
* Power BI では可能な限りパーティションに対して並列処理が使用され、これによって、更新が高速になる可能性がある。

これらのいずれの更新シナリオでも、更新が失敗した場合、データは更新されません。つまり、最新の更新が完了するまでデータが古い可能性があります。あるいは、手動で更新すると、エラーなしで完了します。 更新はパーティションまたはエンティティで行われるため、増分更新が失敗した場合、またはあるエンティティでエラーが発生した場合は、更新トランザクション全体が行われません。 別の言い方をすると、特定のデータフローでパーティション (増分更新ポリシー) またはエンティティが失敗した場合、更新操作全体が失敗に設定され、データは更新されません。

## <a name="understanding-and-optimizing-refreshes"></a>更新の理解および最適化

データフローの更新操作がどのように実行されるかをより深く理解するには、 **[データフロー] > [設定] > [更新履歴]** の順に移動して、データフローの **更新履歴** を確認します。 また、 **[ワークスペース] > コンテキスト メニュー (...) > [更新履歴]** でデータフローを選択することもできます。

:::image type="content" source="media/dataflows-understand-optimize-refresh/dataflows-understand-optimize-refresh-01.png" alt-text="データフローの更新履歴のスクリーンショット。":::

**[更新履歴]** には、種類 ( *[オンデマンド]* または *[計画済み]* )、継続時間、実行状態など、更新の概要が表示されます。 CSV ファイルの形式で詳細を表示するには、更新の説明の行の右端にあるダウンロード アイコンを選択します。 ダウンロードした CSV には、次の表に示す属性が含まれています。 Premium 更新では、共有された容量に存在する Pro ベースのデータフローと対比して、追加のコンピューティングおよびデータフロー機能に基づく詳細な情報が提供されます。 そのため、次のメトリックの一部は Premium でのみ使用できます。



| Item | 説明 | Pro | Premium |
| --- | --- | --- | --- |
| 要求日時 | 更新がスケジュールされたか、[今すぐ更新] がクリックされた時刻 (ローカル時間) | ✔ | ✔ |
| データフロー名 | データフローの名前 | ✔ | ✔ |
| データフローの更新の状態 | 完了、失敗、スキップ (エンティティの場合) の状態があります。 スキップが表示される理由は、リンクされたエンティティなどのユース ケースです。 | ✔ | ✔ |
| エンティティ名 | テーブル名 | ✔ | ✔ |
| パーティション名 | これは、データフローが Premium であるかどうかと、Pro は増分更新をサポートしていないので NA と表示するかどうかによって決まります。 Premium では、FullRefreshPolicyPartition または IncrementalRefreshPolicyPartition-[DateRange] が表示されます。 |  | ✔ |
| 更新の状態 | 個々のエンティティまたはパーティションの更新の状態。更新されたデータのそのタイム スライスの状態が示されます。 | ✔ | ✔ |
| 開始時刻 | Premium では、これは、エンティティまたはパーティションに対して処理されるためにデータフローがキューに登録された時刻です。 データフローに依存関係があり、上流のデータフローの結果セットが処理を開始するまで待機する必要がある場合、これは異なることがあります。 | ✔ | ✔ |
| 終了時刻 | これは、データフローのエンティティまたはパーティションが完了した時刻です (該当する場合)。 | ✔ | ✔ |
| Duration | データフローが更新されるまでの合計経過時間 (HH:MM:SS) | ✔ | ✔ |
| 処理された行数 | 特定のエンティティまたはパーティションに対してデータフロー エンジンによってスキャンまたは書き込まれた行数。 コンピューティング エンジンが使用されていない場合や、データが処理されるときにゲートウェイを使用する場合などには、実行した操作に基づいたデータがこれに必ず含まれるとは限りません。 |  | ✔ |
| Bytes processed (処理済みバイト数) | 特定のエンティティまたはパーティションに対してデータフロー エンジンによって書き込まれたデータ (バイト単位)。<br><br>この特定のデータフローでゲートウェイを使用している場合、この情報は提供されないことに注意してください。 |  | ✔ |
| 最大コミット (KB) | 最大コミットは、M クエリが最適化されていない場合に、メモリ不足のエラーの診断に役立つ最大コミット メモリです。<br><br>この特定のデータフローでゲートウェイを使用している場合、この情報は提供されません。 |  | ✔ |
| Processor Time | 特定のエンティティまたはパーティションに対して、データフロー エンジンによる変換の実行にかかった時間 (HH:MM:SS)。<br><br>この特定のデータフローでゲートウェイを使用している場合、この情報は提供されません。 |  | ✔ |
| 待機時間 | 特定のエンティティまたはパーティションに対し、Premium 容量のワークロードに基づいて、エンティティが待機状態であった時間。 |  | ✔ |
| コンピューティング エンジン | 特定のエンティティまたはパーティションに対する更新操作でコンピューティング エンジンがどのように使用されたかに関する詳細。 次の値があります。<br>- NA<br>- 折りたたみ済み<br>- キャッシュ済み<br>- キャッシュ済み + 折りたたみ済み<br><br>これらの要素については、この記事で後ほど詳しく説明します。 |  | ✔ |
| エラー | 該当する場合、詳細なエラー メッセージがエンティティまたはパーティションごとに記述されます | ✔ | ✔ |

## <a name="dataflow-refresh-guidance"></a>データフローの更新に関するガイダンス 

更新統計情報は、データフローのパフォーマンスの最適化と高速化に使用できる貴重な情報を提供します。 以降のセクションでは、いくつかのシナリオと、注意点、提供される情報に基づいて最適化する方法について説明します。

### <a name="orchestration"></a>オーケストレーション

同じワークスペースでデータフローを使用すると、簡単なオーケストレーションを実現できます。 1 つのワークスペースにデータフロー A、B、C があり、A > B > C のようにチェーンが設定されている場合、ソース (A) を更新すると、下流のエンティティも更新されます。 ただし、C を更新する場合は、他のものを個別に更新する必要があります。

Power BI で実行されている管理されたオーケストレーションに適合しない項目をまとめて連結するシナリオの場合、またはうまく組み合わせたい場合は、API を使用するか、Power Automate を使用するか、その両方を使用することができます。 プログラムによる更新については、[API のドキュメント](https://docs.microsoft.com/rest/api/power-bi/dataflows/getdataflowtransactions)と [PowerShell スクリプト](https://github.com/microsoft/powerbi-powershell/tree/master/examples/dataflows)を参照してください。 コードを記述せずにこれを実行できるようにする Power Automate コネクタがあります。 [順次更新](https://docs.microsoft.com/power-query/dataflows/trigger-dataflows-and-power-bi-dataset-sequentially)に関する特定のチュートリアルと合わせて、[詳細なサンプル](https://docs.microsoft.com/power-query/dataflows/dataflow-power-automate-connector-templates)を確認できます。

### <a name="monitoring"></a>監視

この記事で前述した高度な更新統計情報を使用すると、データフローごとの詳細な更新情報を取得できます。 ただし、テナント全体またはワークスペース全体の更新の概要を含めてデータフローを表示する (おそらく監視ダッシュボードを作成する) 場合は、[API](https://docs.microsoft.com/rest/api/power-bi/dataflows) または [Power Automate テンプレート](https://docs.microsoft.com/power-query/dataflows/dataflow-power-automate-connector-templates)を使用できます。 同様に、[単純または複雑な通知の送信](https://docs.microsoft.com/power-query/dataflows/send-notification-when-dataflow-refresh-completes)などのユース ケースでは、Power Automate コネクタを使用するか、Microsoft の API を使用する独自のカスタム アプリケーションを作成できます。

### <a name="timeout-errors"></a>タイムアウト エラー

抽出、変換、および読み込みのシナリオを実行するためにかかる時間を最適化することが理想的です。 Power BI では、次の状況が当てはまります。

* 一部のコネクタには、構成できる明示的なタイムアウト設定があります。 詳細については、[Power Query のコネクタのリファレンス](https://docs.microsoft.com/power-query/connectors/)を参照してください
* Power BI Pro を使用する Power BI データフローでは、エンティティまたはデータフロー自体の中で実行時間の長いクエリのタイムアウトが発生することもあります。 この制限は、Power BI Premium ワークスペースにはありません。

#### <a name="timeout-guidance"></a>タイムアウトに関するガイダンス

Power BI Pro データフローのタイムアウトしきい値は次のとおりです。

* 個々のエンティティのレベルで 2 時間
* データフロー全体のレベルで 3 時間

たとえば、3 つのテーブルを含むデータフローがある場合、各テーブルに 2 時間を超える時間がかかることはなく、継続時間が 3 時間を超えると、データフロー全体がタイムアウトになります。

タイムアウトが発生している場合は、データフロー クエリを最適化することを検討し、ソース システムで[クエリ フォールディング](https://docs.microsoft.com/power-query/power-query-folding)を使用することを検討してください。

これとは別に、Premium Per User (現在プレビュー段階) にアップグレードすることを検討してください。これには、これらのタイムアウトは適用されず、多くの [Power BI Premium Per User の機能](../../admin/service-premium-per-user-faq.md)のおかげでパフォーマンスが向上します。

### <a name="long-durations"></a>長い継続時間

複雑であるか、大規模なデータフローは、最適化が不十分なデータフローのように、更新に時間がかかることがあります。 次のセクションでは、長い更新時間を軽減する方法について説明します。

#### <a name="guidance-for-long-refresh-durations"></a>長い更新時間に関するガイダンス

[データフローのベスト プラクティス](dataflows-best-practices.md)

データフローの長い更新時間を改善するための最初の手順は、[ベスト プラクティス](dataflows-best-practices.md)に従ってデータフローを構築することです。 注目すべきパターンは次のとおりです。

* 他の変換において後で使用できるデータに、[リンクされたエンティティ](https://docs.microsoft.com/power-query/dataflows/linked-entities)を使用する
* [計算されたエンティティを使用して](https://docs.microsoft.com/power-query/dataflows/computed-entities-scenarios)データをキャッシュし、ソース システムでのデータの読み込みとデータ インジェストの負荷を減らす
* データを[ステージング データフロー](https://docs.microsoft.com/power-query/dataflows/best-practices-for-data-warehouse-using-dataflows#staging-dataflows)と[変換データフロー](https://docs.microsoft.com/power-query/dataflows/best-practices-for-data-warehouse-using-dataflows#transformation-dataflows)に分割し、ETL (抽出、変換、読み込み) を別々のデータフローに分離する
* [テーブル拡張操作の最適化](https://docs.microsoft.com/power-query/optimize-expanding-table-columns)
* [複雑なデータフローに関するガイダンス](https://docs.microsoft.com/power-query/dataflows/best-practices-developing-complex-dataflows)に従う

次に、これは、増分更新を使用できるかどうかを評価するために役立てることができます。

[増分更新](../../connect-data/incremental-refresh-overview.md)を使用すると、パフォーマンスを向上させることができます。 更新操作のためにクエリが送信されるときに、パーティション フィルターがソース システムにプッシュされることが重要です。 フィルタリングをプッシュ ダウンすることは、データ ソースでクエリ フォールディングがサポートされている必要があることを意味します。または、Power Query によるファイルまたはフォルダーの除外やフィルター処理に役立つビジネス ロジックを、関数またはその他の方法を使用して表現できます。 SQL クエリをサポートするほとんどのデータ ソースでは、クエリ フォールディングがサポートされており、一部の OData フィードではフィルタリングもサポートされています。 

ただし、フラット ファイル、BLOB、API などのデータ ソースでは通常、フィルタリングはサポートされていません。 フィルターがデータ ソース バックエンドでサポートされていない場合は、プッシュ ダウンできません。 そのような場合、フィルターはマッシュアップ エンジンによってローカルで補正および適用されます。これには、データ ソースから完全なデータセットを取得することが必要な場合があります。 これにより、増分更新が非常に低速になり、Power BI サービスまたはオンプレミスのデータ ゲートウェイ (使用されている場合) でプロセスがリソース不足になる可能性があります。

各データ ソースでさまざまなレベルのクエリ フォールディングがサポートされている場合は、ソースのクエリにフィルター ロジックが含まれていることを確認するために検証を実行することをお勧めします。 これを簡単にするために、Power BI では、[Power Query Online のステップ フォールディング インジケーター](https://powerbi.microsoft.com/blog/step-folding-indicators-for-power-query-online/)を使用して、この検証の実行が試行されます。 これらの最適化の多くは設計時に行われますが、更新が行われた後、更新のパフォーマンスを分析して最適化する機会があります。

最後に、環境を最適化することを検討します。 次の最適化を行って、容量のスケール アップ、データ ゲートウェイの適切なサイズ設定、ネットワーク待機時間の短縮を行うことで、Power BI 環境を最適化できます。

* Power BI Premium または Premium Per User で使用可能な容量を使用する場合は、Premium インスタンスを増やすか、その中身を別の容量に割り当てることで、パフォーマンスを向上させることができます。

* インターネット経由で直接利用できないデータに Power BI がアクセスする必要がある場合は、必ずゲートウェイが必要です。 オンプレミスのサーバーまたは仮想マシンに[オンプレミス データ ゲートウェイ](../../connect-data/service-gateway-onprem.md)をインストールできます。
      * ゲートウェイのワークロードとサイズ設定の推奨事項について理解するには、「[オンプレミス データ ゲートウェイのサイズ設定](../../guidance/gateway-onprem-sizing.md)」をご覧ください。
      * また、データを最初にステージング データフローに取り込み、リンクおよび計算されたエンティティを使用して下流で参照することについて評価します。

* ネットワーク待機時間は、要求が Power BI サービスに到達するまでに要する時間と、応答の配信に要する時間が増えることで、更新のパフォーマンスに影響を及ぼす可能性があります。 Power BI のテナントは、特定のリージョンに割り当てられています。 ご自身のテナントが配置されている場所を特定するには、「[Power BI テナントの場所](../../admin/service-admin-where-is-my-tenant-located.md)」をご覧ください。 テナントのユーザーが Power BI サービスにアクセスすると、彼らの要求は常にそのリージョンにルーティングされます。 要求が Power BI サービスに到達したときに、サービスから追加の要求が送信されることがあります (たとえば、基になるデータ ソースやデータ ゲートウェイに対して)。これもネットワーク待機時間の影響を受けます。
    * [Azure Speed Test](https://azurespeedtest.azurewebsites.net/) などのツールによって、クライアントと Azure リージョン間のネットワーク待機時間の表示が提供されます。 一般に、ネットワーク待機時間の影響を最小限に抑えるには、データ ソース、ゲートウェイ、および Power BI クラスターをできるだけ近くに配置するようにします。 同じリージョンに置くことをお勧めします。 ネットワーク待機時間が問題になっている場合は、ゲートウェイとデータ ソースをクラウドでホストされる仮想マシン内に配置することで、Power BI クラスターにより近い位置に配置してみてください。

### <a name="high-processor-time"></a>長いプロセッサ時間

プロセッサ時間が長いと思われる場合、適用されている保有ステップの数または行っている変換の種類が原因で、折りたたまれていない高コストの変換が存在する可能性があります。それぞれの原因によって、更新時間が長くなる場合があります。

#### <a name="guidance-for-high-processor-time"></a>長いプロセッサ時間に関するガイダンス

長いプロセッサ時間を最適化するための 2 つのオプションがあります。

まず、データ ソース自体の中でクエリ フォールディングを使用します。これにより、データフロー コンピューティング エンジンの負荷が直接軽減されます。 データ ソース内でのクエリ フォールディングにより、ソース システムでほとんどの作業が実行できるようになるため、最初のクエリの後にメモリ内のすべての計算を実行することなく、データフローがソースのネイティブ言語でクエリをパス スルーできるようになります。

すべてのデータ ソースでクエリ フォールディングを実行できるわけではありません。また、クエリ フォールディングが可能な場合でも、ソースに折りたたむことができない特定の変換を実行するデータフローが存在する可能性があります。 このような場合、特に変換のパフォーマンスを場合によっては最大 25 倍向上させるために Power BI によって採用される機能が、[拡張コンピューティング エンジン](https://docs.microsoft.com/power-bi/transform-model/dataflows/dataflows-premium-workload-configuration#guidance-for-common-scenarios)です。

### <a name="using-the-compute-engine-to-maximize-performance"></a>コンピューティング エンジンを使用してパフォーマンスを最大限に高める

Power Query では、設計時にクエリ フォールディングが表示されますが、[Compute Engine]\(コンピューティング エンジン\) 列には、内部エンジン自体が使用されているかどうかの詳細が表示されます。 コンピューティング エンジンは、複雑なデータフローが存在し、メモリ内で変換を実行している場合に便利です。 このような場合に、エンジン自体が使用されたかどうかの詳細が [Compute Engine]\(コンピューティング エンジン\) 列に表示されるので、高度な更新統計情報が役立つ可能性があります。

以降のセクションでは、コンピューティング エンジンとその統計情報の使用に関するガイダンスを提供します。

#### <a name="guidance-on-compute-engine-statuses"></a>コンピューティング エンジンの状態に関するガイダンス

拡張コンピューティング エンジンをオンにし、さまざまな状態を理解すると、役に立ちます。 内部的には、拡張コンピューティング エンジンは SQL データベースを使用してデータを読み取り、格納します。 ここでクエリ エンジンに対して変換を実行することをお勧めします。 以下の段落では、さまざまな状況と、それぞれの場合にすべきことについてのガイダンスを示します。

**NA** - この状態は、コンピューティング エンジンが使用されなかったことを意味します。その理由は次のいずれかです: Power BI Pro データフローを使用している。これを明示的にオフにしている。データ ソースでクエリ フォールディングを使用している。または、クエリの高速化に使用される SQL エンジンを使用できない複雑な変換を実行している。

長い継続時間が発生していて、依然として状態が **[NA]** である場合は、これが [オンになっていて](dataflows-premium-workload-configuration.md)、誤ってオフになっていないことを確認してください。 推奨されるパターンの 1 つは、[ステージング データフローを使用して最初にデータを Power BI サービスに取リ込み、このデータがステージング データフロー内に入ったら、次にこの上にデータフローを構築することです](https://docs.microsoft.com/power-query/dataflows/best-practices-developing-complex-dataflows#split-data-transformation-dataflows-from-stagingextraction-dataflows)。 このパターンにより、ソース システムの負荷が軽減され、コンピューティング エンジンと共に、変換の速度を上げ、パフォーマンスを向上させることができます。

**キャッシュ済み** - **キャッシュ済み** の状態が表示される場合、データフロー データはコンピューティング エンジンに格納されたので、別のクエリの一部として参照できます。 これは、リンクされたエンティティとしてそれを使用している場合に最適です。そのデータが下流で使用するためにキャッシュされており、同じデータフローで複数回更新される必要がないためです。 これは、DirectQuery にそれを使用する場合にも最適である可能性があります。

キャッシュされた場合、初期インジェストへのパフォーマンスの影響は、後で同じデータフローまたは同じワークスペース内の異なるデータフローで良い結果をもたらします。

エンティティに対する時間が長い場合は、コンピューティング エンジンをオフにすることを検討してください。 Power BI は、エンティティをキャッシュするために、ストレージおよび SQL に書き込みます。 単一使用エンティティの場合、ユーザーにとってのパフォーマンス上の利点は、二重インジェストの不利益を受けるだけの価値がない可能性があります。

**折りたたみ済み** - 折りたたみ済みは、データフローでデータの読み込みに SQL コンピューティングを使用できたことを意味します。 計算されたエンティティは SQL のテーブルを使用してデータを読み取ったので、使用された SQL はクエリの構造に関連付けられています。

折りたたみ済み状態が表示されるのは、オンプレミスまたはクラウドのデータ ソースを使用しているときに、最初にデータをステージング データフローに読み込んで、このデータフローで参照した場合です。 この状態は、別のエンティティを参照するエンティティにのみ適用されます。 これは、クエリが SQL エンジンの上で実行されたことを意味するため、SQL コンピューティングを使用すると、改善される可能性があります。 変換が SQL エンジンによって処理されるようにするには、クエリ エディターでマージ (結合)、グループ化 (集計)、追加 (和集合) アクションなど、SQL フォールディングをサポートする変換を使用します。

**キャッシュ済み + 折りたたみ済み** - **キャッシュ済み + 折りたたみ済み** が表示される場合は、別のエンティティを参照し、かつ別のエンティティの上流によって参照されているエンティティがあるため、データ更新が最適化されている可能性があります。 これは、SQL の上でも実行されます。そのため、SQL コンピューティングを使用すると、改善される可能性もあります。 実現可能である最適なパフォーマンスが得られるようにするには、クエリ エディターでマージ (結合)、グループ化 (集計)、追加 (和集合) アクションなど、SQL フォールディングをサポートする変換を使用します。

### <a name="guidance-for-compute-engine-performance-optimization"></a>コンピューティング エンジンのパフォーマンスの最適化に関するガイダンス

次の手順を実行すると、ワークロードによってコンピューティング エンジンがトリガーできるようになるため、常にパフォーマンスが向上します。

**計算されたエンティティおよびリンクされたエンティティが同じワークスペース内にある場合:**

"*インジェスト*" に関しては、データセット全体のサイズを小さくする場合にのみフィルターを使用して、できるだけ早くストレージにデータを取り込むことに集中します。 変換ロジックはこの手順とは別に保持します。 次に、リンクまたは計算されたエンティティを使用して、変換とビジネス ロジックを同じワークスペース内の別個のデータフローに分割します。これにより、エンジンがアクティブ化し、計算を高速化することができます。 簡単な例えでは、厨房での食品の準備のようなものです。通常、食品の準備は素材を集めることとは異なる別の手順であり、食品をオーブンに入れるための前提条件となります。 同様に、コンピューティング エンジンを利用するには、ロジックを別個に準備する必要があります。

フォールドする操作 (結合、結合、変換、および[その他](https://docs.microsoft.com/power-query/power-query-folding#transformations-that-can-achieve-folding)の操作など) を確実に実行してください。

また、[公開されているガイドラインと制限事項の範囲内](dataflows-features-limitations.md#dataflows-in-premium)でデータフローを構築します。

**コンピューティング エンジンはオンになっているがパフォーマンスが低下している場合:**

コンピューティング エンジンがオンになっていても、パフォーマンスの低下が見られるシナリオについて調べる場合は、次の手順を行います。

* ワークスペース全体に存在する計算されたエンティティおよびリンクされたエンティティを制限します。
* コンピューティング エンジンをオンにした状態で最初の更新が実行されると、データはレイク "*および*" キャッシュに書き込まれます。 この二重書き込みにより、更新が遅くなります。
* 複数のデータフローにリンクされているデータフローがある場合は、すべての更新が同時に行われないように、必ずソース データフローの更新をスケジューリングしてください。

## <a name="considerations-and-limitations"></a>考慮事項と制限事項

Power BI Pro ライセンスを使用する場合、データフローの更新は 1 日あたり 8 回の更新に制限されます。

## <a name="next-steps"></a>次のステップ

* [データフローでの増分更新の使用](https://docs.microsoft.com/power-query/dataflows/incremental-refresh)
* [データセットの増分更新](../../connect-data/incremental-refresh-overview.md)
* [更新に関するトラブルシューティング シナリオ](../..//connect-data/refresh-troubleshooting-refresh-scenarios.md)
* [データフローのベスト プラクティス](dataflows-best-practices.md)
* [データフローの Premium 機能](dataflows-premium-features.md)
* [データフローの制限事項、制約、サポートされているコネクタと機能](dataflows-features-limitations.md)
* [更新に関するトラブルシューティング シナリオ](../../connect-data/refresh-troubleshooting-refresh-scenarios.md)