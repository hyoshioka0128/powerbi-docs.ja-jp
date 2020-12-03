---
title: Power BI Desktop で日付テーブルを設定し、使用する
description: Power BI Desktop でテーブルを日付テーブルとして設定する方法とその意味について説明します。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: conceptual
ms.date: 05/08/2019
LocalizationGroup: Model your data
ms.openlocfilehash: 1a0782e7a80cc8d2cc824effe07a99df7ec64785
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415820"
---
# <a name="set-and-use-date-tables-in-power-bi-desktop"></a>Power BI Desktop で日付テーブルを設定し、使用する

**Power BI Desktop** は裏側で動作し、日付を表す列が自動的に識別され、ユーザーの代わりに、モデルの日付階層やその他の有効化メタデータが作成されます。 ビジュアル、テーブル、クイック メジャー、スライサーなど、レポート機能を作成するとき、内蔵されているこれらの階層を利用できます。 Power BI Desktop では、非表示テーブルを自動作成することでこれを行います。その後、ユーザーは自分のレポートや DAX 式でテーブルを利用できます。

この自動で行われる動作の詳細については、「[Power BI Desktop の自動の日付/時刻](desktop-auto-date-time.md)」の記事を参照してください。

データ アナリストの多くは、独自の日付テーブルを作成することを好みます。それには何の問題もありません。 **Power BI Desktop** では、モデルに **日付テーブル** として使用させるテーブルを指定し、その後、そのテーブルの日付データを利用し、日付関連のビジュアル、テーブル、クイック メジャーなどを作成できます。 独自の日付テーブルを指定すると、モデルで作成した日付階層を制御し、**クイック メジャー** やモデルの日付テーブルを利用するその他の操作で利用できます。

![[日付テーブルとしてマーク] ダイアログ ボックスを示す、Power BI Desktop のスクリーンショット。](media/desktop-date-tables/date-tables_01.png)

## <a name="setting-your-own-date-table"></a>独自の日付テーブルを設定する

**日付テーブル** を設定するには、 **[フィールド]** ウィンドウで日付テーブルとして使用するテーブルを選択し、そのテーブルを右クリックし、メニューが表示されたら、 **[日付テーブルとしてマークする]、[日付テーブルとしてマークする]** の順に選択します。次の画像を参考にしてください。

![[フィールド] ペインの [日付テーブルとしてマーク] フィルター オプションを示す、Power BI Desktop のスクリーンショット。](media/desktop-date-tables/date-tables_02.png)

次の画像のように、テーブルを選択し、 **[モデリング]** リボンから **[日付テーブルとしてマークする]** を選択することもできます。

![[日付テーブルとしてマークする] ボタンとオプションのフィルターを示す、Power BI Desktop のスクリーンショット。](media/desktop-date-tables/date-tables_02b.png)

独自の **日付テーブル** を指定すると、Power BI Desktop はその列とそのデータに次の検証を実行して次のことを確認します。

* データに含まれる値が一意である
* データに null 値が含まれていない
* データの日付値が連続している (始めから終わりまで)
* 日付の種類が **[日付/時刻]** の場合、各値でタイムスタンプが同じになる

独自の日付テーブルを作成するとき、2 つのシナリオが考えられます。いずれも妥当なアプローチです。

* 最初のシナリオは、基本的な日付テーブルと階層を使用するというものです。 これはユーザーのデータの中で、先に説明した日付テーブルの検証基準を満たすテーブルです。 

* 2 番目のシナリオは、Analysis Services のテーブルを使用するというものです。たとえば、日付テーブルとして *dim date* フィールドを使用します。 

日付テーブルを指定すると、そのテーブルのどの列が日付列か選択できます。 使用する列を指定するには、 **[フィールド]** ウィンドウでテーブルを選択し、そのテーブルを右クリックし、 **[日付テーブルとしてマークする]、[日付テーブルの設定]** の順に選択します。 次のウィンドウが表示されます。このウィンドウで、ドロップダウン ボックスから日付テーブルとして使用する列を選択できます。

![重要な注意事項を含む [日付テーブルとしてマーク] ダイアログ ボックスを示す、Power BI Desktop のスクリーンショット。](media/desktop-date-tables/date-tables_03.png)

重要なことですが、独自の日付テーブルを指定するとき、**Power BI Desktop** は階層を自動作成しません (指定しなければ自動的にモデルに組み込まれます)。 後で日付テーブルを選択解除した場合 (手動設定の日付テーブルがなくなった場合)、Power BI Desktop は、テーブルの日付列に対して、自動作成の日付テーブルを自動的に再作成します。

これも重要なことですが、テーブルを日付テーブルとしてマークすると、Power BI Desktop によって作成された組み込みの (自動作成の) 日付テーブルが削除されます。そのような組み込みのテーブルに基づいて以前にビジュアルや DAX 式を作成した場合、それらは正しく機能しなくなります。 

## <a name="marking-your-date-table-as-the-appropriate-data-type"></a>適切なデータ型として日付テーブルをマークする

独自の **日付テーブル** を指定するとき、データ型が正しく設定されていることを確認する必要があります。 たとえば、 **[データ型]** を **[日付/時刻]** や **[日付]** に設定します。 これは次の手順で行います。

1. **[フィールド]** ウィンドウから **日付テーブル** を選択し、必要に応じて展開し、日付として使用する列を選択します。
   
    ![[フィールド] ペインの日付フィルターを示す Power BI Desktop のスクリーンショット。](media/desktop-date-tables/date-tables_04.png) 

2. **[モデリング]** タブで **[データ型]** を選択し、ドロップダウン矢印をクリックして選択できるデータ型を表示します。

    ![[データ型] のフィルターが選択された [モデリング] タブを示す、Power BI Desktop のスクリーンショット。](media/desktop-date-tables/date-tables_05.png)

3. 列のデータ型を指定します。 


## <a name="next-steps"></a>次の手順

この記事に関する詳細については、次のリソースを参照してください。

* [Power BI Desktop の自動の日付/時刻](desktop-auto-date-time.md)
* [Power BI Desktop で日付テーブルを作成する](../guidance/model-date-tables.md)
* [Power BI Desktop でのデータ型](../connect-data/desktop-data-types.md)
* わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
* Power BI チームへのご提案は、 [Power BI を改善するためのアイデアをお寄せください](https://ideas.powerbi.com/)
