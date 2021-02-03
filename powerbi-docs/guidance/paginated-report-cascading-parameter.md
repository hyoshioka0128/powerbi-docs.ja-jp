---
title: ページ分割されたレポートでカスケード型パラメーターを使用する
description: カスケード型パラメーターを使用してページ分割されたレポートをデザインするためのガイダンス。
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 01/14/2020
ms.openlocfilehash: 826c43d67d76f1f53f2bf9b45e519469b9e71c75
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2021
ms.locfileid: "99087708"
---
# <a name="use-cascading-parameters-in-paginated-reports"></a>ページ分割されたレポートでカスケード型パラメーターを使用する

この記事の対象読者は、Power BI の[ページ分割されたレポート](../paginated-reports/paginated-reports-report-builder-power-bi.md)をデザインするレポート作成者です。 カスケード型パラメーターを設計するためのシナリオが示されています。 カスケード型パラメーターは、依存関係があるレポート パラメーターです。 レポート ユーザーが 1 つのパラメーター値 (または複数の値) を選択すると、それを使用して別のパラメーターで使用可能な値が設定されます。

> [!NOTE]
> カスケード型パラメーターの概要とその構成方法については、この記事では説明しません。 カスケード型パラメーターについて完全には理解していない場合は、まず「[レポートにカスケード型パラメーターを追加する (Report Builder とSSRS)](/sql/reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs)」を確認することをお勧めします。

## <a name="design-scenarios"></a>デザイン シナリオ

カスケード型パラメーターを使用するには、2 つのデザイン シナリオがあります。 それらを効果的に使用して、以下を実行できます。

- 項目の "_大量のセット_" をフィルター処理する
- "_関連性のある_" 項目を表示する

### <a name="example-database"></a>データベースの例

この記事で紹介する例は、Azure SQL Database に基づいています。 データベースには販売活動が記録され、リセラー、製品、および販売注文を格納するさまざまなテーブルが含まれています。

**Reseller** という名前のテーブルには、リセラーごとに 1 つのレコードが格納され、多数のレコードが含まれています。 **Reseller** テーブルには、次の列があります。

- ResellerCode (整数)
- ResellerName
- 国/地域
- State-Province
- 市区町村
- 郵便番号

**Sales** という名前のテーブルもあります。 それには、販売注文レコードが格納され、**Reseller** テーブルの **ResellerCode** 列との外部キー リレーションシップがあります。

### <a name="example-requirement"></a>例の要件

リセラー プロファイル レポートを作成する必要があります。 レポートは、単一のリセラーの情報を表示するようにデザインする必要があります。 レポート ユーザーがリセラー コードを覚えていることはめったにないので、それを入力させるのは適切ではありません。

## <a name="filter-large-sets-of-items"></a>項目の大量のセットをフィルター処理する

リセラーなどの使用可能な項目の大量のセットを限定するために役立つ 3 つの例を見ていきましょう。 これらは次のとおりです。

- [関連性のある列によるフィルター処理](#filter-by-related-columns)
- [グループ化列によるフィルター処理](#filter-by-a-grouping-column)
- [検索パターンによるフィルター処理](#filter-by-search-pattern)

### <a name="filter-by-related-columns"></a>関連性のある列によるフィルター処理

この例では、レポート ユーザーは、5 つのレポート パラメーターを操作します。 国/地域、都道府県、市区町村、および郵便番号を選択する必要があります。 最後のパラメーターには、その地理的な場所にあるリセラーの一覧が表示されます。

![関連する列によるフィルター処理が示されている Power BI のページ分割されたレポート パラメーターのスクリーンショット。](media/paginated-report-cascading-parameter/filter-by-related-columns-example.png)

カスケード型パラメーターを作成する方法を次に示します。

1. 5 つのレポート パラメーターを、正しい順序で作成します。
2. 次のクエリ ステートメントを使用して、個別の国/地域の値を取得する **CountryRegion** データセットを作成します。

    ```sql
    SELECT DISTINCT
      [Country-Region]
    FROM
      [Reseller]
    ORDER BY
      [Country-Region]
    ```

3. 次のクエリ ステートメントを使用して、選択した国/地域での個別の都道府県の値を取得する **StateProvince** データセットを作成します。

    ```sql
    SELECT DISTINCT
      [State-Province]
    FROM
      [Reseller]
    WHERE
      [Country-Region] = @CountryRegion
    ORDER BY
      [State-Province]
    ```

4. 次のクエリ ステートメントを使用して、選択した国/地域と都道府県での個別の市町村の値を取得する **City** データセットを作成します。

    ```sql
    SELECT DISTINCT
      [City]
    FROM
      [Reseller]
    WHERE
      [Country-Region] = @CountryRegion
      AND [State-Province] = @StateProvince
    ORDER BY
      [City]
    ```

5. このパターンを続行して、**PostalCode** データセットを作成します。
6. 次のクエリ ステートメントを使用して、選択した地理的な値に該当するすべてのリセラーを取得する **Reseller** データセットを作成します。

    ```sql
    SELECT
      [ResellerCode],
      [ResellerName]
    FROM
      [Reseller]
    WHERE
      [Country-Region] = @CountryRegion
      AND [State-Province] = @StateProvince
      AND [City] = @City
      AND [PostalCode] = @PostalCode
    ORDER BY
      [ResellerName]
    ```

7. 最初のデータセット以外のデータセットで、クエリ パラメーターを対応するレポート パラメーターにマップします。

> [!NOTE]
> これらの例に示されているすべてのクエリ パラメーター (頭に @ 記号が付いているもの) は、SELECT ステートメントに埋め込むことも、ストアド プロシージャに渡すこともできます。
>
> 一般に、ストアド プロシージャは、より優れたデザイン アプローチです。 その理由は、クエリ プランがキャッシュされて実行時間が短縮されるためと、必要に応じてより高度なロジックを開発することができるためです。 ただし、現在のところ、ゲートウェイ リレーショナル データソース、つまり SQL Server、Oracle、および Teradata ではサポートされていません。
>
> 最後に、効率的なデータ取得をサポートするために、適切なインデックスが存在することを常に確認してください。 そうしないと、レポート パラメーターの設定に時間がかかり、データベースが過負荷になる可能性があります。 SQL Server のインデックス作成の詳細については、「[SQL Server のインデックスのアーキテクチャとデザイン ガイド](/sql/relational-databases/sql-server-index-design-guide)」を参照してください。

### <a name="filter-by-a-grouping-column"></a>グループ化列によるフィルター処理

この例では、レポート ユーザーは、リセラーの最初の文字を選択するレポート パラメーターを操作します。 2 番目のパラメーターには、その名前が選択した文字で始まるリセラーの一覧が表示されます。

![グループ化列によるフィルター処理が示されている Power BI のページ分割されたレポート パラメーターのスクリーンショット。](media/paginated-report-cascading-parameter/filter-by-grouping-column-example.png)

カスケード型パラメーターを作成する方法を次に示します。

1. **ReportGroup** と **Reseller** レポート パラメーターを、正しい順序で作成します。
2. 次のクエリ ステートメントを使用して、すべてのリセラーで使用されている最初の文字を取得する **ReportGroup** データセットを作成します。

    ```sql
    SELECT DISTINCT
      LEFT([ResellerName], 1) AS [ReportGroup]
    FROM
      [Reseller]
    ORDER BY
      [ReportGroup]
    ```

3. 次のクエリ ステートメントを使用して、選択した文字で始まるすべてのリセラーを取得する **Reseller** データセットを作成します。

    ```sql
    SELECT
      [ResellerCode],
      [ResellerName]
    FROM
      [Reseller]
    WHERE
      LEFT([ResellerName], 1) = @ReportGroup
    ORDER BY
      [ResellerName]
    ```

4. **Reseller** データセットのクエリ パラメーターを、対応するレポート パラメーターにマップします。

**Reseller** テーブルにグループ化列を追加するほうが効率的です。 永続化され、インデックスが作成されると、最善の結果が得られます。 詳細については、「 [テーブルの計算列の指定](/sql/relational-databases/tables/specify-computed-columns-in-a-table)」を参照してください。

```sql
ALTER TABLE [Reseller]
ADD [ReportGroup] AS LEFT([ResellerName], 1) PERSISTED
```

この手法で、さらに多くの可能性を引き出すことができます。 "_定義済みの一群の文字_" によってリセラーをフィルター処理する新しいグループ化列を追加する次のスクリプトを検討します。 レポート パラメーターによって要求されるデータを効率的に取得するためのインデックスも作成されます。

```sql
ALTER TABLE [Reseller]
ADD [ReportGroup2] AS CASE
  WHEN [ResellerName] LIKE '[A-C]%' THEN 'A-C'
  WHEN [ResellerName] LIKE '[D-H]%' THEN 'D-H'
  WHEN [ResellerName] LIKE '[I-M]%' THEN 'I-M'
  WHEN [ResellerName] LIKE '[N-S]%' THEN 'N-S'
  WHEN [ResellerName] LIKE '[T-Z]%' THEN 'T-Z'
  ELSE '[Other]'
END PERSISTED
GO

CREATE NONCLUSTERED INDEX [Reseller_ReportGroup2]
ON [Reseller] ([ReportGroup2]) INCLUDE ([ResellerCode], [ResellerName])
GO
```

### <a name="filter-by-search-pattern"></a>検索パターンによるフィルター処理

この例では、レポート ユーザーは、検索パターンを入力するレポート パラメーターを操作します。 2 番目のパラメーターには、その名前にパターンが含まれているリセラーの一覧が表示されます。

![検索パターンによるフィルター処理が示されている Power BI のページ分割されたレポート パラメーターのスクリーンショット。](media/paginated-report-cascading-parameter/filter-by-search-pattern-example.png)

カスケード型パラメーターを作成する方法を次に示します。

1. **Search** と **Reseller** レポート パラメーターを、正しい順序で作成します。
2. 次のクエリ ステートメントを使用して、検索テキストが含まれるすべてのリセラーを取得する **Reseller** データセットを作成します。

    ```sql
    SELECT
      [ResellerCode],
      [ResellerName]
    FROM
      [Reseller]
    WHERE
      [ResellerName] LIKE '%' + @Search + '%'
    ORDER BY
      [ResellerName]
    ```

3. **Reseller** データセットのクエリ パラメーターを、対応するレポート パラメーターにマップします。

> [!TIP]
> レポート ユーザーによる制御を強化するようにこのデザインを改良できます。 独自のパターン マッチング値を定義させることができます。 たとえば、"red%" という検索値では、リセラーが "red" という文字で "_始まる_" 名前でフィルター処理されます。
>
> 詳細については、「[LIKE (Transact-SQL)](/sql/t-sql/language-elements/like-transact-sql#using-the--wildcard-character)」を参照してください。

レポート ユーザーが独自のパターンを定義できるようにする方法を次に示します。

```sql
WHERE
  [ResellerName] LIKE @Search
```

ただし、多くのデータベース以外の専門家は、パーセント (%) というワイルドカード文字を知りません。 代わりに、アスタリスク (*) 文字を使用することに慣れています。 WHERE 句を変更することで、この文字を使用させることができます。

```sql
WHERE
  [ResellerName] LIKE SUBSTITUTE(@Search, '%', '*')
```

## <a name="present-relevant-items"></a>関連性のある項目を表示する

このシナリオでは、ファクト データを使用して、使用可能な値を制限できます。 レポート ユーザーには、アクティビティが記録されている項目が表示されます。

この例では、レポート ユーザーは、3 つのレポート パラメーターを操作します。 最初の 2 つには、販売注文日の日付範囲が設定されます。 3 番目のパラメーターには、その期間中に注文が作成されたリセラーの一覧が表示されます。

![次の 3 つのレポート パラメーターが示されている Power BI のページ分割されたレポート パラメーターのスクリーンショット。[開始注文日]、[終了注文日]、および [リセラー]。](media/paginated-report-cascading-parameter/filter-relevant-items-example.png)

カスケード型パラメーターを作成する方法を次に示します。

1. **OrderDateStart**、**OrderDateEnd**、および **Reseller** レポート パラメーターを、正しい順序で作成します。
2. 次のクエリ ステートメントを使用して、期間中に注文が作成されたすべてのリセラーを取得する **Reseller** データセットを作成します。

    ```sql
    SELECT DISTINCT
      [r].[ResellerCode],
      [r].[ResellerName]
    FROM
      [Reseller] AS [r]
    INNER JOIN [Sales] AS [s]
      ON [s].[ResellerCode] = [r].[ResellerCode]
    WHERE
      [s].[OrderDate] >= @OrderDateStart
      AND [s].[OrderDate] < DATEADD(DAY, 1, @OrderDateEnd)
    ORDER BY
      [r].[ResellerName]
    ```

## <a name="recommendations"></a>推奨事項

可能な限り、カスケード型パラメーターを使用してレポートをデザインすることをお勧めします。 その理由は次のとおりです。

- レポート ユーザーに直感的で便利なエクスペリエンスを提供する
- 取得される使用可能な値のセットが小さくなるため、効率的である

次の方法でデータ ソースを最適化してください。

- 可能な場合は常にストアド プロシージャを使用する
- 効率的なデータ取得のための適切なインデックスを追加する
- 高コストのクエリ時間の評価を避けるために、列の値 (および行) を具体化する

## <a name="next-steps"></a>次の手順

この記事に関する詳細については、次のリソースを参照してください。

- [Power BI Report Builder でのレポート パラメーター](../paginated-reports/report-builder-parameters.md)
- [カスケード型パラメーターをレポートに追加する (Report Builder および SSRS)](/sql/reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs)
- わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
- Power BI チームへのご提案は、 [Power BI を改善するためのアイデアをお寄せください](https://ideas.powerbi.com)
