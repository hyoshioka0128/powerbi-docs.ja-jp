---
title: 管理者のための PowerShell コマンドレット、REST API、.NET SDK
description: スクリプトとプログラミング API を使って Power BI を管理する方法について説明します。
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: b4f4227a53a87cd831962bc5c944a569531b8232
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2020
ms.locfileid: "83136291"
---
# <a name="powershell-cmdlets-rest-apis-and-net-sdk-for-power-bi-administration"></a>Power BI 管理のための PowerShell コマンドレット、REST API、.NET SDK
Power BI では、管理者が PowerShell コマンドレットを使用して一般的なタスクのスクリプトを作成できます。 REST API も公開され、管理ソリューションを開発するための .NET SDK が提供されます。 このトピックでは、コマンドレットの一覧と、それに対応する SDK メソッドおよび REST API エンドポイントを示します。 詳細については、次のトピックを参照してください。

- PowerShell の[ダウンロード](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt/)と[ドキュメント](https://docs.microsoft.com/powershell/power-bi/overview?view=powerbi-ps)
- REST API の[ドキュメント](https://docs.microsoft.com/rest/api/power-bi/admin)
- .NET SDK の[ダウンロード](https://www.nuget.org/packages/Microsoft.PowerBI.Api/)

> 以下のコマンドレットを管理用のテナントに対して動作させるには、`-Scope Organization` と共に呼び出す必要があります。

| **コマンドレット名** | **エイリアス** | **SDK メソッド** | **REST API エンドポイント** | **説明** |
| --- | --- | --- | --- | --- |
| `Get-PowerBIDatasource` | N/A | `Datasets_GetDataSourcesAsAdmin` | /v1.0/myorg/admin/datasets/{datasetkey}/datasources | 指定されたデータセットのデータ ソースを取得します。 |
| `Get-PowerBIDataset` | N/A | `Datasets_GetDatasetsAsAdmin` | /v1.0/myorg/admin/datasets | Power BI テナント内の、データセットの完全な一覧を取得します。 |
| `Get-PowerBIWorkspace` | `Get-PowerBIGroup` | `Groups_GetGroupsAsAdmin` | /v1.0/myorg/admin/groups | Power BI テナント内の、ワークスペースの完全な一覧を取得します。 |
| `Add-PowerBIWorkspaceUser` | `Add-PowerBIGroupUser` | `Groups_AddUserAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/users | 指定されたワークスペースのメンバーとしてユーザーを追加します。 |
| `Remove-PowerBIWorkspaceUser` | `Remove-PowerBIGroupUser` | `Groups_DeleteUserAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/users/{user} | 指定されたワークスペースのメンバーシップ一覧からユーザーを削除します。 |
| `Restore-PowerBIWorkspace` |`Restore-PowerBIGroup` | `Groups_RestoreDeletedGroupAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/restore | 削除されたワークスペースを復元します。 |
| `Set-PowerBIWorkspace` |`Set-PowerBIGroup` | `Groups_UpdateGroupAsAdmin` | /v1.0/myorg/admin/groups/{groupId} | 指定されたワークスペースのプロパティを更新します。 |
| `Get-PowerBIDataset -WorkspaceId` | N/A | `Groups_GetDatasetsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/datasets | 指定されたワークスペース内のデータセットを取得します。 |
| `Get-PowerBIReport` | N/A | `Reports_GetReportsAsAdmin` | /v1.0/myorg/admin/reports | Power BI テナント内の、レポートの完全な一覧を取得します。 |
| `Get-PowerBIDashboard` | N/A | `Dashboards_GetDashboardsAsAdmin` | /v1.0/myorg/admin/dashboards | Power BI テナント内の、ダッシュボードの完全な一覧を取得します。 |
| `Get-PowerBIDashboard -WorkspaceId` | N/A | `Groups_GetDashboardsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/dashboards | 指定されたワークスペース内のダッシュボードを取得します。 |
| `Get-PowerBITile` | `Get-PowerBIDashboardTile` | `Dashboards_GetTilesAsAdmin` | /v1.0/myorg/admin/dashboards/{dashboard\_id}/tiles | 指定したダッシュボードのタイルを取得します。 |
| `Get-PowerBIReport` | N/A | `Groups_GetReportsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/reports | 指定されたワークスペース内のレポートを取得します。 |
| `Get-PowerBIImport` | N/A | `Imports_GetImportsAsAdmin` | /v1.0/myorg/admin/imports | Power BI テナント内の、インポートの完全な一覧を取得します。 |
| `Connect-PowerBIServiceAccount` | `Login-PowerBI` &  `Login-PowerBIServiceAccount` | N/A | N/A | Power BI にログインし、セッションを開始します。 |
| `Disconnect-PowerBIServiceAccount` | `Logout-PowerBI` & `Logout-PowerBIServiceAccount` | N/A | N/A | Power BI からログアウトし、既存のセッションを終了します。 |
| `Invoke-PowerBIRestMethod`| N/A | N/A | N/A | Power BI に任意の REST API 呼び出しを送信します。 |
| `Get-PowerBIAccessToken`| N/A | N/A | N/A | セッションの Power BI のアクセス トークンを取得します。 |
| `Resolve-PowerBIError`| N/A | N/A | N/A | 失敗したコマンドレットの呼び出しの詳細なエラー情報を取得します。 |
