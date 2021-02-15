---
title: Power BI 埋め込み分析の一部として説明される Power BI Embedded Generation 2
description: Power BI 埋め込み分析の Power BI Embedded Generation 2 オファリングについて説明します。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: overview
ms.date: 02/03/2021
ms.openlocfilehash: fa72ab380cac1a1ac6d12cb431bdacfb5964ee83
ms.sourcegitcommit: c33e53e1fab1f29872297524a7b4f5af6c806798
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2021
ms.locfileid: "99539644"
---
# <a name="power-bi-embedded-generation-2-preview"></a>Power BI Embedded Generation 2 (プレビュー)

Power BI Embedded では最近、Power BI Embedded の新しいバージョンである **Power BI Embedded Generation 2** がリリースされました。これは便宜上 **Embedded Gen2** と呼ばれています。 Embedded Gen2 は現在プレビュー段階であり、プレビュー期間中 Embedded サブスクライバーが使用できます。 引き続き Power BI Embedded リソースの元のバージョン (*Embedded Gen 1* と呼ばれます) を作成することも、新しい *Embedded Gen 2* リソースを作成することもできます。 プレビュー期間中は、両方の種類の Power BI Embedded 容量を並行して実行し、任意のワークスペースを Gen1、Gen2 のいずれかの容量に割り当てることができます"。

容量の一時停止や再開などの Power BI Embedded Gen 1 の機能はすべて、Gen 2 でも保持されます。 さらに、Gen 2 容量リソースでは、次の更新と改善されたエクスペリエンスが提供されます。

* **強化されたパフォーマンス** - いつでも、どの容量サイズでもパフォーマンスが向上します。 操作は常に最高速度で実行され、容量に対する負荷が容量の上限に近づいても、速度が低下しません。

* **スケーリングの向上** - 次の機能強化が含まれます。

    * "*更新コンカレンシーに制限なし*" - 容量に対して更新されるデータセットのスケジュールを追跡する必要がなくなりました

    * *メモリ制限の緩和*

    * *レポートの操作とスケジュールされた更新の完全な分離*

* **ページ分割されたレポートと AI ワークロードのエントリ レベルの低下** – *A1* SKU から開始し、必要に応じて拡張します。

* **リソースをすぐにスケーリングする** - Power BI Embedded リソースをすぐにスケーリングできます。 Gen1 リソースを数分でスケーリングし、Gen2 リソースを数秒でスケーリングできます。

* **ダウンタイムなしでのスケーリング** - Embedded Gen2 を使用すると、ダウンタイムなしで Power BI Embedded リソースをスケーリングできます。

* **メトリックの改善** - クリアかつ正規化された容量使用率データが含まれ、容量で実行される分析操作の複雑さのみに依存します。 メトリックは、容量のサイズや、分析実行中のシステムに対する負荷のレベルなど、他の要因の影響を受けません。 改善されたメトリックを使用すると、組み込みのレポート ツールによって次のことを明確に表示できます。
    * 使用率分析
    * 予算計画
    * 配賦
    * 容量をアップグレードする必要性

    >[!NOTE]
    >改善されたメトリックはその後、プレビュー期間中に使用できるようになります。 過去 7 日間の使用率メトリックへのアクセスを希望するお客様は、カスタマー サポートにお問い合わせください。

## <a name="using-embedded-gen2"></a>Embedded Gen2 の使用

Embedded Gen2 容量リソースを作成して、その更新内容を活用します。 Embedded Gen2 容量リソースを作成するには、「[Azure portal での Power BI Embedded 容量の作成](azure-pbie-create-capacity.md)」に記載されている手順に従います。

## <a name="known-limitations"></a>既知の制限事項

* Embedded Gen2 容量の使用率を[メトリック アプリ](../../admin/service-admin-premium-monitor-capacity.md)で追跡することはできません。 詳細については、[Premium Gen2 の監視の更新](../../admin/service-premium-what-is.md#updates-for-premium-gen2-preview-2)に関する記事を参照してください。

* 特定のワークロードに対するメモリ割り当ての設定が Embedded Gen2 容量に適用されません。 詳細については、[Embedded Gen 2 メモリの機能強化](embedded-capacity.md#embedded-gen-2-memory-enhancements-preview)に関する記事を参照してください

* Embedded Gen2 で XMLA を使用する場合は、最新バージョンのデータ モデリングおよび管理ツールを使用するようにしてください。

* Embedded Gen2 の Analysis Services の機能は、最新のクライアント ライブラリでのみサポートされています。 この要件をサポートするための依存ツールのリリース予定日は、「[Premium Gen2 の既知の制限](../../admin/service-premium-what-is.md#known-limitations-in-premium-gen2)」に記載されています。

* 現在のすべての Power BI Embedded 用 Azure メトリックおよびログ診断では、Gen1 容量のみがサポートされています。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [Azure Portal での Power BI Embedded 容量の作成](azure-pbie-create-capacity.md)

> [!div class="nextstepaction"]
> [Power BI Embedded の分析の容量と SKU](embedded-capacity.md)

> [!div class="nextstepaction"]
> [Power BI Premium とは](../../admin/service-premium-what-is.md)

> [!div class="nextstepaction"]
>[顧客向けに埋め込む](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[組織向けの埋め込み](embed-sample-for-your-organization.md)