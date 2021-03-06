---
title: Power BI データセット プロパティ
description: Power BI データセット API のプロパティについて説明します
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 7dad7071fbf887c36443cacdb9be83d83e0b89be
ms.sourcegitcommit: a72567f26c1653c25f7730fab6210cd011343707
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "83561503"
---
# <a name="dataset-properties"></a>データセットのプロパティ

データセット API の現行のバージョン 1 では、名前とテーブルのコレクションを使用したデータセットの作成にのみ対応しています。 各テーブルには名前を付け、列のコレクションを含めることができます。 各列には、名前とデータ型があります。 特にメジャーおよびテーブル間のリレーションシップをサポートすることで、これらのプロパティを大幅に拡張します。 このリリースでサポートするプロパティの完全な一覧を次に示します。

> [!IMPORTANT]
> [データセット操作グループ](https://docs.microsoft.com/rest/api/power-bi/datasets)に関するページからアクセスできます。

## <a name="dataset"></a>データセット

Name (名前)  |種類  |Description  |読み取り専用  |必須
---------|---------|---------|---------|---------
ID     |  Guid       | システム全体で一意である、データセットの識別子です。        | True        | False        
名前     | String        | データセットのユーザー定義名です。        | False        | True        
tables     | テーブル[]        | テーブルのコレクションです。        |  False       | False        
relationships     | リレーションシップ[]        | テーブル間のリレーションシップのコレクションです。        | False        |  False  
defaultMode     | String        | "Push" と "Streaming" の値で、データセットがプッシュされるか、ストリーミングされるか、またはその両方かを決定します。         | False        |  False

## <a name="table"></a>Table

Name (名前)  |種類  |Description  |読み取り専用  |必須
---------|---------|---------|---------|---------
名前     | String        |  テーブルのユーザー定義名前です。 これは、テーブルの識別子としても使用されます。       | False        |  True       
列     |  列[]       |  列のコレクション。       | False        |  True       
メジャー     | メジャー[]        |  メジャーのコレクション。       | False        |  False       
isHidden     | Boolean        | true の場合、クライアント ツールにテーブルは表示されません。        | False        | False        

## <a name="column"></a>列

Name (名前)  |種類  |Description  |読み取り専用  |必須
---------|---------|---------|---------|---------
名前     |  String        | 列のユーザー定義名です。        |  False       | True       
dataType     |  String       |  サポートされている [EDM データ型](/dotnet/framework/data/adonet/entity-data-model-primitive-data-types) と制限事項です。 [データ型の制限事項](#data-type-restrictions) を参照してください。      |  False       | True        
formatString     | String        | 値が表示されるときの値の書式設定を示す文字列です。 文字列の書式設定の詳細については、[「FORMAT_STRING Contents」](/analysis-services/multidimensional-models/mdx/mdx-cell-properties-format-string-contents) (FORMAT_STRING の内容) を参照してください。      | False        | False        
sortByColumn    | String        |   同一テーブル内の列の文字列名であり、現在の列を並べ替えるために使用されます。     | False        | False       
dataCategory     | String        |  この列のデータを説明するデータのカテゴリで使用される文字列です。 一般的に使用される値: Address、City、Continent、Country、Image、ImageUrl、Latitude、Longitude、Organization、Place、PostalCode、StateOrProvince、WebUrl       |  False       | False        
isHidden    |  Boolean       |  列がビューで非表示になっているかどうかを示すプロパティです。 既定値は false です。       | False        | False        
summarizeBy     | String        |  列の既定の集計方法です。 含まれる値: default、none、sum、min、max、count、average、distinctCount     |  False       | False

## <a name="measure"></a>メジャー

Name (名前)  |種類  |Description  |読み取り専用  |必須
---------|---------|---------|---------|---------
名前     | String        |  メジャーのユーザー定義名です。       |  False       | True        
expression     | String        | 有効な DAX 式です。        | False        |  True       
formatString     | String        |  値が表示されるときの値の書式設定を示す文字列です。 文字列の書式設定の詳細については、[「FORMAT_STRING Contents」](/analysis-services/multidimensional-models/mdx/mdx-cell-properties-format-string-contents) (FORMAT_STRING の内容) を参照してください。       | False        | False        
isHidden     | String        |  true の場合、クライアント ツールにテーブルは表示されません。       |  False       | False       

## <a name="relationship"></a>リレーションシップ

Name (名前)  |種類  |Description  |読み取り専用  |必須 
---------|---------|---------|---------|---------
名前     | String        | リレーションシップのユーザー定義名です。 リレーションシップの識別子としても使用されます。        | False       | True        
crossFilteringBehavior     | String        |    リレーションシップのフィルターの方向: OneDirection (既定値)、BothDirections、Automatic       | False        | False        
fromTable     | String        | 外部キー テーブルの名前です。        | False        | True         
fromColumn    | String        | 外部キー列の名前です。        | False        | True         
toTable    | String        | 主キー テーブルの名前です。        | False        | True         
toColumn     | String        | 主キー列の名前です。        | False        | True        

## <a name="data-type-restrictions"></a>データ型の制限事項

これらの制限事項は dataType プロパティに適用されます。

データ型  |制限事項  
---------|---------
Int64     |   Int64.MaxValue と Int64.MinValue が許可されまていせん。      
Double     |  Double.MaxValue と Double.MinValue 値が許可されていません。 NaN はサポートされていません。一部の関数では正の無限大と負の無限大がサポートされていません (例: Min、Max)。       
Boolean     |   True または False。
DateTime    |   データの読み込み中に、日時分数の値を 1/300 秒 (3.33ms) の整数倍に量子化します。      
String     |  現在のところ、文字列値あたり、最大 4,000 文字が許可されます。
小数|精度=28、スケール=4

## <a name="example"></a>例
次のコード サンプルには、上記のプロパティが複数含まれています。

```json
{

  "name": "PushAdvanced",

  "tables": [

    {

      "name": "Date",

      "columns": [

        {

          "name": "Date",

          "dataType": "dateTime",

          "formatString": "dddd\\, mmmm d\\, yyyy",

          "summarizeBy": "none"

        }

      ]

    },

    {

      "name": "sales",

      "columns": [

        {

          "name": "Date",

          "dataType": "dateTime",

          "formatString": "dddd\\, mmmm d\\, yyyy",

          "summarizeBy": "none"

        },

        {

          "name": "Sales",

          "dataType": "int64",

          "formatString": "0",

          "summarizeBy": "sum"

        }

      ],

      "measures": [

        {

          "name": "percent to forecast",

          "expression": "SUM(sales[Sales])/SUM(forecast[forecast])",

          "formatString": "0.00 %;-0.00 %;0.00 %"

        }

      ]

    },

    {

      "name": "forecast",

      "columns": [

        {

          "name": "date",

          "dataType": "dateTime",

          "formatString": "m/d/yyyy",

          "summarizeBy": "none"

        },

        {

          "name": "forecast",

          "dataType": "int64",

          "formatString": "0",

          "summarizeBy": "sum"

        }

      ]

    }

  ],

  "relationships": [

    {

      "name": "2ea345ce-b147-436e-8ac2-9d3c4d82af8d",

      "fromTable": "sales",

      "fromColumn": "Date",

      "toTable": "Date",

      "toColumn": "Date",

      "crossFilteringBehavior": "bothDirections"

    },

    {

      "name": "5d95f419-e589-4345-9581-6e70670b1bba",

      "fromTable": "forecast",

      "fromColumn": "date",

      "toTable": "Date",

      "toColumn": "Date",

      "crossFilteringBehavior": "bothDirections"

    }

  ]

}
```