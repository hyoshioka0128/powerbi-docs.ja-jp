---
title: Power BI Desktop で図形マップを使用する (プレビュー)
description: Power BI Desktop で図形マップを使用して領域間の相対比較を作成する
author: mihart
ms.author: mihart
ms.reviewer: sujata
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: how-to
ms.date: 03/18/2020
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 99df17b35faedbebf81b7eb711870e6660dca9d4
ms.sourcegitcommit: 10dfa074558a78a82f44bdfa6228c07c7d860257
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/07/2021
ms.locfileid: "106549519"
---
# <a name="create-shape-map-visualizations-in-power-bi-desktop-preview"></a>Power BI Desktop で図形マップのビジュアルを作成する (プレビュー)

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

色を使用して、マップで領域を比較するために **[図形マップ]** ビジュアルを作成します。 **[マップ]** ビジュアルとは異なり、**[図形マップ]** ではマップ上の地理的な場所を正確には表示できません。 代わりに、これの主な用途は、違う色を適用することにより、マップ上の領域を相対的に比較できます。

**[図形マップ]** のビジュアルは TopoJSON マップをベースにしています。このマップの強みは、ユーザー作成のカスタム マップを使用できることです。 地理、座席配置、フロア プランなどがカスタム マップの例です。 

> [!NOTE]
> Power BI を使用する同僚とレポートを共有するには、それぞれのユーザーが個別の Power BI Pro ライセンスを持っているか、レポートが Premium 容量に保存されている必要があります。

## <a name="creating-shape-maps"></a>図形マップを作成する
このプレビュー リリースに付属するマップで **マップのシェイプ** コントロールをテストできます。あるいは、次のセクション (**カスタム マップの使用**) にある要件を満たす限り、独自のカスタム マップを使用できます。

**[マップのシェイプ]** のビジュアルは、プレビュー段階にあるため、Power BI Desktop でこれを有効にする作業が必要です。 **[マップのシェイプ]** を有効にするには、**[ファイル] > [オプションと設定] > [オプション] > [プレビュー機能]** の順に選択し、**[図形マップのビジュアル]** チェック ボックスをオンにします。 選択を行った後、Power BI Desktop を再起動する必要があります。

![[マップのシェイプ] プレビュー機能の有効化](media/desktop-shape-map/power-bi-preview-features.png)

**[マップのシェイプ]** が有効になったら、**[視覚化]** ウィンドウで **[マップのシェイプ]** アイコンを選択します。

![図形マップ用のテンプレートを選択する](media/desktop-shape-map/power-bi-shape-map-template2.png)

Power BI Desktop は、**[マップのシェイプ]** のビジュアルのデザイン キャンバスを作成します。

![自分のキャンバス上に空の図形マップが表示される](media/desktop-shape-map/shape-map-3.png)

次の手順に従って、**[マップのシェイプ]** を作成します。

1. **[フィールド]** ウィンドウで、地域名 (または省略形) が含まれているデータ フィールドを **[地域]** バケットにドラッグし、データ メジャー フィールドを **[色の彩度]** バケットにドラッグします (地図はまだ表示されません)。

   > [!NOTE]
   > **[マップのシェイプ]** ビジュアルのテストに使用できるサンプル マップ データを取得するには、後述する「**マップ データの取得**」というセクションを参照してください。
   > 
   > 

   ![自分の図形マップを作成する](media/desktop-shape-map/shape-map-3a.png)
2. **[形式]** 設定ウィンドウで、**[図形]** を展開し、**[標準マップ]** ドロップダウンから選択して、目的のデータを表示します。 この時点で、次の図に示すようにレンダリングが行われます。

   ![[書式設定] ウィンドウを開き、[図形] を選択する](media/desktop-shape-map/shape-map-3b-new.png)

   > [!NOTE]
   > この記事の最後に記載した「**地域キー**」セクションは、**[マップのシェイプ]** のビジュアルをテストするのに使用できる地図の地域キーが含まれる表のコレクションです。
   > 
   > 
3. **[既定の色]** や **[ズーム]** などの [書式設定] オプションを使用してマップを変更することができます。 また、カテゴリ データ列を **[凡例]** バケットに追加し、カテゴリに基づいて地図の地域を分類することもできます。

## <a name="use-custom-maps"></a>カスタム マップの使用
それが **TopoJSON** 形式であれば、**マップのシェイプ** でカスタム マップを使用できます。 マップが別の形式の場合、[**Map Shaper**](https://mapshaper.org/) などのオンライン ツールを使用し、*シェイプ ファイル* や *GeoJSON* マップを **TopoJSON** 形式に変換できます。

**TopoJSON** マップ ファイルを使用するには、ShapeMap ビジュアルをレポートに追加し、データを *[場所]* バケットと *[色の彩度]* バケットに追加します。 その後、**[視覚化]** ウィンドウで **[形式]** セクションを選択し (次の画像の (1))、**[図形]** セクションを展開し、**[+ マップの追加]** を選択します。

![[書式設定] ウィンドウを開き、[マップの追加] を選択する](media/desktop-shape-map/shape-map-6-new.png)

## <a name="sample-custom-map"></a>サンプル カスタム マップ
*米国連邦地検* は、訴訟および取扱件数データに関する年次会計報告を公表しました。  これらすべてのレポートは以下のリンクで確認できます。

https://www.justice.gov/usao/resources/annual-statistical-reports

州は複数の区に分けられるため、カスタム シェイプ マップを使用する必要があります。  米国司法管轄区の **TopoJSON** マップを **Power BI Desktop** にインポートすることで、地区検事長の年次会計報告データを視覚化できます。  次の画像はこのマップの例を示しています。

![ユーザー設定の図形マップ](media/desktop-shape-map/shape-map-7a.png)

個々の州マップについても、含まれる区に基づいて詳細を表示することができます。 

![テキサスの図形マップ](media/desktop-shape-map/shape-map-7b.png)

このデータセットと視覚エフェクトを試したい場合は、以下のリンクを使用して、このレポートの生成に使用された元の PBIX ファイルをダウンロードできます。

* [カスタム シェイプ マップのデモ .PBIX ファイル](https://download.microsoft.com/download/1/2/8/128943FB-9231-42BD-8A5D-5E2362C9D589/DistrictAttorneyFiscalReport.pbix)

## <a name="getting-map-data"></a>マップ データの取得
**[マップのシェイプ]** をテストできるようにモデルに迅速にデータを入力するには、**[ホーム]** リボンから **[データの入力]** を選択します。

![Desktop で、[データの入力] を選択する](media/desktop-shape-map/shape-map-4-new.png)

データに複数の列がある場合は、Excel などのエディターを使用してデータを貼り付け、各データ列を個別にコピーする必要があります。 このデータは Power BI Desktop に貼り付けることができます。 一番上の行は、自動的に見出しとして識別されます。

![[テーブルの作成] ウィンドウ](media/desktop-shape-map/shape-map-5.png)

新しい列は簡単に入力できます。新しい列名を入力し (右側の空の列に)、各セルに値を追加します。この方法は Excel で行う操作と同じです。 列の作成が完了したら、**[読み込み]** を選択します。表が Power BI Desktop のデータ モデルに追加されます。

> [!NOTE]
> 国または地域を扱うとき、3 文字の省略形を使用し、マップ視覚エフェクトでジオコーディングが正しく機能するようにします。 2 文字の省略形は *使用しない* でください。正しく認識されない国や地域があります。
> 
> 省略形が 2 文字しかない場合、[この外部ブログ投稿](https://blog.ailon.org/how-to-display-2-letter-country-data-on-a-power-bi-map-85fc738497d6#.yudauacxp)を参照してください。2 文字の国/地域コードを 3 文字の国/地域コードに関連付ける方法が紹介されています。
> 
> 

## <a name="preview-behavior-and-requirements"></a>プレビューの動作と要件
**[マップのシェイプ]** 機能を提供するこのプレビュー リリースには、いくつかの考慮事項と要件があります。

* **[マップのシェイプ]** のビジュアルは、プレビュー段階にあるため、Power BI Desktop でこれを有効にする作業が必要です。 **[マップのシェイプ]** を有効にするには、**[ファイル] > [オプションと設定] > [オプション] > [プレビュー機能]** の順に選択し、**[図形マップのビジュアル]** チェック ボックスをオンにします。
* 現時点で、**[凡例]** の分類が適切に機能するには、**[色の彩度]** バケットも設定されている必要があります。
* **マップのシェイプ** の最終リリース版には、現在選択されているマップのマップ キーが表示されるユーザー インターフェイスが搭載される予定です (最終リリースの日付は未定であり、**マップのシェイプ** はまだプレビュー段階です)。 このプレビュー リリースでは、この記事の次の「**地域キー**」セクションにある表のマップの地域キーを参照してください。
* **マップのシェイプ** ビジュアルで最大 1,500 個のデータ ポイントが描かれます。

## <a name="region-keys"></a>地域キー

このプレビュー リリースでは、次の **地域キー** を使用して、 **[マップのシェイプ]** をテストしてください。

### <a name="australia-states"></a>オーストラリア: 州

| ID | 省略形 | ISO | name | 郵便 |
| --- | --- | --- | --- | --- |
| au-wa |WA |AU-WA |西オーストラリア |WA |
| au-vic |Vic |AU-VIC |ビクトリア州 |VIC |
| au-tas |Tas |AU-TAS |タスマニア |TAS |
| au-sa |SA |AU-SA |南オーストラリア |SA |
| au-qld |Qld |AU-QLD |クイーンズランド |QLD |
| au-nt |NT |AU-NT |北部特別地域 |NT |
| au-nsw |NSW |AU-NSW |ニュー サウス ウェールズ州 |NSW |
| au-act |ACT |AU-ACT |オーストラリア首都特別地域 |ACT |

### <a name="austria-states"></a>オーストリア: 州

| ID | ISO | name | 名前 (英語) | 郵便 |
| --- | --- | --- | --- | --- |
| at-wi |AT-9 |Wien |ウィーン |WI |
| at-vo |AT-8 |Vorarlberg (フォアアールベルク) |Vorarlberg (フォアアールベルク) |VO |
| at-tr |AT-7 |Tirol |Tyrol (チロル) |TR |
| at-st |AT-6 |Steiermark |Styria (シュタイアーマルク) |ST |
| at-sz |AT-5 |Salzburg (ザルツブルク) |Salzburg (ザルツブルク) |SZ |
| at-oo |AT-4 |Oberösterreich |Upper Austria (オーバーエスターライヒ) |OO |
| at-no |AT-3 |Niederösterreich |Lower Austria (ニーダーエスターライヒ) |NO |
| at-ka |AT-2 |Kärnten |Carinthia (ケルンテン) |KA |
| at-bu |AT-1 |Burgenland (ブルゲンラント) |Burgenland (ブルゲンラント) |BU |

### <a name="brazil-states"></a>ブラジル: 州

| ID |
| --- |
| Tocantins |
| Pernambuco |
| Goias |
| Sergipe |
| サンパウロ |
| Santa Catarina |
| Roraima |
| Rondonia |
| Rio Grande do Sul |
| Rio Grande do Norte |
| Rio de Janeiro |
| Piaui |
| Parana |
| Paraiba |
| Para |
| Minas Gerais |
| Mato Grosso |
| Maranhao |
| Mato Grosso do Sul |
| Distrito Federal |
| Ceara |
| Espirito Santo |
| Bahia |
| Amazonas |
| Amapa |
| Alagoas |
| Acre |
| Litigated Zone 1 |
| Litigated Zone 2 |
| Litigated Zone 3 |
| Litigated Zone 4 |

### <a name="canada-provinces"></a>カナダ: 州

| ID | ISO | name | 郵便 |
| --- | --- | --- | --- |
| ca-nu |CA-NU |ヌナブト |NU |
| ca-nt |CA-NT |ノースウエスト準州 |NT |
| ca-yt |CA-YT |ユーコン |YT |
| ca-sk |CA-SK |サスカチュワン |SK |
| ca-qc |CA-QC |ケベック |QC |
| ca-pe |CA-PE |プリンス エドワード島 |PE |
| ca-on |CA-ON |オンタリオ |ON |
| ca-ns |CA-NS |ノバ スコシア |NS |
| ca-nl |CA-NL |ニューファンドランド・ラブラドール |NL |
| ca-nb |CA-NB |ニュー ブランズウィック |NB |
| ca-mb |CA-MB |マニトバ |MB |
| ca-bc |CA-BC |British Columbia |BC |
| ca-ab |CA-AB |Alberta |AB |

### <a name="france-regions"></a>フランス: 地域圏

| ID | name | 名前 (英語) |
| --- | --- | --- |
| Auvergne-Rhone-Alpes |  |  |
| Bourgogne-Franche-Comte |  |  |
| Bretagne |Bretagne |Brittany (ブルターニュ) |
| Centre-Val de Loire (サントル=ヴァル ド ロワール) |Centre-Val de Loire (サントル=ヴァル ド ロワール) |Centre-Val de Loire (サントル=ヴァル ド ロワール) |
| Corse |Corse |Corse (コルシカ島) |
| Grand Est |  |  |
| グアドループ | |   |
| Hauts-de-France |  |  |
| Ile-de-France (イル ド フランス) |Île-de-France |Ile-de-France (イル ド フランス) |
| La Reunion |  |  |
| マヨット  |  |  |
| Normandie (ノルマンディー) |Normandie (ノルマンディー) |  |
| Nouvelle-Aquitaine |  |  |
| Occitanie  |  |  |
| Pays de la Loire (ペイ ド ラ ロワール) |Pays de la Loire (ペイ ド ラ ロワール) |Pays de la Loire (ペイ ド ラ ロワール) |
| Provence-Alpes-Cote d'Azur (プロヴァンス=アルプ=コート ダジュール) |Provence-Alpes-Côte d'Azur |Provence-Alpes-Cote d'Azur (プロヴァンス=アルプ=コート ダジュール) |
|  |  |  |

### <a name="germany-states"></a>ドイツ: 州

| ID | ISO | name | 名前 (英語) | 郵便 |
| --- | --- | --- | --- | --- |
| de-be |DE-BE |ベルリン |ベルリン |BE |
| de-th |DE-TH |Thüringen |Thuringia (チューリンゲン) |TH |
| de-st |DE-ST |Sachsen-Anhalt |Saxony-Anhalt (ザクセン=アンハルト) |ST |
| de-sn |DE-SN |Sachsen |Saxony (サクソニー) |SN |
| de-mv |DE-MV |Mecklenburg-Vorpommern (メクレンブルク=フォアポンメルン) |Mecklenburg-Vorpommern (メクレンブルク=フォアポンメルン) |MV |
| de-bb |DE-BB |Brandenburg (ブランデンブルク) |Brandenburg (ブランデンブルク) |BB |
| de-sh |DE-SH |Schleswig-Holstein (シュレスウィヒ=ホルシュタイン) |Schleswig-Holstein (シュレスウィヒ=ホルシュタイン) |SH |
| de-sl |DE-SL |Saarland (ザールラント) |Saarland (ザールラント) |SL |
| de-rp |DE-RP |Rheinland-Pfalz |Rhineland-Palatinate (ラインラント=プファルツ) |RP |
| de-nw |DE-NW |Nordrhein-Westfalen |North Rhine-Westphalia (ノルトライン=ウェストファーレン) |NW |
| de-ni |DE-NI |Niedersachsen |Lower Saxony (ニーダーザクセン) |NI |
| de-he |DE-HE |Hessen |Hesse (ヘッセン) |HE |
| de-hh |DE-HH |ハンブルク |ハンブルク |HH |
| de-hb |DE-HB |Bremen |Bremen |HB |
| de-by |DE-BY |Bayern |Bavaria (バイエルン) |BY |
| de-bw |DE-BW |Baden-Württemberg |Baden-Wurttemberg (バーデン=ウュルテンベルク) |BW |

### <a name="ireland-counties"></a>アイルランド: 州

| ID |
| --- |
| Wicklow |
| Wexford |
| Westmeath |
| Waterford |
| Sligo |
| Tipperary |
| Roscommon |
| Offaly |
| Monaghan |
| Meath |
| Mayo |
| Louth |
| Longford |
| Limerick |
| Leitrim |
| Laoighis |
| Kilkenny |
| Kildare |
| Kerry |
| Galway |
| ダブリン |
| Donegal |
| Cork |
| Clare |
| Cavan |
| Carlow |

### <a name="italy-regions"></a>イタリア: 州

| ID | ISO | name | 名前 (英語) | 郵便 |
| --- | --- | --- | --- | --- |
| it-vn |IT-34 |Veneto |Veneto |VN |
| it-vd |IT-23 |Valle d'Aosta |Aosta Valley (ヴァッレ ダオスタ) |VD |
| it-um |IT-55 |Umbria |Umbria |UM |
| it-tt |IT-32 |Trentino-Alto Adige |Trentino-South Tyrol (トレンティーノ=アルト アディジェ) |TT |
| it-tc |IT-52 |Toscana |Tuscany (トスカナ) |TC |
| it-sc |IT-82 |Sicilia |Sicily (シチリア島) |SC |
| it-sd |IT-88 |Sardegna |Sardinia (サルディニア) |SD |
| it-pm |IT-21 |Piemonte |Piedmont (ピエモンテ) |PM |
| it-ml |IT-67 |Molise (モリーゼ) |Molise (モリーゼ) |ML |
| it-mh |IT-57 |Marche |Marche |MH |
| it-lm |IT-25 |Lombardia |Lombardy (ロンバルディア) |LM |
| it-lg |IT-42 |Liguria (リグリア) |Liguria (リグリア) |LG |
| it-lz |IT-62 |Lazio (ラツィオ) |Lazio (ラツィオ) |LZ |
| it-fv |IT-36 |Friuli-Venezia Giulia (フリウリ=ベネチア･ジュリア) |Friuli-Venezia Giulia (フリウリ=ベネチア･ジュリア) |FV |
| it-er |IT-45 |Emilia-Romagna (エミリア=ロマーニャ) |Emilia-Romagna (エミリア=ロマーニャ) |ER |
| it-cm |IT-72 |Campania (カンパニア) |Campania (カンパニア) |CM |
| it-lb |IT-78 |Calabria (カラブリア) |Calabria (カラブリア) |LB |
| it-bc |IT-77 |Basilicata |Basilicata |BC |
| it-pu |IT-75 |Apulia |Puglia (プーリア) |PU |
| it-ab |IT-65 |Abruzzo (アブルッツィ) |Abruzzo (アブルッツィ) |AB |

### <a name="mexico-states"></a>メキシコ: 州

| ID | 省略形 | ISO | name | 名前 (英語) | 郵便 |
| --- | --- | --- | --- | --- | --- |
| mx-zac |Zac. |MX-ZAC |Zacatecas (サカテカス) |Zacatecas (サカテカス) |ZA |
| mx-yuc |Yuc. |MX-YUC |Yucatán |Yucatan (ユカタン) |YU |
| mx-ver |Ver. |MX-VER |Veracruz (ベラクルス) |Veracruz (ベラクルス) |VE |
| mx-tla |Tlax. |MX-TLA |Tlaxcala |Tlaxcala |TL |
| mx-tam |Tamps. |MX-TAM |Tamaulipas |Tamaulipas |TM |
| mx-tab |Tab. |MX-TAB |Tabasco |Tabasco |TB |
| mx-son |Son. |MX-SON |Sonora (ソノラ) |Sonora (ソノラ) |SO |
| mx-sin |Sin. |MX-SIN |Sinaloa |Sinaloa |SI |
| mx-slp |S.L.P. |MX-SLP |San Luis Potosí |San Luis Potosi (サン ルイス ポトシ) |SL |
| mx-roo |Q.R. |MX-ROO |Quintana Roo (キンタナロー) |Quintana Roo (キンタナロー) |QR |
| mx-que |Qro. |MX-QUE |Querétaro |Queretaro (ケレタロ) |QE |
| mx-pue |Pue. |MX-PUE |Puebla |Puebla |PU |
| mx-oax |Oax. |MX-OAX |Oaxaca |Oaxaca |OA |
| mx-nle |N.L. |MX-NLE |Nuevo León |Nuevo Leon (ヌエボレオン) |NL |
| mx-nay |Nay. |MX-NAY |Nayarit |Nayarit |NA |
| mx-mor |Mor. |MX-MOR |Morelos |Morelos |MR |
| mx-mic |Mich. |MX-MIC |Michoacán |Michoacan (ミチョアカン) |MC |
| mx-mex |Méx. |MX-MEX |Estado de México |Mexico State (メヒコ) |MX |
| mx-jal |Jal. |MX-JAL |Jalisco |Jalisco |JA |
| mx-hid |Hgo. |MX-HID |Hidalgo |Hidalgo |HI |
| mx-gro |Gro. |MX-GRO |Guerrero |Guerrero |GR |
| mx-gua |Gto. |MX-GUA |Guanajuato |Guanajuato |GT |
| mx-dur |Dgo. |MX-DUR |Durango |Durango |DU |
| mx-dif |CDMX. |MX-DIF |Ciudad de México |Mexico City (メキシコシティー) |DF |
| mx-col |Col. |MX-COL |Colima |Colima |CL |
| mx-coa |Coah. |MX-COA |Coahuila |Coahuila |CA |
| mx-chh |Chih. |MX-CHH |Chihuahua |Chihuahua |CH |
| mx-chp |Chis. |MX-CHP |Chiapas |Chiapas |CP |
| mx-cam |Camp. |MX-CAM |Campeche (カンペチェ) |Campeche (カンペチェ) |CM |
| mx-bcs |B.C.S. |MX-BCS |Baja California Sur |Baja California Sur |BS |
| mx-bcn |B.C. |MX-BCN |Baja California |Baja California |BN |
| mx-agu |Ags. |MX-AGU |Aguascalientes |Aguascalientes |AG |

### <a name="netherlands-provinces"></a>オランダ: 州

| ID | ISO | name | 名前 (英語) |
| --- | --- | --- | --- |
| nl-zh |NL-ZH |Zuid-Holland |South Holland (南ホラント) |
| nl-ze |NL-ZE |Zeeland (ゼーラント) |Zeeland (ゼーラント) |
| nl-ut |NL-UT |Utrecht |Utrecht |
| nl-ov |NL-OV |Overijssel |Overijssel |
| nl-nh |NL-NH |Noord-Holland |North Holland (北ホラント) |
| nl-nb |NL-NB |Noord-Brabant |North Brabant (北ブラバント) |
| nl-li |NL-LI |Limburg |Limburg |
| nl-gr |NL-GR |Groningen (フローニンゲン) |Groningen (フローニンゲン) |
| nl-ge |NL-GE |Gelderland |Gelderland |
| nl-fr |NL-FR |Fryslân |Friesland (フリースラント) |
| nl-fl |NL-FL |Flevoland |Flevoland |
| nl-dr |NL-DR |Drenthe (ドレンテ) |Drenthe (ドレンテ) |

### <a name="uk-countries"></a>英国: 地方

| ID | ISO | name |
| --- | --- | --- |
| gb-wls |GB-WLS |Wales |
| gb-sct |GB-SCT |Scotland |
| gb-nir |GB-NIR |Northern Ireland |
| gb-eng |GB-ENG |England |

### <a name="usa-states"></a>米国: 州

| ID | name | 郵便 |
| --- | --- | --- |
| us-mi |ミシガン |MI |
| us-ak |アラスカ |AK |
| us-hi |ハワイ |HI |
| us-fl |フロリダ |FL |
| us-la |ルイジアナ |LA |
| us-ar |アーカンソー |AR |
| us-sc |サウスカロライナ |SC |
| us-ga |ジョージア |GA |
| us-ms |ミシシッピ |MS |
| us-al |アラバマ |AL |
| us-nm |ニューメキシコ |NM |
| us-tx |テキサス |TX |
| us-tn |テネシー |TN |
| us-nc |ノースカロライナ |NC |
| us-ok |オクラホマ |OK |
| us-az |アリゾナ |AZ |
| us-mo |ミズーリ |MO |
| us-va |バージニア州 |VA |
| us-ks |カンザス |KS |
| us-ky |ケンタッキー |KY |
| us-co |コロラド |CO |
| us-md |メリーランド |MD |
| us-wv |ウェストバージニア |WV |
| us-de |デラウェア |DE |
| us-dc |ワシントン D.C. |DC |
| us-il |イリノイ州 |IL |
| us-oh |オハイオ |OH |
| us-ca |カリフォルニア |CA |
| us-ut |ユタ |UT |
| us-nv |ネバダ |NV |
| us-in |インディアナ |IN |
| us-nj |ニュージャージー |NJ |
| us-ri |ロードアイランド |予約インスタンス |
| us-ct |コネチカット |CT |
| us-pa |ペンシルベニア |PA |
| us-ny |ニューヨーク |NY |
| us-ne |ネブラスカ |NE |
| us-ma |マサチューセッツ |MA |
| us-ia |アイオワ州 |IA |
| us-nh |ニューハンプシャー |NH |
| us-or |オレゴン |OR |
| us-mn |ミネソタ |MN |
| us-vt |バーモント |VT |
| us-id |アイダホ |ID |
| us-wi |ウィスコンシン |WI |
| us-wy |ワイオミング |WY |
| us-sd |サウスダコタ |SD |
| us-nd |ノースダコタ |ND |
| us-me |Maine |ME |
| us-mt |モンタナ |MT |
| us-wa |ワシントン |WA |

## <a name="next-steps"></a>次のステップ

* [Power BI のマトリックス ビジュアル](desktop-matrix-visual.md)

* [Power BI での視覚化の種類](power-bi-visualization-types-for-reports-and-q-and-a.md)
