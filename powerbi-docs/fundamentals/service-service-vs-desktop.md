---
title: Power BI Desktop と Power BI サービスの比較
description: Power BI Desktop は包括的なデータ分析/レポート作成ツールです。 Power BI サービスは、チームや企業が簡単なレポート編集や共同作業を行うためのクラウドベースのオンライン サービスです。
author: maggiesMSFT
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/07/2020
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 0b4a1275a3b50fbadd37d953b77316d6021c800c
ms.sourcegitcommit: 37bd34053557089c4fbf0e05f78e959609966561
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/10/2020
ms.locfileid: "94397095"
---
# <a name="comparing-power-bi-desktop-and-the-power-bi-service"></a>Power BI Desktop と Power BI サービスの比較

Power BI Desktop と Power BI サービスを比較したベン図では、中央の領域にこの 2 つが重なる部分が示されます。 一部のタスクは Power BI Desktop でも Power BI サービスでも実行できます。 ベン図の右側と左側には、アプリケーションとサービスに固有の機能が示されています。  

![Power BI Desktop と Power BI サービスの関係を示すベン図。](media/service-service-vs-desktop/power-bi-venn-desktop-service.png)

**Power BI Desktop** は、ローカル コンピューターに無料でインストールする完全なデータ分析とレポート作成ツールです。 これには、さまざまなデータ ソースに接続し、それらを 1 つのデータ モデルに結合できる (これはモデリングと呼ばれることがあります) クエリ エディターが含まれています。 その後、そのデータ モデルに基づいてレポートを設計します。 「[Power BI Desktop 概要ガイド](desktop-getting-started.md)」でこのプロセスが説明されています。

**Power BI サービス** はクラウドベースのサービスです。 チームや組織のための簡単なレポート編集や共同作業をサポートします。 Power BI サービスでもデータ ソースに接続できますが、モデリングに制限があります。

Business Intelligence プロジェクトに取り組んでいるほとんどの Power BI レポート デザイナーは、 **Power BI Desktop** を使用して Power BI レポートを作成した後、 **Power BI サービス** を使用してレポートを共同作成し、配布します。

Power BI サービスではまた、Power BI Premium 容量によってサポートされるワークスペースで " *ページ分割されたレポート* " がホストされます。 Power BI レポート ビルダーでページ分割されたレポートを作成します。 「Power BI Premium のページ分割されたレポートとは」という記事の「[Power BI レポートとページ分割されたレポートを比較する](../paginated-reports/paginated-reports-report-builder-power-bi.md#compare-power-bi-reports-and-paginated-reports)」をご覧ください。 ご覧ください。

## <a name="editing-power-bi-reports"></a>Power BI レポートを編集する

アプリケーションとサービスの両方で、Power BI " *レポート* " を構築し、編集します。 レポートには任意の数のページとビジュアルを含めることができます。 レポート内の移動機能を強化する目的で、ブックマーク、ボタン、フィルター、ドリルスルーを追加します。

![番号付きセクションがある、Power BI Desktop と Power BI サービスのスクリーンショット。](media/service-service-vs-desktop/power-bi-editing-desktop-service.png)

Power BI Desktop と Power BI サービスのレポート エディターは同じようなものです。 3 つのセクションから構成されています。  

1. 上部のナビ ペイン。Power BI Desktop と Power BI サービスで異なります    
2. レポート キャンバス     
3. **フィールド** 、 **視覚化** 、 **フィルター** の各ウィンドウ

この動画では、Power BI Desktop のレポート エディターをご覧いただけます。 

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>

## <a name="working-in-the-power-bi-service"></a>Power BI サービスでの作業

### <a name="collaborating"></a>共同作業

レポートを作成したら、それを **Power BI サービス** の *ワークスペース* に保存し、そこで同僚と共同作業できます。 このレポートの上に *ダッシュボード* を構築します。 その後、組織内外のレポート利用者とダッシュボードやレポートを共有します。 レポート利用者は Power BI サービスの編集ビューではなく、" *読み取りビュー* " でダッシュボードやレポートを閲覧します。 レポート作成者が利用できる機能をすべて利用することはできません。  また、データセットを共有し、他のユーザーが独自のレポートを作成できるようにすることもできます。 Power BI サービスでの共同作業の詳細については、[こちら](../collaborate-share/service-new-workspaces.md)をご覧ください。

### <a name="self-service-data-prep-with-dataflows"></a>データフローを使用したセルフサービスのデータ準備

データフローは、組織がばらばらのソースからデータを取りまとめてモデリング用に準備するのに役立ちます。 アナリストは、使い慣れたセルフサービス ツールを使用して簡単にデータフローを作成できます。 アナリストは、データフローを使用して、データ ソース接続、ETL ロジック、更新スケジュールなどを定義することにより、ビッグ データの取り込み、変換、統合、補強を行います。 データフローを使用したセルフサービスのデータ準備の詳細については、[こちら](../transform-model/dataflows/dataflows-introduction-self-service.md)をご覧ください。

## <a name="next-steps"></a>次の手順

[Power BI Desktop とは何ですか?](desktop-what-is-desktop.md)

Power BI サービスで[レポートを作成する](../create-reports/service-report-create-new.md)

[レポート デザイナーの基本的な概念](service-basic-concepts.md)

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。