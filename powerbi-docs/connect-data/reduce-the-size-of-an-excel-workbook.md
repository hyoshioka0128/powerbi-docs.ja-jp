---
title: Power BI で表示する Excel ブックのサイズを減らす
description: Power BI で表示する Excel ブックのサイズを減らす
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 01/10/2019
LocalizationGroup: Data from files
ms.openlocfilehash: 9996b8e3f571a04dc41d138947532f3ab402057a
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96404090"
---
# <a name="reduce-the-size-of-an-excel-workbook-to-view-it-in-power-bi"></a>Power BI で表示する Excel ブックのサイズを減らす
1 GB 未満のすべての Excel ブックを Power BI にアップロードできます。 Excel ブックは 2 つの部分で構成されていることがあります。つまり、データ モデルと、レポートの残りの部分 (コアなワークシート コンテンツ) です。 レポートが次のサイズの制限を満たしている場合は、**OneDrive for Business** に保存して、Power BI からこれに接続し、Excel Online で表示できます。

* ブック全体のサイズは最大 1 GB まで許容されます。
* コアなワークシート コンテンツのサイズは最大 30 MB まで許容されます。

## <a name="what-makes-core-worksheet-contents-larger-than-30-mb"></a>コアなワークシート コンテンツが 30 MB を超える原因
コアなワークシート コンテンツが 30 MB を超える原因となり得る要素をいくつか示します。

* 画像。
* 影付きセル。 [セルの網掛け形式を削除](https://support.office.com/article/Add-or-change-the-background-color-of-cells-ac10f131-b847-428f-b656-d65375fb815e)します。
* 色付けされたワークシート。 [シートの背景を削除](https://support.office.com/article/add-or-remove-a-sheet-background-3577a762-8450-4556-96a2-cc265abc00a8)します。
* テキスト ボックス。
* クリップ アート。

できれば、これらの要素を削除することをご検討ください。 

レポートにデータ モデルがある場合は、その他のいくつかのオプションがあります。 

* Excel ワークシートからデータを削除し、代わりに、データ モデルに格納します。 詳しくは、以下の「ワークシートからデータを削除する」をご覧ください。 
* [メモリ効率の高いデータ モデルを作成](https://support.office.com/article/Create-a-memory-efficient-Data-Model-using-Excel-2013-and-the-Power-Pivot-add-in-951c73a9-21c4-46ab-9f5e-14a2833b6a70)して、レポート全体のサイズを減らします。

これらの変更のいずれかを行うには、Excel でブックを編集する必要があります。

[SharePoint Online での Excel ブックのファイル サイズ制限](https://support.office.com/article/File-size-limits-for-workbooks-in-SharePoint-Online-9e5bc6f8-018f-415a-b890-5452687b325e)についての詳しい情報をご覧ください。

## <a name="remove-data-from-worksheets"></a>ワークシートからデータを削除する
[Power Query] タブまたは [Excel データ] タブから Excel にデータをインポートする場合、ブックは Excel テーブルとデータ モデルで同じデータを持つ場合があります。 Excel ワークシートに大きなテーブルが含まれていると、コアなワークシート コンテンツが 30 MB を超える場合があります。 Excel でテーブルを削除して、データをデータ モデルに保持することで、レポートのコアなワークシート コンテンツを大幅に削減できます。 

データを Excel にインポートするときには、次の手順に従います。

* **Power Query で**: **[ワークシートへの読み込み]** ボックスをオフにします。
  
  データはデータ モデルにのみインポートされ、Excel ワークシートにデータは入りません。
* **[Excel データ] タブから**、以前にインポート ウィザードで **[テーブル]** をオンにした場合: **[既存の接続]** に移動し、\>接続をクリックして、\> **[接続の作成のみ]** をクリックします。 元のテーブルまたは最初のインポート中に作成されたテーブルを削除します。
* **[Excel データ] タブから**、 **[Import Data]** (データのインポート) ボックスの **[Table]** (テーブル) をチェックしないでください。

## <a name="workbook-size-optimizer"></a>ブック サイズ オプティマイザー
ブックにデータ モデルが含まれている場合は、ブック サイズ オプティマイザーを実行してブックのサイズを小さくすることができます。 [ブック サイズ オプティマイザーをダウンロードする](https://www.microsoft.com/download/details.aspx?id=38793)。

## <a name="related-info"></a>関連情報
[メモリ効率の高いデータ モデルを作成する](https://support.office.com/article/Create-a-memory-efficient-Data-Model-using-Excel-2013-and-the-Power-Pivot-add-in-951c73a9-21c4-46ab-9f5e-14a2833b6a70)

[Power BI Desktop で OneDrive for Business リンクを使用する](desktop-use-onedrive-business-links.md)

