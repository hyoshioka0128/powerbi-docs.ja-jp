---
title: サポート用に診断情報をキャプチャする
description: Power BI サービスから診断情報を手動で収集するための手順です。 トラブルシューティングに役立つように、この情報をサポートに送信します。
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 01/21/2021
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: ca2d7a49a1323b9c98596dfc61859e65ee896711
ms.sourcegitcommit: 10dfa074558a78a82f44bdfa6228c07c7d860257
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/07/2021
ms.locfileid: "106549291"
---
# <a name="capture-diagnostic-information-from-the-power-bi-service"></a>Power BI サービスから診断情報をキャプチャする

Power BI サービスで発生している問題について Microsoft サポートにお問い合わせいただく前に、私たちが問題を解決するのに役立つファイルをお客様が収集することができます。 ブラウザー セッションからブラウザー トレースを取得することをお勧めします。 ブラウザー トレースは、問題が発生したときに Power BI サービスで何が起こっていたかについての重要な詳細情報を提供する診断ファイルです。

Power BI 管理者は、[Power Platform 管理センター](https://admin.powerplatform.microsoft.com/)の **[ヘルプとサポート]** エクスペリエンスを使用して、セルフヘルプ ソリューションの入手とサポートへの問い合わせを行うことができます。 以下の手順を使用して収集した診断ファイルは、トラブルシューティングに役立つようにサポート リクエストに添付することができます。 その他のサポート オプションについては、[Power BI サポート オプション](service-support-options.md)に関する記事を参照してください。

ブラウザー トレースとその他のセッション情報を収集するには、以下の使用するブラウザー用の手順に従います。

## <a name="collect-a-browser-trace"></a>ブラウザー トレースを収集する

> [!IMPORTANT]
>使用するブラウザーに関係なく、ブラウザー トレース情報の収集を開始する "*前*" に、[Power BI サービス](https://app.powerbi.com)にサインインしてください。 この手順は、お客様のサインインに関連する機密情報がトレース情報に含まれないようにするために重要です。

#### <a name="google-chrome-or-microsoft-edge"></a>[Google Chrome または Microsoft Edge](#tab/google-chrome-or-microsoft-edge)

Google Chrome と Microsoft Edge (Chromium) はどちらも、[Chromium オープンソース プロジェクト](https://www.chromium.org/Home)が基になっています。 以下の手順では開発者ツールの使用方法を示しますが、これは 2 つのブラウザーで似ています。 詳細については、「[Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools)」および「[Microsoft Edge (Chromium) 開発者ツール](/microsoft-edge/devtools-guide-chromium)」を参照してください。

1. サインインしたら、キーボードの F12 キーを押します。 または、Microsoft Edge で **[設定など] ([...])**  >  **[その他のツール]**  >  **[開発者ツール]** の順に選択します。 Google Chrome では、次を選択します: **[Google Chrome の設定]** :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/chromium-icon-settings.png" alt-text="Google Chrome の設定メニュー。" border="false"::: > **その他のツール** > **開発者ツール**。
1. トレース オプションを設定して、ブラウザー トレースを収集する準備を行います。 また、問題の再現を開始する前に収集されたすべての情報を停止してクリアします。 既定では、ブラウザーで現在読み込まれているページのトレース情報のみが保持されます。 次の手順に従い、再現で複数のページに移動してもすべてのトレース情報が保持されるようにブラウザーを設定します。
    1. **開発者ツール** ウィンドウで、 **[Network]\(ネットワーク\)** タブを選択します。次に、 **[Preserve log]\(ログの保持\)** を選択します。
    
       :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-preserve-log.png" alt-text="[ネットワーク] タブでログの保持がオンになっている開発者ツール。" :::

     2. **[Console]\(コンソール\)** タブを選択し、 **[Settings]\(設定\)**  >  **[Preserve log]\(ログの保持\)** を選択します。 
   
           :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-console-settings.png" alt-text="[コンソール] タブでログの保持がオンになっている開発者ツール。" :::

        **[Settings]\(設定\)** をもう一度選択して、 **[Console settings]\(コンソールの設定\)** を閉じます。

3. 次に、進行中の記録を停止してクリアします。 **[Network]\(ネットワーク\)** タブを選択し、 **[Stop recording network log]\(ネットワーク ログの記録の停止\)** を選択した後、 **[Clear]\(クリア\)** を選択します。
   
   :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-stop-recording.png" alt-text="[ネットワーク] タブで記録オプションの停止とクリアが選択されている開発者ツール。" :::
     
2. 次に、Power BI サービスで発生していた問題を再現します。 まず、**開発者ツール** で **[Network]\(ネットワーク\)** タブを選択します。 **[Record network log]\(ネットワーク ログの記録\)** を選択します。

    > [!IMPORTANT]
    >トレースが正しくキャプチャされるように、問題の再現を開始する前に、Power BI サービスでブラウザー ページを更新してください。

   サポートの必要な問題が発生した手順を再現します。

     :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-record-network-log.png" alt-text="[ネットワーク] タブでネットワーク ログの記録が選択されている開発者ツール。" :::

    問題を再現すると、次の画像のような出力が **開発者ツール** ウィンドウに表示されます。

    :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-output.png" alt-text="[ネットワーク] タブにセッションの出力が表示された開発者ツール。" :::
    
3. 問題の動作を再現した後は、そのログ ファイルを保存し、サポート リクエストに添付する必要があります。
    1. ネットワーク ログをエクスポートするには、**開発者ツール** で **[Network]\(ネットワーク\)** タブを選択します。 **[Stop recording network log]\(ネットワーク ログの記録の停止\)** を選択します。 次に、 **[Export HAR...]\(HAR のエクスポート...\)** を選択してファイルを保存します。

         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-export-har.png" alt-text="[ネットワーク] タブで記録を停止し、HAR をエクスポートするオプションが選択されている開発者ツール。" :::

    2. コンソール出力をエクスポートするには、**開発者ツール** で **[Console]\(コンソール\)** タブ選択します。表示されているメッセージを右クリックし、 **[Save as...]\(名前を付けて保存...\)** を選択して、コンソール出力をテキスト ファイルに保存します。
    
         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-save-as.png" alt-text="[コンソール] タブが選択され、名前を付けて保存オプションが表示されている開発者ツール。" :::

   保存した HAR ファイル、コンソール出力、および画面記録を圧縮形式 (.zip など) にパッケージ化し、そのファイルをサポート リクエストに添付します。

#### <a name="apple-safari"></a>[Apple Safari](#tab/apple-safari)

次の手順では、Apple Safari の開発者ツールを使用する方法について説明します。 詳細については、「[Safari 開発者ツールの概要](https://support.apple.com/guide/safari-developer/safari-developer-tools-overview-dev073038698/11.0/mac)」を参照してください。

1. サインイン後、Apple Safari で開発者ツールを有効にします。
    1. ページ ヘッダーから **[Safari]**  >  **[環境設定]** を選択します。
    
       :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-preferences.png" alt-text="環境設定が選択されている Apple Safari メニュー。" :::

    2. **[詳細]** を選択し、 **[メニューバーに"開発"メニューを表示]** をオンにして開発者ツールを有効にします。
    
       :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-show-develop-menu.png" alt-text="[メニューバーに&quot;開発&quot;メニューを表示] がオンになっている Safari の詳細メニュー。" :::

2. 次に、**Web インスペクタ** でオプションを設定して、ブラウザーですべてのトレース情報を保持できるようにします。 既定では、ブラウザーで現在読み込まれているページのトレース情報のみが保持されます。 次の設定により、再現で複数のページに移動する必要がある場合でも、トレース情報が収集されるようになります。

    1. **[開発]**  >  **[Web インスペクタを表示]** を選択します。
    
        :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-web-inspector.png" alt-text="[Web インスペクタを表示] が選択された開発メニュー。" :::

    2. **[ネットワーク]**  >  **[ログを保存]** をオンにします
       
         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-network-preserve-log.png" alt-text="[ネットワーク] で [ログを保存] がオンになっている Web インスペクタのメニュー。" :::

    1. **[コンソール]**  >  **[ログを保存]** をオンにします
   
       :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-console-preserve-log.png" alt-text="[コンソール] で [ログを保存] がオンになっている Web インスペクタのメニュー。" :::

3. オプションを設定したら、 **[ネットワーク]**  >  **[Clear Network Items]\(ネットワーク項目のクリア\)** を選択して、問題の再現に関する詳細情報のみがログに記録されるようにします。

    :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-clear-network-items.png" alt-text="[ネットワーク] で [Clear Network Items]\(ネットワーク項目のクリア\) が選択されている Web インスペクタのメニュー。" :::


4. これで問題を再現する準備ができました。 
    > [!IMPORTANT]
    >トレースが正しくキャプチャされるように、問題の再現を開始する前に、Power BI サービスでブラウザー ページを更新してください。

    発生している問題を再現するための手順を実行します。 問題を再現すると、次の画像のような出力が **[ネットワーク]** ウィンドウに表示されます。

    :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-session-output.png" alt-text="サンプル出力が表示されている [ネットワーク] ウィンドウ。" :::

5. 問題の動作を再現した後は、そのログ ファイルを保存し、サポート リクエストに添付する必要があります。

    1. ネットワーク ログをエクスポートするには、 **[ネットワーク]** タブから **[エクスポート]** を選択し、ファイルを HAR 形式で保存します。

         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-export.png" alt-text="エクスポート オプションが選択されている [ネットワーク] タブ。" :::

    2. コンソール出力をエクスポートするには、 **[開発]** ツール ウィンドウで **[コンソール]** タブを選択し、ウィンドウを展開します。 コンソール出力の先頭にカーソルを置き、出力の内容全体をドラッグして選択します。 Command + C キーを使用して出力をコピーし、テキスト ファイルに保存します。

   保存した HAR ファイル、コンソール出力、および画面記録を圧縮形式 (.zip など) にパッケージ化し、そのファイルをサポート リクエストに添付します。

#### <a name="firefox"></a>[Firefox](#tab/firefox)

次の手順では、Firefox の開発者ツールを使用する方法について説明します。 詳細については、「[開発ツール](https://developer.mozilla.org/docs/Tools)」を参照してください。

1. サインインしたら、キーボードの F12 キーを押します。 または、Firefox で **[メニューを開きます]** :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/firefox-menu.png" alt-text="Firefox のメニュー アイコン。" border="false"::: >  **[Web 開発]**  >  **[開発ツールを表示]** の順に選択します。 画面の下部にツールが表示されます。

1. 次に、**インスペクター** でオプションを設定して、ブラウザーですべてのトレース情報を保持できるようにします。 既定では、ブラウザーで現在読み込まれているページのトレース情報のみが保持されます。 次の設定により、再現で複数のページに移動する必要がある場合でも、トレース情報が収集されるようになります。

    1. **[インスペクター]** ウィンドウで、 **[ネットワーク]** タブを選択し、 **[ネットワーク設定]**  >  **[永続ログ]** を選択します。
    
       :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/firefox-network-persist-logs.png" alt-text="[ネットワーク] タブで永続ログが選択されているインスペクター ツール。" :::

     2. **[コンソール]** タブを選択し、 **[コンソール設定]**  >  **[永続ログ]** を選択します。 
   
           :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/firefox-console-persist-logs.png" alt-text="[コンソール] タブで永続ログが選択されているインスペクター ツール。" :::

3. オプションを設定したら、進行中の記録をクリアします。 **[ネットワーク]** タブを選択し、 **[消去]** を選択します。
   
   :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-stop-recording.png" alt-text="[ネットワーク] タブで記録オプションの停止とクリアが選択されている開発者ツール。" :::
     
2. これで問題を再現する準備ができました。 
    > [!IMPORTANT]
    >トレースが正しくキャプチャされるように、問題の再現を開始する前に、Power BI サービスでブラウザー ページを更新してください。
 
    発生している問題を再現するための手順を実行します。
    
3. 問題の動作を再現した後は、そのログ ファイルを保存し、サポート リクエストに添付する必要があります。
    1. ネットワーク ログをエクスポートするには、 **[ネットワーク]**  >  **[ネットワーク設定]** 、 **[Save All as HAR]\(HAR 形式ですべて保存\)** の順に選択します。

         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/firefox-save-har.png" alt-text="HAR のエクスポート/インポート メニューですべて保存オプションが選択されている [ネットワーク] タブ。" :::

    2. コンソールの出力をエクスポートするには、 **[コンソール]** タブを選択します。表示されたメッセージを右クリックし、 **[表示メッセージをエクスポート]**  >  **[ファイル]** を選択します。
    
         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/firefox-export-visible-messages.png" alt-text="[コンソール] タブが選択され、表示メッセージをエクスポートするオプションが表示されています。" :::

   保存した HAR ファイル、コンソール出力、および画面記録を圧縮形式 (.zip など) にパッケージ化し、そのファイルをサポート リクエストに添付します。

---

診断ファイルを収集したら、それらをサポート リクエストに添付して、サポート エンジニアによる問題解決に役立ててください。 HAR ファイルには、次のような、ブラウザー ウィンドウと Power BI サービス間のネットワーク要求に関するすべての情報が含まれます。

* 各要求のアクティビティ ID。

* 各要求の正確なタイムスタンプ。

* クライアントに返されるエラー情報。

このトレースには、画面に表示されるビジュアルを設定するのに使われるデータも含まれます。

## <a name="next-steps"></a>次のステップ

* [Microsoft 365 で Power BI サービスの正常性を追跡する](service-admin-health.md)
* [サービス中断の通知を有効にする](service-interruption-notifications.md)
* [Power BI コミュニティに参加する](https://community.powerbi.com/)
