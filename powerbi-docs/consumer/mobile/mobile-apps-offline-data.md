---
title: Power BI モバイル アプリでデータをオフライン表示する
description: ネットワークに接続していなくてもデータを表示できるという、モバイル ブラウザーでなくモバイル アプリで Power BI を表示する利点について説明します。
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 12/09/2019
ms.openlocfilehash: addf608d6a3d7d51203dc22534eb8e9b9777ce49
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96397144"
---
# <a name="view-your-data-offline-in-the-power-bi-mobile-apps"></a>Power BI モバイル アプリでデータをオフライン表示する
適用対象:

| ![iPhone](./media/mobile-apps-offline-data/iphone-logo-50-px.png) | ![iPad](./media/mobile-apps-offline-data/ipad-logo-50-px.png) | ![Android フォン](./media/mobile-apps-offline-data/android-phone-logo-50-px.png) | ![Android タブレット](./media/mobile-apps-offline-data/android-tablet-logo-50-px.png) | ![Windows 10](./media/mobile-apps-offline-data/win-10-logo-50-px.png) |
|:--- |:--- |:--- |:--- |:--- |
| iPhone |iPad |Android フォン |Android タブレット |Windows 10 デバイス |

>[!NOTE]
>**Windows 10 Mobile を使用するスマートフォン** に対する Power BI モバイル アプリのサポートは、2021 年 3 月 16 日に廃止されます。 [詳細情報](/legal/powerbi/powerbi-mobile/power-bi-mobile-app-end-of-support-for-windows-phones)

モバイル ブラウザーでなくモバイル アプリで Power BI を表示する 1 つの利点は、ネットワークに接続していなくてもデータを表示できることです。 

![ネットワークに接続していないというメッセージ](./media/mobile-apps-offline-data/power-bi-iphone-no-network.png)

既定では、Power BI のデータは頻繁に更新されるため、通勤中や出張中でもビジネス上の質問に対する最新の答えを得ることができます。

## <a name="data-access-while-youre-offline"></a>オフライン中のデータ アクセス
オフライン中は、モバイル アプリから以前にアクセスしたダッシュボードにアクセスして操作を実行できます。

モバイル アプリから以前にアクセスした Power BI レポートへの読み取り専用アクセスも可能です。 完全なレポートを表示できますが、フィルター処理、クロス フィルター処理、並べ替え、スライサーは使用できません。

>[!NOTE]
> DirectQuery に基づくレポートはキャッシュされず、オフラインで利用できません。

## <a name="background-data-refresh"></a>バックグラウンドでのデータ更新
バックグラウンド更新では、お気に入りのダッシュ ボードに加えて、過去 2 週間に見たダッシュボードとレポートおよび (データ ソースではなく) Power BI サービス上のデータが更新されます。 Wi-Fi に接続している場合は、2 時間ごとにバックグラウンド更新が行われます。 Wi-Fi ではなく 3G ネットワークに接続している場合、コンテンツは Power BI によって 24 時間ごとに更新されます。

ネットワークの使用を回避するなどの場合には、バックグラウンド更新をオフにすることができます。 デバイスの設定を確認してください。

> [!NOTE]
> ユーザーが iOS デバイスで Power BI モバイル アプリを使っていて、組織で Microsoft Intune MAM が構成されている場合は、バックグラウンド データ更新がオフになります。 次にアプリを起動したときは、Web 上の Power BI サービスからデータが更新されます。
> 
> 詳細については、「[Power BI モバイル アプリを Microsoft Intune で構成する](../../admin/service-admin-mobile-intune.md)」をご覧ください。 
> 
> 

## <a name="offline-indicators"></a>オフラインのインジケーター
Power BI には、オフライン モードの切り替えを明確に示すインジケーターと共に、オフラインで使用できないために表示されないダッシュボード、レポート、およびタイルを示すインジケーターがあります。

## <a name="limitations"></a>制限事項
モバイル デバイスで Power BI をオフライン使用する際は、次のようないくつかの制限があります。

* Power BI がオフラインでキャッシュできるデータは最大 250 MB です。
* 一部の種類のタイルはアクティブなサーバー接続を必要とするため、オフラインでは使用できません (たとえば、Bing マップのタイルとカスタム タイルの一部)。
* Power BI 内の Excel ブックはその全体がオフライン利用できません。
* Reporting Services モバイル レポートと KPI は、接続時に表示している場合、オフラインで表示できます。 バックグラウンドでは更新されません。 このデータは開くたびに更新されます。
* Power BI モバイル アプリでは、Power BI Report Server に保存された Power BI Desktop (.pbix) ファイルを表示することはできません。 
* ネットワークがオフラインの間は、ページ分割されたレポート (RDL) を使用することはできません。

## <a name="next-steps"></a>次の手順
Power BI モバイル アプリで使用したいその他の機能にぜひ投票してください。お客様からのフィードバックは、将来実装する機能を決めるのに役立ちます。 

* [モバイル デバイス用の Power BI アプリ](mobile-apps-for-mobile-devices.md)
* Twitter で @MSPowerBI をフォローする
* [Power BI コミュニティの会話](https://community.powerbi.com/)に参加する
* [Power BI とは?](../../fundamentals/power-bi-overview.md)