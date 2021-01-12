---
title: 埋め込み BI 分析情報を向上させるための Power BI 埋め込み分析のパフォーマンス ヒント
description: ハイ パフォーマンス Power BI ビジュアルを構築する方法。 Power BI 埋め込み分析を使用して、より優れた埋め込み BI インサイトを有効にします。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 04/20/2020
ms.openlocfilehash: c8bcf5e13ba769b976ab123adb3ba37f46b0359e
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2021
ms.locfileid: "97885938"
---
# <a name="how-to-build-a-high-performance-power-bi-visual"></a>ハイ パフォーマンス Power BI ビジュアルを構築する方法
この記事では、ビジュアルのレンダリング時に開発者がハイ パフォーマンスを実現する方法について説明します。 

ビジュアルのレンダリングに時間がかかるのは望ましくありません。また、レンダリング時には、コードから可能な限りのパフォーマンスを引き出すことが重要になります。 

> [!NOTE]
> プラットフォームが継続的に改善および強化されており、新しいバージョンの API が常にリリースされています。 Power BI ビジュアルのプラットフォームと機能セットを最大限に活用するために、最新のバージョンで最新の状態を維持することをお勧めします。
>
> 最新の **バージョン 2.1** 以降、Power BI のビジュアル読み込み時間が平均で 20% 向上しています。

## <a name="power-bi-visual-performance-tips"></a>Power BI ビジュアルのパフォーマンスのヒント
ビジュアルの最適なパフォーマンスを実現する方法の推奨事項を次に示します。 

### <a name="use-user-timing-api"></a>User Timing API を使用する
**User Timing API** を使用してアプリの JavaScript のパフォーマンスを測定すると、スクリプトのどの部分に最適化が必要かを判断するのに役立ちます。

詳細については、[User Timing API](https://msdn.microsoft.com/library/hh772738(v=vs.85).aspx) に関するページを参照してください。

### <a name="review-animation-loops"></a>アニメーション ループを確認する
アニメーション ループで、変更されない要素は再描画しますか? 

 - 問題:フレーム間で変更されない要素を描画するのは、時間の浪費です。

 - 解決方法:フレームを選択的に更新します。 
 
静的な視覚化をアニメーション化する場合は、描画コードを 1 つの update 関数に一括でまとめて、アニメーション ループの反復ごとに新しいデータで繰り返し呼び出す方法が考えられます。

代わりに、次の更新パターンを検討し、ビジュアル コンストラクター メソッドを使用して静的なすべてのものを描画します。そうすると、update 関数では変更される視覚化要素を描画するだけで済みます。 

   > [!TIP]
   > 非効率的なアニメーション ループは、軸と凡例でよく見られます。

### <a name="cache-dom-nodes"></a>DOM ノードをキャッシュする 
ノードまたはノード リストを DOM から取得するときは、後の計算で (場合によっては、次のループの反復で) 再利用できるかどうかを検討する必要があります。 関連領域内のノードをさらに追加または削除する必要がない限り、これらのノードをキャッシュすることで、アプリケーションの全体の効率を向上させることができます。

コードが高速で、ブラウザーの速度が低下しないようにするには、DOM アクセスを最小限に抑えます。 

- 次の処理の前 

   ```javascript
   public update(options: VisualUpdateOptions) { 
       let axis = $(".axis"); 
   }
   ```

- 次の処理の後 

   ```javascript
   public constructor(options: VisualConstructorOptions) { 
       this.$root = $(options.element); 
       this.xAxis = this.$root.find(".xAxis"); 
   } 
 
   public update(options: VisualUpdateOptions) { 
       let axis = this.axis; 
   }
   ```

### <a name="avoid-dom-manipulation"></a>DOM の操作を回避する 
DOM の操作を可能な限り制限します。  `prepend()`、`append()`、`after()` などの挿入操作は時間がかかるため、必要な場合以外は使用しないでください。

次に例を示します。

  ```javascript
  for (let i=0; i<1000; i++) { 
      $('#list').append('<li>'+i+'</li>');
  }
  ```

上の例は、`html()` を使用し、事前にリストを構築することで高速化できます。 

  ```javascript
  let list = ''; 
  for (let i=0; i<1000; i++) { 
      list += '<li>'+i+'</li>'; 
  } 

  $('#list').html(list); 
  ```

### <a name="reconsider-jquery"></a>JQuery を再検討する

可能な限り JS フレームワークを制限してネイティブ JS を使用することで、使用可能な帯域幅を増やし、処理のオーバーヘッドを減らすことができます。 これにより、古いブラウザーとの互換性の問題を制限することもできます。 

詳細については、[youmightnotneedjquery.com](http://youmightnotneedjquery.com/) で、JQuery の `show`、`hide`、`addClass` などの関数の別の例を参照してください。  

### <a name="use-canvas-or-webgl"></a>Canvas または WebGL を使用する 
アニメーションを繰り返し使用する場合は、SVG ではなく **Canvas** または **WebGL** を使用することを検討してください。 SVG とは異なり、これらのオプションを使用すると、コンテンツではなくサイズによってパフォーマンスが決まります。 

その違いの詳細については、「[SVG と Canvas: 選択する方法](/previous-versions/windows/internet-explorer/ie-developer/samples/gg193983(v=vs.85))」を参照してください。 

### <a name="use-requestanimationframe-instead-of-settimeout"></a>setTimeout の代わりに requestAnimationFrame を使用する 
[requestAnimationFrame](https://www.w3.org/TR/animation-timing/) を使用して画面上のアニメーションを更新する場合は、ブラウザーで別の再描画が呼び出される **前に**、アニメーション関数が呼び出されます。

詳細については、`requestAnimationFrame`を使用したスムーズなアニメーションに関するこの[サンプル](https://testdrive-archive.azurewebsites.net/Graphics/RequestAnimationFrame/Default.html)を参照してください。

## <a name="next-steps"></a>次のステップ

最適化の手法の詳細については、「[Power BI の最適化ガイド](../../guidance/power-bi-optimization.md)」を参照してください。