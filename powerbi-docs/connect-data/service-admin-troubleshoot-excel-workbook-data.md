---
title: 'エラー: Excel ブックにデータが見つかりませんでした'
description: 'エラー: Excel ブックにデータが見つかりませんでした'
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: troubleshooting
ms.date: 04/30/2019
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 6e78dba3e6a18544f68fae4b737a7840d1fa2724
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96403791"
---
# <a name="error-we-couldnt-find-any-data-in-your-excel-workbook"></a>エラー: Excel ブックにデータが見つかりませんでした

>[!NOTE]  
>この記事は、Excel 2007 以降に適用されます。

Power BI に Excel ブックをインポートするとき、次のエラーが生じることがあります。

*エラー:テーブルとして書式設定されたデータが見つかりませんでした。Excel から Power BI サービスにインポートするには、データをテーブルとして書式設定する必要があります。テーブルで必要なすべてのデータを選択し、Ctrl + T キーを押します。*

![ブックにデータが見つからない](media/service-admin-troubleshoot-excel-workbook-data/power-bi-we-couldnt-find-any-data.png)

## <a name="quick-solution"></a>クイック ソリューション
1. Excel でブックを編集します。
2. データを含むセルの範囲を選択します。 最初の行には、列のヘッダー (列名) が含まれている必要があります。
3. **Ctrl + T** キーを押して、テーブルを作成します。
4. ブックを保存します。
5. Power BI に戻り、ブックを再びインポートします。または、Excel 2016 を使用していて、ブックを OneDrive for Business に保存した場合は、Excel で [ファイル]、[発行] の順にクリックします。

## <a name="details"></a>詳細
### <a name="cause"></a>原因
Excel では、特定のセルの範囲から **テーブル** を作成できます。これにより、並べ替え、フィルター処理、およびデータの書式設定が簡単になります。

Excel ブックをインポートするとき、Power BI はそれらのテーブルを検索してデータセットにインポートします。テーブルが見つからない場合は、このエラー メッセージが表示されます。

### <a name="solution"></a>解決方法
1. Excel でブックを開きます。 
    >[!NOTE]
    >この図は Excel 2013 のものです。 他のバージョンを使用している場合、表示は少し異なりますが、手順は同じです。
    
    ![ブックを開く](media/service-admin-troubleshoot-excel-workbook-data/power-bi-troubleshoot-excel-worksheet-1.png)
2. データを含むセルの範囲を選択します。 最初の行には、列のヘッダー (列名) が含まれている必要があります。
   
    ![セルの範囲の選択](media/service-admin-troubleshoot-excel-workbook-data/power-bi-troubleshoot-excel-worksheet-2.png)
3. **[挿入]** タブのリボンで、 **[テーブル]** をクリックします  (または、ショートカットの **Ctrl + T** キーを押します)。
   
    ![テーブルの挿入](media/service-admin-troubleshoot-excel-workbook-data/power-bi-troubleshoot-excel-worksheet-3.png)
4. 次のダイアログ ボックスが表示されます。 **[先頭行をテーブルの見出しとして使用する]** にチェックマークが付いていることを確認して、 **[OK]** を選択します。
   
    ![テーブルの作成](media/service-admin-troubleshoot-excel-workbook-data/power-bi-troubleshoot-excel-create-table.png)
5. これで、データはテーブルとして書式設定されました。
   
    ![テーブルとして書式設定されたデータ](media/service-admin-troubleshoot-excel-workbook-data/power-bi-troubleshoot-excel-table.png)
6. ブックを保存します。
7. Power BI に戻ります。 ナビ ペインの下部にある [データの取得] を選択します。
   
    ![データを取得](media/service-admin-troubleshoot-excel-workbook-data/power-bi-get-data.png)
8. **[ファイル]** ボックスで、 **[取得]** を選択します。
   
    ![ファイルの取得](media/service-admin-troubleshoot-excel-workbook-data/power-bi-get-files.png)
9. Excel ブックを再度インポートします。 今回は、インポートでテーブルが見つかり、成功するはずです。
   
    インポートがまだ失敗する場合は、ヘルプ メニューの **[コミュニティ]** をクリックして通知してください。
   
    ![[コミュニティ] リンク](media/service-admin-troubleshoot-excel-workbook-data/power-bi-question-menu-community.png)
