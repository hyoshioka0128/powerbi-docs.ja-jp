---
title: Power BI サービスのスライサーの使用
description: Power BI スライサーはフィルターの代わりになる手段であり、レポートの他の視覚化に表示されるデータセットの一部を絞り込むことができます。
author: mihart
ms.reviewer: v-thepet
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 10/06/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 291da6ec949dd6cfb83f26be573e592e1141e99a
ms.sourcegitcommit: 5ccab484cf3532ae3a16acd5fc954b7947bd543a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2020
ms.locfileid: "93412144"
---
# <a name="slicers-in-the-power-bi-service"></a>Power BI サービスのスライサー

[!INCLUDE[consumer-appliesto-ynnn](../includes/consumer-appliesto-yynn.md)]

![水平スライサーでの 2 つの異なる選択の比較](media/end-user-slicer/power-bi-slider.png)

スライサーは、レポート ページ上の他のビジュアルをフィルター処理する一種のビジュアルです。 Power BI レポートを使用すると、さまざまな種類のスライサーが検出されます。 上の画像に示しているのは、同じスライサーですが、選択が異なります。 各選択によってページ上の他のビジュアルがどのようにフィルター処理されているかに注目してください。  


## <a name="how-to-use-slicers"></a>スライサーの使用方法
レポートを作成するときに、" *デザイナー* " はスライサーを追加します。これによりストーリーを伝え易くなり、データを探索するためのツールが提供されます。

### <a name="numeric-range-slicer"></a>数値範囲のスライサー
 数値範囲スライサーを使用すると、リージョン、在庫数、注文日ごとの総売上高などの定量的なデータを調べることができます。 範囲を選択するには、ハンドルを使用します。 

![範囲スライサー用のハンドル](media/end-user-slicer/power-bi-handles.png)

### <a name="basic-vertical-checkbox-slicer"></a>基本的な垂直チェックボックス スライサー

基本的なチェックボックス スライサーで、1 つまたは複数のチェックボックスをオンにすると、ページ上の他のビジュアルへの影響が表示されます。 複数選択するには、CTRL キーを押しながら選択します。 レポート " *デザイナー* " は、一度に 1 つの値しか選択できないようにスライサーを設定する場合があります。 

![基本的な垂直スライサー](media/end-user-slicer/power-bi-basic.png)

### <a name="image-and-shape-slicers"></a>画像および図形のスライサー
スライサー オプションが画像または図形の場合、選択方法はチェックボックスを使用する場合と同様です。 1 または複数の画像または図形を選択して、ページ上の他のビジュアルにスライサーを適用することができます。 

![画像スライサー](media/end-user-slicer/power-bi-image.png)    

![水平スライサー](media/end-user-slicer/power-bi-horizontal.png)    

![図形スライサー](media/end-user-slicer/power-bi-boxes.png)

### <a name="hierarchy-slicer"></a>階層スライサー

階層があるスライサーでは、シェブロンを使用して階層を展開したり折りたたんだりします。 ヘッダーが更新され、選択内容が表示されます。

![階層スライサー](media/end-user-slicer/power-bi-hierarchy.png)

### <a name="relative-time-slicer"></a>相対時間スライサー
新しい高速更新シナリオでは、より小さな時間枠をフィルター処理する機能が非常に便利です。
相対時間スライサーを使用すると、レポート内の任意の日付または時刻のデータにフィルターを適用できます。 たとえば、相対時間スライサーを使用すると、過去の 2 日、数時間、または数分以内のビデオ ビューのみを表示できます。 

![相対時間スライサー](media/end-user-slicer/power-bi-relative-time.png)

## <a name="deactivate-a-slicer"></a>スライサーを非アクティブにする
スライサーを非アクティブにするには、消しゴム アイコンを選択します。

![消しゴム アイコン](media/end-user-slicer/power-bi-eraser.png)

## <a name="next-steps"></a>次のステップ
詳細については、次の記事を参照してください。

[Power BI での視覚化の種類](end-user-visualizations.md)

