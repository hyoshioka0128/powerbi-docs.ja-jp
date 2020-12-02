---
title: データ ソースの管理 - SQL
description: オンプレミス データ ゲートウェイとそのゲートウェイに属している SQL Server データ ソースを管理する方法。
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: how-to
ms.date: 07/15/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 513b5b509328641e2c9f4965741b92939526aee1
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96402411"
---
# <a name="manage-your-data-source---sql-server"></a>データ ソースの管理 - SQL Server

[!INCLUDE [gateway-rewrite](../includes/gateway-rewrite.md)]

[オンプレミス データ ゲートウェイをインストール](/data-integration/gateway/service-gateway-install)したら、ゲートウェイで使用できる[データ ソースを追加](service-gateway-data-sources.md#add-a-data-source)することができます。 この記事では、スケジュールされた更新または DirectQuery に使用されるゲートウェイと SQL Server データ ソースの操作方法について説明します。

## <a name="add-a-data-source"></a>データ ソースの追加

データ ソースを追加する方法の詳細については、「[データ ソースの追加](service-gateway-data-sources.md#add-a-data-source)」を参照してください。 **[データ ソースの種類]** で、 **[SQL Server]** を選択します。

![SQL Server データ ソースの選択](media/service-gateway-enterprise-manage-sql/datasourcesettings2.png)

> [!NOTE]
> DirectQuery をお使いの場合、ゲートウェイでは **SQL Server 2012 SP1** 以降のバージョンのみがサポートされます。

**[サーバー]** や **[データベース]** など、データ ソースの情報を入力します。 

**[認証方法]** で、 **[Windows]** または **[基本]** を選択します。 Windows 認証ではなく SQL 認証を使用する場合は、 **[基本]** を選択します。 次に、このデータ ソースに使用する資格情報を入力します。

> [!NOTE]
> データ ソースへのすべてのクエリは、これらの資格情報を使用して実行されますが、Kerberos シングル サインオン (SSO) が構成されていて、データ ソースに対して有効な場合を除きます。 SSO を使用すると、インポート データセットは保存された資格情報を使用しますが、DirectQuery データセットは現在の Power BI ユーザーを使用し、SSO を使用してクエリを実行します。 資格情報の格納方法の詳細については、「[暗号化された資格情報をクラウドに格納する](service-gateway-data-sources.md#store-encrypted-credentials-in-the-cloud)」を参照してください。 または、[Power BI からオンプレミス データ ソースへのシングル サインオン (SSO) に Kerberos を使用する](service-gateway-sso-kerberos.md)方法について説明している記事を参照してください。

![データ ソース設定の入力](media/service-gateway-enterprise-manage-sql/datasourcesettings3.png)

すべての情報を入力したら、 **[追加]** を選択します。 これで、オンプレミスの SQL Server サーバーに対するスケジュールされた更新または DirectQuery にこのデータ ソースを使用できるようになりました。 成功すると、"*接続成功*" というメッセージが表示されます。

![接続の状態の表示](media/service-gateway-enterprise-manage-sql/datasourcesettings4.png)

### <a name="advanced-settings"></a>詳細設定

必要に応じて、データ ソースのプライバシー レベルを構成できます。 この設定により、データを結合できる方法が管理されます。 これは、スケジュールされた更新にのみ使用されます。 プライバシー レベルの設定は、DirectQuery には適用されません。 データ ソースのプライバシー レベルの詳細については、「[プライバシーレベル (Power Query)](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540)」を参照してください。

![プライバシー レベルの設定](media/service-gateway-enterprise-manage-sql/datasourcesettings9.png)

## <a name="use-the-data-source"></a>データ ソースを使用する

作成したデータ ソースは、DirectQuery 接続またはスケジュールされた更新のいずれかで使用できます。

> [!NOTE]
> Power BI Desktop とオンプレミス データ ゲートウェイ内のデータ ソースとの間で、サーバーとデータベース名が一致している必要があります。

データセットとゲートウェイ内のデータ ソース間のリンクは、サーバー名とデータベース名に基づいています。 これらの名前は一致している必要があります。 たとえば、Power BI Desktop 内でサーバー名の IP アドレスを指定する場合は、ゲートウェイ構成内のデータ ソースでもその IP アドレスを使用する必要があります。 Power BI Desktop で *SERVER\INSTANCE* を使用する場合は、ゲートウェイ用に構成されているデータ ソース内でそれを使用する必要があります。

この要件は、DirectQuery とスケジュールされた更新のどちらにも該当します。

### <a name="use-the-data-source-with-directquery-connections"></a>DirectQuery 接続でデータ ソースを使用する

Power BI Desktop とゲートウェイ用に構成されているデータ ソースとの間で、サーバーとデータベース名が一致していることを確認します。 また、DirectQuery のデータセットを公開するには、自分のアカウントがデータ ソースの **[ユーザー]** タブの一覧に表示されている必要があります。 DirectQuery の選択は、最初にデータをインポートする Power BI Desktop 内で発生します。 Directquery の使用方法の詳細については、「[Power BI Desktop で DirectQuery を使用する](desktop-use-directquery.md)」を参照してください。

公開した後は、Power BI Desktop または **[データの取得]** のいずれかから、レポート機能が利用可能になります。 ゲートウェイ内にデータ ソースを作成してから、接続が使用できるようになるまでには、数分ほどかかることがあります。

### <a name="use-the-data-source-with-scheduled-refresh"></a>スケジュールされた更新でデータ ソースを使用する

ゲートウェイ内に構成されているデータ ソースの **[ユーザー]** タブの一覧に自分のアカウントが表示されていて、さらにサーバー名とデータベース名が一致している場合は、スケジュールされた更新で使用するオプションとして、ゲートウェイが表示されます。

![ユーザーの表示](media/service-gateway-enterprise-manage-sql/powerbi-gateway-enterprise-schedule-refresh.png)

## <a name="next-steps"></a>次のステップ

* [SQL Server でオンプレミス データに接続する](service-gateway-sql-tutorial.md)
* [オンプレミス データ ゲートウェイのトラブルシューティング](/data-integration/gateway/service-gateway-tshoot)
* [ゲートウェイのトラブルシューティング - Power BI](service-gateway-onprem-tshoot.md)
* [Power BI からオンプレミス データ ソースへのシングル サインオン (SSO) に Kerberos を使用する](service-gateway-sso-kerberos.md)

他にわからないことがある場合は、 [Power BI コミュニティ](https://community.powerbi.com/)で質問してみてください。
