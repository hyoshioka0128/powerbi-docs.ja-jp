---
title: 携帯電話用にダッシュボードを最適化する - Power BI
description: 携帯電話での表示専用に Power BI サービスでダッシュボードのカスタマイズしたビューを作成する方法について説明します。
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/18/2019
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: 93d94aadb8e7606fd6d55c463a2be88f87e48047
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2020
ms.locfileid: "83314859"
---
# <a name="optimize-a-dashboard-for-mobile-phones---power-bi"></a>携帯電話用にダッシュボードを最適化する - Power BI 
スマートフォンの縦モードでダッシュボードを開くと、ダッシュボードのタイルがすべて同じサイズで並んで表示されることに気付くでしょう。 Power BI サービスでは、ダッシュボードのカスタマイズされたビュー (特にスマートフォンの縦モード用) を作成できます。 スマートフォンのビューを作成した場合でも、電話を横向きにすると、サービスにレイアウトされているダッシュボードが表示されます。

モバイル デバイスでダッシュボードを表示する方法について情報をお探しの場合は 代わりにクイックスタート「[Power BI モバイル アプリでダッシュボードとレポートを調べる](../consumer/mobile/mobile-apps-quickstart-view-dashboard-report.md)」を参照してください。

> [!NOTE]
> Phone ビューを編集すると、スマートフォンでダッシュボードを見ているユーザーに対して、ビューの変更がリアルタイムで表示される場合があります。 たとえば、ダッシュボードの Phone ビューですべてのタイルの固定を解除すると、突然スマートフォン上のダッシュボードにタイルが 1 つもなくなります。 
> 
> 

## <a name="create-a-phone-view-of-a-dashboard"></a>ダッシュボードの Phone ビューを作成する
1. Power BI サービスでダッシュボードを開きます。
2. 右上隅の **[Web ビュー]** の横にある矢印を選んでから、 **[Phone ビュー]** を選びます。

    ![](media/service-create-dashboard-mobile-phone-view/power-bi-service-phone-view-dashboard.png)

    ダッシュボードの所有者でない場合、このオプションは表示されません。

    ![](media/service-create-dashboard-mobile-phone-view/power-bi-mobile-edit-phone-view-canvas.png)

    スマートフォン用ダッシュボードの編集ビューが開きます。 ここで、スマートフォンでの表示に合わせてタイルの固定解除、サイズ変更、並べ替えができます。 ダッシュボードの Web バージョンは変更されません。


1. タイルを選択してドラッグ、サイズ変更、または固定解除します。 タイルをドラッグすると、他のタイルが移動します。
   
    ![](media/service-create-dashboard-mobile-phone-view/power-bi-unpin-tile-phone-dashboard.png)
   
    固定解除されたタイルは [ピンを外したタイル] ウィンドウに移動し、再度追加しない限り、そのままです。
   
    ![](media/service-create-dashboard-mobile-phone-view/power-bi-mobile-edit-phone-view-post-edit.png)
2. 操作を取り消す場合は、 **[タイルのリセット]** を選ぶと、前のサイズと順序に戻ります。
   
    ![](media/service-create-dashboard-mobile-phone-view/power-bi-service-phone-view-reset-tiles.png)
   
    Power BI サービスでスマートフォン用編集ビューを開くだけで、スマートフォン上のタイルのサイズと形状がわずかに変更されます。 ダッシュボードをスマートフォン用編集ビューで開く前の正確な状態に戻すには、 **[タイルのリセット]** を選択します。
3. スマートフォン用ダッシュボードのレイアウト編集が完了したら、右上隅の **[Phone ビュー]** の横にある矢印を選んだ後、 **[Web ビュー]** を選びます。
   
    スマートフォン用レイアウトが自動的に保存されます。

## <a name="next-steps"></a>次のステップ
* [Power BI 電話アプリ用に最適化したレポートを作成する](desktop-create-phone-report.md)
* [任意のサイズに最適化されるレスポンシブ ビジュアルを作成する](../visuals/desktop-create-responsive-visuals.md)
* 他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
