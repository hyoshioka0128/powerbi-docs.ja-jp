---
title: データフローとセルフサービスのデータ準備の概要
description: Power BI データフローと使用するタイミングの概要
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-dataflows
ms.topic: how-to
ms.date: 10/01/2020
LocalizationGroup: Data from files
ms.openlocfilehash: 5dde70b9834d990987e42c6aa945940a7f110949
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96416073"
---
# <a name="introduction-to-dataflows-and-self-service-data-prep"></a>データフローとセルフサービスのデータ準備の概要

データの量は増え続けるので、データを整った形式のアクションにつながる情報に変換することが課題です。 大量のデータをアクションにつながる分析情報に迅速に変換できるよう、分析を行ったり、ビジュアル、レポート、ダッシュボードに設定したりする準備が整っているデータが必要です。 Power BI のビッグ データに対するセルフサービスのデータ準備を使用すると、ほんの数クリックでデータを Power BI の分析情報にできます。

![データのフロー](media/dataflows-introduction-self-service-flow.png)

## <a name="when-to-use-dataflows"></a>データフローを使用する場合

データフローは、次のシナリオをサポートするように設計されています。

* Power BI 内の多くのデータセットおよびレポートで共有できる再利用可能な変換ロジックを作成します。 データフローにより、基になるデータ要素の再利用性が促進され、クラウドまたはオンプレミスのデータ ソースとの個別の接続を作成する必要がなくなります。

* 独自の Azure Data Lake Gen 2 ストレージ内のデータを公開し、他の Azure サービスを未加工の基になるデータに接続できるようにします。

* 基になるシステムに接続するのではなく、アナリストにデータフローへの接続を強制することで、信頼できる単一の情報源を作成し、アクセスするデータと、データをレポート作成者に公開する方法を制御することができます。 また、データを業界標準の定義にマッピングして、Power Platform の他のサービスや製品で使用できるように、きちんとキュレーションされたビューを作成することもできます。

* 大量のデータを処理して ETL を大規模に実行する場合、Power BI Premium を使用したデータフローはより効率的に拡張され、柔軟性が向上します。 データフローにより、さまざまなクラウドおよびオンプレミスのソースがサポートされます。 

* アナリストが基になるデータ ソースに直接アクセスするのを防ぎます。 レポート作成者はデータフローに基づいて作成できるため、基になるデータソースへのアクセスを少数の個人にのみ許可し、アナリストがデータフローにアクセスし、それに基づいて作成できるようにする方が便利な場合があります。 このアプローチを使用すると、基になるシステムへの負荷が削減され、管理者は、システムが更新から読み込まれるタイミングをより細かく制御できます。

データ フローを作成した後は、Power BI Desktop と Power BI サービスを使用して、Common Data Model を活用するデータセット、レポート、ダッシュボード、アプリを作成し、ビジネス アクティビティについての詳細な分析情報を取得できます。 データセットと同様に、データフローの更新スケジュールは、データフローを作成したワークスペースから直接管理されます。

## <a name="next-steps"></a>次のステップ
この記事では、Power BI でのビッグ データ用のセルフサービスのデータ準備の概要と、それを使用するさまざまな方法を説明しました。 

データフローと Power BI の詳細については、以下の記事を参照してください。

* [データフローの作成](dataflows-create.md)
* [データフローの構成と使用](dataflows-configure-consume.md)
* [Azure Data Lake Gen 2 を使用するようにデータフロー ストレージを構成する](dataflows-azure-data-lake-storage-integration.md)
* [データフローの Premium 機能](dataflows-premium-features.md)
* [データフローでの AI の使用](dataflows-machine-learning-integration.md)
* [データフローの制限事項と考慮事項](dataflows-features-limitations.md)
* [データフローのベスト プラクティス](dataflows-best-practices.md)


Common Data Model について詳しくは、次の概要記事をご覧ください。
* [Common Data Model - 概要](/powerapps/common-data-model/overview)