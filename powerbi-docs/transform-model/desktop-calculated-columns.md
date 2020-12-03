---
title: Power BI Desktop で計算列を使用する
description: Power BI Desktop の計算列
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: how-to
ms.date: 05/07/2019
LocalizationGroup: Model your data
ms.openlocfilehash: 9c7285f90b963166c643c2bb20f9323eddb7ce85
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415935"
---
# <a name="create-calculated-columns-in-power-bi-desktop"></a>Power BI Desktop での計算列の作成
計算列を使うと、既にモデル内に存在するテーブルに新しいデータを追加できます。 しかし、値のクエリを実行してデータ ソースから新しい列に読み込む代わりに、列の値を定義する Data Analysis Expressions (DAX) 数式を作成します。 Power BI Desktop では、 **[レポート]** ビューの新しい列機能を使用して、計算列が作成されます。

クエリ エディターの **[カスタム列の追加]** を使用してクエリの一部として作成されるカスタム列とは異なり、 **[レポート]** ビューまたは **[データ]** ビューで作成される計算列は、モデルに既に読み込まれているデータに基づいています。 たとえば、2 つの異なる (しかし、関連する) テーブルの 2 つの異なる列の値を連結して、加算したり、サブ文字列を抽出したりすることができます。

作成する計算列は、他のフィールドと同じように **[フィールド]** 一覧に表示されますが、その値が数式の結果であることを示す特別なアイコンが表示されます。 列に好きな名前を付けたり、列を他のフィールドと同じようにレポートのビジュアルに追加したりできます。

![[フィールド] ビューの計算列を示す、Power BI Desktop のスクリーンショット。](media/desktop-calculated-columns/calccolinpbid_fields.png)
 
計算列では、DAX を使用して結果を計算します。これは、Power BI Desktop の場合のようなリレーショナル データを操作することを意図した数式言語です。 DAX には 200 を超える関数、演算子、およびコンストラクトから成るライブラリが含まれています。 数式を作成する際の柔軟性が非常に高く、データ分析に必要なほとんどすべての計算結果を得ることができます。 DAX の詳細については、「[Power BI Desktop での DAX の基本事項](desktop-quickstart-learn-dax-basics.md)」をご覧ください。

DAX の数式は Excel の数式と似ています。 実際には、DAX は Excel と同じ機能が多数あります。 ただし、DAX の関数は、Power BI Desktop などのレポートで、データを対話式にスライスしたりフィルターを掛けたりする操作を意図して設計されています。 Excel では、テーブルの行ごとに異なる数式を使用できます。 Power BI では、新しい列に対して DAX 式を作成すると、テーブル内のすべての行に対して結果が計算されます。 列の値は必要に応じて再計算されます。たとえば、基になるデータが更新され、値が変更されたときなどです。

## <a name="lets-look-at-an-example"></a>例を見てみましょう
Jeff は Contoso の配送マネージャーであり、さまざまな市区町村への配送の数を表示するレポートを作成したいと考えています。 Jeff は、市区町村と都道府県ごとに異なるフィールドがある **Geography** テーブルを持っています。 しかし、Jeff はレポートで同じ行の単一の値として、市区町村と都道府県の値を表示したいと考えています。 現時点では、Jeff の **Geography** テーブルには必要なフィールドがありません。

![[フィールド] ビューの Geography フィルターを示す Power BI Desktop のスクリーンショット。](media/desktop-calculated-columns/calccolinpbid_cityandstatefields.png)

しかし、計算列を使用することで、Jeff は **City** 列の市区町村と、**State** 列の都道府県をまとめることができます。

Jeff は、**Geography** テーブルを右クリックしてから、 **[新しい列]** を選択します。 その後、Jeff は次の DAX 式を数式バーに入力します。

![DAX の数式入力を示す Power BI Desktop のスクリーンショット。](media/desktop-calculated-columns/calccolinpbid_formula.png)

この数式では、単に **CityState** という名前の新しい列が作成されます。 **Geography** テーブルの各行については、**City** 列の値を取り、コンマとスペースを追加して、**State** 列の値を連結します。

これで、Jeff は必要なフィールドを取得しました。

![[フィールド] ビューの Geography フィルターで CityState がオンになっていることを示す、Power BI Desktop のスクリーンショット。](media/desktop-calculated-columns/calccolinpbid_citystatefield.png)

Jeff はここで、配送数と共にレポート キャンバスにそれを追加することができます。 これで Jeff は、最小限の労力で、ほぼすべての種類の視覚化に追加できる **CityState** フィールドを取得しました。 Jeff が新しいマップを作成するときに、Power BI Desktop では、新しい列の市区町村と都道府県の値を読み取る方法が既に把握されています。

![マップのビジュアルに表示されているデータを示す Power BI Desktop のスクリーンショット。](media/desktop-calculated-columns/calccolinpbid_citystatemap.png)

## <a name="next-steps"></a>次の手順
ここでは、計算列に関する概要のみを示しました。 詳細については、次のリソースをご覧ください。

* サンプル ファイルをダウンロードし、さらに列を作成する方法についてステップ バイ ステップで学ぶ場合は、「[チュートリアル: Power BI Desktop での計算列の作成](desktop-tutorial-create-calculated-columns.md)」を参照してください

* DAX の詳細については、「[Power BI Desktop での DAX の基本事項](desktop-quickstart-learn-dax-basics.md)」をご覧ください。

* クエリの一部として作成する列の詳細については、[Power BI Desktop での一般的なクエリ タスク](desktop-common-query-tasks.md)に関するページの「**カスタム列の作成**」セクションを参照してください。  

