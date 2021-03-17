---
title: SAP HANA への シングル サインオン (SSO) に Kerberos を使用する
description: Power BI サービスからの SSO を有効にするように SAP HANA サーバーを構成します
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: how-to
ms.date: 03/02/2021
LocalizationGroup: Gateways
ms.openlocfilehash: a8d5bbbb7a08629c65e4c26ba527c9fadf2b3e78
ms.sourcegitcommit: 818b4542925c927a0dfcb469dbbd8984b5810a21
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/16/2021
ms.locfileid: "103602592"
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

## <a name="troubleshooting"></a>トラブルシューティング

このセクションでは、Power BI サービスで SAP HANA へのシングル サインオン (SSO) を利用するために Kerberos を使用する場合のトラブルシューティング手順について詳しく説明します。 これらのトラブルシューティング手順は、発生している可能性のある問題を自己診断し、修正するのに役立ちます。

### <a name="verifying-and-troubleshooting-gateway-errors"></a>ゲートウェイ エラーの検証とトラブルシューティング

このセクションの手順を実行するには、[ゲートウェイ ログを収集する](/data-integration/gateway/service-gateway-tshoot#collect-logs-from-the-on-premises-data-gateway-app)必要があります。

#### <a name="ssl-error-certificate"></a>SSL エラー (証明書)

**エラーの症状:**

この問題には複数の症状があります。 新しいデータ ソースを追加しようとする際には、次のようなエラーが表示される場合があります。

```Unable to connect: We encountered an error while trying to connect to . Details: "We could not register this data source for any gateway instances within this cluster. Please find more details below about specific errors for each gateway instance."```

レポートを作成または更新しようとする際には、次のような内容が表示される場合があります。

:::image type="content" source="media/service-gateway-sso-kerberos-sap-hana/sap-hana-kerberos-troubleshooting-01.png" alt-text="SSL エラーのトラブルシューティングを行うウィンドウ":::

Mashup[date]*.log を調べると、次のエラーが見つかります。

```A connection was successfully established with the server, but then an error occurred during the login process and The certificate chain was issued by an authority that is not trusted.```

**解決策:**

この SSL エラーを解決するには、次の図のように、データ ソース接続にアクセスし、 **[サーバー証明書の検証]** を **[いいえ]** に設定します。

:::image type="content" source="media/service-gateway-sso-kerberos-sap-hana/sap-hana-kerberos-troubleshooting-02.png" alt-text="SSL エラーを解決するウィンドウ":::

これを選択すると、エラーは表示されなくなります。

#### <a name="impersonation"></a>権限借用

権限借用のログ エントリには、次のようなエントリが含まれます: ```About to impersonate user DOMAIN\User (IsAuthenticated: True, ImpersonationLevel: Impersonation).``` 

このログ エントリの重要な要素は、*ImpersonationLevel:* エントリの後の情報です。 *Impersonation* 以外の値が指定されている場合は、権限借用が正しく行われていないということになります。

**解決策:**

「[ゲートウェイ コンピューターでゲートウェイ サービス アカウントのローカル ポリシー権限を付与する](service-gateway-sso-kerberos.md#grant-the-gateway-service-account-local-policy-rights-on-the-gateway-machine)」の手順に従うことで、ImpersonationLevel を適切に設定できます。

構成ファイルが変更されたら、ゲートウェイ サービスを再起動して変更を有効にします。

**検証:**

レポートを更新または作成し、ゲートウェイ ログを収集します。 直近の *GatewayInfo* ファイルを開き、次の文字列を確認します: ```About to impersonate user DOMAIN\User (IsAuthenticated: True, ImpersonationLevel: Impersonation)```。 *ImpersonationLevel:* の設定が *Impersonation* になっていることを確認します。


#### <a name="delegation"></a>委任
通常、委任の問題は、Power BI サービスで一般的なエラーとして表示されます。 問題が委任の問題でないことを確認するには、Wireshark トレースを収集し、フィルターとして *Kerberos* を使用します。 Wireshark の詳細と、Kerberos エラーの詳細については、[ネットワーク キャプチャでの Kerberos エラーに関するブログ記事](/archive/blogs/askds/kerberos-errors-in-network-captures)を参照してください。

次の症状とトラブルシューティング手順は、いくつかの一般的な問題を解決するのに役立ちます。

**サービス プリンシパル名 (SPN) に関する問題:** SPN の問題が発生した場合、Mashup[date]*.log を調べると、次のエラーが見つかります: ```The import [table] matches no exports. Did you miss a module reference?:```

WireShark トレースを使用してさらに調査すると、**KRB4KDC_ERR_S_PRINCIPAL_UNKOWN** というエラーが確認できます。これは、サービス プリンシパル名 (SPN) が見つからなかったか、または存在しないことを意味します。 次に例を示します。

:::image type="content" source="media/service-gateway-sso-kerberos-sap-hana/sap-hana-kerberos-troubleshooting-07.png" alt-text="SPN エラー":::

**解決策:**

このようなサービス プリンシパル名 (SPN) の問題を解決するには、サービス アカウントに SPN を追加する必要があります。 詳細については、[こちらの SAP 記事](https://help.sap.com/viewer/6b94445c94ae495c83a19646e7c3fd56/LATEST/en-US/c786f2cfd976101493dfdf14cf9bcfb1.html)に記載されている SAP ドキュメントを参照してください。

それらの手順を実行することに加えて、次のセクションで説明されている解決手順も実行してください。また、次のセクションで説明するように、「**資格情報が見つからない問題**」セクションの症状にも対処する必要があります。

**資格情報が見つからない問題:** この問題に関しては、明らかな症状が現れない可能性があります。 Mashup[date]*.log を調べると、次のエラーが見つかります。

```29T20:21:34.6679184Z","Action":"RemoteDocumentEvaluator/RemoteEvaluation/HandleException","HostProcessId":"1396","identity":"DirectQueryPool","Exception":"Exception:\r\nExceptionType: Microsoft.Mashup.Engine1.Runtime.ValueException, Microsoft.MashupEngine, Version=1.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35\r\nMessage:```

同じファイルについてさらに詳しく調べると、次の (役に立たない) エラーが見つかります: ```No credentials are available in the security package```

Wireshark トレースをキャプチャすると、次のエラーが見つかります: *KRB5KDC_ERR_BADOPTION*。

:::image type="content" source="media/service-gateway-sso-kerberos-sap-hana/sap-hana-kerberos-troubleshooting-08.png" alt-text="資格情報が見つからないエラー":::

通常、これらのエラーは、SPN *hdb/hana2-s4-sso2.westus2.cloudapp.azure.com* が見つかるものの、ゲートウェイ サービス アカウントの **[委任]** タブにある **[このアカウントが委任された資格情報を提示できるサービス]** に含まれていないことを意味しています。

**解決策:**

*資格情報が見つからない* 問題を解決するには、「[標準の Kerberos の制約付き委任用にゲートウェイ サービス アカウントを構成する](service-gateway-sso-kerberos.md#configure-the-gateway-service-account-for-standard-kerberos-constrained-delegation)」で説明されている手順に従います。 正常に完了すると、ゲートウェイ サービス アカウントの [委任] タブで、 **[このアカウントが委任された資格情報を提示できるサービス]** の一覧に hdb/fqdn が反映されます。


**検証:** 前の手順を実行すると、問題が解決されます。 それでも Kerberos の問題が発生する場合は、**Power BI ゲートウェイ** か、HANA サーバー自体で構成が間違っている可能性があります。 

#### <a name="credentials-errors"></a>資格情報のエラー
資格情報エラーが発生した場合は、ログまたはトレースのエラーで、"*資格情報が無効*" であることを示すエラーか、または類似のエラーが示されます。 これらのエラーは、接続のデータ ソース側 (SAP HANA など) では異なるかたちで示される場合があります。 次の画像は、エラーの例を示したものです。

:::image type="content" source="media/service-gateway-sso-kerberos-sap-hana/sap-hana-kerberos-troubleshooting-09.png" alt-text="無効な資格情報エラー":::

**症状 1**: HANA 認証トレースに、次のようなエントリが見つかる場合があります。

```[Authentication|manager.cpp:166] Kerberos: Using Service Principal Name johnny@CONTOSO.COM with name type: GSS_KRB5_NT_PRINCIPAL_NAME [Authentication|methodgssinitiator.cpp:367] Got principal name: johnny@CONTOSO.COM```

**解決方法**: 「[ゲートウェイ マシンでユーザー マッピングの構成パラメーターを設定する (必要な場合)](service-gateway-sso-kerberos.md#set-user-mapping-configuration-parameters-on-the-gateway-machine-if-necessary)」で説明されている手順を実行します (**Azure AD Connect** サービスが既に構成されている場合でも実行してください)。

**検証**: 正常に完了すると、Power BI サービスでレポートを正常に読み込めるようになります。

**症状 2**: HANA 認証トレースに、次のようなエントリが見つかる場合があります。

```Authentication ManagerAcceptor.cpp(00233) : Extending list of expected external names by johnny@CONTOSO.COM (method: GSS) Authentication AuthenticationInfo.cpp(00168) : ENTER getAuthenticationInfo (externalName=johnny@CONTOSO.COM) Authentication AuthenticationInfo.cpp(00237) : Found no user with expected external name!```

**解決方法**: **[HANA ユーザー]** で Kerberos 外部 ID をチェックして、それらが適切に一致しているかどうかを確認します。

**検証**: 修正されると、Power BI サービスでレポートを作成または更新できるようになります。


## <a name="next-steps"></a>次の手順

オンプレミス データ ゲートウェイと DirectQuery の詳細については、次のリソースを参照してください。

* [オンプレミス データ ゲートウェイとは](/data-integration/gateway/service-gateway-onprem)
* [Power BI の DirectQuery](desktop-directquery-about.md)
* [DirectQuery でサポートされるデータ ソース](power-bi-data-sources.md)
* [DirectQuery と SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery と SAP HANA](desktop-directquery-sap-hana.md)