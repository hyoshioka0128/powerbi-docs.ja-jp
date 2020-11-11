---
title: Power BI のページ分割されたレポートのサンプル
description: この記事では、Power BI のページ分割されたレポートのサンプルをダウンロードして使用する方法について説明します。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: swgupt
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 11/01/2020
ms.openlocfilehash: cf0e6a6e7cd40a5b8bb97560caf94b71c1b48e7a
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2020
ms.locfileid: "93324053"
---
# <a name="sample-power-bi-paginated-reports"></a>Power BI のページ分割されたレポートのサンプル


[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)]

この記事では、Power BI のページ分割されたレポートのサンプルをダウンロードして調べるための情報とリンクを提供します。 ページ分割されたレポートを使用する一般的な方法がわかります。

## <a name="prerequisites"></a>前提条件

- これらのレポートは、編集することなく、そのままオンラインで共有できます。 そのためには、Power BI Pro ライセンスが必要です。 [Power BI Pro の無料試用版ライセンス](../fundamentals/service-self-service-signup-for-power-bi.md#sign-up-for-an-individual-trial-of-power-bi-pro)にサインアップしてください。
- また、[Premium 容量](../admin/service-premium-what-is.md)の Power BI ワークスペースにアクセスする必要もあります。
- これらのレポートを編集するには、Microsoft ダウンロード センターから [Power BI Report Builder をインストールする](https://aka.ms/pbireportbuilder)必要があります。
- これで、GitHub から[これらのページ分割されたレポートのサンプルをダウンロードする](https://github.com/microsoft/Reporting-Services/tree/master/PaginatedReportSamples)準備ができました。 GitHub アカウントは必要ありません。 


## <a name="invoice"></a>請求書

:::image type="content" source="media/paginated-reports-samples/paginated-report-invoice.png" alt-text="Power BI のページ分割されたレポートの請求書サンプルのスクリーンショット。":::


このページ分割されたレポートは、自己完結型の請求書です。 このレポートのシナリオは、ピクセル パーフェクトで印刷可能な請求書が必要である、というものです。 項目の説明、数量、割引、コストなどの詳細情報を含む、合計売上を表示する必要があります。

このサンプルを見ると、次のような実際の請求書の作成に固有の特性がよくわかります。  

- Tablix (テーブルとマトリックスの両方の基になるデータ領域)。 動的に生成されるユーザー固有の内容とテーマが表示されます。
- レポート本体の Tablix の各行に配置された四角形のデータ領域。
- テキスト ボックスや線などのレポート アイテム。
- 内容を動的に選択するレポート パラメーター。 表示される内容は、式のプレースホルダーを使用して、特定の主題に適用されます。 

データ ソース:.rdl ファイルに含まれます

## <a name="labels"></a>ラベル

:::image type="content" source="media/paginated-reports-samples/paginated-report-labels.png" alt-text="ページ分割されたレポートのラベルのスクリーンショット。":::

これは、自己完結型のページ分割されたレポートのサンプルです。 宛名ラベル テンプレートの印刷レイアウトに合わせて完全にサイズ設定された複数列のレポートです。 

ラベル レポートは単純ですが、ページ分割されたラベルを作成するための、いくつかの固有の特性があります。

- 列の間隔が定義された、列数が 3 で固定の Tablix。
- 印刷されるページの行と列にわたって繰り返される四角形のデータ領域。
- 四角形の各データ領域に表示される内容を選択するためのレポート パラメーター。

データ ソース:.rdl に含まれます

## <a name="mailing-letter"></a>郵送レター

:::image type="content" source="media/paginated-reports-samples/paginated-report-letter.png" alt-text="Power BI のページ分割されたレポートのレター サンプルのスクリーンショット。":::

この自己完結型のページ分割されたレポート サンプルは、実際の郵送レターを作成するために設計されています。 このレポートのシナリオは、動的な内容のピクセル パーフェクトで印刷可能なレターが必要である、というものです。

このサンプルには、次のような固有の特性があります。 

- 四角形のデータ領域は、レポート本体の異なるセクションに配置されます。 
- レターをカスタマイズする画像。 
- Tablix データ領域 (テーブルとマトリックスの両方の基になるデータ領域)。 Tablix には、動的に生成されるユーザー固有の内容が表示されます。
- テキスト ボックスや線などのレポート アイテム。
- 内容を動的に選択するレポート パラメーター。 表示される内容は、式のプレースホルダーを使用して、特定の主題に適用されます。 

データ ソース:.rdl に含まれます

## <a name="transcript"></a>トランスクリプト

:::image type="content" source="media/paginated-reports-samples/paginated-report-transcript.png" alt-text="Power BI のページ分割されたレポートのトランスクリプト サンプルのスクリーンショット。":::

このレポートのシナリオは、ピクセル パーフェクトで印刷可能なトランスクリプトが必要である、というものです。 各学生のプログラムの説明の詳細と日付を一覧表示する動的な内容が含まれている必要があります。

この自己完結型のページ分割されたレポート サンプルには、次のような固有の特性があります。 

- Tablix データ領域 (テーブルとマトリックスの両方の基になるデータ領域)。 Tablix には、入れ子になった行グループを使用して動的に生成されるユーザー固有の内容が表示されます。
- 四角形のデータ領域は、レポート本体の異なるセクションに配置されます。
- テキスト ボックスや線などのレポート アイテム。

データ ソース:.rdl に含まれます

## <a name="sales-performance"></a>売上実績

:::image type="content" source="media/paginated-reports-samples/paginated-report-sales-performance.png" alt-text="Power BI のページ分割されたレポートの売上実績サンプルのスクリーンショット。":::

国の売上実績は、自己完結型のページ分割されたレポートのサンプルです。 このレポートのシナリオは、合計売上と詳細を表示するためのピクセル パーフェクトで印刷可能な請求書が必要である、というものです。 次の特徴が示されています。

- テーブルで詳細を展開するためのパラメーターの使用。
- ヘッダーとフッター。
- 式のプレースホルダーを使用した、テキスト ボックス、線、四角形などのレポート アイテム。
- データ バー。
- 傾向線。
- ゲージ パネル。

データ ソース:.rdl に含まれます
  
## <a name="next-steps"></a>次のステップ

[ページ分割されたレポートを Power BI サービスで表示する](../consumer/paginated-reports-view-power-bi-service.md)

その他の質問 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。