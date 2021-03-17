---
title: Power BI Desktop を使用して Oracle データベースに接続する
description: Oracle を Power BI Desktop に接続するために必要な手順とダウンロード
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 01/04/2021
LocalizationGroup: Connect to data
ms.openlocfilehash: 95edbde738a52edc626992a431e3a8083b95421f
ms.sourcegitcommit: cf3469295a33acf729a913ec135b4c5484910d2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2021
ms.locfileid: "102195287"
---
# <a name="connect-to-an-oracle-database-with-power-bi-desktop"></a>Power BI Desktop を使用して Oracle データベースに接続する
Power BI Desktop を使用して Oracle データベースに接続するには、Power BI Desktop を実行しているコンピューター上に適切な Oracle クライアント ソフトウェアをインストールする必要があります。 使用する Oracle クライアント ソフトウェアは、インストールした Power BI Desktop のバージョンによって異なります。32 ビットまたは 64 ビット。 また、お使いの Oracle サーバーのバージョンにもよります。

サポートされている Oracle のバージョン: 
- Oracle Server 9 以降
- Oracle Data Access Client (ODAC) ソフトウェア 11.2 以降

Power BI を使用して Oracle データベースに接続するには、コンピューターに Oracle クライアント ソフトウェア v8.1.7 以降をインストールする必要があります。 32 ビットの Oracle クライアント ソフトウェアをインストールするには、「[32-bit Oracle Data Access Components (ODAC) with Oracle Developer Tools for Visual Studio (12.1.0.2.4)](https://www.oracle.com/technetwork/topics/dotnet/utilsoft-086879.html)」にアクセスしてください。 64 ビットの Oracle クライアントをインストールするには、「[64-bit ODAC 12c Release 4 (12.1.0.2.4) Xcopy for Windows x64](https://www.oracle.com/technetwork/database/windows/downloads/index-090165.html)」アクセスしてください。



Power BI Desktop、オンプレミス データ ゲートウェイ、または Power BI Report Server 用に Oracle データベースを構成する場合は、[Oracle の接続の種類](/sql/reporting-services/report-data/oracle-connection-type-ssrs)に関する記事を参照してください。 


## <a name="determining-which-version-of-power-bi-desktop-is-installed"></a>インストールされている Power BI Desktop バージョンの特定
どのバージョンの Power BI Desktop がインストールされているかを特定するには、 **[ファイル]**  >  **[ヘルプ]**  >  **[バージョン情報]** の順に選択し、次に **[バージョン]** 行を確認します。 次の図の場合、Power BI Desktop の 64 ビット バージョンがインストールされています。

![Power BI Desktop バージョン](media/desktop-connect-oracle-database/connect-oracle-database_1.png)

## <a name="install-the-oracle-client"></a>Oracle クライアントのインストール
- Power BI Desktop の 32 ビット バージョンの場合、[32 ビット Oracle クライアントをダウンロードし、インストールします](https://www.oracle.com/technetwork/topics/dotnet/utilsoft-086879.html)。

- Power BI Desktop の 64 ビット バージョンの場合、[64 ビット Oracle クライアントをダウンロードし、インストールします](https://www.oracle.com/database/technologies/odac-downloads.html)。

> [!NOTE]
> お使いの Oracle サーバーと互換性のある Oracle Data Access Client (ODAC) のバージョンを選択します。 たとえば、ODAC 12.x では、必ずしも Oracle Server バージョン 9 をサポートしていません。
> Oracle クライアント用の Windows インストーラーを選択します。
> Oracle クライアントのセットアップ中に、セットアップ ウィザードの該当するチェック ボックスをオンにすることで、*コンピューター全体のレベルで ODP.NET および/または Oracle Providers for ASP.NET の構成* を有効にする必要があります。 Oracle クライアント ウィザードの一部のバージョンでは、既定でチェックボックスがオンになっていますが、他のバージョンではそうなっていません。 Power BI が Oracle データベースに接続できるように、チェックボックスがオンになっていることを確認してください。

## <a name="connect-to-an-oracle-database"></a>Oracle データベースへの接続
一致する Oracle クライアント ドライバーをインストールした後、Oracle データベースに接続できます。 [オンプレミス データ ゲートウェイ](https://docs.microsoft.com/data-integration/gateway/)を使用して Oracle データベースに接続するには、ゲートウェイを実行しているコンピューター上に適切な Oracle クライアント ソフトウェアをインストールする必要があります。 使用する Oracle クライアント ソフトウェアは、Oracle サーバーのバージョンによって異なりますが、常に 64 ビットのゲートウェイと一致します。 詳細については、「[データ ソースの管理 - Oracle](https://docs.microsoft.com/power-bi/connect-data/service-gateway-onprem-manage-oracle)」を参照してください。

## <a name="capabilities-supported"></a>サポートされる機能
* インポート
* DirectQuery
* [詳細オプション]
   * 分単位のコマンド タイムアウト
   * SQL ステートメント
   * リレーションシップ列を含める
   * 階層全体を使ってナビゲートする

接続するには、次の手順を実行します。

1. **[ホーム]** タブで **[データを取得]** を選択します。 

2. 表示される **[データを取得]** ウィンドウで、 **[その他]** (必要に応じて) を選択し、 **[データベース]**  >  **[Oracle Database]** を選択し、 **[接続]** を選択します。
   
   ![Oracle データベースの接続](media/desktop-connect-oracle-database/connect-oracle-database_2.png)
3. 表示される **[Oracle Database]** ダイアログで **サーバー** の名前を指定し、 **[OK]** を選択します。 SID が必要な場合、次の形式を使用して指定できます: "*サーバー名/SID*"。*SID* はデータベースの一意名です。 "*サーバー名/SID*" の形式で正しく動作しない場合は、"*サーバー名/サービス名*" を使用します。"*サービス名*" は接続に使用した別名です。


   ![Oracle サーバー名の入力](media/desktop-connect-oracle-database/connect-oracle-database_3.png)

   > [!NOTE]
   > ローカル データベースまたは自律データベース接続を使用しているとき、接続エラーを避けるため、サーバー名を引用符で囲む必要がある場合があります。 
      
4. *[インポート]* * または **[DirectQuery]** データ接続モードを選択します。 この例の残りの手順では、データ インポートの接続モードを使用します。 DirectQuery の詳細のついては、「[Power BI Desktop で DirectQuery を使用する](https://docs.microsoft.com/power-bi/connect-data/desktop-use-directquery)」にアクセスしてください。


5. ネイティブ データベース クエリを使用してデータをインポートする場合、 **[Oracle Database]** ダイアログで **[詳細オプション]** セクションを展開すると表示される、 **[SQL ステートメント]** ボックスにクエリを入力します。  Power BI Desktop では、ストアド プロシージャを実行する Oracle ネイティブ クエリはサポートされていません。また、"begin ... end" ブロック内の Oracle ネイティブ クエリは結果セットを返しません。  
   
   ![[詳細オプション] の展開](media/desktop-connect-oracle-database/connect-oracle-database_4.png)


6. **[Oracle Database]** ダイアログに Oracle データベース情報 (SID やネイティブ データベース クエリなどの省略可能な情報を含む) を入力した後、 **[OK]** を選択して接続します。  
7. Oracle データベースがデータベース ユーザー資格情報を必要とする場合、ダイアログで指示が表示されたら資格情報を入力します。


## <a name="troubleshooting"></a>トラブルシューティング

名前付けの構文が正しくない、または適切に構成されていない場合、Oracle で次のエラーが発生する場合があります。

* ORA-12154:TNS:could not resolve the connect identifier specified. (指定された接続識別子を解決できませんでした。)
* ORA-12514:TNS:listener does not currently know of service requested in connect descriptor. (接続記述子で要求されているサービスが現在、リスナーで認識されていません。)
* ORA-12541:TNS:no listener. (リスナーがありません。)
* ORA-12170:TNS:connect timeout occurred. (接続のタイムアウトが発生しました。)
* ORA-12504:TNS:listener was not given the SERVICE_NAME in CONNECT_DATA. (CONNECT_DATA でリスナーに SERVICE_NAME が与えられませんでした)

このようなエラーは、Oracle クライアントがインストールされていないか、正しく構成されていない場合に発生することがあります。 インストールされている場合は、tnsnames.ora ファイルが正しく構成されていることと正しい net_service_name を使用していることを確認します。 また、Power BI Desktop を使用しているコンピューターとゲートウェイを実行しているコンピューターの間で net_service_name が一致していることも確認する必要があります。 詳細については、「[Oracle クライアントのインストール](#install-the-oracle-client)」をご覧ください。

Oracle サーバーのバージョンと Oracle Data Access クライアントのバージョン間で互換性の問題が発生する場合もあります。 一部の組み合わせでは互換性がないため、通常はこれらのバージョンを合わせる必要があります。 たとえば、ODAC 12.x では、Oracle Server バージョン 9 をサポートしていません。

Microsoft Store から Power BI Desktop をダウンロードした場合、Oracle ドライバーの問題により Oracle データベースに接続できない可能性があります。 この問題が発生した場合は、次のエラー メッセージが返されます: "*オブジェクト参照が設定されていません*"。 この問題に対処するには、次のいずれかの手順を行ってください。

* Microsoft Store ではなく、[ダウンロード センター](https://www.microsoft.com/download/details.aspx?id=58494)から Power BI Desktop をダウンロードします。

* Microsoft Store から取得したバージョンを使用する場合は、ご利用のローカル コンピューター上で、_12.X.X\client_X_ から _12.X.X\client_X\bin_ に oraons.dll をコピーします。_X_ はバージョンまたはディレクトリ番号を表します。

Oracle データベースへの接続時に Power BI Gateway に "*オブジェクト参照が設定されていません*" というエラー メッセージが表示される場合は、「[データ ソースの管理 - Oracle](service-gateway-onprem-manage-oracle.md)」に記載されている手順に従ってください。

Power BI Report Server を使用している場合は、[Oracle の接続の種類](/sql/reporting-services/report-data/oracle-connection-type-ssrs)に関する記事のガイダンスを参照してください。

