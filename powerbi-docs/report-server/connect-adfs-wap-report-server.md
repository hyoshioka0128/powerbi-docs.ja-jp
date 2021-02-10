---
title: Web アプリケーション プロキシと Active Directory フェデレーション サービスを使用する - Power BI Report Server
description: Web アプリケーション プロキシ (WAP) と Active Directory フェデレーション サービス (AD FS) を使用して、Power BI Report Server と SQL Server Reporting Services (SSRS) 2016 以降に接続する方法について説明します。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 02/03/2021
ms.openlocfilehash: 73c7e0b2256d4a45fb9f433a887827e772a32257
ms.sourcegitcommit: c33e53e1fab1f29872297524a7b4f5af6c806798
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2021
ms.locfileid: "99533075"
---
# <a name="use-web-application-proxy-and-active-directory-federated-services---power-bi-report-server"></a>Web アプリケーション プロキシと Active Directory フェデレーション サービスを使用する - Power BI Report Server

この記事では、Web アプリケーション プロキシ (WAP) と Active Directory フェデレーション サービス (AD FS) を使用して、Power BI Report Server と SQL Server Reporting Services (SSRS) 2016 以降に接続する方法について説明します。 この統合により、企業ネットワークから離れているユーザーが自分のクライアント ブラウザーから Power BI Report Server と Reporting Services レポートにアクセスでき、AD FS の事前認証によって保護されます。 Power BI モバイル アプリの場合は、[Power BI Report Server と SSRS に接続するように OAuth を構成する](../consumer/mobile/mobile-oauth-ssrs.md)必要もあります。

## <a name="prerequisites"></a>前提条件

### <a name="domain-name-services-dns-configuration"></a>ドメイン ネーム サービス (DNS) の構成

- ユーザーが接続するパブリック URL が決まっている。 これは、次の例のようになります。`https://reports.contosolab.com`
- ホスト名 (例: `reports.contosolab.com`) の DNS レコードが、Web アプリケーション プロキシ (WAP) サーバーのパブリック IP アドレスを指し示すように構成されている。
- AD FS サーバーのパブリック DNS レコードが構成されている。 たとえば、次の URL で AD FS サーバーを構成できます。`https://adfs.contosolab.com`
- DNS レコードが、Web アプリケーション プロキシ (WAP) サーバーのパブリック IP アドレスを指し示すように構成されている (例: `adfs.contosolab.com`)。 それは、WAP アプリケーションの一部として発行されます。

### <a name="certificates"></a>証明書

WAP アプリケーションと AD FS サーバーの両方の証明書を構成する必要があります。 これらの証明書はどちらも、お使いのコンピューターで認識される有効な証明機関の一部である必要があります。

## <a name="1-configure-the-report-server"></a>1.レポート サーバーを構成する

サービス プリンシパル名 (SPN) が有効であることが確認される必要があります。 有効な SPN によって、適切な Kerberos 認証が実行され、レポート サーバーでの認証のネゴシエートが可能になります。

### <a name="service-principal-name-spn"></a>サービス プリンシパル名 (SPN)

SPN は、Kerberos 認証を使うサービスの一意の識別子です。 レポート サーバーの適切な HTTP SPN が存在していることを確認します。

レポート サーバーの適切なサービス プリンシパル名 (SPN) の構成方法については、「[レポート サーバーのサービス プリンシパル名 (SPN) の登録](/sql/reporting-services/report-server/register-a-service-principal-name-spn-for-a-report-server)」をご覧ください。

### <a name="enabling-negotiate-authentication"></a>ネゴシエート認証を有効にする

レポート サーバーが Kerberos 認証を使用できるようにするには、レポート サーバーの認証の種類を RSWindowsNegotiate として構成する必要があります。 これは、rsreportserver.config ファイル内に構成します。

```
<AuthenticationTypes>

    <RSWindowsNegotiate />

    <RSWindowsNTLM />

</AuthenticationTypes>
```

詳しくは、「[Modify a Reporting Services Configuration File](/sql/reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config)」 (Reporting Services 構成ファイルを変更する) および「[レポート サーバーで Windows 認証を構成する](/sql/reporting-services/security/configure-windows-authentication-on-the-report-server)」をご覧ください。

## <a name="2-configure-active-directory-federation-services-ad-fs"></a>2.Active Directory Federation Services (AD FS) を構成する

環境内の Windows 2016 サーバーで AD FS を構成する必要があります。 構成を行うには、サーバー マネージャーで [管理]、[役割と機能の追加] の順に選択します。 詳しくは、「[Active Directoryフェデレーション サービス](/windows-server/identity/active-directory-federation-services)」をご覧ください。

AD FS サーバーで AD FS 管理アプリを使用して、次の手順を実行します。

1. **[証明書利用者信頼]** を右クリックし、 **[証明書利用者信頼の追加]** を選択します。

    ![証明書利用者信頼の追加](media/connect-adfs-wap-report-server/report-server-adfs-add-relying-party-trust.png)

2. **証明書利用者信頼の追加** ウィザードで、次の手順に従います。

    **[要求に対応しない]** オプションを選択して、認証メカニズムとして Windows 統合セキュリティを使用します。

    ![証明書利用者信頼の追加ウィザードへようこそ](media/connect-adfs-wap-report-server/report-server-adfs-add-relying-party-trust-welcome.png)

    **[表示名の指定]** に希望の名前を入力し、 **[次へ]** を選択します。
    証明書利用者信頼の識別子 (`<ADFS\_URL>/adfs/services/trust`) を入力します。

    例: `https://adfs.contosolab.com/adfs/services/trust`

    ![レポート サーバー](media/connect-adfs-wap-report-server/report-server-adfs-configure-identifiers.png)

    組織のニーズに合った **[アクセス制御ポリシー]** を選択し、 **[次へ]** を選択します。

    ![アクセス制御を選択する](media/connect-adfs-wap-report-server/report-server-adfs-choose-access-control.png)
    
    **[次へ]** を選択し、 **[完了]** を選択して、**証明書利用者信頼の追加** ウィザードを完了します。

    完了すると、証明書利用者信頼のプロパティは次のようになります。

    ![証明書利用者信頼](media/connect-adfs-wap-report-server/report-server-adfs-relying-party-trusts.png)

## <a name="3-configure-web-application-proxy-wap"></a>3.Web アプリケーション プロキシ (WAP) を構成する

環境内のサーバーで、Web アプリケーション プロキシ (役割) の Windows の役割を有効にします。 これは、Windows 2016 サーバー上になければなりません。 詳しくは、「[Web Application Proxy in Windows Server 2016](/windows-server/remote/remote-access/web-application-proxy/web-application-proxy-windows-server)」 (Windows Server 2016 での Web アプリケーション プロキシ) および「[Publishing Applications using AD FS Preauthentication](/windows-server/remote/remote-access/web-application-proxy/Publishing-Applications-using-AD-FS-Preauthentication#BKMK_1.2)」 (AD FS の事前認証を使用したアプリケーションの公開) をご覧ください。

### <a name="configure-constrained-delegation"></a>制約付き委任を構成する

Forms 認証から Windows 認証に切り替えるには、プロトコルの切り替えで制約付き委任を使う必要があります。 これは、Kerberos の構成の一部です。 レポートサーバーの SPN は、既にレポート サーバーの構成に定義されています。

Active Directory 内の WAP サーバー コンピューター アカウントで制約付き委任を構成する必要があります。 Active Directory に対する権限を持っていない場合は、ドメイン管理者に頼む必要があります。

制約付き委任を構成するには、次の手順に従います。

1. Active Directory ツールがインストールされているコンピューターで、**Active Directory ユーザーとコンピューター** を起動します。
2. WAP サーバーのコンピューター アカウントを検索します。 既定では、それは **[コンピューター]** コンテナー内にあります。
3. WAP サーバーを右クリックし、 **[プロパティ]** に移動します。
4. **[委任]** タブで、 **[指定されたサービスへの委任でのみこのコンピューターを信頼する]** と **[任意の認証プロトコルを使う]** をオンにします。

    ![このコンピューターを信頼する](media/connect-adfs-wap-report-server/report-server-adfs-delegation-use-any.png)

1. このオプションにより、この WAP サーバー コンピューター アカウントに制約付き委任が設定されます。 次に、このコンピューターが委任を許可されるサービスを指定する必要があります。
2. サービス ボックスの下の **[追加]** を選択します。

    ![AD FS の信頼の追加](media/connect-adfs-wap-report-server/report-server-adfs-trust-add.png)

1. **[ユーザーまたはコンピューター]** を選びます。
2. レポート サーバー用に使用しているサービス アカウントを入力します。 このアカウントは、前の「[レポート サーバーを構成する](#1-configure-the-report-server)」セクションで HTTP SPN を追加するために使用したものと同じです。 

3. レポート サーバーの HTTP SPN を選択し、 **[OK]** を選択します。

    > [!NOTE]
    > NetBIOS の SPN だけが表示される場合があります。 NetBIOS と FQDN の両方の SPN が存在する場合は、実際には両方が選択されます。

1. **[展開済み]** チェック ボックスをオンにすると、結果は次の例のようになります。

    ![WAP のプロパティ](media/connect-adfs-wap-report-server/report-server-wap-properties.png)

### <a name="add-wap-application"></a>WAP アプリケーションを追加する

1. Web アプリケーション プロキシ サーバーで **[リモート アクセス管理]** コンソールを開き、ナビゲーション ペインで **[Web アプリケーション プロキシ]** を選択します。 

2. **[タスク]** ペインで **[発行]** を選択します。

2. [ようこそ] ページで **[次へ]** を選択します。

    ![発行へようこそ](media/connect-adfs-wap-report-server/report-server-welcome-publish-new-app-wizard.png)

3. **[事前認証]** ページで、 **[Active Directory フェデレーション サービス (AD FS)]** を選択し、 **[次へ]** を選択します。

    ![事前承認](media/connect-adfs-wap-report-server/report-server-preauthentication-new-app-wizard.png)

4. レポート サーバーへのブラウザー アクセスのみを設定し、モバイル アプリのアクセスは設定しないため、 **[Web と MSOFBA]** 事前認証を選択します。

    ![サポートされるクライアント](media/connect-adfs-wap-report-server/report-server-supported-clients-publish-new-app-wizard.png)

5. 次に示すように AD FS サーバーで作成した **証明書利用者** を追加し、 **[次へ]** を選択します。

    ![証明書利用者の発行](media/connect-adfs-wap-report-server/report-server-relying-party-publish-new-app-wizard.png)

6. **[外部 URL]** セクションに、WAP サーバーに構成されているパブリックにアクセス可能な URL を入力します。 次に示すように、レポート サーバー (レポート サーバーの構成マネージャー) に構成されている URL を、 **[バックエンド サーバー URL]** セクションに追加します。 レポート サーバーの SPN を、 **[バックエンド サーバー SPN]** セクションに追加します。

    ![発行の設定](media/connect-adfs-wap-report-server/report-server-publishing-settings-new-app-wizard.png)

7. **[次へ]** を選択し、 **[発行]** を選択します。
8. 次の PowerShell コマンドを実行して、WAP 構成を検証します。

    ```
    Get-WebApplicationProxyApplication -Name "PBIRSWAP" | FL
    ```

    ![PowerShell コマンド](media/connect-adfs-wap-report-server/report-server-powershell-get-webapplication.png)

## <a name="connect-to-the-report-server-through-the-browser"></a>ブラウザーを使用してレポート サーバーに接続する

これで、ブラウザーからパブリック WAP URL にアクセスできます (たとえば、Web サービスの `https://reports.contosolab.com/ReportServer` や Web ポータルの `https://reports.contosolab.com/Reports`)。 認証に成功すると、レポートが表示されます。

![AD FS サインイン](media/connect-adfs-wap-report-server/report-server-adfs-sign-in.png)

## <a name="next-steps"></a>次の手順

* [Power BI Report Server と SSRS に接続するように OAuth を構成する](../consumer/mobile/mobile-oauth-ssrs.md)
*[Power BI Report Server とは](get-started.md)  

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
