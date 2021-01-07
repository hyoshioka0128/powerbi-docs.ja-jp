---
title: SAP HANA への シングル サインオン (SSO) に Kerberos を使用する
description: Power BI サービスからの SSO を有効にするように SAP HANA サーバーを構成します
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: how-to
ms.date: 12/16/2020
LocalizationGroup: Gateways
ms.openlocfilehash: 3f50b174e8293d75a0077e1799cb64ff4fdcd696
ms.sourcegitcommit: 5c09d121d3205e65fb33a2eca0e60bc30e777773
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/18/2020
ms.locfileid: "97675122"
---
# <a name="use-kerberos-for-single-sign-on-sso-to-sap-hana"></a>SAP HANA への シングル サインオン (SSO) に Kerberos を使用する

> [!IMPORTANT]
> [SAP では OpenSSL がサポートされなくなったため](https://help.sap.com/viewer/b3ee5778bc2e4a089d3299b82ec762a7/2.0.05/en-US/de15ffb1bb5710148386ffdfd857482a.html)、Microsoft もそのサポートを停止しました。 既存の接続は引き続き機能しますが、2021 年 2 月以降、新しい接続を作成することはできなくなります。 今後は代わりに CommonCryptoLib を使用してください。

この記事では、Power BI サービスからの SSO を有効にするように SAP HANA データ ソースを構成する方法を説明します。

> [!NOTE]
> Kerberos SSO を使用する SAP HANA ベースのレポートを更新する前に、この記事の手順と [Kerberos SSO の構成](service-gateway-sso-kerberos.md)に関するページの手順を両方済ませておいてください。

## <a name="enable-sso-for-sap-hana"></a>SAP HANA に対する SSO を有効にする

SAP HANA に対する SSO を有効にするには、次の手順のようにします。

1. SAP HANA サーバーが必要な最小バージョンを実行していることを確認します。これは、SAP HANA サーバー プラットフォームのレベルによって異なります。
   - [HANA 2 SPS 01 改訂 012.03](https://launchpad.support.sap.com/#/notes/2557386)
   - [HANA 2 SPS 02 改訂 22](https://launchpad.support.sap.com/#/notes/2547324)
   - [HANA 1 SP 12 改訂 122.13](https://launchpad.support.sap.com/#/notes/2528439)

2. ゲートウェイ マシンに、最新の SAP HANA ODBC ドライバーをインストールします。 最小バージョンは 2017 年 8 月の HANA ODBC バージョン 2.00.020.00 です。

3. SAP HANA サーバーが Kerberos ベースの SSO 用に構成されていることを確認します。 Kerberos を使用した SAP HANA の SSO の設定に関する詳細については、SAP HANA セキュリティ ガイドの「[「Single Sign-on Using Kerberos](https://help.sap.com/viewer/b3ee5778bc2e4a089d3299b82ec762a7/2.0.03/1885fad82df943c2a1974f5da0eed66d.html)」(Kerberos を用いたシングル サインオン) をご覧ください。 また、このページからのリンク (特に SAP Note 1837331 – HOWTO HANA DBSSO Kerberos/Active Directory) もご確認ください。

また、次の追加の手順に従うことをお勧めします。これにより、パフォーマンスがわずかに向上します。

1. ゲートウェイのインストール ディレクトリで、次の構成ファイルを見つけて開きます: Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config.

2. `FullDomainResolutionEnabled` プロパティを見つけて、その値を `True` に変更します。

    ```xml
    <setting name=" FullDomainResolutionEnabled " serializeAs="String">
          <value>True</value>
    </setting>
    ```

次に、[Power BI レポートを実行します](service-gateway-sso-kerberos.md#run-a-power-bi-report)。

## <a name="next-steps"></a>次の手順

オンプレミス データ ゲートウェイと DirectQuery の詳細については、次のリソースを参照してください。

* [オンプレミス データ ゲートウェイとは](/data-integration/gateway/service-gateway-onprem)
* [Power BI の DirectQuery](desktop-directquery-about.md)
* [DirectQuery でサポートされるデータ ソース](power-bi-data-sources.md)
* [DirectQuery と SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery と SAP HANA](desktop-directquery-sap-hana.md)
