---
title: データフローのベスト プラクティス
description: データフローのベスト プラクティス リンクとガイダンスのコレクション
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 11/13/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 5adfcc3d4ff7d78335f250b92b856bcd14d64c0a
ms.sourcegitcommit: bd133cb1fcbf4f6f89066165ce065b8df2b47664
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94674745"
---
# <a name="dataflows-best-practices"></a>データフローのベスト プラクティス

Power BI **データフロー** はエンタープライズに重点を置いたデータ準備ソリューションであり、使用、再利用、統合の準備が整ったデータのエコシステムを可能にします。 この記事では、ベスト プラクティスの一覧と、データフローを理解し、最大限に活用するために役立つ記事やその他の情報へのリンクを提供します。


## <a name="dataflows-best-practices-table-and-links"></a>データフローのベスト プラクティスの表とリンク

次の表には、データフローの作成または作業時のベスト プラクティスについて説明する記事へのリンクがまとめてあります。 リンクには、ビジネス ロジックの開発、複雑なデータフローの開発、データフローの再利用、データフローで企業規模を達成する方法に関する情報が含まれています。


|**トピック**  |**ガイダンス領域**  |**記事またはコンテンツへのリンク**  |
|---------|---------|---------|
|Power Query     | データ ラングリング経験を最大限に活用するためのヒントとテクニック        |[Power Query のベスト プラクティス](https://docs.microsoft.com/power-query/best-practices)        |
|計算されたエンティティを活用する     |計算されたエンティティをデータフローで使用することには、パフォーマンス上の利点があります。         |[コンピューティング エンティティのシナリオ](https://docs.microsoft.com/power-query/dataflows/computed-entities-scenarios)         |
|複雑なデータフローの開発     |大規模でパフォーマンスの高いデータフローを開発するためのパターン         |[複雑なデータフロー](https://docs.microsoft.com/power-query/dataflows/best-practices-developing-complex-dataflows)         |
|データフローの再利用     |パターン、ガイダンス、ユースケース         |[データフローの再利用](https://docs.microsoft.com/power-query/dataflows/best-practices-reusing-dataflows)         |
|大規模な実装     |大規模な使用と、エンタープライズ アーキテクチャを補完するガイダンス         |[データフローを使用したデータ ウェアハウス](https://docs.microsoft.com/power-query/dataflows/best-practices-for-data-warehouse-using-dataflows)         |
|拡張コンピューティングの活用     |データフローのパフォーマンスが最大 25 倍になる可能性がある         |[拡張コンピューティング エンジン](dataflows-premium-workload-configuration.md#using-the-compute-engine-to-improve-performance)         |
|ワークロードの設定を最適化する     |パフォーマンスを最大化できる手段を理解することでデータフロー インフラストラクチャを最大限まで活用します         |[データフロー ワークロード構成](dataflows-premium-workload-configuration.md)         |
|テーブルの結合と拡張     |パフォーマンスの高い結合の作成         |[テーブル拡張操作の最適化](https://docs.microsoft.com/power-query/optimize-expanding-table-columns)         |
|クエリ フォールディングのガイダンス     |ソース システムを使用した変換の高速化         |[クエリ フォールディング](https://docs.microsoft.com/power-query/power-query-folding)         |
|データ プロファイルの使用     |列の品質、分布、プロファイルを理解する         |[データ プロファイリング ツール](https://docs.microsoft.com/power-query/data-profiling-tools)         |
|エラー処理の実装     |修正候補を提示し、更新エラーからの回復性がある堅牢なデータフローを開発する         |[一般的なエラーのパターン](https://docs.microsoft.com/power-query/dealing-with-errors)  </br> [複雑なエラー処理](https://docs.microsoft.com/power-query/error-handling)      |
|スキーマ ビューの使用      |幅の広いテーブルを使用するとき、また、スキーマ レベル操作を行うとき、作成エクスペリエンスを向上する         |[スキーマ ビュー](https://docs.microsoft.com/power-query/schema-view)         |
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