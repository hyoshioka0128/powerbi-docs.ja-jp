---
title: サービス プリンシパルの制限事項
description: サービス プリンシパルの制限事項
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 06/06/2020
ms.custom: include file
ms.openlocfilehash: f55cf56edbc26d58dcfb5d67f46a908625ebcf30
ms.sourcegitcommit: 37bd34053557089c4fbf0e05f78e959609966561
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/10/2020
ms.locfileid: "94425353"
---
## <a name="considerations-and-limitations"></a>考慮事項と制限事項

* サービス プリンシパルは、[新しいワークスペース](../collaborate-share/service-create-the-new-workspaces.md)でのみ動作します。
* サービス プリンシパルを使用する場合は、 **マイ ワークスペース** はサポートされません。
* 運用環境に移行するときは、容量が必要です。
* サービス プリンシパルを使用して Power BI ポータルにサインインすることはできません。
* Power BI 管理ポータル内の開発者向け設定でサービス プリンシパルを有効にするには、Power BI 管理者権限が必要です。
* [組織のアプリケーションへの埋め込み](../developer/embedded/embed-sample-for-your-organization.md)では、サービス プリンシパルを使用することはできません。
* [データフロー](../transform-model/dataflows/dataflows-introduction-self-service.md)管理はサポートされていません。
* サービス プリンシパルでは現在、管理 API は一切サポートされていません。
* サービス プリンシパルを [Azure Analysis Services](/azure/analysis-services/analysis-services-overview) データ ソースと共に使用する場合、サービス プリンシパル自体に Azure Analysis Services インスタンスのアクセス許可が含まれている必要があります。 この目的のためのサービス プリンシパルを含むセキュリティ グループを使用することはできません。