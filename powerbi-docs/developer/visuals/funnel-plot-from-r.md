---
title: 埋め込み BI 分析情報を向上させるために、Power BI 埋め込み分析で R スクリプトから R ビジュアルにじょうごプロットを作成する
description: この記事では、R スクリプトから R Power BI ビジュアルにじょうごプロットを作成する方法について説明します。 Power BI 埋め込み分析を使用して、より優れた埋め込み BI インサイトを有効にします。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: tutorial
ms.date: 04/02/2020
ms.openlocfilehash: f3d22a4143287588ad9290d000402a10a4cef227
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2021
ms.locfileid: "97889273"
---
# <a name="tutorial-build-a-funnel-plot-from-r-script-to-r-visual"></a>チュートリアル:R スクリプトから R ビジュアルにフィルター プロットを作成する
この記事では、R ビジュアルで R スクリプトを使用してじょうごプロットを作成する方法を順を追って説明します。

この記事では、次の方法について説明します。

> [!div class="checklist"]
>
> * RStudio の R スクリプト
> * Power BI の R ビジュアル
> * Power BI での "*PNG ベースの*"、R を利用したビジュアル
> * Power BI での "*HTML ベースの*"、R を利用したビジュアル

じょうごプロットを使用すると、予想されるバリエーションの量を簡単に使用、解釈、および表示することができます。 **じょうご** は、信頼制限を使用して形成され、外れ値はじょうごの外側にドットとして表示されます。

この例では、じょうごプロットを使用して、さまざまなセットのデータを比較および分析します。  

> [!NOTE]
> それぞれの一連の手順で、ソース ファイルをダウンロードできます。

## <a name="build-an-r-script-with-dataset"></a>データセットを使用した R スクリプトの作成

1. [最小の R スクリプト](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter1_R/script_R_v1_00.r) とそのデータテーブル ([dataset.csv](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter1_R/dataset.csv)) をダウンロードします。

1. 次に、スクリプトの編集を行って、[こちらのスクリプト](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter1_R/script_R_v1_01.r)をミラーリングします。 これにより、入力エラー処理とユーザー パラメーターが追加され、プロットの外観を制御できます。

## <a name="build-a-report"></a>レポートを作成する

次に、スクリプトの編集を行って、[こちらのスクリプト](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter2_Rvisual/script_RV_v2_00.r)をミラーリングします。 これにより、*read.csv* ではなく *dataset.csv* が Power BI デスクトップ ワークスペースに読み込まれ、**がん死亡率** テーブルが作成されます。 次の [PBIX ファイル](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter2_Rvisual/funnelPlot_Rvisual.pbix)の結果を確認してください。

> [!NOTE]
> `dataset` は、任意の R ビジュアルの入力 `data.frame` に対してハードコーディングされた名前です。 

## <a name="create-an-r-powered-visual-and-package-in-r-code"></a>R コードで R を利用したビジュアルとパッケージを作成する

1. 開始する前に、必ず [PBIVIZ ツールをインストール](./environment-setup.md#install-pbiviz)してください。

1. 次のコマンドを実行して、R を利用した新しいビジュアルを作成します。

   ```bash
   pbiviz new funnel-visual -t rvisual
   cd funnel-visual
   npm install 
   pbiviz package
   ```

   このコマンドによって、初期テンプレート ビジュアル (`-t` は **テンプレート** に対応する) を含むフォルダー *funnel-visual* が作成されます。 PBIVIZ は *dist* フォルダー内の *script.r* ファイルに含まれる R コードです。 それを Power BI にインポートして、何が起こるかを試してみてください。

1. *script.r* ファイルを編集して、その内容を前のスクリプトに置き換えます。

1. *capabilities.json* を編集して、文字列 `Values` を `dataset` に置き換えます。 これにより、テンプレート内の "ロール" の名前が置き換えられ、R コード内と同様になります。

   ![json ファイルに対する変更の差分比較のスクリーンショット。](./samples/funnel-plot/chapter-3/funnel-r-visual-v01/capabilities-changes.PNG)

1. *(省略可能)* *dependencies.json* を編集して、R スクリプトで必要とされる各 R パッケージのセクションを追加します。 これにより、ビジュアルが初めて読み込まれる場合に、これらのパッケージを自動的にインポートするように Power BI に指示が出されます。

   ![cranPackages の項目にコンテンツが追加されたときの差分比較を表示するスクリーンショット。](./samples/funnel-plot/chapter-3/funnel-r-visual-v01/dependencies-changes.PNG)

1. `pbiviz package` コマンドを使用してビジュアルを再パッケージ化してから、それを Power BI にインポートしてみてください。

> [!NOTE]
> ダウンロードについては、[PBIX](https://github.com/microsoft/PowerBI-visuals/blob/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelPlot_RCustomVisual.pbix) と[ソースコード](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v01/)を参照してください。

## <a name="make-r-based-visual-improvements"></a>R ベースのビジュアルの改善

ユーザーは入力テーブル内の列の順序を理解する必要があるため、ビジュアルはまだユーザー フレンドリとは言えません。

1. 入力フィールド `dataset` を次の 3 つのフィールド (ロール) に分割します: `Population`、`Number`、`Tooltips`

   ![CV01to02](./media/funnel-plot/diagram-one.PNG)

1. *capabilities.json* を編集して、`dataset` ロールを 3 つの新しいロールに置き換えるか、または [capabilities.json](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v02/capabilities.json) をダウンロードします。

   各入力フィールドの名前、種類、ツールヒント、および最大列数が定義されているセクション `dataRoles` および `dataViewMappings` を更新する必要があります。

   ![前と後](./samples/funnel-plot/chapter-3/funnel-r-visual-v02/capabilities-before-vs-after.png)
   
   詳細については、[機能](./capabilities.md)に関する記事を参照してください。

1. `dataset` ではなく、`Population`、`Number`、および `Tooltips` を入力データフレームとしてサポートするように *script.r* を編集するか、または [script.r](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v02/script.r) をダウンロードします。

   ![スクリプト](./samples/funnel-plot/chapter-3/funnel-r-visual-v02/script-r-before-vs-after.png)

   > [!TIP]
   > R スクリプト内の変更をたどるには、コメント ブロックを検索します。 
   > 
   > ```r
   > #RVIZ_IN_PBI_GUIDE:BEGIN: Added to enable visual fields
   > ...
   > #RVIZ_IN_PBI_GUIDE:END: Added to enable visual fields
   > 
   > #RVIZ_IN_PBI_GUIDE:BEGIN: Removed to enable visual fields 
   > ...
   > #RVIZ_IN_PBI_GUIDE:BEGIN: Removed to enable visual fields
   > ```

1. `pbiviz package` コマンドを使用してビジュアルを再パッケージ化してから、それを Power BI にインポートしてみてください。

> [!NOTE]
> ダウンロードについては、[PBIX](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelPlot_RCustomVisual.pbix) と[ソースコード](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v02)を参照してください。

## <a name="add-user-parameters"></a>ユーザー パラメーターを追加する

1. UI からの内部パラメーターを含むビジュアル要素の色とサイズをユーザーが制御できるようにするための機能を追加します。

   ![右側のバージョンにオプションが追加された 2 つのバージョンのツール ウィンドウを表示するスクリーンショット。](./media/funnel-plot/diagram-two.PNG)

1. *capabilities.json* を編集して、`objects` セクションを更新します。 ここでは、各パラメーターの名前、ツールヒント、および種類を定義すると共に、パラメーターを複数のグループに分割することも決定します (この場合は 3 つのグループ)。

   [capabilities.json](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/capabilities.json) をダウンロードします。詳細については、[オブジェクトのプロパティ](./objects-properties.md)に関するページを参照してください。

   ![capabilities](./samples/funnel-plot/chapter-3/funnel-r-visual-v03/capabilities-before-after.PNG)

1. *src/settings.ts* の編集を行って、[こちらの settings.ts](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/src/settings.ts) をミラーリングします。 このファイルは TypeScript で記述されています。  

   ここでは、次に示すコードの 2 つのブロックが追加されていることがわかります。
   - プロパティ値を保持する新しいインターフェイスを宣言する
   - メンバー プロパティと既定値を定義する

   ![設定](./samples/funnel-plot/chapter-3/funnel-r-visual-v03/settings-ts-before-after.PNG)

1. *script.r* の編集を行って、[こちらの script.r](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/script.r) をミラーリングします。 これにより、ユーザー パラメーターごとに `if.exists` 呼び出しを追加することで、UI のパラメーターのサポートが追加されます。

   > [!TIP]
   > R スクリプト内の変更をたどるには、次のコメントを検索します。
   >
   > ```r
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Added to enable user parameters
   >  ...
   > #RVIZ_IN_PBI_GUIDE:END:Added to enable user parameters
   >
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Removed to enable user parameters 
   >  ...
   > #RVIZ_IN_PBI_GUIDE:END:Removed to enable user parameters
   > ```

   ![スクリプトの前と後](https://raw.githubusercontent.com/microsoft/PowerBI-visuals/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/script_r_before_after_1.png)

   パラメーターを UI に公開しないように決定することもできます。  

1. `pbiviz package` コマンドを使用してビジュアルを再パッケージ化してから、それを Power BI にインポートしてみてください。

> [!NOTE]
> ダウンロードについては、[PBIX](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelPlot_RCustomVisual.pbix) と[ソースコード](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/)を参照してください。

> [!TIP]
> ここでは、複数の型 (ブール値、数値、文字列、および色) のパラメーターをすべて一度に追加しました。 シンプルなケースとして、単一パラメーターの追加方法については、[こちらの例](https://github.com/Microsoft/PowerBI-visuals/blob/master/RVisualTutorial/PropertiesPane.md)を参照してください。 

## <a name="convert-visual-to-rhtml-based-visual"></a>ビジュアルを RHTML ベースのビジュアルに変換する

結果として得られるビジュアルは PNG ベースのものであるため、マウス ホバーに応答しない、拡大表示することができないなどの制限があります。そのため、これを HTML ベースのビジュアルに変換する必要があります。 R を利用した空の HTML ベースのビジュアル テンプレートを作成して、PNG ベースのプロジェクトからいくつかのスクリプトをコピーします。

1. 次のコマンドを実行します。

   ```bash
   pbiviz new funnel-visual-HTML -t rhtml
   cd funnel-visual-HTML
   npm install 
   pbiviz package
   ```

1. *capabilities.json* を開き、`"scriptOutputType":"html"` 行をメモします。

1. *dependencies.json* を開き、一覧表示されている R パッケージの名前をメモします。

1. *script.r* を開き、その構造をメモします。 それは、外部入力が使用されていないため、RStudio で開いて実行することができます。 

   これにより *out.html* が作成され、保存されます。 自己完結型 (外部の依存関係なし) であるこのファイルでは、HTML ウィジェット内のグラフィックスが定義されます。 

   > [!IMPORTANT]
   > `htmlWidgets` ユーザーを対象として、[r_files フォルダー](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/r_files)には、`plotly` オブジェクトまたは `widget` オブジェクトを自己コンテンツ HTML に変換するのに役立つ R ユーティリティが用意されています。 
   > 
   > R を利用したこのバージョンのビジュアルでは、(以前の種類のビジュアルとは異なって) `source` コマンドもサポートされており、自分のコードを読みやすくすることができます。   
 
1. *capabilities.json* を前の手順からの *capabilities.json* に置き換えるか、または [capabilities.json](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/capabilities.json) をダウンロードします。

   必ず次のようにしてください。

   `"scriptOutputType": "html"`

1. 最新バージョンの *script.r* をテンプレートからの *script.r* にマージするか、または [script.r](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/script.r) をダウンロードします。

   新しいスクリプトでは、`plotly` パッケージを使用して、**ggplot** オブジェクトが **plotly** オブジェクトに変換され、さらに `htmlWidgets` パッケージを使用してそれが HTML ファイルに保存されます。 

   ユーティリティ関数の大部分は [_r_files/utils.r_](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/r_files/utils.r) に移動され、`generateNiceTooltips` 関数は、**plotly** オブジェクトの外観用に追加されます。

   ![1](./samples/funnel-plot/chapter-4/RHTML-v01/script-before-after-1.PNG)
   
   ![2](./samples/funnel-plot/chapter-4/RHTML-v01/script-before-after-2.PNG)

   > [!TIP]
   > R スクリプト内の変更をたどるには、次のコメントを検索します。
   > 
   > ```r
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Added to create HTML-based 
   >  ...
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Added to create HTML-based
   >
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Removed to create HTML-based  
   > ...
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Removed to create HTML-based
   > ```

1. 最新バージョンの *dependencies.json* をテンプレートからの *dependencies.json* にマージして、新しい R パッケージ依存関係を含めるか、または [dependencies.json](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/dependencies.json) をダウンロードします。

1. *src/settings.ts* を前の手順と同じ方法で編集します。

1. `pbiviz package` コマンドを使用してビジュアルを再パッケージ化してから、それを Power BI にインポートしてみてください。

> [!NOTE]
> ダウンロードについては、[PBIX とソースコード](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01)を参照してください。

## <a name="build-additional-examples"></a>追加の例を作成する

1. 次のコマンドを実行して、空のプロジェクトを作成します。 

   ```bash
   pbiviz new example -t rhtml
   cd example
   npm install 
   pbiviz package
   ```

1. この [ショーケース](http://www.htmlwidgets.org/showcase_networkD3.html)からコードを取得し、強調表示されている変更を行います。

   ![強調表示されている変更](./media/funnel-plot/diagram-three.PNG)

1. ご自分のテンプレートの *script.r* を置き換えて、`pbiviz package` を再度実行します。 これで、Power BI レポートにビジュアルが含まれるようになりました。

## <a name="tips-and-tricks"></a>ヒントとコツ

* *pbiviz.json* を編集することで、**バージョン**、**電子メール**、**名前**、**ライセンスの種類** などの正しいメタデータを格納することを開発者にお勧めします。

   > [!IMPORTANT]
   > **guid** フィールドは、ビジュアルの一意の識別子です。 ビジュアルごとに新しいプロジェクトを作成する場合は、GUID もそれぞれ異なります。 それが同じになるのは、新しいビジュアルに古いプロジェクトをコピーして使用する場合のみとなりますが、これを行うべきではありません。

* [*assets/icon.png*](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/assets/icon.png) を編集して、ビジュアル用の一意のアイコンを作成します。 

* ご利用の Power BI レポートと同じデータを使用して RStudio で R コードをデバッグするには、R スクリプトの先頭に以下を追加します (`fileRda` 変数を編集します)。

   ```r
   #DEBUG in RStudio
   fileRda = "C:/Users/yourUserName/Temp/tempData.Rda"
   if(file.exists(dirname(fileRda)))
   {
     if(Sys.getenv("RSTUDIO")!="")
       load(file= fileRda)
     else
       save(list = ls(all.names = TRUE), file=fileRda)
   }
   ```

   これにより、Power BI レポートからの環境が保存され、RStudio に読み込まれます。 

* [GitHub](https://github.com/Microsoft?utf8=%E2%9C%93&q=PowerBI&type=&language=R) で入手できるコードを使用すれば、R を利用したビジュアルをゼロから開発する必要はありません。 テンプレートとして使用するビジュアルを選択し、そのコードを新しいプロジェクトにコピーすることができます。

   たとえば、[スプライン カスタム ビジュアル](https://github.com/Microsoft/PowerBI-visuals-spline)を使用してみてください。

* 各 R ビジュアルでは、その入力テーブルに `unique` 演算子が適用されます。 複数の同一の行が削除されるのを防ぐには、一意の ID を持つ追加の入力フィールドを追加し、R コードでそれを無視することを検討してください。   

* Power BI アカウントを持っている場合は、`pbiviz package` コマンドを使用して再パッケージ化するのではなく、Power BI サービスを使用してビジュアルを[即座に](./develop-circle-card.md)開発してください。

### <a name="html-widgets-gallery"></a>HTML ウィジェット ギャラリー
次のビジュアルで使用するために、[ HTML ウィジェット ギャラリー](http://gallery.htmlwidgets.org/)でビジュアルを探索します。 作業を簡単にするために、20 を超える対話型の HTML ビジュアを含む[ビジュアル プロジェクト リポジトリ](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/multipleRHTML)を作成し、その中から選択できるようにしました。

> [!TIP]
> html ウィジェットを切り替えるには、 **[形式]**  >  **[設定]**  >  **[型]** の順に使用します。 [この PBIX ファイル](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/multipleRHTML/assets/sample.pbix)を使用して試してみてください。 

#### <a name="to-use-a-sample-for-your-visual"></a>ビジュアルに対してサンプルを使用するには

1. フォルダー全体をダウンロードします。
1. *script.r* と *dependencies.json* を編集して、ウィジェットを 1 つだけを保持します。
1. *capabilities.json* と *settings.ts* を編集して、`Type` セレクターを削除します。
1. *visual.ts* 内で、`const updateHTMLHead: boolean = true;` を `false` に変更します (*パフォーマンス向上のため)*
1. *pbiviz.json* 内のメタデータを変更します。最も重要なのは `guid` フィールドです。
1. 再パッケージ化し、必要に応じて、ビジュアルのカスタマイズを続けます。 

![この記事の前半で説明した 6 つのウィジェットを表示するスクリーンショット。](./media/funnel-plot/diagram-four.PNG)

![スクリーンショットは、この記事の前半で説明した追加の 6 つのウィジェットを表示しています。](./media/funnel-plot/diagram-five.PNG)

> [!NOTE]
> このプロジェクトのすべてのウィジェットがサービスでサポートされているわけではありません。

## <a name="next-steps"></a>次の手順

詳細については、[Power BI の円形カード視覚化の開発](./develop-circle-card.md)および [R ビジュアル](../../visuals/service-r-visuals.md)に関する追加の Power BI チュートリアルを参照してください。

[Office ストア (ギャラリー)](https://store.office.com/appshome.aspx?ui=en-US&rs=en-US&ad=US&clickedfilter=OfficeProductFilter%3aPowerBI&productgroup=PowerBI) に対して[ビジュアルを開発して送信する](https://powerbi.microsoft.com/documentation/powerbi-developer-office-store/)方法を学習します。その他の例については、[R スクリプト ショーケース](https://community.powerbi.com/t5/R-Script-Showcase/bd-p/RVisuals)を参照してください