---
title: 'Power BI のお客様の収益性のサンプル: 使ってみる'
description: 'Power BI のお客様の収益性のサンプル: 使ってみる'
author: maggiesMSFT
ms.author: maggies
ms.reviewer: amac
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 07/05/2019
LocalizationGroup: Samples
ms.openlocfilehash: afe01b29513c095919e17d50e1c7e08060f11150
ms.sourcegitcommit: f3669a5f68c9d646d86adcf77e589af4540042e3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2021
ms.locfileid: "102534174"
---
# <a name="customer-profitability-sample-for-power-bi-take-a-tour"></a>Power BI のお客様の収益性のサンプル: 使ってみる

"お客様の収益性のサンプル" コンテンツ パックには、マーケティング資料を製作する会社向けのダッシュボード、レポート、データセットが含まれています。 このダッシュボードは、5 つの事業部のマネージャー (役員)、製品、顧客、および粗利益 (GM) に関する主要なメトリックを確認するために、CFO によって作成されました。 これにより、収益性に影響する要因を一目で確認できます。

![お客様の収益性のサンプルのダッシュボード](media/sample-customer-profitability/power-bi-dash.png)

このサンプルは、ビジネス用のデータ、レポート、ダッシュボードを用いて Power BI を使う方法について説明するシリーズの一部です。 匿名化された実際のデータを使用し、[obviEnce](http://www.obvience.com/) によって作成されています。 データは複数の形式 (コンテンツ パック、Power BI Desktop の .pbix ファイル、Excel ブック) で使用できます。 [Power BI 用のサンプル](sample-datasets.md)を参照してください。 

このチュートリアルでは、Power BI サービス内のお客様の収益性のサンプル コンテンツ パックを調べます。 Power BI Desktop とサービスのレポート エクスペリエンスは似ているので、Power BI Desktop 内のサンプルの .pbix ファイルを使用して作業することもできます。 

Power BI Desktop 内でサンプルを調べるために Power BI ライセンスは不要です。 Power BI Pro ライセンスを持っていない場合は、Power BI サービス内で、マイ ワークスペースにサンプルを保存できます。 

## <a name="get-the-sample"></a>サンプルを入手する

このサンプルを使用するには、事前にサンプルを[コンテンツ パック](#get-the-content-pack-for-this-sample)、[.pbix ファイル](#get-the-pbix-file-for-this-sample)、または [Excel ブック](#get-the-excel-workbook-for-this-sample)としてダウンロードしておく必要があります。

### <a name="get-the-content-pack-for-this-sample"></a>このサンプルのコンテンツ パックを入手する

1. Power BI サービス (app.powerbi.com) を開いてサインインし、サンプルを保存するワークスペースを開きます。

   Power BI Pro ライセンスを持っていない場合は、マイ ワークスペースにサンプルを保存できます。

2. 左下隅にある **[データを取得]** を選びます。

   ![[データを取得] を選択](media/sample-datasets/power-bi-get-data.png)
3. 表示された **[データを取得]** ページで、 **[サンプル]** を選びます。

4. **[お客様の収益性のサンプル]** を選び、**[接続]** を選びます。  

    ![サンプルに接続](media/sample-customer-profitability/get-supplier-sample.png)
5. Power BI によってコンテンツ パックがインポートされ、新しいダッシュボード、レポート、およびデータセットが現在のワークスペースに追加されます。

    !["お客様の収益性のサンプル" 項目](media/sample-customer-profitability/customer-profitability-sample-entry.png)

### <a name="get-the-pbix-file-for-this-sample"></a>このサンプルの .pbix ファイルを取得する

あるいは、Power BI Desktop で使用するように設計された [.pbix](https://download.microsoft.com/download/6/A/9/6A93FD6E-CBA5-40BD-B42E-4DCAE8CDD059/Customer%20Profitability%20Sample%20PBIX.pbix) ファイルとして、"お客様の収益性のサンプル" をダウンロードすることもできます。

### <a name="get-the-excel-workbook-for-this-sample"></a>このサンプルの Excel ブックを取得する

このサンプルのデータ ソースを確認する場合は、[Excel ブック](https://go.microsoft.com/fwlink/?LinkId=529781) として入手することもできます。 ブックには、表示および変更可能な Power View シートが含まれています。 生データを表示するには、データ分析アドインを有効にし、 **[PowerPivot] > [管理]** を選択します。 Power View および Power Pivot のアドインを有効にするための詳細については、[Excel での Excel のサンプルの確認](sample-datasets.md#explore-excel-samples-inside-excel)に関するセクションを参照してください。

## <a name="what-is-our-dashboard-telling-us"></a>ダッシュボードからわかること

サンプルを保存したワークスペースで、お客様の収益性ダッシュボードを探して選択します。

![お客様の収益性のサンプルのダッシュボード](media/sample-customer-profitability/power-bi-dash.png)

### <a name="company-wide-dashboard-tiles"></a>会社全体のダッシュボードのタイル
1. Power BI サービスでダッシュボードを開きます。 CFO はこのダッシュボードのタイルから、自身にとって重要な、会社の高水準なメトリックに関する概要を得ることができます。 何か興味深いものがある場合は、タイルを選んで詳しいデータを掘り下げることができます。

2. 左側にあるダッシュボードのタイルを確認します。

    ![マネージャーのタイル](media/sample-customer-profitability/power-bi-manager.png)

   次の詳細に注意します。
   - 会社の粗利益は 42.5% です。
   - 顧客数は 80 です。
   - 5 つの異なる製品を販売しています。
   - 予算に対する収益差異 % が最低だったのは 2 月で、3 月は最高でした。
   - 収益のほとんどは、東部地域と北部地域から発生しています。 粗利益が予算を超えたことはなく、ER-0 と MA-0 のビジネス ユニットではさらに調査が必要です。
   - 年間の総収益はほぼ予算どおりです。

### <a name="manager-specific-dashboard-tiles"></a>マネージャー固有のダッシュボード タイル
ダッシュボードの右側にあるタイルには、チームのスコアカードが表示されます。 CFO はマネージャーについて把握しておく必要があり、これらのタイルでは GM% を使用して利益の概要が示されます。 いずれかのマネージャーに関して予期しない GM% の傾向が見られる場合は、さらに調査できます。

![マネージャーの GM%](media/sample-customer-profitability/power-bi-manager2.png)

マネージャー固有のダッシュボード タイルを分析することで、以下の所見を得ることができます。

- Carlos を除いた経営陣全員が、既に売上目標を上回っています。 ただし、Carlos の売上実績はもっとも高い値です。
- Annelie の GM% は最低ですが、3 月以降、安定的に増加しているのがわかります。
- その一方で、Valery は GM% が大幅に低下しています。
- Andrew は不安定な 1 年でした。

## <a name="explore-the-dashboards-underlying-data"></a>ダッシュボードの基になるデータの調査
このダッシュボードのタイルはレポートと Excel ブックにリンクされています。

### <a name="open-the-excel-online-data-source"></a>Excel Online のデータ ソースを開く
ダッシュボード上の **[Target vs Actual]\(目標と実績\)** と **[前年比収益成長]** の 2 つのタイルは、Excel ブックからピン留めされたものです。 このタイルのどちらかを選択すると、Power BI によってデータ ソース (この場合は Excel Online) が開きます。

![Excel Online](media/sample-customer-profitability/power-bi-excel-online.png)

1. **[Target vs Actual]** を選択します。 Excel Online が Power BI サービス内で開きます。
2. ブックにはタブ 3 つ分のデータがあることに注意してください。 **[COGS]** を開きます。

    ![選択された [COGS] レポート タブ。](media/sample-customer-profitability/power-bi-cogs.png)

1. 合計収益がコストを大きく超えています。 合計収益の線の形とコストの列の高さは、似ています。  フィルター処理、スライス、ドリルなどを行って、データと対話します。  例として、1 つの Industry のみの **Revenue vs COGS** を見てみましょう。   

    a. **[Industry]** スライサーから、 **[Retail]** を選択します。   
    
    ![小売業界が選択されています。](media/sample-customer-profitability/power-bi-retails.png)

    b. 小売業界を担当している地区マネージャーは、Andrew と Carlos の 2 人だけであることがわかります。  
    
    c. 2014 年第 3 四半期までは、合計収益がコストを大きく超えています。 その積み上げ縦棒を見ると、さらなる調査が必要な奇妙なデータがあります。 7 月は本当にコストがなかったのでしょうか。 サード パーティから払い戻しを受けたのでしょうか。 

4. 調査を続けます。 興味のあるものが見つかったら右上隅にある **[ピン留め]** ![[ピン留め] アイコン](media/sample-customer-profitability/power-bi-excel-pin.png) を選択して、[ダッシュボードにピン留め](service-dashboard-pin-tile-from-excel.md)します。

5. ダッシュボードに戻るには、ブラウザーの戻る矢印を使用します。

### <a name="open-the-underlying-power-bi-report"></a>基になる Power BI レポートを開く
お客様の収益性のサンプル ダッシュボードのタイルは、その大部分が、基になっているお客様の収益性のサンプルのレポートからピン留めされたものです。

1. これらのタイルのいずれかを選択して、読み取りビューでレポートを開きます。

   タイルが Q&A で作成されている場合は、それを選択すると、Q&A ウィンドウが開きます。 **[Exit Q&A]\(Q&A の終了\)** を選択してダッシュボードに戻り、別のタイルを試します。

2. レポートには 3 つのページがあります。 レポートの下部にあるタブは、それぞれが異なるページを表しています。

    ![下部にある 3 つのタブ](media/sample-customer-profitability/power-bi-report-tabs.png)

    * **チーム スコアカード** では、5 人のマネージャーの業績とその顧客管理手法に焦点を合わせます。
    * **業界の利益分析** では、業界全体の状況と比較して収益性を分析する方法が提供されます。
    * **Executive Scorecard** では、カスタム ページ サイズ フォーマットで各マネージャーのビューが提供されます。

### <a name="team-scorecard-page"></a>「チーム スコアカード」ページ
![チーム スコアカード レポート ページ](media/sample-customer-profitability/customer2.png)

2 人のチーム メンバーを詳しく考察し、どのような分析情報が得られるかを確認してみましょう。 

1. 左側の **[Executive]** スライサーで Andrew の名前を選んで、Andrew のデータのみが表示されるようにレポート ページをフィルター処理します。

   * クイック KPI では、Andrew の **収益の状態 (合計年)** に注目します。それは緑色であり、業績が良好であることを意味しています。
   * **[月別および役員別の予算に対する収益率差異]** グラフには、2 月の落ち込みを除き、Andrew は良好な結果を出していることが示されています。 Andrew の主要な地域は東部地域で、49 社の顧客と (7 つのうち) 5 つの製品が含まれています。 Andrew の GM% は、最上位でも最下位でもありません。
   * **[RevenueTY and Revenue % Var to Budget by Month]\(月別の予算に対する収益年合計と収益 % 差異\)** グラフには、安定した一様の収益利益が示されています。 ところが、地域ツリーマップ内の **[Central]\(中部\)** の四角形をクリックしてフィルター処理すると、Andrew は 3 月にインディアナ州でのみ売上があることがわかります。 この傾向は意図的なものでしょうか、それとも検討する必要があるものでしょうか。

2. 次は Valery です。 **[Executive]** スライサーで Valery の名前を選んで、Valery のデータのみを表示するようにレポート ページをフィルター処理します。 

   ![Valery のデータ](media/sample-customer-profitability/customer3.png)

   * **[Revenue Status (Total Year)]\(収益の状態 (年合計)\)** の赤色の KPI に注意してください。 この項目は、明らかにさらなる調査が必要です。
   * Valery の収益差異は、設定された収益マージンを Valery が満たしていないという懸念点も示しています。
   * Valery の顧客はわずか 9 社で、2 製品のみを扱い、取引先はほぼ北部地域の顧客のみに限られています。 この特殊性は、メトリックにおける変動幅が大きいことの説明になる可能性があります。
   * ツリー マップ内の **[North]\(北部\)** の四角形を選ぶと、北部地域での Valery の粗利益が全体的な利益と一貫性があることがわかります。
   * **[Total Revenue by Region]\(地域別合計収益\)** の他の四角形をそれぞれ選択すると、興味深いことがわかります。その GM% は 23% から 79% の範囲にあるのです。 Valery の収益の数値は、北部地域を除くすべての地域で、非常に季節性があります。

3. なぜ Valery の領域で業績が良くないかを知るためにデータの詳しい調査を続けます。 複数の地域、他の事業部、レポートの次のページ「**業界の利益分析**」をご覧ください。

### <a name="industry-margin-analysis"></a>業界の利益分析
このレポート ページでは、データの別のスライスを提供します。 これは、セグメントごとに分割した、業界全体の粗利益を考察します。 CFO はこのページを利用して、会社と事業部のメトリックを業界のメトリックと比較し、傾向と収益性の説明に役立てます。 **[Gross Margin % by Month and Executive]** グラフはチーム固有であるにもかかわらず、なぜこのページ上にあるのか不思議に思われるかもしれません。 ここに表示することで、事業部のマネージャー別にページをフィルター処理することができます。  

![[Industry Margin Analysis] レポート ページ](media/sample-customer-profitability/customer6.png)

1. 業界によって収益性はどのように異なるでしょうか。 製品と顧客は業界別にどのように分類されるでしょうか。 これらの質問に回答するには、左上から 1 つまたは複数の業界を選択します (CPG 業界から始まっています)。 フィルターを消去するには、消しゴムのアイコンを選びます。

2. バブル チャート **[Revenue Var % to Budget, GM%, and RevenueTY by Industry]** で、CFO は最も大きなバブルを探します。収益に対する影響が最も大きいためです。 業界セグメント別の各マネージャーの影響を確認しやすくするには、面グラフ内の各マネージャーの名前を順番に選択することで、ページをフィルター処理します。

3. グラフで各マネージャーの名前を選択するときに、次の詳細を確認します。
   * Andrew が影響を与える領域は多数のさまざまな業界セグメントにまたがり、GM% (ほとんどの正の側) と Var% は大きく異なります。
   * Annelie のグラフは似ていますが、Annelie は少数の業界セグメントにのみ集中し、連邦政府セグメントと Gladius 製品に焦点を合わせています。
   * Carlos は明らかにサービスのセグメントに重点を置き、良好な収益を得ています。 Carlos はさらにハイテク セグメントで差異 % を大幅に向上させ、新しいセグメントである産業セグメントでは、予算に対して特に優れた業績を上げています。
   * Tina がいくつかのセグメントを担当し、最高の GM% を実現していますが、バブルのほとんどが小さいことは、企業の最終的な収益への影響が最小限であることを示しています。
   * Valery が扱っている製品は 1 つのみで、担当の業界セグメントはわずかに 5 つです。 Valery の業界への影響は季節的ですが常に大きなバブルを生み出すことは、会社の最終的な収益に大きな影響を与えていることを示します。 業界セグメントは、その業績が悪いことの説明になりますか。

### <a name="executive-scorecard"></a>役員スコアカード
このページには、カスタム ページ サイズ フォーマットがあります。

## <a name="dig-into-the-data-by-asking-questions-with-qa"></a>Q&A で質問をすることによるデータの詳しい考察
どの業界が Valery の最大の収益を生み出すかを判別することは分析に役立つ場合があります。 Q&A を利用してみましょう。

1. **[レポートの編集]** を選んで、編集ビューでレポートを開きます。 編集ビューは、自分がレポートを所有している場合にのみ使用できます。 このビューは、*作成者* モードと呼ばれることがあります。 自分がレポートを共有しているだけの場合は、編集ビューで開くことはできません。

2.  ダッシュボードの上部から、**[質問する]** を選択して Q&A 質問ボックスを開きます。

    ![データについて質問する](media/sample-customer-profitability/power-bi-ask-question.png)

3. 質問ボックスに「*total revenue by industry for Valery*」と入力します。 質問を入力するに従って視覚化が更新されることにご注意ください。

    ![質問ボックスに質問を入力する](media/sample-customer-profitability/power-bi-qna.png)

   ご覧のように、Valery にとって最大の売上領域は流通業界です。

### <a name="dig-deeper-by-adding-filters"></a>フィルターの追加による詳しい調査
流通業界を見てみましょう。  

1. **[Industry Margin Analysis]\(業界の利益分析\)** レポートのページを開きます。
2. レポート ページで視覚エフェクトが選択されていない状態で、(まだ展開されていない場合は) 右側のフィルター ウィンドウを展開します。 **フィルター** ペインには、**ページ レベル フィルター** のみが表示されます。  

   ![ページ レベル フィルター](media/sample-customer-profitability/power-bi-filters.png)
3. **[Industry]** フィルターを選択し、矢印を選択して一覧を展開します。 流通業界のページ フィルターを追加してみましょう。 まず **[Select All]** チェックボックスをオフにして、すべての選択を解除します。 次に、**[Distribution]** のみを選択します。  

   ![Distribution のフィルター](media/sample-customer-profitability/customer7.png)
4. **[月と役員別の粗利益]** グラフから、この業種の顧客を担当しているのは Valery と Tina だけであり、Valery がこの業種を担当していたのは 6 月から 11 月までの間だけであることがわかります。   
5. **[月と役員別の粗利益]** グラフの凡例で、**[Tina]**、**[Valery]** の順に選びます。 **[製品別の合計売上]** グラフの Tina の部分は、Valery と比較して小さいことに注意してください。
6. 実売上を確認するには、ダッシュボードで Q&A ボックスを選択して、「*total revenue by executive for distribution by scenario*」と入力します。  

     ![Q&A ボックスへの質問の入力](media/sample-customer-profitability/power-bi-qna2.png)

    同様に他の業界を調査して、視覚化に顧客を追加し、Valery の業績の原因を理解することもできます。

## <a name="next-steps-connect-to-your-data"></a>次の手順:データへの接続
変更内容を保存しないことを選択できるため、この環境で試してみるのは安全です。 一方、それらを保存した場合は、 **[データを取得]** を選択して、常にこのサンプルの新しいコピーを取得できます。

この記事から、Power BI ダッシュボード、Q&A、レポートからサンプル データの分析情報をどのように得られるかがご理解いただけたでしょうか。 次はあなたの番です。ご自分のデータに接続してみてください。 Power BI を使用すると、広範なデータ ソースに接続することができます。 詳細については、[Power BI サービスの概要](../fundamentals/service-get-started.md)に関するページを参照してください。
