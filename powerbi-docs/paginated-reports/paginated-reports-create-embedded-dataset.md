---
title: Power BI のページ分割されたレポート用の埋め込みデータセットを作成する
description: この記事では、埋め込みデータ ソースに基づいて、Power BI サービスのページ分割されたレポート用の埋め込みデータセットを作成する方法について説明します。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: how-to
ms.date: 11/5/2018
ms.openlocfilehash: 81d755a529edb2f4fdae0ae6dbe90026b5b290d8
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2020
ms.locfileid: "93297678"
---
# <a name="create-an-embedded-dataset-for-a-paginated-report-in-the-power-bi-service"></a>Power BI サービスのページ分割されたレポート用の埋め込みデータセットを作成する

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

この記事では、埋め込みデータ ソースに基づいて、Power BI サービスのページ分割されたレポート用の埋め込みデータセットを作成する方法について説明します。 埋め込みデータセットは、1 つのページ分割されたレポートに (そのレポートで使用するために) 含まれています。 現時点では、Power BI サービスに発行されるページ分割されたレポートには、埋め込みデータセットと埋め込みデータ ソースが必要です。 埋め込みデータ ソースとデータセットは、レポートの作成時に Power BI レポート ビルダーで作成します。 

データセットを作成する前にデータ ソースを作成する必要があります。 方法については、Power BI サービスの[ページ分割されたレポートの埋め込みデータ ソース](paginated-reports-embedded-data-source.md)に関するページを参照してください。
  
## <a name="create-an-embedded-dataset"></a>埋め込みデータセットを作成する
  
1. Power BI レポート ビルダーのレポート データ ペインで、 **[新規作成]**  >  **[データセット]** を選択します。

1. **[データセットのプロパティ]** ダイアログ ボックスの **[クエリ]** タブで、データセットの名前を指定します。 埋め込みデータ ソースは既に **[データ ソース]** ボックスに表示されています。または、 **[新規作成]** を選択して別の埋め込みデータ ソースを作成することもできます。
 
   ![新しいデータセット](media/paginated-reports-create-embedded-dataset/power-bi-paginated-new-dataset.png)  

3. **[クエリの種類]** で、データセットに使用するコマンドまたはクエリの種類を選択します。 
    - **[テキスト]** では、データベースからデータを取得するクエリを実行します。 これが既定値であり、ほとんどのクエリに使用されます。 クエリを入力するか、 **[インポート]** を選択して既存のクエリをインポートします。 クエリをグラフィカルに作成するには、 **[クエリ デザイナー]** を選択します。 クエリ デザイナーを使用してクエリを作成する場合は、クエリのテキストがこのボックスに表示されます。 式を使用してクエリを動的に生成するには、 **[式]** ( **fx** ) ボタンを選択します。 
    - **[テーブル]** では、テーブル内のすべてのフィールドを選択します。 データセットとして使用するテーブルの名前を入力します。
    - **[ストアド プロシージャ]** では、ストアド プロシージャを名前で実行します。

4. クエリ デザイナーでは、データセット内のテーブルとフィールドの参照および操作、クエリのインポート、またはテキストとしての編集を行うことができます。 ここでフィルターとパラメーターを追加することもできます。 

    ![クエリ デザイナー](media/paginated-reports-create-embedded-dataset/power-bi-paginated-embedded-dataset-edit-query.png)

5. クエリ デザイナーで、 **[クエリの実行]** を選択してクエリをテストし、 **[OK]** を選択します。

1. [データセットのプロパティ] ダイアログ ボックスに戻り、 **[タイムアウト (秒)]** ボックスにクエリがタイムアウトするまでの秒数を入力します。既定値は 30 秒です。 **[タイムアウト]** には、値を指定しないか、0 より大きい値を指定する必要があります。 空の場合は、クエリはタイムアウトしません。

7.  その他のタブでは、データセットの他のプロパティを設定できます。
    - **[フィールド]** タブで計算フィールドを作成します。
    - **[オプション]** タブで詳細設定オプションを設定します。
    - **[フィルター]** タブと **[パラメーター]** タブで、それぞれフィルターとパラメーターを追加または更新します。

8. **[OK]** を選択します。
 
   レポートがレポート デザイン ビューで開きます。 データ ソース、データセット、およびデータセット フィールド コレクションがレポート データ ペインに表示され、ページ分割されたレポートのデザインを続行することができます。  

    ![レポート デザイン ビューに表示されたデータセット](media/paginated-reports-create-embedded-dataset/power-bi-paginated-embedded-dataset-report-design-view.png) 
 
## <a name="next-steps"></a>次の手順 

- [Power BI Premium のページ分割されたレポートとは](paginated-reports-report-builder-power-bi.md)  
- [チュートリアル: ページ分割されたレポートを作成して Power BI サービスにアップロードする](paginated-reports-quickstart-aw.md)
- [ページ分割されたレポートを Power BI サービスに発行する](paginated-reports-save-to-power-bi-service.md)

