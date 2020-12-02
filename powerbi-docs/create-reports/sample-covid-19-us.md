---
title: 米国の州政府および地方自治体向けの COVID-19 の追跡サンプル
description: COVID-19 のパンデミックに対する米国の州および地域のデータを使用したサンプル レポートをダウンロードして変更します。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: maggies
ms.custom: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 04/28/2020
LocalizationGroup: Samples
ms.openlocfilehash: e6f8e02efa7dc2e56a945aaffcf22d8497052404
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96396017"
---
# <a name="covid-19-tracking-sample-for-us-state-and-local-governments"></a>米国の州政府および地方自治体向けの COVID-19 の追跡サンプル

Power BI チームは COVID-19 の追跡サンプルを作成しました。これにより、米国の州政府および地方自治体が、COVID-19 に関する対話型レポートを発行したりカスタマイズしたりすることができます。 Power BI Desktop を使用すると、COVID-19 データを分析して視覚化し、都市、郡、州、および国の各レベルでコミュニティに絶えず情報を提供することができます。 次に Power BI Publish to Web を使用して、レポートを一般に共有し、市民に情報を提供することができます。 この記事では、独自のパブリック ストーリー、ブログ、または Web サイトで Power BI の対話型の視覚化を使用するためのさまざまなオプションを提供します。

:::image type="content" source="media/sample-covid-19-us/covid-19-us-tracking-sample.png" alt-text="米国のデータを使用した COVID-19 のサンプル":::

この記事では、次の方法について説明します。

- 埋め込みコードをコピーして、独自のサイトに配置する。 
- 特定の州の書式設定などのカスタマイズを行う。
- Power BI サービスに発行する。
- Web に公開する。 
- このデータを別のソースからのデータとマッシュアップする。 

## <a name="prerequisites"></a>前提条件

Power BI を使用して自分のストーリーを伝えるには、次の前提条件を満たしている必要があります。

- 無料の [Power BI Desktop](https://powerbi.microsoft.com/desktop/) アプリをダウンロードする
- [Power BI サービス](https://powerbi.microsoft.com/get-started/)にサインアップする

## <a name="option-1-pre-built-embed-code"></a>オプション 1:事前構築済みの埋め込みコード

Microsoft では、サンプル レポートを公開し、Web に公開する埋め込みコードを作成しました。 この埋め込みコードを使用して、独自の Web サイトに完全なサンプル (全米のビューを含む) を埋め込んで、州や郡のレベルにドリルダウンすることができます。 このデータを公開する前に、この記事にある[免責事項](#disclaimers)を確認することをお勧めします。

対話型グラフィックをご自分のサイトに追加するには、次の埋め込みコードをコピーして、Web ページ上のグラフィックを表示したい場所に貼り付けます。  

```
<iframe width="1600" height="900" src="https://app.powerbi.com/view?r=eyJrIjoiMmI2ZjExMzItZTcwNy00YmUwLWFlMTAtYTUxYzVjODZmYjA5IiwidCI6ImMxMzZlZWMwLWZlOTItNDVlMC1iZWFlLTQ2OTg0OTczZTIzMiIsImMiOjF9" frameborder="0" allowFullScreen="true"></iframe>
```

埋め込みコードは HTML iFrame 要素で、任意の HTML ページに挿入できます。 ご自分のサイト内に収まるように、提供された iFrame の幅と高さを調整します。 サンプル レポートは、16:9 の比率で作成されているため、この大きさを保持するサイズを選択します。 正しく実装されている場合、余分な灰色の枠なしでグラフィックが表示されます。 これらの変更を行う場合は、[iFrame のサイズ変更のヒントとテクニックを確認](../collaborate-share/service-publish-to-web.md#tips-for-iframe-height-and-width)すると役立ちます。

## <a name="option-2-customize-the-sample-power-bi-file"></a>オプション 2:サンプル Power BI ファイルのカスタマイズ

Power BI ファイルには、Power BI Desktop で編集できる .pbix ファイル形式のデータと対話型グラフィックが含まれています。  

一般的なカスタマイズでは、レポートを特定の州にフィルター処理してから、カスタマイズされたレポート用に独自の Web に公開する埋め込みコードを作成します。

USAFacts データは、帰属を必要とする Creative Commons ライセンスの下で提供されます。 このデータを公開する前に、[免責事項](#disclaimers)を確認してください。

開始するには、[こちらから](https://go.microsoft.com/fwlink/?linkid=2125058) .pbix ファイルをダウンロードします。

### <a name="update-your-report"></a>レポートを更新する 

1. まだダウンロードしていない場合、無料のアプリ [Power BI Desktop](https://powerbi.microsoft.com/desktop/) の最新バージョンをダウンロードします。 

2. まだダウンロードしていない場合は [.pbix ファイル](https://go.microsoft.com/fwlink/?linkid=2125058)をダウンロードし、Power BI Desktop で開きます。

3. レポートを特定の州にフィルター処理するには、矢印を選択して [フィルター] ペインを展開します。

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-filters-pane.png" alt-text="[フィルター] ペインを展開":::

4. 目的の州を選択します。 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-filter-selection.png" alt-text="州の選択":::

5. ファイルを保存するには、 **[ファイル]**  >  **[保存]** の順に選択します。 

### <a name="refresh-your-report"></a>レポートを更新する 

1. **[更新]** ボタンをクリックします。

    :::image type="content" source="media/sample-covid-19-us/power-bi-desktop-refresh-button.png" alt-text="[更新] ボタン":::

2. **[匿名]**  >  **[接続]** の順に選択します。 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-azure-blob.png" alt-text="[匿名] を選択":::

 
3. **プライバシー レベルを無視** が表示されている場合は選択して、 **[保存]** を選択します。 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-privacy-levels.png" alt-text="プライバシー レベルの選択":::

### <a name="publish-your-report-to-the-power-bi-service"></a>Power BI サービスにレポートを発行する

必要に応じてレポートをカスタマイズしたら、[こちら](../create-reports/desktop-upload-desktop-files.md)に記載されている手順に従って、レポートを Power BI サービスに発行します。

### <a name="configure-scheduled-refresh"></a>スケジュールされた更新の構成

レポートのデータを最新の状態に保つために、レポートを発行した後で、[スケジュールされた更新を構成](../connect-data/refresh-scheduled-refresh.md)することができます。

手順に従って、次のオプションを選択します。

1. データ ソース資格情報の認証方法:匿名
2. このデータ ソースのプライバシー レベルの設定:パブリック

更新設定をテストするには、データセット項目で使用できる、[[今すぐ更新]](../connect-data/refresh-data.md#data-refresh) オプションを選択します。

更新されたデータは、スケジュールが実行されるたびに読み込まれます。 基になるデータは USAFacts によって提供され、更新スケジュールと同じ頻度で更新されない場合があります。 基になるデータが最後に更新された日時を知るには、[USAFacts の Web サイト](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/)で確認してください。 

カスタマイズしたレポートを Web サイトに公開することを予定している場合は、スケジュールされた更新を、少なくとも USAFacts データ更新プログラムと同じ頻度で実行するように構成することをお勧めします。 USAFacts は毎日異なる時刻にデータを更新する可能性があるため、毎日数回の更新を構成することをお勧めします。 

### <a name="create-a-publish-to-web-embed-code"></a>Web に公開する埋め込みコードを作成する 

独自の Web サイトにカスタマイズしたレポートを埋め込むには、[独自の Web に公開する埋め込みコードの作成方法](../collaborate-share/service-publish-to-web.md#create-embed-codes-with-publish-to-web)の手順に従います。

埋め込みコードを公開したら、確認ダイアログの iFrame を使用して、ご自分の Web サイトに埋め込みます。

Power BI Desktop でレポートに変更を加えた場合は、Power BI サービス内の既存のレポートを発行して置き換えることができます。 埋め込みコードは変更されません。 レポートへの変更または更新されたデータが Web サイトに反映されるまで、約 1 時間かかります。 

## <a name="option-3-mash-up-data-from-another-source"></a>オプション 3:別のソースからデータをマッシュアップ 

このレポートのデータを別のソースのデータとマッシュアップすることもできます。 次の例は、[ジョンズ ホプキンス大学](https://github.com/CSSEGISandData/COVID-19)のデータに基づいています。 このデータを公開する前に、この記事にある[免責事項](#disclaimers)を確認することをお勧めします。

1. **[データを取得]**  >  **[Web]** の順に選択します。

    :::image type="content" source="media/sample-covid-19-us/power-bi-desktop-get-data.png" alt-text="[データを取得] ボタン":::

2. 次の URL を入力します。

    ```
    https://raw.githubusercontent.com/CSSEGISandData/COVID-19/master/csse_covid_19_data/csse_covid_19_time_series/time_series_covid19_confirmed_global.csv
    ```

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-from-web.png" alt-text="Web からデータを選択":::

3. **[OK]** を選択します。 

    > [!NOTE]
    > ジョンズ ホプキンス大学によって公開されたリンクは変更される可能性があります。 最新情報については、[Johns Hopkins GitHub ページ](https://github.com/CSSEGISandData/COVID-19)を確認してください。

4. **[読み込み]** を選択して、世界中の確認された症例の合計のデータセットを読み込みます。  

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-load-data.png" alt-text="Web からデータを読み込む":::

    「[Power BI Desktop から Web ページに接続する](../connect-data/desktop-connect-to-web.md)」の記事では、Web からデータを読み込む方法についてより詳しく説明されています。
    
次に、Power BI Desktop を使用してデータを視覚化できます。 最後に、「**オプション 2:** [Power BI サービスにレポートを発行する](#publish-your-report-to-the-power-bi-service)」の手順を使用して、レポートを発行し、カスタムの埋め込みコードを作成します。 

## <a name="option-4-use-the-covid-19-us-tracking-template-app"></a>オプション 4:COVID-19 US トラッキング テンプレートアプリを使用する

もう 1 つのオプションとして、Power BI チームでは、すぐに作業を開始するために COVID-19 US トラッキング "*テンプレート アプリ*" を作成しました。 テンプレート アプリは、特定のデータ ソースのレポート、ダッシュボード、データセットのバンドルです。 AppSource からダウンロードして使用するか、ニーズに合わせて変更し、同僚に配布します。 

この COVID-19 US トラッキング テンプレート アプリには、COVID-19 メトリックの事前に構築されたレポートが含まれています。これは、そのまま使用することも、Power BI サービスで直接、個人用に設定することも、必要に応じてダウンロードして他のデータ ソースを追加することもできます。 [COVID-19 US トラッキング テンプレート アプリ](../connect-data/service-connect-to-covid-19-tracking.md)をインストールし、すぐに使い始める方法について学習してください。

## <a name="about-the-data-source-for-this-report"></a>このレポートのデータ ソースについて
この対話型のレポートでは、アメリカ疾病管理予防センター (CDC) と、州および地方自治体レベルの公的な保健機関からのデータが集計されます。 郡レベルのデータは、州および地方自治体を直接参照 (リンク) することによって確認されます。

データは USAFacts によって提供されます。 データ更新の頻度により、政府機関またはニュース メディアによって報告された正確な数が反映されていない場合があります。 詳細情報またはデータのダウンロードについては、[USAFacts の Web サイト](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/)をご覧ください。 

## <a name="disclaimers"></a>免責事項

このレポートとデータは、"現状有姿" かつ "瑕疵を問わない" 条件で提供され、いかなる保証も与えられないものとします。 Microsoft は、明示的な瑕疵担保責任または保証責任を一切負いません。また、商品性、特定目的に対する適合性、非侵害性に関するいかなる黙示的保証も明示的に放棄します。

USAFacts データは、Creative Commons ライセンスの下で利用できます。 これを使用するには、データ プロバイダーとして USAFacts を明記し、USAFacts にリンクします。 正確な帰属の手順については、「 **#MadewithUSAFacts**」セクション (USAFacts ページ「[Coronavirus in the United States: Mapping the COVID-19 outbreak in the states and counties](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/)」 (米国におけるコロナウイルス: COVID-19 のアウトブレイクの州都郡へのマッピング)) を参照してください。

ジョンズ ホプキンス大学のデータの著作権: 2020 Johns Hopkins University, all rights reserved. これは、教育および学術研究目的でのみ、公に提供されています。 マッシュアップの例に示されているデータの完全な使用条件は、[こちら](https://github.com/CSSEGISandData/COVID-19/blob/master/README.md)をご覧ください。 詳細については、[ジョンズ ホプキンス大学の Web サイト](https://coronavirus.jhu.edu/map-faq.html)をご覧ください。

## <a name="next-steps"></a>次の手順

[Power BI のサンプルを入手する](../create-reports/sample-datasets.md)




