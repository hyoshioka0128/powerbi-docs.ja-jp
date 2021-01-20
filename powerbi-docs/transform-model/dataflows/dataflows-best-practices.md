---
title: データフローのベスト プラクティス
description: データフローのベスト プラクティス リンクとガイダンスのコレクション
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-dataflows
ms.topic: how-to
ms.date: 12/10/2020
LocalizationGroup: Data from files
ms.openlocfilehash: fb688b20fd8b5ee1288f670fba9f7f45fc058680
ms.sourcegitcommit: 1cad78595cca1175b82c04458803764ac36e5e37
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2021
ms.locfileid: "98565368"
---
# <a name="dataflows-best-practices"></a>データフローのベスト プラクティス

Power BI **データフロー** はエンタープライズに重点を置いたデータ準備ソリューションであり、使用、再利用、統合の準備が整ったデータのエコシステムを可能にします。 この記事では、ベスト プラクティスの一覧と、データフローを理解し、最大限に活用するために役立つ記事やその他の情報へのリンクを提供します。

## <a name="dataflows-across-the-power-platform"></a>Power Platform 全体のデータフロー

データフローは、Power Query、Microsoft Dynamics 365 やその他の Microsoft オファリングなど、さまざまな Power Platform テクノロジ全体で使用することができます。 データフローが Power Platform 全体でどのように動作するかの詳細については、[Microsoft 製品全体でのデータフローの使用](/power-query/dataflows/overview-dataflows-across-power-platform-dynamics-365)に関する記事を参照してください。


## <a name="dataflows-best-practices-table-and-links"></a>データフローのベスト プラクティスの表とリンク

次の表には、データフローの作成または作業時のベスト プラクティスについて説明する記事へのリンクがまとめてあります。 リンクには、ビジネス ロジックの開発、複雑なデータフローの開発、データフローの再利用、データフローで企業規模を達成する方法に関する情報が含まれています。


|**トピック**  |**ガイダンス領域**  |**記事またはコンテンツへのリンク**  |
|---------|---------|---------|
|Power Query     | データ ラングリング経験を最大限に活用するためのヒントとテクニック        |[Power Query のベスト プラクティス](/power-query/best-practices)        |
|計算されたエンティティを活用する     |計算されたエンティティをデータフローで使用することには、パフォーマンス上の利点があります。         |[計算されたエンティティのシナリオ](/power-query/dataflows/computed-entities-scenarios)         |
|複雑なデータフローの開発     |大規模でパフォーマンスの高いデータフローを開発するためのパターン         |[複雑なデータフロー](/power-query/dataflows/best-practices-developing-complex-dataflows)         |
|データフローの再利用     |パターン、ガイダンス、ユースケース         |[データフローの再利用](/power-query/dataflows/best-practices-reusing-dataflows)         |
|大規模な実装     |大規模な使用と、エンタープライズ アーキテクチャを補完するガイダンス         |[データフローを使用したデータ ウェアハウス](/power-query/dataflows/best-practices-for-data-warehouse-using-dataflows)         |
|拡張コンピューティングの活用     |データフローのパフォーマンスが最大 25 倍になる可能性がある         |[拡張コンピューティング エンジン](dataflows-premium-workload-configuration.md#using-the-compute-engine-to-improve-performance)         |
|ワークロードの設定を最適化する     |パフォーマンスを最大化できる手段を理解することでデータフロー インフラストラクチャを最大限まで活用します         |[データフロー ワークロード構成](dataflows-premium-workload-configuration.md)         |
|テーブルの結合と拡張     |パフォーマンスの高い結合の作成         |[テーブル拡張操作の最適化](/power-query/optimize-expanding-table-columns)         |
|クエリ フォールディングのガイダンス     |ソース システムを使用した変換の高速化         |[クエリ フォールディング](/power-query/power-query-folding)         |
|データ プロファイルの使用     |列の品質、分布、プロファイルを理解する         |[データ プロファイリング ツール](/power-query/data-profiling-tools)         |
|エラー処理の実装     |修正候補を提示し、更新エラーからの回復性がある堅牢なデータフローを開発する         |[一般的なエラーのパターン](/power-query/dealing-with-errors)  </br> [複雑なエラー処理](/power-query/error-handling)      |
|スキーマ ビューの使用      |幅の広いテーブルを使用するとき、また、スキーマ レベル操作を行うとき、作成エクスペリエンスを向上する         |[スキーマ ビュー](/power-query/schema-view)         |
|リンクされたエンティティ      |変換の再利用と参照         |[リンクされたエンティティ](/power-query/dataflows/linked-entities)         |
|増分更新      |最新または変更されたデータの読み込み、および完全な再読み込み         |[増分更新](/power-query/dataflows/incremental-refresh)         |
|||


        
## <a name="next-steps"></a>次のステップ

データフローと Power BI の詳細については、以下の記事を参照してください。

* [データフローとセルフサービスのデータ準備の概要](dataflows-introduction-self-service.md)
* [データフローの作成](dataflows-create.md)
* [データフローの構成と使用](dataflows-configure-consume.md)
* [データフローの Premium 機能](dataflows-premium-features.md)
* [Azure Data Lake Gen 2 を使用するようにデータフロー ストレージを構成する](dataflows-azure-data-lake-storage-integration.md)
* [データフローを使用した AI](dataflows-machine-learning-integration.md)
* [データフローの制限事項と考慮事項](dataflows-features-limitations.md)