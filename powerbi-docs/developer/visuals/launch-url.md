---
title: 埋め込み BI 分析情報を向上させるため、Power BI 埋め込み分析で起動 URL を作成する
description: この記事では、Power BI ビジュアルを使用して、新しいタブで URL を開く方法について説明します。 Power BI 埋め込み分析を使用して、より優れた埋め込み BI インサイトを有効にします。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: 6fe9908c324705b8cb00519b4743ae8c052c7ad8
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888307"
---
# <a name="create-a-launch-url"></a>起動 URL を作成する

起動 URL を作成することにより、実際の処理を Power BI に任せて、新しいブラウザー タブ (またはウィンドウ) を開くことができます。

> [!IMPORTANT]
> `host.launchUrl()` は、Visuals API 1.9.0 で導入されました。

## <a name="sample"></a>サンプル

`IVisualHost` インターフェイスをインポートし、ビジュアルのコンストラクターで `host` オブジェクトへのリンクを保存します。

```typescript
import powerbi from "powerbi-visuals-api";
import IVisualHost = powerbi.extensibility.visual.IVisualHost;

export class Visual implements IVisual {
    private host: IVisualHost;
    // ...
    constructor(options: VisualConstructorOptions) {
        // ...
        this.host = options.host;
        // ...
    }

    // ...
}
```

## <a name="usage"></a>使用法

`host.launchUrl()` API 呼び出しを使用して、送信先 URL を文字列引数として渡します。

```typescript
this.host.launchUrl('https://some.link.net');
```

## <a name="restrictions"></a>制限

* 絶対パスのみを使用し、相対パスは使用しません。 たとえば、`https://some.link.net/subfolder/page.html` のような絶対パスを使用します。 相対パス `/page.html` を開くことはできません。

* 現在は、*HTTP* および *HTTPS* プロトコルのみがサポートされています。 *FTP* や *MAILTO* などは使用しないでください。

## <a name="best-practices"></a>ベスト プラクティス

* 通常は、ユーザーの明示的なアクションへの応答としてのみリンクを開くことをお勧めします。 リンクまたはボタンをクリックすると新しいタブが開くことを、ユーザーが容易に理解できるようにしてください。ユーザーのアクションがないまま、または別のアクションの副作用として `launchUrl()` 呼び出しをトリガーすると、ユーザーを混乱させたりユーザーに不満を抱かせたりする場合があります。

* ビジュアルが正しく機能するためにリンクが必須ではない場合は、レポートの作成者に、リンクを無効にしたり非表示にしたりする方法を提供することをお勧めします。 この推奨は特に、サードパーティのアプリケーションにレポートを埋め込む場合や、それを Web に公開する場合など、特殊な Power BI のユースケースに関連します。

* `launchUrl()` の呼び出しを、ループ内、ビジュアルの `update` 関数、またはその他の頻繁に繰り返されるコードから、トリガーしないようにします。

## <a name="a-step-by-step-example"></a>ステップバイステップの例

### <a name="add-a-link-launching-element"></a>リンク起動要素を追加する

次の行がビジュアルの `constructor` 関数に追加されました。

```typescript
    this.helpLinkElement = this.createHelpLinkElement();
    options.element.appendChild(this.helpLinkElement);
```

アンカー要素を作成してアタッチするプライベート関数を追加します。

```typescript
private createHelpLinkElement(): Element {
    let linkElement = document.createElement("a");
    linkElement.textContent = "?";
    linkElement.setAttribute("title", "Open documentation");
    linkElement.setAttribute("class", "helpLink");
    linkElement.addEventListener("click", () => {
        this.host.launchUrl("https://docs.microsoft.com/power-bi/developer/visuals/custom-visual-develop-tutorial");
    });
    return linkElement;
};
```

最後に、*visual.less* ファイル内のエントリで、リンク要素のスタイルを定義します。

```less
.helpLink {
    position: absolute;
    top: 0px;
    right: 12px;
    display: block;
    width: 20px;
    height: 20px;
    border: 2px solid #80B0E0;
    border-radius: 20px;
    color: #80B0E0;
    text-align: center;
    font-size: 16px;
    line-height: 20px;
    background-color: #FFFFFF;
    transition: all 900ms ease;

    &:hover {
        background-color: #DDEEFF;
        color: #5080B0;
        border-color: #5080B0;
        transition: all 250ms ease;
    }

    &.hidden {
        display: none;
    }
}
```

### <a name="add-a-toggling-mechanism"></a>切り替えメカニズムを追加する

切り替えメカニズムを追加するには、レポートの作成者がリンク要素の表示を切り替えることができるように、静的なオブジェクトを追加する必要があります。 (既定では "*非表示*" に設定されています。)詳細については、[静的オブジェクトのチュートリアル](https://microsoft.github.io/PowerBI-visuals/docs/concepts/objects-and-properties)に関するページを参照してください。

次のコードに示すように、ブール型の静的オブジェクト `showHelpLink` が、*capabilities.json* ファイルの objects エントリに追加されています。

```typescript
"objects": {
    "generalView": {
            "displayName": "General View",
            "properties":
                "showHelpLink": {
                    "displayName": "Show Help Button",
                    "type": {
                        "bool": true
                    }
                }
            }
        }
    }
```

![Launch URL の切り替え](media/launch-url/launchurl-toggle.png)

また、ビジュアルの `update` 関数に次の行が追加されました。

```typescript
if (settings.generalView.showHelpLink) {
    this.helpLinkElement.classList.remove("hidden");
} else {
    this.helpLinkElement.classList.add("hidden");
}
```

要素の表示を制御するために、*hidden* クラスが *visual.less* ファイルで定義されています。