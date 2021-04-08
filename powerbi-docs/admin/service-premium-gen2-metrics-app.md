---
title: Power BI Premium Gen2 Metrics アプリ (プレビュー)
description: Power BI Premium Gen2 Metrics アプリを使用して、Power BI Premium Gen2 容量を管理およびトラブルシューティングする方法について説明します。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-premium
ms.topic: how-to
ms.date: 03/25/2021
LocalizationGroup: Premium
ms.openlocfilehash: 1265c6c9006e50c5f146c035bacfe3c48d1af8cd
ms.sourcegitcommit: 438eea031f1ed9e9dee510520e5c1039920c3a49
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2021
ms.locfileid: "105099889"
---
# <a name="power-bi-premium-gen2-metrics-app-preview"></a>Power BI Premium Gen2 Metrics アプリ (プレビュー)

**Power BI Premium Gen2 (プレビュー)** のリリースにより、Premium 容量の管理がより容易になっています。 Premium Gen2 容量の使用の管理をさらに容易にするために、Power BI には、この記事で **Premium Gen2 Monitoring App** と呼ばれているセルフサービス監視アプリが用意されています。 

**Premium Gen2 Monitoring App** は、容量リソース使用の原因を明らかにする単純な使用データを提供し、容量のニーズを計画したり、リソースの需要の変化を通知したりできるようにします。

## <a name="install-the-gen2-monitoring-app"></a>Gen2 監視アプリをインストールする

容量管理者は、**Premium Gen2 Monitoring App** アプリを [リンクの場所](https://aka.ms/GenutilizationInstall)から取得するか、Power BI サービスの **[アプリ]** セクションを選択して **[アプリの取得]** ボタンを選択し、「**Premium Gen 2 Capacity Utilization Metrics**」を検索して取得できます。 

:::image type="content" source="media/service-premium-gen2-metrics-app/premium-gen2-metrics-app-01.png" alt-text="[アプリの取得] ボタンの選択のスクリーンショット":::

## <a name="using-the-gen2-monitoring-app"></a>Gen2 監視アプリの使用

**Premium Gen2 Monitoring App** がインストールされたら、アプリを起動し、レポートの上部にある **[データへの接続]** メッセージを選択して、Premium Gen2 容量からのデータの読み込みをトリガーします。 容量に接続するには、2 つのパラメーターを指定する必要があります。

* **容量 ID**
* 使用状況を読み込む日数。 

**容量 ID** は、Power BI 管理ポータルの URL 内にあります。 これは URL の ```/capacity/``` 部分の後の値であり、次の画像に示すような内容です。

:::image type="content" source="media/service-premium-gen2-metrics-app/premium-gen2-metrics-app-02.png" alt-text="URL 内の容量 ID のスクリーンショット":::

レポートに表示する **使用状況の日数** を選択する際は、実行する分析を反映する値を選択します。 たとえば、容量のユーザーに請求するために月単位の使用状況を分析している場合は、30 日から 45 日間のデータを読み込むことを選択できます。

これらのパラメーターを送信すると、**Premium Gen2 Monitoring App** によってデータが読み込まれ、ビューが更新されます。 更新が完了するまで数分かかることがあります。

更新されたら、レポートを開きます。 右側に 2 つのグラフがあります。

* 各日に使用された仮想コア数を示す、 **[Daily peak usage]\(毎日のピーク時の使用状況\)** と呼ばれる折れ線グラフおよび積み上げ縦棒グラフ。
* 容量内のワークスペース別の使用率を示す、 **[Total by workspace ID and operation]\(ワークスペース ID と操作別の合計\)** と呼ばれる積み上げ横棒グラフ。

**[Daily peak usage]\(毎日のピーク時の使用状況\)** グラフには、日ごとの使用可能な仮想コア合計数が縦棒として表示され、その日に記録された最大仮想コア使用率が線として表示されます。 グラフを操作するには、任意の縦棒を選択して、選択した日に対してレポートをフィルター処理します。

:::image type="content" source="media/service-premium-gen2-metrics-app/premium-gen2-metrics-app-03.png" alt-text="[Daily peak usage]\(毎日のピーク時の使用状況\) グラフのスクリーンショット":::

**[Total by workspace ID and operation]\(ワークスペース ID と操作別の合計\)** には、容量のワークスペース別に分類された使用率が示されます。 このビジュアルは、特定の事業単位で使用されているワークスペースの使用量に比例したコストを帰属させることで、組織内での内部のチャージバックを確立するのに役立ちます。

:::image type="content" source="media/service-premium-gen2-metrics-app/premium-gen2-metrics-app-04.png" alt-text="ワークスペース ID と操作別の合計グラフのスクリーンショット":::

## <a name="understanding-usage-patterns"></a>使用パターンの把握

各日の使用パターンを把握するには、 **[Daily peak usage]\(毎日のピーク時の使用状況\)** ビジュアルで任意の日を選択します。 次の画像では、*Feb 04* の日にちが選択されています。

:::image type="content" source="media/service-premium-gen2-metrics-app/premium-gen2-metrics-app-05.png" alt-text="1 日が選択された [Daily peak usage]\(毎日のピーク時の使用状況\) グラフのスクリーンショット":::

レポートの右側には、その日の一日の使用パターンが 15 分間隔で表示されます。 各ビジュアルの左上隅には回転ホイール アイコンがあり、これはデータがグラフに読み込まれているときに回転し続けます。 グラフのレンダリングには有意のデータが必要であるため、データが完全に読み込まれるように、ホイール アイコンが回転していないことを確認してください。

:::image type="content" source="media/service-premium-gen2-metrics-app/premium-gen2-metrics-app-06.png" alt-text="[Daily peak usage]\(毎日のピーク時の使用状況\) グラフの選択した日に関する詳細のスクリーンショット":::

### <a name="interactive-and-background-operations"></a>インタラクティブおよびバックグラウンドの操作

**Premium Gen2 Monitoring App** 全体にわたって、さまざまな成果物からの 2 種類の使用率の値 ("*対話的*" と "*バックグラウンド*") が表示されます。 "*対話的な*" 操作には、リアルタイムでレンダリングされるレポート ビューや対話が含まれます。 "*バックグラウンド*" 操作には、データセットとデータフローの更新が含まれます。

"*バックグラウンド*" 操作は通常、CPU 使用率のスパイクをもたらし、完了するまでにより長い時間がかかります。このため、バックグラウンド操作の使用が、それらが完了した時刻から 24 時間にわたって分散しています。 前の画像に示されている、詳細グラフの薄い青色の線は、全体的なバックグラウンド使用率の値が、その 1 日を通してわずかだけ変化したことを表しています。 これは、各バックグラウンド操作の 24 時間分散が原因です。

"*対話的な*" 使用率は、操作の完了時に計算されます。 Power BI によって、単一の操作が容量を超えないように徹底されます。対話的な操作の使用率がそうなるほど高い場合、そのコストは次の分間に分散されます。 グラフの濃い青の線は、1 日を通した対話的な使用率を示しています。

**Premium Gen2 Monitoring App** の右下に概要ビジュアルのコレクションがあり、選択した日のピーク時の使用率、ピークが発生した時刻、そのピークのどれだけの割合が対話的またはバックグラウンドのいずれかの操作だったかが表示されます。 次の画像は、概要ビジュアルを示しています。

:::image type="content" source="media/service-premium-gen2-metrics-app/premium-gen2-metrics-app-07.png" alt-text="選択した日の使用率の概要データのスクリーンショット":::

### <a name="getting-more-detail"></a>より多くの詳細の取得

グラフ内の特定のデータ ポイントに関する詳細情報を表示するには、データ ポイントを **CTRL キーを押しながらクリック** して、その下に表示されるテーブルにフィルターを適用します。これにより、その 15 分間に容量の使用の一因となった成果物が表示されます。 このテーブルには、成果物 (データセット、データフロー、またはその他の項目)、操作、およびそれを開始したユーザーが含まれます。 次の画像は、**CTRL キーを押しながらクリック** を行った結果を示しています。

:::image type="content" source="media/service-premium-gen2-metrics-app/premium-gen2-metrics-app-08.png" alt-text="選択した期間のテーブル詳細情報のスクリーンショット":::

**Premium Gen2 Monitoring App** のデータセットを使用して、カスタマイズされたレポートを作成したり、他のレポートから使用率データに接続したりできます。 データセットは夜間に更新されます。


## <a name="use-a-single-app-for-all-capacities"></a>すべての容量に 1 つのアプリを使用する

1 つの **Gen2 監視アプリ** を作成して、すべての Power BI Premium Gen2 容量を監視できます。 次の手順では、アプリを作成する方法について説明します。

1. **新しいワークスペースを作成します。** 新しいワークスペースはアプリとして公開され、Premium Gen2 容量を監視するすべてのレポートを含みます。 ワークスペースには好きな名前を付けることができますが、*Capacity monitoring* などのわかりやすい名前を付けることをお勧めします。

    :::image type="content" source="media/service-premium-gen2-metrics-app/premium-gen2-metrics-app-09.png" alt-text="Capacity monitoring という名前の新しいワークスペースの作成のスクリーンショット":::

2. 監視する Premium Gen2 容量ごとに新しいアプリを作成し、各アプリの名前を容量の名前または容量 ID に変更するか、それらを区別できるようにするその他の名前付け規則を使用します。 複数のバージョンのアプリをインストールする場合は、次の画像に示す **[新しいワークスペースにインストールする]** を選択します。

    :::image type="content" source="media/service-premium-gen2-metrics-app/premium-gen2-metrics-app-10.png" alt-text="新しいワークスペースへのアプリのインストールのスクリーンショット":::

3. 前の手順で作成した各アプリを開き、対応する Premium Gen2 容量のデータに各アプリを接続します。 作成したそれぞれのアプリに、対応する **容量 ID** を指定します。

    :::image type="content" source="media/service-premium-gen2-metrics-app/premium-gen2-metrics-app-11.png" alt-text="各アプリを対応する容量に接続しているスクリーンショット":::

4. レポートの容量の "*コピー*" を保存できるように各アプリを編集します。 編集するには、**鉛筆** アイコンを選択し、 **[はい、ワークスペースに移動します]** を選択します。

    :::image type="content" source="media/service-premium-gen2-metrics-app/premium-gen2-metrics-app-12.png" alt-text="ワークスペースの編集":::

    名前の横にある **その他** メニューを選択し、 **[コピーの保存]** を選択します。

    :::image type="content" source="media/service-premium-gen2-metrics-app/premium-gen2-metrics-app-13.png" alt-text="レポートのコピーのスクリーンショット":::    
    
    レポートのコピーの保存先とするワークスペースを選択する際は、**手順 1** で作成したワークスペースをそのコピー先として選択します。 また、レポートが属する特定の Premium Gen2 容量を識別するために、レポートの名前を適切に変更する必要があります。

    :::image type="content" source="media/service-premium-gen2-metrics-app/premium-gen2-metrics-app-14.png" alt-text="レポートのコピーの保存のスクリーンショット":::

5. 次に、**手順 1** で作成したワークスペースをアプリとして公開します。 この例では、2 つの Premium Gen2 容量レポートを統合ワークスペースとアプリに公開しています。 アプリの説明を入力する必要があります。 最初に、左上隅の **[アプリの作成]** を選択します。

    :::image type="content" source="media/service-premium-gen2-metrics-app/premium-gen2-metrics-app-15.png" alt-text="新しいアプリの作成のスクリーンショット":::

    表示されたダイアログで **[公開]** を選択します。

    :::image type="content" source="media/service-premium-gen2-metrics-app/premium-gen2-metrics-app-16.png" alt-text="ダイアログでの公開の選択のスクリーンショット":::

6. アプリが公開されたら、アプリに直接アクセスしたり、リンクをコピーしたりできます。

    :::image type="content" source="media/service-premium-gen2-metrics-app/premium-gen2-metrics-app-17.png" alt-text="公開されたアプリのリンクのスクリーンショット":::

完了すると、作成したワークスペース アプリにコピーした各レポートが表示されます。 この例では、2 つのアプリを作成し、**手順 1** で作成した新しいワークスペースにコピーしました。これで、両方のワークスペース監視レポートをすべて 1つのレポートに表示する統合アプリを設定できました。

:::image type="content" source="media/service-premium-gen2-metrics-app/premium-gen2-metrics-app-18.png" alt-text="統合された容量アプリのスクリーンショット":::

これで、Premium Gen2 容量を監視するための統合アプリが完成しました。

アプリの共有の詳細、または考慮事項と制限事項については、次の各記事を参照してください。

* [他のワークスペースからレポートをコピーする](../connect-data/service-datasets-copy-reports.md)
* [ワークスペース全体のデータセットの概要](../connect-data/service-datasets-across-workspaces.md)

## <a name="next-steps"></a>次のステップ

* [Power BI Premium とは](service-premium-what-is.md)
* [Power BI Premium のよく寄せられる質問](service-premium-faq.md)
* [Power BI Premium Per User に関する FAQ (プレビュー)](service-premium-per-user-faq.md)

