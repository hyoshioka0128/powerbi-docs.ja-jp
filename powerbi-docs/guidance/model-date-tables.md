---
title: Power BI Desktop で日付テーブルを作成する
description: Power BI Desktop で日付テーブルを作成するための手法とガイダンスです。
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 06/24/2020
ms.openlocfilehash: a2616b5f77a03056de03b213369d55e9b590b1b6
ms.sourcegitcommit: 7599622381f35a161bfc54726675ed3c9cf13816
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/31/2020
ms.locfileid: "97827574"
---
# <a name="create-date-tables-in-power-bi-desktop"></a>Power BI Desktop で日付テーブルを作成する

この記事は、Power BI Desktop を操作するデータ モデラーを対象としています。 データ モデルで日付テーブルを作成する際に推奨される設計方法について説明します。

データ分析式 (DAX) の [タイム インテリジェンス関数](/dax/time-intelligence-functions-dax) を使用するには、前提条件となるモデル要件があります。モデルには少なくとも 1 つの "_日付テーブル_" が必要です。 日付テーブルとは、次の要件を満たすテーブルです。

> [!div class="checklist"]
> - "_日付列_" と呼ばれるデータ型 **date** (または **date/time** ) の列が必要です。
> - 日付列には一意の値が含まれている必要があります。
> - 日付列に空白を含めることはできません。
> - 日付列に欠落している日付があってはなりません。
> - 日付列は年間全体にわたっている必要があります。 1 年は必ずしも暦年 (1 月から 12 月) ではありません。
> - 日付テーブルには[日付テーブルとしてマークされている](../transform-model/desktop-date-tables.md#setting-your-own-date-table)必要があります。

モデルに日付テーブルを追加するには、次のいずれかの手法を使用できます。

- [自動の日付/時刻] オプション
- 日付ディメンション テーブルに接続する Power Query
- 日付テーブルを生成する Power Query
- 日付テーブルを生成する DAX
- 既存の日付テーブルを複製する DAX

> [!TIP]
> 日付テーブルは、おそらくモデルに追加する最も一貫性のある機能です。 さらに、組織内では日付テーブルを一貫した方法で定義する必要があります。 そのため、どの方法を使用する場合でも、完全に構成された日付テーブルを含む [Power BI Desktop テンプレート](../create-reports/desktop-templates.md)を作成することをお勧めします。 組織内のすべてのモデル管理者とテンプレートを共有してください。 そうすれば、だれかが新しいモデルを開発するたびに、一貫した方法で定義された日付テーブルから始めることができます。

## <a name="use-auto-datetime"></a>[自動の日付/時刻] を使用する

[[自動の日付/時刻]](../transform-model/desktop-auto-date-time.md) オプションによって、便利かつ高速で使いやすいタイム インテリジェンスが提供されます。 レポート作成者は、カレンダー期間を使用してフィルター処理、グループ化、およびドリルダウンを行うときにタイム インテリジェンスを操作できます。

[自動の日付/時刻] オプションは、カレンダー期間を操作する場合と、時間に関して単純なモデル要件がある場合にのみ有効にすることをお勧めします。 このオプションは、アドホック モデルを作成したり、データの探索やプロファイリングを実行したりするときにも便利に使用できます。 ただし、この方法では、フィルターを複数のテーブルに伝達できる 1 つの日付テーブル デザインはサポートされていません。 詳細については、「[Power BI Desktop での自動の日付/時刻のガイダンス](auto-date-time.md)」を参照してください。

## <a name="connect-with-power-query"></a>Power Query を使用して接続する

データ ソースに既に日付テーブルがある場合は、それをモデルの日付テーブルのソースとして使用することをお勧めします。 データ ウェアハウスには日付ディメンション テーブルがあるため、データ ウェアハウスに接続している場合がこれに該当します。 このようにすると、モデルには組織の時間について 1 つの信頼できる情報源が利用されます。

DirectQuery モデルを開発していて、データ ソースに日付テーブルが含まれていない場合は、データ ソースに日付テーブルを追加することを強くお勧めします。 日付テーブルのすべてのモデリング要件を満たす必要があります。 これで Power Query を使用して日付テーブルに接続できるようになります。 このようにして、モデルの計算に DAX タイム インテリジェンス機能を利用できます。

## <a name="generate-with-power-query"></a>Power Query を使用して生成する

Power Query を使用して日付テーブルを生成できます。 詳細については、Chris Webb のブログ エントリ「[Power Query での日付ディメンション テーブルの生成](https://blog.crossjoin.co.uk/2013/11/19/generating-a-date-dimension-table-in-power-query/)」を参照してください。

> [!TIP]
> 組織内にデータ ウェアハウスやその他の一貫した定義がない場合は、Power Query を使用して[データフロー](../transform-model/dataflows/dataflows-introduction-self-service.md)を発行することを検討します。 次に、すべてのデータ モデル管理者をデータフローに接続し、モデルに日付テーブルを追加します。 このデータフローは、組織内の時間に関する 1 つの信頼できる情報源になります。

日付テーブルを生成する必要がある場合は、DAX を使用して実行することを検討してください。 場合によっては、より簡単と思われるかもしれません。 さらに、DAX には日付テーブルの作成と管理を簡素化する組み込みのインテリジェンスが組み込まれているため、より便利になる可能性があります。

## <a name="generate-with-dax"></a>DAX を使用して生成する

[CALENDAR](/dax/calendar-function-dax) または [CALENDARAUTO](/dax/calendarauto-function-dax) DAX 関数を使用して計算テーブルを作成することで、モデルに日付テーブルを生成することができます。 各関数からは、日付の単一列のテーブルが返されます。 次に、計算された列を使用して計算テーブルを拡張し、日付間隔のフィルター処理とグループ化の要件をサポートできます。

- 日付範囲を定義する場合は、**CALENDAR** 関数を使用します。 開始日と終了日の 2 つの値を渡します。 これらの値は、`MIN(Sales[OrderDate])` や `MAX(Sales[OrderDate])` などの他の DAX 関数で定義できます。
- 日付範囲にモデルに保存されているすべての日付を自動的に含める場合は、**CALENDARAUTO** 関数を使用します。 年の最終月である 1 つの省略可能なパラメーターを渡すことができます (年が 12 月に終わる暦年の場合、値を渡す必要はありません)。 完全な年間の日付が返されること (これはマークされた日付テーブルの場合の要件です) が保証されるため、これは便利な関数です。 さらに、将来の年に備えたテーブルの拡張を管理する必要はありません。データの更新が完了すると、テーブルの再計算がトリガーされます。 新しい年の日付がモデルに読み込まれると、再計算により、テーブルの日付範囲が自動的に拡張されます。

## <a name="clone-with-dax"></a>DAX を使用して複製する

モデルに既に日付テーブルがあり、追加の日付テーブルが必要な場合は、既存の日付テーブルを簡単に複製できます。 たとえば、日付が[ロール プレイング ディメンション](star-schema.md#role-playing-dimensions)の場合です。 計算テーブルを作成することで、テーブルを複製できます。 計算テーブル式は、単に既存の日付テーブルの名前です。

## <a name="next-steps"></a>次の手順

この記事に関する詳細については、次のリソースを参照してください。

- [Power BI Desktop の自動の日付/時刻](../transform-model/desktop-auto-date-time.md)
- [Power BI Desktop での自動の日付/時刻のガイダンス](auto-date-time.md)
- [Power BI Desktop で日付テーブルを設定し、使用する](../transform-model/desktop-date-tables.md)
- [Power BI でのセルフサービスのデータ準備](../transform-model/dataflows/dataflows-introduction-self-service.md)
- [CALENDAR 関数 (DAX)](/dax/calendar-function-dax)
- [CALENDARAUTO 関数 (DAX)](/dax/calendarauto-function-dax)
- わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
- Power BI チームへのご提案は、 [Power BI を改善するためのアイデアをお寄せください](https://ideas.powerbi.com/)