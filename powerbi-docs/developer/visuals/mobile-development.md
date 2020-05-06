---
title: モバイル開発
description: モバイル対応の Power BI ビジュアルを作成する方法
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 03/12/2019
ms.openlocfilehash: 38e6ac3be143381304f1fdfc8e1427b91f398a9a
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82196631"
---
# <a name="how-to-create-mobile-friendly-power-bi-visuals"></a>モバイル対応の Power BI ビジュアルを作成する方法
モバイル消費は、Power BI において大きな役割があります。 その長所の 1 つは、いつでもどこでもデータに接続していられることです。

Power BI ビジュアルを作成する開発者は、できるだけ多くのユーザーが使用できるようにし、最適なモバイル エクスペリエンスを提供するため、各モバイル デバイスに固有の制約に対応する必要があります。

[Windows、iOS、Android 用の Power BI アプリ](/power-bi/consumer/mobile/mobile-apps-for-mobile-devices)を使用して、ビジネス ユーザーが外出先でも指先 1 つでデータの包括的なビューを見られるようにします。

## <a name="requirements"></a>要件

モバイル対応のビジュアル開発には、次の要件が不可欠です。

- レンダー

  Power BI ビジュアルは、サポートされているブラウザーとアプリケーションを含む、サポートされているすべてのモバイル デバイスのレポートやダッシュボードに、または**フォーカス** モードで実行されているとき、エラーを出さずに表示される必要があります。 

- Interactive

  対話機能は、デスクトップ デバイスと同じ方法で提供される必要があります。 デスクトップ ブラウザーで処理されるすべてのイベントは、モバイル デバイスでサポートされるか、またはモバイル デバイス用の同等のイベント ハンドラーが存在する必要があります。
  
  たとえば、基本的なナビゲーションとデータ ポイントの選択は、デスクトップ ブラウザーと同じように機能する必要があります。 **Ctrl** キーを使用する複数選択がビジュアルでサポートされている場合、開発者はモバイル デバイス用に同様のイベント ハンドラーを追加することを検討する必要があります。

  次の表に、モバイル デバイスの対応するイベントの一覧を示します。

  | マウス イベント名 | タッチ イベント名 |
  |:----------------:|:----------------:|
  | `click` | `click` |
  | `mousemove` | `touchmove` |
  | `mousedown` | `touchstart` |
  | `mouseup` | `touchend` |
  | `dblclick` | 外部ライブラリを使用する |
  | `contextmenu` | 外部ライブラリを使用する |
  | `mouseover` | `touchmove` |
  | `mouseout` | `touchmove` (または外部ライブラリ) |
  | `wheel` | `NaN` |

  > [!NOTE]
  > 一部のモバイル デバイスまたはタッチ スクリーン デバイスでは、マウス (つまり、*mouse* プレフィックスが付いた) イベントがサポートされていません。 このような場合は、*mouse* イベントと *touch* イベントの両方を同時に処理します。

## <a name="optional"></a>省略可能
以下はオプションであり、より優れたエンド ユーザー エクスペリエンスを作成するために使用されます。

- レンダー

  小さいサイズのビジュアルをサポートするには、各要素のサイズを調整するためにユーザーが変更できる書式設定オプションを追加してみてください。 たとえば、ラベルをレポートやダッシュボードで使用するための書式設定オプションを追加します。 これにより、ユーザーはモバイル デバイス専用にビジュアルをカスタマイズできます。
  
  同じ設定をデスクトップ ブラウザーのビジュアルにも適用でき、必要に応じてオーバーライドして、ビジュアルをより小さい画面に合わせることができます。

  > [!NOTE]
  > **フォーカス** モードでビジュアルを最適化するには、縦と横両方の向きの画面サイズを考慮する必要があります。[フォーカス モードでのコンテンツの表示](/power-bi/consumer/end-user-focus)に関する記事をご覧ください。

- Interactive

  ドラッグやスクロールなど、モバイル固有のイベント ハンドラーを追加することを検討します。

- [フェールオーバー]

  モバイル デバイスにビジュアルをレンダリングできない場合は、わかりやすいエラーを表示する必要があります。

## <a name="supported-browsers-and-devices"></a>サポートされているブラウザーとデバイス
Power BI ビジュアルは、Power BI アプリをサポートするすべてのデバイスでレンダリングできる必要があります。詳しくは、「[Power BI のサポートされているブラウザー](/power-bi/power-bi-browsers)」および[Power BI モバイル アプリ](/power-bi/consumer/mobile/mobile-apps-for-mobile-devices)に関する記事をご覧ください。

Windows、iOS、Android デバイスの最新モデルに対してテストする場合、開発者はこれらの品質面のほとんどを考慮する必要があります。

## <a name="next-steps"></a>次の手順
作業を開始するには、次を参照してください: 「[チュートリアル: Power BI のビジュアルを開発する](/power-bi/developer/visuals/custom-visual-develop-tutorial)」。
