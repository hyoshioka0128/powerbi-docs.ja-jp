---
title: Power BI で R を利用した Power BI ビジュアルを使用する
description: Power BI で R を利用した Power BI ビジュアルを使用する
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 07/27/2018
LocalizationGroup: Create reports
ms.openlocfilehash: e2a610e12da1a91db6e22ab493ed39410ec1c091
ms.sourcegitcommit: a5e98bc86915f7bea6a0ab5df282683840e63d2c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2021
ms.locfileid: "97969744"
---
# <a name="use-r-powered-power-bi-visuals-in-power-bi"></a>Power BI で R を利用した Power BI ビジュアルを使用する

**Power BI Desktop** および **Power BI サービス** では、R の知識がなく、R スクリプトを作成しなくても、R を利用した Power BI ビジュアルを使用できます。 これにより、自分で R を学習したりプログラミングを実行したりしなくても、R ビジュアルの分析や視覚機能に加え、R スクリプトを活用できます。

R を利用した Power BI ビジュアルを使用するには、まず、使用したい R カスタム ビジュアルを、[**AppSource**](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals&page=1) ギャラリーで Power BI 用の **Power BI ビジュアル** を選択してダウンロードします。

![R ビジュアル 1a](media/desktop-r-powered-custom-visuals/powerbi-r-powered-custom-viz_1a.png)

以下のセクションでは、R を利用したビジュアルを **Power BI Desktop** で選択して読み込み、使用する方法について説明します。

## <a name="use-r-power-bi-visuals"></a>R を利用した Power BI ビジュアルを使用する

R を利用した Power BI ビジュアルを使用するには、各ビジュアルを **Power BI ビジュアル** ライブラリからダウンロードした後、このビジュアルを **Power BI Desktop** で他の種類のビジュアルと同様に使用します。 Power BI ビジュアルを取得する場合、オンラインの **AppSource** サイトからダウンロードする方法と、**Power BI Desktop** 内から参照して取得する方法の 2 つがあります。 

### <a name="get-power-bi-visuals-from-appsource"></a>AppSource から Power BI ビジュアルを取得する

オンラインの **AppSource** サイトからビジュアルを参照して選択する手順を以下に示します。

1. [https://appsource.microsoft.com](https://appsource.microsoft.com/) にある Power BI visuals ライブラリに移動します。 *[製品で絞り込む]* にある *[Power BI apps]* チェックボックスを選択して、 **[すべて表示]** リンクを選択します。

   ![R ビジュアル 2a](media/desktop-r-powered-custom-visuals/powerbi-r-powered-custom-viz_2a.png)

2. [Power BI visuals](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals&page=1) ライブラリ ページで、左側のウィンドウのアドインの一覧から、 **[Power BI visual]** を選択します。

   ![R ビジュアル 2b](media/desktop-r-powered-custom-visuals/powerbi-r-powered-custom-viz_2b.png)

3. 関心のある **ビジュアル** をギャラリーから選択すると、ビジュアルに関する説明のページに移動します。 **[今すぐ入手する]** ボタンを選択してダウンロードします。

   > [!NOTE]
    > **Power BI Desktop** で作成している場合は、ローカル コンピューターに R をインストールしておく必要があります。 ただし、ユーザーが R を利用したビジュアルを **Power BI サービス** に表示したい場合は、R をローカルにインストールしておく必要はありません。

   ![R ビジュアル 3a](media/desktop-r-powered-custom-visuals/powerbi-r-powered-custom-viz_3a.png)

   R は、R を利用した Power BI ビジュアルを **Power BI サービス** で使用するためにインストールする必要はありませんが、**Power BI Desktop** で使用する場合は、ローカル コンピューターにインストールする *必要があります*。 R は、次の場所からダウンロードできます。

   * [CRAN](https://cran.r-project.org/)
   * [MRO](https://mran.microsoft.com/)

4. ビジュアルがダウンロードされたら (ブラウザーから任意のファイルをダウンロードするのと似ています)、**Power BI Desktop** に移動し、 **[視覚化]** ペインの **[その他のオプション]** (...) をクリックして、 **[Import from file]\(ファイルからインポート\)** を選択します。

   ![R ビジュアル 4a](media/desktop-r-powered-custom-visuals/powerbi-r-powered-custom-viz_4a.png)
5. 次の図に示すように、カスタム ビジュアルのインポートに関する警告が表示されます。

   ![R ビジュアル 5](media/desktop-r-powered-custom-visuals/powerbi-r-powered-custom-viz_5.png)
6. ビジュアル ファイルが保存された場所に移動し、そのファイルを選択します。 **Power BI Desktop** のカスタム ビジュアルの拡張子は .pbiviz です。

   ![R ビジュアル 6](media/desktop-r-powered-custom-visuals/powerbi-r-powered-custom-viz_6.png)
7. Power BI Desktop に戻ると、 **[視覚化]** ウィンドウに新しいビジュアルの種類が表示されます。

   ![R ビジュアル 7](media/desktop-r-powered-custom-visuals/powerbi-r-powered-custom-viz_7.png)
8. 新しいビジュアルをインストールする (または、R を利用したカスタム ビジュアルを含むレポートを開く) と、**Power BI Desktop** によって、必要な R パッケージがインストールされます。

   ![R ビジュアル 8](media/desktop-r-powered-custom-visuals/powerbi-r-powered-custom-viz_8.png)

9. そこから、その他の **Power BI Desktop** ビジュアルと同様に、ビジュアルにデータを追加できます。 完了すると、完成したビジュアルがキャンバスに表示されます。 次のビジュアルでは、R を利用したビジュアル "**予測**" が、国連 (UN) の出生率予測 (左側のビジュアル) と共に使用されています。

    ![R ビジュアル 10](media/desktop-r-powered-custom-visuals/powerbi-r-powered-custom-viz_10.png)

    他の **Power BI Desktop** ビジュアルと同様、その R を利用したビジュアルを含むこのレポートを **Power BI サービス** に発行し、他のユーザーと共有することができます。

    新しいビジュアルが頻繁に追加されるため、ライブラリはこまめに確認してください。

### <a name="get-power-bi-visuals-from-within-power-bi-desktop"></a>**Power BI Desktop** 内から Power BI ビジュアルを入手する

1. **Power BI Desktop** 内から Power BI ビジュアルを入手することもできます。 **Power BI Desktop** の **[視覚化]** ウィンドウで省略記号 (...) をクリックして、 **[Import from marketplace]\(Marketplace からインポート\)** を選択します。

   ![R ビジュアル 4a](media/desktop-r-powered-custom-visuals/powerbi-r-powered-custom-viz_4a.png)

2. これを行うと、 **[Power BI ビジュアル]** ダイアログが表示され、スクロールして入手可能な Power BI ビジュアルを選択することができます。 名前で検索したり、カテゴリを選択したり、または単に利用可能なビジュアルをスクロールしていくこともできます。 準備ができたら、 **[追加]** を選択してカスタム ビジュアルを **Power BI Desktop** に追加します。

   ![R ビジュアル 12](media/desktop-r-powered-custom-visuals/powerbi-r-powered-custom-viz_12.png)

## <a name="contribute-r-powered-power-bi-visuals"></a>R を利用した Power BI ビジュアルを投稿する

レポートで使う作成したご自分用の R ビジュアルは、**Power BI ビジュアル ギャラリー** に投稿して世界に公開できます。 投稿は GitHub を通じて行われるため、その処理については次の場所で説明されています。

* [R を利用した Power BI ビジュアル ギャラリーに投稿する](https://github.com/PowerBi-Projects/PowerBI-visuals#building-r-powered-custom-visual-corrplot)

## <a name="troubleshoot-r-powered-power-bi-visuals"></a>R を利用した Power BI ビジュアルをトラブルシューティングする

R を利用した Power BI ビジュアルには、ビジュアルが適切に機能するために必要な特定の依存関係があります。 R を利用した Power BI ビジュアルの実行や読み込みが正常に行われないときは、通常、次のいずれかの問題があります。

* R エンジンがない
* ビジュアルの基になっている R スクリプトにエラーがある
* R パッケージが存在しないか期限切れである

以下のセクションでは、発生した問題に対処するために実行できるトラブルシューティング手順について説明します。

### <a name="missing-or-outdated-r-packages"></a>R パッケージが存在しないか期限が切れている

R パッケージが存在しないか、古くなっていると、R を利用したカスタム ビジュアルをインストールするときにエラーが発生する場合があります。これは次のいずれかの理由によるものです。

* R のインストールと R パッケージの間に互換性がありません
* ファイアウォール、ウイルス対策ソフトウェア、またはプロキシの設定により、R がインターネットに接続できません
* インターネットの接続が遅いか、インターネット接続に問題があります

Power BI チームはこれらの問題の軽減に懸命に取り組んでおり、次の Power BI Desktop には、これらの問題に対処する更新プログラムが組み込まれる予定です。 それまでは、次の手順を使って問題を軽減できます。

1. カスタム ビジュアルを削除してから、再インストールします。 これにより、R パッケージの再インストールが開始します。
2. R のインストールが最新ではない場合は、R のインストールをアップグレードした後、前の手順のようにカスタム ビジュアルを削除して再インストールします。

   サポートされている R のバージョンは、次の図のように、R を利用したカスタム ビジュアルの説明に表示されます。

     ![R ビジュアル 11](media/desktop-r-powered-custom-visuals/powerbi-r-powered-custom-viz_11.png)
    > [!NOTE]
    > 元の R のインストールを残しておき、Power BI Desktop とインストールした最新バージョンの関連付けのみを行うことができます。 **[ファイル] > [オプションと設定] > [オプション] > [R スクリプト]** の順に移動します。

3. R コンソールを使って、R パッケージを手動でインストールします。 このアプローチの手順は次のとおりです。

   a. R を利用したビジュアルのインストール スクリプトをダウンロードし、そのファイルをローカル ドライブに保存します。

   b. R コンソールから、次の手順を実行します。

      ```console
      source("C:/Users/david/Downloads/ScriptInstallPackagesForForecastWithWorkarounds.R")
      ```

   標準的な既定のインストール場所は次のとおりです。

   ```console
       c:\Program Files\R\R-3.3.x\bin\x64\Rterm.exe (for CRAN-R)
       c:\Program Files\R\R-3.3.x\bin\x64\Rgui.exe (for CRAN-R)
       c:\Program Files\R\R-3.3.x\bin\R.exe (for CRAN-R)
       c:\Program Files\Microsoft\MRO-3.3.x\bin\R.exe (for MRO)
       c:\Program Files\Microsoft\MRO-3.3.x\bin\x64\Rgui.exe (for MRO)
       c:\Program Files\RStudio\bin\rstudio.exe (for RStudio)
   ```

4. 前の手順でうまくいかない場合は、次のことを試してください。

   a. **R Studio** を使い、上の 3.b  (R コンソールからのスクリプト行の実行) に記載されている手順に従います。

   b. 前の手順でうまくいかない場合は、**R Studio** で **[ツール] > [グローバル オプション] > [パッケージ]** に移動し、 **[Use Internet Explorer library/proxy for HTTP]** (HTTP に Internet Explorer のライブラリ/プロキシを使用する) チェック ボックスをオンにして、上の手順の 3.b を 繰り返します。

## <a name="next-steps"></a>次のステップ

Power BI での R については、次の追加情報を参照してください。

* [Power BI ビジュアル ギャラリー](https://app.powerbi.com/visuals/)
* [Power BI Desktop での R スクリプトの実行](../connect-data/desktop-r-scripts.md)
* [Power BI Desktop で R ビジュアルを作成する](desktop-r-visuals.md)
* [Power BI で外部 R IDE を使用する](../connect-data/desktop-r-ide.md)
