---
title: チュートリアル:Power BI サービスでの作成の概要
description: Power BI オンライン サービスの概要 (app.powerbi.com)
author: mihart
ms.author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-fundamentals
ms.topic: tutorial
ms.date: 01/13/2021
LocalizationGroup: Get started
ms.openlocfilehash: 04777ba93b6a4639b55406b3952a80de963cb540
ms.sourcegitcommit: 5c5a27aa7ba21612df4c4096e635dfe4b9aaebcf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/27/2021
ms.locfileid: "98861217"
---
# <a name="tutorial-get-started-creating-in-the-power-bi-service"></a>チュートリアル:Power BI サービスでの作成の概要
このチュートリアルでは、*Power BI サービス* の一部の機能について説明します。 ここでは、データに接続し、レポートとダッシュボードを作成して、データに関する質問をします。 Power BI サービスでは、さらに多くのことを行うことができます。このチュートリアルは、単にみなさんの興味をかき立てることを目的としています。 Power BI サービスと他の Power BI 製品の関係を理解するため、「[Power BI とは?](power-bi-overview.md)」を読むことをお勧めします。

レポートの作成者ではなく "*閲覧者*" の場合は 出発点として「[Power BI サービス内の移動](../consumer/end-user-experience.md)」をお勧めします。

:::image type="content" source="media/service-get-started/power-bi-service-rearranged-dashboard.png" alt-text="財務サンプル ダッシュボードのスクリーンショット。":::

このチュートリアルでは、以下の手順を実行します。

> [!div class="checklist"]
> * Power BI オンライン アカウントにサインインするか、まだアカウントをお持ちでない場合はサインアップします。
> * Power BI サービスを開きます。
> * データをいくつか取得し、それをレポート ビューで開きます。
> * そのデータを使用して視覚化を作成し、レポートとして保存します。
> * レポートからタイルをピン留めし、ダッシュボードを作成します。
> * Q&A 自然言語ツールを利用して、他の視覚エフェクトをダッシュボードに追加します。
> * ダッシュボード上でタイルのサイズ変更、再配置、編集を行います。
> * データセット、レポート、ダッシュボードを削除してリソースをクリーンアップします。

## <a name="sign-up-for-the-power-bi-service"></a>Power BI サービスにサインアップする
Power BI でコンテンツを作成するには、Power BI Pro ライセンスが必要です。 Power BI アカウントがない場合は、始める前に[無料の Power BI Pro 試用版にサインアップ](https://app.powerbi.com/signupredirect?pbi_source=web)してください。

## <a name="step-1-get-data"></a>手順 1:データを取得

Power BI レポートを作成するときには、多くの場合、Power BI Desktop から開始します。 Power BI Desktop にはさらに高度な機能があります。 レポートのデザインを開始する前に、データを変換、整形、およびモデル化することができます。 今回は、Power BI サービスでレポートの作成を最初から開始します。

このチュートリアルでは、単純な Microsoft Excel ファイルからデータを取得します。 どうしたらよいでしょうか? [財務サンプル ファイルをダウンロードします](https://go.microsoft.com/fwlink/?LinkID=521962)。

1. まずブラウザーで Power BI サービス (app.powerbi.com) を開きます。 

    アカウントをお持ちではありませんか。 心配はいりません。[無料の Power BI Pro 無料試用版にサインアップできます](https://app.powerbi.com/signupredirect?pbi_source=web)

1. ナビゲーション ペインで **[マイ ワークスペース]** を選択します。

1. **[マイ ワークスペース]** で、 **[新規]**  >  **[ファイルのアップロード]** を選択します。

    **[データの取得]** ページが開きます。   

3. **[新しいコンテンツの作成]** セクションで **[ファイル]** が選択されていることを確認し、Excel ファイルを保存した場所を選択します。
   
    :::image type="content" source="media/service-get-started/power-bi-service-get-data-local-file.png" alt-text="[新しいコンテンツの作成] > [ファイル] のスクリーンショット。":::

5. コンピューター上のファイルに移動し、 **[開く]** を選びます。

5. このチュートリアルでは、 **[インポート]** を選択し、レポートおよびダッシュボードの作成に使用できるデータセットとして、Excel ファイルを追加します。 **[アップロード]** を選択した場合は、Excel ブック全体が Power BI にアップロードされるので、それを Excel Online で開いて編集できます。
   
   :::image type="content" source="media/service-get-started/power-bi-import.png" alt-text="[インポート] の選択のスクリーンショット。":::
6. データセットの準備ができたら、財務サンプル データセットの横にある **[その他のオプション (...)]** を選択し、 **[レポートの作成]** を選択します。
1. レポート エディターを開きます。 

    :::image type="content" source="media/service-get-started/power-bi-service-datasets.png" alt-text="[すべてのコンテンツ] > [レポートの作成] のスクリーンショット。":::

    レポート キャンバスは空白です。 右側に **[フィルター]** 、 **[視覚化]** 、 **[フィールド]** の各ウィンドウが表示されています。

    :::image type="content" source="media/service-get-started/power-bi-service-blank-report.png" alt-text="空のレポート キャンバスのスクリーンショット。":::

    > [!TIP]
    > 左上隅のグローバル ナビゲーション ボタンを選択して、ナビゲーション ペインを折りたたみます。 これで、キャンバスの空き領域が増えます。
    >
    >:::image type="content" source="media/service-get-started/power-bi-global-nav-button.png" alt-text="グローバル ナビゲーション ボタン。":::
    >

7. 現在開かれているのは編集ビューです。 メニュー バーの **[読み取りビュー]** オプションに注目してください。 

    :::image type="content" source="media/service-get-started/power-bi-service-reading-view.png" alt-text="[読み取りビュー] オプションのスクリーンショット。":::

    編集ビューでは、レポートを変更できます。これは、あなたがレポートの "*所有者*" であり、"*作成者*" であるためです。 同僚とレポートを共有すると、多くの場合、その相手は読み取りビューでのみレポートを操作できます。 このようなユーザーは、**マイ ワークスペース** のレポートの "*コンシューマー*" です。 

## <a name="step-2-create-a-chart-in-a-report"></a>手順 2:レポートにグラフを作成する
データに接続したので、探索を開始します。 興味深いものが見つかったら、それをレポート キャンバスに保存できます。 次に、それをダッシュボードに固定して監視し、時間の経過と共にどのように変化するかを確認できます。 ただし、最初に行うことがあります。
    
1. レポート エディターで、ページの右側にある **[フィールド]** ペインで視覚化の作成を開始します。 **[総売上]** フィールドを選択し、 **[日付]** フィールドを選択します。
   
   :::image type="content" source="media/service-get-started/power-bi-service-fields-pane-selected.png" alt-text="フィールド一覧のスクリーンショット。":::

    Power BI によってデータが分析され、縦棒グラフの視覚化が作成されます。 

    > [!NOTE]
    > 最初に **[総売上]** ではなく **[日付]** フィールドを選択した場合は、テーブルが表示されます。 ご心配なく。 次の手順で視覚化を変更します。

    Power BI で数値が含まれていることが検出されたため、一部のフィールドの横にシグマ記号が表示されています。

    :::image type="content" source="media/service-get-started/power-bi-sigma-fields.png" alt-text="シグマ記号が表示されたフィールド。":::

2. このデータを表示する方法を切り替えましょう。 折れ線グラフは、値を時間の経過と共に表示する場合に適したビジュアルです。 **[視覚化]** ペインで **折れ線グラフ** アイコンを選択します。
   
   :::image type="content" source="media/service-get-started/power-bi-service-select-line-chart.png" alt-text="折れ線グラフが選択されているレポート エディターのスクリーンショット。":::

3. 役に立ちそうなので、グラフをダッシュボードに "*ピン留め*" します。 視覚エフェクトをポイントし、ピン留めアイコンを選択します。
   
   :::image type="content" source="media/service-get-started/power-bi-service-pin-visual.png" alt-text="ピン留めアイコンのスクリーンショット。":::

4. これは新しいレポートであるため、視覚エフェクトをダッシュボードにピン留めする前に、レポートを保存するよう要求されます。 レポートに名前を付け (たとえば、「*財務サンプル レポート*」)、 **[保存]** します。 

    これで、読み取りビューでレポートが表示されるようになります。 

6. **ピン留め** アイコンをもう一度選択します。
 
5. たとえば、 **[新しいダッシュボード]** を選択し、「*財務サンプル ダッシュボード*」という名前を付けます。 
   
   :::image type="content" source="media/service-get-started/power-bi-pin.png" alt-text="ダッシュボードの [名前] のスクリーンショット。":::
  
    右上隅の近くに成功メッセージが表示されたら、視覚エフェクトがダッシュボードにタイルとして追加されたことがわかります。
   
    :::image type="content" source="media/service-get-started/power-bi-pin-success.png" alt-text="ダッシュボード ダイアログにピン留めされたスクリーンショット。":::

    この視覚化をピン留めしたので、ダッシュボードに保存されます。 データは最新の状態に保たれるため、最新の値をひとめで追跡できます。 ただし、レポートの視覚化の種類を変更しても、ダッシュボードの視覚化は変更されません。

7. **[ダッシュボードへ移動]** を選択すると、タイルとしてピン留めした折れ線グラフが表示された新しいダッシュボードが表示されます。 
   
   :::image type="content" source="media/service-get-started/power-bi-service-dashboard-tile.png" alt-text="視覚化がピン留めされたダッシュボードのスクリーンショット。":::
   
8. ダッシュボードで新しいタイルを選択します。 Power BI の表示が閲覧表示のレポートに戻ります。

1. 編集表示に戻るには、メニュー バーにある **[その他のオプション]** (...) を選択し、 **[編集]** を選択します。

    :::image type="content" source="media/service-get-started/power-bi-service-edit-report.png" alt-text="[編集] を選択してレポートを編集するスクリーンショット。":::

    編集表示に戻ると、タイルの探索とピン留めを続けることができます。

## <a name="step-3-explore-with-qa"></a>手順 3:Q&A で探索する

データのクイック探索については、Q&A の質問ボックスで質問してください。 Q&A を使用すると、データに関する自然言語のクエリを行うことができます。 Q&A ボックスは、ダッシュボードではメニュー バーの一番上にあります (**データについて質問する**)。 レポートでは、上部のメニュー バーに表示されます (**質問する**)。

1. ダッシュボードに戻るには、黒い **Power BI** ヘッダー バーで **[マイ ワークスペース]** を選択します。

    :::image type="content" source="media/service-get-started/power-bi-service-go-my-workspace.png" alt-text="マイ ワークスペースに戻るスクリーンショット。":::

1. **[マイ ワークスペース]** でダッシュボードを選択します。

    :::image type="content" source="media/service-get-started/power-bi-service-dashboard-tab.png" alt-text="ダッシュボードの選択のスクリーンショット。":::

1. **[データについて質問する]** を選択します。 Q&A によっていくつかの提案が自動的に提供されます。 

    :::image type="content" source="media/service-get-started/power-bi-service-new-qanda.png" alt-text="Q&A キャンバスのスクリーンショット。":::

    > [!NOTE]
    > 提案が表示されない場合は、**新しい Q&A エクスペリエンス** をオンにします。

    :::image type="content" source="media/service-get-started/power-bi-new-qna-experience.png" alt-text="新しい Q&A エクスペリエンスを有効にするスクリーンショット。":::

1. 提案によっては 1 つの値が返されます。 たとえば、 **[what is the average cog]\(平均売上原価はいくらですか\)** を選択します。

    Q&A によって回答が検索され、*カード* 視覚エフェクトの形式で表示されます。

3. **[ビジュアルをピン留めする]** を選択し、その視覚化を財務サンプル ダッシュボードにピン留めします。

    :::image type="content" source="media/service-get-started/power-bi-qna-pin-tile.png" alt-text="ビジュアルのピン留めのスクリーンショット。":::

1. Q&A に戻り、 **[すべての候補を表示する]** を選択します。
1. **[total profit by country]\(国別の総利益\)** を選択します。 

    :::image type="content" source="media/service-get-started/power-bi-qna-total-profit-country.png" alt-text="国別の総利益のスクリーンショット。":::

1. 財務サンプル ダッシュボードにもマップをピン留めします。

1. ダッシュボードで、ピン留めしたマップを選択します。 これで Q&A がもう一度開きます。 
1. [Q&A] ボックス内の「*by month*」の後にカーソルを置き、「*as bar*」と入力します。 Power BI で結果を使用して横棒グラフが作成されます。

    :::image type="content" source="media/service-get-started/power-bi-qna-profit-country-bar.png" alt-text="横棒グラフの視覚化のスクリーンショット。":::

1. 財務サンプル ダッシュボードにも横棒グラフをピン留めします。

4. **[Q&A の終了]** を選択してダッシュボードに戻ると、作成した新しいタイルが表示されます。 

   :::image type="content" source="media/service-get-started/power-bi-service-dashboard-qna.png" alt-text="Q&A ビジュアルがピン留めされたダッシュボードのスクリーンショット。":::

   Q&A でマップを横棒グラフに変更しても、ピン留めしたときにマップだったため、タイルはマップのままでした。 

## <a name="step-4-reposition-tiles"></a>手順 4.タイルの位置変更

ダッシュボード領域をより効果的に使用できるように、タイルを再配置できます。

1. *Gross Sales (総売上)* 折れ線グラフ タイルの右下隅を上にドラッグして、売上タイルと同じ高さにスナップしたら、放します。

    :::image type="content" source="media/service-get-started/power-bi-service-resize-tile.png" alt-text="タイルのサイズ変更のスクリーンショット。":::

    これで、2 つのタイルの高さが同じになりました。

1. [Average of COGS]\(平均売上原価\) タイルの **[その他のオプション (…)]** タイル > **[詳細の編集]** を選択します。 

    :::image type="content" source="media/service-get-started/power-bi-tile-edit-details.png" alt-text="タイルの [その他のオプション] メニューのスクリーンショット。":::

1. **[タイトル]** ボックスに「*平均売上原価*」と入力し  >  **[適用]** を選択します。

    :::image type="content" source="media/service-get-started/power-bi-tile-details-dialog.png" alt-text="[詳細の編集] ダイアログボックスのスクリーンショット。":::

1. 他のビジュアルを合わせて配置します。

    よくなりましたね。

    :::image type="content" source="media/service-get-started/power-bi-service-rearranged-dashboard.png" alt-text="再配置されたダッシュボードのスクリーンショット。":::


## <a name="clean-up-resources"></a>リソースをクリーンアップする
チュートリアルはこれで完了です。データセット、レポート、ダッシュボードは削除してかまいません。 

1. 黒い **Power BI** ヘッダー バーにある **[マイ ワークスペース]** を選択します。
2. 財務サンプル データセットの横にある **[その他のオプション (...)]** 、 **[削除]** の順に選択します。

    :::image type="content" source="media/service-get-started/power-bi-service-delete-dataset.png" alt-text="データセットの削除のスクリーンショット。":::

    "**このデータセットのデータを含むレポートとダッシュボード タイルもすべて削除されます**" という警告が表示されます。

4. **[削除]** を選択します。

## <a name="next-steps"></a>次の手順

[データを Power BI サービスに貼り付けることで、レポートをすばやく作成する](https://powerbi.microsoft.com/en-us/blog/quickly-create-reports-power-bi-service/)

Power BI の Microsoft Learn コンテンツの次のコレクションを確認します。

- [Power BI の学習](/learn/powerplatform/power-bi?WT.mc_id=powerbi_landingpage-docs-link)
- [Power BI データ アナリストになる](/users/microsoftpowerplatform-5978/collections/djwu3eywpk4nm)