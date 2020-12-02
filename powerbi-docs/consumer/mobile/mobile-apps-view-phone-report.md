---
title: 電話用に最適化された Power BI レポートを表示する
description: Power BI 電話アプリで表示するように最適化されたレポート ページとの対話について説明しています。
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 05/05/2020
ms.openlocfilehash: 6b2f8a7f7197d4027115266e8456cee01eb12a9f
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96397075"
---
# <a name="view-power-bi-reports-optimized-for-your-phone"></a>電話用に最適化された Power BI レポートを表示する

適用対象:

| ![iPhone](./media/mobile-apps-view-phone-report/ios-logo-40-px.png) | ![Android フォン](./media/mobile-apps-view-phone-report/android-logo-40-px.png) |
|:--- |:--- |
| iPhone |Android フォン |

スマートフォンで Power BI レポートを表示すると、レポートがスマートフォン向けに最適化されているかどうかが Power BI によって確認されます。 最適化されている場合、Power BI では、最適化されたレポートが縦表示で自動的に開きます。

![縦モードのレポート](./media/mobile-apps-view-phone-report/07-power-bi-phone-report-portrait.png)

電話用に最適化されたレポートが存在しない場合でもレポートは開きますが、最適化されていない横長ビューです。 電話用に最適化されたレポートでも、電話を横向きにすると、レポートが元のレポート レイアウトの最適化されていないビューで開きます。 一部のページのみを最適化している場合、縦長ビューに、レポートを横長で使用できることを示すメッセージが表示されます。

![最適化されていないレポート ページ](./media/mobile-apps-view-phone-report/06-power-bi-phone-report-page-not-optimized.png)

Power BI レポートの他のすべての機能は、引き続き電話用に最適化されたレポートで機能します。 実行できることの詳細については、次を参照してください。

* [iPhone でのレポート](mobile-reports-in-the-mobile-apps.md)。 
* [Android フォンでのレポート](mobile-reports-in-the-mobile-apps.md)。

## <a name="filter-the-report-page-on-a-phone"></a>電話でレポート ページをフィルター処理する
電話用に最適化されたレポートにフィルターが定義されている場合、電話でレポートを表示するときに、これらのフィルターを使うことができます。 レポートは、Web 上のレポートに適用されているフィルターでフィルター処理されてからスマートフォン上で開きます。 ページにアクティブなフィルターがあることを示すメッセージが表示されます。 スマートフォンでフィルターを変更できます。

1. ページの下部にあるフィルター アイコン ![電話のフィルター アイコン](./media/mobile-apps-view-phone-report/power-bi-phone-filter-icon.png) をタップします。

2. 基本的または詳細なフィルター処理を使って、関心がある結果を表示します。
   
    ![Power BI 電話レポートの詳細フィルター](./media/mobile-apps-view-phone-report/power-bi-iphone-advanced-filter-toronto.png)

## <a name="cross-highlight-visuals"></a>ビジュアルをクロス強調表示する
縦表示のビジュアルのクロス強調表示は、Power BI サービスや横長ビューのスマートフォンの場合と同じように機能します。1 つのビジュアルでデータを選択すると、そのページの他のビジュアルの関連するデータが強調表示されます。

詳しくは、[Power BI のフィルターと強調表示について](../../create-reports/power-bi-reports-filters-and-highlighting.md)のページを参照してください。

## <a name="select-visuals"></a>ビジュアルを選択する
電話レポートで、ビジュアルを選択すると、そのビジュアルが強調表示され、フォーカスされて、キャンバスのジェスチャが無効になります。

ビジュアルが選択されている場合、ビジュアル内でスクロールなどの操作を実行できます。 ビジュアルを選択解除するには、ビジュアル領域外の任意の場所に触れるだけです。

## <a name="open-visuals-in-focus-mode"></a>フォーカス モードでビジュアルを開く
スマートフォンの場合、レポートにはフォーカス モードもあります。1 つのビジュアルを大きく表示したり、いろいろ試したりすることが簡単になります。

* 電話レポートで、ビジュアルの右上隅にある省略記号 **[...]** をタップし、 **[フォーカス モードに展開]** をタップします。
  
    ![フォーカス モードに展開](media/mobile-apps-view-phone-report/power-bi-phone-report-focus-mode.png)

フォーカス モードでの実行内容は、レポート キャンバスに持ち込まれます。その逆も可能です。 たとえば、ビジュアルの値を強調表示してから、レポート全体に戻ると、ビジュアルで強調表示した値にレポートがフィルター処理されます。

画面サイズの制限により、フォーカス モードでは、一部の操作のみ実行できます。

* ビジュアルに表示される情報に **ドリルダウン** します。 詳しくは、電話レポートの[ドリルダウンとドリルアップ](mobile-apps-view-phone-report.md#drill-down-in-a-visual)に関するページを参照してください。
* ビジュアル内の値を **並べ替え** ます。
* **[元に戻す]** :ビジュアルで使用した探索手順をクリアし、レポートの作成時に設定された定義に戻します。
  
    ビジュアルからすべての探索をクリアするには、省略記号 **[...]** **[元に戻す]** の順にタップします。
  
    ![元に戻す](media/mobile-apps-view-phone-report/power-bi-phone-report-revert-levels.png)
  
    レポート レベルで元に戻すことができます。試しに実行したことがすべてのビジュアルから消去されます。ビジュアル レベルで元に戻す場合、選択したビジュアルから試しに実行したことが消去されます。   

## <a name="drill-down-in-a-visual"></a>ビジュアルをドリルダウンする
ビジュアルで階層レベルが定義されている場合、ビジュアルに表示されている詳細情報にドリルダウンした後、ドリルアップして戻ることができます。 [ビジュアルへのドリルダウンの追加](../end-user-drill.md)は、Power BI サービスまたは Power BI Desktop で行います。

ドリルダウンには次のような種類があります。

### <a name="drill-down-on-a-value"></a>値でドリルダウン
1. ビジュアル内のデータ ポイントで長くタップします (タップしたまま押さえます)。
2. ツールヒントが表示されます。階層が定義されている場合、ツールヒント フッターにドリルダウンと上矢印が表示されます。
3. 下矢印をタップしてドリルダウンします。

    ![タップしてドリルダウン](media/mobile-apps-view-phone-report/report-drill-down.png)
    
4. 上矢印をタップしてドリルアップします。

### <a name="drill-to-next-level"></a>次のレベルにドリル
1. 電話のレポートでは、右上隅にある省略記号 **[...]** 、 **[フォーカス モードに展開]** の順にタップします。
   
    ![フォーカス モードに展開](media/mobile-apps-view-phone-report/power-bi-phone-report-focus-mode.png)
   
    この例では、バーには州の値が表示されています。
2. 左下の [探索] アイコン ![探索アイコン](./media/mobile-apps-view-phone-report/power-bi-phone-report-explore-icon.png) をタップします。これは左下にあります。
   
    ![探索モード](./media/mobile-apps-view-phone-report/power-bi-phone-report-explore-mode.png)
3. **[次のレベルを表示する]** または **[次のレベルに展開]** をタップします。
   
    ![次のレベルに展開](./media/mobile-apps-view-phone-report/power-bi-phone-report-expand-levels.png)
   
    今度は、バーに都市の値が表示されます。
   
    ![展開されたレベル](./media/mobile-apps-view-phone-report/power-bi-phone-report-expanded-levels.png)
4. 左上隅の矢印をタップすると、下位レベルの値がまだ展開された状態で、電話レポートに戻ります。
   
    ![下位レベルの値がまだ展開された状態](./media/mobile-apps-view-phone-report/power-bi-back-to-phone-report-expanded-levels.png)
5. 上位の元のレベルに戻るには、省略記号 **[...]** を再びタップし、 **[元に戻す]** をタップします。
   
    ![元に戻す](media/mobile-apps-view-phone-report/power-bi-phone-report-revert-levels.png)

## <a name="drill-through-from-a-value"></a>値からドリルスルーする
ドリルスルーでは、あるレポートページ内の値が他のレポートページと接続されます。 データ ポイントから別のレポートページにドリルスルーすると、データ ポイント値を使用し、ドリルスルーしたページにフィルターが適用されます。あるいは、選択したデータのコンテキストで表示されます。
レポート作成者は、レポートを作成するときに[ドリルスルーを定義](../../create-reports/desktop-drillthrough.md)できます。

1. ビジュアル内のデータ ポイントで長くタップします (タップしたまま押さえます)。
2. ツールヒントが表示されます。ドリルスルーが定義されている場合、ツールヒント フッターにドリルスルー矢印が表示されます。
3. 矢印をタップしてドリルスルーします。

    ![タップしてドリルスルー](media/mobile-apps-view-phone-report/report-drill-through1.png)

4. ドリルスルーするレポート ページを選択します。

    ![レポート ページの選択](media/mobile-apps-view-phone-report/report-drill-through2.png)

5. アプリのヘッダーにある [戻る] ボタンを使用すると、開始したページに戻ります。


## <a name="next-steps"></a>次の手順
* [Power BI モバイル アプリ向けに最適化されたレポートを作成する](../../create-reports/desktop-create-phone-report.md)
* [Power BI でダッシュボードの Phone ビューを作成する](../../create-reports/service-create-dashboard-mobile-phone-view.md)
* [任意のサイズに最適化されるレスポンシブ ビジュアルを作成する](../../visuals/power-bi-report-visualizations.md)
* 他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。