---
title: Power BI Desktop での列による並べ替え
description: Power BI では、さまざまなデータ フィールドを並べ替えることで視覚効果を変更できます。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 01/30/2020
LocalizationGroup: Create reports
ms.openlocfilehash: 06cd73aa86fdef58ea77b54305af300b1adb62d7
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96412761"
---
# <a name="sort-by-column-in-power-bi-desktop"></a>Power BI Desktop での列による並べ替え
Power BI Desktop と Power BI サービスでは、さまざまなデータ フィールドを並べ替えることで視覚効果を変更できます。 並べ替えで視覚化を変更することで、伝えたい情報を強調でき、その傾向 (あるいは強調したい点) を視覚化に反映させることができます。

数値データ (売り上げ高など) を使用している場合でも、テキスト データ (州名など) を使用している場合でも、ご利用の視覚エフェクトを並べ替え、目的に応じたスタイルで表示できます。 Power BI では非常に柔軟に並べ替えを行うことができ、クイック メニューが用意されています。 ビジュアルを並べ替えるには、その **[その他のオプション]** (...) メニューを選択し、 **[並べ替え]** を選択してから、並べ替えの基準にするフィールドを選択します。

![[その他のオプション] メニュー](media/desktop-sort-by-column/sortbycolumn_2.png)

## <a name="sorting-example"></a>並べ替えの例
もっと詳しい例を使用して、Power BI Desktop のしくみを確認しましょう。

次の視覚エフェクトでは、製造元の名前別に費用、数量、金額が示されています。 並べ替えを行う前は、ここに表示されているとおりの視覚エフェクトです。

![最初の視覚エフェクト](media/desktop-sort-by-column/sortbycolumn_1.png)

現在、ビジュアルは **SalesQuantity** 列で並べ替えられています。 昇順のバーの色を凡例に一致させることで並べ替え列を決定できますが、より便利な方法として **[その他のオプション]** メニューがあります。これにアクセスするには、省略記号 (...) を選択します。

![[その他のオプション] メニュー](media/desktop-sort-by-column/sortbycolumn_2.png)

並べ替えの選択項目は次のとおりです。

* 現在の並べ替えフィールドは **SalesQuantity** です ( **[SalesQuantity]** が太字で示され、黄色の棒が前に付いています)。 

* 現在の並べ替え方向は昇順です ( **[昇順で並べ替え]** が太字で示され、黄色の棒が前に付いています)。

並べ替えフィールドと並べ替え方向については、次の 2 つのセクションで確認します。

## <a name="select-which-column-to-use-for-sorting"></a>並べ替えに使用する列を選択
**[その他のオプション]** メニューの **[SalesQuantity]** の前に黄色の棒がありました。これは、ビジュアルが **SalesQuantity** 列を基準に並べ替えられていることを示します。 別の列によって並べ替えを行うのは簡単です。省略記号 (...) を選択して **[その他のオプション]** メニューを表示し、 **[並べ替え]** を選択して、別の列を選択します。

次の図では、並べ替えの基準にする列として **[DiscountAmount]** を選択しました。 その列は、ビジュアル上では棒の 1 つとしてではなく、線の 1 つとして表示されます。 

![DiscountAmount で並べ替える](media/desktop-sort-by-column/sortbycolumn_3.png)

図がどのように変更されたかに注目してください。 この値は今、最高の **DiscountAmount** 値を示す Fabrikam Inc. から最低の Northwind Traders まで降順で並べられています。 

降順ではなく、昇順に並べ替える必要がある場合は、どうしたらよいでしょうか。 次のセクションでは、それがいかに簡単かを示します。

## <a name="select-the-sort-order"></a>並べ替え順序を選択
前の図の **[その他のオプション]** メニューを詳しく見てみると、 **[降順で並べ替え]** が太字で表示され、前に棒が付いているのがわかります。

![大きい順に並べ替え](media/desktop-sort-by-column/sortbycolumn_4.png)

**[降順で並べ替え]** が選択されている場合、ビジュアルが選択された列によって最大値から最小値へと降順で並べ替えられていることを意味します。 変更する必要がありますか。 ご心配なく。 **[昇順で並べ替え]** を選択するだけで、選択した列の並べ替え順序が最も小さい値から最も大きい値への昇順に変更されます。

同じビジュアルにおいて、**DiscountAmount** の順序付けを変更すると、次のようになります。 今度は製造元として Northwind Traders が最初に、Fabrikam Inc. が最後に表示されてます。前とは逆の順序になっています。

![小さい順に並べ替え](media/desktop-sort-by-column/sortbycolumn_5.png)

ビジュアルに含まれる任意の列を基準にして並べ替えることができます。並べ替えの基準列として **SalesQuantity** を選択すると、それだけで、売り上げが最も大きい製造元が最初に表示されるようになり、ビジュアル内のその他の列はそのまま保持され、それらはその製造元に適用されます。 それらの設定で表示されたビジュアルは次のとおりです。

![SalesQuantity で並べ替え](media/desktop-sort-by-column/sortbycolumn_6.png)

## <a name="sort-using-the-sort-by-column-button"></a>[列で並べ替え] ボタンを使用して並び替える
ご利用のデータの並べ替えには別の方法があります。 **[モデリング]** リボンの **[列で並べ替え]** ボタンを使用するというものです。

![[列で並べ替え] ボタン](media/desktop-sort-by-column/sortbycolumn_8.png)

この並べ替えのアプローチでは、 **[フィールド]** ペインから、並べ替える列 (フィールド) をまず選択し、次に **[モデリング]**  >  **[列で並べ替え]** の順に選択することで、ご利用のビジュアルを並べ替える必要があります。 列を選択しない場合、 **[列で並べ替え]** ボタンは非アクティブになります。

一般的な例を見てみましょう。 年の各月のデータがあり、このデータを時系列に基づいて並べ替えるとします。 次の手順は、その方法を示しています。

1. ビジュアルは選択されているが、 **[フィールド]** ペインで列が選択されていない場合、 **[列で並べ替え]** ボタンが非アクティブ (灰色表示) になっていることに注目してください。
   
   ![[列で並べ替え] ボタンが無効](media/desktop-sort-by-column/sortbycolumn_9.png)

2. **[フィールド]** ウィンドウで、並べ替える列を選択すると、 **[列で並べ替え]** ボタンがアクティブになります。
   
   ![[列で並べ替え] ボタンが有効](media/desktop-sort-by-column/sortbycolumn_10.png)
3. 次に、ビジュアルが選択された状態で、既定値の **[MonthName]** ではなく、 **[MonthOfYear]** を選択します。これにより、ビジュアルは目的の順序 (年の月順) に並べ替えられます。
   
   ![[列で並べ替え] メニュー](media/desktop-sort-by-column/sortbycolumn_11.png)


<!---
This functionality is no longer active. Jan 2020

## Getting back to default column for sorting
You can sort by any column you'd like, but there may be times when you want the visual to return to its default sorting column. No problem. For a visual that has a sort column selected, open the **More options** menu and select that column again, and the visualization returns to its default sort column.

For example, here's our previous chart:

![Initial visualization](media/desktop-sort-by-column/sortbycolumn_6.png)

When we go back to the menu and select **SalesQuantity** again, the visual defaults to being ordered alphabetically by **Manufacturer**, as shown in the following image.

![Default sort order](media/desktop-sort-by-column/sortbycolumn_7.png)

With so many options for sorting your visuals, creating just the chart or image you want is easy.
--->

## <a name="next-steps"></a>次のステップ

次の記事にも興味をもたれるかもしれません。

* [Power BI Desktop でレポート間のドリルスルーを使用する](desktop-cross-report-drill-through.md)
* [Power BI のスライサー](../visuals/power-bi-visualization-slicers.md)
