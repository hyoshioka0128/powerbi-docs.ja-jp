---
title: SQL Server Reporting Services レポートを Power BI に移行する
description: SQL Server Reporting Services (SSRS) のレポートを Power BI に移行するためのガイダンスです。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 01/03/2020
ms.openlocfilehash: f1b9b710c9f9e4ade80866026f728ddbe3ae6971
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96393188"
---
# <a name="migrate-sql-server-reporting-services-reports-to-power-bi"></a>SQL Server Reporting Services レポートを Power BI に移行する

この記事の対象者は、SQL Server Reporting Services (SSRS) レポートの作成者と Power BI の管理者です。 [レポート定義言語 (RDL)](/sql/reporting-services/reports/report-definition-language-ssrs) で作成されたレポートを Power BI に移行するときに役立つガイダンスを提供します。

> [!NOTE]
> 移行できるのは RDL レポートだけです。 Power BI では、RDL レポートは "_ページ分割されたレポート_" と呼ばれます。

ガイダンスは 4 つのステージに分かれています。 レポートを移行する前に、まず記事全体を読むことをお勧めします。

1. [開始前の準備](#before-you-start)
1. [移行前ステージ](#pre-migration-stage)
1. [移行ステージ](#migration-stage)
1. [移行後ステージ](#post-migration-stage)

SSRS サーバーのダウンタイムや、レポート ユーザーの混乱を発生させずに、移行を行うことができます。 データやレポートを削除する必要がないことを理解しておくことが重要です。 したがって、使用を中止する準備が整うまで、現在の環境をそのままにしておくことができます。

## <a name="before-you-start"></a>開始する前に

移行を始める前に、環境が特定の前提条件を満たしていることを確認する必要があります。 これらの前提条件について説明し、便利な移行ツールを紹介します。

### <a name="preparing-for-migration"></a>移行の準備

Power BI にレポートを移行する準備では、まず、組織に [Power BI Premium](../admin/service-premium-what-is.md) サブスクリプションがあることを確認します。 Power BI のページ分割されたレポートをホストして実行するには、このサブスクリプションが必要です。

### <a name="supported-versions"></a>サポートされているバージョン

オンプレミスで実行されている SSRS インスタンス、または Azure などのクラウド プロバイダーによってホストされている仮想マシン上の SSRS インスタンスを、移行できます。

次の一覧は、Power BI への移行をサポートされている SQL Server のバージョンです。

> [!div class="checklist"]
> - SQL Server 2012
> - SQL Server 2014
> - SQL Server 2016
> - SQL Server 2017
> - SQL Server 2019

Power BI Report Server から移行することもできます。

### <a name="migration-tool"></a>移行ツール

レポートを準備して移行するには、[RDL 移行ツール](https://github.com/microsoft/RdlMigration)を使用することをお勧めします。 このツールは、ユーザーが SSRS サーバーから Power BI に RDL レポートを移行するのを助けるため、Microsoft によって開発されました。 GitHub から入手でき、移行シナリオのエンドツーエンドのチュートリアルが付属しています。

そのツールを使うと、次のタスクを自動化できます。

* [サポートされていないデータ ソース](../paginated-reports/paginated-reports-data-sources.md)および[サポートされていないレポート機能](../paginated-reports/paginated-reports-faq.md#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi)をチェックする
* "_共有_" リソースを "_埋め込み_" リソースに変換する
  * 共有 **データ ソース** は埋め込みデータ ソースになります
  * 共有 **データセット** は埋め込みデータセットになります
* (チェックに合格した) レポートを、ページ分割されたレポートとして、指定した Power BI ワークスペース (Premium 容量上) に発行する

既存のレポートが変更または削除されることはありません。 ツールが完了すると、完了したすべてのアクションの概要 (成功または失敗) が出力されます。

今後、ツールは Microsoft によって改善される可能性があります。 コミュニティにも、拡張への寄与と支援をお願いします。

## <a name="pre-migration-stage"></a>移行前ステージ

組織が前提条件を満たしていることを確認したら、"_移行前_" ステージを始める準備ができました。 このステージには、次の 3 つのフェーズがあります。

1. 検出
1. アクセス
1. 準備

### <a name="discover"></a>検出

"_検出_" フェーズの目的は、既存の SSRS インスタンスを確認することです。 このプロセスでは、ネットワークをスキャンして、組織内のすべての SQL Server インスタンスを識別します。

[Microsoft Assessment and Planning Toolkit](https://www.microsoft.com/download/details.aspx?id=7826) を使用できます。 "MAP Toolkit" とも呼ばれるこのツールでは、SQL Server のインスタンス、バージョン、インストールされている機能が検出されてレポートされます。 移行計画プロセスを簡素化できる、強力なインベントリ、評価、レポート ツールです。

### <a name="assess"></a>アクセス

SSRS インスタンスを検出した後の、_評価_ フェーズの目標は、移行できない SSRS レポート (またはサーバー項目) を理解することです。

SSRS サーバーから Power BI に移行できるのは、RDL レポートのみです。 移行された各 RDL レポートは、Power BI のページ分割されたレポートになります。

ただし、次の SSRS 項目の種類を Power BI に移行することはできません。

- 共有データ ソース<sup>1</sup>
- 共有データセット<sup>1</sup>
- リソース (画像ファイルなど)
- KPI (SSRS 2016 以降 — Enterprise Edition のみ)
- モバイル レポート (SSRS 2016 以降 — Enterprise Edition のみ)
- レポート モデル (非推奨)
- レポート パーツ (非推奨)

<sup>1</sup> [RDL 移行ツール](https://github.com/microsoft/RdlMigration)では、使われているデータ ソースがサポートされているものであれば、共有データ ソースと共有データセットが自動的に変換されます。

[Power BI のページ分割されたレポートでまだサポートされてい機能](../paginated-reports/paginated-reports-faq.md#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi)が RDL レポートで利用されている場合は、[Power BI レポート](../consumer/end-user-reports.md)として開発し直すことができます。 移行できる RDL レポートの場合でも、合理的な理由があれば、Power BI レポートとして最新化することをお勧めします。

RDL レポートで "_オンプレミスのデータ ソース_" からデータを取得する必要がある場合は、シングル サインオン (SSO) を使用できません。 現在のところ、これらのソースからのすべてのデータ取得は、"_ゲートウェイ データ ソース ユーザー アカウント_" のセキュリティ コンテキストを使用して行われています。 SQL Server Analysis Services (SSAS) でユーザーごとに行レベルのセキュリティ (RLS) を適用することはできません。

通常、Power BI のページ分割されたレポートは、**印刷** または **PDF 生成** に対して最適化されています。 Power BI レポートは、**探索と対話性** に最適化されています。 詳細については、「[どのようなときに Power BI のページ分割されたレポートを使用するか](report-paginated-or-power-bi.md)」を参照してください。

### <a name="prepare"></a>準備

"_準備_" フェーズの目的は、すべての準備を完了することです。 Power BI 環境の設定、レポートをセキュリティで保護して発行する方法の計画、移行されない SSRS 項目の再開発の構想が含まれます。

1. Power BI Premium 容量で[ページ分割されたレポート ワークロード](../admin/service-admin-premium-workloads.md#paginated-reports)が有効になっていること、および十分なメモリがあることを確認します。
1. レポートの[データ ソース](../paginated-reports/paginated-reports-data-sources.md)のサポートを確認し、オンプレミスのデータ ソースとの接続を許可するように [Power BI Gateway](../connect-data/service-gateway-onprem.md) を設定します。
1. Power BI のセキュリティについてよく理解し、[Power BI のワークスペースとワークスペース ロール](../collaborate-share/service-new-workspaces.md)で [SSRS のフォルダーとアクセス許可を再現する方法](/sql/reporting-services/security/secure-folders)を計画します。
1. Power BI の共有についての理解を深め、[Power BI アプリ](../collaborate-share/service-create-distribute-apps.md)を発行してコンテンツを配布する方法を計画します。
1. SSRS 共有データ ソースの代わりに、[共有 Power BI データセット](../connect-data/service-datasets-build-permissions.md)を使用することを検討します。
1. [Power BI Desktop](../fundamentals/desktop-what-is-desktop.md) を使用して、モバイルに最適化されたレポートを開発します。場合によっては、SSRS モバイル レポートと KPI の代わりに、[Power KPI カスタム ビジュアル](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083?tab=Overview)を使用します。
1. レポートの **UserID** 組み込みフィールドの使用を再評価します。 レポート データをセキュリティで保護するために **UserID** を利用している場合は、ページ分割されたレポート (Power BI サービスでホストされている場合) では、ユーザー プリンシパル名 (UPN) が返されることに注意してください。 そのため、組み込みフィールドでは、_AW\mblythe_ などの NT アカウント名が返されず、_m.blythe&commat;adventureworks.com_ のような値が返されます。 データセット定義と、場合によってはソース データを修正する必要があります。 修正して発行したら、データ アクセス許可が期待どおりに動作することを確認するためにレポートを徹底的にテストすることをお勧めします。
1. レポートの **ExecutionTime** 組み込みフィールドの使用を再評価します。 ページ分割されたレポート (Power BI サービスでホストされている場合) では、組み込みフィールドから "_協定世界時 (UTC)_ " で日時が返されます。 これは、レポート パラメーターの既定値と、レポート実行時間ラベル (通常はレポート フッターに追加されます) に影響する可能性があります。
1. お使いのデータソースが SQL Server (オンプレミス) の場合は、レポートでマップの視覚化が使用されていないことを確認します。 マップの視覚化は SQL Server の空間データ型に依存し、これらはゲートウェイではサポートされません。 詳細については、[ページ分割されたレポートでのデータ取得のガイダンス (SQL Server の複合データ型)](report-paginated-data-retrieval.md#sql-server-complex-data-types) に関するページを参照してください。
1. レポート作成者が [Power BI Report Builder](../paginated-reports/report-builder-power-bi.md) をインストールしていること、および以降のリリースを組織全体に簡単に配布できることを確認します。

## <a name="migration-stage"></a>移行ステージ

Power BI の環境とレポートを準備した後は、"_移行_" ステージを始めることができます。

移行オプションには、"_手動_" と "_自動_" の 2 種類があります。 手動移行は、レポートの数が少ない場合、または移行前にレポートを変更する必要がある場合に適しています。 自動移行は、多数のレポートの移行に適しています。

### <a name="manual-migration"></a>手動移行

SSRS インスタンスおよび Power BI ワークスペースへのアクセス権を持つユーザーは、手動でレポートを Power BI に移行できます。 手順は次のとおりです。

1. 移行するレポートが含まれる SSRS ポータルを開きます。
1. 各レポート定義をダウンロードし、.rdl ファイルをローカル環境に保存します。
1. "_最新バージョン_" の Power BI Report Builder を開き、Azure AD の資格情報を使って Power BI サービスに接続します。
1. Power BI Report Builder で各レポートを開き、次のようにします。
   1. すべてのデータ ソースとデータセットがレポート定義に埋め込まれていること、およびそれらが[サポートされているデータ ソース](../paginated-reports/paginated-reports-data-sources.md)であることを確認します。
   1. レポートをプレビューし、正しく表示されることを確認します。
   1. _[名前を付けて保存]_ オプションを選択し、 _[Power BI サービス]_ を選択します。
   1. レポートを格納するワークスペースを選択します。
   1. レポートが保存されたことを確認します。 レポートのデザインにまだサポートされていない機能が含まれる場合、保存操作は失敗します。 その理由が通知されます。 その場合は、レポートのデザインを変更してから、もう一度保存してみてください。

### <a name="automated-migration"></a>自動移行

自動移行には次の 2 つのオプションがあります。 使用できるもの:

- RDL 移行ツール
- SSRS および Power BI 用に公開されている API

[RDL 移行ツール](#migration-tool)については、この記事で既に説明しました。

一般公開されている SSRS および Power BI 用の API を使って、コンテンツの移行を自動化することもできます。 RDL 移行ツールでは既にこれらの API が使われていますが、正確な要件に適したカスタム ツールを開発できます。

API の詳細については、以下を参照してください。

- [Power BI REST API リファレンス](../developer/automation/rest-api-reference.md)
- [SQL Server Reporting Services REST API](/sql/reporting-services/developer/rest-api)

## <a name="post-migration-stage"></a>移行後ステージ

移行が正常に完了したら、"_移行後_" ステージに進むことができます。 このステージでは、一連の移行後タスクを実行して、すべてが正常かつ効率的に機能していることを確認します。

### <a name="configure-data-sources"></a>データ ソースの構成

レポートが Power BI に移行されたら、そのデータ ソースが正しく設定されていることを確認する必要があります。 それには、ゲートウェイ データ ソースへの割り当てと、[データ ソースの資格情報の安全な保管](../paginated-reports/paginated-reports-data-sources.md#azure-sql-database-authentication)が含まれます。 これらの作業は、RDL 移行ツールでは行われません。

### <a name="review-report-performance"></a>レポートのパフォーマンスを確認する

次のことを行って、レポートのユーザー エクスペリエンスを可能な限り快適にすることを強くお勧めします。

1. [Power BI でサポートされている各ブラウザー](../fundamentals/power-bi-browsers.md)でレポートをテストし、レポートが正しく表示されることを確認します。
1. テストを実行し、SSRS と Power BI でのレポートの表示時間を比較します。 Power BI のレポートが、許容できる時間内に表示されることを確認します。
1. メモリ不足のために Power BI レポートが表示されない場合は、[Power BI Premium 容量に追加のリソース](../admin/service-admin-premium-workloads.md#paginated-reports)を割り当てます。
1. 表示時間の長いレポートの場合は、[レポートが添付された電子メール サブスクリプション](../consumer/paginated-reports-subscriptions.md)としてレポートをユーザーに配信するよう Power BI を設定することを検討します。
1. Power BI データセットに基づく Power BI レポートの場合は、モデルの設計を見直して、完全に最適化されていることを確認します。

### <a name="reconcile-issues"></a>問題を調整する

移行後フェーズは、問題を調整し、パフォーマンスの問題に対処するために不可欠です。 ページ分割されたレポートのワークロードを容量に追加すると、ページ分割されたレポートおよびその容量に格納されている "_他のコンテンツ_" について、パフォーマンスが低下する可能性があります。

問題を理解して軽減するための具体的な手順など、これらの問題の詳細については、次の記事を参照してください。

- [Premium 容量を最適化する](../admin/service-premium-capacity-optimize.md)
- [アプリで Premium 容量を監視する](../admin/service-admin-premium-monitor-capacity.md)

## <a name="next-steps"></a>次の手順

この記事に関する詳細については、次のリソースを参照してください。

- [Power BI Premium のページ分割されたレポートとは](../paginated-reports/paginated-reports-report-builder-power-bi.md)
- [ページ分割されたレポートでのデータ取得のガイダンス](report-paginated-data-retrieval.md)
- [どのようなときに Power BI のページ分割されたレポートを使用するか](report-paginated-or-power-bi.md)
- [Power BI のページ分割されたレポート: FAQ](../paginated-reports/paginated-reports-faq.md)
- [オンライン コース: ページ分割されたレポート (1 日)](../learning-catalog/paginated-reports-online-course.md)
- [Power BI Premium のよく寄せられる質問](../admin/service-premium-faq.md)
- [RDL 移行ツール](https://github.com/microsoft/RdlMigration)
- わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
- Power BI チームへのご提案は、 [Power BI を改善するためのアイデアをお寄せください](https://ideas.powerbi.com)

Power BI パートナーを利用して、組織の移行プロセスを成功させることができます。 Power BI パートナーを手配するには、[Power BI パートナー ポータル](https://powerbi.microsoft.com/partners/)にアクセスしてください。
