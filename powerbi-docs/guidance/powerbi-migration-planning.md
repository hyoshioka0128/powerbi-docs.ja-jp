---
title: Power BI に移行するためのデプロイを計画する
description: Power BI に移行する場合のデプロイ計画に関するガイダンス。
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/20/2020
ms.openlocfilehash: f161819b6e26c197bacc5534b5abfb426d612624
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96419224"
---
# <a name="plan-deployment-to-migrate-to-power-bi"></a>Power BI に移行するためのデプロイを計画する

この記事では、単一の Power BI ソリューションの移行計画に関係する **ステージ 2** について説明します。

:::image type="content" source="media/powerbi-migration-planning/migrate-to-powerbi-stage-2.png" alt-text="Power BI への移行のステージを示す画像。この記事では、ステージ 2 を重点的に説明します。":::

> [!NOTE]
> 上の図の詳細については、「[Power BI への移行の概要](powerbi-migration-overview.md)」を参照してください。

ステージ 2 の中心的な作業は、ソリューションを Power BI に移行するために、ステージ 1 で定義された要件をどのように使用するかを定義することです。

ステージ 2 の成果としては、デプロイ プロセスを導くための可能な限り多くの明確な意思決定があります。

この性質の意思決定は、反復的で非線形のプロセスです。 一部の計画は、[移行前の手順](powerbi-migration-pre-migration-steps.md)で既に行われています。 概念実証 ([ステージ 3](powerbi-migration-proof-of-concept.md) で説明) の実施は、デプロイ計画と並行して行われる可能性があります。 ソリューションの作成 ([ステージ 4](powerbi-migration-create-validate-content.md) で説明) 中でも、デプロイに関する意思決定に影響を与える追加の情報が発生する可能性があります。

> [!IMPORTANT]
> ステージ 1 から 5 は、1 つの特定のソリューションに関連するアクティビティを表します。 組織やテナント レベルでは、ソリューション レベルでのプロセスに影響を与える意思決定とアクティビティがあります。 このような上位レベルの計画アクティビティの一部については、「[Power BI への移行の概要](powerbi-migration-overview.md)」で説明されています。 効率と一貫性のために、必要に応じて、組織レベルの意思決定に従ってください。

> [!TIP]
> この記事で説明するトピックは、標準の Power BI 実装プロジェクトにも適用されます。

## <a name="choose-power-bi-product"></a>Power BI 製品を選択する

最初に決定する事項の 1 つは、Power BI 製品の選択です。 これは、[Power BI サービス](../fundamentals/power-bi-service-overview.md)または [Power BI Report Server](../report-server/get-started.md) のどちらにするかという決定です。 コンテンツが公開されると、埋め込み、モバイル配信、電子メール サブスクリプションなど、多くの追加オプションが使用できるようになります。

アーキテクチャに関する考慮事項の詳細については、ホワイトペーパー「[Power BI のエンタープライズ展開の計画](https://aka.ms/PBIEnterpriseDeploymentWP)」の **セクション 3** を参照してください。

> [!CAUTION]
> ファイル システムに格納されている Power BI Desktop ファイルの使用に依存する場合は、それが最適な方法ではないことにご注意ください。 Power BI サービス (または Power BI Report Server) を使用することは、セキュリティ、コンテンツ配布、コラボレーションに関して大きな利点があります。 Power BI サービスでは、アクティビティを監査および監視する機能も使用できます。

## <a name="decide-on-workspace-management-approach"></a>ワークスペースの管理アプローチを決定する

[ワークスペース](../collaborate-share/service-new-workspaces.md)は、Power BI サービスの中核となる概念であり、ワークスペースの管理は計画の重要な側面になります。 確認する事項としては、次のようなものがあります。

- この新しいソリューションに新しいワークスペースは必要であるか?
- デプロイ、テスト、運用に対応するために個別のワークスペースが必要となるか?
- データとレポートに個別のワークスペースを使用するか、または単一のワークスペースだけで十分であるか? 個別のワークスペースには、特にデータセットをセキュリティで保護する上で、さまざまな利点があります。 必要に応じて、これらを、レポートを公開するユーザーとは別に管理することができます。
- ワークスペースのセキュリティ要件は何か? これは、[ワークスペースのロール](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces)の計画に影響します。 アプリがコンテンツ コンシューマーによって使用される場合、[アプリのアクセス許可](../collaborate-share/service-create-distribute-apps.md#publish-your-app)は、ワークスペースとは別に管理されます。 アプリ ビューアーに対して個別のアクセス許可を使用することにより、レポートまたはダッシュボードの読み取り専用コンシューマーのセキュリティ要件にさらに柔軟に対応できます。
- 新しいコンテンツをセキュリティで保護するために既存のグループを使用できるか? Azure Active Directory と Microsoft 365 の両方のグループがサポートされます。 既存のプロセスと連携させる場合、グループを使用すると、個々のユーザーに割り当てるよりもアクセス許可の管理が容易になります。
- 外部のゲスト ユーザーに関してセキュリティ上の考慮事項はあるか? [ゲスト ユーザーのアクセス](../admin/service-admin-azure-ad-b2b.md)を構成するには、Azure Active Directory 管理者と Power BI 管理者が協力することが必要になる場合があります。

> [!TIP]
> 特定のビジネス アクティビティまたはプロジェクト用にワークスペースを作成することを検討してください。 組織構造に基づくワークスペース (部署ごとのワークスペースなど) の構築を開始したくなるかもしれませんが、この方法は、多くの場合、あまりにも範囲が広すぎることになります。

## <a name="determine-how-content-will-be-consumed"></a>コンテンツの使用方法を決定する

これは、ソリューションのコンシューマーが好むレポートやダッシュボードの表示方法を理解するのに役立ちます。 確認する事項としては、次のようなものがあります。

- [Power BI アプリ](../consumer/end-user-apps.md) (単一のワークスペースのレポートとダッシュボードで構成) は、コンテンツをコンシューマーに配信する方法として最善であるか、またはコンテンツ ビューワーではワークスペースへの直接アクセスだけで十分であるか?
- 特定のレポートおよびダッシュボードは、[Teams](../collaborate-share/service-embed-report-microsoft-teams.md)、[SharePoint Online](../collaborate-share/service-embed-report-spo.md)、または[安全なポータルや Web サイト](../collaborate-share/service-embed-secure.md)などの他の場所に埋め込まれるか?
- コンシューマーは、[モバイル デバイス](../consumer/mobile/mobile-apps-for-mobile-devices.md)を使用してコンテンツにアクセスするか? 小さいフォーム ファクターのデバイスにレポートを配信するための要件は、一部の[レポート設計上の決定](../create-reports/desktop-create-phone-report.md)に影響を与えます。

## <a name="decide-if-other-content-may-be-created"></a>他のコンテンツを作成できるかどうかを決定する

コンシューマーに新しいコンテンツの作成を許可するかどうかに関しては、次のような重要な事項を決定する必要があります。

- 公開されたデータセットから新しいレポートを作成することをコンシューマーに許可するか? この機能は、データセットの[ビルド アクセス許可](../connect-data/service-datasets-build-permissions.md)をユーザーに割り当てることによって有効にすることができます。
- コンシューマーがレポートをカスタマイズしたい場合、レポートの[コピーを保存](../connect-data/service-datasets-copy-reports.md)し、ニーズに合わせてカスタマイズできるか?

> [!CAUTION]
> "_コピーの保存_" 機能は便利な機能ですが、レポートにグラフィックやヘッダーまたはフッター メッセージが含まれている場合は注意して使用する必要があります。 ログ、アイコン、テキスト メッセージは、多くの場合、ブランド化の要件または規制コンプライアンスに関連するため、配信および配布の方法を慎重に制御することが重要です。 "_コピーの保存_" を使用し、元のグラフィックやヘッダーまたはフッター メッセージが新しい作成者によって変更されないままであれば、レポートの実際の作成者について混乱を招く可能性があります。 また、ブランド化の意味が薄れる可能性もあります。

## <a name="evaluate-needs-for-premium-capacity"></a>Premium 容量の必要性を評価する

ワークスペースを [Premium 容量](../admin/service-premium-what-is.md)に格納すると、追加の機能を使用できます。 Premium 容量上のワークスペースが有利であるいくつかの理由を次に示します。

- Power BI Pro ライセンスを持たないコンシューマーでも、コンテンツにアクセスできます。
- 大規模なデータセットのサポート。
- より頻繁なデータ更新のサポート。
- データフローの完全な機能セットの使用のサポート。
- デプロイ パイプラインや XMLA エンドポイントなどのエンタープライズ機能。
- ページ分割されたレポートのサポート (ワークロードが有効になっている場合)。

## <a name="determine-data-acquisition-method"></a>データの取得方法を決定する

レポートに必要なデータは、いくつかの決定に影響を与える可能性があります。 確認する事項としては、次のようなものがあります。

- 既存の Power BI [共有データセット](../connect-data/service-datasets-share.md)を使用できるか、またはこのソリューションには、新しい Power BI データセットを作成するのが適切であるか?
- 追加のニーズを満たすために、既存の共有データセットを新しいデータまたは測定値で増強する必要があるか?
- どの[データ ストレージ モード](../transform-model/desktop-storage-mode.md)が最も適切であるか? オプションとしては、インポート、DirectQuery、複合、またはライブ接続があります。
- クエリのパフォーマンスを強化するために[集計](../transform-model/desktop-aggregations.md)を使用する必要があるか?
- [データフロー](../transform-model/dataflows/dataflows-introduction-self-service.md)の作成が有用であるか? それは、さまざまなデータセットのソースとして機能できるか?
- 新しい[ゲートウェイ データ ソース](../connect-data/service-gateway-data-sources.md)を登録する必要はあるか?

## <a name="decide-where-original-content-will-be-stored"></a>元のコンテンツの格納場所を決定する

ターゲットのデプロイ先を計画するだけでなく、次のように、元 (ソース) のコンテンツを格納する場所を計画することも重要です。

- 元の Power BI Desktop (.pbix) ファイルを格納するための承認された場所を指定します。 この場所は、コンテンツを編集するユーザーのみが使用できるようにするのが理想的です。 これは、Power BI サービスでのセキュリティの設定方法と一致させる必要があります。
- バージョン管理の履歴またはソース管理を含む場所を元の Power BI Desktop ファイルに使用します。 バージョン管理により、コンテンツ作成者は、必要に応じて、以前のファイル バージョンに戻すことができます。 OneDrive for Business または SharePoint は、この目的に適しています。
- フラット ファイルや Excel ファイルなど、一元化されていないソース データを格納するための承認された場所を指定します。 これは、データセット作成者がエラーなく到達でき、定期的にバックアップされるパスである必要があります。
- Power BI サービスからエクスポートされたコンテンツのための承認された場所を指定します。 目標は、Power BI サービスで定義されたセキュリティが誤って回避されないようにすることを確実にすることです。

> [!IMPORTANT]
> 元の Power BI Desktop ファイル用に、保護された場所を指定することは、ファイルにインポートされたデータが含まれている場合に特に重要です。

## <a name="assess-the-level-of-effort"></a>作業のレベルを評価する

要件 ([ステージ 1](powerbi-migration-requirements.md) で説明) とソリューションのデプロイ計画プロセスから十分な情報が得られたら、作業のベルを評価することができます。 その後、タスク、タイムライン、責任を含むプロジェクト計画を策定することができます。

> [!TIP]
> ほとんどの組織では、通常、人件費 (給与および賃金) が最も高い費用です。 正確に見積もるのは難しい場合がありますが、生産性の向上は投資収益率 (ROI) に優れています。

## <a name="next-steps"></a>次のステップ

[この Power BI への移行シリーズの次の記事](powerbi-migration-proof-of-concept.md)では、ステージ 3 について説明します。このステージは、Power BI に移行する場合、可能な限り早期にリスクを軽減し、不明な部分に対処するための概念実証の実践に関係があります。

その他の役に立つリソースは次のとおりです。

- [Microsoft の BI 変換](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Power BI のエンタープライズ展開の計画に関するホワイト ペーパー](https://aka.ms/PBIEnterpriseDeploymentWP)
- わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
- Power BI チームへのご提案は、 [Power BI を改善するためのアイデアをお寄せください](https://ideas.powerbi.com/)

熟練の Power BI パートナーを活用して、組織の移行プロセスを成功させることができます。 Power BI パートナーを手配するには、[Power BI パートナー ポータル](https://powerbi.microsoft.com/partners/)にアクセスしてください。