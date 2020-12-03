---
title: Power BI デザイナーのダッシュボードのタイルの概要
description: この記事では、Power BI のダッシュボード タイルについて説明します。これには、SQL Server Reporting Services (SSRS) レポートから作成されたタイルも含まれます。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 04/17/2020
LocalizationGroup: Dashboards
ms.openlocfilehash: 56f00568b22d236b498446065cf97ff565993e7a
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418239"
---
# <a name="intro-to-dashboard-tiles-for-power-bi-designers"></a>Power BI デザイナーのダッシュボードのタイルの概要

タイルは、ダッシュボードにピン留めされた、データのスナップショットです。 タイルは、レポート、データセット、ダッシュボード、Q&A ボックス、Excel、SQL Server Reporting Services (SSRS) レポートなどから作成できます。  次のスクリーンショットは、ダッシュボードにピン留めされているさまざまなタイルを示しています。

![Power BI ダッシュボード](media/service-dashboard-tiles/power-bi-dashboard.png)

ダッシュボードおよびダッシュボード タイルは、Power BI Desktop ではなく、Power BI サービスの機能です。 ダッシュボードはモバイル デバイスで作成できますが、そこで[参照し共有する](../consumer/mobile/mobile-apps-view-dashboard.md)ことができます。

タイルをピン留めするだけでなく、[[タイルの追加]](service-dashboard-add-widget.md) コントロールを使用することでダッシュボードで直接、スタンドアロンのタイルを作成できます。 スタンドアロン タイルには、テキスト ボックス、画像、ビデオ、ストリーミング データ、Web コンテンツが含まれます。

Power BI を構成する要素を理解するうえで助けが必要ですか? 「[Power BI サービスのデザイナー向けの基本的な概念](../fundamentals/service-basic-concepts.md)」を参照してください。

> [!NOTE]
> タイルの作成に使った元の視覚エフェクトが変更された場合、タイルは変更されません。  たとえば、レポートからの折れ線グラフをピン留めし、折れ線グラフを横棒グラフに変更した場合でも、ダッシュボード タイルは引き続き折れ線グラフを表示します。 データは更新されますが、視覚化の種類は変更されません。
> 
> 

## <a name="pin-a-tile"></a>タイルをピン留めする
ダッシュボードにタイルを追加 (ピン留め) するには、さまざまな方法があります。 次の場所にあるタイルをピン留めできます。

* [Power BI Q & A](service-dashboard-pin-tile-from-q-and-a.md)
* [レポート](service-dashboard-pin-tile-from-report.md)
* [別のダッシュボード](service-pin-tile-to-another-dashboard.md)
* [OneDrive for Business 上の Excel ブック](service-dashboard-pin-tile-from-excel.md)
* [Quick Insights (クイック分析情報)](service-insights.md)
* [Power BI Report Server または SQL Server Reporting Services のページ分割されたオンプレミス レポート](/sql/reporting-services/pin-reporting-services-items-to-power-bi-dashboards)

[[タイルの追加]](service-dashboard-add-widget.md) コントロールを使用することで、画像、テキスト ボックス、ビデオ、ストリーミング データ、Web コンテンツ用のスタンドアロン タイルをダッシュボードで直接作成します。

  ![タイルの追加アイコン](media/service-dashboard-tiles/add_widgetnew.png)

## <a name="interact-with-tiles-on-a-dashboard"></a>ダッシュボードのタイルとの対話
ダッシュボードにタイルを追加した後、タイルを移動したり、サイズ、外観、動作を変更したりできます。

### <a name="move-and-resize-a-tile"></a>タイルの移動とサイズ変更
タイルをつかんで、[ダッシュボード上を移動](service-dashboard-edit-tile.md)できます。 ![タイル ハンドル](media/service-dashboard-tiles/resize-handle.jpg) ハンドルにマウス カーソルを置いて選択し、タイルのサイズを変更します。

### <a name="hover-over-a-tile-to-change-the-appearance-and-behavior"></a>タイルにカーソルを置いて動作と外観を変更する
1. タイルにマウス カーソルを置き、省略記号を表示します。
   
    ![タイルの省略記号](media/service-dashboard-tiles/ellipses_new.png)
2. 省略記号を選択し、タイルの操作メニューを開きます。
   
    ![省略記号アイコン](media/service-dashboard-tiles/power-bi-tile-menu.png)
   
    ここでは、次の操作を実行できます。
   
     * [ダッシュボードにコメントを追加する](../consumer/end-user-comment.md)。
     * [このタイルの作成に使用されたレポートを開く](../consumer/end-user-reports.md)。  
     * [フォーカス モードで表示する](../consumer/end-user-focus.md)。   
     * [タイルで使用されているデータをエクスポートする](../visuals/power-bi-visualization-export-data.md)。
     * [タイトルとサブタイトルを編集し、ハイパーリンクを追加する](service-dashboard-edit-tile.md)。 
     * [インサイトを実行する](service-insights.md)。 
     * [別のダッシュボードにタイルをピン留めする](service-pin-tile-to-another-dashboard.md)。
     * [タイルを削除する](service-dashboard-edit-tile.md)。

3. 操作メニューを閉じるには、ダッシュボードの空白領域を選択します。

### <a name="select-a-tile"></a>タイルの選択
タイルを選択したときに次に生じる動作は、タイルの作成方法によって異なります。 それ以外の場合、タイルを選択すると、そのタイルを作成するために使われたレポート、Excel Online ブック、オンプレミスの Reporting Services レポート、Q&A の質問に移動できます。 あるいは、[カスタム リンク](service-dashboard-edit-tile.md)がある場合、タイルを選択するとそのリンクに移動します。

> [!NOTE]
> 例外は、 **[タイルの追加]** を使用してダッシュボードに直接作成したビデオ タイルの場合です。 (この方法で作成された) ビデオ タイルを選択すると、ダッシュボード上で直接ビデオが再生されます。   
> 
> 

## <a name="considerations-and-troubleshooting"></a>考慮事項とトラブルシューティング

* 視覚エフェクトの作成に使われたレポートが保存されなかった場合は、タイルを選択してもアクションは発生しません。
* タイルが Excel Online のブックから作成された場合、少なくともそのブックに対する読み取りアクセス許可が必要です。 ない場合、タイルを選択しても Excel Online でブックは開けません。
* **[タイルの追加]** を使用してダッシュボードに直接タイルを作成し、それに対してカスタム ハイパーリンクを設定したとします。 その場合、タイトル、サブタイトル、またはタイルを選択すると、その URL が開きます。 それ以外の場合、既定では、イメージ、Web コード、またはテキスト ボックスのためにダッシュボード上に直接作成されたタイルを選択しても、何も起こりません。
* タイルは、Power BI Report Server または SQL Server Reporting Services のページ分割されたオンプレミス レポートから作成できます。 オンプレミス レポートにアクセスする権限がない場合、タイルを選択すると、アクセス権がないことを示す (rsAccessDenied) ページに移動します。
* Power BI Report Server または SQL Server Reporting Services のページ分割されたオンプレミス レポートから作成されたタイルを選択するとします。 レポート サーバーが置かれているネットワークにアクセスする権限がない場合、そのページ分割されたレポートから作成されたタイルを選択すると、サーバーが見つからないことを示すページに移動します (HTTP 404)。 レポートを表示するには、デバイスにレポート サーバーへのネットワーク アクセスが必要です。
* タイルの作成に使った元の視覚エフェクトが変更された場合、タイルは変更されません。 たとえば、レポートからの折れ線グラフをピン留めし、折れ線グラフを横棒グラフに変更した場合でも、ダッシュボード タイルは引き続き折れ線グラフを表示します。 データは更新されますが、視覚化の種類は変更されません。

## <a name="next-steps"></a>次の手順
- [ダッシュボードのカード (大きな数字のタイル) を作成する](../visuals/power-bi-visualization-card.md)
- [Power BI デザイナーのダッシュボードの概要](service-dashboards.md)  
- [Power BI でのデータの更新](../connect-data/refresh-data.md)
- [Power BI サービスのデザイナー向けの基本的な概念](../fundamentals/service-basic-concepts.md)
- [Power BI タイルを Office ドキュメントに統合する](https://powerbi.microsoft.com/blog/integrating-power-bi-tiles-into-office-documents/)
- [Reporting Services のアイテムを Power BI ダッシュボードにピン留めする](/sql/reporting-services/pin-reporting-services-items-to-power-bi-dashboards)

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。