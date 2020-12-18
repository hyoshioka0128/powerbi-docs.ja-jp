---
title: ゲートウェイのトラブルシューティング - Power BI
description: この記事では、オンプレミス データ ゲートウェイと Power BI に関する問題を解決するための方法を紹介します。 既知の問題を解決できる可能性がある回避策と便利なツールを紹介します。
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: troubleshooting
ms.date: 12/10/2020
LocalizationGroup: Gateways
ms.openlocfilehash: de8d24af0dbaa0ed4b27efca140cf29acda9df76
ms.sourcegitcommit: 772c65b7b440ab082510bf3f64b871d19139d451
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/12/2020
ms.locfileid: "97353418"
---
# <a name="troubleshoot-gateways---power-bi"></a>ゲートウェイのトラブルシューティング - Power BI

[!INCLUDE [gateway-rewrite](../includes/gateway-rewrite.md)]

この記事では、Power BI でオンプレミス データ ゲートウェイを使用するときの一般的な問題について説明します。 ここに記載されていない問題が発生した場合、Power BI [コミュニティ](https://community.powerbi.com) サイトを使用できます。 あるいは、[サポート チケット](https://powerbi.microsoft.com/support)を作成できます

## <a name="configuration"></a>構成

### <a name="error-power-bi-service-reported-local-gateway-as-unreachable-restart-the-gateway-and-try-again"></a>エラー: Power BI サービスからローカル ゲートウェイが到達不可という報告がありました。 ゲートウェイを再起動してからもう一度お試しください

構成の最後に、Power BI サービスがもう一度呼び出されてゲートウェイが検証されます。 Power BI サービスでは、ゲートウェイがライブ状態として報告されません。 Windows サービスを再起動すると、通信が成功する場合があります。 「[Collect logs from the on-premises data gateway app](/data-integration/gateway/service-gateway-tshoot#collect-logs-from-the-on-premises-data-gateway-app)」 (オンプレミス データ ゲートウェイ アプリからログを収集する) の説明に従ってログを収集して確認し、詳細な情報を取得できます。

## <a name="data-sources"></a>データ ソース

### <a name="error-unable-to-connect-details-invalid-connection-credentials"></a>エラー: 接続できません。 詳細:"接続の資格情報が正しくありません"

**[詳細を表示する]** には、データ ソースから受信したエラー メッセージが表示されます。 SQL Server の場合、次のようなメッセージが表示されます。

```output
Login failed for user 'username'.
```

ユーザー名とパスワードが正しいことを確認します。 また、これらの資格情報を使用してデータ ソースに正常に接続できることを確認します。 使用されているアカウントが認証方法と一致していることを確認してください。

### <a name="error-unable-to-connect-details-cannot-connect-to-the-database"></a>エラー: 接続できません。 詳細:"データベースに接続できません"

サーバーには接続できましたが、指定されたデータベースには接続できませんでした。 データベースの名前を確認し、そのデータベースにアクセスできる適切なアクセス許可がユーザー資格情報に付与されていることを確認します。

**[詳細を表示する]** には、データ ソースから受信したエラー メッセージが表示されます。 SQL Server の場合、次のように表示されます。

```output
Cannot open database "AdventureWorks" requested by the login. The login failed. Login failed for user 'username'.
```

### <a name="error-unable-to-connect-details-unknown-error-in-data-gateway"></a>エラー: 接続できません。 詳細:"Unknown error in data gateway" (データ ゲートウェイでの不明なエラー)

このエラーは、さまざまな理由で発生する可能性があります。 ゲートウェイをホストしているコンピューターからデータ ソースに接続できることを必ず確認してください。 サーバーにアクセスできない場合も、この状況が発生することがあります。

**[詳細を表示する]** には、**DM_GWPipeline_UnknownError** のエラー コードが表示されます。

また、 **[イベント ログ]**  >  **[アプリケーションとサービス ログ]**  >  **[オンプレミス データ ゲートウェイ サービス]** の順に選択し、詳細を確認できます。

### <a name="error-we-encountered-an-error-while-trying-to-connect-to-server-details-we-reached-the-data-gateway-but-the-gateway-cant-access-the-on-premises-data-source"></a>エラー: \<server\> に接続しようとしているときにエラーが発生しました。 詳細:"data gateway に到達しましたが、ゲートウェイがオンプレミスのデータ ソースにアクセスできません。"

指定したデータ ソースに接続できませんでした。 そのデータ ソースについて提供された情報を検証してください。

**[詳細を表示する]** には、**DM_GWPipeline_Gateway_DataSourceAccessError** のエラー コードが表示されます。

基になっているエラー メッセージが次のような場合は、データ ソースに対して使用しているアカウントがその Analysis Services インスタンスのサーバー管理者ではないことを意味しています。 詳細は、「[Grant server admin rights to an Analysis Services instance](/sql/analysis-services/instances/grant-server-admin-rights-to-an-analysis-services-instance)」 (Analysis Services インスタンスにサーバー管理者権限を付与する) を参照してください。

```output
The 'CONTOSO\account' value of the 'EffectiveUserName' XML for Analysis property is not valid.
```

基になっているエラー メッセージが次のような場合は、Analysis Services のサービス アカウントに [token-groups-global-and-universal](/windows/win32/adschema/a-tokengroupsglobalanduniversal) (TGGAU) ディレクトリ属性がない可能性があります。

```output
The username or password is incorrect.
```

Windows 2000 以前と互換性のあるアクセス権を持つドメインでは TGGAU 属性は有効になります。 最近作成されたドメインではこの属性が既定で有効になりません。 詳細は、「[一部のアプリケーションや API でアカウント オブジェクトの承認情報に対するアクセス許可が必要になる ](https://support.microsoft.com/kb/331951)」を参照してください。

属性が有効であるかどうかを確認するには、次の手順を行います。

1. SQL Server Management Studio 内の Analysis Services マシンに接続します。 詳細接続プロパティ内に、該当するユーザーの EffectiveUserName を含め、この追加でエラーが再現されるかどうかを確認します。
2. dsacls Active Directory ツールを使用すれば、属性がリストされるかどうかを確認できます。 このツールはドメイン コントローラーにあります。 アカウントのドメインの識別名を確認し、ツールにその名前を渡す必要があります。

   ```console
   dsacls "CN=John Doe,CN=UserAccounts,DC=contoso,DC=com"
   ```

    結果は次のようになります。

   ```console
   Allow BUILTIN\Windows Authorization Access Group
                                   SPECIAL ACCESS for tokenGroupsGlobalAndUniversal
                                   READ PROPERTY
   ```

この問題を修正するには、Analysis Services Windows サービスで使用するアカウントで TGGAU を有効にする必要があります。

#### <a name="another-possibility-for-the-username-or-password-is-incorrect"></a>"ユーザー名またはパスワードが間違っている" 可能性もある

Analysis Services サーバーがユーザーとは異なるドメインにあり、双方向の信頼が確立されていない場合にも、このエラーが発生することがあります。

ドメイン管理者と協力して、ドメイン間の信頼関係を確認してください。

#### <a name="unable-to-see-the-data-gateway-data-sources-in-the-get-data-experience-for-analysis-services-from-the-power-bi-service"></a>Power BI サービスの Analysis Services の [データの取得] エクスペリエンスで、データ ゲートウェイのデータ ソースが表示されない

ゲートウェイ構成内のデータ ソースの **[ユーザー]** タブに、自分のアカウントが表示されていることを確認します。 ゲートウェイへのアクセス権がない場合は、ゲートウェイの管理者に連絡して確認を依頼してください。 **[ユーザー]** の一覧にあるアカウントのみが、Analysis Services の一覧にあるデータ ソースを参照できます。

### <a name="error-you-dont-have-any-gateway-installed-or-configured-for-the-data-sources-in-this-dataset"></a>エラー: このデータセットのデータ ソースに対してゲートウェイをインストールまたは構成していません。

ゲートウェイに 1 つ以上のデータ ソースを追加していることを確認してください。詳細は「[データ ソースの追加](service-gateway-data-sources.md#add-a-data-source)」にあります。 ゲートウェイが管理者ポータルの **[ゲートウェイの管理]** に表示されない場合、ブラウザーのキャッシュを消去するか、サービスからサインアウトし、もう一度サインインしてください。

## <a name="datasets"></a>データセット

### <a name="error-there-is-not-enough-space-for-this-row"></a>エラー: この行には十分な領域がありません。

これは、1 つのサイズが 4 MB を超える行がある場合に発生します。 データ ソースから行を特定し、その行をフィルターで除外するか、その行のサイズを減らしてください。

### <a name="error-the-server-name-provided-doesnt-match-the-server-name-on-the-sql-server-ssl-certificate"></a>エラー: 指定されたサーバー名が、SQL Server SSL 証明書のサーバー名と一致しません

これは、証明書共通名がサーバーの完全修飾ドメイン名 (FQDN) に対するものであるときに、サーバーの NetBIOS 名だけを指定すると発生します。 この状況により、証明書の不一致が発生します。 この問題を解決するには、ゲートウェイのデータ ソースと PBIX ファイルのサーバー名でサーバーの FQDN を使用します。

### <a name="error-you-dont-see-the-on-premises-data-gateway-present-when-you-configure-scheduled-refresh"></a>エラー: スケジュールされた更新を構成するときに、オンプレミス データ ゲートウェイが表示されません。

このエラーの原因として、次のようないくつかのシナリオが考えられます。

- サーバーとデータベース名が、Power BI Desktop で入力されたものと、ゲートウェイに対して構成されているデータ ソースに一致していません。 これらの名前は同じである必要があります。 大文字と小文字は区別されません。
- ゲートウェイ構成内のデータ ソースの **[ユーザー]** タブに、自分のアカウントが表示されていません。 ゲートウェイの管理者に依頼し、そのリストに追加してもらう必要があります。
- Power BI Desktop ファイルに複数のデータ ソースがあり、それらのデータ ソースのすべてがゲートウェイで構成されているわけではありません。 スケジュールされている更新にゲートウェイを表示させるには、ゲートウェイで各データ ソースを定義する必要があります。

### <a name="error-the-received-uncompressed-data-on-the-gateway-client-has-exceeded-the-limit"></a>エラー: ゲートウェイ クライアントで受信した非圧縮データが制限を超えています。

テーブルごとの非圧縮データの上限は 10 GB です。 この問題か発生した場合、最適化して問題を回避できる適切な選択肢があります。 具体的には、不変性が高く、長い文字列値の使用を減らし、代わりに、正規化されたキーを使用します。 あるいは、使用されていない列を削除すると問題が解消されることがあります。

## <a name="reports"></a>レポート

### <a name="error-report-could-not-access-the-data-source-because-you-do-not-have-access-to-our-data-source-via-an-on-premises-data-gateway"></a>エラー: レポートからデータ ソースにアクセスできませんでした。オンプレミス データ ゲートウェイ経由でデータ ソースにアクセスできません。

このエラーは通常、次のいずれかの原因によって発生します。

- データ ソースの情報が、基になるデータセットの情報と一致しません。 オンプレミス データ ゲートウェイ用に定義されているデータ ソースと Power BI Desktop で指定するものとの間では、サーバーとデータベース名が一致している必要があります。 Power BI Desktop で IP アドレスを使用する場合は、オンプレミス データ ゲートウェイ用のデータ ソースでも IP アドレスを使用する必要があります。
- 組織内のゲートウェイには、使用可能なデータ ソースがありません。 新規または既存のオンプレミス データ ゲートウェイでデータ ソースを構成できます。

### <a name="error-data-source-access-error-please-contact-the-gateway-administrator"></a>エラー: データ ソースのアクセス エラー。 ゲートウェイの管理者にお問い合わせください。

このレポートで Analysis Services ライブ接続を使用している場合、EffectiveUserName に渡される値が有効でないか、Analysis Services コンピューターへのアクセス許可のないという問題が発生する場合があります。 通常、認証の問題は、EffectiveUserName に渡される値がローカルのユーザー プリンシパル名 (UPN) と一致していない場合に発生します。

有効なユーザー名を確認するには、次の手順を実行します。

1. [ゲートウェイ ログ](/data-integration/gateway/service-gateway-tshoot#collect-logs-from-the-on-premises-data-gateway-app)内で有効なユーザー名を見つけます。
2. 値が渡されたら、それが正しいことを確認します。 自分のユーザーの場合は、コマンド プロンプトから次のコマンドを使用して UPN を確認できます。 UPN は電子メール アドレスのような形式です。

   ```console
   whoami /upn
   ```

必要に応じて、Azure Active Directory から Power BI が取得した内容を確認できます。

1. [https://developer.microsoft.com/graph/graph-explorer](https://developer.microsoft.com/graph/graph-explorer) にアクセスします。
2. 右上隅にある **[サインイン]** を選択します。
3. 次のクエリを実行します。 かなり大きな JSON 応答が表示されます。

   ```http
   https://graph.windows.net/me?api-version=1.5
   ```

4. **userPrincipalName** を探します。

Azure Active Directory UPN がローカルの Active Directory UPN と一致しない場合は、[[ユーザー名のマップ]](service-gateway-enterprise-manage-ssas.md#map-user-names-for-analysis-services-data-sources) 機能を使用して、有効な値に置き換えることができます。 あるいは、自分の Power BI 管理者かローカルの Active Directory 管理者と協力して自分の UPN を変更できます。

## <a name="kerberos"></a>Kerberos

[Kerberos の制約付き委任](service-gateway-sso-kerberos.md)に対し、基になるデータベース サーバーとオンプレミス データ ゲートウェイが適切に構成されていない場合、ゲートウェイで[詳細なログ](/data-integration/gateway/service-gateway-performance#slow-performing-queries)を有効にします。 次に、トラブルシューティングの出発点として、ゲートウェイのログ ファイルのエラーまたはトレースに基づいて調査します。 表示するゲートウェイ ログの収集については、「[Collect logs from the on-premises data gateway app (オンプレミス データ ゲートウェイ アプリからログを収集する)](/data-integration/gateway/service-gateway-tshoot#collect-logs-from-the-on-premises-data-gateway-app)」をご覧ください。

### <a name="impersonationlevel"></a>ImpersonationLevel

ImpersonationLevel は、SPN の設定またはローカル ポリシーの設定に関連しています。

```
[DataMovement.PipeLine.GatewayDataAccess] About to impersonate user DOMAIN\User (IsAuthenticated: True, ImpersonationLevel: Identification)
```

**解決方法**

問題を解決するには、次の手順を実行します。

1. オンプレミス ゲートウェイ用に SPN を設定します。
2. Active Directory で制約付き委任を設定します。

### <a name="failedtoimpersonateuserexception-failed-to-create-windows-identity-for-user-userid"></a>FailedToImpersonateUserException:ユーザーの userid の Windows ID を作成できませんでした

FailedToImpersonateUserException は、別のユーザーを偽装できない場合に発生します。 このエラーは、偽装しようとしているアカウントが、ゲートウェイ サービス ドメインとは別のドメインのアカウントの場合にも発生する可能性があります。 これは制限です。

**解決方法**

* 前の "ImpersonationLevel" セクションの手順に従って構成が正しいことを確認します。
* 偽装しようとしているユーザー ID が有効な Active Directory アカウントであることを確認します。

### <a name="general-error-1033-error-while-you-parse-the-protocol"></a>一般エラー:プロトコルの解析中に 1033 エラーが発生しました

ユーザーが UPN (alias@domain.com) を使用して偽装されていると、SAP HANA で構成された外部 ID がサインインと一致しない場合に 1033 エラーが発生します。 次のように、エラー ログの先頭に "Original UPN 'alias@domain.com' replaced with a new UPN 'alias@domain.com'" と表示されます。

```
[DM.GatewayCore] SingleSignOn Required. Original UPN 'alias@domain.com' replaced with new UPN 'alias@domain.com.'
```

**解決方法**

* SAP HANA では、偽装されるユーザーが Active Directory (ユーザー エイリアス) で sAMAccountName 属性を使用する必要があります。 この属性が正しくない場合は、1033 エラーが表示されます。

    ![属性エディター](media/service-gateway-onprem-tshoot/sAMAccount.png)

* ログには、UPN ではなく sAMAccountName (エイリアス) が表示されます。このエイリアスの後にドメイン (alias@doimain.com) が続きます。

    ![ログのアカウント情報](media/service-gateway-onprem-tshoot/sAMAccount-02.png)

```xml
      <setting name="ADUserNameReplacementProperty" serializeAs="String">
        <value>sAMAccount</value>
      </setting>
      <setting name="ADServerPath" serializeAs="String">
        <value />
      </setting>
      <setting name="CustomASDataSource" serializeAs="String">
        <value />
      </setting>
      <setting name="ADUserNameLookupProperty" serializeAs="String">
        <value>AADEmail</value>
```

### <a name="sap-aglibodbchdb-dllhdbodbc-communication-link-failure-10709-connection-failed-rte-1-kerberos-error-major-miscellaneous-failure-851968-minor-no-credentials-are-available-in-the-security-package"></a>[SAP AG][LIBODBCHDB DLL][HDBODBC] Communication link failure:-10709 Connection failed (RTE:[-1] Kerberos エラー。 メジャー:"その他のエラー [851968]。" マイナー:"セキュリティ パッケージで利用できる資格情報がありません。"

Active Directory で委任が正しく構成されていない場合は、"-10709 Connection failed" エラー メッセージが表示されます。

**解決方法**

* Active Directory のゲートウェイ サービス アカウントの [委任] タブに SAP Hana サーバーがあることを確認します。

   ![[委任] タブ](media/service-gateway-onprem-tshoot/delegation-in-AD.png)

## <a name="export-logs-for-a-support-ticket"></a>サポート チケットのログをエクスポートする

ゲートウェイ ログは、サポート チケットのトラブルシューティングと作成のために必要です。 このログは次の手順で抽出します。

1. ゲートウェイ クラスターを特定します。

    データセットの所有者であれば、まず、データセットに関連付けられているゲートウェイ クラスター名を確認します。 次の図では、*IgniteGateway* がゲートウェイ クラスターです。

    ![ゲートウェイ クラスター](media/service-gateway-onprem-tshoot/gateway-cluster.png)

2. ゲートウェイのプロパティを確認します。

    ゲートウェイ管理者がその後、クラスター内のゲートウェイ メンバーの数と、負荷分散が有効になっているかどうかを確認します。

    負荷分散が有効になっている場合、全ゲートウェイ メンバーに対して手順 3 を繰り返します。 有効になっていない場合、プライマリ ゲートウェイでのログ エクスポートで十分です。

3. ゲートウェイ ログを取得して、エクスポートします。

    次に、ゲートウェイ システムの管理者でもあるゲートウェイ管理者が次の手順を行います。

    a. ゲートウェイ コンピューターにサインインし、[オンプレミス データ ゲートウェイ アプリ](https://review.docs.microsoft.com/data-integration/gateway/service-gateway-app)を起動し、ゲートウェイにサインインします。
    
    b. [追加のログ記録](https://review.docs.microsoft.com/data-integration/gateway/service-gateway-performance#slow-performing-queries)を有効にします。
    
    c. 必要に応じて、[パフォーマンス監視機能](https://review.docs.microsoft.com/data-integration/gateway/service-gateway-performance#enable-performance-logging)を有効にし、トラブルシューティングの追加詳細を提供するためにパフォーマンス ログを含めることができます。
    
    d. ゲートウェイ ログをキャプチャしようとしているシナリオを実行します。
    
    e. [ゲートウェイのログをエクスポートします](https://review.docs.microsoft.com/data-integration/gateway/service-gateway-tshoot#collect-logs-from-the-on-premises-data-gateway-app)。


## <a name="refresh-history"></a>更新履歴

スケジュールされている更新にゲートウェイを使用するときに、 **[更新履歴]** で発生したエラーの内容を確認できます。 サポート リクエストを作成する場合に役立つデータが得られることもあります。 スケジュールされた更新とオンデマンドの更新を表示できます。 更新履歴を表示する方法は次のようになります。

1. Power BI のナビ ペインの **[データセット]** で、データセットを選択します。 メニューを開き、 **[更新のスケジュール設定]** を選択します。

    ![[更新のスケジュール設定] を選択する方法](media/service-gateway-onprem-tshoot/scheduled-refresh.png)

2. **[設定]** &gt; **[更新のスケジュール設定]** で、 **[更新履歴]** を選択します。

    ![[更新履歴] を選択する](media/service-gateway-onprem-tshoot/scheduled-refresh-2.png)

    ![更新履歴の表示](media/service-gateway-onprem-tshoot/refresh-history.png)

更新のトラブルシューティング シナリオについては、「[更新に関するトラブルシューティング シナリオ](refresh-troubleshooting-refresh-scenarios.md)」をご覧ください。

## <a name="fiddler-trace"></a>Fiddler のトレース

[Fiddler](https://www.telerik.com/fiddler) は、HTTP トラフィックを監視する Telerik 提供の無償ツールです。 クライアント マシンから、Power BI サービスとのやりとりを確認できます。 このトラフィックの一覧では、エラーとその他の関連する情報が表示される場合があります。

![Fiddler トレースの使用](media/service-gateway-onprem-tshoot/fiddler.png)

## <a name="next-steps"></a>次の手順

* [オンプレミス データ ゲートウェイのトラブルシューティング](/data-integration/gateway/service-gateway-tshoot)
* [オンプレミス データ ゲートウェイのプロキシ設定を構成する](/data-integration/gateway/service-gateway-proxy)  
* [データ ソースの管理 - Analysis Services](service-gateway-enterprise-manage-ssas.md)  
* [データ ソースの管理 - SAP HANA](service-gateway-enterprise-manage-sap.md)  
* [データ ソースの管理 - SQL Server](service-gateway-enterprise-manage-sql.md)  
* [データ ソースの管理 - インポート/スケジュールされた更新](service-gateway-enterprise-manage-scheduled-refresh.md)  

他にわからないことがある場合は、 [Power BI コミュニティ](https://community.powerbi.com/)を利用してください。