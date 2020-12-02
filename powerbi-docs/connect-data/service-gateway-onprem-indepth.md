---
title: オンプレミス データ ゲートウェイの詳細
description: この記事では、オンプレミス ゲートウェイについて詳しく取り上げます。 Analysis Services の使用時にこのサービスが Azure Active Directory やローカルの Active Directory と連動するしくみについて説明します。
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: how-to
ms.date: 07/15/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 0964ad3e391c8e066c31ea7bb53f67e97f254422
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96392359"
---
# <a name="on-premises-data-gateway-in-depth"></a>オンプレミス データ ゲートウェイの詳細

[!INCLUDE [gateway-rewrite](../includes/gateway-rewrite.md)]

この記事の情報は、Power BI および一般的なドキュメントに関する複数の記事に移動されました。各見出しの下のリンクに従って、関連するコンテンツを見つけてください。

## <a name="how-the-gateway-works"></a>ゲートウェイのしくみ

「[オンプレミス データ ゲートウェイのアーキテクチャ](/data-integration/gateway/service-gateway-onprem-indepth)」を参照してください。

## <a name="list-of-available-data-source-types"></a>使用可能なデータ ソースの種類の一覧

「[Manage data sources (データ ソースを管理する)](service-gateway-data-sources.md)」を参照してください。

## <a name="authentication-to-on-premises-data-sources"></a>オンプレミス データ ソースの認証

「[オンプレミス データ ソースの認証](/data-integration/gateway/service-gateway-onprem-indepth#authentication-to-on-premises-data-sources)」を参照してください。

## <a name="authentication-to-a-live-analysis-services-data-source"></a>ライブ Analysis Services データ ソースの認証

「[Authentication to a live Analysis Services data source (ライブ Analysis Services データ ソースの認証)](service-gateway-enterprise-manage-ssas.md#authentication-to-a-live-analysis-services-data-source)」を参照してください。

## <a name="role-based-security"></a>ロール ベース セキュリティ

「[Role-based security (ロール ベースのセキュリティ)](service-gateway-enterprise-manage-ssas.md#role-based-security)」を参照してください。

## <a name="row-level-security"></a>行レベルのセキュリティ

「[Row-level security (行レベルのセキュリティ)](service-gateway-enterprise-manage-ssas.md#row-level-security)」を参照してください。

## <a name="what-about-azure-active-directory"></a>Azure Active Directory の役割

「[Azure Active Directory](/data-integration/gateway/service-gateway-onprem-indepth#azure-active-directory)」を参照してください。

## <a name="how-do-i-tell-what-my-upn-is"></a>自分の UPN を確認する方法

「[自分の UPN を確認する方法](/data-integration/gateway/service-gateway-onprem-indepth#how-do-i-tell-what-my-upn-is)」を参照してください。

## <a name="map-user-names-for-analysis-services-data-sources"></a>Analysis Services データ ソースのユーザー名をマップする

「[Analysis Services データ ソースのユーザー名をマッピングする](service-gateway-enterprise-manage-ssas.md#map-user-names-for-analysis-services-data-sources)」を参照してください。

## <a name="synchronize-an-on-premises-active-directory-with-azure-active-directory"></a>オンプレミスの Active Directory を Azure Active Directory と同期する

「[オンプレミスの Active Directory を Azure Active Directory と同期する](/data-integration/gateway/service-gateway-onprem-indepth#synchronize-an-on-premises-active-directory-with-azure-active-directory)」を参照してください。

## <a name="what-to-do-next"></a>次に行うこと

データソースに関する記事をご覧ください。

[データ ソースの管理](service-gateway-data-sources.md)
[データ ソースの管理 - Analysis Services](service-gateway-enterprise-manage-ssas.md)  
[データ ソースの管理 - SAP HANA](service-gateway-enterprise-manage-sap.md)  
[データ ソースの管理 - SQL Server](service-gateway-enterprise-manage-sql.md)  
[データ ソースの管理 - Oracle](service-gateway-onprem-manage-oracle.md)  
[データ ソースの管理 - インポート/スケジュールされた更新](service-gateway-enterprise-manage-scheduled-refresh.md)  

## <a name="where-things-can-go-wrong"></a>うまくいかない場合

「[オンプレミス データ ゲートウェイのトラブルシューティング](/data-integration/gateway/service-gateway-tshoot)」および「[ゲートウェイのトラブルシューティング - Power BI](service-gateway-onprem-tshoot.md)」を参照してください。

## <a name="sign-in-account"></a>アカウントにサインインする

「[アカウントにサインインする](/data-integration/gateway/service-gateway-onprem-indepth#sign-in-account)」を参照してください。

## <a name="windows-service-account"></a>Windows サービス アカウント

「[Change the on-premises data gateway service account (オンプレミスのデータ ゲートウェイ サービス アカウントを変更する)](/data-integration/gateway/service-gateway-service-account)」を参照してください。

## <a name="ports"></a>ポート

「[ポート](/data-integration/gateway/service-gateway-communication#ports)」を参照してください。

## <a name="forcing-https-communication-with-azure-service-bus"></a>Azure Service Bus との強制的な HTTPS 通信

「[Azure Service Bus との HTTPS 通信を強制する](/data-integration/gateway/service-gateway-communication#force-https-communication-with-azure-service-bus)」を参照してください。

## <a name="support-for-tls-12"></a>TLS 1.2 のサポート

「[ゲートウェイトラフィック用の TLS 1.2](/data-integration/gateway/service-gateway-communication#tls-12-for-gateway-traffic)」を参照してください。

## <a name="how-to-restart-the-gateway"></a>ゲートウェイを再起動する方法

「[ゲートウェイを再起動する](/data-integration/gateway/service-gateway-restart)」を参照してください。

## <a name="next-steps"></a>次の手順

[オンプレミス データ ゲートウェイとは](service-gateway-onprem.md)

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。