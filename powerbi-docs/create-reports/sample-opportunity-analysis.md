---
title: Power BI の営業案件の分析のサンプル:ツアーを開始する
description: Power BI の営業案件の分析のサンプル:ツアーを開始する
author: maggiesMSFT
ms.author: maggies
ms.reviewer: amac
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 07/02/2019
LocalizationGroup: Samples
ms.openlocfilehash: 63bbbedd24facfdd485f14b96eb608efc001dd55
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96395810"
---
# <a name="opportunity-analysis-sample-for-power-bi-take-a-tour"></a>Power BI の営業案件の分析のサンプル:ツアーを開始する

営業案件の分析のサンプル コンテンツ パックには、"*直接*" と "*パートナー*" という 2 つの販売チャネルを持つソフトウェア企業向けのダッシュボード、レポート、データセットが含まれています。 地域、案件のサイズ、チャネル別に営業案件と売上を追跡するために、セールス マネージャーがこのダッシュボードを作成しました。

このサンプルでは、次の 2 つの売上メジャーを利用します。

* 収益:売上高に関する営業担当者の予測です。
* 実売上:売上と見込み % を乗算して算出され、実際の営業売上のより正確な予測値として使用されます。 見込みは商談の現在の "*営業段階*" によって率が決まります。
  * 潜在顧客:10%  
  * 見込みあり:20%  
  * 解決方法:40%  
  * 提案:60%  
  * 最終:80%

![営業案件の分析のサンプルのダッシュボード](media/sample-opportunity-analysis/opportunity1.png)

このサンプルは、ビジネス用のデータ、レポート、ダッシュボードを用いて Power BI を使う方法について説明するシリーズの一部です。 匿名化された実際のデータを使用し、[obviEnce](http://www.obvience.com/) によって作成されています。 データは複数の形式 (コンテンツ パック、Power BI Desktop の .pbix ファイル、Excel ブック) で使用できます。 [Power BI 用のサンプル](sample-datasets.md)を参照してください。 

このチュートリアルでは、Power BI サービス内の営業案件の分析のサンプル コンテンツ パックを調べます。 Power BI Desktop とサービスのレポート エクスペリエンスは似ているので、Power BI Desktop 内のサンプルの .pbix ファイルを使用して作業することもできます。 

Power BI Desktop 内でサンプルを調べるために Power BI ライセンスは不要です。 Power BI Pro ライセンスを持っていない場合は、Power BI サービス内で、マイ ワークスペースにサンプルを保存できます。 

## <a name="get-the-sample"></a>サンプルを入手する

このサンプルを使用するには、事前にサンプルを[コンテンツ パック](#get-the-content-pack-for-this-sample)、[.pbix ファイル](#get-the-pbix-file-for-this-sample)、または [Excel ブック](#get-the-excel-workbook-for-this-sample)としてダウンロードしておく必要があります。

### <a name="get-the-content-pack-for-this-sample"></a>このサンプルのコンテンツ パックを入手する

1. Power BI サービス (app.powerbi.com) を開いてサインインし、サンプルを保存するワークスペースを開きます。 

    Power BI Pro ライセンスを持っていない場合は、マイ ワークスペースにサンプルを保存できます。

2. 左下隅にある **[データを取得]** を選びます。

    ![[データを取得] を選択](media/sample-datasets/power-bi-get-data.png)
3. 表示された **[データを取得]** ページで、 **[サンプル]** を選びます。

4. **[営業案件の分析のサンプル]** を選択し、 **[接続]** を選択します。  

   ![サンプルに接続](media/sample-opportunity-analysis/opportunity-connect.png)
5. Power BI によってコンテンツ パックがインポートされ、新しいダッシュボード、レポート、およびデータセットが現在のワークスペースに追加されます。

   ![営業案件の分析のサンプル エントリ](media/sample-opportunity-analysis/opportunity-entry.png)

### <a name="get-the-pbix-file-for-this-sample"></a>このサンプルの .pbix ファイルを取得する

あるいは、Power BI Desktop で使用するために設計された [.pbix ファイル](https://download.microsoft.com/download/9/1/5/915ABCFA-7125-4D85-A7BD-05645BD95BD8/Opportunity%20Analysis%20Sample%20PBIX.pbix)として、営業案件の分析のサンプルをダウンロードすることもできます。

### <a name="get-the-excel-workbook-for-this-sample"></a>このサンプルの Excel ブックを取得する

このサンプルのデータ ソースを確認する場合は、[Excel ブック](https://go.microsoft.com/fwlink/?LinkId=529782) として入手することもできます。 ブックには、表示および変更可能な Power View シートが含まれています。 生データを表示するには、データ分析アドインを有効にし、 **[PowerPivot] > [管理]** を選択します。 Power View および Power Pivot のアドインを有効にするための詳細については、[Excel での Excel のサンプルの確認](sample-datasets.md#explore-excel-samples-inside-excel)に関するセクションを参照してください。

## <a name="what-is-our-dashboard-telling-us"></a>ダッシュボードからわかること
セールス マネージャーは、自分にとって最も重要なメトリックを追跡するためにダッシュボードを作成しました。 何か興味深いものがある場合は、タイルを選んで詳しいデータを確認できます。

- 企業収益は 20 億ドルで、要因を考慮した収益は 4 億 6,100 万ドルです。
- 営業案件数と売上はなじみ深いじょうごパターンに従います。合計は各段階で減少します。
- 営業案件のほとんどは東部地域で発生しています。
- 大規模な営業案件は中小規模の営業案件によりも多額の売上をもたらします。
- パートナーの大規模案件はより多くの売上を生み出します。平均で 800 万ドル、直接販売が 600 万ドルです。

契約を獲得するための労力は取引が大、中、小のいずれに分類されたかにかかわらず同じです。大型の営業案件をより詳しく調べるためにデータを分析する必要があります。

1. サンプルを保存したワークスペースで、 **[ダッシュボード]** タブを開き、 **[営業案件の分析のサンプル]** ダッシュボードを探してそれを選択します。

2. **[Opportunity Count by Partner Driven, Sales Stage]\(パートナー主導の営業案件数、営業段階)** タイルを選んで、[営業案件の分析のサンプル] レポートの最初のページを開きます。 

    ![[Opportunity Count by Partner Driven, Sales Stage]\(パートナー主導の営業案件数、営業段階)\ タイル](media/sample-opportunity-analysis/opportunity2.png)

## <a name="explore-the-pages-in-the-report"></a>レポート内のページの調査

下部のページ タブを選択して、レポート内の各ページを表示します。

### <a name="opportunity-count-overview-page"></a>[Opportunity Count Overview]\(営業案件数の概要\) ページ
![[営業案件数] ページ](media/sample-opportunity-analysis/opportunity3.png)

次の詳細に注意します。
* 営業案件数の観点では、東部が最大の地域です。  
* **[Opportunity Count by Region]\(地域別の営業案件数\)** 円グラフで、各地域を順番に選択して地域別のページをフィルター処理します。 各地域で、パートナーはより多くの大規模案件を追求していることに注目してください。   
* **[Opportunity Count by Partner Driven and Opportunity Size]\(パートナー主導別の営業案件と営業案件サイズ\)** 縦棒グラフに、大規模案件のほとんどがパートナー主導であり、中小規模案件の多くがパートナー主導でないことが示されます。
* **[営業段階別の営業案件数]** 横棒グラフで、各 **営業段階** を順番に選択して地域別数の相違を確認します。 東部地域の営業案件数が最大ですが、ソリューション、提案、最終の営業段階では、この 3 つの地域すべてにおいて数が同等であることに注目してください。 この結果は、中部と西部の地域ではより高い割合で契約を獲得していることを意味します。

### <a name="revenue-analysis-page"></a>[Revenue Analysis]\(売上分析\) ページ
このページでも同様にデータを観察しますが、数ではなく収益の分析観点を使用します。  

![[収益の概要] ページ](media/sample-opportunity-analysis/opportunity4.png)

次の詳細に注意します。
* 東部は営業案件数だけでなく、収益の面でも最大の地域です。  
* **[パートナー主導]** に **[はい]** を選択して **[Revenue by Sales Stage and Partner Driven]\(営業段階およびパートナー主導別の収益\)** をフィルター処理した場合、15 億ドルの収益と 2 億 9,400 万ドルの実売上が表示されます。 これらの金額を、パートナー主導でない収益である 6 億 4,400 万ドルおよび 1 億 6,600 万ドルと比較します。 
* 案件がパートナー主導の場合の大規模取引の平均収益は 800 万で、パートナー主導でないビジネスの 600 万よりも高額です。  
* パートナー主導ビジネスの場合、大規模な営業案件の平均収益は中小規模の営業案件の平均収益のほぼ 2 倍です。  
* 中小企業の平均売上は、パートナー主導と非パートナー主導の両方のビジネスで同等です。   

明らかにパートナーは、非パートナーより高い割合で顧客への販売を成功させています。 より多くの取引をパートナー経由にすることは合理的であると考えられます。

### <a name="opportunity-count-by-region-and-stage"></a>地域と段階別の営業案件数
レポートのこのページでは、前のページのデータと同様のデータを考察しますが、地域と段階によって分類します。 

![[地域段階数] ページ](media/sample-opportunity-analysis/opportunity5.png)

次の詳細に注意します。
* **[Opportunity Count by Region]\(地域別の営業案件数\)** 円グラフ内で **[東部]** を選択して東部地域でフィルター処理すると、この地域内の営業案件がパートナー主導と非パートナー主導にほぼ均等に分割されることがわかります。
* 中部地域で最も一般的なのは大規模案件、東部地域で最も一般的なのは小規模案件、西部地域で最も一般的なのは中規模案件です。

### <a name="upcoming-opportunities-by-month-page"></a>[Upcoming Opportunities by Month]\(月別の今後の営業案件\) ページ
このページでも同様の要因を考察しますが、日付と時刻の分析観点から考察します。 
 
![[今後の営業案件] ページ](media/sample-opportunity-analysis/opportunity6.png)

CFO はこのページを使用して、ワークロードを管理します。 収益案件を営業段階と月別に見ることにより、適切な計画が可能になります。

次の詳細に注意します。
* 最終営業段階の平均売上は最高です。 これらの契約を獲得することは最重要課題です。
* 月によってフィルター処理する ( **[月]** スライサーで月を選ぶ) と、最終営業段階の大規模取引の割合が高いのは 1 月で、実売上が 7,500 万ドルであることがわかります。 その一方で、2 月は、解決と提案の営業段階でほとんどが中規模取引になっています。
* 一般に、要因を考慮した売上の値は、営業段階、営業案件の数、取引サイズによって変化します。 右側の **[フィルター]** ペインを使用して、これらの要因のフィルターを追加し、さらに分析情報を検出します。

## <a name="next-steps-connect-to-your-data"></a>次の手順:データへの接続
変更内容を保存しないことを選択できるため、この環境で試してみるのは安全です。 一方、それらを保存した場合は、 **[データを取得]** を選択して、常にこのサンプルの新しいコピーを取得できます。

この記事から、Power BI ダッシュボード、Q&A、レポートからサンプル データの分析情報をどのように得られるかがご理解いただけたでしょうか。 次はあなたの番です。ご自分のデータに接続してみてください。 Power BI を使用すると、広範なデータ ソースに接続することができます。 詳細については、[Power BI サービスの概要](../fundamentals/service-get-started.md)に関するページを参照してください。
