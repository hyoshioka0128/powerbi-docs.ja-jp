---
title: Power BI Desktop とは何ですか?
description: Power BI Desktop と使用を開始する方法について説明します。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-fundamentals
ms.topic: overview
ms.date: 07/23/2020
LocalizationGroup: Get started
ms.openlocfilehash: 07dba29c57b533537513d84361b4b7b2b61f9221
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2021
ms.locfileid: "99088122"
---
# <a name="what-is-power-bi-desktop"></a>Power BI Desktop とは何ですか?

*Power BI Desktop* はローカル コンピューターにインストールする無料のアプリケーションで、データへの接続、変換、および視覚化を行うことができます。 Power BI Desktop を使用すると、複数の異なるデータ ソースに接続し、それらを組み合わせて (多くの場合、"*モデリング*" と呼ばれます)、データ モデルに結合できます。 このデータ モデルを使用すると、ビジュアルおよびビジュアル コレクションを作成でき、レポートとして、組織内の他のユーザーと共有できます。 Business Intelligence プロジェクトに取り組んでいるほとんどのユーザーは、Power BI Desktop を使用してレポートを作成した後、"*Power BI サービス*" を使用して、レポートを他のユーザーと共有します。

![サンプル データを表示している Power BI Desktop のスクリーンショット。](media/desktop-what-is-desktop/what-is-desktop_01.png)

Power BI Desktop の最も一般的な使い方を次に示します。

* データに接続する
* データの変換とクリーニングを行って、データ モデルを作成する
* データの視覚的表現を示すグラフなどのビジュアルを作成する
* ビジュアルのコレクションである 1 ページまたは複数ページのレポートを作成する
* Power BI サービスを使用して、レポートを他のユーザーと共有する

このようなタスクを最も担当する人物は、多くの場合、"*データ アナリスト*" ("*アナリスト*" と呼ばれることもあります) または Business Intelligence プロフェッショナル (多くの場合 "*レポート作成者*" と呼ばれます) であるとみなされます。 ところが、自身をアナリストでもレポート作成者でもないと考えている多くの人々が、Power BI Desktop を使用すると、説得力のあるレポートを作成したり、さまざまなソースからデータをプルしてデータ モデルを作成したりして、同僚や組織と共有することができます。


> [!IMPORTANT]
> Power BI Desktop は、お客様のフィードバックと新機能を組み込み、月単位で更新およびリリースされます。 サポート対象の Power BI Desktop は、最新バージョンのみです。お客様が Power BI Desktop に関してサポートに問い合わせた場合、最新バージョンにアップグレードするように求められます。 最新バージョンの Power BI Desktop は、[Windows ストア](https://aka.ms/pbidesktopstore)から入手するか、またはサポートされているすべての言語を含む 1 つの実行可能ファイルとして[ダウンロード](https://www.microsoft.com/download/details.aspx?id=58494)してお使いのコンピューターにインストールできます。


Power BI Desktop で使用できるビューは 3 つあり、キャンバスの左側で選択します。 ビューは、次の順に表示されます。
* **[Report]\(レポート\)** : このビューでは、レポートとビジュアルを作成します。作成時間の大半はここで費やされます。
* **データ**:このビューでは、レポートに関連付けられているデータ モデルで使用されるテーブル、メジャー、その他のデータが表示され、レポートのモデルで最適に使用できるようにデータを変換します。
* **モデル**:このビューでは、データ モデル内のテーブル間のリレーションシップを表示および管理します。

次の画面は、キャンバスの左側に沿って 3 つのビューが表示されています。

![3 つのビューのパネルを表示している Power BI Desktop のスクリーンショット。](media/desktop-what-is-desktop/what-is-desktop-07.png)
 

## <a name="connect-to-data"></a>データに接続する
Power BI Desktop の使用を開始するには、最初にデータに接続します。 Power BI Desktop から接続できるデータ ソースには、たくさんの種類があります。 

データに接続するには:

1. **[ホーム]** リボンで、 **[データの取得]**  >  **[すべて表示]** を選択します。 

   **[データの取得]** ウィンドウが表示され、Power BI Desktop で接続できる多くのカテゴリが表示されます。

   ![[データを取得] ダイアログ ボックスを表示している Power BI Desktop のスクリーンショット。](media/desktop-what-is-desktop/what-is-desktop_02.png)

2. データの種類を選択すると、Power BI Desktop がデータ ソースに接続するために必要な、URL や資格情報などの情報の入力を求められます。

   ![[SQL Server Database] ダイアログ ボックスを表示している Power BI Desktop のスクリーンショット。](media/desktop-what-is-desktop/what-is-desktop_03.png)

3. 1 つまたは複数のデータ ソースに接続したら、都合よく利用できるようにデータを変換できます。

## <a name="transform-and-clean-data-create-a-model"></a>データの変換とクリーニング、モデルの作成

Power BI Desktop では、組み込みの [Power Query エディター](../transform-model/desktop-query-overview.md)を使用して、データのクリーンアップと変換ができます。 Power Query エディターでは、データに対して、データ型の変更、列の削除、複数のソースのデータの結合などの変更を行います。 作業は彫刻に似ています。大きな土 (データ) の塊から始めて、望みどおりになるまで、不要な部分を削り、必要な部分を付け加えて、データを整形していきます。 

Power Query エディターを起動するには:

- **[ホーム]** リボンの **[クエリ]** セクションで、 **[データの変換]** を選択します。

   **[Power Query エディター]** ウィンドウが表示されます。

   ![[Power Query エディター] ウィンドウを表示している Power BI Desktop のスクリーンショット。](media/desktop-getting-started/designer_gsg_editquery.png)

データの変換 (テーブル名の変更、データ型の変換、列の削除など) を実行する手順が、Power Query エディターによって記録されます。 このクエリがデータ ソースに接続するたびに、これらの手順が実行され、データが常に指定したとおりに整形されます。

次の画面は、 **[Power Query エディター]** ウィンドウに、整形され、モデルに変換されたクエリが表示されています。

 ![クエリが整形された [Power Query エディター] ウィンドウを表示している Power BI Desktop のスクリーンショット。](media/desktop-getting-started/shapecombine_querysettingsfinished.png)

データが望みどおりになったら、ビジュアルを作成できます。 

## <a name="create-visuals"></a>ビジュアルの作成 

データ モデルを作成したら、レポート キャンバスに "*フィールド*" をドラッグして、"*ビジュアル*" を作成できます。 ビジュアルは、モデル内のデータのグラフィック表現です。 Power BI Desktop から選択できるビジュアルには、さまざまな種類があります。 次のビジュアルは、単純な縦棒グラフを示しています。 

![サンプルの横棒グラフを表示している Power BI Desktop のスクリーンショット。](media/desktop-what-is-desktop/what-is-desktop_04.png)

ビジュアルを作成または変更するには: 

- **[視覚化]** ペインで、ビジュアル アイコンを選択します。 

   ![[視覚化] ペインを表示している Power BI Desktop のスクリーンショット。](media/desktop-what-is-desktop/what-is-desktop_05.png)

   レポート キャンバスでビジュアルが既に選択されている場合は、選択されているビジュアルが選択した種類に変更されます。 

   キャンバスでビジュアルが選択されていない場合は、選択した内容に基づいて新しいビジュアルが作成されます。


## <a name="create-reports"></a>レポートの作成

多くの場合、Power BI Desktop でモデルを作成するために使用しているデータのさまざまな側面を示すビジュアルのコレクションを作成します。 1 つの Power BI Desktop ファイル内のビジュアルのコレクションは "*レポート*" と呼ばれます。 レポートは、Excel ファイルが 1 つ以上のワークシートを持つことができるのと同じように、1 つまたは複数のページを持つことができます。

Power BI Desktop を使用すると、複数のソースのデータを使用して、ビジュアルが豊富な複雑なレポートを作成し、すべてを 1 つのレポートにまとめて、組織内の他のユーザーと共有できます。

次の画面は、Power BI Desktop レポートの最初のページを示しています。画面の下部にあるタブからわかるように、 **[概要]** という名前です。 

![[概要] タブを表示している Power BI Desktop のスクリーンショット。](media/desktop-what-is-desktop/what-is-desktop_01.png)

## <a name="share-reports"></a>レポートの共有

レポートを他のユーザーと共有する準備ができたら、レポートを Power BI サービスに "*発行*" し、組織内で Power BI ライセンスを持つすべてのユーザーが利用できるようにします。 

Power BI Desktop レポートを発行するには: 

1. **[ホーム]** リボンで、 **[発行]** をクリックします。

   ![[発行] ボタンを表示している Power BI Desktop のスクリーンショット。](media/desktop-what-is-desktop/what-is-desktop_06.png)

   Power BI Desktop により、お使いの Power BI アカウントで Power BI サービスに接続されます。 

2. Power BI から、ワークスペース、チーム ワークスペース、Power BI サービス内のその他の場所など、レポートを共有する Power BI サービス内の場所を選択するように求められます。 

   Power BI サービスにレポートを共有するには、Power BI ライセンスが必要です。


## <a name="next-steps"></a>次の手順

Power BI Desktop の使用を開始するには、まず、アプリケーションをダウンロードしてインストールする必要があります。 Power BI Desktop の取得方法は 2 つあります。

* [Windows ストアから Power BI Desktop を取得する](https://aka.ms/pbidesktopstore)
* [Web から Power BI Desktop をダウンロードする](https://www.microsoft.com/download/details.aspx?id=58494)
