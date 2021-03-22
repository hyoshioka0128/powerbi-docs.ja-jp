---
title: ODBC データ ソースの Power BI ゲートウェイとレポート ビルダーのサポート (プレビュー)
description: この記事では、Power BI ゲートウェイで ODBC データ ソースを構成する方法と、Power BI Report Builder で ODBC データ ソースを使用する方法について説明します。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: swgupt
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 03/15/2021
ms.openlocfilehash: eecfcf4eb931167d926991b27ba0f3434831e121
ms.sourcegitcommit: 818b4542925c927a0dfcb469dbbd8984b5810a21
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/16/2021
ms.locfileid: "103602546"
---
# <a name="power-bi-gateway-and-report-builder-support-for-odbc-data-sources-preview"></a>ODBC データ ソースの Power BI ゲートウェイとレポート ビルダーのサポート (プレビュー)


[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

この記事では、Power BI ゲートウェイで ODBC データ ソースを構成する方法と、Power BI Report Builder で ODBC データ ソースを使用する方法について説明します。

データ ソース名 (DSN) とドライバー接続文字列はいずれもサポートされています。 

>[!NOTE]
>Power BI Report Builder には、ODBC ドライバーの 32 ビット バージョンをインストールする必要があります。 Power BI Gateway には 64 ビット バージョンが必要です。

## <a name="before-you-install-the-power-bi-gateway"></a>Power BI ゲートウェイをインストールする前に

2021 年 2 月以降のバージョンの Power BI ゲートウェイが必要です。 ゲートウェイは、Power BI Report Builder または Power BI Desktop とは別のコンピューターにインストールすることをお勧めします。  同じコンピューターを使用すると、問題が発生する場合があります。 一部のプロバイダーでは、32 ビットおよび 64 ビット版のドライバーを同じマシンに同時にインストールすることをサポートしていません。自分のプロバイダーのドキュメントを確認してください。

## <a name="install-configure-power-bi-report-builder-for-odbc-data-source"></a>ODBC データ ソース用の Power BI Report Builder のインストールと構成

Power BI Report Builder の最新バージョンには、既に ODBC データ拡張機能が含まれています。

1.  [Power BI Report Builder](https://www.microsoft.com/download/details.aspx?id=58158) の最新バージョンをインストールします。
2.  Power BI Report Builder で使用する予定の 32 ビットの ODBC ドライバーをインストールします。

## <a name="install-power-bi-gateway-configure-odbc-data-sources"></a>Power BI ゲートウェイのインストールと ODBC データ ソースの構成

ODBC データ ソース用に Power BI ゲートウェイを設定するには、次の手順に従います。

1.  最新の [Power BI ゲートウェイ](https://powerbi.microsoft.com/gateway)をダウンロードします。

    >[!NOTE]
    >ページ分割されたレポートでは、パーソナル ゲートウェイはサポートされていません。DirectQuery のサポートが必要なためです。

2.  これの設定情報については、「[オンプレミス データ ゲートウェイとは](../connect-data/service-gateway-onprem.md)」を参照してください。
3.  ゲートウェイ コンピューターで使用する予定の 64 ビットの ODBC ドライバーをインストールします。

    >[!NOTE]
    >ファイル DSN はサポートされていません。 DSN を使用する場合は、ゲートウェイ コンピューターで 64 ビットの[システム DSN](/previous-versions/windows/desktop/odbc/dn170519(v=vs.85)) を作成します。

1. **[データ ソースの追加]**  >   **[ODBC Data Source Type]\(ODBC データ ソースの種類\)** を選択し、Power BI サービスの **[Manage Gateway]\(ゲートウェイの管理\)** ページで ODBC データ ソースを構成します。

    :::image type="content" source="media/paginated-reports-odbc-support/configure-datasource.png" alt-text="データ ソースを追加する":::

1. 接続文字列 (システム DSN またはドライバー) を貼り付けて、認証方法を選択します。 ODBC データ ソースでは、次の認証方法がサポートされています。

    - Basic
    - Windows

1. **[追加]** ボタンを選択すると、Power BI サービスは、指定した接続文字列と資格情報を使用して ODBC データ ソースに接続し、ゲートウェイに接続できることを検証します。

    >[!NOTE]
    >パブリック プレビューでは、匿名認証方法はサポートされていません。 これを ODBC データ ソースに対して選択することは可能ですが、レポートのレンダリング時に次のような "予期しないエラーが発生しました" というメッセージが表示されます。

    :::image type="content" source="media/paginated-reports-odbc-support/anonymouse-error.png" alt-text="匿名認証はサポートされていません。":::

### <a name="odbc-connection-string-examples"></a>ODBC 接続文字列の例

次に、システム DSN およびさまざまな ODBC ドライバー用の ODBC 接続文字列の例を示します。

- "dsn=Northwind"
- "driver={Microsoft Access Driver (*.mdb, *.accdb)};dbq=c:\Data\Northwind.mdb"
- "driver={SnowflakeDSIIDriver};warehouse=DEMO_WH;server=<span>org.snowflakecomputing</span>.com"
- "driver={Amazon Redshift (x64)};server=<span>org.us-west-2.redshift.amazonaws</span>.com;database=dev"

ドライバーおよび構成によっては、すべての認証方法がサポートされていない場合があります。

ODBC データ ソースは、事前にゲートウェイ上に作成するだけでなく、ページ分割されたレポートをアップロードするときに、必要に応じて作成することもできます。 ODBC データ ソースが存在しない場合は、アップロード手順で作成を求めるメッセージが表示されます。

:::image type="content" source="media/paginated-reports-odbc-support/gateway-binding.png" alt-text="データ ソースの作成のプロンプト。":::

## <a name="known-issues"></a>既知の問題

一般に、Power BI Report Builder で ODBC データ拡張機能を使用する場合に適用されるすべての制限は、Power BI ゲートウェイで ODBC データ拡張機能を使用する場合にも適用されます。

既知の制限は次のとおりです。

- ほとんどの ODBC ドライバーの DateTime パラメーターでは、特定の ODBC データ ソースに適した書式に DateTime パラメーター値がキャストされるために、RDL データセット内のコマンド テキストを変更する必要があります。  

    クエリの例:  
    ```SELECT * FROM DEMO_DB.PUBLIC.DATES WHERE DATE < DATE(?)```

    >[!NOTE]
    >一部のデータ ソースでは、特定の書式設定が必要な場合があります。 上記の例では、式を使用してパラメーターを書式設定します。 たとえば、「 `=Format(Parameters!Date.Value, "yyyy-MM-dd")` 」のように入力します。

- <span>ADO.Net</span> データ型に単純にマップされていない、特定の ODBC ドライバーまたはバックエンドで公開されている特殊なデータ型はサポートされていません。 一例は、Snowflake の配列のデータ型です。
- パラメーターを指定せずにストアド プロシージャを使用する ODBC ドライバーのシナリオは、一般にはサポートされていません。 ただし、Amazon Redshift ドライバーの in/out パラメーターはサポートされています。