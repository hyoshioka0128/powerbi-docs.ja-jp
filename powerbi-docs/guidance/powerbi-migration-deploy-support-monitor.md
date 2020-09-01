---
title: Power BI への展開
description: Power BI に移行するときのコンテンツの展開、サポート、および監視に関するガイダンス。
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/20/2020
ms.author: v-pemyer
ms.openlocfilehash: 58eb9af4975c0afeb12a71a880711ddd73e64d50
ms.sourcegitcommit: 84e75a2cd92f4ba4e0c08ba296b981b79d6d0e82
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/25/2020
ms.locfileid: "88803500"
---
# <a name="deploy-to-power-bi"></a>Power BI への展開

この記事では、Power BI に移行するときのコンテンツの展開、サポート、および監視に関係する**ステージ 5** について説明します。

:::image type="content" source="media/powerbi-migration-deploy-support-monitor/migrate-to-powerbi-stage-5.png" alt-text="Power BI への移行のステージを示す図。この記事では、ステージ 5 を重点的に説明します。":::

> [!NOTE]
> 上の図の詳細については、「[Power BI への移行の概要](powerbi-migration-overview.md)」を参照してください。

ステージ 5 の主な目的は、新しい Power BI ソリューションを運用環境にデプロイすることです。

このステージからの出力は、ビジネスですぐに使用できる運用ソリューションとなります。 アジャイル手法を使用する場合は、将来のイテレーションで提供される計画的な拡張機能をいくつか用意することが許容されます。 このステージでは、サポートと監視も重要であり、継続的に行う必要があります。

> [!TIP]
> 以下で説明するレガシ レポートを並列に実行したり、使用を停止したりする場合を除き、この記事で説明するトピックは、標準の Power BI 実装プロジェクトにも適用されます。

## <a name="deploy-to-test-environment"></a>テスト環境への展開

IT マネージド ソリューション、またはビジネスの生産性に不可欠なソリューションの場合は、一般的にテスト環境があります。 テスト環境は開発と運用の間に位置しますが、すべての Power BI ソリューションに必要なわけではありません。 テスト ワークスペースは、開発から切り離された安定した場所として機能し、運用環境にリリースする前にユーザー受け入れテスト (UAT) を行うことができます。

ご利用のコンテンツが Premium 容量のワークスペースに発行されている場合は、[配置パイプライン](../create-reports/deployment-pipelines-overview.md)によって、開発、テスト、運用の各ワークスペースに展開されるプロセスを簡略化することができます。 あるいは、手動で、または [PowerShell スクリプト](https://powerbi.microsoft.com/blog/duplicating-workspaces-by-using-power-bi-cmdlets/)を使用して発行することもできます。

### <a name="deploy-to-test-workspace"></a>テスト ワークスペースへの展開

テスト ワークスペースへの展開時の主なアクティビティは、次のとおりです。

- **接続文字列とパラメーター:** 開発とテストでデータ ソースが異なる場合は、データセットの接続文字列を調整します。 [パラメーター化](../connect-data/service-parameters.md)を使用すれば、接続文字列を効果的に管理することができます。
- **ワークスペースのコンテンツ:** データセットとレポートをテスト ワークスペースに発行し、ダッシュボードを作成します。
- **アプリ:** テスト ワークスペースからのコンテンツを使用して[アプリ](../consumer/end-user-apps.md)を発行するのは、それが UAT プロセスの一部を形成する場合です。 通常、アプリのアクセス許可は、UAT に関与する少数のユーザーに制限されています。
- **データ更新:** UAT がアクティブに実行されている期間のインポート データセットについては、[データセットの更新をスケジュール](../connect-data/refresh-scheduled-refresh.md)します。
- **セキュリティ:** [ワークスペース ロール](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces)を更新または確認します。 ワークスペース アクセスのテストには、UAT に関与する少数のユーザーが含まれます。

> [!NOTE]
> 開発、テスト、および運用への展開のオプションの詳細については、[Power BI のエンタープライズ展開の計画に関するホワイトペーパー](https://aka.ms/PBIEnterpriseDeploymentWP)のセクション 9 を参照してください。

### <a name="conduct-user-acceptance-testing"></a>ユーザー受け入れテストを実施する

一般に、UAT には領域の専門家であるビジネス ユーザーが必要です。 検証が完了すると、彼らは、新しいコンテンツが正確であること、要件を満たしていること、および他にユーザーによる、より広範な使用のための展開が可能であることを承認します。

この UAT プロセスがどの程度正式であるか (書面による承認を含む) は、自社の変更管理手法によって異なります。

## <a name="deploy-to-production-environment"></a>運用環境に展開する

運用環境への展開を行うには、いくつかの考慮事項があります。

### <a name="conduct-a-staged-deployment"></a>段階的な展開を実施する

リスクおよびユーザーの中断を最小限に抑えようとしている場合、または他の懸念事項がある場合は、段階的な展開を実行することを選択できます。 運用環境への最初の展開では、パイロット ユーザーのグループを小さくすることが必要な場合があります。 パイロットでは、パイロット ユーザーにフィードバックを積極的に求めることができます。

すべてのターゲット ユーザーが新しい Power BI ソリューションへのアクセス許可を持つようになるまで、運用ワークスペースまたはアプリのアクセス許可を段階的に展開します。

> [!TIP]
> [Power BI アクティビティ ログ](../admin/service-admin-auditing.md)を使用して、コンシューマーが新しい Power BI ソリューションをどのように導入し、使用しているかを理解します。

### <a name="handle-additional-components"></a>追加のコンポーネントを処理する

デプロイ プロセス中には、Power BI 管理者と協力して、ソリューション全体をサポートするために必要であるその他の要件に対処することが必要な場合があります。次に例を示します。

- **ゲートウェイのメンテナンス:** データ ゲートウェイに[新しいデータ ソース](../connect-data/service-gateway-data-sources.md)を登録することが必要になる場合があります。
- **ゲートウェイのドライバーとコネクタ:** 新しい専用のデータ ソースを使用するには、ゲートウェイ クラスター内の各サーバーに新しいドライバーまたはカスタム コネクタをインストールすることが必要になる場合があります。
- **新しい Premium 容量を作成する:** 既存の [Premium 容量](../admin/service-premium-capacity-manage.md)を使用できる場合があります。 または、新しい Premium 容量が保証されている場合もあります。 部門のワークロードを意図的に分離したい場合が、それに該当すると考えられます。
- **Power BI データフローを設定する:** Power Query Online を使用すれば、[Power BI データフロー](../transform-model/service-dataflows-overview.md)にデータ準備アクティビティを一度設定することができます。 これは、さまざまな Power BI Desktop ファイル内でデータ準備作業がレプリケートされるのを回避するのに役立ちます。
- **組織のビジュアルを新規に登録する:** AppSource から生成されていないカスタム ビジュアルについては、管理ポータルで[組織のビジュアル](../developer/visuals/power-bi-custom-visuals-organization.md)を登録することができます。
- **おすすめのコンテンツを設定する:** Power BI サービス ホームページで[コンテンツをおすすめに登録する](https://powerbi.microsoft.com/blog/promote-your-reports-dashboards-and-apps-on-power-bi-home/)ことができるユーザーを制御するテナント設定が存在します。
- **秘密度ラベルを設定する:** すべての[秘密度ラベル](../admin/service-security-data-protection-overview.md)が Microsoft Information Protection に統合されています。

### <a name="deploy-to-production-workspace"></a>運用環境のワークスペースに展開する

運用ワークスペースへの展開中の主なアクティビティは、次のとおりです。

- **変更管理:** 必要に応じて、標準的な変更管理手法を使用して、展開の承認を取得し、展開をユーザー全体に通知します。 運用展開が許可されている承認された変更管理期間が存在する場合があります。 通常は、これは IT マネージド コンテンツに適用することができ、セルフサービス コンテンツにはあまり適用されません。
- **ロールバック計画**: 移行では、それが新しいソリューションの初めての移行であることが想定されます。 コンテンツが既に存在する場合は、必要になったときに、以前のバージョンに戻す計画を立てることが賢明です。 以前のバージョンの Power BI Desktop ファイル (SharePoint または OneDrive のバージョン管理を使用) がある場合に、これは効果を発揮します。
- **接続文字列とパラメーター:** テストと運用でデータ ソースが異なる場合は、データセットの接続文字列を調整します。 [パラメーター化](/connect-data/service-parameters.md)を使用すれば、この目的を効果的に達成できます。
- **データ更新:** インポートされたデータセットについては、[データセットの更新をスケジュール](../connect-data/refresh-scheduled-refresh.md)します。
- **ワークスペースのコンテンツ:** データセットとレポートを運用ワークスペースに発行し、ダッシュボードを作成します。 ご利用のコンテンツが Premium 容量のワークスペースに発行されている場合は、[配置パイプライン](../create-reports/deployment-pipelines-overview.md)によって、開発、テスト、運用の各ワークスペースに展開されるプロセスを簡略化することができます。
- **アプリ:** アプリがコンテンツ配布戦略の一部である場合は、運用ワークスペースからのコンテンツを使用して[アプリ](../consumer/end-user-apps.md)を発行します。
- **セキュリティ:** 自社のコンテンツ配布およびコラボレーションの戦略に基づいて、[ワークスペースのロール](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces)を更新して確認します。
- **データセットの設定:** データセットごとに次のような設定を更新して確認します。
  - [推奨](../connect-data/service-datasets-certify.md) (認定済みまたは昇格済みなど)
  - ゲートウェイ接続またはデータ ソースの資格情報
  - スケジュールされている更新
  - [おすすめの Q&A 質問](../create-reports/service-q-and-a-create-featured-questions.md)
- **レポートとダッシュボードの設定:** レポートおよびダッシュボードごとに設定を更新して確認します。 最も重要な設定は次のとおりです。
  - 説明
  - 連絡先のユーザーまたはグループ
  - [秘密度ラベル](../collaborate-share/service-security-apply-data-sensitivity-labels.md)
  - [おすすめコンテンツ](https://powerbi.microsoft.com/blog/promote-your-reports-dashboards-and-apps-on-power-bi-home/)
- **サブスクリプション:** 必要に応じて、レポートのサブスクリプションを設定します。

> [!IMPORTANT]
> この時点で、大きなマイルストーンに達しています。 移行完了時には、成果を公表します。

### <a name="communicate-with-users"></a>ユーザーと通信する

新しいソリューションをコンシューマーに発表します。 コンテンツが置かれている場所に加えて、関連するドキュメント、FQA、およびチュートリアルを彼らに知らせます。 新しいコンテンツを導入するには、ランチミーティング型のセッションをホストすることを検討するか、オンデマンド ビデオを準備してください。

ヘルプをリクエストする方法、およびフィードバックを提供する方法についての説明を必ず記載してください。

### <a name="conduct-a-retrospective"></a>振り返りを実施する

振り返りを実施することで移行でうまくいったこと、および次の移行でより良くできることの確認を検討してください。

## <a name="run-in-parallel"></a>並行して実行する

多くの場合、新しいソリューションは、事前に定義された期間、レガシ ソリューションと並行して実行されます。 並列して実行することの利点は次のとおりです。

- リスクの軽減。特にレポートがミッションクリティカルであると見なされる場合。
- ユーザーが新しい Power BI ソリューションに慣れるまでの時間を確保できます。
- Power BI に表示される情報をレガシ レポートと相互参照することができます。

## <a name="decommission-the-legacy-report"></a>レガシ レポートの使用を停止する

レガシ BI プラットフォームでは、ある時点で、Power BI に移行されたレポートを無効にする必要があります。 レガシ レポートの使用停止は、次の場合に行われます。

- 並列して実行するための事前に定義された時間 (ユーザー全体に伝えられている必要がある) が終了した。 通常は 30 から 90 日です。
- レガシ システムのユーザーがすべて、新しい Power BI ソリューションにアクセスできる。
- レガシ レポートでは、重要なアクティビティが発生しなくなりました。
- 新しい Power BI ソリューションで、ユーザーの生産性に影響を与える可能性がある問題が発生していない。

## <a name="monitor-the-solution"></a>ソリューションを監視する

[Power BI アクティビティ ログ](../admin/service-admin-auditing.md)からのイベントを使用すれば、新しいソリューションの使用パターン (または Power BI Report Server に展開されたコンテンツに関する[実行ログ](/sql/reporting-services/report-server/report-server-executionlog-and-the-executionlog3-view?view=sql-server-ver15)) を把握できます。 アクティビティ ログを分析することは、実際の使用状況が期待と異なるかどうかを判断するのに役立ちます。 また、それによって、ソリューションが適切にサポートされていることを検証することもできます。

アクティビティ ログを確認することによって対処できる質問をいくつか次に示します。

- コンテンツはどのくらいの頻度で表示されますか。
- コンテンツを表示するのはどのような人ですか。
- コンテンツは通常、アプリまたはワークスペースを通じて表示されますか。
- ユーザーのほとんどは、ブラウザーまたはモバイル アプリケーションを使用していますか。
- サブスクリプションは使用されていますか。
- このソリューションに基づく新しいレポートが作成されていますか。
- コンテンツは頻繁に更新されていますか。
- セキュリティはどのように定義されていますか。
- データ更新の失敗など、何度も問題が発生していますか。
- 追加のトレーニングが必要になる可能性があることを意味すると考えられる重大なアクティビティが発生していますか (たとえば、大量のエクスポートアクティビティや多数の個別のレポート共有など)。

> [!IMPORTANT]
> アクティビティ ログを必ず定期的に確認するようにしてください。 単にそれをキャプチャして履歴を格納することは、監査またはコンプライアンスの目的を達成する上で価値のあることです。 ただし、実際の価値は、事前対応型のアクションを実行できる場合にわかります。

## <a name="support-the-solution"></a>ソリューションをサポートする

移行が完了しても、問題に対処し、パフォーマンスの問題を処理するために移行後の期間が重要となります。 時間の経過と共に、移行されたソリューションは、ビジネス ニーズの進化に伴って変化する可能性があります。

セルフ サービス BI が組織全体でどのように管理されているかに応じて、行われるサポートは少し異なる傾向があります。 ビジネス ユニット全体における Power BI のエキスパートが、非公式に第一線のサポートとして行動することがよくあります。 それは非公式の役割ですが、推奨されるべき重要なものです。

サポート チケットを使用して IT 部門によって運営される正式なサポート プロセスを用意することも、日常的なシステム指向の要求を処理し、エスカレーションを行うために不可欠です。

また、組織内で Power BI のサポート、教育、および管理を行う社内コンサルタントのように活動する[センター オブ エクセレンス (COE)](center-of-excellence-establish.md) を置くこともできます。 COE は、内部ポータルで有用な Power BI コンテンツをキュレートする役割を担うことができます。

最後に、コンテンツのコンシューマーに対して、コンテンツに関する質問の問い合わせ先を明確に示し、問題点または改善点に関するフィードバックを提供するためのメカニズムを用意する必要があります。

## <a name="next-steps"></a>次のステップ

[このシリーズの最終記事](powerbi-migration-learn-from-customers.md)では、顧客の Power BI への移行事例から学びます。

その他の役に立つリソースは次のとおりです。

- [Microsoft の BI 変換](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Power BI のエンタープライズ展開の計画に関するホワイト ペーパー](https://aka.ms/PBIEnterpriseDeploymentWP)
- わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
- Power BI チームへのご提案は、 [Power BI を改善するためのアイデアをお寄せください](https://ideas.powerbi.com/)

経験豊富な Power BI パートナーを活用して、組織の移行プロセスを成功させることができます。 Power BI パートナーを手配するには、[Power BI パートナー ポータル](https://powerbi.microsoft.com/partners/)にアクセスしてください。