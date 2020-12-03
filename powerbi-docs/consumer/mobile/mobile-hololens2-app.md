---
title: HoloLens 2 用の Power BI (プレビュー)
description: HoloLens 2 用 Power BI アプリでダッシュボードとレポートを表示します。
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 09/22/2020
ms.openlocfilehash: dffe3344fc10b0daceca629b5d5354f1b8419e81
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96414532"
---
# <a name="power-bi-for-hololens-2-preview"></a>HoloLens 2 用の Power BI (プレビュー)
HoloLens 2 用 Power BI アプリでは、Power BI のレポートとダッシュボードを物理的な環境に合わせて、3D のイマーシブなハンズフリー エクスペリエンスを作成できます。物理的な世界を移動しながら、必要なときに必要な場所で適切なデータを取得できます。

![浮動する Power B I レポートが表示されている HoloLens 2 のイメージ。](media/mobile-hololens2-app/power-bi-hololens2-floating-reports.png)

## <a name="get-the-power-bi-app-for-hololens-2"></a>HoloLens 2 用 Power BI アプリを取得する 

HoloLens 2 用 Power BI アプリは [Microsoft Store](https://go.microsoft.com/fwlink/?linkid=526478) から入手できます。

このアプリはシングル サインオンで動作します。つまり、HoloLens 2 デバイスに現在サインインしているユーザーの ID を使用して Power BI サービスの認証が行われます。

HoloLens 2 デバイスにアプリをインストールする方法の[詳細を確認してください](/hololens/holographic-store-apps)。

## <a name="open-the-power-bi-app-on-your-hololens-2"></a>HoloLens 2 で Power BI アプリを開く

**[スタート]** メニューを開き、Power BI アプリを選択します。 お気に入りのレポートとダッシュボードがすべて仮想ツールベルトに読み込まれた状態でアプリが開きます。それらはここから選択して表示できます。

## <a name="using-the-power-bi-app-for-hololens-2"></a>HoloLens 2 用 Power BI アプリを使用する

HoloLens 2 のハンド ジェスチャと視線追跡を使用して、Power BI コンテンツのサイズ変更、配置、および操作を行います。 HoloLens 2 の世界でオブジェクトを操作する方法の[詳細を確認してください](/hololens/hololens2-basic-usage)。

### <a name="access-reports-and-dashboards"></a>レポートとダッシュボードへのアクセス

レポートまたはダッシュボードにアクセスするには、それを仮想ツールベルトからつかみ出して、目的の場所に配置します。 アプリ ウィンドウをつかんで配置する方法の[詳細を確認してください](/hololens/hololens2-basic-usage#moving-holograms)。

レポートまたはダッシュボードを仮想ツールベルトに含めるには、お気に入りとしてマークする必要があります。 ツールベルトにレポートやダッシュボードがない場合、またはさらなるレポートやダッシュボードを追加する場合は、[Power BI サービス](../end-user-favorite.md)または [Power BI モバイル アプリ](mobile-apps-favorites.md)で、それらの項目をお気に入りとしてマークするだけです。 そうすると、HoloLens 2 の Power BI 仮想ツールベルトで使用できるようになります。

### <a name="resize-reports-and-dashboards"></a>レポートとダッシュボードのサイズを変更する

レポートまたはダッシュボードのサイズを変更するには、そのアプリ ウィンドウの隅に表示されるサイズ変更ハンドルをつかみ、必要に応じてサイズを調整します。 アプリ ウィンドウのサイズ変更の[詳細を確認してください](/hololens/hololens2-basic-usage#resizing-holograms)。

### <a name="position-reports-and-dashboards-in-space"></a>レポートとダッシュボードをスペースに配置する

レポートまたはダッシュボードをスペースに配置するには、そのタイトル バーを人差し指と親指でつまみ、離さないように手を目的の位置に動かします。 目的の場所に配置したら、指を離します。 アプリ ウィンドウの移動の[詳細を確認してください](/hololens/hololens2-basic-usage#moving-holograms)。

レポートまたはダッシュボードを目的の場所に配置すると、HoloLens 2 デバイスによってその場所が環境内に記憶されます。 次に同じ場所に移動すると、配置した項目がまったく同じ場所に表示されます。

### <a name="browse-report-pages"></a>レポート ページを参照する

各レポートには、ページ間を移動するために表示できるページ インデックスがあります。 ページ インデックスを表示または非表示にするには、レポート ウィンドウの右上隅にある **[Page Index]\(ページ インデックス\)** ボタンを選択します。

![HoloLens 2 用 Power B I のレポート ページ インデックスを示す画像](media/mobile-hololens2-app/power-bi-hololens2-browse-report-pages.png)

### <a name="open-reports-with-qr-codes"></a>QR コードを使用してレポートを開く

レポートの QR コードが作成されてアイテムに添付されている場合 (機器のデータがそのレポートに含まれている場合など) は、そのアイテム上の QR コードを確認するだけでレポートを開くことができます。

レポートの QR コードを作成する方法の[詳細を確認してください](../../create-reports/service-create-qr-code-for-report.md)。

### <a name="data-refresh"></a>データ更新

レポートとダッシュボードはアプリの使用中に更新されます。そのため、アプリの使用中に Power BI でデータが変更された場合は、表示しているレポートとダッシュボード内にその変更内容が反映されます。

## <a name="next-steps"></a>次のステップ

* [HoloLens 2 の基本操作](/hololens/hololens2-basic-usage)