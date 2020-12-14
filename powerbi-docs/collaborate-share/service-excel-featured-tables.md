---
title: Excel で Power BI のおすすめのテーブルにアクセスする
description: Excel の組織のデータ型ギャラリーで、Power BI データセットのおすすめのテーブルからデータを検索できます。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 12/07/2020
LocalizationGroup: Share your work
ms.openlocfilehash: b5f84f67231393dfed78bd9f90142fbd1b4f6c91
ms.sourcegitcommit: 30d0668434283c633bda9ae03bc2aca75401ab94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/09/2020
ms.locfileid: "96907061"
---
# <a name="access-power-bi-featured-tables-in-excel-organization-data-types"></a>Excel の組織のデータ型で Power BI のおすすめのテーブルにアクセスする

"*おすすめのテーブル*" は Excel のデータを Power BI のデータにリンクする 1 つの方法です。 Excel シートにエンタープライズ データを簡単に追加できます。 Excel のデータ型ギャラリーでは、Power BI データセットのおすすめのテーブルからデータを検索できます。 この記事では、その方法について説明します。

Power BI でデータセットを作成しますか? [Power BI Desktop でおすすめのテーブルを設定する方法](service-create-excel-featured-tables.md)に関するページを参照してください。

> [!NOTE]
> Excel によって、Power BI でアクセスできる Power BI データセットからデータを分析することもできます。 詳細については、"Power BI の Excel で分析する" 方法に関する記事の「[Excel から Power BI データセットにアクセスするその他の方法](service-analyze-in-excel.md#other-ways-to-access-power-bi-datasets-from-excel)」を参照してください。
> 

## <a name="the-excel-data-types-gallery"></a>Excel のデータ型ギャラリー
Power BI データセットのおすすめのテーブルは、Excel の **データ型** ギャラリーでは、 **[データ]** リボンに "*データ型*" として表示されます。

:::image type="content" source="media/service-excel-featured-tables/excel-data-ribbon.png" alt-text="Excel の [データ] リボンのデータ型ギャラリーのスクリーンショット。":::

ギャラリーを展開すると、 **[株式]** や **[地理]** などの一般的なデータ型に加え、Power BI データセットのおすすめのテーブルである、使用可能な上位 10 個の **[組織]** データ型が表示されます。

:::image type="content" source="media/service-excel-featured-tables/excel-data-types-gallery.png" alt-text="Excel のデータ型ギャラリーのスクリーンショット。":::

## <a name="search-for-power-bi-data-in-the-data-types-gallery"></a>データ型ギャラリーで Power BI データを検索する

Power BI のおすすめのテーブルのデータを検索するには、おすすめのテーブルの値と一致する値を含む、Excel シート内のセルまたは範囲を選択します。 データ型ギャラリーの横にアル **[さらに表示]** 矢印を選択します。

:::image type="content" source="media/service-excel-featured-tables/excel-data-types-more.png" alt-text="Excel データ型ギャラリーの [さらに表示] アイコンのスクリーンショット。":::

探しているテーブルが見つかったら、それを選択します。 見つからない場合、 **[More from your organization]\(組織からさらに表示\)** を選択します。 Excel に、アクセスできるすべてのおすすめのテーブルがウィンドウに表示されます。

:::image type="content" source="media/service-excel-featured-tables/excel-more-your-organization.png" alt-text="組織から選択する操作のスクリーンショット (プレビュー)。":::
 
Excel に、アクセスできるすべてのおすすめのテーブルが表示されます。 **[データ選択ウィザード]** ウィンドウの **[フィルター]** ボックスに入力し、オプションを絞り込みます。 使用するテーブルを選択します。

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-store.png" alt-text="Excel の組織データ、サプライヤー データ型テーブルのスクリーンショット。":::
 
Excel によって高い信頼度で一致する行が検出された場合、そのセルは直ちにそれらの行にリンクされます。 リンクされた項目のアイコンにより、セルが Power BI の行にリンクされていることが示されます。

:::image type="content" source="media/service-excel-featured-tables/excel-linked-card-icon.png" alt-text="リンクされた項目のアイコンのスクリーンショット。":::

一致する可能性のある行がセルに複数ある場合、そのセルに疑問符アイコンが表示され、 **[データ選択ウィザード]** ウィンドウが開きます。 次の例では、B3:B9 からの範囲を選択し、Power BI おすすめのテーブル **ストア** を選択しました。 セル B9 の "508 - Pasadena Lindseys" を除き、すべての行で一致がありました。 **[データ選択ウィザード]** には、使用できる 2 つの一致が表示されます。2 つの異なるテーブルで同じ値です。

:::image type="content" source="media/service-excel-featured-tables/excel-question-mark-featured-table.png" alt-text="Excel の [データ選択ウィザード] ウィンドウのスクリーンショット。":::
 
[組織] データ オプションを使用すれば、複数のおすすめのテーブルから行を返すことができます。 Excel では、一致する可能性のある行が、その元のデータ型によってグループ化されます。 Excel により、一致する可能性が最も高い行に基づいてデータ型が並べ替えられます。 シェブロンの矢印を使用して、一致する行のデータ型を折りたたんだり展開したりできます。

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-multiple.png" alt-text="可能性のあるものが複数示されている Excel の [データ選択ウィザード] ウィンドウのスクリーンショット。":::
 
提案ごとに **[データ選択ウィザード]** ウィンドウで行の名前を選択すると、行内に詳細が表示されるので、正しい行の選択に便利です。 それが見つかったら、 **[選択]** を押して、その行を Excel のセルにリンクします。 

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-details.png" alt-text="[データ選択ウィザード] の詳細のスクリーンショット。":::

## <a name="explore-related-data"></a>関連データの調査

Excel シートの値と Power BI おすすめのテーブルのデータの間に接続が作成されたので、そのデータをいろいろ調べることができます。 データを使用し、Excel レポートを向上させましょう。

### <a name="view-related-data-in-a-card"></a>カードに関連データを表示する 
 
セルの **[カード]** アイコンを選択すると、おすすめのテーブル内のすべてのフィールドと計算フィールドのデータを含むカードが表示されます。 カードのタイトルには、おすすめのテーブルの [行ラベル] フィールドの値が表示されます。
 
:::image type="content" source="media/service-excel-featured-tables/excel-linked-item-details.png" alt-text="リンクされた項目の詳細のスクリーンショット。":::

### <a name="insert-related-data-from-power-bi"></a>Power BI から関連データを挿入する 

**[データの挿入]** アイコンを選択してから、フィールドの一覧からフィールド名を選んで、その値をグリッドに追加します。  

:::image type="content" source="media/service-excel-featured-tables/excel-select-field.png" alt-text="フィールド名の選択のスクリーンショット。":::

フィールド値は、隣接するセルに配置されます。 セルの数式ではリンクされたセルとフィールド名が参照されるので、Excel 関数内でそのデータを使用できます。

:::image type="content" source="media/service-excel-featured-tables/excel-cell-formula.png" alt-text="Excel のセルの数式のスクリーンショット。":::

### <a name="use-cell-formulas"></a>セルの数式を使用する

Excel テーブルでは、`.` (ピリオド) 参照を使用して、リンク テーブルの列を参照し、データ フィールドを追加することができます。

:::image type="content" source="media/service-excel-featured-tables/excel-dot-reference.png" alt-text="Excel のピリオド参照のスクリーンショット。":::

セルの場合と同様に、セルを参照し、`.` (ピリオド) 参照を使用してフィールドを取得することができます。

:::image type="content" source="media/service-excel-featured-tables/excel-cell-dot-reference.png" alt-text="セルのピリオド参照のスクリーンショット。":::

### <a name="show-a-card-change-or-convert-to-text"></a>カードを表示、変更、またはテキストに変換

リンク セルには、右クリック メニュー オプションが追加されています。 セルを右クリックします。 通常のオプションと共に、以下も表示されます。

- **Show Data Type Card (データ型のカードの表示)** 。
- **データ型** > **テキストに変換**。
- **データ型** > **変更**。
- **更新する**。

:::image type="content" source="media/service-excel-featured-tables/excel-right-click-data-type.png" alt-text="右クリックして表示された [テキストに変換] のスクリーンショット。":::
 
**[テキストに変換]** を使用すると、Power BI のおすすめのテーブルの行へのリンクが削除されます。 重要な点として、セル内のテキストはリンク セルの行ラベルの値になります。 意図していなかった行にセルをリンクした場合は、Excel の **[元に戻す]** を選択して、セルの初期値を復元します。
 
## <a name="data-caching-and-refresh"></a>データのキャッシュと更新

Excel によってセルが Power BI のおすすめのテーブルの行にリンクされると、すべてのフィールド値が取得されて Excel ファイルに保存されます。 自分がファイルを共有したすべてのユーザーは、Power BI からデータを要求することなく、任意のフィールドを参照できます。  

リンク セルのデータを更新するには、 **[データ]** リボンの **[すべて最新の情報に更新]** ボタンを使用します。 

:::image type="content" source="media/service-excel-featured-tables/excel-refresh-all.png" alt-text="[すべて最新の情報に更新] のスクリーンショット。":::
 
また、個々のセルを更新することもできます。 セルを右クリックし、 **[データ型]**  >  **[最新の情報に更新]** を選択してください。

## <a name="licensing"></a>ライセンス

Excel のデータ型ギャラリー、および Power BI のおすすめのテーブルに接続されたエクスペリエンスを利用できるのは、Power BI Pro サービス プランをご利用の Excel サブスクライバーのみです。 

## <a name="security"></a>セキュリティ

Power BI でアクセス許可を持っているデータセットのおすすめのテーブルのみが表示されます。 データを更新するときは、Power BI のデータセットにアクセスして行を取得するためのアクセス許可が必要です。 Power BI で[データセットに対するビルドまたは書き込みアクセス許可](../connect-data/service-datasets-build-permissions.md)が必要になります。
 
Excel では、行全体の返されるデータがキャッシュされます。 自分が Excel ファイルを共有するすべてのユーザーが、すべてのリンク セルのすべてのフィールドのデータを表示できます。

## <a name="administrative-control"></a>管理制御

Power BI 管理者は、Excel のデータ型ギャラリーでおすすめのテーブルを使用できる組織内のユーザーを制御できます。 詳細については、管理ポータルに関する記事の「[おすすめのテーブルへの接続を許可する](../admin/service-admin-portal.md#allow-connections-to-featured-tables)」を参照してください。 
 
### <a name="auditing"></a>監査

管理の監査ログには、おすすめのテーブルに関する次のイベントが表示されます。

- **AnalyzedByExternalApplication**:どのユーザーがどのおすすめのテーブルにアクセスしているかを管理者が把握できます。
- **UpdateFeaturedTables**:どのユーザーがおすすめのテーブルを発行および更新しているかを管理者が把握できます。

監査ログのイベントの完全な一覧については、「[Power BI でユーザー アクティビティを追跡する](../admin/service-admin-auditing.md)」をご覧ください。

## <a name="considerations-and-limitations"></a>考慮事項と制限事項

現在の制限事項は次のとおりです。

- 統合は、現在のチャネルの Excel で使用できます。
- 次の機能を使用する Power BI データセットのおすすめのテーブルは、Excel に表示されません。 

    - DirectQuery データセット。
    - ライブ接続を使用するデータセット。

- Excel には、おすすめのテーブルで定義されている列、計算列、およびメジャーのデータのみが表示されます。 次のものは表示されません。
   
    - 関連テーブル上で定義されているメジャー。
    - リレーションシップから算出される暗黙的なメジャー。

- Excel には、新しい Power BI ワークスペースに格納されているおすすめのテーブル ("*データ型*") のみが表示されます。 クラシック ワークスペースに格納されているおすすめのテーブルは、Excel ではデータ型として表示されません。 Power BI で[クラシック ワークスペースを新しいワークスペースにアップグレードする](service-upgrade-workspaces.md)ことができます。

Excel でのデータ型のエクスペリエンスは、lookup 関数に似ています。 Excel シートから提供されるセル値を受け取り、Power BI のおすすめのテーブルで一致する行が検索されます。 検索エクスペリエンスには、次のような動作があります。

- 行の一致は、おすすめのテーブルに含まれるテキスト列に基づいています。 これには Power BI Q&A 機能と同じインデックスが使用されます。これは英語での検索用に最適化されています。 その他の言語で検索すると、正確な一致が得られない場合があります。 
- ほとんどの数値列は、照合の対象とは見なされません。 行ラベルまたはキー列が数値である場合は、それらは照合の対象に含められます。
- 一致は、個々の検索語句の完全一致とプレフィックス一致に基づいています。 セルの値は、スペース、またはタブのようなその他の空白文字に基づいて分割されます。 その後、各単語が検索語句と見なされます。 行のテキスト フィールドの値が、完全一致とプレフィックス一致で各検索語句と比較されます。 行のテキスト フィールドがその検索語句で始まる場合は、プレフィックス一致が返されます。 たとえば、セルに "Orange County" が含まれていた場合、"Orange" と "County" が個別の検索語句になります。 

    - 値が "Orange" または "County" と完全に一致するテキスト列を含む行が返されます。 
    - 値が "Orange" または "County" で始まるテキスト列を含む行が返されます。 
    - 重要なこととして、"Orange" または "County" を含んでいても、それらの語句で始まらない行は返されません。

- Power BI では、各セルに対して最大 100 行の候補が返されます。
- 一部のシンボルはサポートされていません。
- XMLA エンドポイントでのおすすめのテーブルの設定または更新はサポートされていません
- データ モデルを含む Excel ファイルを使用して、おすすめのテーブルを発行することができます。 そのデータを Power BI Desktop に読み込み、おすすめのテーブルを発行します。
- おすすめのテーブルのテーブル名、行ラベル、またはキー列を変更すると、そのテーブルの行にリンクされたセルを使用する Excel ユーザーに影響を及ぼす可能性があります。 
- Excel では、データが Power BI データセットから取得された日時が表示されます。 今回は、Power BI でデータが更新された時間、またはデータセット内の最新のデータ ポイントの時間であるとは限りません。 たとえば、Power BI のデータセットが 1 週間前に更新されましたが、基になるソース データは更新が行われた時点で 1 週間経過していたとします。 実際のデータは 2 週間前のものになりますが、Excel によって、データが Excel に取り込まれた日付/時刻として、取得されたデータが表示されます。 

## <a name="next-steps"></a>次の手順

- [Power BI Desktop でおすすめのテーブルを設定する](service-create-excel-featured-tables.md)
- [Power BI からの Excel のデータ型の使用](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9)について、Excel のドキュメントを参照します。
- わからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。

