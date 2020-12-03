---
title: PowerShell を使用してデータ ソース接続文字列を変更する - 2020 年 10 月より前の Power BI Report Server
description: PowerShell の API を使用してデータ ソース接続文字列を変更する - 2020 年 10 月より前の Power BI Report Server。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 10/26/2020
ms.openlocfilehash: c063d145919dfc6f075cf8945b88a5f3644dead7
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415498"
---
# <a name="change-data-source-connection-strings-in-power-bi-reports-with-powershell---power-bi-report-server-pre-october-2020"></a>PowerShell を使って Power BI レポートのデータ ソース接続文字列を変更する - 2020 年 10 月より前の Power BI Report Server


PowerShell を使用して必要な API を操作することにより、Power BI Report Server でホストされている Power BI レポートのデータ ソース接続文字列を変更できます。 

> [!IMPORTANT]
> Power BI Report Server の最新版である 2020 年 10 月バージョンを使用している場合は、「[PowerShell を使って Power BI レポートのデータ ソース接続文字列を変更する - Power BI Report Server](connect-data-source-apis.md)」を参照してください。

> [!NOTE]
> 現在、この機能は DirectQuery に対してのみ機能します。 インポートとデータ更新のサポートが予定されています。

1. Power BI Report Server PowerShell コマンドレットをインストールします。 コマンドレットとインストール手順は [https://github.com/Microsoft/ReportingServicesTools](https://github.com/Microsoft/ReportingServicesTools) に記載されています。 

    次のコマンドを使用して、[PowerShell ギャラリー](https://www.powershellgallery.com/packages/ReportingServicesTools/)から `ReportingServicesTools` モジュールを直接インストールします。

    ```powershell
    Install-Module ReportingServicesTools
    ```

2. PowerShell コマンドレットを使用して、Power BI ファイルの既存のデータ ソース情報を取得します。

    ```powershell
    Get-RsRestItemDataSource -RsItem '/MyPbixReport'
    ```

    Power BI レポートに含まれている最初のデータ ソースの情報を表示するには: 

    ```powershell
    $dataSources[0]
    ```

3. 必要に応じて、接続情報と資格情報を更新します。 接続文字列とデータ ソースを更新する際に保存された資格情報を使用する場合は、そのアカウントのパスワードを入力する必要があります。 

    データ ソース接続文字列を更新するには:

    ```powershell
    $dataSources[0].ConnectionString = 'data source=myCatalogServer;initial catalog=ReportServer;persist security info=False' 
    ```

    データソースの資格情報の種類を変更するには:

    ```powershell
    $dataSources[0].DataModelDataSource.AuthType = 'Integrated'
    ```

    データ ソースのユーザー名/パスワードを変更するには:

    ```powershell
    $dataSources[0].DataModelDataSource.Username = 'domain\user'
    ```
    ```powershell
    $dataSources[0].DataModelDataSource.Secret = 'password'
    ```

4. 更新した資格情報を、サーバーに保存し直します。

    ```powershell
    Set-RsRestItemDataSource -RsItem '/MyPbixReport' -RsItemType 'PowerBIReport' -DataSources $dataSources
    ```

## <a name="next-steps"></a>次のステップ

[Power BI Report Server でのページ分割されたレポートのデータ ソース](connect-data-sources.md) 

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
