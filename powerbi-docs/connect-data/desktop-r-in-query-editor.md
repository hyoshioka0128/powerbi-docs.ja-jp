---
title: Power Query エディターで R を使用する
description: Power BI Desktop Power Query エディターで R を使用し、高度な分析を行う
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 01/28/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: c70422cc9f02566612cf67a9a5ee1b1b4b033063
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411105"
---
# <a name="use-r-in-power-query-editor"></a>Power Query エディターで R を使用する

[R 言語](https://mran.microsoft.com/documents/what-is-r)は、多くの統計学者、データ科学者、データ アナリストが使用する強力なプログラミング言語です。 Power BI Desktop の Power Query エディターで R を使用し、次のことができます。

* データ モデルの準備。

* レポートの作成。

* データ クレンジング、高度なデータ整形、データセット分析の実行。これには、欠損データの補完、予測、クラスタリングなどが含まれます。  

## <a name="install-r"></a>R をインストールする

R は [Revolution R Open ダウンロード ページ](https://mran.revolutionanalytics.com/download/)と [CRAN リポジトリ](https://cran.r-project.org/bin/windows/base/)から無料でダウンロードできます。

## <a name="install-mice"></a>mice をインストールする

前提条件として、R 環境に [mice ライブラリ](https://www.rdocumentation.org/packages/mice/versions/3.5.0/topics/mice)をインストールする必要があります。 mice がないと、サンプル スクリプト コードは正常に動作しません。 mice パッケージには、足りないデータを処理するメソッドが実装されています。

mice ライブラリをインストールするには:

1. R.exe プログラムを起動します (たとえば、C:\Program Files\Microsoft\R Open\R-3.5.3\bin\R.exe)。  

2. R プロンプトから install コマンドを実行します。

   ``` 
   install.packages('mice') 
   ```

## <a name="use-r-in-power-query-editor"></a>Power Query エディターで R を使用する

Power Query エディターで R を使用する方法を示すために、.csv ファイルに含まれているサンプル株式市場データセットを使用して次の手順を行います。

1. [EuStockMarkets_NA.csv ファイルをダウンロードします](https://download.microsoft.com/download/F/8/A/F8AA9DC9-8545-4AAE-9305-27AD1D01DC03/EuStockMarkets_NA.csv)。 ファイルを保存した場所を忘れないようにします。

1. Power BI Desktop にファイルを読み込みます。 **[ホーム]** タブで **[データを取得]** 、 **[テキスト/CSV]** の順に選択します。

   ![[テキスト/CSV] を選択する](media/desktop-r-in-query-editor/r-in-query-editor_1.png)

1. EuStockMarkets_NA.csv ファイルを選択し、 **[開く]** を選択します。 CSV データが **[Text/CSV file]\(テキスト/CSV ファイル\)** ダイアログ ボックスに表示されます。

   ![CSV ファイルを選択する](media/desktop-r-in-query-editor/r-in-query-editor_2.png)

1. **[読み込み]** を選択し、ファイルからデータを読み込みます。 Power BI でデータが読み込まれると、 **[フィールド]** ウィンドウに新しいテーブルが表示されます。

   ![[フィールド] ペインのデータ](media/desktop-r-in-query-editor/r-in-query-editor_3.png)

1. Power Query エディターを開くには、 **[ホーム]** リボンから **[クエリを編集]** を選択します。

   ![[クエリの編集] を選択する](media/desktop-r-in-query-editor/r-in-query-editor_4.png)

1. **[変換]** タブから、 **[R スクリプトを実行する]** を選択します。 **[R スクリプトを実行する]** エディターが表示されます。 15 行目と 20 行目のデータが欠損しています。この画像に表示されない他の行にも欠損しているデータがあります。 次の手順からは、R によってこれらの行が自動的に補完されるしくみがわかります。

   ![[R スクリプトを実行する] を選択する](media/desktop-r-in-query-editor/r-in-query-editor_5d.png)

1. この例の場合、 **[R スクリプトを実行する]** ウィンドウの **[スクリプト]** ボックスに次のスクリプト コードを入力します。 *&lt;Your File Path&gt;* は、ローカル ファイル システム上の EuStockMarkets_NA.csv のパス (たとえば、C:/Users/John Doe/Documents/Microsoft/EuStockMarkets_NA.csv) に置き換えます。

    ```r
       dataset <- read.csv(file="<Your File Path>/EuStockMarkets_NA.csv", header=TRUE, sep=",")
       library(mice)
       tempData <- mice(dataset,m=1,maxit=50,meth='pmm',seed=100)
       completedData <- complete(tempData,1)
       output <- dataset
       output$completedValues <- completedData$"SMI missing values"
    ```

    > [!NOTE]
    > フィルターが適用された新しいデータセットを適切に作成するには、*output* という名前の変数を場合によっては上書きする必要があります。

7. **[OK]** を選択します。 Power Query エディターにデータ プライバシーに関する警告が表示されます。

   ![データ プライバシーに関する警告](media/desktop-r-in-query-editor/r-in-query-editor_6.png)
8. 警告メッセージ内で、 **[続行]** を選択します。 **[プライバシー レベル]** ダイアログ ボックスが表示されたら、R スクリプトが Power BI サービスで正しく動作するよう、すべてのデータ ソースを **[パブリック]** に設定します。 

   ![[プライバシー レベル] ダイアログ ボックス](media/desktop-r-in-query-editor/r-in-query-editor_7.png)

   プライバシー設定とその意味に関する詳細については、「[Power BI Desktop のプライバシー レベル](../admin/desktop-privacy-levels.md)」を参照してください。

 9. **[保存]** を選択してスクリプトを実行します。 

   **[フィールド]** ウィンドウに **completedValues** という新しい列が表示されます。 この列では、行 15 や行 18 行など、いくつかの行でデータ要素が不足しています。 次のセクションでは、R がデータ要素の不足を処理するしくみを確認します。

   わずか 5 行の R スクリプトと予測モデルによって、Power Query エディターでは不足値が埋められました。

## <a name="create-visuals-from-r-script-data"></a>R スクリプト データからビジュアルを作成する

R スクリプト コードと mice ライブラリで不足値を補うしくみを確認できるビジュアルをこれで作成できます。

![R スクリプト ビジュアル](media/desktop-r-in-query-editor/r-in-query-editor_8a.png)

完成したすべてのビジュアルを 1 つの Power BI Desktop .pbix ファイルに保存し、データ モデルとその R スクリプトを Power BI サービスで使用できます。

> [!NOTE]
> これらの手順をすべて完了した [.pbix ファイルをダウンロード](https://download.microsoft.com/download/F/8/A/F8AA9DC9-8545-4AAE-9305-27AD1D01DC03/Complete%20Values%20with%20R%20in%20PQ.pbix)できます。

Power BI サービスに .pbix ファイルをアップロードしたら、サービス データ更新と更新されたビジュアルを有効にするために追加の手順を行う必要があります。  

* **データセットの定期更新を有効にする**:データセットと R スクリプトが含まれるブックの定期更新を有効にする方法については、「[スケジュールされた更新の構成](refresh-scheduled-refresh.md)」を参照してください。 この記事には、個人のゲートウェイに関する情報も含まれています。

* **個人用ゲートウェイをインストールする**:ファイルと R が配置されているコンピューターに個人用ゲートウェイがインストールされている必要があります。 Power BI サービスではそのブックにアクセスされ、更新されたすべてのビジュアルが再レンダリングされます。 詳細については、「[Power BI で個人用ゲートウェイを使用する](service-gateway-personal-mode.md)」を参照してください。

## <a name="limitations"></a>制限事項

Power Query エディターで作成された R スクリプトを含むクエリにはいくつかの制限事項があります。

* すべての R データ ソース設定が **[パブリック]** に設定されている必要があります。 Power Query エディターのクエリの他のすべての手順も、パブリックにする必要があります。 

   データ ソース設定にアクセスするには、Power BI Desktop で、 **[ファイル]** 、 **[オプションと設定]** 、 **[データ ソース設定]** の順に選択します。

   ![データ ソース設定を選択する](media/desktop-r-in-query-editor/r-in-query-editor_9.png)

   **[データ ソース設定]** ダイアログ ボックスで、1 つまたは複数のデータ ソースを選択し、 **[アクセス許可の編集]** を選択します。 **[プライバシー レベル]** を **[パブリック]** に設定します。

   ![[データ ソース設定] ダイアログ ボックス](media/desktop-r-in-query-editor/r-in-query-editor_10.png)  
  
* R のビジュアルやデータセットの更新日程を設定するには、定期更新を有効にし、ブックと R が含まれるコンピューターに個人用ゲートウェイをインストールする必要があります。 

R とカスタム クエリを使用し、さまざまなことを実行できます。 探索しながらデータの形を決め、好みの方法で表示する

## <a name="next-steps"></a>次のステップ

* [R の概要](https://mran.microsoft.com/documents/what-is-r) 

* [Power BI Desktop で R スクリプトを実行する](desktop-r-scripts.md) 

* [Power BI で外部 R IDE を使用する](desktop-r-ide.md) 

* [Power BI サービスで R パッケージを使用してビジュアルを作成する](service-r-packages-support.md)
