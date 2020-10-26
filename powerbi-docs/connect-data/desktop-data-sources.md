---
title: Power BI Desktop のデータ ソース
description: Power BI Desktop のデータ ソース
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 10/12/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 8565f6ef18192110688d01127129dcc19919cb0f
ms.sourcegitcommit: eab5a02520c421a57019595c03e9ecfdb41d52ad
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/20/2020
ms.locfileid: "92256543"
---
# <a name="data-sources-in-power-bi-desktop"></a>Power BI Desktop のデータ ソース

Power BI Desktop を使用すると、多種多様なソースからデータに接続できます。 利用できるデータ ソースの完全な一覧が必要な場合、「[Power BI データ ソース](power-bi-data-sources.md)」を参照してください。

データに接続するには、 **[ホーム]** リボンを使用します。 **[よく使われる]** データ型メニューを表示するには、 **[データの取得]** ボタン ラベルまたは下矢印を選択します。

![[よく使われる] データ型メニュー、Power BI Desktop の [データの取得]](media/desktop-data-sources/data-sources-01.png)

**[データの取得]** ダイアログ ボックスに移動するには、 **[よく使われる]** データ型メニューを表示し、 **[詳細]** を選択します。 **[データの取得]** ダイアログ ボックスを表示する (そして **[よく使われる]** メニューをバイパスする)には、 **[データの取得]** アイコンを直接選択する方法もあります。

![[データの取得] ボタン、Power BI Desktop](media/desktop-data-sources/data-sources-02.png)

> [!NOTE]
> Power BI チームは Power BI Desktop や Power BI サービスで利用できるデータ ソースを継続的に拡張しています。 そのため、**ベータ**や**プレビュー**などのマークが付いた、未完成の早期バージョンのデータ ソースが頻繁に公開されています。 データ ソースに**ベータ**や**プレビュー**などのマークが付いている場合、サポートや機能が限定されています。運用環境では利用しないでください。 また、Power BI Desktop の**ベータ**または**プレビュー**とマークされているデータ ソースは、データ ソースが一般提供 (GA) になるまで、Power BI サービスまたは他の Microsoft サービスで使用できない可能性があります。

> [!NOTE]
> Power BI Desktop 用のデータ コネクタの多くには、認証に Internet Explorer 10 (またはそれ以降) が必要です。 


## <a name="data-sources"></a>データ ソース

**[データの取得]** ダイアログ ボックスには、次のカテゴリのデータ型が表示されます。

* すべて
* ファイル
* データベース
* Power Platform
* Azure
* オンライン サービス
* その他

**[すべて]** カテゴリには、すべてのカテゴリにあるすべてのデータ接続の種類が含まれます。

### <a name="file-data-sources"></a>ファイルのデータ ソース

**[ファイル]** カテゴリには、次のデータ接続があります。

* Excel
* テキスト/CSV
* XML
* JSON
* フォルダー
* PDF
* SharePoint フォルダー

次の図は、 **[ファイル]** の **[データの取得]** ウィンドウを示しています。

![ファイルのデータ ソース、[データの取得] ダイアログ ボックス、Power BI Desktop](media/desktop-data-sources/data-sources-03.png)

### <a name="database-data-sources"></a>データベースのデータ ソース

**[データベース]** カテゴリには、次のデータ接続があります。

* SQL Server データベース
* Access データベース
* SQL Server Analysis Services データベース
* Oracle データベース
* IBM DB2 データベース
* IBM Informix データベース (ベータ)
* IBM Netezza
* MySQL データベース
* PostgreSQL データベース
* Sybase データベース
* Teradata データベース
* SAP HANA データベース
* SAP Business Warehouse Application サーバー
* SAP Business Warehouse メッセージ サーバー
* Amazon Redshift
* Impala
* Google BigQuery
* Vertica
* Snowflake
* Essbase
* AtScale キューブ
* BI コネクタ 
* Data Virtuality LDW (ベータ)
* Denodo
* Dremio
* Exasol
* Indexima
* InterSystems IRIS (ベータ)
* Jethro (ベータ)
* Kyligence
* Linkar PICK スタイル / MultiValue Databases (ベータ)
* MarkLogic
* MariaDB (ベータ)

> [!NOTE]
> 一部のデータベース コネクタの場合、有効にするためには、 **[ファイル]、[オプションと設定]、[オプション]** の順に選択し、 **[プレビュー機能]** を選択し、コネクタを有効にする必要があります。 前途コネクタの一部が表示されず、その中に使用したいコネクタも含まれている場合は、 **[プレビュー機能]** を確認してください。 データ ソースに*ベータ*や*プレビュー*などのマークが付いている場合、サポートや機能が限定されていることにもご注意ください。運用環境では利用しないでください。

次の図は、 **[データベース]** の **[データの取得]** ウィンドウを示しています。

![データベースのデータ ソース、[データの取得] ダイアログ ボックス、Power BI Desktop](media/desktop-data-sources/data-sources-04.png)

### <a name="power-platform-data-sources"></a>Power Platform のデータ ソース

**[Power Platform]** カテゴリには、次のデータ接続があります。

* Power BI データセット
* Power BI データフロー
* Common Data Service
* Power Platform データフロー (ベータ)

次の図は、 **[Power Platform]** の **[データの取得]** ウィンドウを示しています。

![Power Platform のデータ ソース、[データの取得] ダイアログボックス、Power BI Desktop](media/desktop-data-sources/data-sources-05.png)

### <a name="azure-data-sources"></a>Azure データ ソース

**[Azure]** カテゴリには、次のデータ接続があります。

* Azure SQL データベース
* Azure Synapse Analytics (SQL DW)
* Azure Analysis Services データベース
* Azure Database for PostgreSQL
* Azure Blob Storage
* Azure Table Storage
* Azure Cosmos DB
* Azure Data Explorer (Kusto)
* Azure Data Lake Storage Gen2
* Azure Data Lake Storage Gen1
* Azure HDInsight (HDFS)
* Azure HDInsight Spark
* HDInsight 対話型クエリ
* Azure Cost Management
* Azure Time Series Insights (ベータ)
* Azure Databricks


次の図は、 **[Azure]** の **[データの取得]** ウィンドウを示しています。

![Azure のデータ ソース、[データの取得] ダイアログ ボックス、Power BI Desktop](media/desktop-data-sources/data-sources-06.png)

### <a name="online-services-data-sources"></a>Online Services のデータ ソース

**[オンライン サービス]** カテゴリには、次のデータ接続があります。

* SharePoint Online リスト
* Microsoft Exchange Online
* Dynamics 365 (オンライン)
* Dynamics NAV
* Dynamics 365 Business Central
* Dynamics 365 Business Central (オンプレミス)
* Microsoft Azure Consumption Insights (ベータ)
* Azure DevOps (Boards のみ)
* Azure DevOps Server (Boards のみ)
* Salesforce オブジェクト
* Salesforce レポート
* Google Analytics
* Adobe Analytics
* appFigures (ベータ)
* Data.World - データセットの取得 (ベータ)
* GitHub (Beta)
* LinkedIn Sales Navigator (ベータ)
* Marketo (ベータ)
* Mixpanel (ベータ)
* Planview Enterprise One - PRM (ベータ)
* QuickBooks Online (ベータ)
* Smartsheet
* SparkPost (ベータ)
* SweetIQ (ベータ)
* Planview Enterprise One - CTM (ベータ)
* Twilio (ベータ)
* Zendesk (ベータ)
* Asana (ベータ)
* Dynamics 365 Customer Insights (ベータ版)
* Emigo Data Source
* Entersoft Business Suite (ベータ)
* FactSet Analytics
* Hexagon PPM Smart API
* Intune データ ウェアハウス (ベータ)
* Microsoft Graph Security (ベータ)
* Product Insights (ベータ)
* Quick Base
* TeamDesk (Beta)
* Webtrends Analytics (ベータ)
* Witivio (ベータ)
* Workplace Analytics (ベータ)
* Zoho Creator (ベータ)
* Palantir Foundry
* Industrial App Store
* Power BI 用 Projectplace
* eWay-CRM (ベータ)
* Spigit (ベータ)


次の図は、 **[オンライン サービス]** の **[データの取得]** ウィンドウを示しています。

![Online Services のデータ ソース、[データの取得] ダイアログボックス、Power BI Desktop](media/desktop-data-sources/data-sources-07.png)

### <a name="other-data-sources"></a>その他のデータ ソース

**[その他]** カテゴリには、次のデータ接続があります。

* Web
* SharePoint リスト
* OData フィード
* Active Directory
* Microsoft Exchange
* Hadoop ファイル (HDFS)
* Spark
* Hive LLAP (ベータ)
* R スクリプト
* Python スクリプト
* ODBC
* OLE DB
* Acterys: Model Automation & Planning (ベータ)
* Automation Anywhere (ベータ)
* Solver
* Cherwell (ベータ)
* Cognite Data Fusion (ベータ)
* FHIR
* Information Grid (ベータ)
* Jamf Pro (ベータ)
* MicroStrategy for Power BI
* Paxata
* QubolePresto (ベータ)
* Roamler (ベータ)
* Shortcuts Business Insights (ベータ)
* Siteimprove
* SurveyMonkey (ベータ)
* Tenforce (Smart)List
* TIBCO(R) Data Virtualization (ベータ)
* Vena (ベータ)
* Vessel Insight (ベータ)
* Zucchetti HR Infinity (ベータ)
* 空のクエリ



次の図は、 **[その他]** の **[データの取得]** ウィンドウを示しています。

![Power BI Desktop のその他のデータ ソース](media/desktop-data-sources/data-sources-08.png)

> [!NOTE]
> 現時点では、Azure Active Directory を使用して保護されているカスタム データ ソースに接続することはできません。

### <a name="template-apps"></a>テンプレート アプリ

**[データを取得]** ウィンドウの下部にある **[テンプレート アプリ]** リンクを選択すると、組織用のテンプレート アプリを見つけることができます。 

![Power BI Desktop のその他のデータ ソースに対する [データを取得] ダイアログ ボックス](media/desktop-data-sources/data-sources-12.png)

使用できるテンプレート アプリは、組織によって異なる場合があります。

## <a name="connecting-to-a-data-source"></a>データ ソースに接続する

データ ソースに接続するには、 **[データの取得]** ウィンドウでデータ ソースを選択し、 **[接続]** を選びます。 次の図の場合、 **[その他]** データ接続カテゴリで **[Web]** が選択されています。

![Web への接続、[データの取得] ダイアログボックス、Power BI Desktop](media/desktop-data-sources/data-sources-08.png)

対象のデータ接続に固有の接続ウィンドウが表示されます。 資格情報が必要な場合には、入力を求めるプロンプトが表示されます。 次の図には、Web データ ソースに接続するために URL を入力している様子が示されています。

![URL の入力、[Web から] ダイアログボックス、Power BI Desktop](media/desktop-data-sources/datasources-fromwebbox.png)

URL またはリソースの接続情報を入力し、 **[OK]** を選択します。 Power BI Desktop によってデータ ソースに接続され、 **[ナビゲーター]** に使用できるデータ ソースが表示されます。

![[ナビゲーター] ダイアログボックス、Power BI Desktop](media/desktop-data-sources/datasources-fromnavigatordialog.png)

データを読み込むには、 **[ナビゲーター]** ペインの下部にある **[読み込み]** ボタンをクリックします。 データを読み込む前に Power Query エディターでクエリを変換または編集するには、 **[データの変換]** ボタンを選択します。

これで、Power BI Desktop でデータ ソースに接続できます。 データ ソースの一覧は拡大を続けており、ここからデータへの接続をお試しください。一覧への追加は絶えず続いているため、頻繁にご確認ください。

## <a name="using-pbids-files-to-get-data"></a>PBIDS ファイルを使用したデータの取得

PBIDS ファイルは、特定の構造を持つ Power BI Desktop ファイルであり、Power BI データ ソース ファイルであることを識別するための .PBIDS 拡張子が付いています。

PBIDS ファイルを作成すると、組織の新規または初級のレポート作成者に対する **[データの取得]** エクスペリエンスを効率化できます。 既存のレポートから PBIDS ファイルを作成すると、レポート作成の初心者でも同じデータから新しいレポートを簡単に作成できます。

作成者が PBIDS ファイルを開くと、Power BI Desktop が開き、認証を受けてファイルに指定されているデータ ソースに接続することができる資格情報の入力がユーザーに求められます。 **[ナビゲーション]** ダイアログ ボックスが表示されると、ユーザーはモデルに読み込むデータ ソースからテーブルを選択する必要があります。 PBIDS ファイルで指定されていない場合、ユーザーはデータベースと接続モードの選択も必要な場合があります。

以降、ユーザーはビジュアルの構築を開始するか、 **[最近のソース]** に選択して新しいテーブル セットをモデルに読み込むことができるようになります。

現在、PBIDS ファイルでは、1 つのファイルで 1 つのデータ ソースのみがサポートされています。 複数のデータ ソースを指定すると、エラーが発生します。


### <a name="how-to-create-a-pbids-connection-file"></a>PBIDS 接続ファイルを作成する方法

関心のあるデータに既に接続されている既存の Power BI Desktop (.PBIX) ファイルがある場合は、Power BI Desktop 内からこれらの接続ファイルをエクスポートするだけで済みます。 PBIDS ファイルは Desktop から自動的に生成できるので、これは推奨される方法です。 さらに、その場合でも、テキスト エディターでファイルを編集したり、手動で作成したりできます。 

PBIDS ファイルを作成するには、 **[ファイル] > [オプションと設定] > [データ ソース設定]** を選択します。

![[データ ソース設定] メニュー オプション](media/desktop-data-sources/data-sources-09.png)

表示されるダイアログで、PBIDS としてエクスポートするデータ ソースを選択し、 **[Export PBIDS]\(PBIDS のエクスポート\)** を選択します。

![[データ ソース設定] ダイアログ](media/desktop-data-sources/data-sources-10.png)

**[Export PBIDS]\(PBIDS のエクスポート\)** ボタンを選択すると、Power BI Desktop によって PBIDS ファイルが生成されます。その名前を変更してディレクトリに保存し、他のユーザーと共有できます。 また、次の図に示すように、ファイルをテキスト エディターで開き、ファイル自体での接続モードの指定など、ファイルをさらに変更することもできます。 

![テキスト エディターを使用して PBIDS ファイルを変更する](media/desktop-data-sources/data-sources-11.png)

テキスト エディターで PBIDS ファイルを手動で作成する方がよい場合は、1 つの接続に必要な入力を指定し、PBIDS 拡張機能を付けてファイルを保存する必要があります。 必要に応じて、接続モードを DirectQuery または Import と指定することもできます。 ファイルに **mode** がないか null の場合、ユーザーが Power BI Desktop でファイルを開くと、**DirectQuery** または **Import** を選択するよう求められます。


### <a name="pbids-file-examples"></a>PBIDS ファイルの例

このセクションでは、一般的に使用されるデータ ソースの例をいくつか示します。 ファイルの種類 PBIDS を使用すると、Power BI Desktop でもサポートされているデータ接続のみがサポートされますが、次の例外があります: Wiki URLS、ライブ接続、空のクエリ。

PBIDS ファイルには、認証情報と、テーブルとスキーマの情報が含まれて "*いません*"。  

次のコード スニペットは、PBIDS ファイルの一般的な例をいくつか示していますが、完全でも包括的でもありません。 その他のデータ ソースについては、[プロトコルおよびアドレス情報のデータ ソース参照 (DSR) 形式](/azure/data-catalog/data-catalog-dsr#data-source-reference-specification)に関する記事を参照してください。

接続ファイルを編集している場合、または手動で作成している場合、これらの例は便宜上のものであり、網羅を目的としたものではありません。また、DSR 形式のサポートされているすべてのコネクタが含まれているわけではありません。

#### <a name="azure-as"></a>Azure AS

```json
{ 
    "version": "0.1", 
    "connections": [ 
    { 
        "details": { 
        "protocol": "analysis-services", 
        "address": { 
            "server": "server-here" 
        }, 
        } 
    } 
    ] 
}
```

#### <a name="folder"></a>フォルダー

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "folder", 
        "address": { 
            "path": "folder-path-here" 
        } 
      } 
    } 
  ] 
} 
```

#### <a name="odata"></a>OData

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "odata", 
        "address": { 
            "url": "URL-here" 
        } 
      } 
    } 
  ] 
} 
```

#### <a name="sap-bw"></a>SAP BW

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "sap-bw-olap", 
        "address": { 
          "server": "server-name-here", 
          "systemNumber": "system-number-here", 
          "clientId": "client-id-here" 
        }, 
      } 
    } 
  ] 
} 
```

#### <a name="sap-hana"></a>SAP Hana

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "sap-hana-sql", 
        "address": { 
          "server": "server-name-here:port-here" 
        }, 
      } 
    } 
  ] 
} 
```

#### <a name="sharepoint-list"></a>SharePoint リスト

URL は、サイト内のリストではなく、SharePoint サイト自体を指す必要があります。 ユーザーはナビゲーターを利用し、そのサイトから、それぞれがモデルのテーブルになる 1 つ以上のリストを選択できます。

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "sharepoint-list", 
        "address": { 
          "url": "URL-here" 
        }, 
       } 
    } 
  ] 
} 
```

#### <a name="sql-server"></a>SQL Server

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "tds", 
        "address": { 
          "server": "server-name-here", 
          "database": "db-name-here (optional) "
        } 
      }, 
      "options": {}, 
      "mode": "DirectQuery" 
    } 
  ] 
} 
```

#### <a name="text-file"></a>テキスト ファイル

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "file", 
        "address": { 
            "path": "path-here" 
        } 
      } 
    } 
  ] 
} 
```

#### <a name="web"></a>Web

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "http", 
        "address": { 
            "url": "URL-here" 
        } 
      } 
    } 
  ] 
} 
```

#### <a name="dataflow"></a>データフロー

```json
{
  "version": "0.1",
  "connections": [
    {
      "details": {
        "protocol": "powerbi-dataflows",
        "address": {
          "workspace":"workspace id (Guid)",
          "dataflow":"optional dataflow id (Guid)",
          "entity":"optional entity name"
        }
       }
    }
  ]
}
```

## <a name="next-steps"></a>次の手順

Power BI Desktop では、あらゆる種類の操作を実行できます。 そのような機能について詳しくは、次のリソースをご覧ください。

* [Power BI Desktop とは何ですか?](../fundamentals/desktop-what-is-desktop.md)
* [Power BI Desktop でのクエリの概要](../transform-model/desktop-query-overview.md)
* [Power BI Desktop でのデータ型](desktop-data-types.md)
* [Power BI Desktop でのデータの整形と結合](desktop-shape-and-combine-data.md)
* [Power BI Desktop での一般的なクエリ タスク](../transform-model/desktop-common-query-tasks.md)