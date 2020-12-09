---
title: Power BI からオンプレミス データ ソースへの SSO に Security Assertion Markup Language (SAML) を使用する
description: Security Assertion Markup Language (SAML) でゲートウェイを構成し、Power BI からオンプレミス データ ソースへの SSO を有効にします。
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: how-to
ms.date: 10/22/2020
LocalizationGroup: Gateways
ms.openlocfilehash: 0f971013d5f57174a26d92281cafe673f1487329
ms.sourcegitcommit: cb6e0202de27f29dd622e47b305c15f952c5769b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2020
ms.locfileid: "96577557"
---
# <a name="use-security-assertion-markup-language-saml-for-sso-from-power-bi-to-on-premises-data-sources"></a>Power BI からオンプレミス データ ソースへの SSO に Security Assertion Markup Language (SAML) を使用する

SSO を有効にすると、Power BI レポートおよびダッシュボードでは、オンプレミスのソース上で構成されているユーザー レベルのアクセス許可を考慮しながら、それらのソースからのデータを簡単に更新できるようになります。 [Security Assertion Markup Language (SAML)](https://www.onelogin.com/pages/saml) を使用し、シームレスなシングル サインオン接続を有効にします。 

## <a name="supported-data-sources"></a>サポートされるデータ ソース

現在、SAP HANA に SAML をご利用いただけます。 SAML を使用した SAP HANA のシングル サインオンの設定と構成の詳細については、「[BI プラットフォームから HANA への SAML SSO](https://blogs.sap.com/2020/03/22/sap-bi-platform-saml-sso-to-hana-database/)」を参照してください。

[Kerberos](service-gateway-sso-kerberos.md) では、追加のデータ ソース (SAP HANA を含む) をサポートしています。

SAP HANA については、SAML SSO 接続を確立する前に暗号化を有効にすることをお勧めします。 暗号化を有効にするには、暗号化された接続を許可するよう HANA サーバーを構成し、HANA サーバーとの通信に暗号化を使用するようゲートウェイを構成します。 HANA ODBC ドライバーは既定で SAML アサーションを暗号化しないため、署名された SAML アサーションは、ゲートウェイから HANA サーバーに "*プレーンテキスト*" で送信され、第三者による傍受や再利用に対して脆弱になります。

> [!IMPORTANT]
> SAP では現在、OpenSSL をサポートしていません。結果として、Microsoft もそのサポートを停止しました。 既存の接続と新規の接続は 2020 年の終わりまで正しく機能しますが、2021 年 1 月 1 日からは機能しなくなります。 代わりに CommonCryptoLib を使用してください。

## <a name="configuring-the-gateway-and-data-source"></a>ゲートウェイとデータ ソースを構成する

SAML を使用するには、SSO を有効にする HANA サーバーとゲートウェイの間に信頼関係を確立する必要があります。 このシナリオでは、ゲートウェイは SAML ID プロバイダー (IdP) として機能します。 この関係を確立するには、さまざまな方法があります。 SAP によって推奨されているのは、SAP 暗号化ライブラリ (CommonCryptoLib または sapcrypto とも呼ばれる) を使用して、信頼関係を確立するための設定手順を完了することです。 詳細については、SAP の公式ドキュメントを参照してください。

次の手順では、HANA サーバーによって信頼されたルート CA を使用してゲートウェイ IdP の X509 証明書に署名することで、HANA サーバーとゲートウェイ IdP の間の信頼関係を確立する方法について説明します。 

### <a name="create-the-certificates"></a>証明書を作成する

次の手順に従って証明書を作成します。

1. SAP HANA を実行しているデバイスで、証明書を格納するための空のフォルダーを作成し、そのフォルダーに移動します。
2. 次のコマンドを実行して、ルート証明書を作成します。

   ```
   openssl req -new -x509 -newkey rsa:2048 -days 3650 -sha256 -keyout CA_Key.pem -out CA_Cert.pem -extensions v3_ca'''
   ```

    この証明書を使用して他の証明書に署名するには、パスフレーズを覚えておく必要があります。
    *CA_Cert.pem* と *CA_Key.pem* が作成されていることがわかります。

   
3. 次のコマンドを実行して、IdP 証明書を作成します。
 
    ```
    openssl req -newkey rsa:2048 -days 365 -sha256 -keyout IdP_Key.pem -out IdP_Req.pem -nodes
    ```
    *IdP_Key.pem* と *IdP_Req.pem* が作成されていることがわかります。

4. ルート証明書を使用して IdP 証明書に署名します。

    ```
    openssl x509 -req -days 365 -in IdP_Req.pem -sha256 -extensions usr_cert -CA CA_Cert.pem -CAkey CA_Key.pem -CAcreateserial -out IdP_Cert.pem
    ```
    *CA_Cert.srl* と *IdP_Cert.pem* が作成されていることがわかります。
    ここでは、*IdP_Cert pem* についてのみ説明します。    

### <a name="create-saml-identity-provider-certificate-mapping"></a>SAML ID プロバイダー証明書のマッピングを作成する

次の手順に従って、SAML ID プロバイダー証明書のマッピングを作成します。

1. **SAP HANA Studio** で、SAP HANA サーバー名を右クリックし、 **[Security]\(セキュリティ\) > [Open Security Console]\(セキュリティ コンソールを開く\) > [SAML Identity Provider]\(SAML ID プロバイダー\)** に移動します。
2. SAP 暗号化ライブラリが選択されていない場合は、選択します。 OpenSSL 暗号化ライブラリ (次の図の左側の選択項目) を使用 "*しない*" でください。これは SAP によって非推奨とされています。

    ![SAP 暗号化ライブラリを選択する](media/service-gateway-sso-saml/service-gateway-sso-saml-01.png)

3. 次の図に示すように、青いインポート ボタンをクリックして、署名された証明書 *IdP_Cert pem* をインポートします。

    ![青色のインポート ボタンを選択する](media/service-gateway-sso-saml/service-gateway-sso-saml-02.png)

"*ID プロバイダー名*" に必ず名前を割り当ててください。

### <a name="import-and-create-the-signed-certificates-in-hana"></a>HANA で署名入り証明書をインポートして作成する

次に、HANA で署名入り証明書をインポートして作成します。 次の手順に従います。

1. **HANA Studio** で、次のクエリを実行します。

    ```
    CREATE CERTIFICATE FROM '<idp_cert_pem_certificate_content>'
    ```
    
    次に例を示します。

    ```
    CREATE CERTIFICATE FROM
    '-----BEGIN CERTIFICATE-----
    MIIDyDCCArCgA...veryLongString...0WkC5deeawTyMje6
    -----END CERTIFICATE-----
    '
    ```

2. PSEwith SAML の目的がない場合は、**HANA Studio** で次のクエリを実行して作成します。
    
    ```
    CREATE PSE SAMLCOLLECTION;<br>set pse SAMLCOLLECTION purpose SAML;<br>
    ```

3. 次のコマンドを使用して、新しく作成した署名入り証明書を PSE に追加します。

    ```
    alter pse SAMLCOLLECTION add CERTIFICATE <certificate_id>;
    ```

    次に例を示します。
    ```
    alter pse SAMLCOLLECTION add CERTIFICATE 1978320;
    ```

    次のクエリを使用して、作成した証明書の一覧を確認できます。
    ```
    select * from PUBLIC"."CERTIFICATES"
    ```

    これで証明書が正しくインストールされました。 次のクエリを実行して確認できます。
    ```
    select * from "PUBLIC"."PSE_CERTIFICATES"
    ```

### <a name="map-the-user"></a>ユーザーをマップする

次の手順に従ってユーザーをマップします。

1. **SAP HANA Studio** で **[Security]\(セキュリティ\)** フォルダーを選択します。

    ![[Security]\(セキュリティ\) フォルダーを選択する](media/service-gateway-sso-saml/service-gateway-sso-saml-03.png)

2. **[User]\(ユーザー\)** を展開し、Power BI ユーザーのマップ先のユーザーを選択します。

3. 次の図で強調表示されている **[SAML]** チェックボックスをオンにし、 **[Configure]\(構成\)** を選択します。

    ![SAML を選択してからリンクを構成する](media/service-gateway-sso-saml/service-gateway-sso-saml-04.png)

4. この記事の前半にある「[SAML ID プロバイダー証明書のマッピングを作成する](#create-saml-identity-provider-certificate-mapping)」セクションで作成した ID プロバイダーを選択します。 [External Identity]\(外部 ID\) に Power BI ユーザーの UPN (通常は、Power BI へのログインにユーザーが使用するメール アドレス) を入力し、 **[Add]\(追加\)** を選択します。  次の図は、オプションと選択項目を示しています。

    ![SAML ID の構成ウィンドウ](media/service-gateway-sso-saml/service-gateway-sso-saml-05.png)

    *ADUserNameReplacementProperty* 構成オプションを使用するようゲートウェイを構成した場合は、Power BI ユーザーの元の UPN を置き換える値を入力します。 たとえば、*ADUserNameReplacementProperty* を *SAMAccountName* に設定する場合は、ユーザーの *SAMAccountName* を入力します。

### <a name="configure-the-gateway"></a>ゲートウェイを構成する

これでゲートウェイの証明書と ID を構成できたので、証明書を pfx 形式に変換し、この証明書を使用するようゲートウェイを構成します。手順は次のとおりです。

1. 次のコマンドを実行し、証明書を pfx 形式に変換します。 このコマンドでは、結果として作成される .pfx ファイルに samlcert.pfx という名前を設定し、そのパスワードを *root* に設定します。

    ```
    openssl pkcs12 -export -out samltest.pfx -in IdP_Cert.pem -inkey IdP_Key.pem -passin pass:root -passout pass:root
    ```

2. ゲートウェイ コンピューターに pfx ファイルをコピーします。

    1. *samltest.pfx* をダブルクリックし、 **[ローカル コンピューター]**  >  **[次へ]** を選択します。

    2. パスワードを入力し、**[次へ]** を選択します。

    3. **[証明書をすべて次のストアに配置する]** を選択し、**[参照]** > **[個人]** > **[OK]** の順に選択します。

    4. **[次へ]** を選択し、**[完了]** を選択します。

       ![証明書のインポート](media/service-gateway-sso-saml/service-gateway-sso-saml-06.png)

3. 証明書の秘密キーにアクセスする許可をゲートウェイ サービス アカウントに付与します。手順は次のとおりです。

    1. ゲートウェイ コンピューターで、Microsoft 管理コンソール (MMC) を実行します。

        ![MMC を実行する](media/service-gateway-sso-saml/run-mmc.png)

    2. **[ファイル]** で **[スナップインの追加と削除]** を選択します。

        ![スナップインを追加する](media/service-gateway-sso-saml/add-snap-in.png)

    3. **[証明書]**  >  **[追加]** の順に選択し、 **[コンピューター アカウント]**  >  **[次へ]** の順に選択します。

    4. **[ローカル コンピューター]**  >  **[完了]**  >  **[OK]** の順に選択します。

    5. **[証明書]**  >  **[個人]**  >  **[証明書]** の順に展開し、証明書を見つけます。

    6. 証明書を右クリックし、**[すべてのタスク]** &gt; **[秘密キーの管理]** の順に移動します。

        ![秘密キーを管理する](media/service-gateway-sso-saml/manage-private-keys.png)

    1. ゲートウェイ サービス アカウントを一覧に追加します。 既定では、アカウントは **NT SERVICE\PBIEgwService** です。 **services.msc** を実行してゲートウェイ サービスを実行しているアカウントを見つけ、**オンプレミス データ ゲートウェイ サービス** を特定することができます。

        ![ゲートウェイ サービス](media/service-gateway-sso-saml/gateway-service.png)

最後に、次の手順を実行して、証明書の拇印をゲートウェイ構成に追加します。

1. 次の PowerShell コマンドを実行して、マシン上の証明書を一覧表示します。

    ```powershell
    Get-ChildItem -path cert:\LocalMachine\My
    ```

2. 作成した証明書の拇印をコピーします。

3. ゲートウェイ ディレクトリ (既定では *C:\Program Files\On-premises data gateway*) に移動します。

4. *PowerBI.DataMovement.Pipeline.GatewayCore.dll.config* を開き、*SapHanaSAMLCertThumbprint* セクションを見つけます。 コピーした拇印を貼り付けます。

5. ゲートウェイ サービスを再起動します。

## <a name="running-a-power-bi-report"></a>Power BI レポートを実行する

Power BI の **[Manage Gateway]\(ゲートウェイの管理\)** ページを使用して SAP HANA データ ソースを構成できるようになりました。 **[詳細設定]** で、SAML 経由で SSO を有効にします。 こうすることで、そのデータ ソースにバインドされているレポートやデータセットを発行できます。

   ![詳細設定](media/service-gateway-sso-saml/advanced-settings.png)

## <a name="troubleshooting"></a>トラブルシューティング

SAML ベースの SSO を構成した後、Power BI ポータルで次のエラーが表示される場合があります: "*指定された資格情報は SapHana のソースに使用できません*"。 このエラーは、SAML 資格情報が SAP HANA によって拒否されたことを示します。

サーバー側の認証トレースを利用すれば、SAP HANA での資格情報の問題をトラブルシューティングするための詳細情報が得られます。 以下の手順に従って、ご利用の SAP HANA サーバーに対するトレースを構成します。

1. SAP HANA サーバー上で、次のクエリを実行して認証トレースをオンにします。

    ```
    ALTER SYSTEM ALTER CONFIGURATION ('indexserver.ini', 'SYSTEM') set ('trace', 'authentication') = 'debug' with reconfigure 
    ```

1. 問題を再現します。

1. HANA Studio で、管理コンソールを開いて、**[Diagnosis Files]\(診断ファイル\)** タブを選択します。

1. 最新のインデックス サーバー トレースを開いて、*SAMLAuthenticator.cpp* を検索します。

    次のように、根本原因を示す詳細なエラー メッセージを見つける必要があります。

    ```
    [3957]{-1}[-1/-1] 2018-09-11 21:40:23.815797 d Authentication   SAMLAuthenticator.cpp(00091) : Element '{urn:oasis:names:tc:SAML:2.0:assertion}Assertion', attribute 'ID': '123123123123123' is not a valid value of the atomic type 'xs:ID'.
    [3957]{-1}[-1/-1] 2018-09-11 21:40:23.815914 i Authentication   SAMLAuthenticator.cpp(00403) : No valid SAML Assertion or SAML Protocol detected
    ```

1. トラブルシューティングが完了したら、次のクエリを実行して認証トレースをオフにします。

    ```
    ALTER SYSTEM ALTER CONFIGURATION ('indexserver.ini', 'SYSTEM') UNSET ('trace', 'authentication');
    ```

## <a name="next-steps"></a>次の手順

オンプレミス データ ゲートウェイと DirectQuery の詳細については、次のリソースを参照してください。

* [オンプレミス データ ゲートウェイとは](/data-integration/gateway/service-gateway-onprem)
* [Power BI の DirectQuery](desktop-directquery-about.md)
* [DirectQuery でサポートされるデータ ソース](power-bi-data-sources.md)
* [DirectQuery と SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery と SAP HANA](desktop-directquery-sap-hana.md)
