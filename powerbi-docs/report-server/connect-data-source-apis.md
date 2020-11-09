---
title: PowerShell を使用してデータ ソース接続文字列を変更する
description: PowerShell の API を使ってデータ ソース接続文字列を変更します - Power BI Report Server。
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 10/26/2020
ms.author: maggies
ms.openlocfilehash: 165d38c718377ff7e47442cdf0fe67173b610bd8
ms.sourcegitcommit: a5fa368abad54feb44a267fe26c383a731c7ec0d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2020
ms.locfileid: "93044955"
---
# <a name="change-data-source-connection-strings-in-power-bi-reports-with-powershell---power-bi-report-server"></a>PowerShell を使って Power BI レポートのデータ ソース接続文字列を変更する - Power BI Report Server


Power BI Report Server の 2020 年 10 月リリースから、DirectQuery および最新の情報への更新のために Power BI レポートの接続を更新する機能が有効になります。

> [!IMPORTANT]
> これは、以前のリリースでのこの設定方法に対する破壊的変更でもあります。 Power BI Report Server の 2020 年 10 月より前のバージョンを使用している場合は、「[PowerShell を使って Power BI レポートのデータ ソース接続文字列を変更する - 2020 年 10 月より前の Power BI Report Server](connect-data-source-apis-pre-oct-2020.md)」を参照してください

## <a name="prerequisites"></a>前提条件:
- [Power BI Report Server と Power BI Report Server 向けに最適化された Power BI Desktop](https://powerbi.microsoft.com/report-server/) の 2020 年 10 月リリースをダウンロードしてください。
- **拡張データセット メタデータ** が有効になっている、Report Server 向けに最適化された Power BI Desktop の 2020 年 10 月リリースで保存されたレポート。
- パラメーター化された接続を使用するレポート。 発行後に更新できるのは、パラメーター化された接続とデータベースを使用するレポートのみです。
- この例では、Reporting Services PowerShell ツールを使用します。 新しい REST API を使用して、同じことを実現できます。

## <a name="create-a-report-with-parameterized-connections"></a>パラメーター化された接続を使用してレポートを作成する
    
1. サーバーへの SQL Server 接続を作成します。 下の例では、localhost の ReportServer という名前のデータベースに接続し、ExecutionLog からデータをプルしています。

    :::image type="content" source="media/connect-data-source-apis/sql-server-connect-database.png" alt-text="SQL Server データベースに接続する":::

    この時点での M クエリは次のようになります。

    ```
    let
        Source = Sql.Database("localhost", "ReportServer"),
        dbo_ExecutionLog3 = Source{[Schema="dbo",Item="ExecutionLog3"]}[Data]
    in
        dbo_ExecutionLog3
    ```

2. Power Query エディターのリボンで **[パラメーターの管理]** を選択します。

    :::image type="content" source="media/connect-data-source-apis/power-query-manage-parameters.png" alt-text="[パラメーターの管理] を選択する":::

1.  サーバー名とデータベース名のパラメーターを作成します。

    :::image type="content" source="media/connect-data-source-apis/report-server-manage-parameters.png" alt-text="パラメーターの管理、サーバー名とデータベース名を設定する。":::


3. 最初の接続のクエリを編集し、データベースとサーバー名をマップします。

    :::image type="content" source="media/connect-data-source-apis/report-server-map-database-server.png" alt-text="サーバーとデータベース名をマップする":::

    クエリは次のようになります。

    ```
    let
        Source = Sql.Database(ServerName, Databasename),
        dbo_ExecutionLog3 = Source{[Schema="dbo",Item="ExecutionLog3"]}[Data]
    in
        dbo_ExecutionLog3
    ```
    
    4. そのレポートをサーバーに発行します。 この例では、レポートの名前は executionlogparameter です。 次の図は、データソース管理ページの例です。

    :::image type="content" source="media/connect-data-source-apis/report-server-manage-data-source-credentials.png" alt-text="データソース管理ページ。":::

## <a name="update-parameters-using-the-powershell-tools"></a>PowerShell ツールを使用してパラメーターを更新する

1. PowerShell を開き、[https://github.com/microsoft/ReportingServicesTools](https://github.com/microsoft/ReportingServicesTools) の説明に従って、最新の Reporting Services ツールをインストールします。
    
2.  レポートのパラメーターを取得するには、次の PowerShell 呼び出しを使用して、新しい REST DataModelParameters API を使用します。

    ```powershell
    Get-RsRestItemDataModelParameters '/executionlogparameter'

        Name         Value
        ----         -----
        ServerName   localhost
        Databasename ReportServer
    ```

3. この呼び出しの結果を変数に保存します。

    ```powershell
    $parameters = Get-RsRestItemDataModelParameters '/executionlogparameter'
    ```

4. 変更する必要がある値で、この変数を更新します。
5. この呼び出しの結果を変数に保存します。

    ```powershell
    $parameters[0].Value = 'myproductionserver'
    $parameters[1].Value = 'myproductiondatabase'
    ```

6. 更新された値でコマンドレット `Set-RsRestItemDataModelParameters` を使用してサーバーの値を更新できます。

    ```powershell
    Set-RsRestItemDataModelParameters -RsItem '/executionlogparameter' -DataModelParameters $parameters
    ```

7. パラメーターが更新されると、そのパラメーターにバインドされているすべてのデータ ソースがサーバーによって更新されます。 **[データ ソースの編集]** ダイアログ ボックスに戻ると、更新されたサーバーとデータベースに対して資格情報を設定できるはずです。

    :::image type="content" source="media/connect-data-source-apis/report-server-manage-executionlogparameter-dialog.png" alt-text="更新されたサーバーとデータベースに対して資格情報を設定する。":::

## <a name="next-steps"></a>次のステップ

[Power BI Report Server でのページ分割されたレポートのデータ ソース](connect-data-sources.md) 

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
