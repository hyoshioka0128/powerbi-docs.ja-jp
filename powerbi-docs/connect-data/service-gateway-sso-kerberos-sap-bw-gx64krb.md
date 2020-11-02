---
title: gx64krb5 を用いた SAP BW へのシングル サインオン (SSO) に Kerberos を使用する
description: gx64krb5 を用いた Power BI サービスからの SSO を有効にするように SAP BW サーバーを構成します
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: how-to
ms.date: 10/21/2020
LocalizationGroup: Gateways
ms.openlocfilehash: 6fc8dba8e4cdcb8d8ff38c00f3e477902fe8234e
ms.sourcegitcommit: 3ddfd9ffe2ba334a6f9d60f17ac7243059cf945b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2020
ms.locfileid: "92349462"
---
# <a name="use-kerberos-for-single-sign-on-sso-to-sap-bw-using-gx64krb5"></a>gx64krb5 を用いた SAP BW へのシングル サインオン (SSO) に Kerberos を使用する

この記事では、gx64krb5 を使用して Power BI サービスから SSO を有効にするよう SAP BW データ ソースを構成する方法について説明します。

> [!IMPORTANT]
> SAP では現在、gx64krb5 をサポートしていません。結果として、Microsoft もそのサポートを停止しました。 既存の接続と新規の接続は 2020 年の終わりまで正しく機能しますが、2021 年 1 月 1 日からは機能しなくなります。 代わりに CommonCryptoLib を使用してください。 

> [!NOTE]
> [Kerberos SSO の構成](service-gateway-sso-kerberos.md)に関する記事の手順に加えて、この記事の手順を完了することにより、Power BI サービスの SAP BW アプリケーション サーバー ベースのレポートについて SSO ベースの更新を有効にすることができます。 ただし、SNC ライブラリとしては gx64krb5 ではなく CommonCryptoLib を使用することをお勧めします。 SAP では gx64krb5 がサポートされなくなったため、これをゲートウェイ用に構成するのに必要な手順は、CommonCryptoLib と比べてかなり複雑になっています。 CommonCryptoLib を使用して SSO を構成する方法については、[CommonCryptoLib を使用した SSO 用の SAP BW の構成](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md)に関するページを参照してください。 CommonCryptoLib " *または* " gx64krb5 を SNC ライブラリを使用してください。ただし、両方は使用しないでください。 両方のライブラリの構成手順を行わないでください。

このガイドは広範囲に及んでいるため、説明されている手順の一部を既に完了している場合は、それらはスキップしてかまいません。 たとえば、gx64krb5 を使用して SSO 用に SAP BW サーバーを既に構成している場合があります。

## <a name="set-up-gx64krb5-on-the-gateway-machine-and-the-sap-bw-server"></a>ゲートウェイ コンピューターと SAP BW サーバーで gx64krb5/gsskrb5 を設定する

> [!NOTE]
> gx64krb5 ライブラリは、SAP ではサポートされなくなりました。 詳細については、[SAP Note 352295](https://launchpad.support.sap.com/#/notes/352295) をご覧ください。 gx64krb5 では、データ ゲートウェイから SAP BW メッセージ サーバーへの SSO 接続が許可されていないことに注意してください。SAP BW アプリケーション サーバーへの接続のみが可能です。 [CommonCryptoLib](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md) を SNC ライブラリとして使用する場合、この制限はありません。 他の SNC ライブラリも BW SSO で機能する可能性はありますが、Microsoft は公式にはサポートしていません。

ゲートウェイを介して SSO 接続を完了するには、クライアントとサーバーの両方で gx64krb5 を使用する必要があります。 つまり、クライアントとサーバーの両方で同じ SNC ライブラリを使用する必要があります。

1. [SAP Note 2115486](https://launchpad.support.sap.com/) から gx64krb5.dll をダウンロードします (SAP S-User が必要)。 バージョンが 1.0.11.x 以上になっていることを確認します。 また、ゲートウェイ経由で SSO 接続を試みる前に SAP GUI で SSO 接続をテストする場合は、gsskrb5.dll (32 ビット版のライブラリ) もダウンロードします (推奨)。 SAP GUI は 32 ビットのみであるため、SAP GUI を使用してテストするには、32 ビット版が必要です。

1. ゲートウェイ サービス ユーザーがアクセスできる、ゲートウェイ マシン上の場所に gx64krb5.dll を配置します。 SAP GUI を使用して SSO 接続をテストする場合は、ご使用のマシンにも gsskrb5.dll のコピーを配置し、それを指すように **SNC_LIB** 環境変数を設定します。 ゲートウェイ サービス ユーザーとそのサービス ユーザーが偽装する Active Directory (AD) ユーザーの両方に、gx64krb5.dll のコピーに対する読み取りおよび実行アクセス許可が必要です。 Authenticated Users グループに .dll ファイルに対するアクセス許可を付与することをお勧めします。 テスト目的の場合、ゲートウェイ サービス ユーザーと、テストに使用する Active Directory ユーザーの両方にこれらのアクセス許可を明示的に付与することもできます。

1. gx64krb5.dll を使用して SSO 用に BW サーバーをまだ構成していない場合は、SAP BW サーバー マシン上の .dll の別のコピーを、SAP BW サーバーからアクセスできる場所に配置します。 

    SAP BW サーバーで使用できるように gx64krb5.dll を構成する方法の詳細については、[SAP のドキュメント](https://launchpad.support.sap.com/#/notes/2115486)を参照してください (SAP S-User が必要)。

1. クライアントおよびサーバー マシンで、 **SNC_LIB** および **SNC_LIB_64** 環境変数を設定します。 
    - gsskrb5.dll を使用する場合は、 **SNC_LIB** 変数にその絶対パスを設定します。 
    - gx64krb5.dll を使用する場合は、 **SNC_LIB_64** 変数にその絶対パスを設定します。

## <a name="configure-an-sap-bw-service-user-and-enable-snc-communication-on-the-bw-server"></a>BW サーバー上で SAP BW サービス ユーザーを構成し、SNC 通信を有効にする

gx64krb5 を用いて SNC 通信 (SSO など) 用に SAP BW サーバーをまだ構成していない場合は、このセクションを完了します。

> [!NOTE]
> このセクションでは、BW 用のサービス ユーザーを既に作成し、これに適切な SPN (つまり、 *SAP/* で始まる名前) をバインドしていることを想定しています。

1. サービス ユーザーに、SAP BW アプリケーション サーバーへのアクセス権を付与します。

    1. SAP BW サーバー マシンで、ローカル管理者グループにサービス ユーザーを追加します。 **[コンピューターの管理]** プログラムを開き、サーバーのローカル管理者グループを見つけます。 

        ![[コンピューターの管理] プログラム](media/service-gateway-sso-kerberos/computer-management.png)

    1. ローカル管理者グループをダブルクリックし、 **[追加]** を選んで、グループにサービス ユーザーを追加します。 

    1. **[名前の確認]** を選択し、名前を正しく入力したことを確認してから、 **[OK]** を選択します。

1. SAP BW サーバーのサービス ユーザーを、SAP BW サーバー マシンで SAP BW サーバー サービスを開始するユーザーとして設定します。

    1. **[ファイル名を指定して実行]** を開き、「 **Services.msc** 」と入力します。 

    1. SAP BW アプリケーション サーバー インスタンスに対応するサービスを見つけ、それを右クリックして、 **[プロパティ]** を選択します。

        ![[プロパティ] が強調表示されている [サービス] のスクリーン ショット](media/service-gateway-sso-kerberos/server-properties.png)

    1. **[ログオン]** タブに切り替えて、ユーザーを SAP BW サービス ユーザーに変更します。 

    1. ユーザーのパスワードを入力し、 **[OK]** を選択します。

1. SAP ログオンでサーバーにサインインし、RZ10 トランザクションを使用して次のプロファイル パラメーターを設定します。

    1. **snc/identity/as** プロファイル パラメーターを " *p:&lt;作成した SAP BW サービス ユーザー&gt;* " に設定します。 たとえば、 *p:BWServiceUser\@MYDOMAIN.COM* とします。 *p:* をサービス ユーザーの UPN の前に指定することに注意してください。対照的に、SNC ライブラリとして CommonCryptoLib を使用するときは、 *p:CN =* を UPN の前に指定します。

    1. **snc/gssapi\_lib** プロファイル パラメーターを " *&lt;BW サーバーの gx64krb5.dll のパス&gt;* " に設定します。 SAP BW アプリケーション サーバーがアクセスできる場所にライブラリを配置します。

    1. 次の追加のプロファイル パラメーターを設定し、必要に応じて値を変更します。 最後の 5 つのオプションを使用すると、SNC を構成せずに、SAP ログオンを使用してクライアントを SAP BW サーバーに接続することができます。

        | **設定** | **値** |
        | --- | --- |
        | snc/data\_protection/max | 3 |
        | snc/data\_protection/min | 1 |
        | snc/data\_protection/use | 9 |
        | snc/accept\_insecure\_cpic | 1 |
        | snc/accept\_insecure\_gui | 1 |
        | snc/accept\_insecure\_r3int\_rfc | 1 |
        | snc/accept\_insecure\_rfc | 1 |
        | snc/permit\_insecure\_start | 1 |

    1. **snc/enable** プロパティを 1 に設定します。

1. これらのプロファイル パラメーターを設定した後、サーバー マシンで SAP 管理コンソールを開き、SAP BW インスタンスを再起動します。 

   サーバーが起動しない場合は、プロファイル パラメーターを正しく設定したことを確認します。 プロファイル パラメーターの設定の詳細については、[SAP のドキュメント](https://help.sap.com/saphelp_nw70ehp1/helpdata/en/e6/56f466e99a11d1a5b00000e835363f/frameset.htm)を参照してください。 また、この記事の「[トラブルシューティング](#troubleshooting)」セクションも参照できます。

## <a name="map-an-sap-bw-user-to-an-active-directory-user"></a>SAP BW ユーザーを Active Directory ユーザーにマップする

まだ行っていない場合は、Active Directory ユーザーを SAP BW アプリケーション サーバー ユーザーにマップし、SAP ログオンで SSO 接続をテストします。

1. SAP ログオンを使用して SAP BW サーバーにサインインします。 トランザクション SU01 を実行します。

1. **[User]\(ユーザー\)** には、SSO 接続を有効にする SAP BW ユーザーを入力します。 SAP ログオン ウィンドウの左上付近にある **編集** アイコン (ペンのアイコン) を選択します。

    ![SAP BW [User maintenance]\(ユーザーの管理\) 画面](media/service-gateway-sso-kerberos/user-maintenance.png)

1. **[SNC]** タブを選びます。SNC 名の入力ボックスに、「 *p:&lt;Active Directory ユーザー&gt;@&lt;ドメイン&gt;* 」と入力します。 SNC 名では、Active Directory ユーザーの UPN の前に *p:* を指定する必要があります。 UPN では大文字と小文字が区別されることに注意してください。

   指定した Active Directory ユーザーは、SAP BW アプリケーション サーバーへの SSO アクセスを有効にする対象の個人または組織に属している必要があります。 たとえば、ユーザー testuser\@TESTDOMAIN.COM の SSO アクセスを有効にする場合は、「 *p:testuser\@TESTDOMAIN.COM* 」と入力します。

    ![SAP BW [Maintain Users]\(ユーザー管理\) 画面](media/service-gateway-sso-kerberos/maintain-users.png)

1. 画面の左上付近にある **保存** アイコン (フロッピー ディスクの画像) を選択します。

## <a name="test-sign-in-via-sso"></a>SSO 経由のサインインをテストする

SSO アクセスを有効にした Active Directory ユーザーとして、SSO 経由で SAP ログオンを使用してサーバーにサインインできることを確認します。

1. 先ほど SSO アクセスを有効にした Active Directory ユーザーとして、SAP ログオンがインストールされているドメイン内のマシンにサインインします。 SAP ログオンを起動し、新しい接続を作成します。

1. 先ほどダウンロードした gsskrb5.dll ファイルを、サインインしたマシン上の場所にコピーします。 **SNC_LIB** 環境変数をこの場所の絶対パスに設定します。

1. SAP ログオンを起動し、新しい接続を作成します。

1. **[Create New System Entry]\(新しいシステム エントリの作成\)** 画面で **[User Specified System]\(ユーザー指定のシステム\)** を選択し、 **[Next]\(次へ\)** を選択します。

    ![[Create New System Entry]\(新しいシステム エントリの作成\) 画面](media/service-gateway-sso-kerberos/new-system-entry.png)

1. 次の画面で、アプリケーション サーバー、インスタンス番号、システムの ID などの該当する詳細情報を入力します。 次に、 **[Finish]\(完了\)** を選択します。

1. 新しい接続を右クリックして **[Properties]\(プロパティ\)** を選択し、 **[Network]\(ネットワーク\)** タブを選択します。 

1. **[SNC Name]\(SNC 名\)** ボックスに、「 *p:&lt;SAP BW サービス ユーザーの UPN&gt;* 」と入力します。 たとえば、 *p:BWServiceUser\@MYDOMAIN.COM* とします。 **[OK]** を選択します。

    ![[System Entry Properties]\(システム エントリ プロパティ\) 画面](media/service-gateway-sso-kerberos/system-entry-properties.png)

1. 先ほど作成した接続をダブルクリックして、SAP BW サーバーへの SSO 接続を試みます。 

   この接続に成功した場合は、次のセクションを続行します。 そうでない場合は、このドキュメントの前の手順を見直して正しく完了していることを確認するか、「[トラブルシューティング](#troubleshooting)」のセクションを参照してください。 このコンテキストで SSO を介して SAP BW サーバーに接続できない場合は、ゲートウェイのコンテキストで SSO を使用して SAP BW サーバーに接続することはできません。

## <a name="add-registry-entries-to-the-gateway-machine"></a>ゲートウェイ コンピューターにレジストリ エントリを追加する

必要なレジストリ エントリを、ゲートウェイがインストールされているマシンのレジストリと、Power BI Desktop から接続するマシンに追加します。 これらのレジストリ エントリを追加するには、次のコマンドを実行します。

- ```REG ADD HKLM\SOFTWARE\Wow6432Node\SAP\gsskrb5 /v ForceIniCredOK /t REG_DWORD /d 1 /f```

- ```REG ADD HKLM\SOFTWARE\SAP\gsskrb5 /v ForceIniCredOK /t REG_DWORD /d 1 /f```

## <a name="add-a-new-sap-bw-application-server-data-source-to-the-power-bi-service-or-edit-an-existing-one"></a>Power BI サービスに新しい SAP BW アプリケーション サーバー データ ソースを追加するか、既存のものを編集する

1. データ ソース構成ウィンドウで、Power BI Desktop から SAP BW サーバーにサインインするときと同様に、SAP BW アプリケーション サーバーの **[ホスト名]** 、 **[システム番号]** 、 **[クライアント ID]** を入力します。

1. **[SNC パートナー名]** フィールドに、「 *p:&lt;SAP BW サービス ユーザーにマップした SPN&gt;* 」と入力します。 たとえば、SPN が SAP/BWServiceUser\@MYDOMAIN.COM の場合、 **[SNC パートナー名]** フィールドには「 *p:SAP/BWServiceUser\@MYDOMAIN.COM* 」と入力します。

1. SNC ライブラリでは、 **SNC\_LIB** または **SNC\_LIB\_64** を選択します。 ゲートウェイ コンピューターの **SNC\_LIB\_64** が gx64krb5.dll を指していることを確認します。 または、 **[カスタム]** オプションを選択し、ゲートウェイマシン上の gx64krb5.dll の絶対パスを指定することもできます。

1. **[DirectQuery クエリには Kerberos 経由で SSO を使用します]** を選択し、 **[適用]** を選択します。 テスト接続が成功しなかった場合は、前のセットアップおよび構成手順が正常に完了したことを確認します。

1. [Power BI レポートを実行する](service-gateway-sso-kerberos.md#run-a-power-bi-report)

## <a name="troubleshooting"></a>トラブルシューティング

### <a name="troubleshoot-gx64krb5-configuration"></a>gx64krb5 の構成のトラブルシューティング

次の問題のいずれかが発生した場合は、以下の手順に従って、gx64krb5 インストールと SSO 接続のトラブルシューティングを行います。

* gx64krb5 の設定手順を実行すると、エラーが発生する。 たとえば、プロファイル パラメーターの変更した後に SAP BW サーバーが起動しないとします。 このようなエラーのトラブルシューティングを行うには、サーバー ログ (サーバー マシン上の …work\dev\_w0) を確認してください。 

* サインオンの失敗が原因で SAP BW サービスを開始できない。 SAP BW " *開始* " ユーザーの設定時に間違ったパスワードを指定した可能性があります。 Active Directory 環境内のマシンで SAP BW サービス ユーザーとしてサインインして、パスワードを確認してください。

* 基になるデータ ソース (SQL Server など) の資格情報に関するエラーが発生してサーバーを起動できない場合は、サービス ユーザーに SAP BW データベースへのアクセス権が付与されていることを確認してください。

* 次のメッセージが表示される: " *(GSS-API) 指定された対象は不明か、または到達できません* "。 このエラーは通常、間違った SNC 名が指定されていることを意味します。 クライアント アプリケーションのサービス ユーザーの UPN の前には、 *p:CN=* ではなく、必ず *P:* だけを使用するようにしてください。

* 次のメッセージが表示される: " *(GSS-API) An invalid name was supplied ((GSS-API) 無効な名前が指定されました)* "。 サーバーの SNC ID プロファイル パラメーターの値が *p:* であることを確認してください。

* 次のメッセージが表示される: " *(SNC error) the specified module could not be found ((SNC エラー) 指定されたモジュールが見つかりませんでした)* "。 このエラーは、多くの場合、アクセスするには昇格された特権 (../管理者権限) が必要な場所に gx64krb5 を配置したことによって発生します。

### <a name="troubleshoot-gateway-connectivity-issues"></a>ゲートウェイ接続の問題のトラブルシューティングを行う

1. ゲートウェイのログを確認します。 ゲートウェイ構成アプリケーションを開き、 **[診断]** 、 **[ログのエクスポート]** の順に選択します。 直近のエラーは、確認するログ ファイルの末尾に記載されています。

    ![[診断] が強調表示されているオンプレミス データ ゲートウェイ アプリケーション](media/service-gateway-sso-kerberos/gateway-diagnostics.png)

1. SAP BW トレースを有効にし、生成されたログ ファイルを確認します。 使用できる SAP BW トレースにはいくつかの種類があります (CPIC トレースなど)。

   a. CPIC トレースを有効にするには、次の 2 つの環境変数を設定します。 **CPIC\_TRACE** と **CPIC\_TRACE\_DIR** です。

      最初の変数はトレース レベルを設定し、2 番目の変数はトレース ファイルのディレクトリを設定します。 ディレクトリは、Authenticated Users グループのメンバーが書き込み可能な場所である必要があります。 
 
    b. **CPIC\_TRACE** を *3* に、 **CPIC\_TRACE\_DIR** をトレース ファイルの書き込み先にする任意のディレクトリに設定します。 例:

      ![CPIC トレース](media/service-gateway-sso-kerberos/cpic-tracing.png)

    c. 問題を再現し、 **CPIC\_TRACE\_DIR** にトレース ファイルが含まれていることを確認します。 
    
    d. トレース ファイルの内容を調べて、ブロッキングの問題を特定します。 たとえば、gx64krb5.dll が正しく読み込まれていなかったり、Active Directory ユーザーが SSO 接続を開始すると想定していたユーザーとは異なっていることに気付く場合があります。

## <a name="next-steps"></a>次の手順

オンプレミス データ ゲートウェイと DirectQuery の詳細については、次のリソースを参照してください。

* [オンプレミス データ ゲートウェイとは](/data-integration/gateway/service-gateway-onprem)
* [Power BI の DirectQuery](desktop-directquery-about.md)
* [DirectQuery でサポートされるデータ ソース](power-bi-data-sources.md)
* [DirectQuery と SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery と SAP HANA](desktop-directquery-sap-hana.md)
