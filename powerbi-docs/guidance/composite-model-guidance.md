---
title: Power BI Desktop の複合モデルのガイダンス
description: 複合モデルの開発に関するガイダンス。
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 12/24/2019
ms.openlocfilehash: 8dab2829b9b59e065e241b9d28d2d66a9f050706
ms.sourcegitcommit: 13a150d1aa810f309421bf603fa8581718a4b299
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "101842655"
---
# <a name="composite-model-guidance-in-power-bi-desktop"></a>Power BI Desktop の複合モデルのガイダンス

この記事は、Power BI の複合モデルを開発するデータ モデラーを対象としています。 複合モデルのユース ケースについて説明し、設計ガイダンスを提供します。 具体的には、ご自分のソリューションに複合モデルが適切かどうかを判断するためのガイダンスです。 該当する場合、この記事は最適なモデルの設計にも役立ちます。

> [!NOTE]
> この記事では、複合モデルの概要については説明しません。 複合モデルをよく理解していない場合は、まず「[Power BI Desktop で複合モデルを使用する](../transform-model/desktop-composite-models.md)」の記事を読むことをお勧めします。
>
> 複合モデルは少なくとも 1 つの DirectQuery ソースで構成されるため、[モデルのリレーションシップ](../transform-model/desktop-relationships-understand.md)、[DirectQuery モデル](../connect-data/desktop-directquery-about.md)、および [DirectQuery モデルの設計ガイダンス](directquery-model-guidance.md)をよく理解していることも重要です。

## <a name="composite-model-use-cases"></a>複合モデルのユース ケース

可能な限り、インポート モードでモデルを開発することをお勧めします。 このモードを使うと、最大限のデザインの柔軟性と最高のパフォーマンスが得られます。

ただし、大量のデータに関連する課題や、ほぼリアルタイムのデータに関するレポートは、インポート モデルでは解決できません。 このいずれのケースでも、[DirectQuery モードでサポートされる](../connect-data/power-bi-data-sources.md)単一のデータ ソースにデータが格納されている場合は、DirectQuery モデルを検討できます。

さらに、次の状況で複合モデルの開発を検討できます。

- モデルを DirectQuery モデルにすることもできますが、パフォーマンスを向上させる必要があります。 複合モデルでは、各テーブルに適切なストレージを構成することでパフォーマンスを改善できます。 [集計](../transform-model/desktop-aggregations.md)を追加することもできます。 これら両方の最適化について、この記事の後半で説明します。
- DirectQuery モデルと追加のデータを結合し、モデルにインポートする必要があります。 インポートされたデータは、別のデータ ソースまたは計算テーブルから読み込むことができます。
- 複数の DirectQuery データ ソースを 1 つのモデルに結合する必要があります。

> [!NOTE]
> 複合モデルでは、外部の分析データベースへの接続を組み合わせることはできません。 これに該当するものとしては、[外部でホストされるモデル](../connect-data/service-datasets-understand.md#external-hosted-models)、Power BI データセット、SAP Business Warehouse、および SAP HANA ([SAP HANA を多次元ソースとして扱う](../connect-data/desktop-directquery-sap-hana.md)場合) へのライブ接続があります。

## <a name="optimize-model-design"></a>モデルの設計を最適化する

複合モデルを最適化するには、テーブル [ストレージ モード](../transform-model/desktop-storage-mode.md)を構成し、[集計](../transform-model/desktop-aggregations.md)を追加します。

### <a name="table-storage-mode"></a>テーブル ストレージ モード

複合モデルでは、(計算テーブルを除く) 各テーブルのストレージ モードを構成できます。

- **DirectQuery**:大量のデータを示すテーブル、または準リアルタイムの結果を提供する必要があるテーブルの場合は、このモードを設定することをお勧めします。 データがこれらのテーブルにインポートされることはありません。 通常、これらのテーブルはファクト型テーブル (集計に使用されるテーブル) になります。
- **インポート**:ディメンション型テーブル (フィルター処理とグループ化に使用されるテーブル) の場合は、このモードを設定することをお勧めします。 実際のところ、DirectQuery モードでサポートされていないソースに基づくテーブルの場合、これが唯一の選択肢です。 計算テーブルは常にインポート テーブルです。
- **デュアル**:ディメンション型テーブルで、同じソースの DirectQuery ファクト型テーブルと共にクエリが実行される可能性がある場合は、このモードを設定することをお勧めします。

Power BI で複合モデルにクエリを実行する場合は、いくつかのシナリオが考えられます。

- **インポート テーブルまたはデュアル テーブルに対してのみクエリを実行する**:すべてのデータは、モデル キャッシュから取得されます。 可能な限り最速のパフォーマンスを達成できます。 このシナリオは、フィルターまたはスライサー ビジュアルによってクエリが行われるディメンション型テーブルの場合に一般的です。
- **同じソースのデュアル テーブルまたは DirectQuery テーブルに対してクエリを実行する**:1 つ以上のネイティブ クエリを DirectQuery ソースに送信することで、すべてのデータを取得します。 特にソース テーブルに適切なインデックスが存在する場合に、最速のパフォーマンスを達成できます。 このシナリオは、デュアル ディメンション型テーブルと DirectQuery ファクト型テーブルを関連付けるクエリの場合に一般的です。 これらのクエリは "_ソース グループ内_" なので、1 対 1 または 1 対多の関係はすべて [標準リレーションシップ](../transform-model/desktop-relationships-understand.md#regular-relationships)として評価されます。
- **他のすべてのクエリ**:これらのクエリには、ソース グループ間のリレーションシップが含まれます。 これは、インポート テーブルが DirectQuery テーブルと関係しているか、デュアル テーブルが異なるソースの DirectQuery テーブルと関係している (この場合はインポート テーブルとして動作します) ためです。 すべてのリレーションシップは[制限付きリレーションシップ](../transform-model/desktop-relationships-understand.md#limited-relationships)として評価されます。 また、非 DirectQuery テーブルに適用されるグループ化は、仮想テーブルとして DirectQuery ソースに送信される必要があることも意味します。 この場合、特に大規模なグループ化セットの場合、ネイティブ クエリは非効率的です。 また、ネイティブ クエリでは機密データが公開される可能性があります。

まとめると、推奨事項は次のとおりです。

- 複合モデルが適切なソリューションであることを慎重に検討します。異なるデータ ソースをモデルレベルで統合できますが、結果として設計が複雑になるという影響もあります
- テーブルが大量のデータを格納するファクト型テーブルである場合、または準リアルタイムの結果を提供する必要がある場合は、ストレージ モードを **DirectQuery** に設定します
- テーブルがディメンション型テーブルの場合は、ストレージ モードを **デュアル** に設定します。これにより、同じソースに基づく **DirectQuery** ファクト型テーブルと共にクエリが実行されます
- デュアル テーブル (および依存するすべての計算テーブル) のモデル キャッシュとソース データベースとの同期を維持するように、適切な更新頻度を構成します
- データ ソース (モデル キャッシュを含む) 間のデータの整合性を確保します。関連する列の値が一致しない場合は、制限付きリレーションシップによって行が削除されます
- 効率的な結合、フィルター処理、グループ化のために適切なインデックスを使用して DirectQuery データ ソースを最適化します
- ネイティブ クエリが傍受されるリスクがある場合は、機密データをインポート テーブルまたはデュアル テーブルに読み込まないでください。詳細については、「[Power BI Desktop で複合モデルを使用する (セキュリティへの影響)](../transform-model/desktop-composite-models.md#security-implications)」を参照してください。

### <a name="aggregations"></a>集計

複合モデルの DirectQuery テーブルには集計を追加できます。 集計はモデルにキャッシュされるので、インポート テーブルとして動作します (ただし、モデル テーブルのように使用することはできません)。 その目的は、"より高い粒度" のクエリのパフォーマンスを向上させることです。 詳しくは、「[Power BI Desktop での集計](../transform-model/desktop-aggregations.md)」をご覧ください。

次の基本的な規則に従う集計テーブルにすることをお勧めします。その行数は、基となるテーブルよりも少なくとも 10 倍小さくする必要があります。 たとえば、基となるテーブルに 10 億行が格納されている場合、集計テーブルは 1 億行を超えないようにします。 この規則により、集計テーブルの作成と保守のコストに対して適切なパフォーマンスの向上が保証されます。

## <a name="next-steps"></a>次の手順

この記事に関する詳細については、次のリソースを参照してください。

- [Power BI Desktop で複合モデルを使用する](../transform-model/desktop-composite-models.md)
- [Power BI Desktop でのモデル リレーションシップ](../transform-model/desktop-relationships-understand.md)
- [Power BI Desktop での DirectQuery モデル](../connect-data/desktop-directquery-about.md)
- [Power BI Desktop で DirectQuery を使用する](../connect-data/desktop-use-directquery.md)
- [Power BI Desktop での DirectQuery モデルのトラブルシューティング](../connect-data/desktop-directquery-troubleshoot.md)
- [Power BI データ ソース](../connect-data/power-bi-data-sources.md)
- [Power BI Desktop のストレージ モード](../transform-model/desktop-storage-mode.md)
- [Power BI Desktop での集計](../transform-model/desktop-aggregations.md)
- わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
- Power BI チームへのご提案は、 [Power BI を改善するためのアイデアをお寄せください](https://ideas.powerbi.com)
