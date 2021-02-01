---
title: Power BI Desktop で SAP Business Warehouse (BW) Connector を使用する
description: Power BI Desktop で SAP BW Connector を使用する
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 01/21/2021
LocalizationGroup: Connect to data
ms.openlocfilehash: fec45c895b4b4eb43bd6efd2e5428d789ff4f44d
ms.sourcegitcommit: 77912d4f6ef2a2b1ef8ffccc50691fe5b38ee97a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2021
ms.locfileid: "98687099"
---
# <a name="use-the-sap-business-warehouse-connector-in-power-bi-desktop"></a>Power BI Desktop で SAP Business Warehouse コネクタを使用する

Power BI Desktop で、*SAP BusinessWarehouse (BW)* のデータにアクセスできます。

SAP のお客様が既存の SAP BW システムに Power BI を接続することで得られる利点については、[Power BI と SAP BW に関するホワイトペーパー](https://aka.ms/powerbiandsapbw)を参照してください。 DirectQuery と SAP BW を使用する方法については、「[DirectQuery と SAP Business Warehouse (BW)](desktop-directquery-sap-bw.md)」を参照してください。

2018 年 6 月リリース以降の Power BI Desktop で、2018 年 10 月に一般公開された *SAP BW コネクタ* をパフォーマンスと機能が大幅に向上された実装で使うことができます。 Microsoft は、SAP BW Connector の "*Implementation 2.0*" を開発しました。 SAP BW Connector のバージョン 1 または Implementation 2.0 SAP Connector のいずれかを選択します。 以下のセクションでは、各バージョンのインストールについて順番に説明します。 Power BI Desktop から SAP BW に接続するときは、どちらか一方または両方のコネクタを選ぶことができます。

可能な場合は常に Implementation 2.0 SAP Connector を使用することをお勧めします。

## <a name="installation-of-version-1-of-the-sap-bw-connector"></a>SAP BW Connector バージョン 1 のインストール

可能な場合は常に Implementation 2.0 SAP Connector を使用することをお勧めします。 このセクションでは、SAP BW Connector のバージョン 1 のインストールについて説明します。

1. ローカル コンピューターに *SAP NetWeaver* ライブラリをインストールします。 SAP NetWeaver ライブラリは、SAP の管理者から入手するか、[SAP Software Download Center](https://support.sap.com/swdc) から直接入手してください。 SAP Software Download Center は構成が頻繁に変更されるので、サイトのナビゲーションに関する具体的なガイダンスはありません。 通常、SAP NetWeaver ライブラリは、SAP クライアント ツールのインストールに含まれます。

   最新バージョンをダウンロードできる場所は、*SAP Note #1025361* に記載されています。 SAP NetWeaver ライブラリのアーキテクチャ (32 ビットまたは 64 ビット) が Power BI Desktop インストールと一致する必要があります。 SAP Note に従って、*SAP NetWeaver RFC SDK* に含まれるすべてのファイルをインストールします。
2. Power BI Desktop で、 **[データを取得]** を選択します。 **[データベース]** オプションには、 *[SAP Business Warehouse Application サーバー]* と *[SAP Business Warehouse メッセージ サーバー]* が含まれます。

   ![SAP の [データの取得] オプション](media/desktop-sap-bw-connector/sap_bw_2a.png)

## <a name="installation-of-implementation-20-sap-connector"></a>Implementation 2.0 SAP Connector のインストール

SAP Connector の Implementation 2.0 には、SAP .NET Connector 3.0 が必要です。 ダウンロードへのアクセスには、有効な S-user が必要です。 SAP Basis チームに連絡して、SAP .NET Connector 3.0 を入手してください。

SAP から [SAP .NET Connector 3.0](https://support.sap.com/en/product/connectors/msnet.html) をダウンロードできます。

コネクタには、32 ビット バージョンと 64 ビット バージョンがあります。 Power BI Desktop のインストールと一致するバージョンを選択します。 現在、Web サイトには .NET Framework 4.0 の 2 つのバージョンが表示されています。

* SAP Connector for Microsoft .NET 3.0.22.0 for Windows 32-bit (x86) 以降 (.NET Framework 4.0)
* SAP Connector for Microsoft .NET 3.0.22.0 for Windows 64-bit (x64) 以降 (.NET Framework 4.0)

インストール時に、 **[Optional setup steps]\(省略可能な設定手順\)** で必ず *[Install assemblies to GAC]\(アセンブリを GAC にインストールする\)* を選択します。

![SAP のオプション セットアップ手順](media/desktop-sap-bw-connector/sap_bw_2b.png)

> [!NOTE]
> SAP BW 実装の最初のバージョンでは、NetWeaver DLL が必要でした。 SAP Connector の Implementation 2.0 を使用していて、最初のバージョンを使用していない場合、NetWeaver DLL は必要ありません。

## <a name="version-1-sap-bw-connector-features"></a>SAP BW Connector 機能のバージョン 1

Power BI Desktop でバージョン 1 の SAP BW Connector を使うと、*SAP Business Warehouse Server* キューブからデータをインポートすること、または DirectQuery を使うことができます。

SAP BW Connector とその DirectQuery での使用方法の詳細については、[DirectQuery と SAP Business Warehouse (BW)](desktop-directquery-sap-bw.md) に関するページを参照してください。

接続するときに、 **[サーバー]** 、 **[システム番号]** 、 **[クライアント ID]** を指定します。

![SAP サーバーの接続設定](media/desktop-sap-bw-connector/sap_bw_3a.png)

また、 **[詳細設定オプション]** として、**言語コード** と、指定したサーバーに対して実行するカスタム **MDX ステートメント** の 2 つを指定できます。

![追加の接続情報](media/desktop-sap-bw-connector/sap_bw_4a.png)

MDX ステートメントを指定しない場合、接続設定には、サーバーで使用可能なキューブの一覧が表示されます。 使用可能なキューブから、ディメンションやメジャーなどの項目をドリルダウンして選択することができます。 Power BI には、[Open Analysis インターフェイス](https://help.sap.com/saphelp_nw70/helpdata/en/d9/ed8c3c59021315e10000000a114084/content.htm)によって公開されているクエリとキューブが表示されます。

サーバーから 1 つ以上の項目を選択すると、[ナビゲーター] ダイアログで出力テーブルのプレビューが作成されます。

![SAP テーブルのプレビュー](media/desktop-sap-bw-connector/sap_bw_5.png)

**[ナビゲーター]** ダイアログには次のオプションも表示されます。

* **[Display Only selected items]\(選択した項目のみを表示する\)** 。 既定では、 **[ナビゲーター]** にすべての項目が表示されます。  このオプションは、選択した項目の最終セットを確認するのに役立ちます。 選択した項目を表示するには、[プレビュー] 領域の列名を選択する方法もあります。
* **[データ プレビューを有効にします]** 。 この値は既定値です。 データのプレビューを表示します。 データ プレビューを無効にすると、プレビューのためのデータが必要なくなるため、サーバー呼び出しの回数が減ります。
* **[技術名]** 。 SAP BW はキューブ内のオブジェクトの *技術名* の概念をサポートしています。 技術名を使うと、キューブの所有者がキューブ内のオブジェクトの *物理名* だけでなく、*フレンドリ名* も公開できます。

![[ナビゲーター] ウィンドウ](media/desktop-sap-bw-connector/sap_bw_6.png)

必要なオブジェクトをすべて選択したら、次のいずれかのオプションを選択して、次に行う操作を決定できます。

* **[読み込み]** を選択して、出力テーブルの行セット全体を Power BI Desktop データ モデルに読み込みます。 **レポート** ビューが開きます。 データのビジュアル化またはさらなる変更を開始するには、**データ** または **リレーションシップ** ビューを使用します。
* **[編集]** を選択して **クエリ エディター** を開きます。 行のセット全体が Power BI Desktop データ モデルに取り込まれる前に、追加のデータ変換およびフィルター手順を指定します。

Power BI Desktop では SAP BW のキューブから情報をインポートするだけでなく、他のさまざまなデータ ソースからもデータをインポートし、1 つのレポートにまとめることができます。 この機能により、SAP BW のデータに加えて、レポートや分析の際のさまざまな興味深いシナリオが得られます。

## <a name="using-implementation-20-sap-bw-connector"></a>Implementation 2.0 SAP BW Connector の使用

SAP BW Connector の Implementation 2.0 を使って新しい接続を作成します。 新しい接続を作成するには、次の手順のようにします。

1. **[データを取得]** を選択します。 **[SAP Business Warehouse アプリケーションサーバー]** または **[SAP Business Warehouse メッセージサーバー]** を選択し、[接続] をクリックします。

2. 新しい接続ダイアログで、実装を選択します。 次の図に示すように、 **[実装]** に **[2.0]** を選択すると、 **[実行モード]** 、 **[バッチ サイズ]** 、および **[特性の構造を有効にします]** が有効になります。

    ![SAP 接続ダイアログ](media/desktop-sap-bw-connector/sap_bw_7.png)

3. **[OK]** を選択します。 この時点以降、エクスペリエンスは、バージョン 1 SAP BW Connector の「[SAP BW Connector 機能のバージョン 1](#version-1-sap-bw-connector-features)」で説明されているものと同じです。

### <a name="new-options-for-implementation-20"></a>Implementation 2.0 の新しいオプション

Implementation 2.0 は以下のオプションをサポートします。

* *ExecutionMode* - サーバーでクエリを実行するために使われる MDX インターフェイスを指定します。 次のオプションが有効です。

  * `SapBusinessWarehouseExecutionMode.BasXml`
  * `SapBusinessWarehouseExecutionMode.BasXmlGzip`
  * `SapBusinessWarehouseExecutionMode.DataStream`

    既定値は `SapBusinessWarehouseExecutionMode.BasXmlGzip` です。

    `SapBusinessWarehouseExecutionMode.BasXmlGzip` を使うと、大規模なデータセットで待機時間が長い場合にパフォーマンスが向上することがあります。

* *BatchSize* には、MDX ステートメントの実行時に取得する行の最大数を指定します。 大規模なデータセットを取得するときに、数値を小さくすると、サーバーに対する呼び出し回数が多くなります。 行数を多くするとパフォーマンスが向上する可能性がありますが、SAP BW サーバーでメモリの問題が発生する場合があります。 既定値は 50,000 行です。

* *EnableStructures* は、特性の構造が認識されるかどうかを示します。 このオプションの既定値は false です。 選択できるオブジェクトの一覧に反映されます。 ネイティブ クエリ モードではサポートされていません。

*ScaleMeasures* オプションは、この実装では廃止されました。 この動作は *ScaleMeasures* を false に設定することと同じであり、スケーリングされていない値が常に表示されます。

### <a name="additional-improvements-for-implementation-20"></a>Implementation 2.0 でのその他の機能強化

次の一覧に、新しい実装でその他に強化された機能の一部を示します。

* 向上したパフォーマンス。
* 数百万データ行を取得し、バッチ サイズ パラメーターによって微調整する機能。
* 実行モードを切り替える機能。
* 圧縮モードのサポート。 待ち時間の長い接続または大規模なデータセットに特に有効です。
* `Date` 変数の検出が向上しました。
* [実験] `Date` (ABAP 型 DATS) および `Time` (ABAP 型 TIMS) ディメンションの、テキスト値ではなく、それぞれ日付および時刻としての公開。
* 例外処理の向上。 BAPI の呼び出しで発生したエラーが表示されるようになりました。
* BasXml および BasXmlGzip モードでの列の折りたたみ。 たとえば、生成された MDX クエリは 40 列を取得するのに対し、現在の選択で必要なのは 10 列だけの場合、この要求がサーバーに渡されて、取得されるデータセットが小さくなります。

### <a name="changing-existing-reports-to-use-implementation-20"></a>Implementation 2.0 を使用するための既存レポートの変更

Implementation 2.0 を使用するように既存のレポートを変更することは、インポート モードでのみ可能です。 次の手順に従います。

1. 既存のレポートを開き、リボンの **[クエリを編集]** を選んで、更新する SAP Business Warehouse クエリを選びます。

1. クエリを右クリックし、 **[詳細エディター]** を選びます。

1. **詳細エディター** で、`SapBusinessWarehouse.Cubes` の呼び出しを次のように変更します。

    次の例のように、オプション レコードがクエリに既に含まれるかどうかを確認します。

    ![オプション レコードを含むプレーンテキスト クエリを示すスクリーンショット。](media/desktop-sap-bw-connector/sap_bw_9.png)

    その場合は、次に示すように、`Implementation` 2.0 オプションを追加し、`ScaleMeasures` オプションが存在する場合は削除します。

    ![新しく追加された値が Implementation = 2.0 であるプレーンテキスト クエリを示すスクリーンショット。](media/desktop-sap-bw-connector/sap_bw_10.png)

    クエリにオプション レコードがまだ含まれていない場合は、単に追加します。 次のオプションの場合:

    ![オプション レコードを含むプレーンテキスト クエリを示すスクリーンショットを追加。](media/desktop-sap-bw-connector/sap_bw_11.png)

    単に次のように変更します。

    ![新しく追加された値が Implementation = 2.0 である新しいオプションのプレーンテキスト クエリを示すスクリーンショット。](media/desktop-sap-bw-connector/sap_bw_12.png)

SAP BW Connector の Implementation 2.0 がバージョン 1 と互換性を持つように、あらゆる作業が行われています。 ただし、使われている SAP BW MDX 実行モードの違いによる相違が存在する可能性があります。 何らかの不一致を解決するには、実行モードを切り替えてみてください。

## <a name="troubleshooting"></a>トラブルシューティング

このセクションでは、SAP BW Connector に関するトラブルシューティング状況 (および解決策) を説明します。

1. SAP BW からの数値データで、桁区切りがコンマではなくピリオドになります。 たとえば、1,000,000 が 1.000.000 として返されます。

   SAP BW からは、小数点区切り文字として `,` (コンマ) または `.` (ピリオド) のいずれかを含む 10 進データが返されます。 SAP BW が小数点記号にどちらを使うかを指定するため、Power BI Desktop によって使われるドライバーから `BAPI_USER_GET_DETAIL` が呼び出されます。 この呼び出しからは、"*10 進形式の表記*" を格納する `DCPFM` というフィールドを持つ `DEFAULTS` という構造が返されます。 このフィールドは、次のいずれかの値を受け取ります。

   * ' ' (スペース) = 小数点はコンマです。N.NNN,NN
   * 'X' = 小数点はピリオドです。N,NNN.NN
   * 'Y' = 小数点は N NNN NNN,NN です

   正しくないデータで `BAPI_USER_GET_DETAIL` を呼び出すと、次のようなメッセージでエラーになる (正しくないデータが表示される) 問題がお客様から報告されています。

   ```xml
    You are not authorized to display users in group TI:
        <item>
            <TYPE>E</TYPE>
            <ID>01</ID>
            <NUMBER>512</NUMBER>
            <MESSAGE>You are not authorized to display users in group TI</MESSAGE>
            <LOG_NO/>
            <LOG_MSG_NO>000000</LOG_MSG_NO>
            <MESSAGE_V1>TI</MESSAGE_V1>
            <MESSAGE_V2/>
            <MESSAGE_V3/>
            <MESSAGE_V4/>
            <PARAMETER/>
            <ROW>0</ROW>
            <FIELD>BNAME</FIELD>
            <SYSTEM>CLNTPW1400</SYSTEM>
        </item>
   ```

   このエラーを解決するには、Power BI で使われている SAPBW ユーザーに `BAPI_USER_GET_DETAIL` の実行権限を付与するよう、SAP 管理者に依頼する必要があります。 また、このトラブルシューティング ソリューションで前述したように、ユーザーが必要な `DCPFM` 値を持つことを確認することもお勧めします。

2. SAP BEx クエリ用の接続
   
   Power BI Desktop で BEx クエリを実行するには、次の図に示すように特定のプロパティを有効にします。
   
   ![外部アクセスのリリースを有効にする](media/desktop-sap-bw-connector/sap_bw_8.png)
   
3. **[ナビゲーター]** ペインにデータ プレビューが表示されず、代わりに "*オブジェクト参照がオブジェクトのインスタンスに設定されていない*" というエラー メッセージが表示されます。
   
   SAP ユーザーは、メタデータを取得し、SAP BW の InfoProviders からデータを取得するために、特定の BAPI 関数モジュールにアクセスする必要があります。 これらのモジュールは次のとおりです。

   * BAPI_MDPROVIDER_GET_CATALOGS
   * BAPI_MDPROVIDER_GET_CUBES
   * BAPI_MDPROVIDER_GET_DIMENSIONS
   * BAPI_MDPROVIDER_GET_HIERARCHYS
   * BAPI_MDPROVIDER_GET_LEVELS
   * BAPI_MDPROVIDER_GET_MEASURES
   * BAPI_MDPROVIDER_GET_MEMBERS
   * BAPI_MDPROVIDER_GET_VARIABLES
   * BAPI_IOBJ_GETDETAIL

   この問題を解決するには、ユーザーがさまざまな MDPROVIDER モジュールと `BAPI_IOBJ_GETDETAIL` にアクセスできることを確認します。 この問題や同様の問題をさらにトラブルシューティングするには、トレースを有効にします。 **[ファイル]**  >  **[オプションと設定]**  >  **[オプション]** の順に選択します。 **[オプション]** で **[診断]** を選択し、 **[トレースを有効にする]** を選択します。 トレースがアクティブになっている間に SAP BW からデータを取得し、詳細についてトレース ファイルを調べてみます。

## <a name="sap-bw-connection-support"></a>SAP BW 接続のサポート

次の表では、SAP BW の現在のサポートについて説明します。

|Product  |モード  |認証  |コネクタ  |SNC ライブラリ  |サポートされている  |
|---------|---------|---------|---------|---------|---------|
|Power BI Desktop     |任意         | ユーザー/パスワード  | アプリケーション サーバー | 該当なし  | はい  |
|Power BI Desktop     |任意         | Windows          | アプリケーション サーバー | sapcrypto + gsskrb5/gx64krb5  | はい  |
|Power BI Desktop     |任意         | 借用による Windows | アプリケーション サーバー | sapcrypto + gsskrb5/gx64krb5  | はい  |
|Power BI Desktop     |任意         | ユーザー/パスワード        | メッセージ サーバー | 該当なし  | はい  |
|Power BI Desktop     |任意         | Windows        | メッセージ サーバー | sapcrypto + gsskrb5/gx64krb5  | はい  |
|Power BI Desktop     |任意         | 借用による Windows | メッセージ サーバー | sapcrypto + gsskrb5/gx64krb5  | はい  |
|Power BI Gateway     |インポート      | Power BI Desktop と同じ |         |   |   |
|Power BI Gateway     |DirectQuery | ユーザー/パスワード        | アプリケーション サーバー | 該当なし  | はい  |
|Power BI Gateway     |DirectQuery | 借用による Windows (固定ユーザー、SSO なし) | アプリケーション サーバー | sapcrypto + gsskrb5/gx64krb5  | はい  |
|Power BI Gateway     |DirectQuery | DirectQuery クエリ オプションには Kerberos 経由で SSO を使用する | アプリケーション サーバー | sapcrypto + gsskrb5/gx64krb5   | はい  |
|Power BI Gateway     |DirectQuery | ユーザー/パスワード        | メッセージ サーバー | 該当なし  | はい  |
|Power BI Gateway     |DirectQuery | 借用による Windows (固定ユーザー、SSO なし) | メッセージ サーバー | sapcrypto + gsskrb5/gx64krb5  | はい  |
|Power BI Gateway     |DirectQuery | DirectQuery クエリ オプションには Kerberos 経由で SSO を使用する | メッセージ サーバー | gsskrb5/gx64krb5  | いいえ  |
|Power BI Gateway     |DirectQuery | DirectQuery クエリ オプションには Kerberos 経由で SSO を使用する | メッセージ サーバー | sapcrypto  | はい  |

## <a name="next-steps"></a>次の手順

SAP と DirectQuery については、次のリソースをご覧ください。

* [DirectQuery と SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery と SAP Business Warehouse (BW)](desktop-directquery-sap-bw.md)
* [Power BI で DirectQuery を使用する](desktop-directquery-about.md)
* [Power BI データ ソース](power-bi-data-sources.md)
* [Power BI と SAP BW に関するホワイト ペーパー](https://aka.ms/powerbiandsapbw)
