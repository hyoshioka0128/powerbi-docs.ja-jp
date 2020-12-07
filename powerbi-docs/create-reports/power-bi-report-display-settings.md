---
title: Power BI レポートのページ表示設定
description: レポートのページ表示設定
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 05/29/2019
LocalizationGroup: Reports
ms.openlocfilehash: 9452a4a6340480bcb6c8b646c16125fe73f68235
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96393487"
---
# <a name="apply-page-display-settings-in-a-power-bi-report"></a>Power BI レポートにページ表示設定を適用する
レポートのレイアウトをピクセル パーフェクトに保つことは重要です。 しかし場合によってはこれは難しいことです。自身や同僚が縦横比やサイズの異なる画面でレポートを表示しなければならない場合があるためです。 

既定の表示レイアウトは **[ページに合わせる]** で、既定の表示サイズは **[16:9]** です。 異なる縦横比にロックしたり、別の方法でレポートの表示を調整したりするには、**_[ページ表示]_* _ 設定と _*_[ページ サイズ]_*_ 設定の 2 つのツールを利用できます。


<iframe width="560" height="315" src="https://www.youtube.com/embed/5tg-OXzxe2g" frameborder="0" allowfullscreen></iframe>


## <a name="where-to-find-page-view-settings-in-the-power-bi-service-and-power-bi-desktop"></a>Power BI サービスおよび Power BI Desktop でのページ表示設定の場所
ページ表示設定は Power BI サービスと Power BI Desktop の両方で使うことができますが、インターフェイスは若干異なります。 次のセクションでは、各 Power BI ツールでの表示設定の場所について説明します。

### <a name="in-power-bi-desktop"></a>Power BI Desktop の場合
レポート ビューで、_ *[表示]* * タブを選んで [ページ表示] 設定と [電話レイアウト] 設定を開きます。

  ![Desktop のページ表示設定](media/power-bi-report-display-settings/power-bi-desktop-view-settings.png)

### <a name="in-the-power-bi-service-apppowerbicom"></a>Power BI サービス (app.powerbi.com) の場合
Power BI サービスでは、レポートを開き、左上のメニュー バーから **[表示]** を選びます。

![サービスのページ表示設定](media/power-bi-report-display-settings/power-bi-change-page-view.png)

ページ表示設定は、[読み取りビューと編集ビュー](../consumer/end-user-reading-view.md)の両方で使用できます。 編集ビューでは、レポート所有者が個々のレポート ページにページ表示設定を割り当てることができ、それらの設定はレポートとともに保存されます。 同僚が読み取りビューでそのレポートを開くと、所有者の設定を使用してレポート ページが表示されます。 読み取りビューでは、同僚は *一部* の **ページ表示** 設定を変更できますが、レポートを終了するときに変更は保存されません。

## <a name="page-view-settings"></a>ページ表示の設定
ページ表示設定の最初のセットでは、ブラウザー ウィンドウを基準とした相対的なレポート ページの表示を制御できます。 次の中から選びます。

* **ページに合わせる** (既定値): ページに合わせて最適なサイズに内容が拡大/縮小されます
* **幅に合わせる**: ページの幅に収まるように内容が拡大/縮小されます
* **原寸大**: フル サイズで内容が表示されます

ページ表示設定の 2 番目のセットでは、レポート キャンバス上のオブジェクトの位置を制御できます。 次の中から選びます。

* **グリッド線の表示**: レポート キャンバスにオブジェクトを配置するときに役立つグリッド線を表示します。
* **グリッドに合わせる**: **[グリッド線の表示]** と併用して、レポート キャンバス上のオブジェクトを正確に配置して整列させます。 
* **オブジェクトをロック**: 移動したりサイズが変わったりしないように、キャンバス上のすべてのオブジェクトをロックします。
* **選択ウィンドウ**: **[選択]** ウィンドウにはキャンバス上のすべてのオブジェクトが一覧表示されます。 表示するものと非表示にするものを決定することができます。

    ![選択ウィンドウ](media/power-bi-report-display-settings/power-bi-selection-pane.png)



## <a name="page-size-settings"></a>ページ サイズ設定
![ページ サイズ変更設定](media/power-bi-report-display-settings/power-bi-page-size.png)

**ページ サイズ** 設定は、レポートの所有者のみ利用できます。 Power BI サービス (app.powerbi.com) の場合は、レポートを[編集ビュー](../consumer/end-user-reading-view.md)で開けることを意味します。 **ページ サイズ** 設定は **[視覚化]** ウィンドウにあり、レポート キャンバスの表示比率と実際のサイズ (ピクセル単位) を制御できます。   

* 4:3 の縦横比
* 16:9 の縦横比 (既定値)
* レター
* カスタム (ピクセル単位の高さと幅)

## <a name="next-steps"></a>次の手順
[Power BI Desktop のレポート ビュー](desktop-report-view.md)

[自分の Power BI レポートでページ表示とページ サイズ設定を変更する](../consumer/end-user-report-view.md)

[Power BI のレポート](../consumer/end-user-reports.md)で詳細を確認する

[Power BI サービスのデザイナー向けの基本的な概念](../fundamentals/service-basic-concepts.md)

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。
