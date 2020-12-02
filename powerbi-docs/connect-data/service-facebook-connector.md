---
title: サード パーティのサービス:Power BI Desktop の Facebook コネクタ
description: サード パーティのサービス:Power BI Desktop の Facebook コネクタ
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 02/20/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 4f1faf585643c593e194e965dff2bb29988e27d4
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96402572"
---
# <a name="use-the-facebook-connector-for-power-bi-desktop"></a>Power BI Desktop の Facebook コネクタを使用する
**Power BI Desktop** の Facebook コネクタは、Facebook Graph API に依存します。 そのため、今後機能や可用性が変更になることがあります。

「[Power BI Desktop の Facebook コネクタに関するチュートリアル](desktop-tutorial-facebook-analytics.md)」を参照してください。

> [!IMPORTANT]
> **Facebook データ コネクタの廃止に関する通知:** 2020 年 4 月以降、Excel に Facebook からデータをインポートして更新する機能が正常に機能しなくなります。 それまでは、Facebook *取得と変換 (Power Query)* コネクタを使用できます。 それ以降は Facebook に接続できなくなり、エラー メッセージが表示されるようになります。 予期せぬ結果を防ぐには、Facebook コネクタを使用する既存の *取得と変換 (Power Query)* クエリをできるだけ早く修正または削除することをお勧めします。


Facebook では 2015 年 4 月 30 日に Graph API v1.0 の有効期限が切れました。 Power BI は Facebook コネクタのバックグラウンドで Graph API を使用し、これによりデータに接続でき、分析できます。

2015 年 4 月 30 日より前に作成されたクエリは、すでに機能しなくなっていたり、返すデータが少なくなったりしています。 2015 年 4 月 30 日以降、Power BI では、Facebook API のすべての呼び出しで v2.8 を利用しています。 クエリが 2015 年 4 月 30 日より前に作成され、それ以降に使用されていない場合は、もう一度認証して、要求される新しいアクセス許可のセットを承認しなければならない可能性があります。

すべての変更に調和するように更新プログラムをリリースすることを試みていますが、API は、生成するクエリの結果に影響を与えるように変更される可能性があります。 特定のクエリがサポートされなくなる可能性もあります。 このような依存関係があることから、このコネクタの使用中にはクエリの結果は保証できません。

Facebook API の変更の詳細については、[こちら](https://developers.facebook.com/docs/apps/changelog#v2_0)をクリックしてください。

