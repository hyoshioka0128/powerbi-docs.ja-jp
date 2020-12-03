---
title: Power BI モバイル アプリでバーコードをスキャンする
description: 現実世界でバーコードをスキャンし、Power BI モバイル アプリでフィルターされた BI 情報に直接アクセスできます。
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 12/02/2019
ms.openlocfilehash: 5d1534ec3b6ccdf730cd2b255ba1142e80a6f9f9
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96413106"
---
# <a name="scan-a-barcode-with-your-device-from-the-power-bi-mobile-app"></a>デバイスで Power BI モバイル アプリからバーコードをスキャンする
現実世界でバーコードをスキャンし、Power BI モバイル アプリでフィルターされた BI 情報に直接アクセスできます。


適用対象:

| ![iPhone](./media/mobile-apps-qr-code/ios-logo-40-px.png) | ![iPad](./media/mobile-apps-qr-code/ios-logo-40-px.png) | ![Android フォン](././media/mobile-apps-qr-code/android-logo-40-px.png) | ![Android タブレット](././media/mobile-apps-qr-code/android-logo-40-px.png) |
|:--- |:--- |:--- |:--- |
|iPhone |iPad |Android フォン |Android タブレット |

たとえば、同僚が [Power BI Desktop のレポートのバーコード フィールドにタグを付け](../../transform-model/desktop-mobile-barcodes.md)、そのレポートを自分と共有したとします。 

![製品バーコード スキャンのスクリーンショット。色の付いた飲料のバーコードにスキャナーがあてられています。](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-scanner.png)

デバイスの Power BI アプリのスキャナーで製品バーコードをスキャンすると、そのバーコードのレポート (またはレポートの一覧) が表示されます。 そのバーコードにフィルター処理されたレポートを開くことができます。

## <a name="scan-a-barcode-with-the-power-bi-scanner"></a>Power BI スキャナーでバーコードをスキャンする
1. ナビゲーション バーの **[その他のオプション]** (...) をタップし、 **[スキャナー]** をタップします。

    ![ナビゲーション ウィンドウの [その他のオプション] のスクリーンショット。スキャナー選択があります。](media/mobile-apps-scan-barcode-iphone/power-bi-scanner.png)

2. カメラが有効になっていない場合は、Power BI アプリでカメラを使用することを承認する必要があります。 これは、1 回限りの承認です。 
4. 製品のバーコードをスキャナーでポイントします。 そのバーコードに関連付けられたレポートの一覧が表示されます。
5. そのバーコードに従って自動的にフィルター処理されたレポート名をタップして、デバイスで開きます。

## <a name="filter-by-other-barcodes-while-in-a-report"></a>レポートを開いているときに他のバーコードでフィルターする
あるバーコードでフィルター処理されたレポートをデバイスで表示しているときに、そのレポートを別のバーコードでフィルター処理したい場合があります。

* バーコード アイコンにフィルター ![フィルター適用アイコン](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-filtered-icon-black.png)がある場合、フィルターがアクティブになり、レポートをバーコードでフィルターすることができます。 
* アイコンにフィルター ![フィルター適用なしアイコン](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-unfiltered-icon.png)が含まれていない場合、フィルターはアクティブにならず、レポートはバーコードでフィルターされません。 

いずれの方法でも、アイコンをタップすると浮動スキャナーがある小さなメニューが開きます。

* スキャナーを新しい項目に移動すると、レポートのフィルターは別のバーコード値に変わります。 
* フィルターされていないレポートに戻るには、 **[Clear barcode filter]** (バーコード フィルターのクリア) を選択します。
* レポート フィルターを、現在のセッション内でスキャンしたバーコードのいずれかに変更するには、 **[Filter by recent barcodes]** (最近のバーコードでフィルター) を選択します。

## <a name="issues-with-scanning-a-barcode"></a>バーコードのスキャンに関する問題
ここでは、製品でバーコードをスキャンするときに表示される可能性があるメッセージについて説明します。

### <a name="couldnt-filter-report"></a>"レポートをフィルター処理できませんでした..."
フィルター対象に選択したレポートは、このバーコード値を含まないデータ モデルに基づいています。 たとえば、レポートに "mineral water" という製品が含まれていません。  

### <a name="allsome-of-the-visuals-in-the-report-dont-contain-any-value"></a>レポートのすべてまたは一部のビジュアルに値が含まれていない
スキャンしたバーコード値はモデル内に存在しますが、レポートのすべてまたは一部のビジュアルに、この値が含まれていないため、フィルターからは空の状態が返されます。 他のレポート ページを見るか、Power BI デスクトップでレポートを編集してこの値を含めます。 

### <a name="looks-like-you-dont-have-any-reports-that-can-be-filtered-by-barcodes"></a>"バーコードでフィルターをかけられるレポートはお持ちでないようです。"
これは、バーコード対応のレポートがないことを意味します。 バーコード スキャナーは、 **[バーコード]** とマークされた列があるレポートのみをフィルターできます。  

自分またはレポート所有者が Power BI Desktop で列に **[バーコード]** とタグを付けていることを確認します。 詳細については、[Power BI Desktop でバーコード フィールドにタグを付ける方法](../../transform-model/desktop-mobile-barcodes.md)に関するページを参照してください。

### <a name="couldnt-filter-report---looks-like-this-barcode-doesnt-exist-in-the-report-data"></a>"レポートをフィルター処理できませんでした - このバーコードはレポート データに存在しないようです。"
フィルター対象に選択したレポートは、このバーコード値を含まないデータ モデルに基づいています。 たとえば、レポートに "mineral water" という製品が含まれていません。 別の製品をスキャンする、別のレポートを選択する (複数のレポートを使用できる場合)、またはフィルターされていないレポートを表示することができます。 

## <a name="next-steps"></a>次の手順
* [Power BI Desktop のバーコード フィールドにタグを付ける](../../transform-model/desktop-mobile-barcodes.md)
* [Power BI のダッシュボードのタイル](../end-user-tiles.md)
* [Power BI のダッシュボード](../end-user-dashboards.md)
