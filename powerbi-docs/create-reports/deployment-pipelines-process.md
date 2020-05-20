---
title: 配置パイプラインのプロセス
description: Power BI 配置パイプラインのプロセスについて理解する
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-service
ms.date: 05/06/2020
ms.openlocfilehash: c4a823b0b41def6c10cd8f932bb97e91eb977ecb
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2020
ms.locfileid: "83148594"
---
# <a name="understand-the-deployment-process-preview"></a>配置プロセスについて理解する (プレビュー)

配置プロセスを使用すると、パイプライン内のあるステージのコンテンツを別のステージに (通常は開発からテスト、テストから運用に) クローンすることができます。

配置中に、Power BI は現在のステージのコンテンツをターゲットのステージにコピーします。 コピーされた項目間の接続は、コピー プロセス中は保持されます。 また、Power BI は、構成済みのデータセット ルールをターゲット ステージの更新されたコンテンツに適用します。 配置する項目の数によっては、コンテンツの配置に時間がかかることがあります。 この間、Power BI ポータルで他のページに移動できますが、ターゲット ステージのコンテンツを使用することはできません。

## <a name="deploying-content-to-an-empty-stage"></a>空のステージへのコンテンツの配置

空のステージにコンテンツを配置すると、配置元のワークスペースにあるレポート、ダッシュボード、およびデータセットのメタデータが配置先のステージにコピーされます。 配置先のステージの新しいワークスペースが、Premium 容量で作成されます。

あるステージから次のステージにコンテンツを配置する方法は 2 つあります。 すべてのコンテンツを配置することも、[配置するコンテンツ項目を選択](deployment-pipelines-get-started.md#selective-deployment)することもできます。

コンテンツは、配置パイプラインの後の方のステージから前の方のステージに、逆方向に配置することもできます。

配置が完了したら、新しくコピーしたコンテンツを使用できるように、データセットを更新します。 データはあるステージから別のステージにコピーされないため、データセットの更新が必要です。 配置プロセス中にどの項目のプロパティがコピーされ、どの項目のプロパティがコピーされないかを理解するには、「[配置中にコピーされる項目のプロパティ](#item-properties-copied-during-deployment)」のセクションを参照してください。

### <a name="creating-a-premium-capacity-workspace"></a>Premium 容量ワークスペースの作成

配置パイプラインによって、初回の配置時に、Premium 容量のアクセス許可があるかどうかが確認されます。  

容量のアクセス許可がある場合は、配置先のステージにワークスペースのコンテンツがコピーされ、そのステージの新しいワークスペースが Premium 容量に作成されます。

容量のアクセス許可を持っていない場合、ワークスペースは作成されますが、コンテンツはコピーされません。 容量管理者にワークスペースを容量に追加するように依頼するか、容量に対する割り当てアクセス許可を要求できます。 その後、ワークスペースが容量に割り当てられたら、このワークスペースにコンテンツを配置できます。

### <a name="workspace-and-content-ownership"></a>ワークスペースとコンテンツの所有権

配置を行うユーザーは、自動的に、クローンされたデータセットのデータセット所有者になり、新しいワークスペースの唯一の管理者になります。

## <a name="deploy-content-to-an-existing-workspace"></a>既存のワークスペースへのコンテンツの配置

動作中の運用パイプラインのコンテンツを、既存のワークスペースを持つステージに配置すると、次のようになります。

* 既にコンテンツが含まれているステージに、新しいコンテンツが追加として配置されます。

* 現在の動作中のステージで、新しいコンテンツが配置され、古いコンテンツが置き換えられます。

### <a name="deployment-process"></a>デプロイ プロセス

現在のステージのコンテンツは、ターゲット ステージにコピーされます。 Power BI は、ターゲット ステージ内の既存のコンテンツを識別し、それを上書きします。 どのコンテンツ項目を上書きする必要があるかを特定するために、配置パイプラインは親項目とそのクローンの間の接続を使用します。 この接続は、新しいコンテンツの作成時に保持されます。 上書き操作では、項目のコンテンツのみが上書きされます。 項目の ID、URL、およびアクセス許可は変更されません。

ターゲット ステージでは、[コピーされない項目のプロパティ](deployment-pipelines-process.md#item-properties-that-are-not-copied)は、配置前の状態のままです。 新しいコンテンツと新しい項目が、現在のステージからターゲット ステージにコピーされます。

### <a name="refreshing-the-dataset"></a>データセットの更新

ターゲット データセット内のデータは、可能であれば保持されます。 データセットに変更がない場合、データは配置前と同じままで保持されます。

テーブルまたは計算メジャーの追加などの小さな変更では、Power BI によって元のデータが保持され、必要な部分のみを更新するように、更新が最適化されます。 重大なスキーマ変更や、データ ソース接続の変更では、完全な更新が必要です。

### <a name="requirements-for-deploying-to-a-stage-with-an-existing-workspace"></a>既存のワークスペースを持つステージへの配置の要件

配置されたコンテンツが [Premium 容量](../admin/service-premium-what-is.md)に存在する限り、以下の条件を満たすユーザーは、既存のワークスペースを持つステージにコンテンツを配置できます。

* ソース配置ステージとターゲット配置ステージの両方のワークスペースのメンバーである [Pro ユーザー](../admin/service-admin-purchasing-power-bi-pro.md)。

* 配置しようとしているターゲット ワークスペース内のすべてのデータセットの所有者。

詳細については、「[アクセス許可](#permissions)」のセクションを参照してください。

## <a name="deployed-items"></a>配置される項目

あるパイプライン ステージから別のパイプライン ステージにコンテンツを配置する場合、コピーされるコンテンツには以下の Power BI 項目が含まれます。

* データセット

* レポート

* ダッシュボード

### <a name="unsupported-items"></a>サポートされていない項目

配置パイプラインでは、以下の項目はサポートされていません。

* .pbix 由来ではないデータセット

* サポートされていないデータセットに基づくレポート

* ワークスペースでテンプレート アプリを使用できません

* ページ分割されたレポート

* データフロー

* プッシュ データセット

* ブック

## <a name="item-properties-copied-during-deployment"></a>配置中にコピーされる項目のプロパティ

配置時に、以下の項目のプロパティがコピーされ、ターゲット ステージで項目のプロパティが上書きされます。

* データ ソース ([データセット ルール](deployment-pipelines-get-started.md#step-4---create-dataset-rules)はサポートされています)

* パラメーター ([データセット ルール](deployment-pipelines-get-started.md#step-4---create-dataset-rules)はサポートされています)

* レポート ビジュアル

* レポート ページ

* データのプッシュ時の

* モデルのメタデータ

* 項目のリレーションシップ

### <a name="item-properties-that-are-not-copied"></a>コピーされない項目のプロパティ

以下の項目のプロパティは、配置中にコピーされません。

* データ - データはコピーされていません。メタデータのみがコピーされます

* URL

* ID

* アクセス許可 - ワークスペースまたは特定の項目に対するもの

* ワークスペースの設定 - 各ステージには独自のワークスペースがあります

* アプリのコンテンツと設定 - アプリを配置するには、「[Power BI アプリの配置](#deploying-power-bi-apps)」を参照してください

以下のデータセットのプロパティも、配置中にコピーされません。

* ロール割り当て
    
* スケジュールの更新
    
* データ ソース資格情報
    
* クエリ キャッシュの設定 (容量から継承可能)
    
* 保証の設定

## <a name="deploying-power-bi-apps"></a>Power BI アプリの配置

[Power BI アプリ](../consumer/end-user-apps.md)は、コンテンツを無料の Power BI コンシューマーに配布するための推奨される方法です。 配置パイプラインを使用すると、アプリのライフサイクルに関してより柔軟な制御ができるように、配置パイプライン内の Power BI アプリを管理できます。

配置パイプラインのステージごとにアプリを作成し、各アプリの更新部分をエンド ユーザーの観点からテストできるようにします。 配置パイプラインを使用すると、このプロセスを簡単に管理できます。 特定のパイプライン ステージでアプリを発行または表示するには、ワークスペース カードの発行ボタンまたは表示ボタンを使用します。

[![](media/deployment-pipelines-process/publish.png "Publish app")](media/deployment-pipelines-process/publish.png#lightbox)

運用ステージでは、左下隅にあるメイン アクション ボタンをクリックすると、Power BI のアプリの更新ページが開き、アプリ ユーザーがコンテンツを更新できるようになります。

[![](media/deployment-pipelines-process/update-app.png "Update app")](media/deployment-pipelines-process/update-app.png#lightbox)

>[!IMPORTANT]
>配置プロセスには、アプリのコンテンツや設定の更新は含まれません。 コンテンツまたは設定に変更を適用するには、必要なパイプライン ステージでアプリを手動で更新する必要があります。

## <a name="permissions"></a>アクセス許可

パイプラインのアクセス許可とワークスペースのアクセス許可は、個別に付与および管理されます。 たとえば、ワークスペースのアクセス許可を持たない、パイプライン アクセス権を持つユーザーは、パイプラインを表示したり、他のユーザーと共有したりできます。 ただし、このユーザーは、パイプラインまたはワークスペース ページでワークスペースのコンテンツを表示することはできず、配置を実行できません。

### <a name="user-with-pipeline-access"></a>パイプライン アクセス権を持つユーザー

パイプライン アクセス権を持つユーザーは、以下のアクセス許可を持ちます。

* パイプラインを表示する
    
* 他のユーザーとパイプラインを共有する
    
* パイプラインを編集および削除する

>[!NOTE]
>パイプライン アクセス権では、ワークスペースのコンテンツに対する表示やアクションの実行のためのアクセス許可は付与されません。

### <a name="workspace-viewer"></a>ワークスペース ビューアー

"*パイプライン アクセス権*" を持つワークスペース ビューアーは、以下の操作も実行できます。

* コンテンツを使用する

>[!NOTE]
>ワークスペース ビューアーは、データセットにアクセスしたり、ワークスペースのコンテンツを編集したりすることはできません。

### <a name="workspace-contributor"></a>ワークスペースの共同作成者

"*パイプライン アクセス権*" を持つワークスペース共同作成者は、以下の操作も実行できます。

* コンテンツを使用する

* ステージを比較する

* データセットを表示する

### <a name="workspace-member"></a>ワークスペース メンバー

"*パイプライン アクセス権*" を持つワークスペース メンバーは、以下の操作も実行できます。

* ワークスペースのコンテンツを表示する
    
* ステージを比較する
    
* レポートとダッシュボードを配置する

* ワークスペースを削除する

### <a name="workspace-admin"></a>ワークスペース管理者

"*パイプライン アクセス権*" を持つワークスペース管理者は、"*ワークスペース メンバー*" アクションを行うことができ、以下の操作も実行できます。

* ワークスペースの割り当て

* ワークスペースを削除する

### <a name="dataset-owner"></a>データセット所有者

ワークスペースのメンバーまたは管理者であるデータセット所有者は、次の操作も実行できます。

* データセットの更新
    
* ルールを構成する

>[!NOTE]
>このセクションでは、配置パイプラインでのユーザーのアクセス許可について説明します。 このセクションに記載されているアクセス許可は、他の Power BI 機能では異なる適用になる場合があります。

## <a name="limitations"></a>制限事項

このセクションでは、配置パイプラインでのほとんどの制限を列挙します。

* ワークスペースは、 [Premium 容量](../admin/service-premium-what-is.md)に存在する必要があります。

* Power BI の[秘密度ラベル](../admin/service-security-data-protection-overview.md#sensitivity-labels-in-power-bi)が付いているレポートやダッシュボードなどの Power BI 項目は、配置できません。

* [増分更新](../admin/service-premium-incremental-refresh.md)で構成されたデータセットは、配置できません。

* ワークスペースの制限事項の一覧については、「[ワークスペースの割り当ての制限事項](deployment-pipelines-get-started.md#workspace-assignment-limitations)」を参照してください。

* データセット ルールの制限事項の一覧については、「[データセット ルールの制限事項](deployment-pipelines-get-started.md#dataset-rule-limitations)」を参照してください

* サポートされていない項目の一覧については、「[サポートされていない項目](#unsupported-items)」を参照してください。

## <a name="next-steps"></a>次の手順

>[!div class="nextstepaction"]
>[配置パイプラインの概要](deployment-pipelines-overview.md)

>[!div class="nextstepaction"]
>[配置パイプラインのベスト プラクティス](deployment-pipelines-best-practices.md)

>[!div class="nextstepaction"]
>[配置パイプラインの使用を開始する](deployment-pipelines-get-started.md)

>[!div class="nextstepaction"]
>[配置パイプラインのトラブルシューティング](deployment-pipelines-troubleshooting.md)