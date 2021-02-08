---
title: Power BI レポートのフィルターと強調表示
description: Power BI レポートのフィルターと強調表示について
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 01/29/2021
LocalizationGroup: Reports
ms.openlocfilehash: 572bbc8b24fc3ebf8ee2890480eff25eab87d37d
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2021
ms.locfileid: "99087823"
---
# <a name="filters-and-highlighting-in-power-bi-reports"></a>Power BI レポートのフィルターと強調表示
 この記事では、Power BI サービスでのフィルター処理と強調表示の概要を示します。 操作は Power BI Desktop の場合とほぼ同じです。 *フィルター処理* を実行すると、絞り込んだデータ以外のすべてのデータが削除されます。 一般に、"*強調表示*" はフィルター処理ではありません。 ほとんどのビジュアルでは、関連のないデータは削除されません。 代わりに、関連するデータのサブセットが強調表示されます。 残りのデータは表示されますが、淡色表示になります。 詳細については、この記事で後述する「[アドホック クロスフィルター処理とクロス強調表示](#ad-hoc-cross-filtering-and-cross-highlighting)」を参照してください。

Power BI ではさまざまな方法でレポートをフィルター処理および強調表示できます。 すべての情報をまとめて説明すると混乱するので、以下のセクションに分けて説明します。

* フィルターと強調表示の概要 (この記事)
* Power BI Desktop と Power BI サービスのレポートの[編集ビューでフィルターを作成し、使用する](power-bi-report-add-filter.md)方法。 レポートの編集アクセス許可がある場合、レポートでフィルターを作成、変更、削除できます。
* Power BI サービスのレポートの読み取りビューで、ビジュアルを[共有レポートでフィルターしたり、強調表示したりする](../consumer/end-user-interactions.md)方法。 できることには限りがありますが、それでもさまざまなフィルター処理と強調表示のオプションを使用できます。  
* Power BI Desktop と Power BI サービスの[編集ビューで利用できるフィルターと強調表示のコントロール](power-bi-report-add-filter.md)の詳細なツアー。 この記事では、日付と時刻、数値、テキストなどのフィルターの種類について詳しく説明します。 また、基本オプションと詳細オプションの違いについても説明します。
* フィルターと強調表示の既定の動作を理解した後は、[ページの視覚エフェクトが相互にフィルターおよび強調表示する方法を変更する](service-reports-visual-interactions.md)方法を学習してください

**ご存知でしたか?** Power BI には新しいフィルター エクスペリエンスがあります。 詳細については、[Power BI レポートの新しいフィルター エクスペリエンス](power-bi-report-filter.md)に関する記事をご覧ください。

![新しいフィルター エクスペリエンス](media/power-bi-reports-filters-and-highlighting/power-bi-filter-reading.png)


## <a name="intro-to-the-filters-pane"></a>フィルター ウィンドウの概要

**[フィルター]** ウィンドウで、またはレポート自体で直接 [スライサーを使って選択する](../visuals/power-bi-visualization-slicers.md)ことにより、フィルターを適用することができます。 フィルター ウィンドウには、レポートで使用されているテーブルとフィールド、および適用されているフィルター (ある場合) が表示されます。 

![フィルター ウィンドウ](media/power-bi-reports-filters-and-highlighting/power-bi-add-filter-reading-view.png)

フィルターには次の 4 つの種類があります。

- **ページ フィルター** は、レポート ページ上のすべてのビジュアルに適用されます。     
- **ビジュアル フィルター** は、レポート ページ上の単一のビジュアルに適用されます。 レポート キャンバスでビジュアルを選択した場合は、ビジュアル レベル フィルターのみが表示されます。    
- **レポート フィルター** は、レポート内のすべてのページに適用されます。    
- **ドリルスルー フィルター** は、レポート内の単一のエンティティーに適用されます。    

読み取りビューまたは編集ビューで、ページ フィルター、ビジュアル フィルター、レポート フィルターを使用して検索を行い、目的の値を探して選択できます。 

![フィルターで検索する](media/power-bi-reports-filters-and-highlighting/power-bi-search-filter.png)

フィルターに **すべて** と表示されている場合は、フィールドのすべての値がフィルターに含まれることを意味します。  たとえば、次のスクリーンショットの **[Chain(All)]\(Chain は (すべて) です\)** は、このレポート ページにすべてのストア チェーンに関するデータが含まれることを意味します。  一方、レポート レベル フィルターの **[FiscalYear is 2013 or 2014]\(FiscalYear が 2013 または 2014 である\)** は、レポートに 2013 年および 2014 年の会計年度のデータのみが含まれることを示します。

## <a name="filters-in-reading-or-editing-view"></a>読み取りビューまたは編集ビューでのフィルター
レポートとの対話には、[読み取りビュー](../consumer/end-user-reading-view.md)と編集ビューの 2 つのモードがあります。 使用できるフィルター処理機能は、どのモードを使用しているかによって異なります。

* 編集ビューでは、レポート、ページ、ドリルスルー、ビジュアルの各フィルターを追加できます。 モバイル アプリで開く場合でも、レポートを保存すると、フィルターはレポートと共に保存されます。 読み取りビューでレポートを表示しているユーザーは、追加したフィルターと対話できますが、新しいフィルターを追加することはできません。
* 読み取りビューでは、レポートに既に存在するすべてのフィルターと対話して、行った選択の内容を保存することができます。 新しいフィルターを追加することはできません。

### <a name="filters-in-reading-view"></a>読み取りビューでのフィルター
読み取りビューでしかレポートにアクセスできない場合、フィルター ウィンドウは次のようになります。

![読み取りビューでのフィルター](media/power-bi-reports-filters-and-highlighting/power-bi-filter-reading-view.png)

レポートのこのページには、6 個のページ レベル フィルターと 1 個のレポート レベル フィルターがあります。

各ビジュアルではビジュアル内のすべてのフィールドにフィルターを設定でき、レポート作成者はさらに追加できます。 次の図では、バブル チャートに 6 個のフィルターがあります。

![ビジュアルレベルのフィルター](media/power-bi-reports-filters-and-highlighting/power-bi-filter-visual-level.png)

読み取りビューでは、既存のフィルターを変更することによってデータを調べます。 モバイル アプリでレポートを開く場合でも、加えた変更の内容はレポートと共に保存されます。 方法については、「[レポート フィルター ウィンドウの使用方法](../consumer/end-user-report-filter.md)」をご覧ください

レポートを終了すると、フィルターが保存されます。 フィルター処理を取り消し、レポート作成者が設定したフィルター処理、スライス、ドリル、並べ替えに戻すには、一番上のメニュー バーから **[既定値にリセット]** を選択します。

![[既定値にリセット] アイコン](media/power-bi-reports-filters-and-highlighting/power-bi-reset-to-default.png)

### <a name="filters-in-editing-view"></a>編集ビューでのフィルター
レポートに対する所有者権限を持つユーザーが編集ビューでレポートを開くと、**フィルター** は使用可能な複数の編集ウィンドウの 1 つとして表示されます。

![編集ビューの [フィルター] ウィンドウ](media/power-bi-reports-filters-and-highlighting/power-bi-add-filter-editing-view.png)

読み取りビューと同じように、レポートのこのページには、6 個のページ レベル フィルターと 1 個のレポート レベル フィルターがあります。 また、バブル チャートを選択すると、6 個のビジュアル レベル フィルターが適用されていることがわかります。

編集ビューでは、フィルターと強調表示に関してさらに多くのことができます。 まず第一に、新しいフィルターを追加できます。 その方法と他の機能については、「[レポートにフィルターを追加する](power-bi-report-add-filter.md)」をご覧ください。

## <a name="ad-hoc-cross-filtering-and-cross-highlighting"></a>アドホック クロスフィルター処理とクロス強調表示
1 つのビジュアルで値または軸のラベルを選択し、ページ上の他のビジュアルの関連する値をクロスフィルター処理またはクロス強調表示します。 ほとんどのビジュアルでは、1 つのビジュアルで値を選択しても、他のビジュアルの関連のないデータは削除されません。 代わりに、関連するデータのサブセットが強調表示されます。 関連のないデータは表示されますが、淡色表示になります。 ただし、ビジュアルによっては、1 つのビジュアルで値を選択すると、他のビジュアルでフィルターのように動作することがあります。 たとえば、折れ線グラフおよび散布図では、関連するデータのみが表示されます。 フィルターを使用した場合と同じように、関連のないデータは表示されません。 

強調表示を解除するには、もう一度値を選択するか、同じビジュアル内の空の領域を選択します。 強調表示は、データの変化を簡単に調べられる楽しい方法です。 その他の例については、Power BI レポートでのビジュアル相互間のクロスフィルター処理の「[クロスフィルター処理とクロス強調表示](../consumer/end-user-interactions.md#cross-filtering-and-cross-highlighting)」セクションを参照してください。

![クロスフィルター処理とクロス強調表示を示すアニメーション。](media/power-bi-reports-filters-and-highlighting/power-bi-adhoc-filter.gif)

レポート エディターを使用すると、ビジュアルの相互作用の方法を変更できます。 クロス強調表示の動作を微調整する方法については、[レポート内でのビジュアルの相互作用を変更する](service-reports-visual-interactions.md)方法に関するページを参照してください。

## <a name="next-steps"></a>次のステップ

[Power BI レポートの新しいフィルター エクスペリエンス](power-bi-report-filter.md)

[レポートへのフィルターの追加 (編集ビュー)](power-bi-report-add-filter.md)

[レポート フィルターの使用方法](../consumer/end-user-report-filter.md)

[レポート内でレポートのビジュアルを相互間でクロスフィルター処理とクロス強調表示する方法](../consumer/end-user-interactions.md)

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。
