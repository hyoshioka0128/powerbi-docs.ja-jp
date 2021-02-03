---
title: Power BI データ ソース
description: この記事では、Power BI でサポートされているデータ ソースをリストアップします。DirectQuery やオンプレミス データ ゲートウェイに関する情報などです。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: conceptual
ms.date: 12/14/2020
ms.openlocfilehash: def849c9a3b867f181dbc91628260cf24491e855
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2021
ms.locfileid: "99087938"
---
# <a name="power-bi-data-sources"></a>Power BI データ ソース

この表には、DirectQuery やオンプレミス データ ゲートウェイに関する情報など、データセットに対して Power BI でサポートされているデータ ソースがまとめられています。 データフローの詳細については、「[Power BI データフロー用のデータ リソースに接続する](../transform-model/dataflows/dataflows-configure-consume.md)」を参照してください。

| データ ソースの | デスクトップから接続する | サービスから接続し、更新する | DirectQuery / ライブ接続 | ゲートウェイ (サポートあり) | ゲートウェイ (必須) | Power BI データフロー |
|---|---|---|---|---|---|---|---|
| Access データベース | はい | はい | いいえ | はい <sup>1</sup> | はい | はい |
| Active Directory | はい | はい | いいえ | はい | はい | はい |
| Adobe Analytics | はい | はい | いいえ | いいえ | いいえ | いいえ |
| Amazon Redshift | はい | Yes | はい | はい | いいえ | はい |
| appFigures | はい | はい | いいえ | いいえ | いいえ | いいえ |
| AtScale キューブ | はい | はい | はい | はい | いいえ | いいえ |
| Azure Analysis Services | はい | Yes | はい | いいえ | いいえ | いいえ |
| Azure Blob Storage | はい | はい | いいえ | はい | いいえ | はい |
| Azure Cosmos DB | はい | はい | いいえ | いいえ | いいえ | いいえ |
| Azure Cost Management | はい | はい | いいえ | いいえ | いいえ | いいえ |
| Azure Data Explorer (Kusto) | はい | はい | はい | はい | いいえ | はい |
| Azure Data Lake Storage Gen1 | はい | はい | いいえ | いいえ | いいえ | いいえ |
| Azure Data Lake Storage Gen2 | はい | はい | いいえ | はい | いいえ | はい |
| Azure Databricks | はい | Yes | Yes | はい | いいえ | いいえ |
| Azure DevOps | はい | はい | いいえ | いいえ | いいえ | いいえ |
| Azure DevOps Server | はい | はい | いいえ | はい | はい | いいえ |
| Azure HDInsight (HDFS) | はい | はい | いいえ | いいえ | いいえ | いいえ |
| Azure HDInsight Spark | はい | はい | はい | いいえ | いいえ | はい |
| Azure SQL データベース | はい | Yes | Yes | はい | いいえ | はい |
| Azure SQL Data Warehouse | はい | Yes | Yes | はい | いいえ | はい |
| Azure Table Storage | はい | はい | いいえ | はい | いいえ | はい |
| BI コネクタ | はい | Yes | はい | はい | はい | いいえ |
| BI360 - Budgeting & Financial Reporting | はい | はい | いいえ | いいえ | いいえ | いいえ |
| Microsoft Dataverse | はい | はい | はい | いいえ | いいえ | はい |
| Data.World - データセットの取得 | はい | はい | いいえ | いいえ | いいえ | いいえ |
| Denodo | はい | Yes | Yes | Yes | はい | いいえ |
| Dremio | はい | Yes | Yes | はい | はい | いいえ |
| Dynamics 365 (オンライン) | はい | はい | いいえ | いいえ | いいえ | いいえ |
| Dynamics 365 Business Central | はい | はい | いいえ | いいえ | いいえ | いいえ |
| Dynamics 365 Business Central (オンプレミス) | はい | はい | いいえ | いいえ | いいえ | いいえ |
| Dynamics 365 Customer Insights | はい | はい | いいえ | いいえ | いいえ | いいえ |
| Dynamics NAV | はい | はい | いいえ | いいえ | いいえ | いいえ |
| Emigo Data Source | はい | はい | いいえ | いいえ | いいえ | いいえ |
| Entersoft Business Suite | はい | はい | いいえ | いいえ | いいえ | いいえ |
| Essbase | はい | はい | はい | Yes | はい | いいえ |
| Exasol | はい | はい | はい | Yes | はい | いいえ |
| Excel | はい <sup>3</sup> | はい <sup>3</sup> | いいえ | はい <sup>3</sup> | いいえ <sup>4</sup> | はい |
| Facebook | はい | はい | いいえ | いいえ | いいえ | いいえ |
| ファイル | はい | はい | いいえ | はい | はい | はい |
| Folder | はい | はい | いいえ | はい | はい | はい |
| GitHub | はい | はい | いいえ | いいえ | いいえ | いいえ |
| Google Analytics | はい | はい | いいえ | いいえ | いいえ | いいえ |
| Google BigQuery | はい | Yes | Yes | はい | いいえ | はい |
| Hadoop ファイル (HDFS) | はい | いいえ | いいえ | いいえ | いいえ | いいえ |
| Hive LLAP | はい | はい | Yes | はい | いいえ | いいえ |
| HDInsight 対話型クエリ | はい | Yes | はい | いいえ | いいえ | いいえ |
| IBM DB2 | はい | はい | はい | はい | いいえ | はい |
| IBM Informix データベース | はい | はい | いいえ | はい | いいえ | いいえ |
| IBM Netezza | はい | Yes | Yes | Yes | はい | いいえ |
| Impala | はい | Yes | Yes | Yes | はい | はい |
| Indexima | はい | はい | Yes | はい | はい | いいえ |
| Industrial App Store | はい | はい | いいえ | いいえ | いいえ | いいえ |
| Information Grid | はい | はい | いいえ | いいえ | いいえ | いいえ |
| Intersystems IRIS | はい | はい | Yes | はい | はい | いいえ |
| Intune データ ウェアハウス | はい | はい | いいえ | いいえ | いいえ | いいえ |
| Jethro ODBC | はい | はい | はい | Yes | はい | いいえ |
| JSON | はい | はい | いいえ | はい** | いいえ <sup>4</sup> | はい |
| Kyligence Enterprise | はい | Yes | はい | はい | はい | いいえ |
| MailChimp | はい | はい | いいえ | いいえ | いいえ | いいえ |
| Marketo | はい | はい | いいえ | いいえ | いいえ | いいえ |
| MarkLogic ODBC | はい | Yes | はい | Yes | はい | いいえ |
| Microsoft Azure Consumption Insights | はい | はい | いいえ | いいえ | いいえ | いいえ |
| Microsoft Exchange | はい | はい | いいえ | はい | いいえ | いいえ |
| Microsoft Exchange Online | はい | はい | いいえ | いいえ | いいえ | はい |
| Microsoft Graph Security | はい | はい | いいえ | はい | いいえ | いいえ |
| Mixpanel | はい | はい | いいえ | いいえ | いいえ | いいえ |
| MySQL | はい | はい | いいえ | はい | Yes | はい |
| OData | はい | はい <sup>7</sup> | いいえ | はい | いいえ | はい |
| ODBC | はい | はい | いいえ | はい | はい | はい |
| OleDb | はい | はい | いいえ | はい | はい | いいえ |
| Oracle | はい | はい | Yes | Yes | Yes | はい |
| Paxata <sup>8</sup> | はい | はい | いいえ | はい | いいえ | いいえ |
| PDF | はい | はい | いいえ | はい | いいえ <sup>4</sup> | はい |
| Planview Enterprise One - CTM | はい | はい | いいえ | いいえ | いいえ | いいえ |
| Planview Enterprise One - PRM | はい | はい | いいえ | いいえ | いいえ | いいえ |
| Planview Projectplace | はい | はい | いいえ | いいえ | いいえ | いいえ |
| PostgreSQL | はい | はい | はい | はい | いいえ | はい |
| Power BI データフロー | はい | はい | いいえ | いいえ | いいえ | はい |
| Power BI データセット | はい | Yes | はい | いいえ | いいえ | いいえ |
| Power Platform データフロー | はい | はい | いいえ | いいえ | いいえ | はい |
| Python スクリプト | はい | はい <sup>5</sup> | いいえ | はい <sup>5</sup> | はい | いいえ |
| QubolePresto | はい | Yes | はい | はい | はい | いいえ |
| Quick Base | はい | はい | いいえ | はい | はい | いいえ |
| QuickBooks Online | はい | はい | いいえ | いいえ | いいえ | いいえ |
| R スクリプト | はい | はい <sup>5</sup> | いいえ | はい <sup>5</sup> | いいえ | いいえ |
| Roamler | はい | はい | いいえ | はい | いいえ | いいえ |
| Salesforce オブジェクト | はい | はい | いいえ | いいえ | いいえ | はい |
| Salesforce レポート | はい | はい | いいえ | いいえ | いいえ | はい |
| SAP Business Warehouse メッセージ サーバー | はい | はい | はい | Yes | Yes | はい |
| SAP Business Warehouse サーバー | はい | はい | はい | はい | はい | はい |
| SAP HANA | はい | Yes | はい | Yes | Yes | はい |
| SharePoint フォルダー | はい | はい | いいえ | はい | いいえ <sup>4</sup> | はい |
| SharePoint リスト | はい | はい | いいえ | はい | いいえ <sup>4</sup> | はい |
| SharePoint Online リスト | はい | はい | いいえ | はい | いいえ | はい |
| Smartsheet | はい | はい | いいえ | いいえ | いいえ | はい |
| Snowflake | はい | はい | Yes | はい | いいえ | はい |
| Spark | はい | Yes | はい | はい | いいえ | はい |
| SparkPost | はい | はい | いいえ | いいえ | いいえ | いいえ |
| SQL Server | はい | Yes | Yes | Yes | Yes | はい |
| SQL Server Analysis Services | はい | Yes | Yes | Yes | はい | いいえ |
| Stripe | はい | はい | いいえ | いいえ | いいえ | いいえ |
| SurveyMonkey | はい | はい | いいえ | はい | いいえ | いいえ |
| SweetIQ | はい | はい | いいえ | いいえ | いいえ | いいえ |
| Sybase | はい | はい | いいえ | はい | Yes | はい |
| TeamDesk | はい | はい | いいえ | はい | いいえ | いいえ |
| Tenforce | はい | はい | いいえ | いいえ | いいえ | いいえ |
| Teradata | はい | Yes | Yes | Yes | Yes | Yes |
| テキスト/CSV | はい | はい | いいえ | はい | いいえ <sup>4</sup> | Yes |
| Twilio | はい | はい | いいえ | いいえ | いいえ | いいえ |
| tyGraph | はい | はい | いいえ | いいえ | いいえ | いいえ |
| Vertica | はい | Yes | Yes | Yes | Yes | Yes |
| Web | はい | はい | いいえ | はい | はい <sup>6</sup> | Yes |
| Webtrends | はい | はい | いいえ | いいえ | いいえ | いいえ |
| Workforce Dimensions | はい | はい | いいえ | はい | いいえ | いいえ |
| XML | はい | はい | いいえ | はい | いいえ <sup>4</sup> | Yes |
| Zendesk | はい | はい | いいえ | いいえ | いいえ | いいえ |
| | | | | | | | |

<sup>1</sup>[ACE OLEDB プロバイダー](https://www.microsoft.com/download/details.aspx?id=54920)でサポートされ、ゲートウェイと同じコンピューターにインストールされます。

<sup>3</sup> Excel 1997-2003 ファイル (.xls) には [ACE OLEDB プロバイダー](https://www.microsoft.com/download/details.aspx?id=54920)が必要です。

<sup>4</sup> オンプレミス バージョンのテクノロジに必須です。

<sup>5</sup>[個人ゲートウェイ](service-gateway-personal-mode.md)でのみサポートされます。

<sup>6</sup> .html、.xls、Access データベースに必要です

<sup>7</sup> Power BI service では汎用 OAuth2 がサポートされません。

<sup>8</sup> Paxata は、Power BI Report Server 向けに最適化された Power BI Desktop のバージョンでサポートされています。 Power BI Report Server に発行された Power BI レポートではサポートされていません。 サポートされているデータ ソースの一覧については、「[Power BI Report Server での Power BI レポート データ ソース](../report-server/data-sources.md)」を参照してください。

## <a name="considerations-and-limitations"></a>考慮事項と制限事項

- Power BI Desktop 用のデータ コネクタの多くには、認証に Internet Explorer 10 (またはそれ以降) が必要です。 
- 一部のデータ ソースは、Power BI Report Server 用に最適化された Power BI Desktop では使用できますが、Power BI Report Server に発行するときはサポートされていません。 サポートされているデータ ソースの一覧については、「[Power BI Report Server での Power BI レポート データ ソース](../report-server/data-sources.md)」を参照してください。

## <a name="single-sign-on-sso-for-directquery-sources"></a>DirectQuery ソースのシングル サインオン (SSO)

SSO オプションが有効になっている場合、データ ソースを基に作成されたレポートにユーザーがアクセスすると、Power BI によって基になるデータ ソースへのクエリで、認証済みの Azure AD 資格情報が送信されます。 これにより、Power BI はデータ ソース レベルで構成されているセキュリティ設定を適用できます。
SSO オプションは、このデータ ソースを使うすべてのデータセットで有効になります。 インポートのシナリオに使われる認証方法には影響しません。 次のデータ ソースでは、DirectQuery 経由の接続で SSO をサポートします。

- Azure SQL Database
- Azure SQL Data Warehouse
- Impala
- SAP HANA
- SAP BW
- SAP BW Message Server
- Snowflake
- Spark
- SQL Server
- Teradata

## <a name="next-steps"></a>次の手順

[Power BI Desktop でデータに接続する](desktop-quickstart-connect-to-data.md)  
[Power BI で DirectQuery を使用する](desktop-directquery-about.md)  
[Power BI の SQL Server Analysis Services ライブ データ](sql-server-analysis-services-tabular-data.md)  
[オンプレミス データ ゲートウェイとは](service-gateway-onprem.md)  
[Power BI Report Server での Power BI レポート データ ソース](../report-server/data-sources.md)
