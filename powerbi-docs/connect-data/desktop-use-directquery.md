---
title: Power BI Desktop の DirectQuery
description: Power BI Desktop の DirectQuery (ライブ接続とも呼ばれます) を使用します
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 08/28/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 4619219705a80b53883a9b0578791a60a853125e
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96404228"
---
# <a name="use-directquery-in-power-bi-desktop"></a>Power BI Desktop の DirectQuery
*Power BI Desktop* では、データ ソースに接続するときに、常にデータのコピーを Power BI Desktop にインポートすることができます。 データ ソースによっては、代替手法を利用できます。DirectQuery を使用して、データ ソースに直接接続します。

## <a name="supported-data-sources"></a>サポートされるデータ ソース
DirectQuery をサポートするデータ ソースの完全なリストについては、「[DirectQuery でサポートされるデータ ソース](power-bi-data-sources.md)」を参照してください。

## <a name="how-to-connect-using-directquery"></a>DirectQuery を使用して接続する方法
**[データの取得]** を使用して、DirectQuery でサポートされているデータ ソースに接続すると、接続ダイアログ ボックスで接続方法を選択できます。 たとえば、Power BI Desktop の **[ホーム]** リボンで、 **[データの取得]**  >  **[SQL Server]** の順に選択します。 **[SQL Server データベース]** ダイアログ ボックスの **[データ接続モード]** に、**Import** と **DirectQuery** のオプションが表示されます。

![Import と DirectQuery のオプション、SQL Server データベース ダイアログ、Power BI Desktop](media/desktop-use-directquery/directquery_sqlserverdb.png)

**Import** と **DirectQuery** の選択の違いを以下に示します。

- **インポート**:選択されたテーブルと列は Power BI Desktop にインポートされます。 視覚エフェクトを作成するか、操作するときPower BI Desktop はインポートされたデータを使用します。 初回インポートまたは最新の更新以降の基になるデータの変更を確認するには、データを更新し、完全なデータ セットをもう一度インポートする必要があります。

- **DirectQuery**:Power BI Desktop にデータがインポートされたり、コピーされたりすることはありません。 リレーショナル ソースの場合、選択したテーブルと列は **[フィールド]** リストに表示されます。 SAP Business Warehouse のように多次元ソースの場合、選択したキューブのディメンションとメジャーは **[フィールド]** リストに表示されます。 視覚エフェクトを作成または操作するときに、Power BI Desktop で基になるデータ ソースに対してクエリが実行されるため、常に現在のデータが表示されます。

いくつかの制約がありますが、DirectQuery の使用時に多くのデータ モデリングとデータ変換を利用できます。 視覚エフェクトを作成または操作する場合は、基になるソースに対してクエリを実行する必要があります。 視覚エフェクトの更新に必要な時間は、基になるデータ ソースのパフォーマンスによって異なります。 要求の処理に必要なデータが最近要求された場合、Power BI Desktop では最近のデータが使用され、視覚エフェクトの表示に必要な時間が短縮されます。 **[ホーム]** リボンの **[更新]** を選択すると、すべての視覚エフェクトが現在のデータで更新されます。

DirectQuery の詳細については、「[Power BI と DirectQuery](desktop-directquery-about.md)」の記事を参照してください。 DirectQuery を使用する場合の利点、制限、重要な考慮事項について詳しくは、次のセクションを参照してください。

## <a name="benefits-of-using-directquery"></a>DirectQuery を使用する利点
DirectQuery を使用する利点をいくつか以下に示します。

- DirectQuery では非常に大きなデータセットに対して視覚エフェクトを構築できますが、他の方法では、事前集計を使用して最初にすべてのデータをインポートすることはできません。
- 基になるデータが変更されると、データの更新が必要になる場合があります。 一部のレポートでは、最新のデータを表示するために大規模なデータ転送が必要になる場合があり、データを再インポートできなくなります。 これに対し、DirectQuery レポートでは常に現在のデータが使用されます。
- 1 GB のデータセット制限は、DirectQuery には適用され "*ません*"。

## <a name="limitations-of-directquery"></a>DirectQuery の制限
現在、DirectQuery の使用には、いくつかの制限があります。

- **クエリ エディター** のクエリが複雑すぎると、エラーが発生します。 エラーを解決するには、問題となるステップを **クエリ エディター** で削除するか、DirectQuery を使用する代わりにデータを "*インポート*" します。 SAP Business Warehouse のような多次元ソースの場合、**クエリ エディター** はありません。

- タイム インテリジェンス機能は DirectQuery では利用できません。 たとえば、データ列 (年度、四半期、月、日など) の特殊な処理は、DirectQuery モードではサポートされていません。

- 計算テーブルおよび計算列で、シングル サインオン (SSO) 認証を使用してデータ ソースから DirectQuery テーブルを参照することは、Power BI サービスではサポートされていません。

- 基になるデータ ソースに送信されるクエリが許容範囲のパフォーマンスを確実に発揮できるよう、メジャー内で許可される DAX 式には制約があります。

- クラウド ソースには 100 万行の制限があり、オンプレミス ソースでは、定義されているペイロードが 1 行あたり約 4 MB (独自の圧縮アルゴリズムに依存)、またはビジュアル全体に対して 16MB データ サイズに制限されています。 Premium 容量を使用するとき、特定の制限が発生する場合があります。 この制限は、DirectQuery を使用して返されるデータセットの作成に使用される集計や計算には影響しません。 返される行にのみ影響します。 Premium 容量の場合、[こちらの投稿](https://powerbi.microsoft.com/blog/five-new-power-bi-premium-capacity-settings-is-available-on-the-portal-preloaded-with-default-values-admin-can-review-and-override-the-defaults-with-their-preference-to-better-fence-their-capacity/)で説明されているように、最大行数の制限を設定できます。 

    たとえば、データ ソースで実行されるクエリを使用して、1,000 万行を集計できます。 返された Power BI データが 100 万行未満の場合、クエリでは、DirectQuery を使用して Power BI にその集計の結果が正確に返されます。 DirectQuery から 100 万を超える行が返された場合、(Premium 容量で、行数が管理者が設定した上限を下回る場合を除き) Power BI からはエラーが返されます。


## <a name="important-considerations-when-using-directquery"></a>DirectQuery を使用する場合の重要な考慮事項
DirectQuery を使用する場合は、次の 3 つの点を考慮してください。

- **パフォーマンスと負荷**:DirectQuery 要求はすべて、ソース データベースに送信されます。そのため、ビジュアルの更新に必要な時間は、そのバックエンド ソースがクエリの結果で応答する時間によって異なります。 ビジュアルに DirectQuery を使用する場合、(要求されたデータが返される) 推奨応答時間は 5 秒以内です。最大推奨時間は 30 秒です。 それ以上長くなると、レポート使用のユーザー エクスペリエンスが許容範囲外になります。 レポートが Power BI サービスに発行された後、数分以上かかるクエリはすべてタイムアウトとなり、ユーザーはエラーを受け取ります。
  
    ソース データベースの負荷も、公開されたレポートを使用する Power BI ユーザーの数に基づき考慮してください。 **行レベル セキュリティ** (RLS) を使用する場合も、大きな影響を与える可能性があります。 複数のユーザーによって共有される RLS 以外のダッシュボード タイルでは、データベースに対して 1 つのクエリが実行されます。 しかし、ダッシュボード タイルで RLS を使用することは、通常、タイルの更新には、"*ユーザーごと*" に 1 つのクエリが必要になり、ソース データベースへの負荷が大幅に増加し、パフォーマンスに影響する可能性があることを意味します。
  
    Power BI では、可能な限り効率的なクエリが作成されます。 しかし、特定の状況では、生成されたクエリは十分に効率的ではなく、更新が失敗することがあります。 このような状況の一例として、生成されたクエリで、バックエンド データ ソースから非常に多数の行が取得される場合が挙げられます。 この場合、次のエラーが発生します。

    ```output
    The resultset of a query to external data source has exceeded
    ```
  
    このような状況は、カーディナリティが非常に高い列を含む簡単なグラフで集計オプションが **[Don’t Summarize]** (集計しない) に設定されている場合に発生します。 ビジュアルには、カーディナリティが 100 万未満の列のみが必要です。あるいは、適切なフィルターを適用する必要があります。

- **セキュリティ**:既定では、発行されたレポートを利用するすべてのユーザーは、Power BI サービスへの発行後に入力された資格情報を利用して、バックエンド データ ソースに接続します。 このプロセスはインポートされたデータと同じです。バックエンド ソースに定義されているセキュリティ ルールに関係なく、すべてのユーザーに同じデータが表示されます。

    DirectQuery ソースで実装されたユーザーごとのセキュリティが必要なお客様は、RLS を使用するか、ソースに対する Kerberos 制約付き認証を構成する必要があります。 Kerberos はすべてのソースで使用できるわけではありません。 [RLS についての詳細情報](../admin/service-admin-rls.md)。 [DirectQuery についての詳細情報](service-gateway-sso-kerberos.md)。

- **サポートされている機能**:Power BI Desktop の一部の機能は DirectQuery モードでサポートされていないか、制限があります。 また、Power BI サービスの一部の機能 (*クイック分析情報* など) は、DirectQuery を使用するデータセットでは利用できません DirectQuery を使用するかどうかを決定するときは、これらの機能の制限事項を考慮する必要があります。

> [!NOTE]
> Azure SQL Database とプライベート IP アドレスで DirectQuery を使用する場合は、オンプレミスのゲートウェイが必要です。 

## <a name="publish-to-the-power-bi-service"></a>Power BI サービスに公開する
DirectQuery を使用して作成されたレポートを、Power BI サービスに発行できます。

使用されたデータ ソースで **オンプレミス データ ゲートウェイ** が必要でない場合 (**Azure SQL Database**、**Azure SQL Data Warehouse**、または **Redshift**) は、発行されたレポートが Power BI サービスで表示される前に資格情報を入力する必要があります。 資格情報を入力するには、これらの手順に従います。

1. [Power BI](https://www.powerbi.com/) にサインインします。
2. Power BI サービスで、 **[設定]** 歯車アイコンを選択し、 **[設定]** メニュー項目を選びます。

    ![[設定]、Power BI サービス](media/desktop-use-directquery/directquery_pbiservicesettings.png)

3. Power BI サービスの [設定] ページで、 **[データセット]** タブを選択し、**DirectQuery** を使用するデータセットを選び、 **[資格情報を編集]** を選択します。

4. 資格情報を追加します。 そうしないと、発行されたレポートを開いたとき、または DirectQuery 接続で作成されたデータセットを探索したときにエラーが発生します。

DirectQuery を使用する **Azure SQL Database**、**Azure SQL Data Warehouse**、**Redshift**、または **Snowflake Data Warehouse** 以外のデータ ソースのデータ接続を行うには、**オンプレミス データ ゲートウェイ** をインストールし、データ ソースを登録します。 詳細については、「[オンプレミス データ ゲートウェイとは](service-gateway-onprem.md)」を参照してください

## <a name="next-steps"></a>次の手順
DirectQuery の詳細については、次のリソースを参照してください。

- [Power BI で DirectQuery を使用する](desktop-directquery-about.md)
- [DirectQuery でサポートされるデータ ソース](power-bi-data-sources.md)
- [DirectQuery と SAP Business Warehouse (BW)](desktop-directquery-sap-bw.md)
- [DirectQuery と SAP HANA](desktop-directquery-sap-hana.md)
- [オンプレミス データ ゲートウェイとは](service-gateway-onprem.md)
