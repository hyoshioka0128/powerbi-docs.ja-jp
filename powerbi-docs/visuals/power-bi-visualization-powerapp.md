---
title: Power BI レポートに新しいパワー アプリを埋め込む
description: 同じデータ ソースを使用し、他のレポート項目のようにフィルター処理できるアプリを埋め込みます
author: mihart
manager: kvivek
ms.reviewer: tapan maniar
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 06/01/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: c46410caff373eb8474a4b687e834b822f2da8ac
ms.sourcegitcommit: 37bd34053557089c4fbf0e05f78e959609966561
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/10/2020
ms.locfileid: "94397532"
---
# <a name="tutorial-embed-a-power-apps-visual-in-a-power-bi-report"></a>チュートリアル:Power BI レポートに Power Apps ビジュアルを埋め込む

このチュートリアルでは、Power Apps ビジュアルを使用して、サンプル Power BI レポートに埋め込まれる新しいアプリを作成します。 このアプリでは、そのレポート内の他のビジュアルとの対話が行われます。

Power Apps サブスクリプションをお持ちでない場合は、開始する前に[無料アカウントを作成](https://make.powerapps.com/signup?redirect=marketing&email=)してください。

このチュートリアルで学習する内容は次のとおりです。
> [!div class="checklist"]
> * Power BI レポートに Power Apps ビジュアルを追加する
> * Power Apps で、Power BI レポートのデータを使用する新しいアプリを作成する操作を行う
> * レポート内に Power Apps ビジュアルを表示して操作する

## <a name="prerequisites"></a>前提条件

* [Google Chrome](https://www.google.com/chrome/browser/) または [Microsoft Edge](https://www.microsoft.com/windows/microsoft-edge) ブラウザー
* [営業案件の分析のサンプル](../create-reports/sample-opportunity-analysis.md#get-the-content-pack-for-this-sample)がインストールされた [Power BI サブスクリプション](../fundamentals/service-self-service-signup-for-power-bi.md)
* [Power Apps でアプリを作成する](/powerapps/maker/canvas-apps/data-platform-create-app-scratch)方法と [Power BI レポートを編集する](../create-reports/service-the-report-editor-take-a-tour.md)方法を理解している



## <a name="create-a-new-app"></a>新しいアプリの作成
Power Apps ビジュアルをレポートに追加すると、Power Apps と Power BI 間のライブ データ接続を使用して Power Apps Studio が起動されます。

1. 営業案件の分析のサンプル レポートを開き、 *[Upcoming Opportunities]\(今後の案件\)* ページを選択します。 


2. 新しいビジュアル用のスペースを確保するために、レポート タイルの一部を移動してサイズを変更します。

    ![レポート タイルの移動とサイズ変更](media/power-bi-visualization-powerapp/power-bi-report-page.jpg)

2. [視覚化] ペインで、[Power Apps] アイコンを選択し、作成したスペースに合うようにビジュアルのサイズを変更します。

    ![[Powe Apps] アイコンが選択されている [視覚化] ウィンドウ](media/power-bi-visualization-powerapp/power-bi-powerapps-icon.jpg)

3. **[フィールド]** ウィンドウで、 **[名前]** 、 **[製品コード]** 、 **[営業段階]** を選択します。 

    ![フィールドを選択する](media/power-bi-visualization-powerapp/power-bi-fields.png)

4. Power Apps ビジュアルで、アプリを作成する Power Apps 環境を選択し、 **[新規作成]** を選択します。

    ![新しいアプリの作成](media/power-bi-visualization-powerapp/power-bi-create-new-powerapp.png)

    Power Apps Studio では、基本的なアプリが作成され、Power BI で選択したフィールドの 1 つが " *ギャラリー* " に表示されます。

    ![Power Apps が開く](media/power-bi-visualization-powerapp/power-bi-power-app.png)

5.  画面の半分のみを占めるようにギャラリーのサイズを変更します。 

6. 左側のペインで、 **[Screen1]** を選択し、画面の **[塗りつぶし]** プロパティを (レポートで目立つように) [LightBlue] に設定します。

    ![色パレット](media/power-bi-visualization-powerapp/power-bi-powerapps-fill.png)

6. ラベル コントロール用のスペースを作成します。 

    ![ギャラリーのサイズを変更する](media/power-bi-visualization-powerapp/power-bi-powerapps-gallery.png)


8. **[ギャラリー]** の下に、テキスト ラベル コントロールを挿入します。

   ![ラベル コントロール](media/power-bi-visualization-powerapp/power-bi-label.png)

7. ラベルをビジュアルの一番下にドラッグします。 **[テキスト]** プロパティを `"Opportunity Count: " & CountRows(Gallery1.AllItems)` に設定します。 これで、データ セット内の営業案件の総数が表示されます。

    ![ギャラリーのサイズを変更したアプリ](media/power-bi-visualization-powerapp/power-bi-power-app-label.png)

    ![ラベルが更新されたアプリ](media/power-bi-visualization-powerapp/power-bi-label-live.png)

7. 「営業案件」という名前でアプリを保存します。 

    ![アプリを保存する](media/power-bi-visualization-powerapp/power-bi-save-powerapp.png)


## <a name="view-the-app-in-the-report"></a>レポートでアプリを確認する
Power BI レポートでアプリを使用できるようになりました。アプリは他のビジュアルと対話できます。これは、同じデータ ソースを共有しているためです。

![Power BI レポート内のアプリ](media/power-bi-visualization-powerapp/power-bi-powerapps-visual.png)

Power BI レポートのスライサーで **[1 月]** を選択します。これで、アプリ内のデータを含むレポート全体がフィルター処理されます。

![フィルター処理されたレポート](media/power-bi-visualization-powerapp/power-bi-last.png)

アプリの営業案件数が、レポートの左上の数と一致することに注目してください。 レポートの他の項目を選択すると、アプリのデータが更新されます。


## <a name="clean-up-resources"></a>リソースをクリーンアップする
営業案件の分析のサンプルをもう使用しない場合は、ダッシュボード、レポート、およびデータセットを削除できます。

## <a name="limitations-and-considerations"></a>制限事項と考慮事項
トラブルシューティングの詳細については、「[Power BI 用の Power Apps ビジュアル](/powerapps/maker/canvas-apps/powerapps-custom-visual#limitations-of-the-power-apps-visual)」を参照してください。

## <a name="next-steps"></a>次の手順
[Q&A ビジュアル](power-bi-visualization-types-for-reports-and-q-and-a.md)    
[チュートリアル: Power BI レポートに Power Apps ビジュアルを埋め込む](/powerapps/maker/canvas-apps/powerapps-custom-visual)