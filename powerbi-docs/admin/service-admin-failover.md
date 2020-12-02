---
title: Power BI の高可用性、フェールオーバー、およびディザスター リカバリーに関する FAQ
description: Power BI サービスでユーザーに高可用性、ビジネス継続性およびディザスター リカバリーがどのように提供されるかを理解します。
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 06/18/2020
LocalizationGroup: Administration
ms.openlocfilehash: ff41f702edc605ee346aa10a759e633377597504
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96408966"
---
# <a name="power-bi-high-availability-failover-and-disaster-recovery-faq"></a>Power BI の高可用性、フェールオーバー、およびディザスター リカバリーに関する FAQ

この記事では、Power BI サービスでユーザーに高可用性、ビジネス継続性およびディザスター リカバリーがどのように提供されるかについて説明します。 この記事を読み終える頃には、高可用性がどのように実現されるか、どのような状況で Power BI によってフェールオーバーが実行されるのか、また、フェールオーバー時にサービスに求められることについての理解が深まっているはずです。

## <a name="what-does-high-availability-mean-for-power-bi"></a>Power BI における "高可用性" にはどのような意味がありますか。

Power BI は、フル マネージドのサービスとしてのソフトウェア (SaaS) です。  Microsoft では、ユーザーがいつでも自分のレポートにアクセスできるように、インフラストラクチャ エラーに対して回復力を持たせるように設計し、運用しています。  サービスは [99.9% SLA](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=37) によってサポートされます。

## <a name="what-is-a-power-bi-failover"></a>Power BI のフェールオーバーとは

Power BI では、ビジネス継続性を保証するために Azure データセンター (リージョンともいう) 内の各コンポーネントの複数のインスタンスを保持します。 サービスが停止したか、問題が発生し、Power BI がリージョンでアクセス不可または操作不能となった場合、Power BI ではバックアップ インスタンスに対するそのリージョン内のすべてのコンポーネントが失敗します。 フェールオーバーによって、可用性と運用性は ([Microsoft Trust Center](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location) に示されているように、通常は同じ地理的場所内の) 新しいリージョンの Power BI サービス インスタンスに復元されます。

フェールオーバーされた Power BI サービスのインスタンスでサポートされるのは、_読み取り操作_ のみです。つまり、フェールオーバー中は、更新、レポートの発行操作、ダッシュボードまたはレポートの変更、および Power BI メタデータの変更が必要となるその他の操作 (レポートへのコメントの挿入など) はサポートされません。  (オンプレミス データ ソースに対する DirectQuery と Live Connect に基づいていない) ダッシュボードやレポートの表示などの読み取り操作は、引き続き正常に機能します。

## <a name="how-are-backup-instances-kept-in-sync-with-my-data"></a>バックアップ インスタンスとデータとの同期はどのように保持されますか。

Power BI サービスのすべてのコンポーネントでは、そのバックアップ インスタンスを定期的に同期します。 15 分ごとのポイントインタイム同期については、Power BI でアップロードまたは変更されたコンテンツが対象となります。 フェールオーバーが発生した場合、Power BI では [Azure ストレージ geo 冗長レプリケーション](/azure/storage/common/storage-redundancy-grs)と [Azure SQL geo 冗長レプリケーション](/azure/sql-database/sql-database-active-geo-replication)を使用して、バックアップ インスタンスが他のリージョンに存在することを保証し、フェールオーバーの場合に使用できるようにします。

## <a name="where-are-the-failover-clusters-located"></a>フェールオーバー クラスターはどこに配置されますか。

[Microsoft Trust Center](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location) に示されていない限り、バックアップ インスタンスは、組織が Power BI にサインアップしたときに選択されたのと同じ地理的場所 (geo) 内に存在します。 geo には複数のリージョンを含めることができ、Microsoft では、データの回復性のために特定の geo 内のいずれかのリージョンにデータをレプリケートする場合があります。 Microsoft では、geo 外に顧客データをレプリケートしたり、移動したりすることはありません。 Power BI によって提供される geo とそれに含まれるリージョンとのマッピングについては、[Microsoft Trust Center](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location) を参照してください。

## <a name="how-does-microsoft-decide-to-fail-over"></a>Microsoft ではフェールオーバーすることをどのように決定するのですか。

フェールオーバーがいつ必要になる可能性があるかを示す 2 つの異なるシステムがあります。

- 外部および内部の監視プローブでは、正しく操作できない、あるいは可用性が欠如していることを示します。 示される内容は、Power BI コンポーネント、またはリージョン内の Power BI が依存する 1 つ以上のサービスで検出されたサービス停止に基づく場合があります。
- リージョン内の重大なサービス停止については、Microsoft Azure の中央オペレーション チームによって通知されます。

いずれの場合も、Power BI エグゼクティブ チームのメンバーがフェールオーバーすることを決定します。つまり、決定自体は自動化されていません。 決定されると、フェールオーバーのプロセスが自動的に実行されます。

## <a name="how-do-i-know-power-bi-is-now-in-failover-mode"></a>Power BI が現在、フェールオーバー モードかどうかを確認するにはどうすればよいですか。

Power BI のサポート ページ ([https://powerbi.microsoft.com/support/](https://powerbi.microsoft.com/support/)) に通知が投稿されます。 通知には、ダッシュボードの発行、更新、作成、複製、およびアクセス許可の変更など、フェールオーバー時に利用できない主な操作が含まれます。

## <a name="how-long-does-it-take-power-bi-to-fail-over"></a>Power BI でのフェールオーバーにはどれくらいかかりますか。

フェールオーバーが必要であると判断されてから、Power BI が再度運用可能になるには約 15 分かかります。 フェールオーバーが必要であることの判断の時間は、破損のシナリオによって異なります。 

フェールオーバーが実行されると、Power BI は Azure Storage の GEO レプリケーションを使用してフェールオーバーを実行します。 このようなレプリケーションのリターン ポイントは通常 15 分ですが、SLA で [Azure Storage のこの時間が保証されていない](/azure/storage/common/storage-redundancy)ため、Power BI でも時間の保証はありません。 

## <a name="what-happens-to-workspaces-and-reports-if-my-premium-capacity-becomes-unavailable"></a>Premium 容量が使用できなくなった場合、ワークスペースとレポートはどうなりますか。 

Premium 容量が使用できなくなった場合、ワークスペースとレポートは、以前にそれらに対するアクセス権を持っていた Power BI Pro ライセンスを持つすべてのユーザーが引き続きアクセスして表示できます。

## <a name="when-does-my-power-bi-instance-return-to-the-original-region"></a>自分の Power BI インスタンスはいつ元のリージョンに戻りますか。

Power BI サービス インスタンスは、フェールオーバーの原因となった問題が解決されたときに元のリージョンに戻ります。 Power BI のサポート ページを確認してください。問題が解決されると、Power BI チームによって、フェールオーバーについて記述された通知が削除されます。 その時点で、操作は正常な状態に戻ります。

## <a name="am-i-responsible-for-the-availability-of-my-power-bi-solution"></a>自分の Power BI ソリューションの可用性に対して、自分に責任がありますか。

組織で使用される Power BI ソリューションに次の要素のいずれかが含まれている場合は、ソリューションの高可用性が保たれていることを保証するために何らかの対応が必要です。

- 組織で Power BI Premium が使用されている場合は、デプロイの負荷需要を満たすために Premium 容量のサイズが設定されていることを確認する必要があります。  [Power BI Premium の計画と展開に関するホワイトペーパー](https://aka.ms/Premium-Capacity-Planning-Deployment)、および [Power BI Premium 容量メトリック アプリ](service-admin-premium-monitor-capacity.md)に関するページは、計画とこの要件を満たすのに役立つ場合があります。 Power BI の管理ポータルとメトリック アプリには、役立つ新しい機能が定期的に追加されています。
- 組織でオンプレミス データ ゲートウェイを使用してオンプレミスのデータ ソースにアクセスする場合は、高可用性をサポートするために、[この記事の説明に従って](/data-integration/gateway/service-gateway-high-availability-clusters)ゲートウェイを設定する必要があります。 インポート モードでレポートを更新するか、DirectQuery または Live Connect を使用してデータまたはデータ モデルにアクセスするかに関係なく、このガイダンスに従ってください。

## <a name="will-gateways-function-when-in-failover-mode"></a>フェールオーバー モードの場合、ゲートウェイは機能しますか。

いいえ。 オンプレミス データ ソースで必要なデータ (直接クエリと Live Connect に基づくすべてのレポートとダッシュボード) は、フェールオーバー中には機能しません。 しかし、ゲートウェイの構成は変更されません。 Power BI インスタンスが元の状態に戻ると、ゲートウェイは正常な機能に戻ります。

プライマリ リージョンで深刻な障害が発生し、長時間にわたってオンラインに戻すことができなくなった場合、フェールオーバーされたプライマリ リージョンでは、読み取りと書き込みの両方が操作可能となり、お客様は新しいリージョンに対してゲートウェイを再デプロイして構成することができるようになります。

お客様は、新しいゲートウェイを別のコンピューターにインストールするか、既存のゲートウェイを引き継ぐことができます。 古いゲートウェイに関連付けられているすべてのデータソースが新しいゲートウェイに引き継がれるため、既存のゲートウェイを使用する方が簡単です。
