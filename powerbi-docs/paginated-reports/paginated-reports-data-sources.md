---
title: Power BI のページ分割されたレポートでサポートされるデータ ソース
description: この記事では、Power BI サービスのページ分割されたレポートでサポートされるデータ ソースについて、および Azure SQL Database データ ソースに接続する方法について学習します。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 11/12/2020
ms.openlocfilehash: e26e273ff16d67defb9299c226a8435a75b93661
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96398378"
---
# <a name="supported-data-sources-for-power-bi-paginated-reports"></a>Power BI のページ分割されたレポートでサポートされるデータ ソース

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

この記事では、Power BI サービスのページ分割されたレポートでサポートされるデータ ソースについて、および Azure SQL Database データ ソースに接続する方法について詳しく説明します。 一部のデータ ソースはネイティブでサポートされています。 データ ゲートウェイを介してその他に接続することができます。

## <a name="natively-supported-data-sources"></a>ネイティブでサポートされているデータ ソース

ページ分割されたレポートでは、次のデータ ソースの一覧をネイティブでサポートします。

| データ ソース | 認証 | ノート |
| --- | --- | --- |
| Azure SQL データベース <br>Azure SQL Data Warehouse | 基本、シングル サインオン (SSO)、OAuth2 | Azure SQL Database でエンタープライズ ゲートウェイを使用できます。 ただし、このようなシナリオでは、SSO または oAuth2 を使用して認証を行うことはできません。   |
| Azure SQL Managed Instance | 基本 | パブリック エンドポイントまたはプライベート エンドポイント経由 (プライベート エンドポイントは、エンタープライズ ゲートウェイ経由でルーティングする必要があります)  |
| Azure Analysis Services | SSO、OAuth2 | AAS ファイアウォールを無効にするか、BlackForest リージョンの IP 範囲をすべて許可するように構成する必要があります。 これは、BlackForest リージョンにのみ適用されます。  外部テナントからの SSO はサポートされていません。 |
| Power BI データセット | SSO | Premium と Premium 以外の Power BI データセット。 読み取りのアクセス許可が必要 |
| Premium Power BI データセット (XMLA) | SSO | "アプリ所有データ" のシナリオでは、Power BI データセットは埋め込みのページ分割されたレポートのデータ ソースとしてはサポートされません。  Power BI レポート ビルダーで適切に接続できるようにするには、データ ソースを設定するときに [資格情報を使用しない] オプションが選択されていることを確認します。   |
| データの入力 | 該当なし | データはレポートに埋め込まれます。 |

Azure SQL Database を除き、データ ソースはすべて、Power BI サービスにレポートをアップロードした後に使用できるようになります。 データ ソースは、既定でシングル サインオン (SSO) を使用するように設定されています (該当する場合)。 Azure Analysis Services では、認証の種類を OAuth2 に変更できます。 ただし、特定のデータ ソースの認証の種類が OAuth2 に変更されると、SSO を使用するように戻すことはできません。  また、この変更は、特定のテナントのすべてのワークスペースでそのデータ ソースを使用するすべてのレポートに適用されます。  ページ分割されたレポートの行レベルのセキュリティは、ユーザーが認証の種類に SSO を選択しない限り機能しません。

Azure SQL Database データ ソースについては、「[Azure SQL Database Authentication](#azure-sql-database-authentication)」(Azure SQL Database 認証) セクションで説明されているように、詳細情報を指定する必要があります。

## <a name="other-data-sources"></a>その他のデータ ソース

上記のネイティブでサポートされているデータ ソースに加えて、[Power BI エンタープライズ ゲートウェイ](../connect-data/service-gateway-onprem.md)を介して次のデータ ソースにアクセスできます。

- SQL Server
- SQL Server Analysis Services
- Oracle
- Teradata

ページ分割されたレポートでは、現在、Azure Analysis Services には、Power BI エンタープライズ ゲートウェイを介してアクセスできます。

## <a name="azure-sql-database-authentication"></a>Azure SQL Database 認証

Azure SQL Database データ ソースの場合は、レポートを実行する前に、認証の種類を設定する必要があります。 これは、ワークスペースで最初にデータ ソースを使用するときにのみ適用されます。 最初に、次のメッセージが表示されます。

![Power BI へ発行する](media/paginated-reports-data-sources/power-bi-paginated-publishing.png)

資格情報を指定しない場合、レポートの実行時にエラーが発生します。 **[続行]** を選択して、アップロードしたレポートの **[データ ソースの資格情報]** ページに移動します。

![Azure SQL Database の設定](media/paginated-reports-data-sources/power-bi-paginated-settings-azure-sql.png)

特定のデータ ソースの **[資格情報の編集]** リンクを選択すると、 **[構成]** ダイアログ ボックスが表示されます。

![Azure SQL Database の構成](media/paginated-reports-data-sources/power-bi-paginated-configure-azure-sql.png)

Azure SQL Database データ ソースの場合、サポートされている認証の種類は次のとおりです。

- 基本 (ユーザー名とパスワード)
- SSO (シングル サインオン)
- OAuth2 (格納されている Azure Active Directory トークン)

SSO と OAuth2 を正常に機能させるには、データ ソースが接続している Azure SQL Database サーバーで [Azure Active Directory 認証サポートを有効にする](/azure/sql-database/sql-database-aad-authentication-configure)必要があります。 OAuth2 認証方法では、Azure Active Directory によってトークンが生成され、今後のデータ ソース アクセスのために格納されます。 代わりに [SSO 認証方法](../connect-data/service-azure-sql-database-with-direct-connect.md#single-sign-on)を使用するには、そのすぐ下の SSO オプション **[エンド ユーザーは、このデータ ソースに DirectQuery 経由でアクセスするときに、独自の OAuth2 資格情報を使用します。]** を選択します。
  
## <a name="next-steps"></a>次の手順

[ページ分割されたレポートを Power BI サービスで表示する](../consumer/paginated-reports-view-power-bi-service.md)

その他の質問 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。
