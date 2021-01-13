---
title: 埋め込み BI 分析情報を向上させるための Power BI 埋め込み分析の認定済み Power BI ビジュアル
description: 認定を受けるためにカスタム ビジュアルを提出する場合の要件とプロセス、認定済み Power BI ビジュアルの一覧。 Power BI 埋め込み分析を使用して、より優れた埋め込み BI インサイトを有効にします。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 03/08/2020
ms.openlocfilehash: 5f337197655d41b830b237c04faa2642991c34ee
ms.sourcegitcommit: a5e98bc86915f7bea6a0ab5df282683840e63d2c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2021
ms.locfileid: "97969813"
---
# <a name="get-a-power-bi-visual-certified"></a>認定済みの Power BI ビジュアルを取得する

認定済み Power BI ビジュアルとは、Microsoft Power BI チームの[コード要件](#certification-requirements)に適合している [AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?page=1&product=power-bi-visuals) の Power BI ビジュアルです。 これらのビジュアルは、外部のサービスやリソースにアクセスしないこと、およびセキュリティで保護されたコーディング パターンとガイドラインに従っていることを検証するテストを受けています。

Power BI ビジュアルが認定されると、提供される機能が増えます。 たとえば、[PowerPoint にエクスポート](../../consumer/end-user-powerpoint.md)したり、ユーザーが[レポート ページをサブスクライブしている](../../consumer/end-user-subscribe.md)ときに受信メールにビジュアルを表示したりできます。

認定プロセスは任意です。 認定されていない Power BI ビジュアルは、安全ではない Power BI ビジュアルとは限りません。 一部の Power BI ビジュアルは 1 つまたは複数の[認定要件](power-bi-custom-visuals-certified.md#certification-requirements)を満たしていないために認定されていません。 たとえば、外部サービスに接続するマップ Power BI ビジュアルや、商用ライブラリを使用する Power BI ビジュアルです。

> [!NOTE]
> Microsoft は、サードパーティの Power BI ビジュアルの作成者ではありません。 サードパーティのビジュアルの機能を確認するには、ビジュアルの作成者に直接問い合わせてください。

## <a name="certification-requirements"></a>認定要件

Power BI ビジュアルの[認定を受ける](#get-a-power-bi-visual-certified)には、Power BI ビジュアルがこのセクションに記載されている要件を満たしている必要があります。 

### <a name="general-requirements"></a>一般的な要件

Power BI ビジュアルは、パートナー センターで承認される必要があります。 Power BI ビジュアルはあらかじめ [AppSource](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) に発行しておくことをお勧めします。 Power BI ビジュアルを AppSource に発行する方法については、「[Power BI ビジュアルをパートナー センターに発行する](office-store.md)」を参照してください。

認定対象の Power BI ビジュアルを提出する前に、「[Power BI ビジュアルの ガイドライン](guidelines-powerbi-visuals.md)」に準拠していることを確認してください。

Power BI ビジュアルを提出する場合は、コンパイルされたパッケージが、提出されるパッケージと完全に一致していることを確認します。

### <a name="code-repository-requirements"></a>コード リポジトリの要件

GitHub でコードをパブリックに共有する必要はありませんが、コード リポジトリは Power BI チームがレビューのために使用できる必要があります。 これを行う最適な方法は、GitHub でソース コード (JavaScript または TypeScript) を提供することです。

リポジトリには、次のものが含まれている必要があります。
* 1 つだけの Power BI ビジュアルのコード。 複数の Power BI ビジュアルのコード、または関連のないコードを含めることはできません。
* **certification** (必ず小文字) という名前のブランチ。 このブランチのソース コードは、提出されたパッケージと一致している必要があります。 このコードは、次回の提出プロセス中に、Power BI ビジュアルを再提出する場合にのみ、更新できます。

Power BI ビジュアルにプライベート npm パッケージまたは git サブ モジュールを使用している場合は、そのコードを含む追加のリポジトリへのアクセスを提供する必要があります。

Power BI ビジュアルのリポジトリの外観を把握するには、GitHub リポジトリで[Power BI ビジュアルのサンプル横棒グラフ](https://github.com/microsoft/PowerBI-visuals-sampleBarChart)を確認してください。

### <a name="file-requirements"></a>ファイルの要件

Power BI ビジュアルを作成するには、最新バージョンの API を使用します。

リポジトリには、次のファイルを含める必要があります。
* **.gitignore** - `node_modules`、`.tmp`、`dist` をこのファイルに追加します。 コードに *node_modules*、 *.tmp*、または *dist* フォルダーを含めることはできません。
* **capabilities.json** - このファイルのプロパティに変更を加えた Power BI ビジュアルの新しいバージョンを提出する場合は、既存のユーザーのレポートを破損しないことを確認します。
* **pbiviz.json** 
* **package.json**。 ビジュアルには、次のパッケージがインストールされている必要があります。
   * ["tslint"](https://www.npmjs.com/package/tslint) - バージョン 5.18.0 以上
   * ["typescript"](https://www.npmjs.com/package/typescript) - バージョン 3.0.0 以上
   * ["tslint-microsoftcontrib"](https://www.npmjs.com/package/tslint-microsoft-contrib) - バージョン 6.2.0 以上
   * このファイルには、リンターを実行するためのコマンドが含まれている必要があります - `"lint": "tslint -c tslint.json -p tsconfig.json"`
* **package-lock.json**
* **tsconfig.json**

### <a name="command-requirements"></a>コマンドの要件

次のコマンドでエラーが返されないことを確認します。

* `npm install`
* `pbiviz package`
* `npm audit` - 高レベルまたは中レベルの警告を返してはなりません。
* [必要な構成](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/master/tslint.json)を備えた [Microsoft の TSlint](https://www.npmjs.com/package/tslint-microsoft-contrib)。 このコマンドから lint エラーが返されてはなりません。

### <a name="compiling-requirements"></a>コンパイルの要件

Power BI ビジュアルを作成するには、最新バージョンの [powerbi-visuals-tools](https://www.npmjs.com/package/powerbi-visuals-tools) を使用します。

`pbiviz package` を使用して Power BI ビジュアルをコンパイルする必要があります。 独自のビルド スクリプトを使用している場合は、`npm run package` カスタム ビルド コマンドを用意します。

### <a name="source-code-requirements"></a>ソース コードの要件

[Power BI ビジュアルの追加の認定](/legal/marketplace/certification-policies#1200-power-bi-visuals-additional-certification)ポリシー一覧に従っていることを確認します。 提出がこれらのガイドラインに従っていない場合、パートナー センターからの却下メールには、このリンクに記載されているポリシー番号が記載されます。

次に示すコードの要件に従って、コードが Power BI 認定ポリシーに準拠していることを確認します。  

**必須**
* 公開されている Javascript や TypeScript ライブラリなどの公開レビュー可能な OSS コンポーネントのみを使用します。
* このコードでは、[レンダリング イベント API](event-service.md) をサポートする必要があります。
* DOM が安全に操作されていることを確認します。 ユーザー入力またはユーザー データにサニタイズを使用してから DOM に追加します。
* テスト データセットとして[サンプル レポート](https://github.com/PowerBi-Projects/PowerBI-visuals/tree/gh-pages/assets)を使用します。

**禁止**
* 外部のサービスまたはリソースへのアクセス。 たとえば、Power BI から任意のサービスにアクセスできる HTTP/S または WebSocket 要求を含めることはできません。
* `innerHTML` または `D3.html(user data or user input)` の使用。
* すべて入力データに対するブラウザー コンソールの JavaScript エラーまたは例外。
* `eval()`、`settimeout()`、`requestAnimationFrame()`、`setinterval(user input function)` の安全ではない使用、ユーザー入力またはユーザー データなどの任意のコードまたは動的コード。
* 縮小された JavaScript ファイルまたはプロジェクト。

## <a name="submitting-a-power-bi-visual-for-certification"></a>認定されるための Power BI ビジュアルの提出

自分の Power BI ビジュアルに対する Power BI チームによる認定をパートナー センターを通して要求できます。

>[!TIP]
>Power BI 認定プロセスには時間がかかることがあります。 新しい Power BI ビジュアルを作成している場合は、Power BI 認定を要求する前に、パートナー センターを通して Power BI ビジュアルを発行しておくことをお勧めします。 これにより、自分のビジュアルの発行が遅れないようにすることができます。

Power BI 認定を要求するには:

1. パートナー センターにサインインします。
2. **[概要]** ページで、自分の Power BI ビジュアルを選択し、 **[製品]** 設定ページに移動します。
3. **[Power BI 認定を要求します]** チェック ボックスをオンにします。
4. **[確認と発行]** ページで、 **[認定の注意書き]** テキスト ボックスに、ソース コードへのリンクと、それにアクセスするために必要な資格情報を入力します。

### <a name="private-repository-submission-process"></a>プライベート リポジトリの提出プロセス

GitHub などのプライベート リポジトリを使用して、認定を受けるために Power BI ビジュアルを送信する場合は、このセクションの手順に従ってください。
1. 検証チーム用の新しいアカウントを作成します。
2. アカウントに対して [2 要素認証](https://help.github.com/github/authenticating-to-github/securing-your-account-with-two-factor-authentication-2fa)を構成します。
3. [新しい回復用コードのセットを生成します](https://help.github.com/github/authenticating-to-github/configuring-two-factor-authentication-recovery-methods#generating-a-new-set-of-recovery-codes)。
4. Power BI ビジュアルを提出する際に、以下を指定します。
    * リポジトリへのリンク
    * ログイン資格情報 (パスワードを含む)
    * 回復用コード
    * アカウントに対する読み取り専用アクセス許可 ([pbicvsupport](https://github.com/pbicvsupport))

## <a name="certified-power-bi-visual-badges"></a>認定済み Power BI ビジュアル バッジ

Power BI ビジュアルは、認定されると、認定を受けたことを示すバッジが与えられます。

### <a name="certified-power-bi-visuals-in-appsource"></a>AppSource の認定済み Power BI ビジュアル

* [AppSource の Power BI ビジュアル](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals)をオンラインで検索する場合、ビジュアルのカード上の小さい黄色いバッジは、それが認定済みの Power BI ビジュアルであることを示しています。

    ![AppSource の認定済み Power BI ビジュアル](media/power-bi-custom-visuals-certified/certified-visual-yellow-small.png)

* AppSource で Power BI ビジュアルのカードをクリックすると、"*PBI 認定*" という黄色いバッジが表示され、この Power BI ビジュアルが認定されていることを示します。

    ![アプリ ページの認定済み Power BI ビジュアル](media/power-bi-custom-visuals-certified/certified-visual-yellow-big.png)

### <a name="certified-power-bi-visuals-in-the-power-bi-interface"></a>Power BI インターフェイスの認定済み Power BI ビジュアル

* Power BI (デスクトップまたはサービス) 内から Power BI ビジュアルをインポートする場合、青いバッジは Power BI ビジュアルが認定されていることを示します。

    ![Power BI インターフェイス認定済み Power BI ビジュアル](media/power-bi-custom-visuals-certified/certified-visual-blue.png)

* 認定済み Power BI ビジュアルのみを表示するには、" *[Power BI 認定]* " フィルター オプションを選択します。

## <a name="publication-timeline"></a>パブリケーション タイムライン

AppSource への配置は、時間がかかる可能性のあるプロセスです。 このプロセスが完了すると、Power BI ビジュアルが AppSource からダウンロードできるようになります。

### <a name="when-will-users-be-able-to-download-my-visual"></a>ユーザーはいつビジュアルをダウンロードできますか。

* 初めて Power BI ビジュアルを送信した場合、AppSource から電子メールを受信してから数時間後にユーザーがダウンロードできるようになります。

* 既存の Power BI ビジュアルに更新を送信した場合、ユーザーは送信から 1 か月以内にダウンロードできるようになります。

    >[!NOTE]
    > AppSource の *[バージョン]* フィールドは、Power BI が AppSource によって承認された日に更新されます。これは、ビジュアルの送信後約 1 週間です。 ユーザーは更新されたビジュアルをダウンロードできますが、更新された機能は有効になりません。 ビジュアルの新機能は、約 1 か月後にユーザーのレポートに影響を与えます。 

### <a name="when-will-my-power-bi-visual-display-a-certification-badge"></a>Power BI ビジュアルに証明書バッジが表示されるのはいつですか。

* Power BI ビジュアルを初めて送信した場合は、AppSource から承認メールを受け取った日から 1 日以内に証明書バッジが表示されます。

* 既存の Power BI ビジュアルの認定を要求している場合、証明書バッジは送信から 1 か月以内に表示されます。

## <a name="next-steps"></a>次の手順

* Power BI の独自の視覚化を作成して  [Microsoft AppSource](https://appsource.microsoft.com) に追加することに関心がある Web 開発者は、 [Power BI の円形カード視覚化の開発](develop-circle-card.md)に関するチュートリアルから始めてください。

* ビジュアルについて詳しくは、[認定済みのビジュアルに関してよく寄せられる質問](power-bi-custom-visuals-faq.md#certified-power-bi-visuals)に関する記事をご覧ください。

* [YouTube での Microsoft の Power BI ビジュアル プレイリスト](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)

* [Power BI のビジュアル](power-bi-custom-visuals.md)

* [Microsoft AppSource に Power BI ビジュアルを発行する](office-store.md)

* 他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。
