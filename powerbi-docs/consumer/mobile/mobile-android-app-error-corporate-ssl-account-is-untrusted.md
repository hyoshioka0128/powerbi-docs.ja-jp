---
title: "\"お使いの企業 SSL 証明書が信頼されていません\" を修正する"
description: Power BI 用の Android アプリにサインインするとき、"お使いの企業 SSL 証明書が信頼されていないため、認証できませんでした" というメッセージが表示されることがあります
.": ''
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 08/28/2019
ms.author: mshenhav
ms.openlocfilehash: cde8a4bbaed9ef10940b7a102d40a8bc6009e9b9
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73879478"
---
# <a name="fixing-corporate-ssl-certificate-is-untrusted---power-bi"></a>"企業 SSL 証明書が信頼されていません" を修正する
Microsoft Power BI 用の Android モバイル アプリにサインインするとき、"お使いの企業 SSL 証明書がこのデバイスによって信頼されていないため、認証できませんでした。 会社の IT 管理者にお問い合わせください。" というメッセージが表示されることがあります。 

このメッセージへの対処方法は、通常、Android デバイスのオペレーティング システムによって異なりますが、このエラーの原因になる可能性のある問題が他にも 2 つあります。

## <a name="on-android-7-or-later"></a>Android 7 以降
**Chrome** という名前のアプリの更新プログラムを探してインストールします。

## <a name="on-android-6-and-earlier"></a>Android 6 以前
デバイスの System Webview の更新バージョンが必要な場合があります。 既にデバイスにインストールされている可能性があり、その場合は **[更新]** をクリックする必要があるだけです。

System Webview がデバイスにインストールされていない場合:

1. Android デバイスで、Power BI を閉じます。
2. Google Play ストアを開き、Google Inc. の **System Webview** を検索します。
3. インストールします。
4. Power BI アプリを再起動し、サインインします。

## <a name="time-zone-settings"></a>タイム ゾーンの設定
デバイスのタイム ゾーンの設定が正しくない可能性があります。 

**[設定]**  >  **[システム]**  >  **[日付と時刻]** で確認します。

## <a name="custom-authentication-server"></a>カスタム認証サーバー
カスタム認証サーバーを使っている場合、会社の認証サーバーの SSL 証明書が有効ではない可能性があります。 組織の IT と協力し、[こちらの記事](https://support.microsoft.com/help/3203929/using-adal-to-authenticate-from-android-devices-fails-if-additional-ce)のガイダンスに従って、会社の認証サーバーの構成をテストします。

## <a name="next-steps"></a>次の手順
* Android アプリ ストアから [Android アプリをダウンロード](https://go.microsoft.com/fwlink/?LinkID=544867)する。
* わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。 

