---
title: コンマ区切り値 (.csv) ファイルからデータを取得する
description: .csv ファイルから Power BI にデータを取得する方法を学習します
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 05/08/2019
LocalizationGroup: Data from files
ms.openlocfilehash: 01bef505d48f28df869bf2be705dcda963b3d0f9
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96403331"
---
# <a name="get-data-from-comma-separated-value-csv-files"></a>コンマ区切り値 (.csv) ファイルからデータを取得する
![CSV アイコン](media/service-comma-separated-value-files/csv_icon.png)

コンマ区切り値ファイルは、.csv とも呼ばれるシンプルなテキスト ファイルです。データは各行に配置され、各データのそれぞれの値がコンマで区切られた形となっています。 この種のファイルでは、ファイルのサイズを比較的小さく抑えつつ非常に多くのデータを入れておくことができるため、Power BI にとって理想的なデータ ソースの 1 つとなっています。 サンプルの .csv ファイルは[こちら](https://go.microsoft.com/fwlink/?LinkID=619356)からダウンロードできます。

.csv の用意ができたら、それをデータセットとして Power BI サイトで使ってみましょう。Power BI サイトでは、データの探索はもちろん、ダッシュボードを作成したり、得られた洞察を他の人と共有したりできます。

>[!TIP]
>多くの組織では、データを更新した .csv を毎日出力しています。 Power BI に置かれたデータセットと更新後のファイルとが常に正しく同期できるように、ファイルを OneDrive に保存するときには同じ名前を使用してください。

## <a name="where-your-file-is-saved-makes-a-difference"></a>ファイルの保存場所による違い
**ローカル** - コンピューターのローカル ドライブまたは組織内の別の場所に .csv ファイルを保存した場合、ファイルを Power BI に *インポート* できます。 実際はファイルがローカル ドライブに残ったままになるため、本当にファイル全体が Power BI にインポートされるわけではありません。 実際には、Power BI に新しいデータセットが作成され、.csv ファイルのデータがそのデータセットに読み込まれるという処理が発生しています。

**OneDrive - ビジネス用** - OneDrive for Business を利用していて、Power BI にサインインするときと同じアカウントを使ってサインインした場合、.csv ファイルの内容と Power BI のデータセット、レポート、およびダッシュボードとを最も効果的に同期できます。Power BI と OneDrive はどちらもクラウドにあるため、Power BI は約 1 時間ごとに OneDrive 上のファイルに *接続* します。 なんらかの変更が見つかった場合には、データセット、レポート、およびダッシュボードが Power BI で自動的に更新されます。

**OneDrive - 個人用** – OneDrive アカウントにファイルを保存すると、OneDrive for Business の場合と同じメリットが多数得られます。 最も大きな違いは、([データの取得]、[ファイル]、[OneDrive - 個人用] の順に選択して) ファイルに初めて接続するときに、Microsoft アカウントを使って OneDrive にサインインする必要があるという点です (このアカウントは通常、Power BI へのサインインに使うものとは異なります)。 Microsoft アカウントを使って OneDrive にサインインするときは、[サインインしたままにする] オプションを必ず選択してください。 これにより、Power BI は、約 1 時間ごとにファイルに接続して、Power BI のデータセットの同期を保つことができます。

**SharePoint チーム サイト** – Power BI Desktop のファイルを SharePoint – チーム サイトに保存することは、OneDrive for Business に保存することとほぼ同じです。 最も大きな違いは、Power BI からファイルに接続する方法にあります。 URL を指定したり、ルート フォルダーに接続したりできます。

## <a name="import-or-connect-to-a-csv-file"></a>.csv ファイルのインポートまたは .csv ファイルへの接続
>[!IMPORTANT]
>Power BI にインポートできるファイルの最大サイズは 1 GB です。

1. Power BI の [ナビゲーター] ウィンドウで、 **[データの取得]** をクリックします。
   
   ![ナビ ペインのボタンを示す、Power B I Desktop の [データの取得] のスクリーンショット。](media/service-comma-separated-value-files/csv_get_data_button.png)
2. **[ファイル]** 、 **[取得]** の順にクリックします。
   
   ![[ファイル] ダイアログのスクリーンショット。[取得] ボタンが表示されています。](media/service-comma-separated-value-files/csv_files_get.png)
3. 目的のファイルを見つけます。
   
   ![ファイルを見つけるための 4 つのタイルのスクリーンショット。ローカル ファイル、OneDrive Business、OneDrive Personal、SharePoint から選択できます。](media/service-comma-separated-value-files/csv_find_your_file.png)

## <a name="next-steps"></a>次の手順
**データの探索** - ファイルのデータを Power BI に取得したら、次は探索です。 新しいデータセットを右クリックして **[探索]** をクリックします。

**更新のスケジュール設定** - ファイルをローカル ドライブに保存した場合には、更新スケジュールを設定することによって、Power BI 内のデータセットとレポートを最新の状態に保つことができます。 詳しくは、「[Power BI でのデータの更新](refresh-data.md)」をご覧ください。 Power BI は、ファイルが OneDrive に保存されると約 1 時間ごとに自動でそのファイルと同期します。

