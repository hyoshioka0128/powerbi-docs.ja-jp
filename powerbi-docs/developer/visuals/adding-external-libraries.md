---
title: 埋め込み BI 分析情報を向上させるための Power BI 埋め込み分析での Power BI ビジュアルへの外部ライブラリの追加
description: この記事では Power BI ビジュアルで外部ライブラリを使用する方法について説明します。 Power BI 埋め込み分析を使用して、より優れた埋め込み BI インサイトを有効にします。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 02/24/2020
ms.openlocfilehash: b9a443040384e4d38bd7440eae0a5582cc422836
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2021
ms.locfileid: "97889181"
---
# <a name="adding-external-libraries"></a>外部ライブラリを追加する

この記事では Power BI ビジュアルで外部ライブラリを使用する方法について説明します。 これには、Power BI ビジュアルのコードから外部ライブラリをインストール、インポート、および呼び出す方法が含まれます。

## <a name="javascript-libraries"></a>JavaScript ライブラリ

1. *npm* や *yarn* などのパッケージ マネージャーを使用して、外部の JavaScript ライブラリをインストールします。
2. 外部ライブラリを使用して、必要なモジュールをソース ファイルにインポートします。

>[!NOTE]
>ご利用の JavaScript ライブラリに型指定を追加して、Intellisense とコンパイル時の安全性を確保するには、必ず適切なパッケージをインストールしてください。

### <a name="installing-the-d3-library"></a>d3 ライブラリのインストール

以下は、[npm](https://www.npmjs.com/) を使用して、[d3 ライブラリ](https://www.npmjs.com/package/d3)と [@types/d3](https://www.npmjs.com/package/@types/d3) パッケージをインストールする例です。

完全な例については、[Power BI 視覚化](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L29)に関するコードを参照してください。

1. *d3* パッケージと *d3 types* パッケージをインストールします。

    ```powershell
    npm install d3@5 --save
    npm install @types/d3@5 --save
    ```

2. `visual.ts` など、*d3* ライブラリを使用するファイルにそれをインポートします。

    ```typescript
    import * as d3 from "d3";
    ```

## <a name="css-framework"></a>CSS フレームワーク

1. *npm* や *yarn* などのパッケージ マネージャーを使用して、外部の CSS フレームワークをインストールします。
2. ビジュアルの `.less` ファイルに、`import` ステートメントを含めます。

### <a name="installing-bootstrap"></a>ブートストラップのインストール

[npm](https://www.npmjs.com/) を使用して[ブートストラップ](https://www.npmjs.com/package/bootstrap)をインストールする例を次に示します。

完全な例については、[Power BI 視覚化](https://github.com/Microsoft/powerbi-visuals-sankey/blob/c8200da56913cd8b253be949a35fad0f4472b6de/style/visual.less#L32)に関するコードを参照してください。

1. "*ブートストラップ*" パッケージをインストールします。

    ```powershell
    npm install bootstrap --save
    ```

2. `visual.less` に `import` ステートメントを含めます。

    ```less
    @import (less) "node_modules/bootstrap/dist/css/bootstrap.css";
    ```
