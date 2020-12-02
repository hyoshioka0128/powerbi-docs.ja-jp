---
title: レポートから Power BI ダッシュボードを作成する
description: レポートから Power BI ダッシュボードを作成する
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 07/17/2019
ms.openlocfilehash: 4482fc3317b1ca10589645f19c22af31c8f8a80a
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96395557"
---
# <a name="create-a-power-bi-dashboard-from-a-report"></a>レポートから Power BI ダッシュボードを作成する
「[Power BI デザイナーのダッシュボードの概要](service-dashboards.md)」を読みました。今度は自分のダッシュボードを作成します。 ダッシュボードを作成するには、さまざまな方法があります。 たとえば、レポートから、何もない状態から、データセットから、または既存のダッシュボードを複製して、ダッシュボードを作成できます。  

まずは、既に作成されているレポートから視覚エフェクトをピン留めして、すばやく簡単なダッシュボードを作成します。 

この記事を完了すると、次のことを十分に理解できるようになります。
- ダッシュボードとレポートの関係
- レポート エディターで編集ビューを開く方法
- タイルをピン留めする方法 
- ダッシュボードとレポートの間を移動する方法 
 
![いくつかの視覚エフェクトを表示する Power B I ダッシュボードのスクリーンショット。](media/service-dashboard-create/power-bi-completed-dashboard-small.png)

> [!NOTE] 
> ダッシュボードは、Power BI Desktop ではなく、Power BI サービスの機能です。 ダッシュボードは Power BI モバイル デバイスで作成することはありませんが、そこで[表示および共有する](../consumer/mobile/mobile-apps-view-dashboard.md)ことができます。
>
> 

## <a name="video-create-a-dashboard-by-pinning-visuals-and-images-from-a-report"></a>ビデオ:レポートからビジュアルとイメージをピン留めすることでダッシュボードを作成する
レポートからの視覚化をピン留めして、新しいダッシュボードを作成する手順をご覧ください。 その後は、次のセクションの「[レポートでデータセットをインポートする](#import-a-dataset-with-a-report)」にある手順に従い、調達の分析のサンプルを使ってご自身でお試しください。
    

<iframe width="560" height="315" src="https://www.youtube.com/embed/lJKgWnvl6bQ" frameborder="0" allowfullscreen></iframe>

## <a name="import-a-dataset-with-a-report"></a>レポートでデータセットをインポートする
このステップバイステップでは、Power BI サンプル データセットの 1 つをインポートし、それを使って新しいダッシュボードを作成します。 ここで使うサンプルは、2 つの PowerView シートを含む Excel ブックです。 Power BI でブックをインポートすると、データセットとレポートがワークスペースに追加されます。 レポートは、PowerView シートから自動的に作成されます。

1. [調達の分析のサンプル](https://go.microsoft.com/fwlink/?LinkId=529784)の Excel ファイルをダウンロードします。 OneDrive for Business に保存することをお勧めします。
2. ブラウザーで Power BI サービス (app.powerbi.com) を開きます。
3. ナビ ペインから **[マイ ワークスペース]** を選択し、次に **[データの取得]** を選択します。

    ![ナビゲーション ウィンドウ](media/service-dashboard-create/power-bi-get-data-new-look.png)
5. **[ファイル]** で **[取得]** を選択します。

   ![ファイルの取得](media/service-dashboard-create/power-bi-select-files.png)
6. 調達の分析のサンプルの Excel ファイルを保存した場所に移動します。 ファイルを選び、 **[接続]** を選択します。

   ![ファイルへの接続](media/service-dashboard-create/power-bi-connectnew.png)
7. この演習では、 **[インポート]** を選択します。

    ![OneDrive for Business ウィンドウ](media/service-dashboard-create/power-bi-import.png)
8. 成功メッセージが表示されたら、 **[x]** を選択して閉じます。

   ![X が選択された成功メッセージが表示されているスクリーンショット。](media/service-dashboard-create/power-bi-view-datasetnew.png)

> [!TIP]
> ご存知でしたか? ナビ ペインを絞り込むには、上部の 3 本線のアイコン ![ナビ ペインの表示/非表示アイコン](media/service-dashboard-create/power-bi-new-look-hide-nav-pane.png) を選択します。 これにより、レポート自体の領域が増えます。

### <a name="open-the-report-and-pin-tiles-to-your-dashboard"></a>レポートを開いてダッシュボードにタイルをピン留めする
1. 同じワークスペースで **[レポート]** タブを選択し、 **[調達の分析のサンプル]** を選択してレポートを開きます。

    ![[レポート] タブ](media/service-dashboard-create/power-bi-reports.png) 読み取りビューでレポートが開きます。 左側に 2 つのタブがあることに注目してください。 **[割引の分析]** と **[支出の概要]** です。 各タブはレポートのページを表します。

2. **[その他のオプション (...)]**  >  **[レポートの編集]** を選択して、編集ビューでレポートを開きます。

    ![読み取りビューのレポート](media/service-dashboard-create/power-bi-reading-view.png)
3. 視覚化をポイントして、使用可能なオプションを表示します。 ダッシュボードに視覚エフェクトを追加するには、ピン留めアイコンを選択します ![ピン留めアイコン](media/service-dashboard-create/power-bi-pin-icon.png).

    ![タイルのポイント](media/service-dashboard-create/power-bi-hover.png)
4. ここでは新しいダッシュボードを作成しているため、 **[新しいダッシュボード]** オプションを選択して名前を指定します。

    ![[ダッシュボードにピン留めする] ウィンドウが表示されているスクリーンショット。](media/service-dashboard-create/power-bi-pin-tile.png)
5. **[ピン留め]** を選択すると、現在のワークスペースに新しいダッシュボードが作成されます。 **[ダッシュボードにピン留めしました]** というメッセージが表示されたら、 **[ダッシュボードに移動]** を選択します。 レポートの保存を求めるメッセージが表示されたら、 **[保存]** を選択します。

    ![[ダッシュボードに移動] オプションが選択された成功メッセージが表示されているスクリーンショット。](media/service-dashboard-create/power-bi-pin-success.png)

    Power BI で新しいダッシュボードが開きます。 1 つのタイルがあります。ピン留めしたばかりの視覚エフェクトです。

   ![1 つのタイルを含むダッシュボード](media/service-dashboard-create/power-bi-pinned.png)
7. タイルを選択してレポートに戻ります。 新しいダッシュボードにさらにいくつかタイルをピン留めします。 **[ダッシュボードにピン留めする]** ウィンドウが表示されたら、 **[既存のダッシュボード]** を選択します。  

   ![[既存のダッシュボード] オプションが選択された [ダッシュボードにピン留めする] ウィンドウが表示されているスクリーンショット。](media/service-dashboard-create/power-bi-existing-dashboard.png)

## <a name="pin-an-entire-report-page-to-the-dashboard"></a>レポート ページ全体をダッシュボードにピン留めする
1 度に 1 つのビジュアルをピン留めするのではなく、[レポート ページ全体を *ライブ タイル* としてピン留め](service-dashboard-pin-live-tile-from-report.md)できます。 やってみましょう。

1. レポート エディターで、 **[支出の概要]** タブを選択して、レポートの 2 ページ目を開きます。

   ![レポート タブ](media/service-dashboard-create/power-bi-page-tab.png)

2. ダッシュボードにレポートの視覚エフェクトをすべて表示してみましょう。 メニューバーの右上隅で、 **[ライブ ページをピン留めする]** を選択します。 ダッシュボードではページが更新されるたびに、ライブ ページのタイルが更新されます。

   ![レポート エディターの右上](media/service-dashboard-create/power-bi-pin-live.png)

3. **[ダッシュボードにピン留めする]** ウィンドウが表示されたら、 **[既存のダッシュボード]** を選択します。

   ![[既存のダッシュボード] オプションがオンになっている [ライブをピン留めする] ボタンを表示する [ダッシュボードにピン留めする] ウィンドウのスクリーンショット。](media/service-dashboard-create/power-bi-pin-live2.png)

4. 成功メッセージが表示されたら、 **[ダッシュボードに移動]** を選択します。 そこに、レポートからピン留めされたタイルが表示されています。 次の例では、レポートの 1 ページ目から 2 つのタイルを、レポートの 2 ページ目から 1 つのライブ タイルをピン留めしています。

   ![この記事の視覚エフェクトを表示する Power B I ダッシュボードのスクリーンショット。](media/service-dashboard-create/power-bi-dashboard.png)

## <a name="next-steps"></a>次の手順
これで初めてのダッシュボードを作成できました。 作成したダッシュボードでは、さらに多くの処理を行うことができます。 以下に提案されている記事のいずれかに従うか、ご自分で調査を開始してください。 

* [タイルのサイズを変更したり、移動したりする](service-dashboard-edit-tile.md)
* [ダッシュボードのタイルの概要](service-dashboard-tiles.md)
* [アプリを作成することによってダッシュボードを共有する](../collaborate-share/service-create-workspaces.md)
* [Power BI - 基本的な概念](../fundamentals/service-basic-concepts.md)
* [優れたダッシュボードのデザインに関するヒント](service-dashboards-design-tips.md)

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。
