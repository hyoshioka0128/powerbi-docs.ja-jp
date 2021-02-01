---
title: チュートリアル:Power BI Desktop でディメンション モデルから魅力的なレポートを作成する
description: このチュートリアルでは、ディメンション モデルから始めて、開始から終了まで 20 分で美しいレポートを作成します。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: tutorial
ms.date: 01/19/2021
LocalizationGroup: Reports
ms.openlocfilehash: 03eac7aefdebb31eac353c969db2bf8810173395
ms.sourcegitcommit: 77912d4f6ef2a2b1ef8ffccc50691fe5b38ee97a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2021
ms.locfileid: "98687365"
---
# <a name="tutorial-from-dimensional-model-to-stunning-report-in-power-bi-desktop"></a>チュートリアル:Power BI Desktop でディメンション モデルから魅力的なレポートを作成する 

このチュートリアルでは、ディメンション モデルから始めて、開始から終了まで 45 分で美しいレポートを作成します。

あなたは、AdventureWorks に勤務しています。上司は最新の売上高に関するレポートを見たいと考えており、 次の内容を含むエグゼクティブ サマリを要求されました。 

- 2019 年 2 月に売上が最も多かったのは何日か? 
- 会社が最も成功を収めたのは、どの国か? 
- 会社が投資を継続する必要があるのは、どの製品カテゴリとどの業種のリセラーか? 

[AdventureWorks Sales サンプル Excel ブック](https://github.com/microsoft/powerbi-desktop-samples/blob/main/AdventureWorks%20Sales%20Sample/AdventureWorks%20Sales.xlsx)を使用すると、このレポートを即座に作成できます。 最終的なレポートは次のようになります。 

:::image type="content" source="media/desktop-dimensional-model-report/adventureworks-finished-report.png" alt-text="完成した AdventureWorks レポート。":::

完成品を確認する必要がある場合は、 [完成した Power BI .pbix ファイル](https://github.com/microsoft/powerbi-desktop-samples/blob/main/AdventureWorks%20Sales%20Sample/AdventureWorks%20Sales.pbix)をダウンロードすることもできます。

それでは始めましょう。 

このチュートリアルでは、以下について説明します。

> [!div class="checklist"]
> * 変換を数回行ってデータを準備する
> * タイトル、3 つのビジュアル、スライサーを含むレポートを作成する
> * 仕事仲間と共有できるように、レポートを Power BI サービスに発行する

## <a name="prerequisites"></a>前提条件

- 開始する前に、[Power BI Desktop をダウンロードする](../fundamentals/desktop-get-the-desktop.md)必要があります。 
- レポートを Power BI サービスに発行する予定があり、まだサインアップしていない場合は、[無料試用版にサインアップ](../fundamentals/service-self-service-signup-for-power-bi.md)します。 

## <a name="get-data-download-the-sample"></a>データの取得: サンプルをダウンロードする 

1. [AdventureWorks Sales サンプル Excel ブック](https://github.com/microsoft/powerbi-desktop-samples/blob/main/AdventureWorks%20Sales%20Sample/AdventureWorks%20Sales.xlsx)をダウンロードします。 

1. Power BI Desktop を開きます。 

1. **[ホーム]** リボンの **[データ]** セクションで、 **[Excel]** を選択します。 

1. サンプルのブックを保存した場所に移動し、 **[開く]** を選択します。 

## <a name="prepare-your-data"></a>データの準備 

[ナビゲーター] ウィンドウには、データを  *[変換する]*  または  *[読み込む]*  オプションがあります。 [ナビゲーター] には、データの範囲が正しいことを確認できるように、データのプレビューが表示されます。 数値データ型は斜体で示されます。 このチュートリアルでは、データを読み込む前に変換します。

すべてのテーブルを選択し、 **[データの変換]** を選択します。 シート ( *_data* というラベルが付いたもの) を選択しないようにしてください。 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-load-tables.png" alt-text="ナビゲーターにテーブルを読み込む。":::

列のデータ型が次のテーブルのデータ型と一致することを確認します。 Power BI で自動的にデータ型を検出できるようにするには、クエリを選択してから、1 つまたは複数の列を選択します。 **[変換]** タブで、 **[データ型の検出]** を選択します。 検出されたデータ型を変更するには、 **[ホーム]** タブで **[データ型]** を選択し、テーブルから適切なデータ型を選択します。

:::image type="content" source="media/desktop-dimensional-model-report/power-query-change-data-types.png" alt-text="列のデータ型を確認する。":::


|クエリ  |列  |データ型  |
|---------|---------|---------|
|Customer  |  CustomerKey | 整数 |
|Date | DateKey |    整数     |
|     | Date | Date      |
|     | MonthKey  | 整数 |
|成果物  | ProductKey | 整数  | 
|     | Standard Cost | 10 進数  | 
|     | List Price | 10 進数  | 
|Reseller  | ResellerKey | 整数  | 
|Sales   | SalesOrderLineKey | 整数  | 
|     | ResellerKey  | 整数  | 
|     | CustomerKey | 整数  | 
|     | ProductKey  | 整数  | 
|     | OrderDateKey | 整数  | 
|     | DueDateKey  | 整数  | 
|     | ShipDateKey | 整数  | 
|     | SalesTerritoryKey | 整数  | 
|     | Order Quantity   | 整数  | 
|     | Unit Price  | 10 進数  | 
|     | Extended Amount  | 10 進数  | 
|     | Unit Price Discount Pct | パーセント  | 
|     | Product Standard Cost | 10 進数  | 
|     | Total Product Cost | 10 進数  | 
|     | Sales Amount | 10 進数  | 
| SalesTerritory  | SalesTerritoryKey | 整数  | 
|  販売注文   |  SalesOrderLineKey | 整数  | 

 **[ホーム]**  タブに戻り、 **[Close & Apply]\(閉じて適用する\)** を選択します。 

:::image type="content" source="media/desktop-dimensional-model-report/power-query-close-and-apply.png" alt-text="Power Query の [Close & Apply]\(閉じて適用する\) ボタン。":::

## <a name="model-your-data"></a>データのモデル化 

読み込んだデータは、レポートのための準備がほとんど完了しています。 データ モデルを調べて、いくつかの変更を加えましょう。 

左側にある **[モデル ビュー]** を選択します。 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-select-model-view.png" alt-text="Power BI Desktop で [モデル ビュー] を選択する。":::

データ モデルは、次の図のようになります。各テーブルはボックスで囲まれています。 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-data-model-1.png" alt-text="開始するデータ モデル。":::

### <a name="create-relationships"></a>リレーションシップの作成

このモデルは、データウェアハウスで見られる典型的な "*スター スキーマ*" です。これは、星の形に似ています。 星の中心にあるのは、ファクト テーブルです。 周囲にあるテーブルはディメンション テーブルと呼ばれ、リレーションシップにより、ファクト テーブルと関連付けられます。 ファクト テーブルには、Sales Amount (売上高) や Product Standard Cost (製品標準コスト) など、販売トランザクションに関する数値情報が含まれています。 ディメンションにより、コンテキストが提供されるため、特に次のような分析を行うことができます。 

- 販売された製品... 
- 販売先... 
- 販売したリセラー... 
- 販売区域。  

よく見ると、Date (日付) テーブルを除いて、すべてのディメンション テーブルがリレーションシップでファクトに関連付けられていることがわかります。 ここで、いくつかのリレーションシップを Date に追加してみましょう。 DateKey を Date テーブルから、Sales (販売) テーブルの OrderDateKey にドラッグします。 線の両端にある **1** とアスタリスク * (多) で示されているように、Date から Sales へいわゆる "1 対多" のリレーションシップを作成しました。  

特定の日付に 1 つ以上の販売注文があるため、リレーションシップは "1 対多" です。 各日付に販売注文が 1 つしかなければ、リレーションシップは "1 対 1" になります。 線の中央にある小さな矢印は、"クロス フィルター処理の方向" を示します。 これは、Date テーブルの値を使用して、Sales テーブルをフィルター処理できることを示しているため、このリレーションシップにより、販売注文がいつ発注されたかを分析できます。  

:::image type="content" source="media/desktop-dimensional-model-report/desktop-date-sales-relationship.png" alt-text="Sales テーブルと Date テーブル間のリレーションシップ。":::

Sales テーブルには、Due Date (期限) や Ship Date (出荷日) など、販売注文に関連する日付について詳細な情報が含まれています。 ドラッグして Date テーブルにさらに 2 つのリレーションシップを追加しましょう。 

- DateKey から DueDateKey 
- DateKey から ShipDateKey 
    
:::image type="content" source="media/desktop-dimensional-model-report/desktop-date-sales-relationships-done.png" alt-text="Sales テーブルと Date テーブル間の 3 つのリレーションシップ。":::

OrderDateKey の最初のリレーションシップは実線で示されており、アクティブであることがわかります。 他の 2 つは破線で示されており、非アクティブです。 Power BI では、既定により、アクティブなリレーションシップを使用して Sales と Date が関連付けられます。 このため、SalesAmount の合計は、Due Date や Ship Date ではなく Order Date (注文日) で計算されます。 この動作に影響を与えることができます。 このチュートリアルで後ほど説明する「[追加の手順: DAX でメジャーを作成する](#extra-credit-write-a-measure-in-dax)」を参照してください。

### <a name="hide-key-columns"></a>キー列を非表示にする

一般的なスター スキーマには、ファクトとディメンションの間のリレーションシップを保持するキーがいくつか含まれています。 通常は、レポートでキー列を使用する必要はありません。 キー列を非表示にして、[フィールド] リストに表示されるフィールドの数を削減し、データ モデルを使いやすくしましょう。 

すべてのテーブルを調べて、*Key* で終わる名前を持つ列を非表示にします。 

列の横にある **目** のアイコンを選択し、 **[Hide in report view]\(レポート ビューで非表示にする\)** を選択します。

:::image type="content" source="media/desktop-dimensional-model-report/desktop-column-visible.png" alt-text="目のアイコンがある表示列。":::

[プロパティ] ウィンドウで列の横にある **目** のアイコンを選択することもできます。

非表示フィールドの横には、次のアイコン (斜線が入った目) が表示されます。 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-column-hidden.png" alt-text="非表示の目のアイコンがあるフィールド。":::
 
次のフィールドを非表示にします。

|テーブル  |列  |
|---------|---------|
|Customer  | CustomerKey |
|Date     | DateKey |
|     | MonthKey |
|成果物     | ProductKey  |
|Reseller   | ResellerKey  |
|Sales     | CustomerKey  |
|     | DueDateKey |
|     | OrderDateKey |
|     | ProductKey |
|     | ResellerKey        |
|     | SalesOrderLineKey        |
|     | SalesTerritoryKey        |
|     | ShipDateKey        |
| 販売注文    | SalesOrderLineKey |
| SalesTerritory  | SalesTerritoryKey |

これで、データ モデルは次のデータ モデルのようになり、Sales と他のすべてのテーブル間のリレーションシップは保持されたまま、すべてのキー フィールドが非表示になります。 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-data-model-2-hidden-columns.png" alt-text="非表示のキー列があるデータ モデル。":::

### <a name="create-hierarchies"></a>階層を作成する

非表示の列のおかげでデータ モデルは使いやすくなりましたが、ここでいくつかの "*階層*" を追加すると、モデルをさらに使いやすくすることができます。 階層を使用すると、グループの移動が容易になります。 たとえば、市は都道府県にあり、都道府県は国または地域にあります。 

次の階層を作成します。 

1. 階層の最上位または最も詳細な粒度のフィールドを右クリックし、 **[階層の作成]** を選択します。 

1. **[プロパティ]** ウィンドウで、階層の **[名前]** を設定し、レベルを設定します。 

1. 次に、 **[レベルの変更を適用]** します。 

    :::image type="content" source="media/desktop-dimensional-model-report/desktop-hierarchy-properties.png" alt-text="階層の [プロパティ] ウィンドウ。":::

また、レベルを追加した後、[プロパティ] ウィンドウで階層内のレベルの名前を変更することもできます。 Date テーブル内にある Fiscal (会計) 階層の Year (年) および Quarter (四半期) レベルの名前を変更する必要があります。 

作成する必要がある階層を次に示します。

| テーブル |階層名 |Levels  |
|---------|---------|---------|
|Customer     | [地理的な場所]   | 国/地域  |
|     | | State-Province  |
|     |         | City |
|Row4     |         | 郵便番号 |
|Row5     |         | Customer   |
|Date     | Fiscal  | Year (Fiscal Year)  |
|     |         | Quarter (Fiscal Quarter) |
|     |         | Month |
|     |         | Date |
| Product  | 製品 | カテゴリ |
|     |         | サブカテゴリ |
|     |         | モデル |
|     |         | Product |
| Reseller   | [地理的な場所] | 国/地域 |
|     |         | State-Province |
|     |         | City  |
|     |         | 郵便番号  |
|     |         | Reseller |
| 販売注文  | Sales Orders | Sales Order |
|     |         | Sales Order Line |
| SalesTerritory    | Sales Territories | Group |
|     |         | Country |
|     |         | リージョン |
 
データ モデルは、次のデータ モデルのようになります。 同じテーブルが含まれますが、各ディメンション テーブルには、階層が含まれます。 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-data-model-3-added-hierarchies.png" alt-text="階層を含むディメンション テーブルがあるデータ モデル。":::

### <a name="rename-tables"></a>テーブル名を変更する

モデリングを完了には、[プロパティ] ウィンドウで次のテーブルの名前を変更しましょう。 

|古いテーブル名  |新しいテーブル名  |
|---------|---------|
|SalesTerritory    |  Sales Territory   |
|販売注文  |  Sales Order   |

Excel テーブル名にはスペースを含めることができないため、この手順が必要です。

以上で、最終的なデータ モデルの準備ができました。

:::image type="content" source="media/desktop-dimensional-model-report/desktop-data-model-4-renamed-tables.png" alt-text="テーブル名を変更して完成したデータ モデル。":::

## <a name="extra-credit-write-a-measure-in-dax"></a>追加の手順: DAX でメジャーを作成する 

DAX 数式言語による "*メジャー*" の作成は、非常に強力なデータ モデリングです。 [DAX の詳細については、Power BI のドキュメントを参照してください](/dax/)。 ここでは、既定の注文日ではなく、販売注文の期限で総売上高を計算する基本的なメジャーを作成しましょう。 このメジャーでは、[USERELATIONSHIP 関数](/dax/userelationship-function-dax)を使用して、このメジャーのコンテキストの DueDate で Sales と Date 間のリレーションシップをアクティブにします。 次に、[CALCULATE](/dax/calculate-function-dax) を使用して、そのコンテキスト内の売上高を合計します。

1. 左側にある [データ ビュー] を選択します。 

    :::image type="content" source="media/desktop-dimensional-model-report/desktop-open-data-view.png" alt-text="左側の [データ ビュー] を選択する。":::

1. [フィールド] リストで [Sales] テーブルを選択します。

    :::image type="content" source="media/desktop-dimensional-model-report/desktop-select-sales-table.png" alt-text="[フィールド] リストで [Sales] テーブルを選択する。":::

1.  **[ホーム]**  リボンで、 **[新しいメジャー]** を選択します。 

1. このメジャーを選択または入力して、既定の注文日ではなく、販売注文の期限で合計売上高を計算します。

    ```dax
    Sales Amount by Due Date = CALCULATE(SUM(Sales[Sales Amount]), USERELATIONSHIP(Sales[DueDateKey],'Date'[DateKey]))
    ```

1. チェック マークを選択してコミットします。 

    :::image type="content" source="media/desktop-dimensional-model-report/desktop-adding-a-dax-measure.png" alt-text="チェック マークを選択して、DAX メジャーをコミットする。":::

## <a name="build-your-report"></a>レポートの構築 

データをモデル化したので、次はレポートを作成します。 [レポート ビュー] に移動します。 右側にある [フィールド] ウィンドウに、作成したデータ モデルのフィールドが表示されます。

一度に 1 つずつビジュアルを作成して、最終的なレポートを完成させましょう。 

:::image type="content" source="media/desktop-dimensional-model-report/adventureworks-finished-report-with-numbers.png" alt-text="各ビジュアルを数字でマークした、完成したレポート。":::

### <a name="visual-1-add-a-title"></a>ビジュアル 1: タイトルの追加 

1. **[挿入]** リボンで、 **[テキスト ボックス]** を選択します。 「Executive Summary - Sales Report」 (エグゼクティブ サマリ - 売上高レポート) と入力します。 

1. 入力したテキストを選択します。 フォント サイズを **[20]** と **[太字]** に設定します。 

    :::image type="content" source="media/desktop-dimensional-model-report/executive-summary-text-box.png" alt-text="テキスト Executive Summary を書式設定する。":::

1. [視覚化] ウィンドウで、 **[背景]** を **[オフ]** に切り替えます。 

1. 1 行に収まるようにボックスのサイズを変更します。 

### <a name="visual-2-sales-amount-by-date"></a>ビジュアル 2: 日付別の売上高 

次に、売上高が最も多かった月と年がわかるように折れ線グラフを作成します。

1. [フィールド] ウィンドウで、 **[Sales Amount]** フィールドを **[Sales]** テーブルからレポート キャンバスの空白領域にドラッグします。 Power BI では、既定により、縦棒が 1 つ (Sales Amount) ある縦棒グラフが表示されます。 

1. **[Month] (月)** を **[Date]** テーブルの **[Fiscal] (会計)** 階層からドラッグし、縦棒グラフにドロップします。 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-year.png" alt-text="各年の縦棒がある縦棒グラフを作成する。":::

1. [視覚化] ウィンドウの **[フィールド]** セクションで、 **[Year] (年)** と **[Quarter] (四半期)** フィールドを削除します。 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-year-remove-year-and-quarter.png" alt-text="[視覚化] ウィンドウの [フィールド] セクションで、[Year] と [Quarter] フィールドを削除する。":::

1. [視覚化] ウィンドウで、視覚化の種類を **[面グラフ]** に変更します。 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-year-change-to-area.png" alt-text="縦棒グラフから面グラフに変更する。":::

1. 上記の追加の手順で DAX メジャーを追加した場合、それを **[値]** にも追加します。 
1. [形式] ウィンドウを開き、[データの色] を開いて、**Sales Amount by Due Date (期限別売上高)** の色を赤などのより対照的な色に変更します。

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-year-add-DAX-measure.png" alt-text="面グラフとしての Sales Amount by Due Date。":::

    ご覧のとおり、Sales Amount by Due Date は、Sales Amount をわずかに下回っています。 これは、DueDateKey を使用する Sales テーブルと Date テーブルの間のリレーションシップを使用していることを証明しています。 

 

### <a name="visual-3-order-quantity-by-reseller-country"></a>ビジュアル 3: リセラーの国別の注文数量 

次に、マップを作成して、リセラーの注文数量が最も多い国を表示します。

1. [フィールド] ウィンドウで、 **[Reseller] (リセラー)**  テーブルの **[Country-Region] (国/地域)** フィールドをレポート キャンバスの空白領域にドラッグします。 Power BI によってマップが作成されます。 

1. **[Order Quantity] (注文数量)** フィールドを **[Sales]** テーブルからドラッグして、マップにドロップします。 **[Country-Region]** が **[場所]** にも入力され、 **[Order Quantity]** が **[サイズ]** にも入力されていることをご確認ください。 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-order-quantity-by-reseller-country.png" alt-text="国/地域別の注文数量のマップ。":::

### <a name="visual-4-sales-amount-by-product-category-and-reseller-business-type"></a>ビジュアル 4: 製品カテゴリおよびリセラーの業種別の売上高 

次に、どの業種のリセラーによってどの製品が販売されているかを調査するための縦棒グラフを作成します。

1. 作成した 2 つのグラフをドラッグして、キャンバスの上半分に横に並べて表示します。 キャンバスの左側に少しスペースを取っておきます。 

1. レポート キャンバスの下半分の空白領域を選択します。 

1. [フィールド] ウィンドウで、 **[Sales]** から **[Sales Amount]** 、 **[Product] (製品)** から **[Product Category] (製品カテゴリ)** 、 **[Reseller]** から **[Business Type] (業種)** をそれぞれ選択します。
    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-product-category-field-well.png" alt-text="[Category] と [Business Type] が [行] にあり、[Sales Amount] が [値] として選択されていることを確認します。":::
    
    Power BI によって、集合縦棒グラフが自動的に作成されます。 視覚化を **[マトリックス]** に変更します。 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-product-category-change-to-matrix.png" alt-text="集合縦棒グラフをマトリックスに変更する。":::

1. マトリックスを選択したまま、[フィルター] ウィンドウの **[業種]** で **[すべて選択]** をオンにして、 **[[該当なし]]** ボックスをオフにします。 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-product-category-filter-not-applicable.png" alt-text="業種 [該当なし] を除外する。":::

1. 上の 2 つのグラフの下にあるスペースを埋めるのに十分な幅になるように、マトリックスをドラッグします。 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-product-category-increase-width.png" alt-text="マトリックスの幅を広げてレポートを埋める。":::

1. マトリックスの [書式設定] ウィンドウで、 **[条件付き書式]** セクションを開き、 **[データ バー]** をオンにします。 **[詳細コントロール]** を選択し、正のバーに明るい色を設定します。 **[OK]** を選択します。 

1. マトリックスをドラッグして Sales Amount 列の幅を広げ、領域全体を覆うようにします。

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-product-category-add-databars.png" alt-text="Sales Amount のデータ バーがあるマトリックス。":::

全体的に Bikes (自転車) の売上高が多く、Value Added Resellers (付加価値リセラー) が最も多く売り上げており、僅差で Warehouses (量販店) が続いていることが示されています。 Components (部品) の売上高については、Warehouses の方が Value Added Resellers よりも多くなっています。 

 

### <a name="visual-5-fiscal-calendar-slicer"></a>ビジュアル 5: 会計カレンダー スライサー 

スライサーは、レポート ページのビジュアルを特定の選択範囲にフィルター処理するための重要なツールです。 この場合、各月、四半期、年の業績を絞り込むためのスライサーを作成できます。 

1. [フィールド] ウィンドウで、 **[Date]** テーブルから **[Fiscal]** 階層を選択し、キャンバスの左側にある空白領域にドラッグします。 

1. [視覚化] ウィンドウで、 **[スライサー]** を選択します。 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-add-fiscal-calendar-slicer.png" alt-text="レポートの販売カレンダー スライサーを追加する。":::

1. [視覚化] ウィンドウの [フィールド] セクションで、 **[Quarter]** と **[Date]** フィールドを削除して、 **[Year]** と **[Month]** のみを残します。 
 
    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-add-fiscal-calendar-slicer-remove-quarter-and-date.png" alt-text="会計スライサーから Quarter と Date を削除する。":::

以上で、上司が特定の月のデータのみを表示するように要求した場合、スライサーを使用して、年を切り替えたり、各年の特定の月に切り替えたりすることができます。 

## <a name="extra-credit-format-the-report"></a>追加の手順: レポートを書式設定する 

このレポートに対して何らかの淡色の書式設定を行って洗練さを高める必要がある場合、以下に簡単な手順をいくつか示します。 

### <a name="theme"></a>テーマ 

-  **[表示]**  リボンで、 **[テーマ]** を選択し、テーマを  **[エグゼクティブ]** に変更します。 

    :::image type="content" source="media/desktop-dimensional-model-report/formatting-report-change-theme.png" alt-text="[エグゼクティブ] テーマを選択する。":::

### <a name="spruce-up-the-visuals"></a>ビジュアルを整理する 

[視覚化] ウィンドウの  **[書式]**  タブで、次の変更を加えます。 

:::image type="content" source="media/desktop-dimensional-model-report/formatting-report-formatting-pane.png" alt-text="[視覚化] ウィンドウの [書式] タブのスクリーンショット。":::

**ビジュアル 2、日付別の売上高**

1. [ビジュアル 2、日付別の売上高] を選択します。 
1.  **[タイトル]**   セクションで、DAX メジャーを追加しなかった場合は、 **[タイトルのテキスト]** を "Sales Amount by Order Date" (注文日別の売上高) に変更します。 

    DAX メジャーを追加した場合は、 **[タイトルのテキスト]** を "Sales Amount by Order Date / Due Date" (注文日/期限別の売上高) に変更します。 

1. **[テキスト サイズ]** を  **[16 pt]** に設定します。 
1.  **[影]**   を  **[オン]** に切り替えます。 

**ビジュアル 3、リセラーの国別の注文数量**

1. [ビジュアル 3、リセラーの国別の注文数量] を選択します。 
1.  **[マップ スタイル]**   セクションで、 **[テーマ]**   を  **[グレースケール]** に変更します。 
1.  **[タイトル]**   セクションで、 **[タイトル テキスト]** を "Order Quantity by Reseller Country" (リセラーの国別の注文数量) に変更します。
1. **[テキスト サイズ]**  を  **[16 pt]** に設定します。 
1.  **[影]**   を  **[オン]** に切り替えます。  

**ビジュアル 4、製品カテゴリおよびリセラーの業種別の売上高**

1. [ビジュアル 4、製品カテゴリおよびリセラーの業種別の売上高] を選択します。 
1.  **[タイトル]**  セクションで、 **[タイトル テキスト]** を "Sales Amount by Product Category and Reseller Business Type" (製品カテゴリおよびリセラーの業種別の売上高) に変更します。
1. **[テキスト サイズ]**  を  **[16 pt]** に設定します。 
1.  **[影]**   を  **[オン]** に切り替えます。 

**ビジュアル 5、会計カレンダー スライサー**

1. [ビジュアル 5、会計カレンダー スライサー] を選択します。
1.  **[選択範囲のコントロール]**  セクションで、 **[[すべて選択] オプションを表示する]** を  **[オン]** に切り替えます。 
1.  **[スライサー ヘッダー]**  セクションで、 **[テキスト サイズ]**  を  **[16 pt]** に設定します。 

### <a name="add-a-background-shape-for-the-title"></a>タイトルの背景図形を追加する 

1.  **[挿入]** リボンで、 **[図形]**  > **[四角形]** の順に選択します。 
1. それをページの一番上に配置し、ページの幅とタイトルの高さに合わせて引き伸ばします。 
1.  **[図形の書式設定]**  ウィンドウの  **[線]**  セクションで、 **[透明度]**  を  **[100%]** に変更します。 
1.  **[塗りつぶし]**  セクションで、 **[塗りつぶしの色]**  を  **[テーマの色 5 #6B91C9 (青)]** に変更します。 
1.  **[書式設定]**  タブで、 ** [背面へ移動]**  > **[Send to back]\(最背面へ移動\)** の順に選択します。 
1. ビジュアル 1 のテキスト、タイトルを選択し、 **[フォントの色]** を  **[白]** に変更します。 

## <a name="finished-report"></a>完成したレポート 

スライサーで **[FY2019]** を選択します。

:::image type="content" source="media/desktop-dimensional-model-report/adventureworks-finished-report.png" alt-text="完成した最終的なレポート。":::

手短に言えば、このレポートは、上司が最も関心のある質問に答えることができます。 

- 2019 年 2 月に売上が最も多かったのは何日か? 
    2 月 25 日、売上高 253,915.47 ドル。 

- 会社が最も成功を収めたのは、どの国か? 
    米国、注文数量 132,748。 

- 会社が投資を継続する必要があるのは、どの製品カテゴリとどの業種のリセラーか? 
    同社は引き続きカテゴリ Bike と業種 Value Added Reseller および Warehouse に投資する必要があります。 

## <a name="save-your-report"></a>レポートの保存 

-  **[ファイル]**  メニューで、 **[保存]** を選択します。 


## <a name="publish-to-the-power-bi-service-to-share"></a>Power BI サービスに発行して共有する 

レポートを上司や仕事仲間と共有するには、Power BI サービスに発行します。 Power BI アカウントを持っている仕事仲間と共有する場合、仕事仲間はレポートを操作できますが、変更を保存することはできません。

1. Power BI Desktop の  **[ホーム]**  リボンで、 **[発行]** を選択します。 
1. Power BI サービスにサインインする必要がある場合があります。 まだアカウントをお持ちではない場合は、 [無料試用版にサインアップ](https://app.powerbi.com/signupredirect?pbi_source=web)してください。 

1. [Power BI サービス] >  **[選択]** で、[個人用ワークスペース] などの宛先を選択します。 

1.  **[Power BI で 'ファイル名' を開く]** を選択します。 完成したレポートがブラウザーに表示されます。 

1. レポートの上部にある  **[共有]**   を選択して、レポートを他のユーザーと共有します。

## <a name="next-steps"></a>次の手順 

- [完成した Power BI .pbix ファイル](https://github.com/microsoft/powerbi-desktop-samples/blob/main/AdventureWorks%20Sales%20Sample/AdventureWorks%20Sales.pbix)をダウンロードする
- Power BI Desktop での DAX とデータ モデリングの詳細については、[こちら](/learn/modules/dax-power-bi-models/)を参照してください

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。
