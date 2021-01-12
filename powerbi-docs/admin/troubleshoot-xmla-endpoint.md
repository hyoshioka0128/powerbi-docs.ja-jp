---
title: Power BI での XMLA エンドポイント接続のトラブルシューティング
description: Power BI Premium で XMLA エンドポイントを使用した接続のトラブルシューティングを行う方法について説明します。
author: Minewiskan
ms.author: kfollis
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: troubleshooting
ms.date: 01/04/2021
ms.custom: seodec18, css_fy20Q4
LocalizationGroup: Premium
ms.openlocfilehash: 191cf3ce71ca30f257276df78ad43cdb2e49a1e1
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2021
ms.locfileid: "97886088"
---
# <a name="troubleshoot-xmla-endpoint-connectivity"></a>XMLA エンドポイント接続のトラブルシューティング

Power BI Premium の XMLA エンドポイントは、ネイティブの Analysis Services 通信プロトコルを使用して、Power BI データセットにアクセスします。 このため、XMLA エンドポイントのトラブルシューティングは、一般的な Analysis Services 接続のトラブルシューティングとほとんど同じです。 ただし、Power BI 固有の依存関係に関するいくつかの違いがあります。

## <a name="before-you-begin"></a>始める前に

XMLA エンドポイント シナリオのトラブルシューティングを行う前に、「[XMLA エンドポイントを使用したデータセット接続](service-premium-connect-tools.md)」に記載されている基本事項を確認してください。 そこでは、最も一般的な XMLA エンドポイントのユースケースについて説明されています。 Power BI のトラブルシューティングのその他のガイド、「[ゲートウェイのトラブルシューティング - Power BI](../connect-data/service-gateway-onprem-tshoot.md)」および「["Excel で分析" に関するトラブルシューティング](../collaborate-share/desktop-troubleshooting-analyze-in-excel.md)」も役立ちます。

## <a name="enabling-the-xmla-endpoint"></a>XMLA エンドポイントを有効にする

XMLA エンドポイントは、Power BI Premium と Power BI Embedded どちらの容量でも有効にすることができます。 メモリが 2.5 GB のみの A1 容量など、容量が少ない場合には、XMLA エンドポイントを **[読み取り/書き込み]** に設定しようとして、 **[適用]** を選択したとき、容量設定でエラーが発生することがあります。 エラーには、"There was an issue with your workload settings. Try again in a little while." (ワークロードの設定で問題が発生しました。しばらくしてからもう一度お試しください。) と表示されます。

次の 2 つの方法を試すことができます。

- 容量に対する他のサービス (データフローなど) のメモリ消費量を 40% 以下に制限するか、不要なサービスを完全に無効にします。  
- 大きい容量の SKU にアップグレードします。 たとえば、容量を A1 から A3 にアップグレードすると、データフローを無効にしなくても、この構成の問題は解決します。

Power BI 管理ポータルでテナントレベルの[エクスポート データ設定](service-premium-connect-tools.md#security)も有効にする必要があることに注意してください。 この設定は、[Excel で分析] 機能にも必要です。

## <a name="establishing-a-client-connection"></a>クライアント接続を確立する

XMLA エンドポイントを有効にした後は、その容量でワークスペースへの接続をテストすることをお勧めします。 詳細については、「[Premium ワークスペースに接続する](service-premium-connect-tools.md#connecting-to-a-premium-workspace)」を参照してください。 また、XMLA の接続に関する現在の制約に関する役立つヒントや情報について、「[接続の要件](service-premium-connect-tools.md#connection-requirements)」のセクションを確認してください。

### <a name="connecting-with-a-service-principal"></a>サービス プリンシパルを使用して接続する

「[サービス プリンシパルを有効にする](service-premium-service-principal.md#enable-service-principals)」の説明に従い、テナント設定でサービス プリンシパルが Power BI API を使用できるようにした場合、サービス プリンシパルを使用して XMLA エンドポイントに接続できます。 サービス プリンシパルには、ワークスペースまたはデータセット レベルで、通常のユーザーと同じレベルのアクセス許可が必要であることに注意してください。

サービス プリンシパルを使用するには、アプリケーション ID 情報を必ず次のように接続文字列に指定します。

- `User ID=<app:appid@tenantid>`
- `Password=<application secret>`

例:

`Data Source=powerbi://api.powerbi.com/v1.0/myorg/Contoso;Initial Catalog=PowerBI_Dataset;User ID=app:91ab91bb-6b32-4f6d-8bbc-97a0f9f8906b@19373176-316e-4dc7-834c-328902628ad4;Password=6drX...;`

次のエラー メッセージが表示される場合:

"We cannot connect to the dataset due to incomplete account information. For service principals, make sure you specify the tenant ID together with the app ID using the format app:\<appId>@\<tenantId>, then try again." (アカウント情報が不完全なためデータセットに接続できません。サービス プリンシパルについて、app:\<appId>@\<tenantId> という形式でテナント ID とアプリ ID を一緒に指定してから、やり直してください。)

正しい形式を使用して、アプリ ID と共にテナント ID を指定してください。

また、テナント ID を指定せずにアプリ ID を指定することもできます。 ただし、その場合は、データ ソース URL の `myorg` エイリアスを実際のテナント ID で置き換える必要があります。 そうすると、Power BI が、正しいテナントでサービス プリンシパルを見つけることができます。 ただし、ベスト プラクティスとしては、`myorg` エイリアスを使用し、ユーザー ID パラメーターにアプリ ID と共にテナント ID を指定することをお勧めします。

### <a name="connecting-with-azure-active-directory-b2b"></a>Azure Active Directory B2B を使用して接続する

Azure Active Directory (Azure AD) 企業間 (B2B) は Power BI でサポートされており、XMLA エンドポイントを介したデータセットへのアクセスを外部ゲスト ユーザーに提供できます。 Power BI 管理ポータルで [[外部ユーザーとコンテンツを共有する]](service-admin-portal.md#export-and-sharing-settings) 設定が有効になっていることを確認します。 詳細については、「[Azure AD B2B で外部ゲスト ユーザーに Power BI コンテンツを配布する](service-admin-azure-ad-b2b.md)」をご覧ください。

## <a name="deploying-a-dataset"></a>データセットを配置する

Visual Studio (SSDT) での表形式モデル プロジェクトの Power BI Premium ワークスペースへの配置は、Azure Analysis Services への配置とほとんど同じです。 ただし、Power BI Premium ワークスペースに配置する際には、追加の考慮事項がいくつかあります。 「XMLA エンドポイントを使用したデータセット接続」の記事で「[Visual Studio からモデル プロジェクトを配置する (SSDT)](service-premium-connect-tools.md#deploy-model-projects-from-visual-studio-ssdt)」のセクションを確認してください。

### <a name="deploying-a-new-model"></a>新しいモデルを配置する

既定の構成では、Visual Studio は配置操作の中でモデルの処理を試行し、データ ソースからデータセットにデータを読み込みます。 「[Visual Studio からモデル プロジェクトを配置する (SSDT)](service-premium-connect-tools.md#deploy-model-projects-from-visual-studio-ssdt)」で説明しているように、データ ソースの資格情報を配置操作の中で指定できないために、この操作が失敗する可能性があります。 その代わり、データ ソースの資格情報が既存のデータセットのいずれについても定義されていない場合は、データ ソースの資格情報を Power BI ユーザー インターフェイスを使用してデータセット設定に指定する必要があります ( **[データセット]**  >  **[設定]**  >  **[データ ソースの資格情報]**  >  **[資格情報の編集]** )。 データ ソースの資格情報を定義したら、メタデータ配置が成功してデータセットが作成された後で、新しいすべてのデータセットについて、Power BI がこのデータ ソースに資格情報を自動的に適用できます。

Power BI が新しいデータセットをデータ ソースの資格情報にバインドできない場合は、エラー "データベースを処理できません。 理由:サーバーに対する変更の保存に失敗しました。" が表示されます。 エラー コードは "DMTS_DatasourceHasNoCredentialError" です。以下をご覧ください。

:::image type="content" source="media/troubleshoot-xmla-endpoint/deploy-refresh-error.png" alt-text="モデル配置エラー":::

処理のエラーを回避するには、次の図のように、 **[配置オプション]**  >  **[処理オプション]** を **[処理しない]** に設定します。 そうすると、Visual Studio はメタデータのみを配置します。 次に、データ ソースの資格情報を構成し、Power BI ユーザー インターフェイスでデータセットについて **[今すぐ更新]** をクリックします。 処理の問題のトラブルシューティングの詳細については、この記事の後半の「[データセットを更新する](#refreshing-a-dataset)」のセクションを参照してください。

:::image type="content" source="media/troubleshoot-xmla-endpoint/do-not-process.png" alt-text="[処理しない] オプション":::

### <a name="new-project-from-an-existing-dataset"></a>既存のデータセットから新しいプロジェクト

Power BI Premium ワークスペースの既存のデータセットからメタデータをインポートして、Visual Studio の新しい表形式プロジェクトを作成することは、サポートされていません。 ただし、SQL Server Management Studio を使用してデータセットに接続し、メタデータをスクリプト化し、他の表形式プロジェクトで再利用することはできます。

## <a name="migrating-a-dataset-to-power-bi"></a>データセットを Power BI に移行する

表形式モデルには 1500 (以上) の互換性レベルを指定することをお勧めします。 この互換性レベルでは、ほとんどの機能とデータ ソースの種類がサポートされます。 新しい互換性レベルには、以前のレベルとの下位互換性があります。

### <a name="supported-data-providers"></a>サポートされているデータ プロバイダー

1500 互換性レベルで、Power BI は次の種類のデータ ソースをサポートします。

- プロバイダー データ ソース (モデル メタデータ内の接続文字列を使用するレガシ)。
- 構造化されたデータ ソース (1400 互換性レベルで導入)。
- データ ソースのインライン M 宣言 (Power BI Desktop によって宣言)。

構造化されたデータ ソースを使用することをお勧めします。これは、インポート データ フローを実行するときに Visual Studio によって既定で作成されます。 ただし、プロバイダーのデータ ソースを使用する Power BI に既存のモデルを移行する場合は、プロバイダーのデータ ソースが、サポート対象のデータ プロバイダーを使用することを確認してください。 具体的には、Microsoft OLE DB Driver for SQL Server およびサードパーティの ODBC ドライバーです。 OLE DB Driver for SQL Server の場合は、データ ソース定義を .NET Framework Data Provider for SQL Server に切り替える必要があります。 Power BI サービスで使用できない可能性があるサードパーティ ODBC ドライバーの場合は、代わりに、構造化データ ソースの定義に切り替える必要があります。

また、SQL Server データ ソース定義内の古い Microsoft OLE DB Driver for SQL Server (SQLNCLI11) も .NET Framework Data Provider for SQL Server で置き換えることをお勧めします。

次の表に示すのは、対応する OLE DB Driver for SQL Server の接続文字列を置き換える、.NET Framework Data Provider for SQL Server 接続文字列の例です。

|OLE DB Driver for SQL Server  |SQL Server 用の .NET Framework データ プロバイダー   |
|---------|---------|
|`Provider=SQLNCLI11;Data Source=sqldb.database.windows.net;Initial Catalog=AdventureWorksDW;Trusted_Connection=yes;`    |   `Data Source=sqldb.database.windows.net;Initial Catalog=AdventureWorksDW2016;Integrated Security=SSPI;Encrypt=true;TrustServerCertificate=false`       |

### <a name="cross-referencing-partition-sources"></a>パーティション ソースを相互参照する

複数の種類のデータ ソースがあるようにパーティション ソースにも複数の種類があり、表形式モデルに組み込んでデータをテーブルにインポートできます。 具体的には、パーティションは、クエリ パーティション ソースまたは M パーティション ソースを使用できます。 これらのパーティション ソースの種類は、プロバイダーのデータ ソースまたは構造化されたデータ ソースを参照できます。 Azure Analysis Services の表形式モデルでは、これらのさまざまなデータ ソースとパーティションの種類の相互参照がサポートされていますが、Power BI ではより厳密なリレーションシップが適用されます。 クエリ パーティション ソースはプロバイダー データ ソースを参照し、M パーティション ソースは構造化データ ソースを参照する必要があります。 その他の組み合わせは Power BI ではサポートされません。 相互参照データセットを移行する場合にサポートされている構成を次の表で説明します。  

|データ ソースの   |パーティション ソース   |コメント   |XMLA エンドポイントを使用する Power BI Premium でのサポート   |
|---------|---------|---------|---------|
|プロバイダー データ ソース      |   クエリ パーティション ソース      |   AS エンジンは、カートリッジベースの接続スタックを使用してデータ ソースにアクセスします。       |     はい     |
|プロバイダー データ ソース      |   M パーティション ソース       |   AS エンジンは、プロバイダー データ ソースを一般的な構造化データ ソースに変換し、マッシュアップ エンジンを使用してデータをインポートします。       |    いいえ     |
|構造化データ ソース      |     クエリ パーティション ソース     |    AS エンジンは、パーティション ソースに対するネイティブのクエリを M 式にラップしてから、マッシュアップ エンジンを使用してデータをインポートします。      |    いいえ     |
|構造化データ ソース      |    M パーティション ソース      |     AS エンジンは、マッシュアップ エンジンを使用してデータをインポートします。     |   はい      |

## <a name="refreshing-a-dataset"></a>データセットを更新する

XMLA エンドポイントを使用すると、表形式モデルおよび Power BI Desktop で作成されたデータセットに対して更新操作を実行できます。 後者をサポートするには、[Enhanced storage format]\(拡張ストレージ形式\)設定を必ず指定してください。 この設定は、XMLA エンドポイントを使用して、処理またはその他の読み取り/書き込み操作を実行する場合に必要です。 この設定は、Power BI Desktop のプレビュー機能の中にあります。 設定が完了したら、Power BI Premium ワークスペースに PBIX ソリューションを発行します。  

拡張メタデータを含まないモデルに対して XMLA エンドポイントを使用して更新を実行すると、Power BI によって次のエラーが返されます。"この操作は、Power BI Premium でプロパティ 'DefaultPowerBIDataSourceVersion' が 'PowerBI_V3' に設定されているモデルでのみサポートされています。"

### <a name="data-sources-and-impersonation"></a>データ ソースと権限の借用

プロバイダーのデータ ソースに対して定義できる権限の借用の設定は、Power BI には関係ありません。 Power BI は、データセットの設定に基づく別のメカニズムを使用して、データ ソースの資格情報を管理します。 このため、プロバイダー データ ソースを作成する場合は、 **[サービス アカウント]** を必ず選択してください。

:::image type="content" source="media/troubleshoot-xmla-endpoint/impersonate-services-account.png" alt-text="サービス アカウントの権限を借用":::

### <a name="fine-grained-processing"></a>きめ細かい処理

Power BI で、スケジュールされた更新またはオンデマンドの更新をトリガーするとき、通常、Power BI はデータセット全体を更新します。 多くの場合、選択して更新を実行する方が効率的です。 次のように SQL Server Management Studio (SSMS) で、またはサードパーティのツールまたはスクリプトを使用して、きめ細かい処理を実行できます。

:::image type="content" source="media/troubleshoot-xmla-endpoint/process-tables.png" alt-text="SSMS でのテーブルの処理":::

### <a name="overrides-in-refresh-tmsl-command"></a>Refresh TMSL コマンドでのオーバーライド

[Refresh コマンド (TMSL)](/analysis-services/tmsl/refresh-command-tmsl) でのオーバーライドを使用すると、ユーザーは更新操作のために別のパーティション クエリ定義またはデータ ソース定義を選択できます。 現時点では、Power BI Premium では **オーバーライドはサポートされていません**。 エラー "Out-of-line binding is not allowed in Power BI Premium. For additional information, see 'XMLA read/write support' in the product documentation." (不一致バインドは Power BI Premium では許可されていません。詳細については、製品ドキュメントの「XMLA の読み取りおよび書き込みのサポート」を参照してください。) が 返されます。

## <a name="errors-in-ssms---premium-gen-2"></a>SSMS のエラー - Premium Gen 2

### <a name="query-execution"></a>クエリ実行

[Premium Gen2](service-premium-what-is.md#power-bi-premium-generation-2-preview) 容量のワークスペースに接続されているとき、SQL Server Management Studio に次のエラーが表示されることがあります。

```
Executing the query ...
Error -1052311437:
```

これは、SSMS v18.7.1 でインストールされたクライアント ライブラリでセッション トレーシングがサポートされていないために発生します。 これは SSMS 18.8 以降で解決されています。 [最新の SSMS をダウンロードしてください](/sql/ssms/download-sql-server-management-studio-ssms)。

### <a name="refresh-operations"></a>更新操作

v18.7.1 以前の SSMS を使用し、Premium Gen2 容量のデータセットで長時間 (1 分超) の更新操作を実行するとき、更新操作に成功したとしても、SSMS には次のようなエラーが表示されることがあります。

```
Executing the query ...
Error -1052311437:
The remote server returned an error: (400) Bad Request.

Technical Details:
RootActivityId: 3716c0f7-3d01-4595-8061-e6b2bd9f3428
Date (UTC): 11/13/2020 7:57:16 PM
Run complete
```

これは、更新要求の状態が間違って追跡記録されるというクライアント ライブラリの既知の問題によるものです。 これは SSMS 18.8 以降で解決されています。 [最新の SSMS をダウンロードしてください](/sql/ssms/download-sql-server-management-studio-ssms)。

## <a name="editing-role-memberships-in-ssms"></a>SSMS でロール メンバーシップを編集する

SQL Server Management Studio (SSMS) v18.8 を使用してデータセットのロール メンバーシップを編集するとき、SSMS に次のエラーが表示されることがあります。

```
Failed to save modifications to the server. 
Error returned: ‘Metadata change of current operation cannot be resolved, please check the command or try again later.’ 
```

これはアプリ サービス REST API の既知の問題によるものです。 これは今後のリリースで解決される予定です。 それまでの間は、このエラーを回避するには、 **[ロールのプロパティ]** で **[スクリプト]** をクリックし、次の TMSL コマンドを入力し、実行してください。

```json
{ 
  "createOrReplace": { 
    "object": { 
      "database": "AdventureWorks", 
      "role": "Role" 
    }, 
    "role": { 
      "name": "Role", 
      "modelPermission": "read", 
      "members": [ 
        { 
          "memberName": "xxxx", 
          "identityProvider": "AzureAD" 
        }, 
        { 
          "memberName": “xxxx” 
          "identityProvider": "AzureAD" 
        } 
      ] 
    } 
  } 
} 
```

## <a name="publish-error---live-connected-dataset"></a>発行エラー - ライブ接続されたデータセット

Analysis Services コネクタを使用し、ライブ接続されたデータセットを再発行するとき、次のエラーが表示されることがあります。

:::image type="content" source="media/troubleshoot-xmla-endpoint/couldnt-publish-to-power-bi.png" alt-text="Power BI エラーに発行できませんでした。":::

エラー メッセージに示されているように、この問題を解決するには、既存のデータセットを削除するか、その名前を変更します。 また、レポートに依存しているアプリがあれば、それを必ず再発行してください。 必要であれば、最新のレポートにアクセスできるよう、新しいレポートでブックマークを更新するように下流のユーザーにもお知らせください。  

## <a name="see-also"></a>関連項目

[XMLA エンドポイントを使用したデータセット接続](service-premium-connect-tools.md)  
[サービス プリンシパルを使用して Premium ワークスペースとデータセットのタスクを自動化する](service-premium-service-principal.md)  
[Excel で分析のトラブルシューティング](../collaborate-share/desktop-troubleshooting-analyze-in-excel.md)  
[表形式モデル ソリューションのデプロイ](/analysis-services/deployment/tabular-model-solution-deployment?view=power-bi-premium-current&preserve-view=true)
