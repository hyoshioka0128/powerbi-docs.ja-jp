---
title: オンプレミスのデータ ゲートウェイ
description: この記事は Power BI のオンプレミス データ ゲートウェイの概要です。 このゲートウェイを使用し、DirectQuery データ ソースを操作できます。 また、このゲートウェイを使用し、オンプレミス データでクラウド データセットを更新できます。
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
LocalizationGroup: Gateways
ms.date: 07/15/2019
ms.openlocfilehash: 2d0b5ff4bbf14012eb0a60759007fa0d021befea
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96402158"
---
# <a name="what-is-an-on-premises-data-gateway"></a>オンプレミス データ ゲートウェイとは

[!INCLUDE [gateway-rewrite](../includes/gateway-rewrite.md)]

オンプレミス データ ゲートウェイはブリッジとして機能し、オンプレミス データ (クラウド内に存在しないデータ) といくつかの Microsoft クラウド サービスとの間でデータをすばやく安全に転送できます。 そのようなクラウド サービスには、Power BI、PowerApps、Power Automate、Azure Analysis Services、Azure Logic Apps があります。 ゲートウェイを使用することにより、組織はオンプレミス ネットワーク上のデータベースやその他のデータソースを維持しながら、そのオンプレミス データをクラウド サービスで安全に使用することができます。

## <a name="how-the-gateway-works"></a>ゲートウェイのしくみ

![ゲートウェイの概要](media/service-gateway-onprem/on-premises-data-gateway.png)

ゲートウェイのしくみの詳細については、「[オンプレミス データ ゲートウェイのアーキテクチャ](/data-integration/gateway/service-gateway-onprem-indepth)」を参照してください。

## <a name="types-of-gateways"></a>ゲートウェイの種類

ゲートウェイには 2 種類あって、それぞれ異なるシナリオで使用されます。

* **オンプレミス データ ゲートウェイ** の場合、複数のユーザーが複数のオンプレミスのデータ ソースに接続できます。 単一のゲートウェイ インストールで、サポートされているすべてのサービスでオンプレミス データゲートウェイを使用できます。 このゲートウェイは、複数のユーザーが複数のデータ ソースにアクセスする複雑なシナリオに適しています。

* **オンプレミス データ ゲートウェイ (個人用モード)** の場合、1 人のユーザーがソースに接続できます。他のユーザーとは共有できません。 オンプレミスのデータ ゲートウェイ (個人用モード) は、Power BI でのみ使用できます。 このゲートウェイは、レポートを作成するユーザーが 1 人だけであり、データ ソースを他のユーザーと共有する必要がないシナリオに適しています。

## <a name="use-a-gateway"></a>ゲートウェイの使用

ゲートウェイを使用するための 4 つの主要な手順があります。

1. [ゲートウェイをダウンロードして、ローカル コンピューターにインストールします](/data-integration/gateway/service-gateway-install)。
1. ご利用のファイアウォールやその他のネットワーク要件に基づいてゲートウェイを[構成](/data-integration/gateway/service-gateway-app)します。
1. 他のネットワーク要件も管理および操作できる[ゲートウェイ管理者を追加](/data-integration/gateway/service-gateway-manage)します。
1. [ゲートウェイを使用](service-gateway-sql-tutorial.md)して、オンプレミスのデータ ソースを更新します。
1. エラーが発生した場合にゲートウェイの[トラブルシューティング](service-gateway-onprem-tshoot.md)を行います。

## <a name="next-steps"></a>次のステップ

* [オンプレミス データ ゲートウェイのインストール](/data-integration/gateway/service-gateway-install)

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。
