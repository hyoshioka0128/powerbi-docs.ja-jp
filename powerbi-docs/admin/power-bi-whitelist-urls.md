---
title: Power BI URL を許可リストに追加する
description: この記事では、Power BI への接続の許可リストに追加する URL エンドポイントとポートの一覧を示します。
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 06/25/2020
ms.custom: seodec18
ms.openlocfilehash: 1495400a59d8250f407a5f7415a550871501e4e3
ms.sourcegitcommit: cb6e0202de27f29dd622e47b305c15f952c5769b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2020
ms.locfileid: "96577511"
---
# <a name="add-power-bi-urls-to-your-allow-list"></a>Power BI URL を許可リストに追加する
[//]: # "suparnap、miwehnia、natham はこのリストを維持するための連絡先です"

Power BI サービスではインターネットへの接続が必要です。 Power BI サービスを使用するお客様は、この記事の表に記載されているエンドポイントに接続できる必要があります。

Power BI のサービスを使用するには、次の表で **必須** とマークされているエンドポイントと、リンク先のサイトで **必須** とマークされているすべてのエンドポイントに接続できる必要があります。 外部サイトへのリンクが特定のセクションを参照している場合は、そのセクション内のエンドポイントを確認するだけでかまいません。

**オプション** とマークされているエンドポイントも、特定の機能を動作させるために許可リストに登録できます。

Power BI のサービスで必要なことは、リストに記載されているエンドポイントのために TCP ポート 443 を開いておくことだけです。

ワイルドカード (*) は、ルート ドメインの下のすべてのレベルを表し、情報を利用できない場合には "該当なし" としています。 **ターゲット** 列には、ドメイン名と、追加のエンドポイント情報を含む外部サイトへのリンクが示されます。

>[!Important]
>次の表の情報は、Power BI Germany、21Vianet によって運営される Power BI China、または米国政府向け Power BI には適用されません。 クラウド サービス間の通信の詳細については、「[行政機関向け Azure クラウド サービスとグローバルな Azure クラウド サービスに接続する](service-govus-overview.md#connect-government-and-global-azure-cloud-services)」を参照してください。

## <a name="authentication"></a>認証

Power BI は、Microsoft 365 の認証セクションと ID セクションの必須エンドポイントに依存します。 Power BI を使用するには、以下のリンク先のサイト内のエンドポイントに接続できる必要があります。

| 行 | 目的 | ターゲット | ポート |
| --- | --- | --- | --- |
| 1 | **必須:** 認証と ID | [Microsoft 365 Common と Office Online の URL](/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) に関するドキュメントを参照  | 該当なし |

## <a name="general-site-usage"></a>一般的なサイトの使用

Power BI の一般的な使用では、次の表内とリンク先のサイトのエンドポイントに接続できる必要があります。

| 行 | 目的 | ターゲット | ポート |
| --- | --- | --- | --- |
| 1 | **必須:** バックエンド API | api.powerbi.com | TCP 443 |
| 2 | **必須:** バックエンド API | *.analysis.windows.net | TCP 443 |
| 3 | **必須:** バックエンド API | *.pbidedicated.windows.net | TCP 443 |
| 4 | **必須:** Content Delivery Network (CDN) | content.powerapps.com | TCP 443 |
| 5 | **必須:** Microsoft 365 の統合 | [Microsoft 365 Common と Office Online の URL](/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) に関するドキュメントを参照 | 該当なし |
| 6 | **必須:** ポータル | *.powerbi.com | TCP 443 |
| 7 | **必須:** サービスの利用統計情報 | dc.services.visualstudio.com | TCP 443 |
| 8 | **オプション:** 情報メッセージ | dynmsg.modpim.com | TCP 443 |
| 9 | **オプション:** NPS 調査 | nps.onyx.azure.net | TCP 443 |
| | | |

## <a name="administration"></a>Administration

Power BI 内で管理機能を実行するには、以下のリンク先のサイト内のエンドポイントに接続できる必要があります。

| 行 | 目的 | ターゲット | ポート |
| --- | --- | --- | --- |
| 1 | **必須:** ユーザーの管理と監査ログの表示用 | [Microsoft 365 Common と Office Online の URL](/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) に関するドキュメントを参照 | 該当なし |
| | | |

## <a name="getting-data"></a>データの取得

OneDrive などの特定のデータ ソースからデータを取得するには、次の表内のエンドポイントに接続できる必要があります。 組織内で使用されている特定のデータ ソースでは、追加のインターネット ドメインおよび URL へのアクセスが必要となる場合があります。

| 行 | 目的 | ターゲット | ポート |
| --- | --- | --- | --- |
| 1 | **必須:** AppSource (Power BI の内部または外部のアプリ) | appsource.microsoft.com <br> *.s-microsoft.com  | TCP 443 |
| 2 | **オプション:** サインインしてコンテンツ パックのデータを取得する | 使用しているコンテンツパックによって異なる | 使用しているコンテンツパックによって異なる |
| 3 | **オプション:** 個人用 OneDrive からのファイルのインポート | 「[Required URLs and ports for OneDrive](/onedrive/required-urls-and-ports)」 (OneDrive に必要な URL とポート) を参照 | 該当なし |
| 4 | **オプション:** Power BI の 60 秒間のチュートリアル ビデオ | *.doubleclick.net <br> *.ggpht.com <br> *.google.com <br> *.googlevideo.com <br> *.youtube.com <br> *.ytimg.com <br> fonts.gstatic.com | TCP 443 |
| 5 | **オプション:** PubNub ストリーミング データ ソース | [PubNub のドキュメント](https://support.pubnub.com/hc/en-us/categories/360004336832-PubNub-101)を参照 | 該当なし |
| | | |

## <a name="dashboard-and-report-integration"></a>ダッシュボードとレポートの統合

Power BI は、ダッシュボードとレポートをサポートするため、特定のエンドポイントに依存します。 次の表内とリンク先のサイトのエンドポイントに接続できる必要があります。

| 行 | 目的 | ターゲット | ポート |
| --- | --- | --- | --- |
| 1 | **必須:** Excel との連携 | [Microsoft 365 Common と Office Online の URL](/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) に関するドキュメントを参照 | 該当なし |
| | | |

## <a name="power-bi-visuals"></a>Power BI ビジュアル

Power BI は、Power BI ビジュアルの表示とアクセスのために、特定のエンドポイントに依存します。 次の表内とリンク先のサイトのエンドポイントに接続できる必要があります。

| 行 | 目的 | ターゲット | ポート |
| --- | --- | --- | --- |
| 1 | **必須:** Marketplace インターフェイスまたはファイルからカスタム ビジュアルをインポートする | *.azureedge.net <br> *.blob.core.windows.net <br> *.osi.office.net <br> *.msecnd.net <br> store.office.com <br> web.vortex.data.microsoft.com <br> store-images.s-microsoft.com | TCP 443 |
| 2 | **オプション:** Bing マップ | bing.com <br> platform.bing.com <br> *.virtualearth.net | TCP 443 |
| 3 | **オプション:** PowerApps | PowerApps のシステム要件のサイトの「[必要なサービス](/powerapps/maker/canvas-apps/limits-and-config#required-services)」セクションを参照 | 該当なし |
| 4 | **オプション:** Visio | [Microsoft 365 Common と Office Online の URL](/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) に関するドキュメントおよび「[SharePoint Online と OneDrive for Business](/office365/enterprise/urls-and-ip-address-ranges#sharepoint-online-and-onedrive-for-business)」を参照 | 該当なし |
| | | |

## <a name="related-external-sites"></a>関連する外部サイト

その他の関連サイトへの Power BI リンク。 これらのサイトは、ドキュメント、サポート、新しい機能要求などをホストします。 これらのサイトへのアクセスは Power BI の機能に影響しません。そのため、許可リストへの追加は省略可能です。

| 行 | 目的 | ターゲット | ポート |
| --- | --- | --- | --- |
| 1 | **オプション:** コミュニティ サイト | community.powerbi.com <br> oxcrx34285.i.lithium.com | TCP 443 |
| 2 | **オプション:** ドキュメントのサイト | docs.microsoft.com <br> img-prod-cms-rt-microsoft-com.akamaized.net <br> statics-uhf-eas.akamaized.net <br> cdnssl.clicktale.net <br> ing-district.clicktale.net | TCP 443 |
| 3 | **オプション:** ダウンロード サイト (Power BI Desktop など) | download.microsoft.com | TCP 443 |
| 4 | **オプション:** 外部リダイレクト | aka.ms <br> go.microsoft.com | TCP 443 |
| 5 | **オプション:** アイデアのフィードバック サイト| ideas.powerbi.com <br> powerbi.uservoice.com | TCP 443 |
| 6 | **オプション:** Power BI サイト - ランディング ページ、詳細情報のリンク、サポート サイト、ダウンロード リンク、パートナー ショーケースなど。 | powerbi.microsoft.com | TCP 443 |
| 7 | **オプション:** Power BI デベロッパー センター | dev.powerbi.com | TCP 443 |
| 8 | **オプション:** サポート サイト | support.powerbi.com <br> s3.amazonaws.com <br> *.olark.com <br> logx.optimizely.com <br> mscom.demdex.net <br> tags.tiqcdn.com | TCP 443 |
| | | |
