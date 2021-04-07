---
title: デプロイ パイプライン (Power BI のアプリケーション ライフサイクル管理 (ALM) ツール) のトラブルシューティング
description: Power BI のアプリケーション ライフサイクル管理 (ALM) ツールである、デプロイ パイプラインのトラブルシューティングに関する質問への回答を紹介します
author: KesemSharabi
ms.author: kesharab
ms.topic: troubleshooting
ms.service: powerbi
ms.subservice: pbi-deployment
ms.date: 03/22/2021
ms.openlocfilehash: c772ee5905d231bd5d0032ae89cae0fea6fe78b3
ms.sourcegitcommit: 9fd7fbcc819bee4a242cb786aad9e675ea83e83d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104834217"
---
# <a name="deployment-pipelines-troubleshooting"></a>配置パイプラインのトラブルシューティング

この記事では、配置パイプラインの問題のトラブルシューティングについて説明します。

## <a name="general"></a>全般

### <a name="whats-deployment-pipelines-in-power-bi"></a>Power BI の配置パイプラインとはどのようなものですか?

Power BI の配置パイプラインがどのようなものであるかを理解するには、[配置パイプラインの概要](deployment-pipelines-overview.md)に関するページを参照してください。

### <a name="how-do-i-get-started-with-deployment-pipelines"></a>配置パイプラインの使用を開始するにはどうすればよいですか。

配置パイプラインの使用を開始するには、[使用開始の手順](deployment-pipelines-get-started.md)を利用してください。

### <a name="why-cant-i-see-the-deployment-pipelines-button"></a>配置パイプラインのボタンが表示されないのはなぜですか。

以下の条件が満たされていない場合は、配置パイプラインのボタンを表示することができません。

* 次のいずれかの Premium ライセンスを持っている。

    * Power BI [Pro ユーザー](../admin/service-admin-purchasing-power-bi-pro.md)であり、Premium 容量を持つ組織に所属している。

    * [Premium Per User (PPU)](../admin/service-premium-per-user-faq.md)。

* [新しいワークスペース エクスペリエンス](../collaborate-share/service-create-the-new-workspaces.md)の管理者である。

### <a name="why-cant-i-see-the-pipeline-stage-tag-in-my-workspace"></a>ワークスペースにパイプライン ステージ タグが表示されないのはなぜですか?

デプロイ パイプラインには、パイプラインに割り当てられているワークスペースのパイプライン ステージ タグが表示されます。 "*開発*" および "*テスト*" ステージのタグは常に表示されます。 ただし、[パイプラインへのアクセス権](deployment-pipelines-process.md#user-with-pipeline-access)を持っている場合、または [ワークスペース管理者](deployment-pipelines-process.md#workspace-admin)である場合にのみ、"*運用環境*" タグが表示されます。

> [!div class="mx-imgBorder"]
> ![運用環境パイプライン ワークスペースの運用環境タグのスクリーンショット。](media/deployment-pipelines-troubleshooting/production-tag.png)

## <a name="licensing"></a>ライセンス

### <a name="what-licenses-are-needed-to-work-with-deployment-pipelines"></a>配置パイプラインを操作するには、どのようなライセンスが必要ですか。

配置パイプラインを使用するには、次のいずれかのライセンスを持っている必要があります。

* [Premium 容量](../admin/service-premium-what-is.md)に存在するワークスペースを持つ [Pro ユーザー](../admin/service-admin-purchasing-power-bi-pro.md) ライセンス。

* [Premium Per User (PPU)](../admin/service-premium-per-user-faq.md)。

詳細については、「[配置パイプラインへのアクセス](deployment-pipelines-get-started.md#accessing-deployment-pipelines)」を参照してください。

### <a name="what-type-of-capacity-can-i-assign-to-a-workspace-in-a-pipeline"></a>パイプラインのワークスペースには、どのような種類の容量を割り当てることができますか。

パイプラインを機能させるには、配置パイプライン内のすべてのワークスペースが容量内に存在する必要があります。 ただし、パイプライン内の異なるワークスペースに対して、異なる容量を使用できます。 また、同じパイプライン内の異なるワークスペースに対して、異なる容量の種類を使用することもできます。

開発とテストでは、ユーザーごとの Pro Power BI アカウントと共に A または EM 容量を使用できます。 また、開発およびテストのステージで、各ユーザーに PPU を使用することもできます。

運用ワークスペースの場合は、P 容量が必要です。 ISV が埋め込みアプリケーションを使用してコンテンツを配布する場合は、運用環境で A または EM 容量を使用することもできます。 PPU は、運用ワークスペースでも使用できます。

>[!NOTE]
>PPU を使用してワークスペースを作成すると、他の PPU ユーザーのみがワークスペースにアクセスしてそのコンテンツを使用できるようになります。

## <a name="technical"></a>技術的な質問

### <a name="why-cant-i-see-all-my-workspaces-when-i-try-to-assign-a-workspace-to-a-pipeline"></a>パイプラインにワークスペースを割り当てようとするときに、一部のワークスペースが表示されないのはなぜですか。

パイプラインにワークスペースを割り当てるには、以下の条件を満たす必要があります。

* ワークスペースが[新しいワークスペース エクスペリエンス](../collaborate-share/service-create-the-new-workspaces.md)である

* 自分がワークスペースの管理者である

* ワークスペースが他のパイプラインに割り当てられていない

* ワークスペースが [Premium 容量](../admin/service-premium-what-is.md)上にある

これらの条件を満たしていないワークスペースは、選択できるワークスペースの一覧に表示されません。

### <a name="how-can-i-assign-workspaces-to-all-the-stages-in-a-pipeline"></a>パイプラインのすべてのステージにワークスペースを割り当てるにはどうすればよいですか。

パイプラインごとに、1 つのワークスペースを割り当てることができます。 ワークスペースがパイプラインに割り当てられたら、それを次のパイプライン ステージに配置できます。 最初のデプロイ時に、ソース ステージの項目のコピーを使用して新しいワークスペースが作成されます。 コピーされた項目間のリレーションシップは保持されます。 詳細については、[配置パイプラインにワークスペースを割り当てる](deployment-pipelines-get-started.md#step-2---assign-a-workspace-to-a-deployment-pipeline)方法に関するページを参照してください。

### <a name="why-did-my-first-deployment-fail"></a>最初の配置が失敗したのですが、なぜでしょうか。

最初の配置が失敗した原因として、さまざまなものが考えられます。 それらの理由の一部を次の表に示します。

|Error  |アクション  |
|---------|---------|
|[Premium 容量のアクセス許可](deployment-pipelines-process.md#creating-a-premium-workspace)がない。     |Premium 容量を持つ組織で働いている場合は、容量管理者にワークスペースを容量に追加するように依頼するか、容量に対する割り当てアクセス許可を要求します。 ワークスペースが容量に追加されたら、再配置します。</br></br>Premium 容量を持つ組織で働いていない場合は、[Premium Per User (PPU)](../admin/service-premium-per-user-faq.md) の購入を検討してください。        |
|ワークスペースに対するアクセス許可がない。     |デプロイするには、ワークスペース メンバーになっている必要があります。 ワークスペース管理者に、適切なアクセス許可を付与するよう依頼します。         |
|Power BI 管理者がワークスペースの作成を無効にしている。     |Power BI 管理者に連絡してサポートを依頼します。         |
|ワークスペースが[新しいワークスペース エクスペリエンス](../collaborate-share/service-create-the-new-workspaces.md)でない。     |新しいワークスペース エクスペリエンスでコンテンツを作成します。 クラシック ワークスペースにコンテンツがある場合は、新しいワークスペース エクスペリエンスに[アップグレード](../collaborate-share/service-upgrade-workspaces.md)できます。         |
|[選択的配置](deployment-pipelines-get-started.md#selective-deployment)を使用しており、コンテンツのデータセットを選択していない。     |次のいずれかの操作を行います。 </br></br>データセットにリンクされているコンテンツの選択を解除します。 選択されていないコンテンツ (レポートやダッシュボードなど) は、次のステージにコピーされません。 </br></br>選択したコンテンツにリンクされているデータセットを選択します。 データセットが次のステージにコピーされます。         |

### <a name="im-getting-a-warning-that-i-have-unsupported-artifacts-in-my-workspace-when-im-trying-to-deploy-how-can-i-know-which-artifacts-are-not-supported"></a>配置を試みているときに、自分のワークスペースに "サポートされていない成果物" があることを示す警告が表示されます。 どの成果物がサポートされていないかを知るには、どうすればよいですか。

配置パイプラインでサポートされていない項目と成果物の包括的な一覧については、以下のセクションを参照してください。

* [サポートされていない項目](deployment-pipelines-process.md#unsupported-items)

* [コピーされない項目のプロパティ](deployment-pipelines-process.md#item-properties-that-are-not-copied)

### <a name="why-did-my-deployment-fail-due-to-broken-rules"></a>ルールの破損により配置が失敗したのはなぜですか。

配置ルールの構成で問題が発生している場合は、[配置ルール](deployment-pipelines-get-started.md#step-4---create-deployment-rules)にアクセスし、[配置ルールの制限事項](deployment-pipelines-get-started.md#deployment-rules-limitations)に従っていることを確認してください。

以前は配置が成功していて、破損したルールによって突然失敗した場合は、再発行されているデータセットが原因である可能性があります。 ソース データセットに対して以下の変更を行うと、配置が失敗します。

**パラメーター ルール**

* パラメーターの削除

* パラメーター名の変更

**データ ソース ルール**

配置ルールに値がありません。 この問題は、データセットが変更された場合に発生する可能性があります。

![破損したリンクのために配置が失敗した場合に表示される、無効なルールに関するエラーのスクリーンショット。](media/deployment-pipelines-troubleshooting/broken-rule.png)

以前は成功した配置が、破損したリンクのために失敗する場合は、警告が表示されます。 **[ルールの構成]** を選択すると、失敗したデータセットがマークされているデプロイ設定ペインに移動できます。 データセットを選択すると、破損したルールがマークされます。

正常に配置するには、破損したルールを修正または削除し、再配置します。

### <a name="how-can-i-change-the-data-source-in-the-pipeline-stages"></a>パイプライン ステージのデータ ソースを変更するにはどうすればよいですか。

Power BI サービスでは、データ ソース接続を変更することはできません。

テストまたは運用ステージでデータ ソースを変更する場合は、[配置ルール](deployment-pipelines-get-started.md#step-4---create-deployment-rules)または [API](/rest/api/power-bi/datasets/updateparametersingroup) を使用できます。 配置ルールは、次回の配置の後でのみ有効になります。

### <a name="i-fixed-a-bug-in-production-but-now-i-cant-select-the-deploy-to-previous-stage-button-why-is-it-greyed-out"></a>運用環境でバグを修正しましたが、[deploy to previous stage]\(前のステージにデプロイする\) ボタンを選択できなくなりました。 淡色表示になったのはなぜですか。

逆方向に配置できるのは、配置先が空のステージである場合のみです。 テスト ステージにコンテンツがある場合は、運用環境から逆方向に配置することはできません。

パイプラインの作成後は、開発ステージを使用してコンテンツを開発し、テスト ステージを使用してそれを確認し、テストしてください。 これらのステージでバグを修正したうえで、修正した環境を運用ステージに配置できます。

>[!NOTE]
>逆方向の配置では、[完全配置](deployment-pipelines-get-started.md#deploying-all-content)のみがサポートされます。 [選択的配置](deployment-pipelines-get-started.md#selective-deployment)はサポートされていません

### <a name="why-do-i-need-to-deploy-after-configuring-deployment-rules"></a>配置ルールを構成した後に配置する必要があるのはなぜですか。

配置ルールは、構成された後すぐに適用されるわけではありません。 配置ルールを適用するには、データセットをソース ステージから、作成された配置ルールを含むターゲット ステージに配置する必要があります。 配置ルールを構成した後で、かつ配置する前には、構成されたルールを含むデータセットの横に "*異なる*" インジケーターが表示されます。 これは、ソース ステージからターゲット ステージにそのデータセットを配置する必要があることを示しています。 配置すると、その他の変更が行われていない場合は "*異なる*" インジケーターは表示されなくなり、ルールが正常に適用されたことが示されます。

### <a name="why-are-the-deployment-rules-greyed-out"></a>配置ルールがグレー表示されるのはなぜですか。

[配置ルール](deployment-pipelines-get-started.md#step-4---create-deployment-rules)を作成するには、配置ルールを作成している Power BI 項目の所有者である必要があります。 Power BI 項目の所有者でない場合は、配置ルールがグレー表示されます。

>[!div class="mx-imgBorder"]
>![グレー表示された配置パイプラインの配置ルールを示すスクリーンショット。](media/deployment-pipelines-troubleshooting/rules-greyed-out.png)

いずれかのルール オプションがグレー表示されている場合は、次に示す理由が考えられます。

* **データ ソース ルール** - ルールを構成する対象となるデータ ソースがありません。

* **パラメーター ルール** - ルールを構成する対象となるパラメーターがありません。

### <a name="why-am-i-getting-the-deployment-was-stopped-error"></a>[配置が停止] エラーが表示されるのはなぜですか。

ソース ステージ スキーマの破壊的変更 (列の型の整数から文字列への置き換えなど) によって、配置の後にターゲット データセットでデータ損失が発生します。

配置中に、ソース データセット内のメタデータがターゲット メタデータに対してチェックされます。 スキーマの破壊的変更が検出されると、配置が停止します。 これが発生すると、 *[配置が停止]* エラーが表示されます。

:::image type="content" source="media/deployment-pipelines-troubleshooting/deployment-was-stopped-error.png" alt-text="配置パイプラインでの [配置が停止] エラーのスクリーンショット":::

この配置を続行した場合は、ターゲット ステージでデータが失われます。 このオプションは、データセットに加えた変更が意図的であった場合に使用できます。 配置が完了したら、ターゲット データセットを更新する必要があります。

変更が意図的でなかった場合は、エラー ウィンドウを閉じ、修正された PBIX ファイルをソース ワークスペースにアップロードして再配置します。

スキーマ変更のために配置が失敗した後、ターゲット ステージでは *[配置できませんでした]* メッセージの後に *[詳細の表示]* リンクが表示されます。 このリンクにより、失敗した配置のときに表示されたのと同じ *[配置が停止]* エラー ウィンドウが開かれます。

### <a name="does-deployment-pipelines-support-multi-geo"></a>配置パイプラインでは Multi-Geo はサポートされていますか。

Multi-Geo はサポートされています。 異なる geo のステージ間でコンテンツを配置するのには、時間がかかることがあります。

## <a name="paginated-reports"></a>ページ分割されたレポート

### <a name="why-cant-i-deploy-a-paginated-report"></a>ページ分割されたレポートを配置できないのはなぜですか。

ページ分割されたレポートを配置するには、次の条件の両方が満たされている必要があります。

* 配置元のワークスペース (ソース ステージ ワークスペース) 内のワークスペース メンバーである必要があります。 ソース ステージ内のワークスペース メンバーでない場合は、ページ分割されたレポートを配置できません。

* ターゲット ステージの容量で、[ページ分割されたレポートのワークロードを有効にする](./../developer/embedded/embed-paginated-reports-organization.md#enable-paginated-reports-workload)必要があります。

### <a name="whos-the-owner-of-a-deployed-paginated-report"></a>配置済みのページ分割されたレポートの所有者はだれですか。

ページ分割されたレポートを初めて配置している場合は、そのレポートの所有者になります。

ページ分割されたレポートを、そのページ分割されたレポートのコピーが既に含まれているステージに配置している場合は、前のレポートがオーバーライドされ、前の所有者に代わってその所有者になります。 このような場合は、ページ分割されたレポートでデータを使用できるように、基になるデータ ソースに対する資格情報が必要になります。

### <a name="why-does-my-target-stage-paginated-report-display-data-from-a-power-bi-dataset-in-the-source-stage"></a>ターゲット ステージのページ分割されたレポートにソース ステージ内の Power BI データセットのデータが表示されるのはなぜですか。

現時点では、データセットは外部の Analysis Services データ ソースとして扱われ、配置の後にデータセットへの接続が自動的に切り替えられることはありません。

Power BI データセットに接続されているページ分割されたレポートを配置すると、それは引き続き、最初に接続されていたデータセットを指します。 ページ分割されたレポートが (ターゲット ステージ データセットなどを含む) 希望する任意のデータセットを指すようにするには、[配置ルール](deployment-pipelines-get-started.md#step-4---create-deployment-rules)を使用します。

Power BI データセットを含むページ分割されたレポートを使用している場合は、「[Power BI データセットを含むページ分割されたレポートの配置ルールを作成するにはどうすればよいですか](#how-do-i-create-a-deployment-rule-for-a-paginated-report-with-a-power-bi-dataset)」を参照してください。

### <a name="where-are-my-paginated-report-subreports"></a>ページ分割されたレポートのサブレポートはどこにありますか。

ページ分割されたレポートのサブレポートは、ページ分割されたレポートが保持されているのと同じフォルダーに保持されます。 [選択的コピー](deployment-pipelines-get-started.md#selective-deployment)を使用して、サブレポートを含むページ分割されたレポートをコピーしているときのレンダリング問題を回避するには、親レポートとサブレポートの両方を選択します。

### <a name="how-do-i-create-a-deployment-rule-for-a-paginated-report-with-a-power-bi-dataset"></a>Power BI データセットを含むページ分割されたレポートの配置ルールを作成するにはどうすればよいですか。

[ページ分割されたレポートが同じステージ内のデータセットを指す](#why-does-my-target-stage-paginated-report-display-data-from-a-power-bi-dataset-in-the-source-stage)ようにしたい場合は、ページ分割されたレポートのルールを作成できます。 ページ分割されたレポートの配置ルールを作成する場合は、データベースとサーバーを選択する必要があります。

Power BI データセットが含まれていないページ分割されたレポートの配置ルールを設定している場合は、ターゲット データ ソースが外部であるため、サーバーとデータベースの両方を指定する必要があります。

ただし、Power BI データセットを使用するページ分割されたレポートでは内部データセットが使用されます。 このような場合は、接続先の Power BI データセットを識別するためにデータ ソース名に依存することはできません。 データ ソース ルールを作成するか、または[データソースの更新](/rest/api/power-bi/datasets/updatedatasourcesingroup) API を呼び出すと、データ ソース名はターゲット ステージで更新されても変更されなくなります。 配置ルールを設定する場合は、データベース形式を維持し、データベース フィールド内のデータセット オブジェクト ID を置き換える必要があります。 データセットが内部であるため、サーバーは同じままです。

* **データベース** - Power BI データセットを含むページ分割されたレポートのデータベース形式は `sobe_wowvirtualserver-<dataset ID>` です。 たとえば、「 `sobe_wowvirtualserver-d51fd26e-9124-467f-919c-0c48a99a1d63` 」のように入力します。 `<dataset ID>` をデータセットの ID に置き換えます。 データセット ID を URL から取得するには、`datasets/` の後で、かつ次のフォワードスラッシュの前にある GUID を選択します。

    :::image type="content" source="media/deployment-pipelines-troubleshooting/datasets-id.png" alt-text="Power BI の URL に表示されているデータセット ID のスクリーンショット。":::

* **サーバー** - データベースをホストするサーバー。 既存のサーバーをそのままにします。

## <a name="permissions"></a>アクセス許可

### <a name="what-is-the-deployment-pipelines-permissions-model"></a>配置パイプラインのアクセス許可モデルとはどのようなものですか。

配置パイプラインのアクセス許可モデルについては、「[アクセス許可](deployment-pipelines-process.md#permissions)」のセクションで説明されています。

### <a name="who-can-deploy-content-between-stages"></a>ステージ間でコンテンツを配置できるのはだれですか。

コンテンツは、空のステージにも、コンテンツを含むステージにも配置できます。 コンテンツは、[Premium 容量](../admin/service-premium-what-is.md)に存在する必要があります。

* **空のステージへの配置** - ソース ワークスペースのメンバーまたは管理者であるすべての [Pro](../admin/service-admin-purchasing-power-bi-pro.md) または [PPU](../admin/service-premium-per-user-faq.md) のユーザー。

* **コンテンツがあるステージへの配置** - ソースとターゲットの展開ステージの両方でワークスペースのメンバーまたは管理者であるすべての [Pro](../admin/service-admin-purchasing-power-bi-pro.md) または [PPU](../admin/service-premium-per-user-faq.md) のユーザー。

* **データセットのオーバーライド** - 配置では、データセットが変更されなかった場合でも、ターゲット ステージに含まれる各データセットがオーバーライドされます。 ユーザーは、配置で指定されたすべてのターゲット ステージ データセットの所有者である必要があります。

### <a name="which-permissions-do-i-need-to-configure-deployment-rules"></a>配置ルールを構成するには、どのアクセス許可が必要ですか。

配置パイプラインで配置ルールを構成するには、データセット所有者である必要があります。

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