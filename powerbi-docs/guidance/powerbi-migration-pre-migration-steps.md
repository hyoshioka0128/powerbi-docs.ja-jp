---
title: Power BI への移行を準備する
description: Power BI に移行する場合の移行前の手順に関するガイダンス。
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/20/2020
ms.openlocfilehash: 33bee844aced23973bd033cf0d9ae9d8caa4d267
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418580"
---
# <a name="prepare-to-migrate-to-power-bi"></a>Power BI への移行を準備する

この記事では、Power BI に移行する前に考慮できる操作について説明します。

:::image type="content" source="media/powerbi-migration-pre-migration-steps/migrate-to-powerbi-pre-migration-steps.png" alt-text="Power BI への移行のステージを示す画像。この記事では、移行前の手順について重点的に説明します。":::

> [!NOTE]
> 上の図の詳細については、「[Power BI への移行の概要](powerbi-migration-overview.md)」を参照してください。

移行前の手順では、事前の計画が重視されます。これは、5 つの移行ステージに進む前に重要な準備です。 移行前の手順のほとんどは 1 回実行されますが、大規模な組織では、事業単位または部門領域ごとに反復的に行われる場合があります。

移行前の手順の出力には、移行するレポートとデータのインベントリに加えて、初期ガバナンス モデルである初期の高レベルの初期展開計画が含まれます。 個々のソリューションを移行するための工数レベルを完全に見積もるには、ステージ 1、2、3 のアクティビティの追加情報が必要になります。

> [!TIP]
> この記事で説明するほとんどのトピックは、標準の Power BI 実装プロジェクトにも適用されます。

## <a name="create-costbenefit-analysis-and-evaluation"></a>コストまたはメリットの分析と評価を作成する

初期の評価では、次のような主な考慮事項があります。

- ビジネス ケースと BI 戦略を明確にして、具体的な目的の状態を実現する。
- 成功の意味と、移行イニシアチブの進行状況および成功を測定する方法を明確にする。
- コストの見積もりと、投資収益率 (ROI) の計算結果を取得する。
- 範囲と複雑さのレベルが低い、生産性の高いいくつかの Power BI イニシアチブが結果的に成功を収める。

## <a name="identify-stakeholders-and-executive-support"></a>利害関係者と役員サポートを識別する

利害関係者の識別に関するいくつかの考慮事項を次に示します。

- ビジネス ケースと BI 戦略での利害関係者との連携を確保する。
- 事業単位全体の代表者を含める。これは、後のスケジュールでコンテンツが移行予定の場合でも、その動機と懸念事項を理解するためのものです。
- Power BI のエキスパートを早期に含める。
- 関係者とのコミュニケーション計画を作成し、フォローする。

> [!TIP]
> オーバーコミュニケーションが危惧されるくらいの状態が、ほどよいと言えます。

## <a name="generate-initial-governance-model"></a>初期ガバナンス モデルを生成する

Power BI 実装の初期段階で対処すべきいくつかの重要な項目は、次のとおりです。

- Power BI 導入の具体的な目標と、組織の BI 戦略全体の中で Power BI が適合する場所。
- Power BI 管理者ロールがどのように処理されるか (特に、分散された組織で)。
- 信頼できるデータの実現に関連するポリシー: 権限のあるデータ ソースの使用、データ品質の問題への対処、一貫性のある用語と共通定義の使用。
- データ ソース、データ モデル、レポート、内部および外部ユーザーへのコンテンツ配信に関するセキュリティとデータのプライバシー戦略。
- 内部および外部のコンプライアンス、規制、監査の要件が満たされるかどうか。

> [!IMPORTANT]
> 最も効果的なガバナンス モデルは、ユーザーの権限と必要なレベルの制御とのバランスを取ることです。 詳細については、「[中核部での統制](center-of-excellence-microsoft-business-intelligence-transformation.md#discipline-at-the-core)」と「[エッジにおける柔軟性](center-of-excellence-microsoft-business-intelligence-transformation.md#flexibility-at-the-edge)」を参照してください。

## <a name="conduct-initial-deployment-planning"></a>初期の展開計画を実施する

初期の展開計画では、組織の Power BI 実装の標準、ポリシー、基本設定を定義します。

[ステージ 2](powerbi-migration-planning.md) ではソリューションレベルの展開計画を参照することにご注意ください。 ステージ 2 のアクティビティでは、可能な限り組織レベルの決定を考慮する必要があります。

Power BI 実装の初期段階で対処すべきいくつかの重要な項目は、次のとおりです。

- [Power BI のテナント設定](admin-tenant-settings.md)に関する決定。ドキュメントに記載する必要があります。
- [ワークスペース管理](../collaborate-share/service-new-workspaces.md)に関する決定。ドキュメントに記載する必要があります。
- アプリ、ワークスペース、共有、サブスクリプション、コンテンツの埋め込みなど、データと[コンテンツの配布方法](../collaborate-share/service-how-to-collaborate-distribute-dashboards-reports.md)に関連する考慮事項および基本設定。
- Import モードや DirectQuery モードの使用、[Composite モデルでの 2 つのモードの組み合わせ](composite-model-guidance.md)など、[データセット モード](../connect-data/service-dataset-modes-understand.md)に関連する基本設定。
- [データとアクセスの保護](../admin/service-admin-power-bi-security.md)。
- [共有データセット](../connect-data/service-datasets-share.md)を使用した再利用性の実現。
- [データ証明](../collaborate-share/service-endorsement-overview.md)の適用による、権限のある信頼できるデータの使用の促進。
- さまざまなユース ケースや事業単位に対する、Power BI レポート、Excel レポート、ページ分割されたレポートなどのさまざまな[レポートの種類](../create-reports/index.yml)の使用。
- 一元化された BI 成果物とビジネス管理の BI 成果物を管理するための変更管理アプローチ。
- コンシューマー、データ モデル作成者、レポート作成者、管理者向けのトレーニング計画。
- [Power BI Desktop テンプレート](../create-reports/desktop-templates.md)、[カスタム ビジュアル](https://powerbi.microsoft.com/blog/how-to-govern-power-bi-visuals-inside-your-organization/)、およびドキュメントに記載されたレポート デザイン標準を使用したコンテンツ作成者のサポート。
- 新しいライセンスの要求、新しいゲートウェイ データ ソースの追加、ゲートウェイ データ ソースへのアクセス許可の取得、新しいワークスペースの要求、ワークスペースのアクセス許可の変更、定期的に発生する可能性があるその他の一般的な要件など、ユーザーの要件を管理するための手順とプロセス。

> [!IMPORTANT]
> 展開計画は反復的なプロセスです。 展開に関する決定は、Power BI に関する組織の経験が豊かになり、Power BI が進化するにつれて、何度も改善され、強化されます。 このプロセスで行った決定は、移行プロセスの[ステージ 2](powerbi-migration-planning.md)に関するページで説明されているソリューションレベルの展開計画で使用されます。

## <a name="establish-initial-architecture"></a>初期アーキテクチャを確立する

[BI ソリューション アーキテクチャ](center-of-excellence-business-intelligence-solution-architecture.md)は、時間の経過と共に進化し、成熟します。 Power BI のすぐに処理べきセットアップ タスクは次のとおりです。

- Power BI テナントをセットアップし、Azure Active Directory と統合する。
- [Power BI 管理者](../admin/service-admin-role.md)を定義する。
- 初期の[ユーザー ライセンス](../admin/service-admin-licensing-organization.md)を取得し、割り当てる。
- [Power BI テナントの設定](admin-tenant-settings.md)を構成し、確認する。
- [ワークスペース ロール](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces)を設定し、Azure Active Directory セキュリティ グループおよびユーザーへのアクセス権を割り当てる。
- 定期的に更新する計画を使用して、初期の[データ ゲートウェイ](../connect-data/service-gateway-deployment-guidance.md) クラスターを構成する。
- 初期の [Premium 容量ライセンス](../admin/service-admin-premium-purchase.md)を購入する (該当する場合)。
- 継続的に管理する計画を使用して、[Premium 容量のワークロード](../admin/service-admin-premium-workloads.md)を構成する。

## <a name="define-success-criteria-for-migration"></a>移行の成功の基準を定義する

最初のタスクは、個々のソリューションを移行する場合の成功とはどのようなものかを理解することです。 次のような疑問が生じることが考えられます。

- **この移行の動機と目標は何ですか?** 詳細については、[「Power BI 移行の概要」の「移行の理由を検討する」](powerbi-migration-overview.md#consider-migration-reasons)を参照してください。 この記事では、Power BI に移行する最も一般的な理由について説明します。 もちろん、目標は組織レベルで指定する必要があります。 これに加えて、あるレガシ BI ソリューションを移行すると、コストの節約によって大きなメリットが得られる可能性があります。一方、別のレガシ BI ソリューションの移行では、ワークフローの最適化によるメリットを得ることに重点が置かれる場合があります。
- **この移行で予想されるコストやメリットまたは ROI はどのようなものですか?** コスト、強化された機能、複雑さの軽減、機敏性の向上に関連する期待値を明確に理解することは、成功を測定するうえで役立ちます。 これにより、移行プロセス中の意思決定に役立つ基本原則を提供できます。
- **成功を測定するためにどのような主要業績評価指標 (KPI) が使用されますか?** 次の一覧に KPI の例をいくつか示します。
    - レガシ BI プラットフォームから表示されるレポートの数。月単位で減少します。
    - Power BI から表示されるレポートの数。月単位で増加します。
    - Power BI レポートのコンシューマーの数。四半期単位で増加します。
    - ターゲットの日付別の運用環境に移行されたレポートの割合。
    - ライセンス コストの年単位の削減。

> [!TIP]
> [Power BI アクティビティ ログ](../admin/service-admin-auditing.md)は、KPI の進行状況を測定するためのソースとして使用できます。

## <a name="prepare-inventory-of-existing-reports"></a>既存のレポートのインベントリを準備する

レガシ BI プラットフォームで既存のレポートのインベントリを準備することは、既に存在するものを理解するための重要な手順です。 この手順の結果は、移行工数レベルを評価するための入力となります。 インベントリの準備に関連するアクティビティには、次のものが含まれます。

1. **レポートのインベントリ:** 移行の候補であるレポートとダッシュボードの一覧をコンパイルします。
2. **データ ソースのインベントリ:** 既存のレポートによってアクセスされるすべてのデータ ソースの一覧をコンパイルします。 これには、エンタープライズ データ ソースと部門データ ソースおよび個人データ ソースの両方が含まれている必要があります。 このプロセスでは、これまで IT 部門に知られていなかったデータ ソース ("_シャドウ IT_" とも呼ばれる) が明らかになる可能性があります。
3. **監査ログ:** レガシ BI プラットフォームの監査ログからデータを取得して、使用パターンを把握し、優先順位付けを支援します。 監査ログから取得する重要な情報は次のとおりです。
    - 各レポートが週、月、または四半期ごとに実行された平均回数。
    - 週、月、または四半期ごとのレポートあたりの平均コンシューマー数。
    - 各レポート (特に役員が使用するレポート) のコンシューマー。
    - 各レポートが実行された最新の日付。

> [!NOTE]
> 多くの場合、コンテンツはそのまま Power BI に移行されません。 移行は、データ アーキテクチャを再設計したり、レポートの配信を改善したりする機会を表します。 レポートのインベントリをコンパイルすることは、どのようなリファクタリングが必要であるかを評価できるように、現在存在しているものを理解するために重要です。 このシリーズの残りの記事では、改善の可能性について詳しく説明します。

## <a name="explore-automation-options"></a>オートメーション オプションの詳細

Power BI の変換プロセスをエンドツーエンドで完全に自動化することはできません。

自動化のための既存のツールがある場合は、自動化の候補として、データとレポートの既存のインベントリをコンパイルすることが考えられます。 移行プロセスの一部 (既存のインベントリのコンパイルなど) で自動化を使用できる程度は、使用しているツールによって大きく異なります。

## <a name="next-steps"></a>次のステップ

[この Power BI 移行シリーズの次の記事](powerbi-migration-requirements.md)では、Power BI への移行時における要件の収集と優先順位付けに関係するステージ 1 について説明します。

その他の役に立つリソースは次のとおりです。

- [Microsoft の BI 変換](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Power BI のエンタープライズ展開の計画に関するホワイト ペーパー](https://aka.ms/PBIEnterpriseDeploymentWP)
- わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
- Power BI チームへのご提案は、 [Power BI を改善するためのアイデアをお寄せください](https://ideas.powerbi.com/)

熟練の Power BI パートナーを活用して、組織の移行プロセスを成功させることができます。 Power BI パートナーを手配するには、[Power BI パートナー ポータル](https://powerbi.microsoft.com/partners/)にアクセスしてください。
