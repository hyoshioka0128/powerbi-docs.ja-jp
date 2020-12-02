---
title: チュートリアル:Web ページからのデータのインポートと分析
description: チュートリアル:Power BI Desktop を使用して Web ページからデータをインポートおよび分析する
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: tutorial
ms.date: 01/13/2020
LocalizationGroup: Learn more
ms.openlocfilehash: d407da8e11473180f21e62c94f0ab440050beedc
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96404826"
---
# <a name="tutorial-analyze-webpage-data-by-using-power-bi-desktop"></a>チュートリアル:Power BI Desktop を使用して Web ページのデータを分析する

昔からのサッカー ファンなら、UEFA 欧州選手権 (ユーロ カップ) の優勝国が気になります。 Power BI Desktop を使うと、このデータを Web ページからレポートにインポートして、データを表示する視覚エフェクトを作成できます。 このチュートリアルでは、Power BI Desktop を使って次のことを行う方法を学習します。

- Web データ ソースに接続し、使用可能なテーブルの間を移動します。
- Power Query エディターを使ってデータの整形と変換を行います。
- クエリに名前を付け、Power BI Desktop レポートにインポートします。
- マップと円グラフの視覚エフェクトを作成してカスタマイズします。

## <a name="connect-to-a-web-data-source"></a>Web データ ソースに接続する

UEFA 優勝国のデータは、UEFA European Football Championship Wikipedia ページ (https://en.wikipedia.org/wiki/UEFA_European_Football_Championship ) の Results テーブルから取得できます。 

![Wikipedia の Results テーブル](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage1.png)

Web 接続の確立には基本認証のみが使用されます。 Web コネクタを使用すると、認証が必要な Web サイトが正常に動作しないことがあります。

データをインポートするには:

1. Power BI Desktop の **[ホーム]** リボン タブで、 **[データを取得]** の横の矢印をドロップダウンして、 **[Web]** を選びます。

   ![リボンからの [データを取得]](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web3.png) 

   >[!NOTE]
   >**[データの取得]** 項目自体を選択するか、Power BI Desktop の [作業の開始] ダイアログから **[データの取得]** を選択し、 **[データの取得]** ダイアログの **[すべて]** または **[その他]** セクションから **[Web]** を選択して、 **[接続]** を選択することもできます。

1. **[Web から]** ダイアログで、URL `https://en.wikipedia.org/wiki/UEFA_European_Football_Championship` を **[URL]** テキスト ボックスに貼り付けて、 **[OK]** を選択します。

    ![ダイアログからの [データを取得]](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web2.png)

   Wikipedia の Web ページに接続すると、 **[ナビゲーター]** ダイアログに、ページで使用可能なテーブルの一覧が表示されます。 テーブル名を選んでデータをプレビューできます。 **Results[edit]** テーブルに目的のデータがありますが、必要な形式と正確には一致していません。 レポートに読み込む前に、形式を変更し、データをクリーンアップします。

   ![[ナビゲーター] ダイアログ ボックス](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/tutorialimanaly_navigator.png)

   >[!NOTE]
   >**[プレビュー]** ペインには最後に選択したテーブルが表示されますが、 **[データの変換]** または **[読み込み]** を選択すると、選択したすべてのテーブルが Power Query エディターに読み込まれます。

1. **[ナビゲーター]** の一覧で **Results[edit]** テーブルを選択し、 **[データの変換]** を選択します。

   テーブルのプレビューが **Power Query エディター** で開きます。ここで、変換を適用してデータをクリーンアップできます。

   ![Power Query エディター](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage3.png)

## <a name="shape-data-in-power-query-editor"></a>Power Query エディターでデータを整形する

年と優勝国だけを表示することによって、データをスキャンしやすくします。 Power Query エディターを使って、以下のデータ整形とクレンジングの手順を実行します。

まず、テーブルから 2 列を除くすべての列を削除します。 このプロセスの後半で、これらの列の名前を *Year* と *Country* に変更します。

1. **[Power Query エディター]** グリッドで、列を選択します。 複数の項目を選択するには、Ctrl キーを押しながら選択します。

1. 右クリックして **[他の列の削除]** を選択するか、 **[ホーム]** リボン タブの **[列の管理]** グループから **[列の削除]**  >  **[他の列の削除]** を選択し、テーブルから他のすべての列を削除します。

   ![[他の列の削除] ドロップダウン メニュー](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web6.png)

   または

   ![[他の列の削除] リボン](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage4.png)

次に、最初の列のセルから余計な単語 *Details* を削除します。

1. 最初の列を選択します。

1. 右クリックし、 **[値の置換]** を選択するか、リボンの **[ホーム]** タブの **[変換]** グループから **[値の変換]** を選択します。 このオプションは、 **[変換]** タブの **[任意の列]** グループにもあります。

   ![[値の置換] ドロップダウン メニュー](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web7.png) 

   または

   ![[値の置換] リボン](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web8a.png)

1. **[値の置換]** ダイアログの **[検索する値]** テキスト ボックスに「**Details**」と入力し、 **[置換後の文字列]** テキスト ボックスを空のままにします。そして、 **[OK]** を選択してこの列から *Details* という単語を削除します。

   ![列から単語を削除する](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage6.png)

一部のセルには、年の値ではなく "Year" という単語のみが含まれています。 列をフィルター処理して、"Year" という単語が含まれていない行のみを表示できます。

1. 列のフィルター ドロップダウン矢印を選択します。

1. ドロップダウン メニューで下にスクロールし、**Year** オプションの横にあるチェックボックスをオフにして **[OK]** を選択します。

   ![データのフィルター処理](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage7.png)

勝者国のデータだけが表示されるので、2 列目の名前を **Country** に変更します。 列の名前を変更するには次のようにします。

1. 2 列目のヘッダーをダブルクリックするか長押しします。
   - 列ヘッダーを右クリックし、 **[名前の変更]** を選択します。
   - \* 列を選択し、リボンの **[変換]** タブの **[任意の列]** グループから **[名前の変更]** を選択します。

   ![ドロップダウン メニューの [名前の変更]](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage7a.png) 
  
   または

   ![[名前の変更] リボン](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web8.png)

1. ヘッダーに「**Country**」と入力して **Enter** キーを押し、列の名前を変更します。

"2020" 年のように **Country** 列が null 値の行もフィルターで除外します。 **Year** の値で行ったようにフィルター メニューを使って行うことができます。または次のようにしてもかまいません。

1. 値が *null* である **2020** の行の **Country** セルを右クリックします。

1. コンテキスト メニューで **[テキスト フィルター]**  >  **[指定の値と等しくない]** を選び、そのセルの値を含むすべての行を削除します。

   ![テキスト フィルター](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web11.png)

## <a name="import-the-query-into-report-view"></a>レポート ビューにクエリをインポートする

意図したとおりにデータを整形したので、クエリに "Euro Cup Winners" という名前を付けて、レポートにインポートすることができます。

1. **[クエリ設定]** ウィンドウの **[名前]** テキスト ボックスに「 **欧州選手権の勝者**」と入力します。

   ![クエリに名前を付ける](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage8.png)

1. リボンの **[ホーム]** タブから **[閉じて適用]**  >  **[閉じて適用]** を選びます。

   ![閉じて適用](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage9.png)

クエリが Power BI Desktop の *レポート* ビューに読み込まれて、 **[フィールド]** ペインに表示されます。

   ![[フィールド] ウィンドウ](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage11.png)

>[!TIP]
>いつでも次のようにして Power Query エディターに戻ってクエリを編集および調整できます。
>- **[フィールド]** ペインで **Euro Cup Winners** の隣の **[その他のオプション]** の省略記号ボタン **[...]** を選択して、 **[クエリの編集]** を選択します。
>- または、レポート ビューの **[ホーム]** リボン タブの **[外部データ]** グループで **[クエリの編集]**  >  **[クエリの編集]** を選びます。 

## <a name="create-a-visualization"></a>視覚エフェクトを作成する

データに基づいて視覚エフェクトを作成するには:

1. **[フィールド]** ウィンドウで **Country** フィールドを選ぶか、フィールドをレポート キャンバスにドラッグします。 Power BI Desktop がデータを国名として認識し、自動的に **マップ** 視覚エフェクトを作成します。

   ![マップの視覚エフェクト](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web14.png)

1. 隅のハンドルをドラッグしてマップを拡大し、すべての優勝国名が表示されるようにします。  

   ![マップを拡大する](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage14.png)

1. マップには、欧州選手権トーナメントで優勝したすべての国のデータ ポイントが同じように表示されています。 優勝した回数を反映するように各データ ポイントのサイズを変更するには、 **[視覚化]** ウィンドウの下部の **[サイズ]** の下の **[ここにデータ フィールドをドラッグしてください]** に **Year** フィールドをドラッグします。 フィールドが自動的に **[Year のカウント]** メジャーに変化し、マップ視覚エフェクトで優勝回数が多い国ほどデータ ポイントが大きく表示されるようになります。

   ![Year のカウントを [サイズ] にドラッグする](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage15.png)

## <a name="customize-the-visualization"></a>視覚エフェクトをカスタマイズする

ご覧のように、データに基づいて視覚化を作成することはとても簡単です。 また、意図した表現方法に少しでも近くなるように視覚エフェクトをカスタマイズするのも簡単です。

### <a name="format-the-map"></a>マップの書式を設定する

視覚エフェクトを選んで **[視覚化]** ウィンドウの **[書式]** (ペイント ローラー) アイコンを選ぶことで、視覚エフェクトの外観を変更することができます。 たとえば、視覚エフェクトの "Germany" のデータ ポイントは誤解を招きやすい表現になっています。これは、ドイツは西ドイツとして 2 回、ドイツとして 1 回優勝していますが、マップでは 2 つのポイントが分けられたりまとめられたりせずに、重ねて表示されているためです。 2 つのポイントに異なる色を設定して、このファクトをわかりやすくします。 また、マップのタイトルをよりわかりやすく魅力的にすることもできます。

1. 視覚エフェクトを選び、 **[書式]** アイコンを選んでから、 **[データの色]** を選んでデータの色のオプションを展開します。

   ![書式アイコンとデータの色の選択](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web15.png)

1. **[すべて表示]** を **[オン]** にし、**West Germany** の横のドロップダウン メニューで黄色を選択します。

   ![色の変更](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web16.png)

1. **[タイトル]** を選んでタイトルのオプションを展開し、 **[タイトル テキスト]** フィールドの現在のタイトルの代わりに「**Euro Cup Winners**」と入力します。

1. **[フォントの色]** を赤に、 **[テキスト サイズ]** を **12** に、 **[フォント ファミリ]** を **[Segoe (Bold)]** にそれぞれ変更します。

   ![フォントの色、サイズ、ファミリ](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web17.png)

マップの視覚エフェクトは次のようになります。

![書式設定されたマップの視覚エフェクト](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web18.png)

### <a name="change-the-visualization-type"></a>視覚化の種類の変更

視覚化の種類を変更するには、視覚化を選択し、 **[視覚化]** ペインの上部で別のアイコンを選択します。 たとえば、マップ視覚エフェクトにはロシア連邦とチェコ共和国のデータが表示されていません。これらの国が世界地図に存在しなくなったためです。 ツリーマップや円グラフのような別の種類の視覚エフェクトの方が、すべての値が表示されるためいっそう正確です。

マップを円グラフに変更するには、マップを選んだ後、 **[視覚化]** ペインで **[円グラフ]** アイコンを選択します。

![視覚化を円グラフに変更する](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/get-data-web19.png)

>[!TIP]
>- **[データの色]** 書式オプションを使って、"Germany" と "West Germany" を同じ色にすることができます。 
>- 円グラフで優勝回数の多い国をグループにするには、視覚化の右上隅にある省略記号 **[...]** を選択し、 **[Year で並べ替え]** を選択します。

Power BI Desktop は、さまざまなデータ ソースからデータを取得して分析のニーズに合わせてデータの形を整えることから、このデータを機能豊富な対話型の方法で視覚化することまで、シームレスなエンド ツー エンドのエクスペリエンスを提供します。 レポートが完成したら、[Power BI にアップロード](../create-reports/desktop-upload-desktop-files.md)し、それに基づいて、他の Power BI ユーザーと共有可能なダッシュボードを作成できます。

## <a name="see-also"></a>関連項目

* [Microsoft Learn for Power BI](/learn/powerplatform/power-bi?WT.mc_id=powerbi_landingpage-docs-link)
* [Power BI Desktop のビデオを見る](../fundamentals/desktop-videos.md)
* [Power BI フォーラムにアクセスする](https://go.microsoft.com/fwlink/?LinkID=519326)
* [Power BI ブログを読む](https://go.microsoft.com/fwlink/?LinkID=519327)