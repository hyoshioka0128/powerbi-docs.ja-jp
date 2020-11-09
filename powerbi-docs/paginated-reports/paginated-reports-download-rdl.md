---
title: ページ分割されたレポートの .rdl をデータセットからダウンロードする
description: この記事では、Power BI サービスの共有データセットからダウンロードするという方法で、Power BI のページ分割されたレポートの .rdl を作成する方法について説明します。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: swgupt
ms.service: powerbi
ms.subservice: report-builder
ms.topic: how-to
ms.date: 10/15/2020
ms.openlocfilehash: c5c8f61a7253da46529a83276366044560d4f030
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2020
ms.locfileid: "93297631"
---
# <a name="download-the-rdl-for-a-power-bi-paginated-report-from-a-dataset"></a>Power BI のページ分割されたレポートの .rdl をデータセットからダウンロードする

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

この記事では、Power BI サービスの共有データセットからダウンロードするという方法で、Power BI のページ分割されたレポートの .rdl を作成する方法について説明します。 ページ分割されたレポートのファイル形式は *.rdl* です。 Power BI サービスのデータセットから直接 .rdl ファイルを作成できます。

1. マイ ワークスペースなど、任意のワークスペースのリスト ビューに移動します。 
1. データセットの **[その他のオプション (...)]** を選択し、 **[Download the .rdl]\(.rdl のダウンロード\)** を選択します。

    :::image type="content" source="media/paginated-reports-download-rdl/power-bi-paginated-download-rdl.png" alt-text="Power BI サービスの [Download the .rdl]\(.rdl のダウンロード\) のスクリーンショット。":::
1. Power BI レポート ビルダーの更新プログラムが必要であることを示すメッセージが表示されます。 **[Download]** を選択します。 

    :::image type="content" source="media/paginated-reports-download-rdl/power-bi-report-builder-updates.png" alt-text="Power BI レポート ビルダー更新プログラムのインストールのスクリーンショット。":::

    Power BI レポート ビルダーの最新バージョンをインストール済みであることがわかっている場合は、 **[既にこれらの更新はインストールしました]** を選択します。

1. Power BI レポート ビルダーのインストール プロセスを実行します。 

    1. **[Download]** を選択します。  
    2. **[ファイルを開く]** を選択し、Power BI レポート ビルダー セットアップ ウィザードの手順を実行します。

1. レポート ビルダーのインストールが完了したら、Power BI サービスに戻り、 **[Download the .rdl]\(.rdl のダウンロード\)** を選択します。

    :::image type="content" source="media/paginated-reports-download-rdl/power-bi-report-builder-finished-installing.png" alt-text="[Download the .rdl]\(.rdl のダウンロード\) ダイアログ ボックスのスクリーンショット。":::

1. ブラウザー ウィンドウで **[ファイルを開く]** を選択します。

    :::image type="content" source="media/paginated-reports-download-rdl/power-bi-paginated-open-file.png" alt-text="ブラウザーで [ファイルを開く] を選択したスクリーンショット。":::

1. Power BI レポート ビルダーが開き、自動生成されたタイトルと、 **Data Sources** フォルダー内の Power BI データセット .pbix ファイルが表示されます。 データ ソースの名前は Power BI データセットと同じです。

    :::image type="content" source="media/paginated-reports-download-rdl/power-bi-report-builder-design-canvas.png" alt-text="デザイン ビューの Power BI レポート ビルダーのスクリーンショット。":::

    デザイン画面には、[Power BI のページ分割されたレポートの 1 日](../learning-catalog/paginated-reports-online-course.md) ビデオベース コースへのリンクも表示されます。 ページ分割されたレポートの作成に慣れていない場合、短時間で習得するには、このコースをお勧めします。  これは、レポートのデザインを始めるときに削除できます。

    これで、ページ分割されたレポートの設計を開始する準備は完了です。
 
## <a name="next-steps"></a>次の手順 

- [Power BI Premium のページ分割されたレポートとは](paginated-reports-report-builder-power-bi.md)  
- [チュートリアル: ページ分割されたレポートを作成して Power BI サービスにアップロードする](paginated-reports-quickstart-aw.md)
- [ページ分割されたレポートを Power BI サービスに発行する](paginated-reports-save-to-power-bi-service.md)

