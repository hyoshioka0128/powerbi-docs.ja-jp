---
title: URL のクエリ文字列パラメーターを使用してレポートをフィルター処理する
description: URL クエリ文字列パラメーターを使って、レポートをフィルター処理します。複数のフィールドでもフィルター処理できます。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/30/2020
LocalizationGroup: Reports
ms.openlocfilehash: e2840d2695b70867b73c873aea7a06acf26bcc3e
ms.sourcegitcommit: 53c2b5ea4ee1fe2659804d5ccc8e4bb445a8bcad
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2020
ms.locfileid: "76913566"
---
# <a name="filter-a-report-using-query-string-parameters-in-the-url"></a>URL のクエリ文字列パラメーターを使用してレポートをフィルター処理する

Power BI サービスでレポートを開くと、レポートの各ページに一意の URL があります。 そのレポート ページをフィルター処理するには、レポート キャンバスの [フィルター] ウィンドウを使うことができます。  または、クエリ文字列パラメーターを URL に追加して、レポートを事前にフィルター処理できます。 同僚に見せるレポートに事前にフィルターを適用したい場合、 これをフィルター処理する方法の 1 つは、レポートの既定の URL にフィルター パラメーターを追加し、新しい URL 全体をメールで同僚に送ることです。

![サービスでの Power BI のレポート](media/service-url-filters/power-bi-report2.png)

## <a name="uses-for-query-string-parameters"></a>クエリ文字列パラメーターの用途

Power BI Desktop で作業しているとします。 他の Power BI レポートへのリンクを含むレポートを作成しますが、他のレポートの情報の一部のみを表示する必要があります。 最初に、クエリ文字列パラメーターを使用してレポートをフィルター処理し、URL を保存します。 次に、Desktop でこれらの新しいレポート URL を使用してテーブルを作成します。  その後、レポートを発行して共有します。

また、クエリ文字列パラメーターは、高度な Power BI ソリューションを作成するユーザーが使用することもできます。  DAX を使用して、現在のレポートでの顧客の選択に基づいて、フィルター処理されたレポート URL を動的に生成するレポートを作成します。 顧客が URL を選択すると、目的の情報のみが表示されます。 

## <a name="query-string-parameter-syntax-for-filtering"></a>フィルター処理のためのクエリ文字列パラメーターの構文

パラメーターを使用すれば、値にスペースや特殊文字が含まれている場合でも、レポートで 1 つ以上の値をフィルター処理することができます。 基本構文はとても簡単です。レポート URL に疑問符を追加し、その後にフィルター構文を追加します。

*<URL>* ?filter= *<テーブル>* / *<フィールド>* eq ' *<値>* '

![フィルターを含む URL](media/service-url-filters/power-bi-filter-urls7b.png)

* **テーブル**と**フィールド**の名前では大文字と小文字が区別されますが、**値**では区別されません。
* レポート ビューに表示されないフィールドをフィルター処理することもできます。

### <a name="reports-in-apps"></a>アプリ内のレポート

アプリ内のレポートに URL フィルターを追加する場合は、書式設定が少し異なります。 アプリ内のレポートへのリンクには、URL に追加されるクエリ パラメーター (ctid) が含まれます。 クエリ パラメーターはアンパサンド (&) で区切ります。 “?filter=” を保持し、ctid パラメーターを URL の末尾に移動し、その前にアンパサンド (&) を指定します。 

次の例のようにします。

app.powerbi.com/groups/me/apps/*app-id*/reports/*report-id*/ReportSection?filter=*Table*/*Field* eq '*value*'&ctid=*ctid*

### <a name="field-types"></a>フィールドの型

フィールドの型は、数値、日付時刻、または文字にすることができます。使用する型は、データセットに設定されている型と一致する必要があります。  たとえば、日付として設定されているデータセット列で日付時刻値や数値を検索する場合、"文字列" 型のテーブル列を指定しても動作しません (Table/StringColumn eq 1 など)。

* **文字列**は単一引用符で囲む必要があります (例: 'manager name')。
* **数値**には特別な書式設定は必要ありません。 詳細については、この記事の「[数値データ型](#numeric-data-types)」を参照してください。
* **日付と時刻**については、この記事の「[日付データ型](#date-data-types)」を参照してください。 

以下では構文についてさらに詳しく説明します。  

## <a name="filter-on-a-field"></a>フィールドをフィルター処理する

次のようなレポートの URL があるものとします。

![URL の開始](media/service-url-filters/power-bi-filter-urls6.png)

そして、ノースカロライナ州の店舗に関するマップの視覚化 (上図) を表示します。

>[!NOTE]
>この例は、[Retail Analysis サンプル](sample-datasets.md)が基になっています。
> 

"NC" (ノースカロライナ) の店舗のデータだけが表示されるようにレポートをフィルター処理するには、URL に以下を追加します。

?filter=Store/Territory eq 'NC'

![フィルターを含む URL](media/service-url-filters/power-bi-filter-urls7.png)

>[!NOTE]
>*NC* は、**Store** テーブルの **Territory** フィールドに格納されている値です。
> 

レポートはノースカロライナでフィルター処理されます。レポート ページのすべての視覚化には、ノースカロライナのデータだけが表示されます。

![ノースカロライナでフィルター処理されたレポート](media/service-url-filters/power-bi-report4.png)

## <a name="filter-on-more-than-one-value-in-a-field"></a>1 つのフィールド内の複数の値をフィルター処理する

1 つのフィールド内の複数の値をフィルター処理するには、**and** 演算子ではなく **in** 演算子を使用します。 の構文は次のとおりです。

*<URL>* ?filter= *<テーブル>* / *<フィールド>* **in** (' *<値 1>* ', ' *<値 2>* ')

同じ例を使用して、"NC" (ノースカロライナ) または "TN" (テネシー) の店舗のデータのみを表示するようにレポートをフィルター処理するには、URL に以下を追加します。

?filter=Store/Territory in ('NC', 'TN')

その他の便利な演算子の一覧については、この記事で後述する「[演算子](#operators)」の表を参照してください。

## <a name="filter-on-multiple-fields"></a>複数のフィールドでフィルター処理する

URL にパラメーターを追加し、複数のフィールドでフィルター処理することもできます。 元のフィルター パラメーターに戻りましょう。

```
?filter=Store/Territory eq 'NC'
```

追加フィールドでフィルター処理するには、上記と同じ形式で '**and**' と別のフィールドを追加します。 次に例を示します。

```
?filter=Store/Territory eq 'NC' and Store/Chain eq 'Fashions Direct'
```

## <a name="operators"></a>演算子

Power BI では、'**and**' に加え、多くの演算子がサポートされています。 次の表に、その演算子とサポートされるコンテンツの種類を一覧表示します。

|演算子  | 定義 | 文字列  | 数値 | Date |  例|
|---------|---------|---------|---------|---------|---------|
|**and**     | と |  はい      | はい |  はい|  product/price le 200 and price gt 3.5 |
|**eq**     | 次の値に等しい |  はい      | はい   |  はい       | Address/City eq 'Redmond' |
|**ne**     | 等しくない |   はい      | はい  | はい        |  Address/City ne 'London' |
|**ge**     |  以上       | いいえ | はい |はい |  product/price ge 10
|**gt**     | より大きい        |いいえ | はい | はい  | product/price gt 20
|**le**     |   以下      | いいえ | はい | はい  | product/price le 100
|**lt**     |  次の値未満       | いいえ | はい | はい |  product/price lt 20
|**in\*\***     |  含む       | はい | はい |  はい | Student/Age in (27, 29)


\*\***in** を使用する場合、**in** の右側の値をかっこで囲んだコンマ区切りのリストにすることができます。または、コレクションを返す単一の式にすることもできます。

### <a name="numeric-data-types"></a>数値データ型

Power BI の URL フィルターには、次の形式で数値を含めることができます。

|数値型  |例  |
|---------|---------|
|**integer**     |   5      |
|**long**     |   5 L または 5 l      |
|**double**     |   5.5、55e-1、0.55e+1、5D、5d、0.5e1D、0.5e1d、5.5D、5.5d、55e-1D、55e-1d     |
|**decimal**     |   5 M、5 m、5.5 M、または 5.5 m      |
|**float**     | 5 F、5 f、0.5e1 F、または 0.5e-1 d        |

### <a name="date-data-types"></a>日付データ型

Power BI では、**Date** および **DateTimeOffset** データ型で OData V3 と V4 の両方がサポートされます。 OData V3 の場合、日付は単一引用符で囲み、その前には datetime という単語を付ける必要があります。 OData V4 では、単一引用符と datetime という単語を使用する必要ありません。 
  
日付は EDM 形式を使用して表されます (2019-02-12T00:00:00)。日付を 'YYYY-MM-DD' と指定した場合、Power BI ではそれが 'YYYY-MM-DDT00:00:00' と解釈されます。 月と日は必ず 2 桁 (MM および DD) とする必要があります。

この区別が重要なのはなぜでしょうか? たとえば、**Table/Date gt '2018-08-03'** というクエリ文字列パラメーターを作成するとします。  結果には 2018 年 8 月 3 日が含まれるのでしょうか。または、2018 年 8 月 4 日 で始まるのでしょうか。 ご利用のクエリは、Power BI によって、**Table/Date gt '2018-08-03T00:00:00'** に変換されます。 したがって、結果にはゼロ以外の時刻部分を持つ日付が含まれます。これらの日付は **'2018-08-03T00:00:00'** よりも大きいためです。

V3 と V4 には他にも違いがあります。 OData V3 では、Dates はサポートされていません。サポートされているのは DateTime のみです。 そのため、V3 形式を使用する場合は、それを完全な日時で修飾する必要があります。 "datetime'2019-05-20'" のような日付リテラルは、V3 表記ではサポートされていません。 しかし、V4 表記では "2019-05-20" のみの記述するだけで済みます。 V3 と V4 の 2 つの同等のフィルター クエリを次に示します。

- OData V4 形式: filter=Table/Date gt 2019-05-20
- OData V3 形式: filter=Table/Date gt datetime'2019-05-20T00:00:00'


## <a name="special-characters-in-url-filters"></a>URL フィルター内の特殊文字

特殊文字とスペースにはいくつか追加の書式設定が必要です。 クエリにスペース、ダッシュ、またはその他の非 ASCII 文字を含める場合は、それらの特殊文字の前に、アンダースコアと X ( **_x**) で始まる "*エスケープ コード*" を付け、その後に 4 桁の **Unicode** を続け、さらにもう 1 つのアンダースコアを付加します。 Unicode が 4 文字未満の場合は、それをゼロで埋める必要があります。 次に例をいくつか示します。

|識別子  |Unicode  | Power BI 用のコーディング  |
|---------|---------|---------|
|**テーブル名**     | スペースは 0x20        |  Table_x0020_Name       |
|**列**@**数値**     |   @ は 0x40     |  Column_x0040_Number       |
|**[列]**     |  [ is 0x005B ] は 0x005D       |  _x005B_Column_x005D_       |
|**列+プラス**     | + は 0x2B        |  Column_x002B_Plus       |

Table_x0020_Name/Column_x002B_Plus eq 3 ![ 特殊文字をレンダリングするテーブルのビジュアル](media/service-url-filters/power-bi-special-characters1.png)


Table_x0020_Special/_x005B_Column_x0020_Brackets_x005D_ eq '[C]' ![特殊文字をレンダリングするテーブルのビジュアル](media/service-url-filters/power-bi-special-characters2.png)

## <a name="use-dax-to-filter-on-multiple-values"></a>DAX を使用して複数の値をフィルター処理する

複数のフィールドにフィルターを適用するもう 1 つの方法は、2 つのフィールドを 1 つの値に連結する計算列を作成することです。 その後は、その値に対してフィルターを適用できます。

たとえば、[Territory] および [Chain] という 2 つのフィールドがあるとします。 Power BI Desktop で、TerritoryChain という名前の[新しい計算列 (フィールド) を作成](desktop-tutorial-create-calculated-columns.md)します。 **フィールド**名にスペースが含まれてはならないことに注意してください。 その列に DAX 式は次のようになります。

TerritoryChain = [Territory] & " - " & [Chain]

レポートを Power BI サービスに公開した後、URL クエリ文字列を使って、NC の Lindseys 店のデータだけを表示するようにフィルター処理します。

    https://app.powerbi.com/groups/me/reports/8d6e300b-696f-498e-b611-41ae03366851/ReportSection3?filter=Store/TerritoryChain eq 'NC – Lindseys'

## <a name="pin-a-tile-from-a-filtered-report"></a>フィルター処理されたレポートのタイルをピン留めする

クエリ文字列パラメーターを使ってレポートをフィルター処理した後は、そのレポートの視覚化をダッシュボードにピン留めできます。  ダッシュボードのタイルにはフィルター処理されたデータが表示され、そのダッシュボードのタイルを選ぶと、タイルの作成に使われたレポートが表示されます。  ただし、URL を使用して実行したフィルター処理は、レポートと共に保存されません。 ダッシュボードのタイルを選択すると、フィルター処理されていない状態でレポートが開きます。  したがって、ダッシュボードのタイルに表示されるデータは、レポートの視覚化に表示されるデータと一致しません。

この不一致は、フィルター処理されたダッシュボードとフィルター処理されていないレポートで、異なる結果を見たい場合に役立ちます。

## <a name="considerations-and-troubleshooting"></a>考慮事項とトラブルシューティング

クエリ文字列パラメーターを使う場合に注意すべき点が 2 つあります。

* *in* 演算子を使用する場合は、*in* の右側の値をかっこで囲んだコンマ区切りのリストにする必要があります。    
* Power BI Report Server で、レポートの URL に含ませることによって[レポート パラメーターを渡す](https://docs.microsoft.com/sql/reporting-services/pass-a-report-parameter-within-a-url?view=sql-server-2017.md)ことができます。 レポート処理エンジンに直接渡されるため、これらの URL パラメーターにはプレフィックスが付いていません。
* クエリ文字列のフィルター処理は、[Web に公開](service-publish-to-web.md)や [PDF にエクスポート](consumer/end-user-pdf.md)では機能しません。
* 「[SharePoint Online にレポート Web パーツを埋め込む](service-embed-report-spo.md)」では、URL のフィルター処理はサポートされていません。
* JavaScript の制限により、long データ型は (2^53-1) となります。
* レポート URL フィルターには、10 個の式 (AND によって連結された 10 個のフィルター) の制限があります。

## <a name="next-steps"></a>次の手順

[視覚化をダッシュボードにピン留めする](service-dashboard-pin-tile-from-report.md)  
[無料試用版にサインアップ](https://powerbi.microsoft.com/get-started/)

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
