---
title: インポート、ライブ接続、直接クエリで自然言語を使用する
description: この記事では、Power BI で使用できるさまざまな種類のデータ ソースと Q&A 機能が連動するしくみについて説明します。 また、インデックス作成とキャッシュの概念についても説明します。
author: mohaali
ms.author: mohaali
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 08/19/2020
ms.openlocfilehash: 23ecc8edd82f6c1694c850f73fef2a892230ff14
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418971"
---
# <a name="use-natural-language-with-import-live-connect-and-direct-query"></a>インポート、ライブ接続、直接クエリで自然言語を使用する

Power BI の Q&A 機能によって、ご自分のデータから回答をすばやく取得することができますが、その方法は自然言語を利用してそのデータに関する質問をするというものです。 この記事では、インデックス作成とキャッシュを使用し、サポートされている構成別にパフォーマンスを改善する方法について説明します。

## <a name="what-data-sources-are-supported-in-qa"></a>Q&A でサポートされるデータ ソース

Q&A は、次の構成でサポートされています。

- インポート モード
- ライブ接続モード – オンプレミス SQL Server Analysis Services、Azure Analysis Services、Power BI データセットを使用
- 直接クエリ – Azure Synapse、Azure SQL、SQL Server 2019。 他のソースが直接クエリモードで動作する場合がありますが、そのようなソースは正式にはサポートされていません。

既定では、Q&A ビジュアルを使用する場合、レポート内で Q&A が有効になります。 直接クエリまたはライブ接続を使用している場合、プロンプトが表示されます。 オプションに進むことで、レポートの自然言語機能のオンとオフを明示的に切り替えることができます。

![Q&A デスクトップ オプション](media/qna-desktop-options.png)

詳細については、「[Power BI Q&A の制限事項](q-and-a-limitations.md)」を参照してください。

## <a name="how-does-indexing-work-with-qa"></a>インデックス作成と Q&A が連動するしくみ

Q&A を有効にすると、ユーザーにリアルタイム フィードバックをすばやく提供し、ユーザーの質問の解釈を支援する目的でインデックスが作成されます。 インデックスは作成に時間がかかることがあり、次の要素と制限があります。

- Q&A ツール内で明示的にオフにされていない限り、列名とテーブルはすべて、インデックスに挿入されます。
- 100 文字未満のテキスト値はすべてインデックス化されます。 100 文字より多いテキスト値はすべてインデックス化されません。 
- Q&A ではそのインデックスに最大 500 万個の一意の値が格納されます。 このしきい値を超える場合、Q&A から受け取る結果の精度を下げる可能性がある値はすべて、インデックスで保持されません。
- インデックス作成中にエラーが発生した場合、インデックスは部分的な状態になり、次のセクションで説明するように、次回の更新で再作成されます。

## <a name="how-often-is-the-index-refreshed-and-cached"></a>インデックスが更新およびキャッシュされる頻度

Power BI Desktop では、Q&A が使用されるときにインデックスが作成されます。 小さいアイコンが表示され、インデックスが作成中であることがわかります。 この間、提案を含め、Q&A ビジュアルの読み込みに時間がかかることがあります。

Power BI サービスによって、発行と再発行時および更新時にインデックスが再作成されます。 Q&A インデックスは常に自動作成されるとは限りません。データセット更新を最適化するため、オンデマンド基準になることがあります。 直接クエリの場合、直接クエリ ソースへの影響を減らすため、データのインデックス作成は多くても 1 日 1 回にしています。

## <a name="next-steps"></a>次の手順

自然言語は、自分のレポートにさまざまな方法で統合できます。 詳細については、次の記事を参照してください。

* [Q&A ビジュアル](../visuals/power-bi-visualization-q-and-a.md)
* [Q&A ベスト プラクティス](q-and-a-best-practices.md)
