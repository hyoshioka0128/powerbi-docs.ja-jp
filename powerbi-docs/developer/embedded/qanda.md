---
title: 埋め込み BI 分析情報を向上させるための Power BI 埋め込み分析の Q&A
description: Power BI 埋め込み分析では、アプリケーションに Q&A を組み込む手段が提供されており、ユーザーは自然言語を使って質問できます。 Power BI 埋め込み分析を使用して、より優れた埋め込み BI インサイトを有効にします。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 11/20/2017
ms.openlocfilehash: 43e886e6472c6d95b900ccdb5c2e73b8dca3d4a0
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2021
ms.locfileid: "97886605"
---
# <a name="qa-in-power-bi-embedded-analytics"></a>Power BI 埋め込み分析の Q&A

Power BI 埋め込み分析では、アプリケーションに Q&amp;A を組み込む手段が提供されており、ユーザーは、自然言語を使って質問し、チャートやグラフなどのビジュアルの形式ですぐに回答を受け取ることができます。

![埋め込みフレームでの Q&A の対話的な質問](media/qanda/embedded-qanda.gif)

アプリケーション内に Q&A を埋め込むには、**対話式** と **結果のみ** の 2 つのモードがあります。 **対話式** モードでは、質問を入力し、ビジュアル内に表示することができます。 保存されている質問、または表示したい設定済みの質問がある場合は、埋め込み構成に質問を設定することにより、**結果のみ** モードを使うことができます。

JavaScript のコードは次のようになります。

```javascript
// Embed configuration used to describe the what and how to embed.
// This object is used when calling powerbi.embed within the JavaScript API.
// You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
var config= {
    type: 'qna',
    tokenType:   models.TokenType.Embed | models.TokenType.Aad,
    accessToken: access token value,
    embedUrl:    https://app.powerbi.com/qnaEmbed (groupId to be appended as query parameter if required),
    datasetIds:  array of requested data set ids (at the moment we support only one dataset),
    viewMode:    models.QnaMode.Interactive | models.QnaMode.ResultOnly,
    question:    optional parameter for Explore mode (QnaMode.Interactive) and mandatory for Render Result mode (QnaMode.ResultOnly)
};

// Get a reference to the embedded QNA HTML element
var qnaContainer = $('#qnaContainer')[0];

// Embed the QNA and display it within the div container.
var qna = powerbi.embed(qnaContainer, config);
```

## <a name="set-question"></a>設定済みの質問

設定済みの質問で **結果モード** を使う場合、追加の質問をフレームに挿入し、すぐに得られる回答で前の結果を置き換えることができます。 新しい質問と一致する新しいビジュアルが表示されます。

この使用例の 1 つは、よく寄せられる質問の一覧です。 ユーザーは質問を選んで、同じ埋め込みパーツ内で回答を見ることができます。

**JS SDK を使った場合のコード スニペット:**  

```javascript
// Get a reference to the embedded Q&A HTML element
var qnaContainer = $('#qnaContainer')[0];

// Get a reference to the embedded Q&A.
qna = powerbi.get(qnaContainer);

qna.setQuestion("This year sales")
    .then(function (result) {
        …….
    })
    .catch(function (errors) {
        …….
    });
```

## <a name="visual-rendered-event"></a>ビジュアル レンダリング イベント

**対話式** モードでは、アプリケーションはレンダリングされたビジュアルが変化するたびにデータ変更イベントの通知を受信して、入力時に、更新済みの入力クエリを対象とすることができます。

*visualRendered* イベントをリッスンすると、後で使うために質問を保存することができます。 

**JS SDK を使った場合のコード スニペット:**  

```javascript
// Get a reference to the embedded Q&A HTML element
var qnaContainer = $('#qnaContainer')[0];

// Get a reference to the embedded Q&A.
qna = powerbi.get(qnaContainer);

// qna.off removes a given event listener if it exists.
qna.off("visualRendered");

// qna.on will add an event listener.
qna.on("visualRendered", function(event) {
     …….
});
```

## <a name="embed-token"></a>埋め込みトークン

Q&A パーツを開始するためのデータセットの埋め込みトークンを作成します。 詳細については、[トークンの生成](/rest/api/power-bi/embedtoken)に関するページをご覧ください。

## <a name="next-steps"></a>次のステップ

Q&A の埋め込みを試してみるなら、[JavaScript の埋め込みサンプル](https://microsoft.github.io/PowerBI-JavaScript/demo/)をご覧ください。

その他の質問 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。