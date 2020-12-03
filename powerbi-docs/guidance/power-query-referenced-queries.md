---
title: Power Query クエリの参照
description: Power Query クエリを参照するためのガイダンス。
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 11/30/2019
ms.openlocfilehash: f7756c53799838182be9288f297c0d01a7c6cca3
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96419293"
---
# <a name="referencing-power-query-queries"></a>Power Query クエリの参照

この記事は、Power BI Desktop を操作するデータ モデラーを対象としています。 他のクエリを参照する Power Query クエリを定義する際のガイダンスを示します。

次の文が何を意味してるかを十分に理解しましょう。"_あるクエリで 2 つ目のクエリが参照されるとき、2 つ目のクエリの手順は最初のクエリと結合されているかのように扱われ、最初のクエリの手順が実行される前に実行されます。_ "

いくつかのクエリを検討します。**Query1** のデータ ソースは Web サービスであり、その読み込みは無効にななっています。 **Query2**、**Query3**、**Query4** は、すべて **Query1** を参照しており、それらの出力がデータ モデルに読み込まれます。

![前の段落で説明したクエリが表示されている、クエリの依存関係ビューを示す図。](media/power-query-referenced-queries/query-dependencies-web-service.png)

このデータ モデルが更新されるとき、Power Query によって **Query1** の結果が取得され、それを参照しているクエリで再利用されるものと思うことがよくあります。 この考え方は正しくありません。 実際には、Power Query では、**Query2**、**Query3**、および **Query4** は個別に実行されます。

**Query2** には、**Query1** の手順が埋め込まれていると考えることができます。 同じことが、**Query3** と **Query4** にも当てはまります。 次の図は、クエリがどのように実行されるかをより明確に示しています。

![Query2、Query3、および Query4 が表示されている、クエリの依存関係ビューの変更バージョンを示す図。](media/power-query-referenced-queries/query-dependencies-web-service-concept.png)

**Query1** は 3 回実行されます。 複数の実行によってデータ更新が低速になり、データ ソースに悪影響を及ぼす可能性があります。

**Query1** で [Table.Buffer](/powerquery-m/table-buffer) 関数を使用しても、追加のデータ取得が排除されることはありません。 この関数は、テーブルをメモリにバッファー処理します。 そして、バッファー処理されたテーブルは、同じクエリの実行内でのみ使用できます。 したがって、この例では、**Query2** の実行時に **Query1** がバッファー処理された場合でも、**Query3** と **Query4** の実行時にバッファー処理されたデータを使用することはできません。 各自でバッファー処理が実行されるため、データは、さらに 2 回バッファー処理されます (テーブルが参照元のクエリによって個別にバッファー処理されるため、パフォーマンスへの悪影響が増加する可能性があります)。

> [!NOTE]
> Power Query のキャッシュ アーキテクチャは複雑であり、それはこの記事の焦点ではありません。 Power Query では、データ ソースから取得したデータをキャッシュできます。 ただし、クエリの実行時に、データ ソースからデータを複数回取得する場合があります。

## <a name="recommendations"></a>推奨事項

通常は、クエリ間でのロジックの重複を回避するようにクエリを参照することが推奨されています。 ただし、この記事で説明したように、この設計方法では、データ更新の速度が低下し、データ ソースに過度の負荷がかかる可能性があります。

代わりに、[データフロー](../transform-model/dataflows/dataflows-introduction-self-service.md)を作成することをお勧めします。 データフローを使用すると、データ更新時間が短縮され、データ ソースへの影響が軽減されます。

ソース データと変換をカプセル化するようにデータフローを設計できます。 データフローは Power BI サービス内に保持されるデータ ストアであるため、データは高速で取得されます。 そのため、クエリの参照でデータフローに対する要求が複数回発生した場合でも、データ更新時間を短縮することができます。

この例では、**Query1** をデータフロー エンティティとして再設計すれば、**Query2**、**Query3**、および **Query4** でそれをデータ ソースとして使用できます。 この設計では、**Query1** をソースとするエンティティの評価は、1 回だけ実行されます。

## <a name="next-steps"></a>次の手順

この記事に関する詳細については、次のリソースを参照してください。

- [Power BI でのセルフサービスのデータ準備](../transform-model/dataflows/dataflows-introduction-self-service.md)
- [Power BI でのデータフローの作成と使用](../transform-model/dataflows/dataflows-create.md)
- わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
- Power BI チームへのご提案は、 [Power BI を改善するためのアイデアをお寄せください](https://ideas.powerbi.com/)