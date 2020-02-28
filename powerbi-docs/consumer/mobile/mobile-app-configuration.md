---
title: Power BI アプリの構成設定
description: MDM ツールを使用して Power BI の動作をカスタマイズする方法
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: painbar
ms.openlocfilehash: b7a02261e6e00c01befa8ba7716b9e0d132323ea
ms.sourcegitcommit: f9909731ff5b6b69cdc58e9abf2025b7dee0e536
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/20/2020
ms.locfileid: "77496744"
---
# <a name="remotely-configure-power-bi-app-using-mobile-device-management-mdm-tool"></a>モバイル デバイス管理 (MDM) ツールを使用して Power BI アプリをリモートで構成する

iOS および Android 用 Power BI Mobile アプリでは、モバイル デバイス管理 (MDM) (Intune など) の管理者が、アプリの動作をカスタマイズできるようにするアプリ設定がサポートされています。

Power BI Mobile アプリでは、次の構成シナリオがサポートされています。

* レポート サーバーの構成 (iOS および Android)
* データ保護の設定 (iOS および Android)
* 対話式操作の設定 (Android)

## <a name="report-server-configuration-ios-and-android"></a>レポート サーバーの構成 (iOS および Android)

管理者は、iOS および Android 用 Power BI アプリを使って、登録済みデバイスにレポート サーバーの構成をリモートで "プッシュ" することができます。

| キー | 種類 | 説明 |
|---|---|---|
| com.microsoft.powerbi.mobile.ServerURL | 文字列 | レポート サーバー URL。<br><br>先頭は http/https である必要があります。|
| com.microsoft.powerbi.mobile.ServerUsername | 文字列 | (省略可能)<br><br>サーバーの接続に使用するユーザー名。<br><br>存在しない場合、アプリで、ユーザーに接続用のユーザー名の入力を求めるメッセージが表示されます。|
| com.microsoft.powerbi.mobile.ServerDisplayName | 文字列 | (省略可能)<br><br>既定値は "Report server" です<br><br>サーバーを表すためにアプリで使用されるフレンドリ名。 |
| com.microsoft.powerbi.mobile.OverrideServerDetails | ブール値 | (省略可能)<br><br>既定値は True です。 True に設定されている場合、モバイル デバイスに既にあるレポート サーバーのすべての定義がオーバーライドされます。 既に構成されているサーバーは、削除されます。 また、オーバーライドを True に設定すると、ユーザーはその構成を削除できなくなります。<br><br>False に設定すると、既存の設定はそのままで、プッシュされた値が追加されます。 同じサーバー URL がモバイル アプリに既に構成されている場合、アプリはその構成をそのままにします。 アプリで同じサーバーへの再認証をユーザーに求めることはありません。 |

## <a name="data-protection-settings-ios"></a>データ保護の設定 (iOS)

管理者は、iOS および Android 用 Power BI アプリを使用して、セキュリティとプライバシーの設定に対する既定の構成をカスタマイズすることができます。 Power BI アプリにアクセスするときに、ユーザーに自分の Face ID、Touch ID、またはパスコードを入力するように強制できます。

| キー | 種類 | 説明 |
|---|---|---|
| com.microsoft.powerbi.mobile.ForceDeviceAuthentication | ブール値 | 既定値は False です。 <br><br>デバイス上のアプリにアクセスするために、ユーザーに TouchID や FaceID などの生体測定を要求することができます。 必要に応じて、認証に加えて生体測定が使用されます。<br><br>アプリ保護ポリシーを使用している場合、Microsoft ではデュアル アクセスのプロンプトを防ぐために、この設定を無効にすることをお勧めします。 |

## <a name="interaction-settings-android"></a>対話式操作の設定 (Android)

Android 用 Power BI アプリでは、組織内のユーザー グループ全体で既定の対話式操作の設定を変更する必要があると判断された場合に、管理者が対話式操作の設定を構成することができます。 

| キー | 種類 | 値 | 説明 |
|---|---|---|---|
| com.microsoft.powerbi.mobile.ReportTapInteraction | 文字列 |  <nobr>single-tap</nobr><br><nobr>double-tap</nobr> | ビジュアル上でタップすることでデータ ポイントの選択も行うかどうかを構成します。 |
| com.microsoft.powerbi.mobile.RefreshAction | 文字列 |  <nobr>pull-to-refresh</nobr><br>選択します。 | ユーザーがレポートを更新するためにボタンを使用するか、引っ張って更新を使用する必要があるかを構成します。 |
| com.microsoft.powerbi.mobile.FooterAppearance | 文字列 |  docked<br>動的 | レポートのフッターをレポートの下部にドッキングするか、自動的に非表示にするかを構成します。 |

## <a name="deploying-app-configuration-settings"></a>アプリ構成設定を配置する

アプリ構成ポリシーを作成するために必要な手順を、次に示します。 構成ポリシーを作成したら、ユーザーのグループにその設定を割り当てることができます。

1. MDM ツールを接続します。
2. 新しいアプリ構成ポリシーを作成して名前を付けます。
3. このアプリ構成ポリシーを配布するユーザーを選択します。
4. ユーザーにプッシュする設定に対してキー値のペアを作成します。

管理者は、Intune ポータルを使用して、アプリ構成ポリシーによってこれらの設定を簡単に Power BI アプリに配置できます。 しかし、任意の MDM プロバイダーがサポートされています。 Intune を使用していない場合は、これらの設定を配置する方法について、ご利用の MDM のドキュメントを参照する必要があります。

## <a name="next-steps"></a>次の手順

* [App Store](https://apps.apple.com/app/microsoft-power-bi/id929738808) と [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.powerbim&amp;amp;clcid=0x409) から Power BI モバイル アプリを入手する
* Twitter で [@MSPowerBI をフォローする](https://twitter.com/MSPowerBI)
* [Power BI コミュニティの会話](https://community.powerbi.com/)に参加する
