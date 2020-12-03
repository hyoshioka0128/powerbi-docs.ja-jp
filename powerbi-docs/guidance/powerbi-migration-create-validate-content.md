---
title: Power BI に移行するコンテンツを作成する
description: Power BI に移行するときのコンテンツの作成と検証に関するガイダンス。
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/20/2020
ms.openlocfilehash: 03a55f2f414ca8af7ca86f51dcafb0258efc88b7
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418603"
---
# <a name="create-content-to-migrate-to-power-bi"></a>Power BI に移行するコンテンツを作成する

この記事では、Power BI に移行するときのコンテンツの作成と検証に関係する **ステージ 4** について説明します。

:::image type="content" source="media/powerbi-migration-create-validate-content/migrate-to-powerbi-stage-4.png" alt-text="Power BI への移行のステージを示す図。この記事では、ステージ 4 を重点的に説明します。":::

> [!NOTE]
> 上の図の詳細については、「[Power BI への移行の概要](powerbi-migration-overview.md)」を参照してください。

ステージ 4 の主な目的は、概念実証 (POC) を運用可能なソリューションに変換する実際の作業を実行することです。

このステージからの出力は、開発ワークスペースで検証され、運用環境へのデプロイの準備ができている Power BI ソリューションです。

> [!TIP]
> この記事で説明するほとんどのトピックは、標準の Power BI 実装プロジェクトにも適用されます。

## <a name="create-the-production-solution"></a>運用ソリューションの作成

この時点で、POC を実行したのと同じ人物が、運用環境に対応するように Power BI ソリューションの作成を続けて行うことができます。 または、別の人物が関係している可能性があります。 タイムラインが守られるのであれば、将来の Power BI 開発を担当する人々を関わらせるのは良いことです。 そうすることで積極的に学習できます。

> [!IMPORTANT]
> POC での作業をできるだけ多く再利用します。

### <a name="develop-new-import-dataset"></a>新しいインポート データセットの開発

ニーズに合う既存の Power BI データセットがまだ存在しない場合や、既存のデータセットをニーズに合わせて拡張できない場合は、新しいインポート データセットを作成することができます。

理想的には、最初から、データとレポートの開発作業を切り離すことを検討してください。 [データとレポートを切り離す](report-separate-from-model.md)ことにより、データ モデリングとレポートを別々の担当者が担当する場合に、作業およびアクセス許可の切り分けが容易になります。 これにより、よりスケーラブルなアプローチが可能になり、データの再利用が促進されます。

インポート データセットの開発に関連する重要なアクティビティは次のとおりです。

- 1 つまたは複数のデータ ソース (Power BI データフローである可能性があります) から[データを取得](../connect-data/desktop-quickstart-connect-to-data.md)します。
- データを[整形、結合、準備](../connect-data/desktop-shape-and-combine-data.md)します。
- [日付テーブル](../transform-model/desktop-date-tables.md)を含む[データセット モデル](../transform-model/desktop-modeling-view.md)を作成します。
- [モデル リレーションシップ](../transform-model/desktop-create-and-manage-relationships.md)を作成および検証します。
- [メジャー](../transform-model/desktop-measures.md)を定義します。
- 必要に応じて、[行レベルのセキュリティ](../admin/service-admin-rls.md)を設定します。
- シノニムを構成し、[Q&A を最適化](../natural-language/q-and-a-best-practices.md)します。
- 拡張性、パフォーマンス、同時実行性を計画します。これは、[複合モデル](../transform-model/desktop-composite-models.md)や[集計](../transform-model/desktop-aggregations.md)の使用など、データ ストレージ モードに関する決定に影響を与える可能性があります。

> [!TIP]
> 開発、テスト、運用の環境が異なる場合は、データ ソースの[パラメーター化](/power-query/power-query-query-parameters)を検討します。 そうすることで、[ステージ 5](powerbi-migration-deploy-support-monitor.md) で説明されている展開が大幅に簡単になります。

### <a name="develop-new-reports-and-dashboards"></a>新しいレポートとダッシュボードの開発

Power BI レポートまたはダッシュボードの開発に関連する重要なアクティビティは次のとおりです。

- 既存のデータ モデルへのライブ接続を使用するか、新しいデータ モデルを作成するかを決定します
- 新しいデータ モデルを作成する場合は、モデル テーブルの[データ ストレージ モード](../transform-model/desktop-storage-mode.md) (インポート、DirectQuery、または複合) を決定します。
- 要件を満たす最適なデータ視覚化ツールを決定します: Power BI Desktop、Paginated Report Builder、または Excel。
- レポートで伝える必要があるストーリーを伝え、レポートで答える必要がある質問に対処するための、[最適なビジュアル](../consumer/end-user-visual-type.md)を決定します。
- すべてのビジュアルに明確で簡潔な、ビジネスに適した用語が示されていることを確認します。
- 対話性の要件に対処します。
- ライブ接続を使用する場合は、[レポートレベルのメジャー](../transform-model/desktop-tutorial-create-measures.md)を追加します。
- Power BI サービスに[ダッシュボード](../create-reports/service-dashboards.md)を作成します (特に、コンシューマーが主要なメトリックを簡単に監視する方法が必要な場合)。

> [!NOTE]
> これらの決定の多くは、計画の早い段階または技術的 POC において行います。

## <a name="validate-the-solution"></a>ソリューションの検証

Power BI ソリューションの検証には、主に次の 4 つの側面があります。

1. データの精度
2. セキュリティ
3. 機能
4. パフォーマンス

### <a name="validate-data-accuracy"></a>データの精度の検証

移行中に 1 回限りの作業として、新しいレポートのデータが従来のレポートに表示されるものと一致することを確認する必要があります。 または、違いがある場合は、その理由を説明できるようにします。 従来のソリューションにエラーが見つかり、新しいソリューションでそれを解決することは、皆さんが思っている以上によくあります。

継続的なデータ検証作業の一環として、通常は新しいレポートと元のソース システムをクロスチェックする必要があります。 この検証は、反復可能な方法で、レポートの変更を発行するたびに実行するのが理想的です。

### <a name="validate-security"></a>セキュリティの検証

セキュリティを検証する際に考慮すべき主な側面が 2 つあります。

- データのアクセス許可
- データセット、レポート、ダッシュボードへのアクセス

インポート データセットでは、[行レベルのセキュリティ](../admin/service-admin-rls.md) (RLS) を定義することによって、データ アクセス許可が適用されます。 DirectQuery ストレージ モード (場合によっては[シングル サインオン](../connect-data/service-gateway-sso-overview.md)を使用) を使用する場合、ソース システムによってデータのアクセス許可が適用される可能性もあります。

Power BI のコンテンツへのアクセスを許可する主な方法は次のとおりです。

- [ワークスペース ロール](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces) (コンテンツの編集者および閲覧者用)。
- パッケージ化されたワークスペース コンテンツのセットに適用される、[アプリのアクセス許可](../collaborate-share/service-create-distribute-apps.md#publish-your-app) (閲覧者用)。
- 個々のレポートまたはダッシュボードの[共有](../collaborate-share/service-share-dashboards.md) (閲覧者用)。

> [!TIP]
> セキュリティを効果的に管理する方法についてコンテンツ作成者にトレーニングを行うことをお勧めします。 また、信頼性の高いテスト、監査、監視を実施することも重要です。

### <a name="validate-functionality"></a>機能の検証

次は、フィールド名、書式設定、並べ替え、既定の概要作成の動作など、データセットの詳細をダブルチェックします。 [スライサー](../visuals/power-bi-visualization-slicers.md)、[ドリルダウン](../consumer/end-user-drill.md)、[ドリルスルー](../create-reports/desktop-drillthrough.md)、[式](../create-reports/desktop-conditional-format-visual-titles.md)、[ボタン](../create-reports/desktop-buttons.md)、[ブックマーク](../create-reports/desktop-bookmarks.md)など、対話型のレポート機能もすべて検証する必要があります。

開発プロセスでは、Power BI ソリューションを Power BI サービスの開発ワークスペースに定期的に発行する必要があります。 すべての機能がサービスで期待どおりに動作することを確認します (カスタム ビジュアルのレンダリングなど)。 それは、さらにテストを実行するのにも適したタイミングです。 [スケジュールされた更新](../connect-data/refresh-scheduled-refresh.md)、[Q&A](../consumer/end-user-q-and-a.md)、また、レポートとダッシュボードが[モバイル デバイス](../consumer/mobile/mobile-apps-for-mobile-devices.md)でどのように表示されるかをテストします。

### <a name="validate-performance"></a>パフォーマンスの検証

Power BI ソリューションのパフォーマンスは、コンシューマーのエクスペリエンスにとって重要です。 ほとんどのレポートでは、10 秒以内にビジュアルが表示される必要があります。 読み込みにそれよりも時間がかかるレポートがある場合は、一度立ち止まって、何が遅延の原因になっているかを再検討します。 レポートのパフォーマンスは、Power BI Desktop に加えて、Power BI サービスで定期的に評価する必要があります。

基準を下回る [DAX (Data Analysis eXpressions)](../transform-model/desktop-quickstart-learn-dax-basics.md)、不適切なデータセット デザイン、または最適でないレポート デザイン (たとえば、1 つのページに表示されるビジュアルの数が多すぎるなど) によって、多くのパフォーマンスの問題が発生します。 ネットワーク、過負荷のデータ ゲートウェイ、Premium 容量がどのように構成されているかといった技術的な環境の問題も、パフォーマンスの問題の原因になることがあります。 詳細については、「[Power BI の最適化ガイド](power-bi-optimization.md)」と「[Power BI でのレポートのパフォーマンスのトラブルシューティング](report-performance-troubleshoot.md)」を参照してください。

## <a name="document-the-solution"></a>ソリューションの文書化

Power BI ソリューションに役立つドキュメントには、主に次の 2 種類があります。

- データセットのドキュメント
- レポートのドキュメント

ドキュメントは、対象ユーザーが最も簡単にアクセスできる場所に保存できます。 一般的なオプションは次のとおりです。

- **SharePoint サイト内:** SharePoint サイトは、センター オブ エクセレンスまたは社内 Power BI コミュニティ サイトとして存在する場合があります。
- **アプリ内:** Power BI アプリを発行するときに URL を構成して、コンシューマーに詳細情報を案内することができます。
- **個々の Power BI Desktop ファイル内:** テーブルや列などのモデル要素に説明を定義できます。 このような説明は、レポートを作成するときに、 **[フィールド]** ペインにヒントとして表示されます。

> [!TIP]
> Power BI 関連のドキュメントのハブとして機能するサイトを作成する場合は、その URL の場所を使用して [[ヘルプの表示] メニューをカスタマイズする](../admin/service-admin-portal.md#publish-get-help-information)ことを検討します。

### <a name="create-dataset-documentation"></a>データセットのドキュメントの作成

データセットのドキュメントは、将来データセットを管理するユーザーを対象としています。 次のものを含めると便利です。

- 設計上の決定とその理由。
- データセットの所有、メンテナンス、認定を行うユーザー。
- データ更新の要件。
- データセットに定義されたカスタム ビジネス ルール。
- 特定のデータセットのセキュリティまたはデータのプライバシーに関する要件。
- 将来のメンテナンスのニーズ。
- 既知の未解決の問題または遅延バックログ項目。

また、時間の経過に伴ってデータセットに発生した最も重要な変更をまとめた、変更ログを作成することもできます。

### <a name="create-report-documentation"></a>レポートのドキュメントの作成

レポートのドキュメントは、通常、レポート コンシューマーを対象とするチュートリアルとして構成されており、コンシューマーがレポートやダッシュボードからより多くの価値を得るのに役立ちます。 多くの場合、短いビデオ チュートリアルが効果的です。

また、レポートの非表示ページに追加のレポート ドキュメントを含めることもできます。 これには、設計上の決定と変更ログを含めることができます。

## <a name="next-steps"></a>次のステップ

[この Power BI 移行シリーズの次の記事](powerbi-migration-deploy-support-monitor.md)では、Power BI に移行するときのコンテンツの展開、サポート、監視に関係するステージ 5 について説明します。

その他の役に立つリソースは次のとおりです。

- [Microsoft の BI 変換](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Power BI のエンタープライズ展開の計画に関するホワイト ペーパー](https://aka.ms/PBIEnterpriseDeploymentWP)
- わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
- Power BI チームへのご提案は、 [Power BI を改善するためのアイデアをお寄せください](https://ideas.powerbi.com/)

経験豊富な Power BI パートナーを活用して、組織の移行プロセスを成功させることができます。 Power BI パートナーを手配するには、[Power BI パートナー ポータル](https://powerbi.microsoft.com/partners/)にアクセスしてください。
