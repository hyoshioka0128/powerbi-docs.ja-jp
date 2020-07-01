---
title: 配置パイプラインのトラブルシューティング
description: Power BI の配置パイプラインに関するトラブルシューティングを行います
author: KesemSharabi
ms.author: kesharab
ms.topic: troubleshooting
ms.service: powerbi
ms.subservice: powerbi-service
ms.date: 05/06/2020
ms.openlocfilehash: e41a13fac3e0ffea5171d2927cc0f3b9debbeef1
ms.sourcegitcommit: a453ba52aafa012896f665660df7df7bc117ade5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "85485877"
---
# <a name="deployment-pipelines-troubleshooting-preview"></a>配置パイプラインのトラブルシューティング (プレビュー)

この記事では、配置パイプラインの問題のトラブルシューティングについて説明します。

## <a name="general"></a>全般

### <a name="whats-deployment-pipelines-in-power-bi"></a>Power BI の配置パイプラインとはどのようなものですか。

Power BI の配置パイプラインがどのようなものであるかを理解するには、[配置パイプラインの概要](deployment-pipelines-overview.md)に関するページを参照してください。

### <a name="how-do-i-get-started-with-deployment-pipelines"></a>配置パイプラインの使用を開始するにはどうすればよいですか。

配置パイプラインの使用を開始するには、[使用開始の手順](deployment-pipelines-get-started.md)を利用してください。

### <a name="why-cant-i-see-the-deployment-pipelines-button"></a>配置パイプラインのボタンが表示されないのはなぜですか。

以下の条件が満たされていない場合は、配置パイプラインのボタンを表示することができません。

* Power BI の [Pro ユーザー](../admin/service-admin-purchasing-power-bi-pro.md)である

* Premium 容量を持つ組織に属している

* ワークスペースは、1 つのパイプラインにのみ割り当てることができる

* 自分が新しいワークスペースの管理者である

## <a name="licensing"></a>ライセンス

### <a name="what-licenses-are-needed-to-work-with-deployment-pipelines"></a>配置パイプラインを操作するには、どのようなライセンスが必要ですか。

配置パイプラインを使用するには、[Premium 容量](../admin/service-premium-what-is.md)を持つ [Pro ユーザー](../admin/service-admin-purchasing-power-bi-pro.md)である必要があります。 詳細については、「[配置パイプラインへのアクセス](deployment-pipelines-get-started.md#accessing-deployment-pipelines)」を参照してください。

### <a name="what-type-of-capacity-can-i-assign-to-a-workspace-in-a-pipeline"></a>パイプラインのワークスペースには、どのような種類の容量を割り当てることができますか。

パイプラインを機能させるには、配置パイプライン内のすべてのワークスペースが専用の容量内に存在する必要があります。 ただし、パイプライン内の異なるワークスペースに対して、異なる容量を使用できます。 また、同じパイプライン内の異なるワークスペースに対して、異なる容量の種類を使用することもできます。

開発とテストでは、ユーザーごとの Pro Power BI アカウントと共に A または EM 容量を使用できます。

運用ワークスペースの場合は、P 容量が必要です。 ISV が埋め込みアプリケーションを使用してコンテンツを配布する場合は、運用環境で A または EM 容量を使用することもできます。

## <a name="technical"></a>技術的な質問

### <a name="why-cant-i-see-all-my-workspaces-when-i-try-to-assign-a-workspace-to-a-pipeline"></a>パイプラインにワークスペースを割り当てようとするときに、一部のワークスペースが表示されないのはなぜですか。

パイプラインにワークスペースを割り当てるには、以下の条件を満たす必要があります。

* ワークスペースが[新しいワークスペース エクスペリエンス](../collaborate-share/service-create-the-new-workspaces.md)である

* 自分がワークスペースの管理者である

* ワークスペースが他のパイプラインに割り当てられていない

* ワークスペースが [Premium 容量](../admin/service-premium-what-is.md)上にある

これらの条件を満たしていないワークスペースは、選択できるワークスペースの一覧に表示されません。

### <a name="how-can-i-assign-workspaces-to-all-the-stages-in-a-pipeline"></a>パイプラインのすべてのステージにワークスペースを割り当てるにはどうすればよいですか。

パイプラインごとに、1 つのワークスペースを割り当てることができます。 ワークスペースがパイプラインに割り当てられたら、それを次のパイプライン ステージに配置できます。 最初の配置時に、ソース ステージの項目のコピーを使用して新しいワークスペースが作成されます。 コピーされた項目間のリレーションシップは保持されます。 詳細については、[配置パイプラインにワークスペースを割り当てる](deployment-pipelines-get-started.md#step-2---assign-a-workspace-to-a-deployment-pipeline)方法に関するページを参照してください。

### <a name="why-did-my-first-deployment-fail"></a>最初の配置が失敗したのですが、なぜでしょうか。

最初の配置が失敗した原因として、さまざまなものが考えられます。 それらの理由の一部を次の表に示します。

|Error  |アクション  |
|---------|---------|
|[Premium 容量のアクセス許可](deployment-pipelines-process.md#creating-a-premium-capacity-workspace)がない。     |Premium 容量のアクセス許可を取得するには、容量管理者にワークスペースを容量に追加するように依頼するか、容量に対する割り当てアクセス許可を要求します。 ワークスペースが容量に追加されたら、再配置します。        |
|ワークスペースに対するアクセス許可がない。     |配置するには、ワークスペース メンバーになっている必要があります。 ワークスペース管理者に、適切なアクセス許可を付与するよう依頼します。         |
|Power BI 管理者がワークスペースの作成を無効にしている。     |Power BI 管理者に連絡してサポートを依頼します。         |
|ワークスペースが[新しいワークスペース エクスペリエンス](../collaborate-share/service-create-the-new-workspaces.md)でない。     |新しいワークスペース エクスペリエンスでコンテンツを作成します。 クラシック ワークスペースにコンテンツがある場合は、新しいワークスペース エクスペリエンスに[アップグレード](../collaborate-share/service-upgrade-workspaces.md)できます。         |
|[選択的配置](deployment-pipelines-get-started.md#selective-deployment)を使用しており、コンテンツのデータセットを選択していない。     |次のいずれかの操作を行います。 </br></br>データセットにリンクされているコンテンツの選択を解除します。 選択されていないコンテンツ (レポートやダッシュボードなど) は、次のステージにコピーされません。 </br></br>選択したコンテンツにリンクされているデータセットを選択します。 データセットが次のステージにコピーされます。         |

### <a name="im-getting-a-warning-that-i-have-unsupported-artifacts-in-my-workspace-when-im-trying-to-deploy-how-can-i-know-which-artifacts-are-not-supported"></a>配置を試みているときに、自分のワークスペースに "サポートされていない成果物" があることを示す警告が表示されます。 どの成果物がサポートされていないかを知るには、どうすればよいですか。

配置パイプラインでサポートされていない項目と成果物の包括的な一覧については、以下のセクションを参照してください。

* [サポートされていない項目](deployment-pipelines-process.md#unsupported-items)

* [コピーされない項目のプロパティ](deployment-pipelines-process.md#item-properties-that-are-not-copied)

### <a name="why-did-my-deployment-fail-due-to-broken-rules"></a>ルールの破損により配置が失敗したのはなぜですか。

データセット ルールの構成で問題が発生した場合は、[データセット ルール](deployment-pipelines-get-started.md#step-4---create-dataset-rules)にアクセスし、[データセット ルールの制限事項](deployment-pipelines-get-started.md#dataset-rule-limitations)に従っていることを確認してください。

以前は配置が成功していて、破損したルールによって突然失敗した場合は、再発行されているデータセットが原因である可能性があります。 ソース データセットに対して以下の変更を行うと、配置が失敗します。

**パラメーター ルール**

* パラメーターの削除

* パラメーター名の変更

**データ ソース ルール**

データセット ルールに値がありません。 この問題は、データセットが変更された場合に発生する可能性があります。

![破損したルール](media/deployment-pipelines-troubleshooting/broken-rule.png)

以前は成功した配置が、破損したリンクのために失敗する場合は、警告が表示されます。 **[ルールの構成]** をクリックすると、失敗したデータセットがマークされている配置設定ペインに移動できます。 データセットをクリックすると、破損したルールがマークされます。

正常に配置するには、破損したルールを修正または削除し、再配置します。

### <a name="how-can-i-change-the-data-source-in-the-pipeline-stages"></a>パイプライン ステージのデータ ソースを変更するにはどうすればよいですか。

Power BI サービスでは、データ ソース接続を変更することはできません。

テスト ステージまたは運用ステージでデータ ソースを変更する場合は、[データセット ルール](deployment-pipelines-get-started.md#step-4---create-dataset-rules)または [API](https://docs.microsoft.com/rest/api/power-bi/datasets/updateparametersingroup) を使用できます。 データセット ルールは、次回の配置後にのみ有効になります。

### <a name="i-fixed-a-bug-in-production-but-now-i-cant-click-the-deploy-to-previous-stage-button-why-is-it-greyed-out"></a>運用環境でバグを修正しましたが、[deploy to previous stage]\(前のステージに配置する\) ボタンをクリックできなくなりました。 淡色表示になったのはなぜですか。

逆方向に配置できるのは、配置先が空のステージである場合のみです。 テスト ステージにコンテンツがある場合は、運用環境から逆方向に配置することはできません。

パイプラインの作成後は、開発ステージを使用してコンテンツを開発し、テスト ステージを使用してそれを確認し、テストしてください。 これらのステージでバグを修正したうえで、修正した環境を運用ステージに配置できます。

>[!NOTE]
>逆方向の配置では、[完全配置](deployment-pipelines-get-started.md#deploying-all-content)のみがサポートされます。 [選択的配置](deployment-pipelines-get-started.md#selective-deployment)はサポートされていません

### <a name="does-deployment-pipelines-support-multi-geo"></a>配置パイプラインでは Multi-Geo はサポートされていますか。

Multi-Geo はサポートされています。 異なる geo のステージ間でコンテンツを配置するのには、時間がかかることがあります。

## <a name="permissions"></a>アクセス許可

### <a name="what-is-the-deployment-pipelines-permissions-model"></a>配置パイプラインのアクセス許可モデルとはどのようなものですか。

配置パイプラインのアクセス許可モデルについては、「[アクセス許可](deployment-pipelines-process.md#permissions)」のセクションで説明されています。

### <a name="who-can-deploy-content-between-stages"></a>ステージ間でコンテンツを配置できるのはだれですか。

コンテンツは、空のステージにも、コンテンツを含むステージにも配置できます。 コンテンツは、[Premium 容量](../admin/service-premium-what-is.md)に存在する必要があります。

* **空のステージへの配置** - ソース ワークスペースのメンバーまたは管理者であるすべての [Pro ユーザー](../admin/service-admin-purchasing-power-bi-pro.md)。

* **コンテンツがあるステージへの配置** - ソース配置ステージとターゲット配置ステージの両方でワークスペースのメンバーまたは管理者であるすべての [Pro ユーザー](../admin/service-admin-purchasing-power-bi-pro.md)。

* **データセットのオーバーライド** - 配置では、データセットが変更されなかった場合でも、ターゲット ステージに含まれる各データセットがオーバーライドされます。 ユーザーは、配置で指定されたすべてのターゲット ステージ データセットの所有者である必要があります。

### <a name="which-permissions-do-i-need-to-configure-dataset-rules"></a>データセット ルールを構成するには、どのようなアクセス許可が必要ですか。

配置パイプラインでデータセット ルールを構成するには、データセットの所有者である必要があります。

### <a name="why-cant-i-see-workspaces-in-the-pipeline"></a>パイプラインのワークスペースが表示されないのですが、なぜでしょうか。

パイプラインのアクセス許可とワークスペースのアクセス許可は、別々に管理されます。 パイプラインのアクセス許可を持っていても、ワークスペースのアクセス許可を持っていない可能性があります。 詳細については、「[アクセス許可](deployment-pipelines-process.md#permissions)」のセクションを参照してください。

## <a name="next-steps"></a>次の手順

>[!div class="nextstepaction"]
>[配置パイプラインの概要](deployment-pipelines-overview.md)

>[!div class="nextstepaction"]
>[配置パイプラインの使用を開始する](deployment-pipelines-get-started.md)

>[!div class="nextstepaction"]
>[配置パイプライン プロセスを理解する](deployment-pipelines-process.md)

>[!div class="nextstepaction"]
>[配置パイプラインのベスト プラクティス](deployment-pipelines-best-practices.md)