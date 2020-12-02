---
title: DAX サンプル モデル
description: 参照記事をサポートするための DAX サンプル モデルです。
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 06/25/2020
ms.openlocfilehash: b2930003da1593ef5d5888c611af6700e00d3d07
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96394062"
---
# <a name="dax-sample-model"></a>DAX サンプル モデル

**Adventure Works DW 2020** Power BI Desktop サンプル モデルは、お客様の DAX の学習をサポートするために設計されています。 このモデルは、AdventureWorksDW2017 の [Adventure Works データ ウェアハウス サンプル](/sql/samples/adventureworks-install-configure#data-warehouse-downloads)に基づいています。ただし、データはサンプル モデルの目的に合わせて変更されています。

## <a name="scenario"></a>シナリオ

:::image type="content" source="media/dax-sample-model/adventure-works-logo-150x150.png" alt-text="Adventure Works の会社のロゴの画像が表示されます。":::

Adventure Works 社は、自転車やアクセサリをグローバル市場に販売する自転車の製造業者を表しています。 この会社は、自社のデータ ウェアハウスのデータを Azure SQL Database に格納しています。

## <a name="model-structure"></a>モデル構造

そのモデルには、7 つのテーブルがあります。

|テーブル|Description|
|-----|-------|
|**Customer**|顧客とその地理的な場所を説明します。 顧客はオンライン (インターネット販売) で製品を購入します。|
|**Date**|**Date** テーブルと **Sales** テーブルの間には、注文日、出荷日、および期限の 3 つのリレーションシップがあります。 注文日のリレーションシップはアクティブです。 この会社では、毎年 7 月 1 日に始まる会計年度を使用して売上を報告しています。 このテーブルは、**Date** 列を使用して、日付テーブルとしてマークされています。|
|**Product**|完成した製品のみを格納します。|
|**Reseller**|リセラーとその地理的な場所を説明します。 リセラーは顧客に製品を販売します。|
|**Sales**|販売注文明細行の単位で行を格納します。 金額の値はすべて米国ドル (USD) です。 最も古い注文日は 2017 年 7 月 1 日、最新の注文日は 2020 年 6 月 15 日です。|
|**Sales Order**|販売注文と注文明細行番号、および販売チャネルについて説明します。これは **Reseller**、**Internet** のいずれかです。 このテーブルには、**Sales** テーブルとの一対一のリレーションシップがあります。|
|**Sales Territory**|販売区域は、グループ (北米、ヨーロッパ、太平洋)、国、地域に分類されます。 米国のみが、地域レベルで製品を販売しています。|

このモデルには DAX 計算は含まれていません。

## <a name="download-sample"></a>サンプルのダウンロード

Power BI Desktop サンプル モデルのファイルは、[こちら](https://aka.ms/dax-docs-sample-file)でダウンロードできます。

## <a name="next-steps"></a>次の手順

この記事に関する詳細については、次のリソースを参照してください。

- [Data Analysis Expressions (DAX) リファレンス](/dax/)
- ラーニング パス:[Power BI Desktop で DAX を使用する](/learn/paths/dax-power-bi/)
- わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
- Power BI チームへのご提案は、 [Power BI を改善するためのアイデアをお寄せください](https://ideas.powerbi.com)