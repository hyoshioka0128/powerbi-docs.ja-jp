---
title: チュートリアル:VM での Power BI Report Server の探索
description: このチュートリアルでは、Power BI Report Server が既にインストールされている仮想マシンを作成し、Web ポータルを探索します。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: tutorial
ms.date: 05/06/2019
ms.openlocfilehash: 85fcd6249a833c35cb98fca6abf2881ab1a4bf7e
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418419"
---
# <a name="tutorial-explore-the-power-bi-report-server-web-portal-in-a-vm"></a>チュートリアル:VM で Power BI Report Server Web ポータルを探索する
このチュートリアルでは、Power BI Report Server が既にインストールされている Azure 仮想マシンを作成するので、サンプルの Power BI とページ分割されたレポートの表示、編集、および管理と、KPI を体験できます。

![Report Server の Web ポータル](media/tutorial-explore-report-server-web-portal/power-bi-report-server-browser-in-vm-no-numbers.png)

このチュートリアルでは、次のタスクを実行します。

> [!div class="checklist"]
> * VM を作成して接続する
> * VM で Power BI Report Server Web ポータルを起動して探索する
> * お気に入りの項目にタグを付ける
> * Power BI レポートを表示して編集する
> * ページ分割されたレポートを表示、管理、編集する
> * Excel Online で Excel ブックを表示する

このチュートリアルには、Azure サブスクリプションが必要です。 お持ちでない場合は、始める前に[無料アカウント](https://azure.microsoft.com/free/?WT.mc_id=A261C142F)を作成してください。

## <a name="create-a-power-bi-report-server-vm"></a>Power BI Report Server VM を作成する

Power BI チームが作成した、Power BI Report Server が既にインストールされている VM を利用できます。

1. Azure Marketplace で、Power BI Report Server を選択します。 このリンクで直接開きます。[Power BI Report Server](https://azuremarketplace.microsoft.com/marketplace/apps/reportingservices.technical-preview?tab=Overview)。  

2. **[今すぐ入手する]** を選択します。
3. プロバイダーの使用条件とプライバシー ポリシーに同意するには、 **[続行]** を選択します。

4. **[作成]** を選択します。

    ![Power BI Report Server VM を作成する](media/tutorial-explore-report-server-web-portal/power-bi-report-server-create.png)

5. **手順 1 の [基本]** で **[VM 名]** に「**reportservervm**」と入力します。

    Power BI Report Server VM 名にダッシュを含めることはできません。

5. 新しいユーザー名とパスワードを作成します。

6. **[リソース グループ]** で **[新規作成]** を選択し、 **「reportserverresourcegroupOK」と名前を付けて** >  **[OK]** を選択します。

    チュートリアルを複数回繰り返す場合、2 回目以降はリソース グループに別の名前を付ける必要があります。 1 つのサブスクリプションで 2 回、同じリソース グループ名を使用することはできません。 

    ![VM とリソース グループに名前を付ける](media/tutorial-explore-report-server-web-portal/power-bi-report-server-create-resource-group.png)

7. その他の項目は既定値のままにして **[OK]** を選択します。

8. **手順 2 の [設定]** では既定値のままにして **[OK]** を選択します。
 
    **SQL ストレージ アカウント** と **診断ストレージ アカウント** の値も一意である必要があります。 チュートリアルを複数回実行する場合は、異なる名前を付ける必要があります。

9. **手順 3 の [概要]** で、選択した内容を確認し > **[OK]** を選択します。

10. **手順 4 の [購入]** でユーザーの [ご契約条件] とプライバシー ポリシーを確認し > **[作成]** を選択します。

    "**Power BI Report Server のデプロイを送信しています**" のプロセスには数分かかることがあります。

## <a name="connect-to-your-virtual-machine"></a>仮想マシンに接続する

1. Azure のナビ ペインで、 **[仮想マシン]** を選択します。 

2. **[名前でフィルター]** ボックスに、「report」と入力します。 

3. **REPORTSERVERVM** という名前の VM を選択します。

    ![仮想マシンを表示する](media/tutorial-explore-report-server-web-portal/power-bi-report-server-view-virtual-machine.png)

4. REPORTSERVERVM 仮想マシンで、 **[接続]** を選択します。

    ![仮想マシンに接続する](media/tutorial-explore-report-server-web-portal/power-bi-report-server-connect-to-virtual-machine.png)

5. **[仮想マシンに接続する]** ウィンドウで、既定値のままにして **[RDP ファイルのダウンロード]** を選択します。

1. **[リモート デスクトップ接続]** ダイアログ ボックスで、 **[接続]** を選択します。

6. VM 用に作成した名前とパスワードを入力し、 **[OK]** を選択します。

7. 次のダイアログ ボックスに、**リモート コンピューターの ID を特定できない** というメッセージが表示されます。 **[はい]** を選択します。

   すると、新しい VM が開きます。

## <a name="power-bi-report-server-on-the-vm"></a>VM 上の Power BI Report Server

VM が開いたら、デスクトップには次の項目が表示されます。

![Power BI Report Server 仮想マシンの起動](media/tutorial-explore-report-server-web-portal/power-bi-report-server-vm-5-numbers.png)

|数値  |説明  |
|---------|---------|
|![番号 1](media/tutorial-explore-report-server-web-portal/number-1.png) | サンプル Power BI (.PBIX) レポート |
|![番号 2](media/tutorial-explore-report-server-web-portal/number-2.png) | Power BI Report Server ドキュメントへのリンク |
|![番号 3](media/tutorial-explore-report-server-web-portal/number-3.png) | Power BI Report Server (2019 年 1 月) 向けに最適化された Power BI Desktop を起動します |
|![番号 4](media/tutorial-explore-report-server-web-portal/number-4.png) | ブラウザーで Power BI Report Server の Web ポータルを開きます |
|![番号 5](media/tutorial-explore-report-server-web-portal/number-5.png) | ページ分割された (.RDL) レポートを作成するために SQL Server Data Tools を起動します |

**[Report Server Web ポータル]** アイコンをダブルクリックします。 ブラウザーで `https://localhost/reports/browse` が開きます。 Web ポータルには、種類ごとにグループ化されたさまざまなファイルが表示されます。 

![Power BI レポート サーバーの Web ポータル](media/tutorial-explore-report-server-web-portal/power-bi-report-server-browser-in-vm.png)

|数値  |説明  |
|---------|---------|
|![番号 1](media/tutorial-explore-report-server-web-portal/number-1.png) | Web ポータルで作成された KPI |
|![番号 2](media/tutorial-explore-report-server-web-portal/number-2.png) |  Power BI (.PBIX) レポート  |
|![番号 3](media/tutorial-explore-report-server-web-portal/number-3.png) | SQL Server Mobile Report Publisher で作成されたモバイル レポート  |
|![番号 4](media/tutorial-explore-report-server-web-portal/number-4.png) |  レポート ビルダーまたは SQL Server Data Tools で作成されたページ分割されたレポート  |
|![番号 5](media/tutorial-explore-report-server-web-portal/number-5.png) | Excel ブック   | 
|![番号 6](media/tutorial-explore-report-server-web-portal/number-6.png) | ページ分割されたレポートのデータ ソース | 


## <a name="tag-your-favorites"></a>お気に入りにタグを追加する
お気に入りに登録するレポートおよび KPI をタグ付けすることができます。 それらはすべて 1 つの [お気に入り] フォルダーに集められるので、Web ポータルと Power BI モバイル アプリの両方で簡単に見つけることができます。 

1. **利益率** KPI の右上にある省略記号 ( **...** ) を選択し、 **[お気に入りに追加]** を選択します。
   
    ![お気に入りに追加](media/tutorial-explore-report-server-web-portal/power-bi-report-server-add-to-favorites.png)
2. お気に入りにした KPI やモバイル レポートまたは他のお気に入りを Web ポータルの [お気に入り] ページで表示するには、Web ポータルの **[お気に入り]** を選択します。
   
    ![[お気に入り] を表示](media/tutorial-explore-report-server-web-portal/power-bi-report-server-favorites.png)

3. **[参照]** を選択して Web ポータルに戻ります。
   
## <a name="view-items-in-list-view"></a>リスト ビューで項目を表示する
規定では、Web ポータルのコンテンツはタイル ビューで表示されます。

リスト ビューに切り替えると、複数の項目を同時に簡単に移動または削除できます。 

1. **[タイル]**  >  **[リスト]** を選択します。
   
    ![ビューの切り替え](media/tutorial-explore-report-server-web-portal/report-server-web-portal-list-view.png)

2. タイル ビューに戻ります。 **[リスト]**  >  **[タイル]** の順に選択します。

## <a name="power-bi-reports"></a>Power BI レポート

Web ポータルで Power BI レポートを表示して操作し、Web ポータルから Power BI Desktop を起動することができます。

### <a name="view-power-bi-reports"></a>Power BI レポートを表示する

1. Web ポータルの **[Power BI レポート]** で、 **[Sample Customer Overview Report]** を選択します。 ブラウザーにレポートが表示されます。

1. ツリー マップの [United States] ブロックを選択し、他の視覚化の関連する値がどのように強調表示されるかを確認します。

    ![強調表示されている Power BI レポート](media/tutorial-explore-report-server-web-portal/power-bi-report-server-power-bi.png)

### <a name="edit-in-power-bi-desktop"></a>Power BI Desktop で編集する

1. **[Power BI Desktop で編集]** を選択します。

1. **[許可]** を選択すると、この Web サイトで、このコンピューター上のプログラムを開くことができるようになります。 

     Power BI Desktop でレポートが開きます。 上部のバーに "Power BI Desktop (2019 年 1 月)" と表示されます。 これは Power BI Report Server 向けに最適化されたバージョンです。

    VM にインストールされているバージョンの Power BI Desktop を使用します。 レポートのアップロードのためにドメイン間を移動することはできません。

3. [フィールド] ウィンドウで Customers テーブルを展開し、Occupation フィールドをレポート レベル フィルターにドラッグします。

    ![フィールドを [フィルター] ウィンドウにドラッグする](media/tutorial-explore-report-server-web-portal/power-bi-report-server-desktop-filter.png)

1. レポートを保存します。

1. ブラウザーのレポートに戻り、ブラウザーの **[更新]** アイコンを選択します。

    ![ブラウザーの [更新] アイコン](media/tutorial-explore-report-server-web-portal/power-bi-report-server-browser-refresh.png)

8. 右側にある **[フィルター]** ウィンドウを展開し、追加した **Occupation** フィルターを表示します。 **Professional** を選択します。

    ![フィルター処理された Power BI レポート](media/tutorial-explore-report-server-web-portal/power-bi-report-server-power-bi-filtered.png)

3. **[参照]** を選択して Web ポータルに戻ります。

## <a name="paginated-rdl-reports"></a>ページ分割された (RDL) レポート

ページ分割されたレポートの表示と管理、レポート ビルダーの起動は、Web ポータルから実行できます。

### <a name="manage-a-paginated-report"></a>ページ分割されたレポートを管理する

1. Web ポータルの **[ページ分割されたレポート]** で、 **[Sales Order]** の横の **その他のオプション (...)**  >  **[管理]** を順に選択します。

1. **[パラメーター]** を選択し、**SalesOrderNumber** の既定値を「**SO50689**」に変更し >  **[適用]** を選択します。

   ![レポート パラメーターを設定する](media/tutorial-explore-report-server-web-portal/power-bi-report-server-set-parameters.png)

3. **[参照]** を選択して Web ポータルに戻ります。

### <a name="view-a-paginated-report"></a>ページ分割されたレポートを表示する

1. Web ポータルで **[Sales Order]** を選択します。
 
3.  設定した **Order** パラメーターには **SO50689** が表示されていることがわかります。 

    ![ページ分割されたレポートのパラメーター](media/tutorial-explore-report-server-web-portal/power-bi-report-server-paginated.png)

    既定値を変更せずに、このパラメーターを他のパラメーターと共に変更することができます。

1. **[Order** **SO48339]**  >  **[レポートの表示]** を選択します。

4. 2 ページ中 1 ページ目にあることがわかります。 右矢印を選択すると、2 ページ目が表示されます。 テーブルは 2 ページ目に続いています。

    ![ページ分割されたレポートのページ 2/2](media/tutorial-explore-report-server-web-portal/power-bi-report-server-paginated-2-of-2.png)

5. **[参照]** を選択して Web ポータルに戻ります。

### <a name="edit-a-paginated-report"></a>ページ分割されたレポートを編集する

レポート ビルダーでページ分割されたレポートを編集できます。また、レポート ビルダーはブラウザーから直接起動することができます。

1. Web ポータルで、 **[Sales Order]** の横の **その他のオプション (...)**  >  **[レポート ビルダーで編集]** を順に選択します。

1. **[許可]** を選択すると、この Web サイトで、このコンピューター上のプログラムを開くことができるようになります。

1. レポート ビルダーにデザイン ビューで Sales Order レポートが表示されます。

    ![デザイン ビュー、ページ分割されたレポート](media/tutorial-explore-report-server-web-portal/power-bi-report-server-paginated-design-view.png)

1. **[実行]** を選択してレポートをプレビューします。

    ![ページ分割されたレポートをプレビューする](media/tutorial-explore-report-server-web-portal/power-bi-report-server-paginated-preview.png)

5. レポート ビルダーを閉じてブラウザーに戻ります。

## <a name="view-excel-workbooks"></a>Excel ブックを表示する

Power BI Report Server で、Excel Online の Excel ブックを表示し、操作することができます。 

1. Excel ブック **Office Liquidation Sale.xlsx** を選択します。 資格情報の入力が求められることがあります。 **[キャンセル]** を選択します。 
    Web ポータルで開かれます。
1. スライサーで **[アプライアンス]** を選択します。

    ![Web ポータルでの Excel Online](media/tutorial-explore-report-server-web-portal/power-bi-report-server-excel-online.png)

1. **[参照]** を選択して Web ポータルに戻ります。

## <a name="clean-up-resources"></a>リソースをクリーンアップする

このチュートリアルを完了したら、リソース グループ、仮想マシン、およびすべての関連リソースを削除します。 

- 削除するには、VM のリソース グループを選択し、 **[削除]** を選択します。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、Power BI Report Server を使用して VM を作成しました。 Web ポータルの機能の一部を試し、各エディターで Power BI レポートとページ分割されたレポートを開きました。 この VM には、SQL Server Analysis Services データ ソースがインストールされているため、それと同じデータ ソースを使用して自身の Power BI とページ分割されたレポートの作成を試すことができます。 

Power BI Report Server のレポート作成についてさらに学習するには、次の記事に進んでください。

> [!div class="nextstepaction"]
> [Power BI Report Server の Power BI レポートの作成](./quickstart-create-powerbi-report.md)



