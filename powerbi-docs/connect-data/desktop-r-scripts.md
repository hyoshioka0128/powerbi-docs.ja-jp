---
title: Power BI Desktop での R スクリプトの実行
description: Power BI Desktop での R スクリプトの実行
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 01/14/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 604e90cf2f2c1010559c70df67a6cd54ac08fa36
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96404550"
---
# <a name="run-r-scripts-in-power-bi-desktop"></a>Power BI Desktop での R スクリプトの実行

Power BI Desktop で R スクリプトを直接実行し、生成されたデータセットを Power BI Desktop データ モデルにインポートできます。

## <a name="install-r"></a>R をインストールする

Power BI Desktop で R スクリプトを実行するには、ローカル コンピューターに R をインストールする必要があります。 R はさまざまな場所から無料でダウンロードしてインストールできます (たとえば、[Microsoft R Application Network](https://mran.revolutionanalytics.com/download/) や [CRAN Repository](https://cran.r-project.org/bin/windows/base/) など)。 現在のリリースでは、インストール パスで Unicode 文字とスペース (空白文字) がサポートされています。

## <a name="run-r-scripts"></a>R スクリプトを実行する

Power BI Desktop でごくわずかの手順を実行するだけで、R スクリプトを実行してデータ モデルを作成できます。 このデータ モデルでは、レポートを作成して Power BI サービスで共有することができます。 Power BI Desktop の R スクリプトは、小数点 (.) とコンマ (,) が含まれる数値形式をサポートするようになりました。

### <a name="prepare-an-r-script"></a>R スクリプトを準備する

Power BI Desktop で R スクリプトを実行するには、ローカル R 開発環境でスクリプトを作成し、それが正常に動作することを確認します。

Power BI Desktop でスクリプトを実行するには、新しく、変更されていないワークスペースでスクリプトが正常に動作することを確認します。 この前提条件は、すべてのパッケージと依存関係を明示的に読み込んで実行する必要があることを意味しています。 `source()` を使用して、依存スクリプトを実行できます。

Power BI Desktop で R スクリプトを準備して実行するときに、いくつかの制限があります。

* データ フレームのみがインポートされるため、Power BI にインポートするデータは、データ フレームで表されていることを確認してください。
* 複合型とベクトル型の列はインポートされず、作成されたテーブルではエラー値に置換されます。
* `N/A` の値は、Power BI Desktop では `NULL` 値に変換されます。
* R スクリプトの実行は、30 分を超えるとタイムアウトします。
* ユーザー入力の待機中など、R スクリプトの対話的呼び出しでスクリプトの実行が停止します。
* R スクリプト内で作業ディレクトリを設定する場合は、作業ディレクトリへの相対パスではなく、完全パスを定義する "*必要*" があります。

### <a name="run-your-r-script-and-import-data"></a>R スクリプトを実行し、データをインポートする

R スクリプトを実行して Power BI Desktop にデータをインポートできるようになりました。

1. Power BI Desktop で、 **[データの取得]** を選択します。 **[その他]**  >  **[R スクリプト]** を選択し、 **[接続]** を選択します。

    ![R スクリプトへの接続、[その他] カテゴリ、[データの取得] ダイアログ ボックス、Power BI Desktop](media/desktop-r-scripts/r-scripts-1.png)

2. R がローカル コンピューターにインストールされている場合は、スクリプトをスクリプト ウィンドウにコピーし、 **[OK]** を選択します。 インストールされている最新バージョンが R エンジンとして表示されます。

    ![[R スクリプト] ダイアログ ボックス、Power BI Desktop](media/desktop-r-scripts/r-scripts-2.png)

3. **[OK]** を選択し、R スクリプトを実行します。 スクリプトが正常に実行されたら、生成されたデータ フレームを選択し、Power BI モデルに追加できます。

スクリプトの実行に使用する R インストールを制御できます。 R インストール設定を指定するには、 **[ファイル]**  >  **[オプションと設定]**  >  **[オプション]** を選択した後、 **[R スクリプト]** を選択します。 **[R スクリプトのオプション]** で、 **[検出された R ホーム ディレクトリ]** ドロップダウン リストに、現在の R インストールの選択肢が表示されます。 希望する R のインストールが表示されない場合は、 **[その他]** を選択した後、 **[R ホーム ディレクトリを設定します]** で目的の R インストール フォルダーを参照するか入力します。

![[R スクリプトオプション]、[オプション] ダイアログ ボックス、Power BI Desktop](media/desktop-r-scripts/r-scripts-4.png)

### <a name="refresh"></a>更新

Power BI Desktop で R スクリプトを更新できます。 R スクリプトを更新するとき、Power BI Desktop は Power BI Desktop 環境で R スクリプトをもう一度実行します。

## <a name="next-steps"></a>次のステップ

Power BI での R については、次の追加情報を参照してください。

* [R を使用した Power BI ビジュアルの作成](../create-reports/desktop-r-visuals.md)
* [Power BI で外部 R IDE を使用する](desktop-r-ide.md)
