---
title: Power BI Desktop の変更ログ
description: この変更ログは Power BI Desktop 用です。リリースされた各ビルドの新しい項目とバグの修正が一覧表示されます。
author: willthom
ms.author: v-okkyry
ms.reviewer: maggies, davidi
ms.service: powerbi
ms.subservice: pbi-fundamentals
ms.topic: conceptual
ms.date: 03/30/2021
ms.openlocfilehash: 497cd89f0d8967895642941d8135081fca5c6323
ms.sourcegitcommit: 904dd7f991ff4087f2802c50a8af7d8515d9378c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/31/2021
ms.locfileid: "106012206"
---
# <a name="change-log-for-power-bi-desktop"></a>Power BI Desktop の変更ログ

この変更ログは Power BI Desktop 用です。リリースされた各 QFE ビルドの新しい項目とバグの修正が一覧表示されます。

新機能の詳細については、「[Power BI の新機能](desktop-latest-update.md)」を参照してください。 

## <a name="march-2021-qfe-1"></a>2021 年 3 月 QFE 1

*バージョン: 2.91.884.0、リリース日: 2021 年 3 月 29 日*

バグ修正:
- 評価のシャットダウン中に Microsoft Information Protection SDK がハングする問題の修正。
- Amazon Redshift ドライバーの更新プログラムは、クエリのマージ後、null 許容ではない主キーの列が空の文字列として扱われる問題を修正します。
- 集計の使用時、スライサーに一意の (重複しない) 値を含めるための修正。
- 数式バーの修正: 空のメジャー、計算列、計算テーブルがモデルから削除されたとき、UI の相互作用を妨ぎます。
- PBI.FormatAnnotationStats テレメトリ イベントの修正。
- カスタマイズされたフィールドの表示フォルダーの修正: データの更新後、あるいは Power Query で **[列の選択]** 変更後、フォルダーが消えないようになりました。
- ODBC ドライバーが新しいバージョンに更新されます。
- Microsoft Information Protection タイムアウト問題の修正: ユーザーがファイルかサインインを開き、ネットワーク問題が発生しても、MIP 例外が表示されなくなりました。

## <a name="february-2021-qfe-1"></a>2021 年 2 月 QFE 1

*バージョン: 2.90.1081.0、リリース日: 2021 年 3 月 8 日*

バグ修正: 
- Azure Analysis Services OAuth トークン更新時の問題を修正。
- Power Query モデルを Excel から Power BI Desktop にインポートするときの問題を修正。
- 動的な書式指定文字列、系列、カテゴリ、列値、行値を含む複合グラフの問題を修正。
- Power BI Desktop 保存検証機能の修正: Analysis Services によって zip ファイルに書き込まれることに起因する場合、顧客の前のファイルが無効な .pbix ファイルで上書きされることがなくなりました。
- Model ビューの大きな .pbix ファイルの修正: モデル ビューにすばやく切り替えたとき、エラーがスローされることがなくなりました。 
- モデル ビューのテーブル カード内でぼやけるフィールドとアイコン テキストの修正。 
- カラー ピッカーの修正: ESC キーを押したときに閉じられるようになりました。 

## <a name="next-steps"></a>次の手順

[Power BI の新機能](desktop-latest-update.md)
[Power BI の以前の月次更新プログラム](desktop-latest-update-archive.md)

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
