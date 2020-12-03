---
title: Power BI ビジュアルのガイドライン
description: Microsoft AppSource にカスタム ビジュアルを発行して、それを他のユーザーが見つけたり、購入して使用できるようにする方法について説明します。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 08/12/2020
ms.openlocfilehash: 427fba66b34fefb0b7ca9d70a29b08ebe7d743cb
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96416142"
---
# <a name="guidelines-for-power-bi-visuals"></a>Power BI ビジュアルのガイドライン
他のユーザーが検出して使用できるようにご自分の Power BI ビジュアルを Microsoft AppSource に[発行](office-store.md)する前に、ユーザー向けに優れたエクスペリエンスを作成するためのガイドラインに従っていることを確認してください。

## <a name="power-bi-visuals-with-additional-purchases"></a>Power BI ビジュアルの追加購入

無料の Power BI ビジュアルを Marketplace (Microsoft AppSource) に送信できます。 また、"追加購入が必要になる場合がある" という価格タグが付いている Microsoft AppSource Power BI ビジュアルに送信することもできます。 "追加購入が必要になる場合がある" Power BI ビジュアルは、Office ストアのアプリ内購入 (IAP) アドインと似ています。 

無料の Power BI ビジュアルと同様に、IAP Power BI ビジュアルも認定を受けることができます。 認定を受けるにあたっては IAP Power BI ビジュアルを送信する前に、[認定要件](power-bi-custom-visuals-certified.md)に準拠していることを確認してください。

### <a name="what-is-a-power-bi-visual-with-iap-features"></a>IAP 機能のある Power BI ビジュアルとは

IAP Power BI ビジュアルは、*無料の機能* を提供する *無料* のビジュアルです。 これには、追加料金が適用される場合がある、いくつかの高度な機能も用意されています。 開発者は、Power BI ビジュアルの説明で、操作のために追加購入が必要となる機能についてユーザーに通知する必要があります。 現在、Microsoft は、アプリおよびアドインの購入をサポートするためのネイティブ API を提供していません。

開発者は、これらの購入に対し、任意のサードパーティ製の支払いシステムを使うことができます。 詳細については、[ストアのポリシー](/legal/marketplace/certification-policies#11002-displaying-ads)に関する記事をご覧ください。


>[!IMPORTANT]  
> Power BI ビジュアルを無料から "追加購入が必要になる場合があります" に更新する場合、ユーザーは、更新前に同じレベルの無料の機能を受け取る必要があります。 既存の無料機能に加えて、オプションの高度な有料機能を追加できます。

### <a name="watermarks"></a>透かし

透かしを使用することで、顧客が支払いをせずに引き続き IAP の高度な機能を使用できるようにすることができます。 

透かしを使用すると、購入前に、Power BI ビジュアルのすべての機能を紹介することができます。 

* 透かしは、有効なライセンスなしに使用される有料の機能でのみ使用できます。
* *無料* の価格タグが付いた Power BI ビジュアルに、透かしを使用することはできません。
* ユーザーが無料の機能を使用している場合、IAP ビジュアルで透かしを使用することはできません。 

### <a name="pop-up-window"></a>ポップアップ ウィンドウ

Power BI IAP ビジュアルで無効 (または有効期限切れ) のライセンスが使用されている場合は、ポップアップ ウィンドウを使用してライセンスの購入方法を説明できます。

### <a name="submission-process"></a>送信プロセス

[提出プロセス](office-store.md#submitting-to-appsource)に従った後、 *[製品のセットアップ]* タブに移動し、 *[この製品ではサービスを購入する必要があります]* チェック ボックスをオンにします。

Power BI ビジュアルが検証されて承認されたら、IAP Power BI ビジュアル用の Microsoft AppSource の一覧で、価格オプションの下に "追加購入が必要になる場合があります" と記載されます。

## <a name="context-menu"></a>コンテキスト メニュー
コンテキスト メニューは、ユーザーがビジュアルの上にマウス ポインターを置いたときに表示される右クリック メニューです。
すべての Power BI ビジュアルでは、コンテキスト メニューを使用して、統一されたエクスペリエンスを実現できます。
コンテキスト メニューを追加する方法については、[こちらの記事](https://github.com/Microsoft/PowerBI-visuals/blob/gh-pages/tutorials/building-bar-chart/adding-context-menu-to-the-bar.md)をご覧ください。

>[!div class="mx-imgBorder"]
>![Power BI ビジュアルのコンテキスト メニューのスクリーンショット。](media/guidelines-powerbi-visuals/context-menu.png)

## <a name="commercial-logo"></a>商用ロゴ
このセクションでは、Power BI ビジュアルに商用ロゴを追加するための仕様について説明します。 商用ロゴは必須ではありません。 追加する場合、これらのガイドラインに従う必要があります。

> [!NOTE]
> * この記事に含まれている商用ロゴは、以下の図で説明されているように任意の営利企業のアイコンを示しています。
> * この記事での Microsoft の商用ロゴの使用は例としてのみとなっています。 ご利用の Power BI ビジュアルでは独自の商用ロゴを使用します。

> [!IMPORTANT]
> 商用ロゴは "*編集*" モードでのみ使用できます。 商用ロゴはビュー モードでは表示 *できません*。

### <a name="commercial-logo-type"></a>商用ロゴの種類

商用ロゴには、次の 3 種類があります。
* **ロゴ** - ロゴは、アイコンと名前の 2 つの要素で構成されています。

    ![Microsoft ロゴのスクリーンショット。](media/guidelines-powerbi-visuals/microsoft-logo.png)

* **シンボル** - テキストを含まないグラフィック。

    ![Microsoft シンボルのスクリーンショット。](media/guidelines-powerbi-visuals/microsoft-symbol.png)

* **ロゴタイプ** - テキストのみで構成され、アイコンを含まないロゴ。

    ![Microsoft ロゴ (アイコンなし) のスクリーンショット。](media/guidelines-powerbi-visuals/microsoft-logotype.png)

### <a name="commercial-logo-color"></a>商用ロゴの色

商用ロゴを使用する場合、ロゴの色は灰色 (16 進カラー コードは #C8C8C8) とする必要があります。 グラデーションなどの効果を商用ロゴに追加しないでください。

* **ロゴ**

    ![灰色の Microsoft ロゴのスクリーンショット。](media/guidelines-powerbi-visuals/grey-microsoft-logo.png)

* **シンボル** - テキストを含まないグラフィック。

    ![灰色の Microsoft シンボルのスクリーンショット。](media/guidelines-powerbi-visuals/grey-microsoft-symbol.png)

* **ロゴタイプ** - テキストのみで構成され、アイコンを含まないロゴ。

    ![灰色の Microsoft ロゴ (アイコンなし) のスクリーンショット。](media/guidelines-powerbi-visuals/grey-microsoft-logotype.png)

> [!TIP]
> * ご利用の Power BI ビジュアルにグラフィックが含まれている場合、ご利用のロゴに対して余白を 10 px に設定した白の背景の追加を検討してください。
> * ご利用のロゴに対して影付き文字 (不透明度 30% の黒) の追加を検討してください。

### <a name="commercial-logo-size"></a>商用ロゴのサイズ

Power BI ビジュアルには、サイズの大きいタイル用と小さいタイル用の 2 つの商用ロゴが必要です。 右上隅または右下隅に配置されている境界ボックス内に、4 px の余白が設定されたロゴを配置します。

次の表では、Power BI ビジュアルのサイズに関する考慮事項について説明します。

|設定  |小さい Power BI ビジュアル  |大きい Power BI ビジュアル  |
|---------|---------|---------|
|*ロゴの幅*    |最大 240 px         |240 px より大きい         |
|*ロゴの高さ*     |最大 160 px         |160 px より大きい         |
|*境界ボックスのサイズ*     |40 x 15 px         |101 x 30 px         |
|*商用ロゴの例*     |![小さなバージョンの Microsoft の商用ロゴのスクリーンショット。](media/guidelines-powerbi-visuals/grey-microsoft-symbol.png)         |![Microsoft の商用ロゴのスクリーンショット。](media/guidelines-powerbi-visuals/grey-microsoft-logo.png)         |
|*境界ボックスの例*    |![小さいロゴ サイズのスクリーンショット。](media/guidelines-powerbi-visuals/small-logo-box.png)         |![大きいロゴ サイズのスクリーンショット。](media/guidelines-powerbi-visuals/big-logo-box.png)         |
|    |         |         |

### <a name="commercial-logo-behavior"></a>商用ロゴの動作

商用ロゴは編集モードでのみ使用できます。 クリックすると、商用ロゴには次の機能のみを含めることができます。

* 商用ロゴをクリックすると、ご利用の Web サイトにリダイレクトされます。

* 商用ロゴをクリックすると、ポップアップウィンドウが開き、追加の情報が表示されます。 ポップアップ ウィンドウは、次の 2 つのセクションに分けられます。
    * 商用ロゴ、ビジュアル、市場の評価などを含めることができるマーケティング分野。
    * 情報やリンクを含めることができる情報領域。    


### <a name="things-to-avoid"></a>回避事項

* 商用ロゴをビュー モードで表示することはできません。

* アニメーション化された商用ロゴには、最大 5 秒間アニメーションを表示できます。

* ご利用の Power BI のビジュアルに閲覧モードで情報アイコン (i) が含まる場合は、それらは、前述のように、商用ロゴの色、サイズ、および場所に準拠している必要があります。

* カラフルな商用ロゴまたは黒い商用ロゴを避けてください。 商用ロゴは灰色 (16 進カラー コードは #C8C8C8) にする必要があります。

    ![許可されていないカラフルな Microsoft ロゴのスクリーンショット。](media/guidelines-powerbi-visuals/no-color-logo.png) ![許可されていない Microsoft の黒いロゴのスクリーンショット](media/guidelines-powerbi-visuals/black-logo.png)

* グラデーションや濃い影などの効果がある商用ロゴ。

    ![許可されていない Microsoft ロゴ スタイルの例のスクリーンショット。](media/guidelines-powerbi-visuals/no-style-logo.png)

## <a name="best-practices"></a>ベスト プラクティス

Power BI ビジュアルを発行する場合は、ユーザーに優れたエクスペリエンスを提供するために、次の推奨事項を考慮してください。

### <a name="visual-landing-page"></a>ビジュアルのランディング ページ

ランディング ページを使用すると、ご自分のビジュアルの使用方法およびライセンスの購入場所をユーザーに対して明確にすることができます。 自動でトリガーされる動画は含めないでください。 ライセンス購入の詳細に関する情報やリンク、および IAP 機能の使用方法など、ユーザーのエクスペリエンスの向上に役立つ資料のみを追加してください。

### <a name="license-key-and-token"></a>ライセンス キーおよびトークン

ユーザーの利便性のために、書式ウィンドウの上部にライセンス キーやトークン関連のフィールドを追加します。

## <a name="faq"></a>よく寄せられる質問

Power BI ビジュアルの詳細については、[追加購入を含む Power BI ビジュアルについてよく寄せられる質問](power-bi-custom-visuals-faq.md#visuals-with-additional-purchases)に関する記事をご覧ください。

## <a name="next-steps"></a>次のステップ

Microsoft AppSource にご利用の Power BI ビジュアルを発行して、他のユーザーが見つけたり使用したりすることができるようにする方法について説明します。

>[!div class="nextstepaction"]
>[Power BI ビジュアルを発行する](office-store.md)