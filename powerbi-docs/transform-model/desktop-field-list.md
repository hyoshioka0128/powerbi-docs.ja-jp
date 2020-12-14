---
title: Power BI Desktop のフィールド一覧の使用 (プレビュー)
description: Power BI Desktop でフィールド一覧を使用してデータをモデル化し、レポートを作成します
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: conceptual
ms.date: 11/11/2020
LocalizationGroup: Transform and shape data
ms.openlocfilehash: ced861f0d229153866c1d52616494f8b444220ae
ms.sourcegitcommit: 8993400b32a44f4e7ce9a2db998ddebda18c7698
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2020
ms.locfileid: "96536486"
---
# <a name="using-the-field-list-in-power-bi-desktop-preview"></a>Power BI Desktop のフィールド一覧の使用 (プレビュー)

2020 年 11 月の更新プログラム以降、Power BI Desktop のモデル ビュー、データ ビュー、レポート ビューのすべてで **フィールド** 一覧を統一する作業が行われています。 これらのビューを統一することで、ビュー全体の機能とユーザー インターフェイス (UI) が一貫したものになり、お客様からのフィードバックに対処されます。

ビューに関する変更点は次のとおりです。

* 図像
* 検索機能
* コンテキスト メニュー項目
* 類似したドラッグ アンド ドロップ動作
* ヒント
* アクセシビリティの機能強化

目的は Power BI Desktop をいっそう使いやすくすることです。 通常のデータ ワークフローへの変更の影響は、最小限にする必要があります。

## <a name="enabling-the-new-field-list-preview"></a>新しいフィールド一覧の有効化 (プレビュー)

統合フィールド一覧は **[モデル]** ビューで開始し、その後、他のビューで有効になります。 統合フィールド ビューを有効にするには、Power BI Desktop で **[ファイル] > [オプションと設定] > [オプション]** に移動し、左側のペインで **[プレビュー機能]** を選択します。 [プレビュー機能] セクションで、 **[New field list]\(新しいフィールド一覧\)** の横にあるチェック ボックスをオンにします。

![新しいフィールド一覧を有効にする](media/desktop-field-list/field-list-01.png)

選択を有効にするため Power BI Desktop を再起動するよう求められます。

## <a name="field-list-changes"></a>フィールド一覧の変更

次の表では、フィールド一覧に関する更新を示します。 


|**元のフィールド一覧 (モデル ビュー)**  | **新しいフィールド一覧 (モデル ビュー)**  |
|:---------:|:---------:|
|**Original** |**[新規作成]** |
|**アイコンと UI**       ||
|![元のフィールド一覧](media/desktop-field-list/field-list-01a.png)     |![新しいフィールド一覧](media/desktop-field-list/field-list-01b.png)    |
|**コンテキスト メニュー - フィールド**       ||
|![フィールドの元のコンテキスト メニュー](media/desktop-field-list/field-list-02a.png)     |![フィールドの新しいコンテキスト メニュー](media/desktop-field-list/field-list-02b.png)    |
|**コンテキスト メニュー - テーブル**       ||
|![テーブルの元のコンテキスト メニュー](media/desktop-field-list/field-list-03a.png)     |![テーブルの新しいコンテキスト メニュー](media/desktop-field-list/field-list-03b.png)    |
|**ヒント**       ||
|![元のヒント](media/desktop-field-list/field-list-04a.png)     |![新しいヒント](media/desktop-field-list/field-list-04b.png)    |

## <a name="field-list-icons"></a>フィールド一覧アイコン

新しいフィールド一覧アイコンもあります。 次の表では、元のアイコンとそれに相当する新しいアイコン、およびそれぞれの簡単な説明を示します。 


|元のアイコン  |新規アイコン  |説明  |
|:---------:|:---------:|:---------|
|![元のフォルダー アイコン](media/desktop-field-list/field-list-05a.png)     |![新しいフォルダー アイコン](media/desktop-field-list/field-list-05b.png)           |[フィールド] リストのフォルダー         |
|![元の数値フィールド アイコン](media/desktop-field-list/field-list-06a.png)     |![新しい数値フィールド アイコン](media/desktop-field-list/field-list-06b.png)         |数値フィールド: 数値フィールドは、合計や平均などが可能な集計です。 集計は、データと一緒にインポートされ、レポートの基となるデータ モデルで定義されます。 詳細については、「[Power BI レポートの集計](../create-reports/service-aggregates.md)」を参照してください。         |
|![元の計算列アイコン](media/desktop-field-list/field-list-07a.png)     |![新しい計算列アイコン](media/desktop-field-list/field-list-07b.png)         |数値以外のデータ型を含む計算列: 列の値を定義する Data Analysis Expressions (DAX) 式を使用して作成する新しい数値以外の列です。 [計算列](desktop-calculated-columns.md)に関する詳細情報を表示します。        |
|![元の数値計算列アイコン](media/desktop-field-list/field-list-08a.png)     |![新しい数値計算列アイコン](media/desktop-field-list/field-list-08b.png)          |数値の計算列: 列の値を定義する Data Analysis Expressions (DAX) 式を使用して作成する新しい列です。 [計算列](desktop-calculated-columns.md)に関する詳細情報を表示します。         |
|![元のメジャー アイコン](media/desktop-field-list/field-list-09a.png)     |![新しいメジャー アイコン](media/desktop-field-list/field-list-09b.png)          |メジャー: メジャーには、独自のハードコーディングされた式があります。 レポート閲覧者は、計算を変更することはできません、たとえば、合計であれば、合計のままにしかできません。 値は列に格納されません。 これらは、ビジュアル内の場所のみに応じて、すぐに計算されます。 詳細については、「[メジャーについて](desktop-measures.md)」を参照してください。         |
|![元のメジャー グループ アイコン](media/desktop-field-list/field-list-10a.png)     |![新しいメジャー グループ アイコン](media/desktop-field-list/field-list-10b.png)         |メジャー グループ。         |
|![元の KPI アイコン](media/desktop-field-list/field-list-11a.png)     |![新しい KPI アイコン](media/desktop-field-list/field-list-11b.png)         |KPI: 測定可能な目標に対する進捗状況を視覚的に伝える方法の 1 つです。 [主要業績評価指標 (KPI)](../visuals/power-bi-visualization-kpi.md) ビジュアルに関する詳細について参照してください。         |
|![元のフィールド階層アイコン](media/desktop-field-list/field-list-12a.png)     |![新しいフィールド階層アイコン](media/desktop-field-list/field-list-12b.png)           |フィールドの階層: 矢印を選択し、階層を構成するフィールドを表示します。 詳細については、YouTube で[階層の作成と使用](https://www.youtube.com/watch?v=q8WDUAiTGeU)についてのこの Power BI ビデオをご覧ください。         |
|![元の geo データ アイコン](media/desktop-field-list/field-list-13a.png)     |![新しい geo データ アイコン](media/desktop-field-list/field-list-13b.png)         |Geo データ: これらの場所フィールドは、地図の視覚化を作成するために使用できます。         |
|![元の ID フィールド アイコン](media/desktop-field-list/field-list-14a.png)     |![新しい ID フィールド アイコン](media/desktop-field-list/field-list-14b.png)          |ID フィールド: このアイコンのフィールドは、一意のフィールドであり、重複するものがあっても、すべての値が表示されるように設定されています。 たとえば、データに 'Robin Smith' という名前のユーザーのためのレコードが 2 つあったとしても、それぞれが一意として扱われます。 これらは合算されることはありません。         |
|![元のパラメーター アイコン](media/desktop-field-list/field-list-15a.png)     |![新しいパラメーター アイコン](media/desktop-field-list/field-list-15b.png)          |パラメーター: 1 つまたは複数のパラメーター値に応じて、レポートおよびデータ モデルの一部 (クエリ フィルター、データ ソース参照、メジャー定義など) にするパラメーターを設定します。 詳細については、この Power BI の[クエリ パラメーター](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/)に関するブログ投稿を参照してください。         |
|![元のカレンダー日付フィールド アイコン](media/desktop-field-list/field-list-16a.png)     |![新しいカレンダー日付フィールド アイコン](media/desktop-field-list/field-list-16b.png)         |組み込みの日付テーブルを含むカレンダー日付フィールド。         |
|![元の計算テーブル アイコン](media/desktop-field-list/field-list-17a.png)     |![新しい計算テーブル アイコン](media/desktop-field-list/field-list-17b.png)          |計算テーブル:モデルに既に読み込まれているデータに基づいて、Data Analysis Expressions (DAX) 式で作成されたテーブル。 これらは中間計算に最適であり、モデルの一部として格納できます。         |
|![元の警告アイコン](media/desktop-field-list/field-list-18a.png)     |![新しい警告アイコン](media/desktop-field-list/field-list-18b.png)         |警告:エラーがある計算フィールド。 たとえば、DAX 式の構文が正しくない場合があります。         |
|![元のグループ アイコン](media/desktop-field-list/field-list-19a.png)     |![新しいグループ アイコン](media/desktop-field-list/field-list-19b.png)         |グループ:この列の値は、グループとビンの機能を使用する、別の列からの値のグループ化に基づいています。 [グループ化とビン分割を使用する](../create-reports/desktop-grouping-and-binning.md)方法を参照してください。         |
| 元のアイコンなし    |![新しい変更検出メジャー アイコン](media/desktop-field-list/field-list-20b.png)          |変更検出メジャー:ページが自動的に更新されるようにページを構成するときに、ページのビジュアルの残りの部分を更新する必要があるかどうかを判断するためにクエリが実行される[変更検出メジャー](../create-reports/desktop-grouping-and-binning.md)を構成できます。         |


## <a name="next-steps"></a>次のステップ

次の記事にも興味をもたれるかもしれません。

* [Power BI Desktop での計算列の作成](desktop-calculated-columns.md)
* [Power BI Desktop でグループ化とビン分割を使用する](../create-reports/desktop-grouping-and-binning.md)
* [Power BI Desktop レポートでグリッド線と "グリッドにスナップ" を使用する](../create-reports/desktop-gridlines-snap-to-grid.md)

