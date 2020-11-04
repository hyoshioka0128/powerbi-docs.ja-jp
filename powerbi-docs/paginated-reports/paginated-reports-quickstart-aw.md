---
title: チュートリアル:ページ分割されたレポートを作成して Power BI サービスにアップロードする
description: このチュートリアルでは、サンプルの Azure SQL データベースに接続します。 その後、レポート ビルダーのウィザードを使用してページ分割されたレポートを作成します。 次に、Power BI サービスで Premium 容量のワークスペースにページ分割されたレポートをアップロードします。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: tutorial
ms.date: 11/06/2018
ms.openlocfilehash: baccdcae82fb56b2f7f7a9d6cb4839e941e99bf0
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2020
ms.locfileid: "93297531"
---
# <a name="tutorial-create-a-paginated-report-and-upload-it-to-the-power-bi-service"></a>チュートリアル:ページ分割されたレポートを作成して Power BI サービスにアップロードする

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

このチュートリアルでは、サンプルの Azure SQL データベースに接続します。 その後、Power BI レポート ビルダーのウィザードを使用して、複数のページにラップするテーブルを含むページ分割されたレポートを作成します。 次に、Power BI サービスで Premium 容量のワークスペースにページ分割されたレポートをアップロードします。

![Power BI サービスにおけるページ分割されたレポート](media/paginated-reports-quickstart-aw/power-bi-paginated-report-service.png)

このチュートリアルで実行する手順を次に示します。

> [!div class="checklist"]
> * Azure のサンプル データベースを作成します。
> * Power BI レポート ビルダーのウィザードを使用してマトリックスを作成します。
> * 各ページのタイトル、ページ番号、列見出しでレポートの書式を設定します。
> * 通貨の書式を設定します。
> * Power BI サービスにレポートをアップロードします。

Azure サブスクリプションをお持ちでない場合は、開始する前に [無料アカウント](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) を作成してください。
 
## <a name="prerequisites"></a>前提条件  

ページ分割されたレポートを作成するための前提条件を次に示します。

- [Power BI レポート ビルダーは、Microsoft ダウンロード センターから](https://aka.ms/pbireportbuilder)インストールしてください。 

- クイック スタート「[Azure portal で Azure SQL データベースを作成する](/azure/sql-database/sql-database-get-started-portal)」に従います。 **[概要]** タブの **[サーバー名]** ボックスの値をコピーして保存します。Azure で作成したパスワードとユーザー名を憶えておきます。

ページ分割されたレポートを Power BI サービスにアップロードするための前提条件を次に示します。

- [Power BI Pro ライセンス](../admin/service-admin-licensing-organization.md)が必要です。
- [Power BI Premium 容量](../admin/service-premium-what-is.md)内のサービス上のワークスペースが必要です。 ワークスペース名の横にダイヤモンド形のアイコン ![Premium のダイヤモンド形アイコン](media/paginated-reports-quickstart-aw/premium-diamond.png) が表示されます。

## <a name="create-the-matrix-with-a-wizard"></a>ウィザードでマトリックスを作成する
  
1.  コンピューターから Power BI レポート ビルダーを開始します。  
  
     **[作業の開始]** ダイアログ ボックスが開きます。  
  
     ![レポート ビルダーの [作業の開始]](media/paginated-reports-create-embedded-dataset/power-bi-paginated-get-started.png)
  
1.  左側のウィンドウで **[新しいレポート]** が選択されていることを確認し、右側のウィンドウで **[テーブルまたはマトリックス ウィザード]** を選択します。  
  
4.  **[データセットの選択]** ページで、 **[データセットを作成する]** > **[次へ]** の順に選択します。  

    ![データセットを作成する](media/paginated-reports-quickstart-aw/power-bi-paginated-create-dataset.png)
  
5.  **[データ ソースへの接続の選択]** ページで、 **[新規]** を選択します。 

    ![新しいデータ ソース](media/paginated-reports-quickstart-aw/power-bi-paginated-new-data-source-connection.png)
  
     **[データ ソースのプロパティ]** ダイアログ ボックスが表示されます。  
  
6.  文字とアンダースコアを使用して、データ ソースに任意の名前を付けます。 このチュートリアルでは、 **[名前]** ボックスに「 **MyAzureDataSource** 」と入力します。  
  
7.  **[接続の種類の選択]** ボックスで、 **[Microsoft Azure SQL Database]** を選択します。  
  
8.  **[接続文字列]** ボックスの隣の **[構築]** を選択します。 

    ![[データ ソースのプロパティ] - [構築]](media/paginated-reports-quickstart-aw/power-bi-paginated-data-source-properties-build.png)

9. **Azure で:** Azure portal に戻り、 **[SQL データベース]** を選択します。

1. この記事の「 **前提条件** 」セクションで示したクイック スタート「Azure portal で Azure SQL データベースを作成する」で作成した Azure SQL データベースを選択します。

1. **[概要]** タブで、 **[サーバー名]** ボックスの値をコピーします。

2. **レポート ビルダーで** : **[接続プロパティ]** ダイアログ ボックスの **[サーバー名]** にコピーしたサーバー名を貼り付けます。 

1. **[サーバー ログオン]** で、 **[SQL Server 認証を使用する]** が選択されていることを確認し、サンプル データベース用に Azure で作成したユーザー名とパスワードを入力します。

1. **[データベースへの接続]** でドロップダウン矢印を選択し、Azure で作成したデータベース名を選択します。
 
    ![データ ソース接続プロパティ](media/paginated-reports-quickstart-aw/power-bi-paginated-connection-properties.png)

1. **[接続テスト]** を選択します。 **[テスト結果]** に " **接続テストに成功しました** " というメッセージが表示されます。

1. **[OK]**  >  **[OK]** の順に選択します。 

   **[接続文字列]** ボックスに、作成した接続文字列が表示されます。 

    ![データ ソース接続文字列](media/paginated-reports-quickstart-aw/power-bi-paginated-data-source-properties-connection-string.png)

1. **[OK]** を選択します。
  
9. **[データ ソースへの接続の選択]** ページで、作成したデータ ソース接続の下に [(このレポートで)] と表示されます。 そのデータ ソースを選択し、 **[次へ]** を選択します。  

    ![My Azure データ ソース](media/paginated-reports-quickstart-aw/power-bi-paginated-my-azure-data-source.png)

10. ボックスに同じユーザー名とパスワードを入力します。 
  
10. **[クエリのデザイン]** ページで、SalesLT を展開し、テーブルを展開して、次のテーブルを選択します。

    - Address
    - Customer
    - 製品
    - ProductCategory
    - SalesOrderDetail
    - SalesOrderHeader

     **[リレーションシップ]**  >  **[自動検出]** が選択されているので、レポート ビルダーによってこれらのテーブル間のリレーションシップが検出されます。 
    
    ![クエリのデザイン](media/paginated-reports-quickstart-aw/power-bi-paginated-design-query.png)
 
1.  **[クエリの実行]** を選択します。 レポート ビルダーで **[クエリ結果]** が表示されます。 
 
     ![Query results](media/paginated-reports-quickstart-aw/power-bi-paginated-query-results.png)

18. **[次へ]** を選択します。 

19. **[データセットの選択]** ページで、先ほど作成したデータセットを選択し、 **[次へ]** を選択します。

    ![データセットを選択する](media/paginated-reports-quickstart-aw/power-bi-paginated-choose-dataset.png)

1. **[フィールドの配置]** ページで、以下のフィールドを **[使用できるフィールド]** ボックスから **[行グループ]** ボックスにドラッグします。

    - CompanyName
    - SalesOrderNumber
    - Product_Name

1. 以下のフィールドを **[使用できるフィールド]** ボックスから **[値]** ボックスにドラッグします。

    - OrderQty
    - UnitPrice
    - LineTotal

    レポート ビルダーで自動的に **[値]** ボックスのフィールドの合計が行われます。

    ![フィールドの配置](media/paginated-reports-quickstart-aw/power-bi-paginated-drag-fields.png)

24. **[レイアウトの選択]** ページでは、すべての設定を既定のままにしますが、 **[グループの展開/折りたたみ]** はオフにします。 一般には、グループの展開/折りたたみ機能は優れていますが、ここではテーブルを複数のページにラップします。

1. **[次へ]**  >  **[完了]** の順に選択します。 テーブルがデザイン サーフェイスに表示されます。
 
## <a name="what-youve-created"></a>作成したもの

いったん手を止めて、ウィザードの結果を見てみましょう。

![マトリックス ウィザードの結果](media/paginated-reports-quickstart-aw/power-bi-paginated-wizard-results.png)

1. [レポート データ] ウィンドウには、埋め込まれた Azure データ ソースと、それに基づく埋め込まれたデータセット (どちらも作成したもの) が表示されます。 

2. デザイン サーフェイスの幅は約 6 インチです。 デザイン サーフェイスには、列見出しとプレースホルダー値を含むマトリックスが表示されています。 マトリックスには 6 つの列があり、5 行だけが表示されています。 

3. Order Qty、Unit Price、Line Total はすべて合計であり、各行グループには小計があります。 

    実際のデータ値はまだ表示されていません。 それらを表示するにはレポートを実行する必要があります。

4. [プロパティ] ウィンドウでは、Tablix1 というマトリックスが選択されています。 レポート ビルダーでの *tablix* は、行と列でデータが表示されるデータ領域です。 テーブルまたはマトリックスのいずれかにすることができます。

5. [グループ化] ウィンドウには、ウィザードで作成した 3 つの行グループが表示されています。 

    - CompanyName
    - Sales Order
    - 製品名

    このマトリックスには、列グループはありません。

### <a name="run-the-report"></a>レポートを実行する

実際の値を表示するには、レポートを実行する必要があります。

1. **[ホーム]** ツール バーで **[実行]** を選択します。

   これで、値が表示されるようになります。 マトリックスには、デザイン ビューで表示されていたものよりはるかに多くの行があります。 レポート ビルダーでページが **[1** / **2?]** と表示されていることに注意してください。 レポート ビルダーでは可能な限り速やかにレポートが読み込まれるので、一度に読み込まれるのは数ページ分だけのデータです。 疑問符は、レポート ビルダーにすべてのデータがまだ読み込まれていないことを示します。

   ![レポートを実行する](media/paginated-reports-quickstart-aw/power-bi-paginated-run-report.png)

2. **[印刷レイアウト]** を選択します。 印刷時には、レポートはこの形式になります。 レポート ビルダーは、レポートが 33 ページであることを認識するようになっており、フッターに日付と時刻のスタンプを自動的に追加しています。

## <a name="format-the-report"></a>レポートを書式設定する

現在、33 ページにラップするマトリックスを含むレポートがあります。 それでは、他の機能を追加し、見た目をもっとよくしてみましょう。 結果を確認したい場合は、すべてのステップの後でレポートを実行できます。

- リボンの **[実行]** タブで **[デザイン]** を選択し、変更を続けられるようにします。  

### <a name="set-page-width"></a>ページの幅を設定する

通常、ページ分割されたレポートは印刷用に書式設定されており、一般的なページは 8 1/2 X 11 インチです。 

1. ルーラーをドラッグして、デザイン サーフェイスの幅を 7 インチにします。 既定の余白は各側とも 1 インチなので、横の余白を狭くする必要があります。

1. デザイン サーフェイスを囲む灰色の領域内をクリックすると、 **[レポート]** プロパティが表示されます。

    [プロパティ] ウィンドウが表示されない場合は、 **[表示]** タブの **[プロパティ]** をクリックします。

2. **[余白]** を展開し、 **[左]** と **[右]** を 1in から 0.75in に変更します。 

    ![ページの余白を設定する](media/paginated-reports-quickstart-aw/power-bi-paginated-set-margins.png)
  
### <a name="add-a-report-title"></a>レポート タイトルの追加  

1. ページの上部にある **[クリックしてタイトルを追加]** を選択し、「 **Sales by Company** 」と入力します。  

2. タイトルのテキストを選択し、[プロパティ] ウィンドウの **[フォント]** で、 **[色]** を **[青]** に変更します。
  
### <a name="add-a-page-number"></a>ページ番号を追加する

レポートのフッターに日付と時刻のスタンプがあるのがわかります。 フッターにはページ番号も追加できます。

1. デザイン サーフェイス下端のフッターの右側に、[&ExecutionTime] と表示されています。 

2. レポート データ ペインで [組み込みフィールド] フォルダーを展開します。 **[ページ番号]** を、フッター左側の [&ExecutionTime] と同じ高さにドラッグします。

3. [&PageNumber] ボックスの右側をドラッグして、正方形にします。

4. **[挿入]** タブで **[テキスト ボックス]** を選択します。

5. [&PageNumber] の右側をクリックし、「of」と入力してから、テキスト ボックスを四角形にします。

6. **[全体的な総ページ数]** をフッターの "of" の右側にドラッグし、右側の境界をドラッグしてやはり正方形にします。

    ![ページ数をドラッグする](media/paginated-reports-quickstart-aw/power-bi-paginated-add-page-numbers.png)

### <a name="make-the-table-wider"></a>テーブルを広くする  

今度は、マトリックスをページの幅いっぱいに広げて、名前があまり多くスクロールしないようにテキスト列の幅を広くします。 
 
1. マトリックスを選択し、Company Name 列を選択します。

3. マトリックス上部の Company Name 列の右端にある灰色のバーをポイントします。 列の終わりが 1 3/8 インチになるまで、右側にドラッグします。 

    ![列の右端をドラッグする](media/paginated-reports-quickstart-aw/power-bi-paginated-drag-column.png)

4. Product Name の右端を、列が 3 3/4 インチで終了するまでドラッグします。   

これで、マトリックスが印刷領域とほぼ同じ幅になりました。

### <a name="format-the-currency"></a>通貨の書式を設定する

レポートを実行したときに気付いたかもしれませんが、金額がまだ通貨として書式設定されていません。

1. 左上の [Sum(OrderQty)] セルを選択し、Shift キーを押しながら、右下の [Sum(LineTotal)] セルを選択します。

    ![通貨値を含むセルを選択する](media/paginated-reports-quickstart-aw/power-bi-paginated-select-money-cells.png)

2. **[ホーム]** タブでドル ( **$** ) の通貨記号を選択し、 **[プレースホルダーのスタイル]** の隣の矢印を選択して、 > **[サンプルの値]** を選択します。
 
    ![サンプルの値を表示する](media/paginated-reports-quickstart-aw/power-bi-paginated-format-currency.png)

    値が通貨として書式設定されて表示されます。

    ![通貨サンプルの値](media/paginated-reports-quickstart-aw/power-bi-paginated-display-sample-values.png)

### <a name="add-column-headers-on-each-page"></a>各ページに列見出しを追加する

Power BI サービスにレポートを発行する前に、もう 1 つの書式改善として、レポートの各ページに列見出しが表示されるようにします。

1. [グループ化] ウィンドウの上部バーの右端で、ドロップダウン矢印を選択して、 **[詳細設定モード]** を選択します。

    ![詳細設定モードを有効にする](media/paginated-reports-quickstart-aw/power-bi-paginated-advanced-mode.png)

2. **[行グループ]** で、先頭の **[Static]** バーを選択します。 マトリックスで Company Name セルが選択されたことがわかります。

   ![静的グループを選択する](media/paginated-reports-quickstart-aw/power-bi-paginated-static-group.png)

3. **[プロパティ]** ウィンドウには、 **[Tablix メンバー]** のプロパティが表示されています。 **[KeepWithGroup]** を **[後]** に設定し、 **[RepeatOnNewPage]** を **[True]** に設定します。

    ![RepeatOnNewPage を設定する](media/paginated-reports-quickstart-aw/power-bi-paginated-repeat-on-new-page.png)

    レポートを実行して、どのようになったか確認します。

5. **[ホーム]** タブの **[実行]** を選択します。

6. まだ選択されている場合は、 **[印刷レイアウト]** を選択します。 レポートのページ数は 29 になっています。 何ページかスクロールします。 通貨が書式設定されており、すべてのページの列に見出しが付いており、ページ番号と日時スタンプを含むフッターがすべてのページに表示されることがわかります。
 
    ![完成したページ](media/paginated-reports-quickstart-aw/power-bi-paginated-finished-page.png)

7. コンピューターにレポートを保存します。
 
##  <a name="upload-the-report-to-the-service"></a>レポートをサービスにアップロードする

このページ分割されたレポートの作成は済んだので、次に Power BI サービスにレポートをアップロードします。

1. Power BI サービス (`https://app.powerbi.com`) のナビ ペインで、 **[ワークスペース]**  >  **[ワークスペースの作成]** の順に選択します。

2. ワークスペースに、「 **Azure AW** 」または他の一意名を付けます。 今のところ、メンバーはまだ自分だけです。 

3. **[詳細設定]** の横にある矢印を選択して、 **[専用の容量]** をオンにします。 

    ![Premium 容量でワークスペースを作成する](media/paginated-reports-quickstart-aw/power-bi-paginated-create-workspace-premium-capacity.png)

    オンにできない場合は、Power BI 管理者に依頼して、専用の Premium 容量にワークスペースを追加するためのアクセス許可を付与してもらう必要があります。

4. **[このワークスペースに対して利用可能な専用容量を選択する]** を選択し、必要な場合は **[保存]** を選択します。
    
    ![ダイヤモンド形の Premium アイコン](media/paginated-reports-quickstart-aw/power-bi-paginated-diamond-icon.png)

    ワークスペースが Premium 容量内にない場合は、レポートをアップロードしようとすると、"ページ分割されたレポートをアップロードできません" というメッセージが表示されます。 Power BI 管理者に連絡し、ワークスペースを移動してもらいます。

1. 新しいワークスペースで、 **[データを取得]** を選択します。

2. **[ファイル]** ボックスの **[取得]** を選択します。

3. **[ローカル ファイル]** を選択し、ファイルを保存した場所に移動して、 **[開く]** を選択します。

   Power BI によってファイルがインポートされ、アプリ一覧ページの **[レポート]** に表示されます。

    ![アプリ一覧内のレポート](media/paginated-reports-quickstart-aw/power-bi-paginated-app-list.png)

4. レポートを選択して表示します。

5. エラーが発生する場合は、資格情報の再入力が必要な場合があります。 **[管理]** アイコンを選択します。

    ![レポートを管理する](media/paginated-reports-quickstart-aw/power-bi-paginated-manage-report.png)

6. **[資格情報を編集]** を選択し、Azure データベースを作成するときに Azure で使用した資格情報を入力します。

    ![レポートの資格情報を編集する](media/paginated-reports-quickstart-aw/power-bi-paginated-edit-credentials.png)

7. ページ分割されたレポートを、Power BI サービスで表示できるようになります。

    ![Power BI サービスにおけるページ分割されたレポート](media/paginated-reports-quickstart-aw/power-bi-paginated-report-service.png)

## <a name="next-steps"></a>次の手順

[Power BI Premium のページ分割されたレポートとは](paginated-reports-report-builder-power-bi.md)