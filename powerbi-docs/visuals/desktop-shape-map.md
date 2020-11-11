---
title: Power BI Desktop で図形マップを使用する (プレビュー)
description: Power BI Desktop で図形マップを使用して領域間の相対比較を作成する
author: msftrien
ms.reviewer: sujata
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 03/18/2020
ms.author: rien
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 6ecf39926c759d202c034e5cb196067b9ca378d0
ms.sourcegitcommit: 5ccab484cf3532ae3a16acd5fc954b7947bd543a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2020
ms.locfileid: "93411316"
---
# <a name="create-shape-map-visualizations-in-power-bi-desktop-preview"></a>Power BI Desktop で図形マップのビジュアルを作成する (プレビュー)

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

色を使用して、マップで領域を比較するために **[図形マップ]** ビジュアルを作成します。 **[マップ]** ビジュアルとは異なり、 **[図形マップ]** ではマップ上の地理的な場所を正確には表示できません。 代わりに、これの主な用途は、違う色を適用することにより、マップ上の領域を相対的に比較できます。

**[図形マップ]** のビジュアルは TopoJSON マップをベースにしています。このマップの強みは、ユーザー作成のカスタム マップを使用できることです。 地理、座席配置、フロア プランなどがカスタム マップの例です。 カスタム マップを利用する機能は、このプレビュー リリースの **マップのシェイプ** では使用できません。

> [!NOTE]
> Power BI を使用する同僚とレポートを共有するには、それぞれのユーザーが個別の Power BI Pro ライセンスを持っているか、レポートが Premium 容量に保存されている必要があります。

## <a name="creating-shape-maps"></a>図形マップを作成する
このプレビュー リリースに付属するマップで **マップのシェイプ** コントロールをテストできます。あるいは、次のセクション ( **カスタム マップの使用** ) にある要件を満たす限り、独自のカスタム マップを使用できます。

**[マップのシェイプ]** のビジュアルは、プレビュー段階にあるため、Power BI Desktop でこれを有効にする作業が必要です。 **[マップのシェイプ]** を有効にするには、 **[ファイル] > [オプションと設定] > [オプション] > [プレビュー機能]** の順に選択し、 **[図形マップのビジュアル]** チェック ボックスをオンにします。 選択を行った後、Power BI Desktop を再起動する必要があります。

![[マップのシェイプ] プレビュー機能の有効化](media/desktop-shape-map/power-bi-preview-features.png)

**[マップのシェイプ]** が有効になったら、 **[視覚化]** ウィンドウで **[マップのシェイプ]** アイコンを選択します。

![図形マップ用のテンプレートを選択する](media/desktop-shape-map/power-bi-shape-map-template2.png)

Power BI Desktop は、 **[マップのシェイプ]** のビジュアルのデザイン キャンバスを作成します。

![自分のキャンバス上に空の図形マップが表示される](media/desktop-shape-map/shape-map-3.png)

次の手順に従って、 **[マップのシェイプ]** を作成します。

1. **[フィールド]** ウィンドウで、地域名 (または省略形) が含まれているデータ フィールドを **[地域]** バケットにドラッグし、データ メジャー フィールドを **[色の彩度]** バケットにドラッグします (地図はまだ表示されません)。

   > [!NOTE]
   > **[マップのシェイプ]** をテストするためのマップ データを迅速に取得する方法については、後述する「 **マップ データの取得** 」セクションを参照してください。
   > 
   > 

   ![自分の図形マップを作成する](media/desktop-shape-map/shape-map-3a.png)
2. **[形式]** 設定ウィンドウで、 **[図形]** を展開し、 **[標準マップ]** ドロップダウンから選択して、目的のデータを表示します。 この時点で、次の図に示すようにレンダリングが行われます。

   ![[書式設定] ウィンドウを開き、[図形] を選択する](media/desktop-shape-map/shape-map-3b-new.png)

   > [!NOTE]
   > この記事の最後に記載した「 **地域キー** 」セクションは、 **[マップのシェイプ]** のビジュアルをテストするのに使用できる地図の地域キーが含まれる表のコレクションです。
   > 
   > 
3. **[既定の色]** や **[ズーム]** などの [書式設定] オプションを使用してマップを変更することができます。 また、カテゴリ データ列を **[凡例]** バケットに追加し、カテゴリに基づいて地図の地域を分類することもできます。

## <a name="use-custom-maps"></a>カスタム マップの使用
それが **TopoJSON** 形式であれば、 **マップのシェイプ** でカスタム マップを使用できます。 マップが別の形式の場合、 [**Map Shaper**](https://mapshaper.org/) などのオンライン ツールを使用し、 *シェイプ ファイル* や *GeoJSON* マップを **TopoJSON** 形式に変換できます。

**TopoJSON** マップ ファイルを使用するには、ShapeMap ビジュアルをレポートに追加し、データを *[場所]* バケットと *[色の彩度]* バケットに追加します。 その後、 **[視覚化]** ウィンドウで **[形式]** セクションを選択し (次の画像の (1))、 **[図形]** セクションを展開し、 **[+ マップの追加]** を選択します。

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
**[マップのシェイプ]** をテストできるようにモデルに迅速にデータを入力するには、 **[ホーム]** リボンから **[データの入力]** を選択します。

![Desktop で、[データの入力] を選択する](media/desktop-shape-map/shape-map-4-new.png)

データに複数の列がある場合は、Excel などのエディターを使用してデータを貼り付け、各データ列を個別にコピーする必要があります。 このデータは Power BI Desktop に貼り付けることができます。 一番上の行は、自動的に見出しとして識別されます。

![[テーブルの作成] ウィンドウ](media/desktop-shape-map/shape-map-5.png)

新しい列は簡単に入力できます。新しい列名を入力し (右側の空の列に)、各セルに値を追加します。この方法は Excel で行う操作と同じです。 列の作成が完了したら、 **[読み込み]** を選択します。表が Power BI Desktop のデータ モデルに追加されます。

> [!NOTE]
> 国または地域を扱うとき、3 文字の省略形を使用し、マップ視覚エフェクトでジオコーディングが正しく機能するようにします。 2 文字の省略形は *使用しない* でください。正しく認識されない国や地域があります。
> 
> 省略形が 2 文字しかない場合、[この外部ブログ投稿](https://blog.ailon.org/how-to-display-2-letter-country-data-on-a-power-bi-map-85fc738497d6#.yudauacxp)を参照してください。2 文字の国/地域コードを 3 文字の国/地域コードに関連付ける方法が紹介されています。
> 
> 

## <a name="preview-behavior-and-requirements"></a>プレビューの動作と要件
**[マップのシェイプ]** 機能を提供するこのプレビュー リリースには、いくつかの考慮事項と要件があります。

* **[マップのシェイプ]** のビジュアルは、プレビュー段階にあるため、Power BI Desktop でこれを有効にする作業が必要です。 **[マップのシェイプ]** を有効にするには、 **[ファイル] > [オプションと設定] > [オプション] > [プレビュー機能]** の順に選択し、 **[図形マップのビジュアル]** チェック ボックスをオンにします。
* 現時点で、 **[凡例]** の分類が適切に機能するには、 **[色の彩度]** バケットも設定されている必要があります。
* **マップのシェイプ** の最終リリース版には、現在選択されているマップのマップ キーが表示されるユーザー インターフェイスが搭載される予定です (最終リリースの日付は未定であり、 **マップのシェイプ** はまだプレビュー段階です)。 このプレビュー リリースでは、この記事の次の「 **地域キー** 」セクションにある表のマップの地域キーを参照してください。
* **マップのシェイプ** ビジュアルで最大 1,500 個のデータ ポイントが描かれます。

## <a name="region-keys"></a>地域キー

このプレビュー リリースでは、次の **地域キー** を使用して、 **[マップのシェイプ]** をテストしてください。

### <a name="australia-states"></a>オーストラリア:州

| ID | 省略形 | ISO | name | 郵便 |
| --- | --- | --- | --- | --- |
| au-wa |WA |AU-WA |Western Australia |WA |
| au-vic |Vic |AU-VIC |Victoria |VIC |
| au-tas |Tas |AU-TAS |Tasmania |TAS |
| au-sa |SA |AU-SA |South Australia |SA |
| au-qld |Qld |AU-QLD |Queensland |QLD |
| au-nt |NT |AU-NT |Northern Territory |NT |
| au-nsw |NSW |AU-NSW |New South Wales |NSW |
| au-act |ACT |AU-ACT |Australian Capital Territory |ACT |

### <a name="austria-states"></a>オーストリア:州

| ID | ISO | name | 名前 (英語) | 郵便 |
| --- | --- | --- | --- | --- |
| at-wi |AT-9 |Wien |Vienna (ウィーン) |WI |
| at-vo |AT-8 |Vorarlberg |Vorarlberg (フォアアールベルク) |VO |
| at-tr |AT-7 |Tirol |Tyrol (チロル) |TR |
| at-st |AT-6 |Steiermark |Styria (シュタイアーマルク) |ST |
| at-sz |AT-5 |Salzburg |Salzburg (ザルツブルク) |SZ |
| at-oo |AT-4 |Oberösterreich |Upper Austria (オーバーエスターライヒ) |OO |
| at-no |AT-3 |Niederösterreich |Lower Austria (ニーダーエスターライヒ) |NO |
| at-ka |AT-2 |Kärnten |Carinthia (ケルンテン) |KA |
| at-bu |AT-1 |Burgenland |Burgenland (ブルゲンラント) |BU |

### <a name="brazil-states"></a>ブラジル:州

| ID |
| --- |
| Tocantins |
| Pernambuco |
| Goias |
| Sergipe |
| Sao Paulo |
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

### <a name="canada-provinces"></a>カナダ:州

| ID | ISO | name | 郵便 |
| --- | --- | --- | --- |
| ca-nu |CA-NU |Nunavut |NU |
| ca-nt |CA-NT |Northwest Territories |NT |
| ca-yt |CA-YT |Yukon |YT |
| ca-sk |CA-SK |Saskatchewan |SK |
| ca-qc |CA-QC |Quebec |QC |
| ca-pe |CA-PE |Prince Edward Island |PE |
| ca-on |CA-ON |Ontario |ON |
| ca-ns |CA-NS |Nova Scotia |NS |
| ca-nl |CA-NL |Newfoundland and Labrador |NL |
| ca-nb |CA-NB |New Brunswick |NB |
| ca-mb |CA-MB |Manitoba |MB |
| ca-bc |CA-BC |British Columbia |BC |
| ca-ab |CA-AB |Alberta |AB |

### <a name="france-regions"></a>フランス:Regions

| ID | name | 名前 (英語) |
| --- | --- | --- |
| Auvergne-Rhone-Alpes |  |  |
| Bourgogne-Franche-Comte |  |  |
| Bretagne |Bretagne |Brittany (ブルターニュ) |
| Centre-Val de Loire (サントル=ヴァル ド ロワール) |Centre-Val de Loire |Centre-Val de Loire (サントル=ヴァル ド ロワール) |
| Corse |Corse |Corse (コルシカ島) |
| Grand Est |  |  |
| Guadeloupe | |   |
| Hauts-de-France |  |  |
| Ile-de-France (イル ド フランス) |Île-de-France |Ile-de-France (イル ド フランス) |
| La Reunion |  |  |
| Mayotte  |  |  |
| Normandie (ノルマンディー) |Normandie (ノルマンディー) |  |
| Nouvelle-Aquitaine |  |  |
| Occitanie  |  |  |
| Pays de la Loire |Pays de la Loire |Pays de la Loire |
| Provence-Alpes-Cote d'Azur |Provence-Alpes-Côte d'Azur |Provence-Alpes-Cote d'Azur |
|  |  |  |

### <a name="germany-states"></a>ドイツ:州

| ID | ISO | name | 名前 (英語) | 郵便 |
| --- | --- | --- | --- | --- |
| de-be |DE-BE |Berlin |Berlin (ベルリン) |BE |
| de-th |DE-TH |Thüringen |Thuringia (チューリンゲン) |TH |
| de-st |DE-ST |Sachsen-Anhalt |Saxony-Anhalt (ザクセン=アンハルト) |ST |
| de-sn |DE-SN |Sachsen |Saxony (サクソニー) |SN |
| de-mv |DE-MV |Mecklenburg-Vorpommern |Mecklenburg-Vorpommern (メクレンブルク=フォアポンメルン) |MV |
| de-bb |DE-BB |Brandenburg |Brandenburg (ブランデンブルク) |BB |
| de-sh |DE-SH |Schleswig-Holstein |Schleswig-Holstein (シュレスウィヒ=ホルシュタイン) |SH |
| de-sl |DE-SL |Saarland |Saarland (ザールラント) |SL |
| de-rp |DE-RP |Rheinland-Pfalz |Rhineland-Palatinate (ラインラント=プファルツ) |RP |
| de-nw |DE-NW |Nordrhein-Westfalen |North Rhine-Westphalia (ノルトライン=ウェストファーレン) |NW |
| de-ni |DE-NI |Niedersachsen |Lower Saxony (ニーダーザクセン) |NI |
| de-he |DE-HE |Hessen |Hesse (ヘッセン) |HE |
| de-hh |DE-HH |Hamburg |Hamburg (ハンブルク) |HH |
| de-hb |DE-HB |Bremen |Bremen (ブレーメン) |HB |
| de-by |DE-BY |Bayern |Bavaria (バイエルン) |BY |
| de-bw |DE-BW |Baden-Württemberg |Baden-Wurttemberg (バーデン=ウュルテンベルク) |BW |

### <a name="ireland-counties"></a>アイルランド:郡

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
| Dublin |
| Donegal |
| Cork |
| Clare |
| Cavan |
| Carlow |

### <a name="italy-regions"></a>イタリア:Regions

| ID | ISO | name | 名前 (英語) | 郵便 |
| --- | --- | --- | --- | --- |
| it-vn |IT-34 |Veneto |Veneto (ベネト) |VN |
| it-vd |IT-23 |Valle d'Aosta |Aosta Valley (ヴァッレ ダオスタ) |VD |
| it-um |IT-55 |Umbria |Umbria (ウンブリア) |UM |
| it-tt |IT-32 |Trentino-Alto Adige |Trentino-South Tyrol (トレンティーノ=アルト アディジェ) |TT |
| it-tc |IT-52 |Toscana |Tuscany (トスカナ) |TC |
| it-sc |IT-82 |Sicilia |Sicily (シチリア島) |SC |
| it-sd |IT-88 |Sardegna |Sardinia (サルディニア) |SD |
| it-pm |IT-21 |Piemonte |Piedmont (ピエモンテ) |PM |
| it-ml |IT-67 |Molise |Molise (モリーゼ) |ML |
| it-mh |IT-57 |Marche |Marche (マルケ) |MH |
| it-lm |IT-25 |Lombardia |Lombardy (ロンバルディア) |LM |
| it-lg |IT-42 |Liguria |Liguria (リグリア) |LG |
| it-lz |IT-62 |Lazio |Lazio (ラツィオ) |LZ |
| it-fv |IT-36 |Friuli-Venezia Giulia |Friuli-Venezia Giulia (フリウリ=ベネチア･ジュリア) |FV |
| it-er |IT-45 |Emilia-Romagna |Emilia-Romagna (エミリア=ロマーニャ) |ER |
| it-cm |IT-72 |Campania |Campania (カンパニア) |CM |
| it-lb |IT-78 |Calabria |Calabria (カラブリア) |LB |
| it-bc |IT-77 |Basilicata |Basilicata (バシリカータ) |BC |
| it-pu |IT-75 |Apulia |Puglia (プーリア) |PU |
| it-ab |IT-65 |Abruzzo |Abruzzo (アブルッツィ) |AB |

### <a name="mexico-states"></a>メキシコ:州

| ID | 省略形 | ISO | name | 名前 (英語) | 郵便 |
| --- | --- | --- | --- | --- | --- |
| mx-zac |Zac. |MX-ZAC |Zacatecas |Zacatecas (サカテカス) |ZA |
| mx-yuc |Yuc. |MX-YUC |Yucatán |Yucatan (ユカタン) |YU |
| mx-ver |Ver. |MX-VER |Veracruz |Veracruz (ベラクルス) |VE |
| mx-tla |Tlax. |MX-TLA |Tlaxcala |Tlaxcala (トラスカラ) |TL |
| mx-tam |Tamps. |MX-TAM |Tamaulipas |Tamaulipas (タマウリパス) |TM |
| mx-tab |Tab. |MX-TAB |Tabasco |Tabasco (タバスコ) |TB |
| mx-son |Son. |MX-SON |Sonora |Sonora (ソノラ) |SO |
| mx-sin |Sin. |MX-SIN |Sinaloa |Sinaloa (シナロア) |SI |
| mx-slp |S.L.P. |MX-SLP |San Luis Potosí |San Luis Potosi (サン ルイス ポトシ) |SL |
| mx-roo |Q.R. |MX-ROO |Quintana Roo |Quintana Roo (キンタナロー) |QR |
| mx-que |Qro. |MX-QUE |Querétaro |Queretaro (ケレタロ) |QE |
| mx-pue |Pue. |MX-PUE |Puebla |Puebla (プエブラ) |PU |
| mx-oax |Oax. |MX-OAX |Oaxaca |Oaxaca (オアハカ) |OA |
| mx-nle |N.L. |MX-NLE |Nuevo León |Nuevo Leon (ヌエボレオン) |NL |
| mx-nay |Nay. |MX-NAY |Nayarit |Nayarit (ナヤリト) |NA |
| mx-mor |Mor. |MX-MOR |Morelos |Morelos (モレロス) |MR |
| mx-mic |Mich. |MX-MIC |Michoacán |Michoacan (ミチョアカン) |MC |
| mx-mex |Méx. |MX-MEX |Estado de México |Mexico State (メヒコ) |MX |
| mx-jal |Jal. |MX-JAL |Jalisco |Jalisco (ハリスコ) |JA |
| mx-hid |Hgo. |MX-HID |Hidalgo |Hidalgo (イダルゴ) |HI |
| mx-gro |Gro. |MX-GRO |Guerrero |Guerrero (ゲレロ) |GR |
| mx-gua |Gto. |MX-GUA |Guanajuato |Guanajuato (グアナフアト) |GT |
| mx-dur |Dgo. |MX-DUR |Durango |Durango (ドゥランゴ) |DU |
| mx-dif |CDMX. |MX-DIF |Ciudad de México |Mexico City (メキシコシティー) |DF |
| mx-col |Col. |MX-COL |Colima |Colima (コリマ) |CL |
| mx-coa |Coah. |MX-COA |Coahuila |Coahuila (コアウイラ) |CA |
| mx-chh |Chih. |MX-CHH |Chihuahua |Chihuahua (チワワ) |CH |
| mx-chp |Chis. |MX-CHP |Chiapas |Chiapas (チャパス) |CP |
| mx-cam |Camp. |MX-CAM |Campeche |Campeche (カンペチェ) |CM |
| mx-bcs |B.C.S. |MX-BCS |Baja California Sur |Baja California Sur (バハ カリフォルニア スル) |BS |
| mx-bcn |B.C. |MX-BCN |Baja California |Baja California (バハ カリフォルニア) |BN |
| mx-agu |Ags. |MX-AGU |Aguascalientes |Aguascalientes (アグアスカリエンテス) |AG |

### <a name="netherlands-provinces"></a>オランダ:州

| ID | ISO | name | 名前 (英語) |
| --- | --- | --- | --- |
| nl-zh |NL-ZH |Zuid-Holland |South Holland (南ホラント) |
| nl-ze |NL-ZE |Zeeland |Zeeland (ゼーラント) |
| nl-ut |NL-UT |Utrecht |Utrecht (ユトレヒト) |
| nl-ov |NL-OV |Overijssel |Overijssel (オーバーアイセル) |
| nl-nh |NL-NH |Noord-Holland |North Holland (北ホラント) |
| nl-nb |NL-NB |Noord-Brabant |North Brabant (北ブラバント) |
| nl-li |NL-LI |Limburg |Limburg (リンブルフ) |
| nl-gr |NL-GR |Groningen |Groningen (フローニンゲン) |
| nl-ge |NL-GE |Gelderland |Gelderland (ヘルデルラント) |
| nl-fr |NL-FR |Fryslân |Friesland (フリースラント) |
| nl-fl |NL-FL |Flevoland |Flevoland (フレヴォラント) |
| nl-dr |NL-DR |Drenthe |Drenthe (ドレンテ) |

### <a name="uk-countries"></a>英国:国

| ID | ISO | name |
| --- | --- | --- |
| gb-wls |GB-WLS |Wales |
| gb-sct |GB-SCT |Scotland |
| gb-nir |GB-NIR |Northern Ireland |
| gb-eng |GB-ENG |England |

### <a name="usa-states"></a>米国:州

| ID | name | 郵便 |
| --- | --- | --- |
| us-mi |Michigan |MI |
| us-ak |Alaska |AK |
| us-hi |Hawaii |HI |
| us-fl |Florida |FL |
| us-la |Louisiana |LA |
| us-ar |Arkansas |AR |
| us-sc |South Carolina |SC |
| us-ga |Georgia |GA |
| us-ms |Mississippi |MS |
| us-al |Alabama |AL |
| us-nm |New Mexico |NM |
| us-tx |Texas |TX |
| us-tn |Tennessee |TN |
| us-nc |North Carolina |NC |
| us-ok |Oklahoma |OK |
| us-az |Arizona |AZ |
| us-mo |Missouri |MO |
| us-va |Virginia |VA |
| us-ks |Kansas |KS |
| us-ky |Kentucky |KY |
| us-co |Colorado |CO |
| us-md |Maryland |MD |
| us-wv |West Virginia |WV |
| us-de |Delaware |DE |
| us-dc |District of Columbia |DC |
| us-il |Illinois |IL |
| us-oh |Ohio |OH |
| us-ca |California |CA |
| us-ut |Utah |UT |
| us-nv |Nevada |NV |
| us-in |Indiana |IN |
| us-nj |New Jersey |NJ |
| us-ri |Rhode Island |RI |
| us-ct |Connecticut |CT |
| us-pa |Pennsylvania |PA |
| us-ny |New York |NY |
| us-ne |Nebraska |NE |
| us-ma |Massachusetts |MA |
| us-ia |Iowa |IA |
| us-nh |New Hampshire |NH |
| us-or |Oregon |OR |
| us-mn |Minnesota |MN |
| us-vt |Vermont |VT |
| us-id |Idaho |ID |
| us-wi |Wisconsin |WI |
| us-wy |Wyoming |WY |
| us-sd |South Dakota |SD |
| us-nd |North Dakota |ND |
| us-me |Maine |ME |
| us-mt |モンタナ |MT |
| us-wa |ワシントン |WA |

## <a name="next-steps"></a>次の手順

* [Power BI のマトリックス ビジュアル](desktop-matrix-visual.md)

* [Power BI での視覚化の種類](power-bi-visualization-types-for-reports-and-q-and-a.md)
