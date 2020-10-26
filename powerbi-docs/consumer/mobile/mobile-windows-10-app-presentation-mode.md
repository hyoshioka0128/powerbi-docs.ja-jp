---
title: Surface Hub と Windows 10 でプレゼンテーション モードを表示する - Power BI
description: Surface Hub で Power BI レポートを表示する方法と、Windows 10 デバイスで Power BI のダッシュボード、レポート、タイルを全画面表示モードで表示する方法について説明します。
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 08/12/2020
ms.author: painbar
ms.openlocfilehash: a47af4b96e80508a6ea21de2d8d3e0b40f907d8d
ms.sourcegitcommit: 383d87841d2509131fac7cc02c5c37c6a868144f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/14/2020
ms.locfileid: "92025935"
---
# <a name="view-reports-and-dashboards-in-presentation-mode-on-surface-hub-and-windows-10-devices"></a>Surface Hub と Windows 10 デバイスで、プレゼンテーション モードでレポートとダッシュボードを表示する
Windows 10 デバイスと Surface Hub で、プレゼンテーション モードを使用し、レポートとダッシュボードを全画面表示できます。 プレゼンテーション モードは、会議やカンファレンスで、またはオフィスの専用プロジェクターで Power BI を表示する場合や、小さい画面上の領域を最大化するためだけにも役立ちます。

![全画面表示モードでのレポート](./media/mobile-windows-10-app-presentation-mode/power-bi-presentation-mode-2.png)

プレゼンテーション モードの場合:
* すべての "クロム" (ナビゲーション バーやメニュー バーなど) は表示されなくなり、レポート内のデータに集中しやすくなります。
* 操作ツール バーを使用できるようになり、データと対話したり、プレゼンテーションを制御したりできます。
* ページ、ブックマーク、またはページとブックマークの両方を自動的に順番に表示する、スライドショーを再生できます。

>[!NOTE]
>**Windows 10 Mobile を使用するスマートフォン**に対する Power BI モバイル アプリのサポートは、2021 年 3 月 16 日に廃止されます。 [詳細情報](/legal/powerbi/powerbi-mobile/power-bi-mobile-app-end-of-support-for-windows-phones)

## <a name="use-presentation-mode"></a>プレゼンテーション モードを使用する
Power BI モバイル アプリで **[全画面表示]** アイコンをタップすると、全画面表示モードに切り替わります。
![[全画面表示] アイコン](././media/mobile-windows-10-app-presentation-mode/power-bi-full-screen-icon.png) アプリのクロムが消え、画面の下部または右側と左側 (画面のサイズによって変わります) に操作ツール バーが表示されます。

[![サイド ツール バーが表示された全画面表示モードのレポート](./media/mobile-windows-10-app-presentation-mode/power-bi-presentation-mode-toolbar.png)](./media/mobile-windows-10-app-presentation-mode/power-bi-presentation-mode-toolbar-expanded.png#lightbox)

このツール バーからタップして、次の操作を実行できます。

| アイコン | アクション |
|------|--------|
|![[戻る] アイコン](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-back-icon.png)|前のページに**戻ります**。 アイコンを長押しすると、階層リンク ウィンドウがポップアップ表示され、レポートやダッシュボードを含むフォルダーに移動できます。|
|![改ページ アイコン](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-pages-icon.png)|プレゼンテーション内のレポートの別のページに**ページを切り替えます**。|
|![ブックマーク アイコン](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-bookmarks-icon.png)|**ブックマークを適用**して、そのブックマークによってキャプチャされるデータの特定のビューを表示します。 個人用とレポートの両方のブックマークを適用できます。|
|![インク アイコン](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-ink-icon.png)|Surface ペンを使ってレポート ページ上に描画したり、注釈を付けたりするときの**インクの色を選択します**。|
|![消しゴム アイコン](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-eraser-icon.png)|Surface ペンを使ってレポート ページ上に描画したり、注釈を付けたりするために作成した**インク マークを消します**。          |
|![リセット アイコン](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-reset-icon.png)|**既定のビューにリセット**し、プレゼンテーション中に行ったすべてのフィルター、スライサー、またはその他のデータ ビューの変更をクリアします。|
|![[共有] アイコン](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-share-icon.png)|プレゼンテーション ビューの画像を同僚と**共有します**。 この画像には、プレゼンテーション中に Surface ペンで書いたすべての注釈が含まれます。|
|![アイコンを更新する](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-refresh-icon.png)|レポートを**更新します**。|
|![[再生] アイコン](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-play-icon.png)|**スライドショーを再生します**。操作バーを非表示にして、スライドショーを開始します。 セレクターを使用すると、ページ、ブックマーク、またはページとブックマークの両方の間での自動切り替えを選択できます。 既定では、スライドショーでは 30 秒ごとに自動的にページが切り替わります。 これらの設定は、[ **[設定] > [オプション]** ](#slideshow-settings) で変更できます。 スライドショーについての[詳細情報](#slideshows)を参照してください|
|![全画面表示モードを終了](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-exit-full-screen-icon.png)|プレゼンテーション モードを**終了します**。|
|![[検索] アイコン](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-search-icon.png)|Power BI 内の他の成果物を**検索します**。|

ツール バーを切り離し、画面上の任意の場所にドラッグ アンド ドロップできます。 これは大きな画面の場合に便利です。レポートの特定の領域に集中的に取り組むとき、その隣にツールを配置します。 ツール バーを指で触れ、レポート キャンバスまでスワイプします。

[![プレゼンテーション モードのレポートと切り離されたツール バー](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-drag-toolbar-2.png)](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-drag-toolbar-2-expanded.png#lightbox)

## <a name="slideshows"></a>スライドショー

スライドショーを再生して、自動的にプレゼンテーションを順番に表示することができます。 ページ、ブックマーク、またはページとブックマークの両方を順番に表示するようにスライドショーを設定できます。 スライドショーの間に、[ページの自動更新](../../create-reports/desktop-automatic-page-refresh.md)が設定されているレポート ページは、構成どおりに自動的に更新され、最新のデータが常に表示されます。

操作ツール バーの **[再生]** ボタンを選択すると、スライドショーが開始します。 コントローラーが表示され、スライドショーを一時停止したり、再生されている内容 (ページ、ブックマーク、またはページとブックマークの両方) を変更したりできます。

![スライドショーのセレクターのスクリーンショット](././media/mobile-windows-10-app-presentation-mode//power-bi-windows-10-slideshow-selector.png)

 コントローラーには、現在表示されているビュー (ページまたはブックマークとページ) の名前が表示されます。 上の図では、**Sales** という名前のレポート内で、現在 **Sales Performance** ページ上の **Asia Pacific** ブックマークが表示されていることを確認できます。

既定では、スライドショーは 30 秒ごとに 1 回のペースでページのみが切り替わります。 [スライドショーの設定](#slideshow-settings)で既定の動作を変更できます。


### <a name="auto-play-a-slideshow-on-startup"></a>スタートアップ時にスライドショーを自動再生する

アプリが起動されるたびにスライドショーの再生を自動的に開始するように、Power BI モバイル アプリを設定できます。 このオプションは、手動で介入せずに、パブリック表示でレポートを実行するキオスクのようなエクスペリエンスを作成する場合に便利です。 自動再生用のレポートの設定に関する詳細については、「[スライドショーの設定](#slideshow-settings)」を参照してください。

### <a name="slideshow-settings"></a>スライドショーの設定

既定では、スライドショーは 30 秒ごとに 1 回のペースでページのみが切り替わります。 この既定の動作を変更するには、次に示すように、 **[設定]、[オプション]** の順に移動します。 自動再生をオンにして、再生するレポートを選択することもできます。

1. [設定] アイコンを選択します。

1. [オプション] タブを開きます。

1. 必要に応じて、スライドショーで切り替える内容の既定の設定 (ページ、ブックマーク、またはその両方) と、スライドショーを切り替える頻度を変更します。

1. アプリの起動時にレポートの自動再生を開始する必要がある場合は、切り替えをオンにして、 **[レポートの選択]** を選択します。 アクセス権のあるレポートを検索することができます。

![スライドショーの設定のスクリーンショット](././media/mobile-windows-10-app-presentation-mode//power-bi-windows-10-slideshow-settings.png)

## <a name="next-steps"></a>次の手順
* [Power BI サービスから全画面表示モードでダッシュボードとレポートを表示する](../end-user-focus.md)
* わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。