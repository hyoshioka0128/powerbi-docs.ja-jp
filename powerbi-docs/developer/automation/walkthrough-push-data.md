---
title: 埋め込み BI 分析情報を向上させるため、Power BI 埋め込み分析でデータセットにデータをプッシュする
description: Power BI データセットにデータをプッシュします。 Power BI 埋め込み分析を使用して、より優れた埋め込み BI インサイトを有効にします。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: tutorial
ms.date: 05/22/2019
ms.openlocfilehash: 3c5805f4d498e8e2d8a788c5703a09a8109e024b
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887433"
---
# <a name="push-data-into-a-power-bi-dataset"></a>Power BI データセットにデータをプッシュする

Power BI API を使うと、Power BI データセットにデータをプッシュできます。 この記事では、Product テーブルを含んだ Sales Marketing データセットを、既存のデータセットにプッシュする方法について説明します。

作業を開始する前に、Azure Active Directory (Azure AD) と [Power BI アカウント](../embedded/create-an-azure-active-directory-tenant.md)が必要です。

## <a name="steps-to-push-data-into-a-dataset"></a>データセットにデータをプッシュする手順

* 手順 1: [アプリを Azure AD に登録する](../embedded/register-app.md)
* 手順 2: [認証アクセス トークンを取得する](walkthrough-push-data-get-token.md)
* 手順 3:[Power BI でデータセットを作成する](walkthrough-push-data-create-dataset.md)
* 手順 4: [Power BI テーブルに行を追加するためにデータセットを取得する](walkthrough-push-data-get-datasets.md)
* 手順 5: [Power BI テーブルに行を追加する](walkthrough-push-data-add-rows.md)

次のセクションでは、データをプッシュする Power BI API 操作の概要を説明します。

## <a name="power-bi-api-operations-to-push-data"></a>データをプッシュする Power BI API の操作

Power BI REST API を使うと、Power BI にデータ ソースをプッシュできます。 アプリによりデータセットに行が追加されると、ダッシュボードのタイルは新しいデータで自動的に更新されます。 データをプッシュするには、[PostDataset](/rest/api/power-bi/pushdatasets/datasets_postdataset) および [PostRows](/rest/api/power-bi/pushdatasets/datasets_postrows) 操作を使います。 データセットを検索するには、[データセットの取得](/rest/api/power-bi/datasets/getdatasets)操作を使います。 これらの操作のいずれについても、グループ ID を渡してグループを操作することができます。 グループ ID の一覧を取得するには、[グループの取得](/rest/api/power-bi/groups/getgroups)操作を使います。

データセットにデータをプッシュするための操作を次に示します。

* [PostDataset](/rest/api/power-bi/pushdatasets/datasets_postdataset)
* [データセットの取得](/rest/api/power-bi/datasets/getdatasets)
* [行の POST](/rest/api/power-bi/pushdatasets/datasets_postrows)
* [グループの取得](/rest/api/power-bi/groups/getgroups)

Power BI でデータセットを作成するには、Power BI サービスに JavaScript Object Notation (JSON) 文字列を渡します。 JSON について詳しくは、「[JSON の紹介](https://json.org/)」をご覧ください。

データセットの JSON 文字列は、次のような形式です。

**Power BI のデータセット JSON オブジェクト**

```json
{"name": "dataset_name", "tables":
    [{"name": "", "columns":
        [{ "name": "column_name1", "dataType": "data_type"},
         { "name": "column_name2", "dataType": "data_type"},
         { ... }
        ]
      }
    ]
}
```

Sales Marketing データセットの例では、以下のような JSON 文字列を渡します。 この例では、**SalesMarketing** がデータセット名、**Product** がテーブル名です。 テーブルを定義したら、テーブル スキーマを定義します。 **SalesMarketing** データセットの場合、テーブル スキーマには、ProductID、Manufacturer、Category、Segment、Product、IsCompete の列が含まれています。

**データセット オブジェクト JSON の例**

```json
{
    "name": "SalesMarketing",
    "tables": [
        {
            "name": "Product",
            "columns": [
            {
                "name": "ProductID",
                "dataType": "int"
            },
            {
                "name": "Manufacturer",
                "dataType": "string"
            },
            {
                "name": "Category",
                "dataType": "string"
            },
            {
                "name": "Segment",
                "dataType": "string"
            },
            {
                "name": "Product",
                "dataType": "string"
            },
            {
                "name": "IsCompete",
                "dataType": "bool"
            }
            ]
        }
    ]
}
```

Power BI のテーブル スキーマでは、次のデータ型を使うことができます。

## <a name="power-bi-table-data-types"></a>Power BI テーブルのデータ型

| **データの種類** | **制限事項** |
| --- | --- |
| Int64 |Int64.MaxValue と Int64.MinValue が許可されまていせん。 |
| Double |Double.MaxValue と Double.MinValue 値が許可されていません。 NaN はサポートされていません。一部の関数では正の無限大と負の無限大がサポートされていません (例: Min、Max)。 |
| Boolean |なし |
| Datetime |データの読み込み中に、日時分数の値を 1/300 秒 (3.33 ms) の整数倍に量子化します。 |
| String |現在、最大 128 K 文字が許可されています。 |

## <a name="learn-more-about-pushing-data-into-power-bi"></a>Power BI へのデータのプッシュに関する詳細

データセットへのデータのプッシュを始める方法については、「[手順 1:ナビ ペインで Azure AD](../embedded/register-app.md) にアプリを登録します。

## <a name="next-steps"></a>次のステップ

* [Power BI にサインアップする](../embedded/create-an-azure-active-directory-tenant.md)  
* [JSON の紹介](https://json.org/)  
* [Power BI REST API の概要](overview-of-power-bi-rest-api.md)  

その他の質問 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。