---
title: Azure と Power BI
description: Azure と Power BI を使用して、自分で処理したデータを、自分のビジネスをリアルタイムで分析できる分析やレポートに変える方法について説明します。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 05/08/2019
LocalizationGroup: Data from databases
ms.openlocfilehash: 024f3f3b37555a45b1c0d216b0de4f29d65da2bc
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96403607"
---
# <a name="azure-and-power-bi"></a>Azure と Power BI

**Azure** サービスと **Power BI** を併用すると、データ処理の労力を、ビジネスにリアルタイムの洞察を与える分析やレポートに変えることができます。 データ処理がクラウド ベースかオンプレミスか、簡単か複雑か、ソースが 1 つか膨大なスケールか、あるいはウェアハウスに保存されたデータかリアルタイムのデータかに関わらず、Azure と Power BI には相互接続が組み込まれていて統合されているので、ビジネス インテリジェンス作業の効率が高まります。

![アジュール](media/service-azure-and-power-bi/azure_1.png)

Power BI では多数の Azure との接続を利用でき、それらのサービスを使用してユーザーのビジネスにとって一意なビジネス インテリジェンス ソリューションを作成できます。 1 つまたは少数の Azure データ ソースに接続し、そのデータを成形して調整することによって、カスタマイズ レポートを作成できます。

## <a name="azure-sql-database-and-power-bi"></a>Azure SQL Database と Power BI

最初に、Azure SQL Database に対する簡単な接続を確立し、ビジネスの進捗状況を監視するレポートを作成できます。 [Power BI Desktop](../fundamentals/desktop-getting-started.md) を使用すると、ビジネスを促進する傾向や主要業績評価指標を特定するレポートを作成することが可能です。

![PBI への SQL](media/service-azure-and-power-bi/azure_2_sqltopbi.png)

[Azure SQL Database](https://azure.microsoft.com/services/sql-database/) の詳細についてはこちらをご覧ください。

## <a name="transform-shape-and-merge-your-cloud-data"></a>クラウド データの変換、成形、マージ

複雑なデータや、各種ソースのデータがありますか。 問題はありません。 **Power BI Desktop** と Azure サービスを併用すると、 **[データ取り出し]** ダイアログをタップするだけで接続できます。 同じクエリ内で、**Azure SQL Database**、**Azure HDInsight** データ ソース、**Azure BLOB ストレージ** (または **Azure テーブル ストレージ**) に接続してから、必要なそれぞれのサブセットのみを選択し調整していくことができます。

同じデータ接続を使用して、さらには同じクエリを使用しても、異なる対象ユーザーに別個のレポートを作成できます。 新しいレポート ページを作成し、それぞれの対象ユーザー向けに視覚エフェクトを調整し、ビジネスが情報に通じているように監視するだけです。

![PBI への複数処理](media/service-azure-and-power-bi/azure_3_multipletopbi.png)

詳細については、次のリソースを参照してください。

* [Azure SQL Database](https://azure.microsoft.com/services/sql-database/)
* [Azure HDInsight](https://azure.microsoft.com/services/hdinsight/)
* [Azure Storage](https://azure.microsoft.com/services/storage/) (BLOB ストレージおよびテーブル ストレージ)

## <a name="get-complex-and-ahead-using-azure-services-and-power-bi"></a>Azure サービスおよび Power BI による各種融合と成長

Azure と Power BI を使用して必要な限りの拡張を行えます。 複数のソース データ処理の活用、大規模なリアルタイム システムの使用、[Stream Analytics](https://azure.microsoft.com/services/stream-analytics/) と [Event Hubs](https://azure.microsoft.com/services/event-hubs/) の使用、ビジネスで優位性を与えるビジネス インテリジェンス レポートと各種 SaaS サービスとの融合を行います。

![Azure 複合](media/service-azure-and-power-bi/azure_4_complex.png)

## <a name="context-insights-with-power-bi-embedded-analytics"></a>Power BI Embedded アナリティクスによるコンテキストの分析情報

魅力的でインタラクティブなデータ視覚化を、アプリケーション、Web サイト、ポータル、などに埋め込むことで、ビジネス データを活用できます。 [Azure のリソースとして Power BI Embedded を使用すると](https://azure.microsoft.com/services/power-bi-embedded/)、インタラクティブなレポートやダッシュボードを簡単に埋め込むことができるため、ユーザーはデバイスの種類にかかわらず一貫した再現性に優れた製品体験を楽しむことができます。  分析を埋め込んで Power BI を使用することで、データからナレッジ、分析情報、行動へと、体験を進めることができます。  さらに、[社内のアプリケーションやポータルに](https://powerbi.microsoft.com/developers/embedded-analytics/organization/)分析を埋め込むことで、Power BI Azure をさらに活用できるようになります。

[Power BI デベロッパー ポータル](https://dev.powerbi.com)には、Power BI API に関する詳細が示されています。

詳細については、「[Azure の Power BI Embedded とは何か](../developer/embedded/azure-pbie-what-is-power-bi-embedded.md)」を参照してください。

## <a name="embed-your-power-bi-data-within-your-app"></a>アプリ内に Power BI データを埋め込む

魅力的でインタラクティブなデータ視覚化を、アプリケーション、Web サイト、ポータルなどに埋め込むことによって、ビジネス データをコンテキストと共に表示することができます。 [Azure の Power BI Embedded](https://azure.microsoft.com/services/power-bi-embedded/) を使用すると、インタラクティブなレポートやダッシュボードを簡単に埋め込むことができるため、ユーザーはデバイスの種類にかかわらず一貫した再現性に優れた製品体験を楽しむことができます。

## <a name="what-could-you-do-with-azure-and-power-bi"></a>Azure と Power BI を併用して何ができますか。

**Azure** と **Power BI** を組み合わせて行えるシナリオはたくさんあります - 可能性とチャンスはビジネスによって異なります。 **Azure サービス** について詳しくは、こちらの [概要ページ](/azure/machine-learning/team-data-science-process/plan-your-environment)をご確認ください。**Azure を使用したデータ分析シナリオ**、およびお持ちのデータ ソースをビジネスをさらに成長させるインテリジェンスに変換する方法が取り上げられています。