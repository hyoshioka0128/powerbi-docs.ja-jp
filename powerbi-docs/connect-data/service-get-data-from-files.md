---
title: ファイルから Power BI 用のデータを取得する
description: Excel、Power BI Desktop、.csv ファイルから Power BI にデータを取得する方法について学習します
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 05/08/2019
LocalizationGroup: Data from files
ms.openlocfilehash: 2ed532986dd31e97e535f27d70c9f5cfd8c66fd5
ms.sourcegitcommit: 24887643bd3e1b3749ce325dc0ae407432d7fee4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100489879"
---
# <a name="get-data-from-files-for-power-bi"></a>ファイルから Power BI 用のデータを取得する
![Excel、Power B I Desktop、および CSV アイコン](media/service-get-data-from-files/file_icons.png)

Power BI が接続したり、データやレポートをインポートしたりできるファイルは 3 種類あります。

* Microsoft Excel (.xlsx、または .xlsm)
* Power BI Desktop (.pbix)
* コンマ区切り値 (.csv)

## <a name="what-does-get-data-from-a-file-really-mean"></a>ファイルからデータを取得することの意味
Power BI で探索するデータは、データセットから取得します。 しかし、データセットを用意するには、最初にいくつかのデータを取得する必要があります。 この記事では、ファイルからデータを取得する操作を中心に説明します。

データセットの重要性とそのデータを取得する方法についてより深く理解するために、自動車を例として考えてみましょう。 車のシートに座り、ダッシュボードを眺めてみましょう。 これは、コンピューターの前に座って Power BI のダッシュボードを見ているのとよく似ています。 ダッシュボードには、エンジンの回転数、温度、使っているギア、走行速度など、車の動作状態に関するいろいろな情報が表示されます。

Power BI では、データセットは車のエンジンのようなものです。 データセットは、データ、メトリック、および Power BI ダッシュボードに表示される情報を提供します。 もちろん、エンジン (つまりデータセット) には燃料が必要です。Power BI で燃料となるのがデータです。 車には、エンジンにガソリンを供給する燃料タンクがあります。 同様に、Power BI でも、データセットにデータを供給できる燃料タンクが必要です。 ここで燃料タンクに相当するのが、Power BI Desktop ファイル、Excel ブック ファイル、または .csv ファイルです。

さらに話を進めましょう。 車の燃料タンクにはガソリンを入れる必要があります。 Power BI Desktop ファイル、Excel ファイル、または .csv ファイルに入れるガソリンに相当するのは、別のデータ ソースからのデータです。 つまり、別のデータ ソースからデータを取得して、Excel、Power BI Desktop、または .csv ファイルにデータを格納することになります。 Excel ブックまたは .csv ファイルの場合は、データ行を手動で入力できます。 また、外部データ ソースに接続してデータを照会し、ファイルにデータを読み込むこともできます。 データが入ったファイルを準備できたら、これをデータセットとして Power BI に取得することができます。

> [!NOTE]
> Excel ブックのデータは、Power BI によってインポートされるテーブルまたはデータ モデル内に存在する必要があります。
> 
> 

## <a name="where-your-file-is-saved-makes-a-difference"></a>ファイルの保存場所による違い
**ローカル** - コンピューターのローカル ドライブまたは組織内の別の場所にファイルを保存した場合、ファイルを Power BI に *インポート* できます。 実際はファイルがローカル ドライブに残ったままになるため、本当にファイル全体が Power BI にインポートされるわけではありません。 実際には、Power BI サイトに新しいデータセットが作成され、データ (場合によってはデータ モデル) がデータセットに読み込まれるという処理が発生しています。 ファイルにレポートが含まれている場合、これらのレポートは Power BI サイトの [レポート] に表示されます。

**OneDrive - ビジネス用** – OneDrive for Business を利用していて、Power BI にサインインするときと同じアカウントを使ってサインインした場合、Excel、Power BI Desktop、または .csv ファイル内の作業内容と Power BI のデータセット、レポート、およびダッシュボードとを最も効果的に同期できます。Power BI と OneDrive はどちらもクラウドにあるため、Power BI は約 1 時間ごとに OneDrive 上のファイルに接続します。 なんらかの変更が見つかった場合には、データセット、レポート、およびダッシュボードが Power BI で自動的に更新されます。

**OneDrive - 個人用** – OneDrive アカウントにファイルを保存すると、OneDrive for Business の場合と同じメリットが多数得られます。 最も大きな違いは、([データの取得]、[ファイル]、[OneDrive - 個人用] の順に選択して) ファイルに初めて接続するときに、Microsoft アカウントを使って OneDrive にサインインする必要があるという点です (このアカウントは通常、Power BI へのサインインに使うものとは異なります)。 Microsoft アカウントを使って OneDrive にサインインするときは、[サインインしたままにする] オプションを必ず選択してください。 これにより、Power BI は、約 1 時間ごとにファイルに接続して、Power BI のデータセットの同期を保つことができます。

**SharePoint チーム サイト** – Power BI Desktop のファイルを SharePoint – チーム サイトに保存することは、OneDrive for Business に保存することとほぼ同じです。 最も大きな違いは、Power BI からファイルに接続する方法にあります。 URL を指定したり、ルート フォルダーに接続したりできます。

## <a name="ready-to-get-started"></a>さあ、始めてみましょう。
ファイルを Power BI に取得する方法について詳しくは、次の記事をご覧ください。

* [Excel ブック ファイルからデータを取得する](service-excel-workbook-files.md)
* [Power BI Desktop ファイルからデータを取得する](service-desktop-files.md)
* [コンマ区切り値 (.csv) ファイルからデータを取得する](service-comma-separated-value-files.md)

