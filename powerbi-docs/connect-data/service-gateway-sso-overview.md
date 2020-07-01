---
title: Power BI のゲートウェイ用シングル サインオン (SSO) の概要
description: Power BI からオンプレミス データ ソースへのシングル サインオン (SSO) を有効にするようにゲートウェイを構成します。
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: how-to
ms.date: 10/10/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 4a4bb6ccb74ce08ea1ff63f44b1c2c5406c527ad
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/23/2020
ms.locfileid: "85231307"
---
# <a name="overview-of-single-sign-on-sso-for-gateways-in-power-bi"></a>Power BI のゲートウェイ用シングル サインオン (SSO) の概要

オンプレミスのデータ ゲートウェイを構成することにより、シームレスなシングル サインオン接続を確立して、Power BI のレポートとダッシュボードをオンプレミスのデータでリアルタイムに更新することができます。 ゲートウェイの構成には、[Kerberos](service-gateway-sso-kerberos.md) 制約付き委任を使用する方法と SAML ([Security Assertion Markup Language](service-gateway-sso-saml.md)) を使用する方法とがあります。 オンプレミス データ ゲートウェイは、[DirectQuery](desktop-directquery-about.md) を使用して、または更新用にオンプレミスのデータ ソースに接続することで SSO をサポートします。 

Power BI では、次のデータ ソースがサポートされています。

* SQL Server (Kerberos)
* SAP HANA (Kerberos と SAML)
* SAP BW Application Server (Kerberos)
* SAP BW Message Server (Kerberos) 
* Oracle (Kerberos) 
* Teradata (Kerberos)
* Spark (Kerberos)
* Impala (Kerberos)

現在、[M-extensions](https://github.com/microsoft/DataConnectors/blob/master/docs/m-extensions.md) の SSO はサポートされていません。

ユーザーが Power BI サービスで DirectQuery レポートを操作すると、クロスフィルター、スライス、並べ替え、レポート編集の各操作で、基になるオンプレミス データ ソースに対してクエリがライブ実行される場合があります。 データ ソースへの SSO を構成すると、Power BI を操作しているユーザーの ID でクエリが実行されます (つまり、Web エクスペリエンスまたは Power BI モバイル アプリで)。 そのため、各ユーザーには、そのユーザーが基になるデータ ソースでアクセス許可を持っているデータだけが表示されます。 

また、Power BI サービスで更新が設定されているレポートに SSO を使用するよう設定することもできます。 このデータ ソースに SSO を構成すると、クエリは Power BI 内のデータセットの所有者の ID で実行されます。 そのため、基になるデータ ソースに対するデータセットの所有者の権限に基づいて更新が実行されます。 SSO を使用した更新は、現在 [Kerberos](service-gateway-sso-kerberos.md) の制約付き委任を使用するデータ ソースに対してのみ有効になっています。 

## <a name="query-steps-when-running-sso"></a>SSO を実行するときのクエリ ステップ

SSO を使ったクエリ実行は、次の図に示す 3 つのステップで構成されます。

![SSO クエリ ステップ](media/service-gateway-sso-overview/sso-query-steps.png)

各手順の詳細を次に示します。

1. 構成済みゲートウェイにクエリ要求が送信されるときに、クエリごとに Power BI サービスには "*ユーザー プリンシパル名 (UPN)* "、つまり現在 Power BI サービスにサインインしているユーザーの完全修飾ユーザー名が含まれます。

2. ゲートウェイは、Azure Active Directory の UPN を Active Directory のローカル ID にマップする必要があります。

   a. Azure AD DirSync (*Azure AD Connect* とも呼ばれる) が構成されている場合は、マッピングがゲートウェイで自動的に動作します。

   b.  それ以外の場合、ゲートウェイは、ローカルの Active Directory ドメインに対して検索を実行することにより、Azure AD UPN を参照し、これをローカルの AD ユーザーにマップします。

3. ゲートウェイ サービスのプロセスは、マップされたローカル ユーザーを偽装して、基になるデータベースへの接続を開いた後、クエリを送信します。 データベースと同じマシンにゲートウェイをインストールする必要はありません。

## <a name="next-steps"></a>次のステップ

ゲートウェイ経由での SSO 実現に関する基礎を理解したところで、Kerberos と SAML に関する詳細をお読みください。

* [シングル サインオン (SSO) - Kerberos](service-gateway-sso-kerberos.md)
* [シングル サインオン (SSO) - SAML](service-gateway-sso-saml.md)
