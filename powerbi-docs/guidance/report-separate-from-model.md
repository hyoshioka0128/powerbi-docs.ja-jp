---
title: Power BI Desktop のモデルからレポートを分離する
description: Power BI Desktop のモデルからレポートを分離するためのガイダンスです。
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 04/11/2020
ms.openlocfilehash: 20e674765d2a908ff1952b0f316d125d0e3c5bd3
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2021
ms.locfileid: "99088306"
---
# <a name="separate-reports-from-models-in-power-bi-desktop"></a>Power BI Desktop のモデルからレポートを分離する

新しい Power BI Desktop ソリューションを作成する場合に、最初に行う必要がある作業の 1 つが "データの取得" です。 データを取得すると、2 つのまったく異なる結果が得られる可能性があります。 次のとおりです。

- 既に発行されているモデル (Power BI のデータセットまたはリモートでホストされる Analysis Services のモデルである可能性があります) への[ライブ接続](../connect-data/desktop-report-lifecycle-datasets.md) が作成されます。
- 新しいモデルの開発が開始されます。これは、インポート、DirectQuery、複合モデルのいずれかになります。

この記事では、2 番目のシナリオについて説明します。 レポートとモデルを 1 つの Power BI Desktop ファイルに結合する必要があるかどうかについてのガイダンスを提供します。

## <a name="single-file-solution"></a>単一ファイルのソリューション

"_単一ファイルのソリューション_" は、モデルに基づくレポートが 1 つしかない場合に適しています。 この場合、モデルとレポートの両方が同じユーザーの作業であると思われます。 レポートを他のユーザーと共有することもできますが、ここでは "_個人 BI_" ソリューションとして定義します。 このようなソリューションでは、ロール スコープのレポートまたはビジネス チャレンジの 1 回限りの評価を表すことができます。これは、多くの場合 "_アド ホック_" レポートとして記述されます。

:::image type="content" source="media/report-separate-from-model/single-file-solution.png" alt-text="1 つのファイルには、同じユーザーによって開発されたモデルとレポートが含まれています。" border="true":::

## <a name="separate-report-files"></a>レポート ファイルを分離する

次の場合には、モデルとレポートの開発を別々の Power BI Desktop ファイルに分割する方が理にかなっています。

- データ モデルの作成者とレポートの作成者が異なる。
- 現在、または将来、モデルが複数のレポートのソースになることがわかっている。

:::image type="content" source="media/report-separate-from-model/separate-report-files.png" alt-text="3 つの PBIX ファイルがあります。1 つ目には、モデルのみが含まれます。他の 2 つにはレポートのみが含まれ、Power BI サービスでホストされているモデルにライブ接続します。レポートは、さまざまなユーザーによって開発されています。" border="true":::

データ モデルの作成者は、引き続き Power BI Desktop のレポート作成エクスペリエンスを使用して、モデル設計をテストおよび検証できます。 ただし、ファイルを Power BI サービスに発行した直後に、ワークスペースからレポートを削除する必要があります。 また、データセットを再発行して上書きするたびに、レポートを削除しておく必要があります。

### <a name="preserve-the-model-interface"></a>モデルのインターフェイスを保持する

モデルの変更が避けられないこともあります。 データ モデルの作成者はモデルのインターフェイスが壊れないように注意を払う必要があります。 そうしないと、関連するレポートのビジュアルまたはダッシュボードのタイルが壊れる可能性があります。 壊れたビジュアルはエラーとして表示され、レポートの作成者やコンシューマーのストレスになる可能性があります。 さらに悪いことに、データの信頼性が低下する可能性があります。

そのため、モデルの変更は慎重に管理してください。 可能であれば、次の変更は避けてください。

- テーブル、列、階層、階層レベル、またはメジャーの名前を変更する。
- 列のデータ型を変更する。
- 異なるデータ型を返すように、メジャー式を変更する。
- メジャーを別のホーム テーブルに移動する。 これは、メジャーを移動すると、メジャーがホーム テーブル名で完全修飾されたレポートスコープのメジャーが壊れる可能性があるためです。 完全修飾メジャー名を使用して DAX 式を記述することはお勧めしません。 詳細については、「[DAX: 列参照とメジャー参照](dax-column-measure-references.md)」を参照してください。

新しいテーブル、列、階層、階層レベル、メジャーの追加は安全ですが、1 つ例外があります。新しいメジャー名がレポートスコープのメジャー名と競合する可能性があります。 競合を回避するには、レポートにメジャーを定義するときに、レポート作成者が名前付け規則を採用することをお勧めします。 レポートスコープのメジャー名の前にはアンダースコアまたはその他の文字を付けることができます。

モデルに破壊的変更を加える必要がある場合は、次のいずれかの方法をお勧めします。

- Power BI サービスで[データセットに関連するコンテンツを表示する](../consumer/end-user-related.md)。
- Power BI サービスの[データ系列](../collaborate-share/service-data-lineage.md)ビューを調べる。

どちらのオプションを使用しても、関連するレポートとダッシュボードをすばやく識別できます。 データ系列ビューの方が、関連する各成果物の担当者を簡単に確認できるので、より適しています。 実際に、担当者宛ての電子メール メッセージが開くハイパーリンクがあります。

関連する各成果物の所有者に連絡して、破壊的変更の予定を通知することをお勧めします。 こうすることで、レポートを修正して再発行する準備ができ、ダウンタイムとストレスを最小限に抑えることができます。

## <a name="next-steps"></a>次の手順

この記事に関する詳細については、次のリソースを参照してください。

- [Power BI Desktop から Power BI サービスのデータセットに接続する](../connect-data/desktop-report-lifecycle-datasets.md)
- [Power BI サービスで関連するコンテンツを表示する](../consumer/end-user-related.md)
- [Data lineage (データ系列)](../collaborate-share/service-data-lineage.md)
- わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
- Power BI チームへのご提案は、 [Power BI を改善するためのアイデアをお寄せください](https://ideas.powerbi.com/)
