---
title: 組織向けの埋め込みのときに Power BI アプリを自動インストールする
description: 組織向けの埋め込みのときに Power BI アプリを自動インストールする方法について説明します。
ms.subservice: powerbi-developer
author: KesemSharabi
ms.author: kesharab
ms.topic: how-to
ms.service: powerbi
ms.custom: ''
ms.date: 04/16/2019
ms.openlocfilehash: f84527a189be0f78f73470cbc475f45206dd8cf1
ms.sourcegitcommit: 5ccab484cf3532ae3a16acd5fc954b7947bd543a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2020
ms.locfileid: "93412397"
---
# <a name="auto-install-power-bi-apps-when-embedding-for-your-organization"></a>組織向けの埋め込みのときに Power BI アプリを自動インストールする

アプリからコンテンツを埋め込むには、埋め込みを行うユーザーが[そのアプリにアクセス](../../collaborate-share/service-create-distribute-apps.md)できる必要があります。 そのユーザー向けにアプリがインストールされている場合、埋め込みはスムーズに行われます。 詳細については、「[アプリからレポートやダッシュボードを埋め込む](embed-from-apps.md)」を参照してください。 すべてのアプリが[自動的にインストール](https://powerbi.microsoft.com/blog/automatically-install-apps/)されるように PowerBI.com で定義することはできます。 ただし、このアクションはテナント レベルで行われ、すべてのアプリに適用されます。

## <a name="auto-install-app-on-embedding"></a>埋め込み時にアプリを自動インストールする

ユーザーがアプリにアクセスできる場合でも、アプリがインストールされていなければ、埋め込みは失敗します。 アプリからの埋め込み時にこのようなエラーを回避するため、埋め込み時にアプリの自動インストールを許可することができます。 このアクションは、ユーザーが埋め込もうとしているアプリがインストールされていない場合、ユーザーに代わって自動的にインストールされるということを意味します。 そのため、必要なコンテンツがすぐに埋め込まれ、ユーザーにスムーズなエクスペリエンスが提供されることになります。

## <a name="embed-for-power-bi-users-user-owns-data"></a>Power BI ユーザー向けに埋め込む (ユーザーがデータを所有)

ユーザーにアプリの自動インストールを許可するには、[アプリケーションの登録](register-app.md#register-an-azure-ad-app)時に 'コンテンツの作成' アクセス許可をアプリケーションに付与するか、アプリを登録済みの場合は追加する必要があります。

![アプリのコンテンツ作成登録](media/embed-auto-install-app/register-app-create-content.png)

次に、埋め込み URL にアプリ ID を指定する必要があります。 アプリ ID を指定するには、アプリの作成者はまずアプリをインストールし、サポートされている [Power BI Rest API](/rest/api/power-bi/) 呼び出し ([レポートの取得](/rest/api/power-bi/reports/getreports)または[ダッシュボードの取得](/rest/api/power-bi/dashboards/getdashboards)) のいずれか 1 つを使用する必要があります。 その後アプリの作成者は REST API 応答から埋め込み URL を取得する必要があります。 コンテンツがアプリからのものである場合、アプリ ID は URL 内に含まれています。  埋め込み URL の取得後は、定期的な埋め込みに使用できます。

## <a name="secure-embed"></a>安全な埋め込み

アプリの自動インストールを使用するには、アプリの作成者はまずアプリをインストールし、PowerBI.com 上のそのアプリに移動し、レポートを表示して、通常の方法でリンクを取得する必要があります。 そのリンクを使用可能なアプリにアクセスできる他のすべてのユーザーは、そのレポートを埋め込むことができます。

## <a name="considerations-and-limitations"></a>考慮事項と制限事項

* レポートとダッシュボードの埋め込みは、このシナリオでのみ実行できます。

* アプリが所有するデータと SharePoint の埋め込みシナリオでは、この機能は現在サポートされていません。