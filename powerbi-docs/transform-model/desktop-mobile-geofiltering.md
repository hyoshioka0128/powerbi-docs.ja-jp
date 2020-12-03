---
title: モバイル アプリ向けの Power BI Desktop で地理的フィルターを設定する
description: Power BI Desktop でモデルに地理的フィルタリングを設定すると、Power BI モバイル アプリでデータを自動的に現在の場所でフィルター処理できます。
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: how-to
ms.date: 01/16/2018
LocalizationGroup: Model your data
ms.openlocfilehash: 2368732d5f0f5fe6b0c32ac535068725e8620215
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96413984"
---
# <a name="set-geographic-filters-in-power-bi-desktop-for-use-in-the-mobile-app"></a>モバイル アプリで使用するために Power BI Desktop で地理的フィルターを設定する
Power BI Desktop で列の[地理的データを分類](desktop-data-categorization.md)し、Power BI Desktop がレポートの表示での値の処理方法を認識できるようにすることができます。 追加された特典として、お客様や仕事仲間が Power BI モバイル アプリでそのレポートを表示すると、Power BI では現在地に一致する地理的フィルターが自動的に適用されます。 

たとえば、顧客を訪問する営業マネージャーが、その顧客の総売上と収益をすばやくフィルター処理し、 県、市、または実際の住所など、現在の場所のデータを抽出したいと考えます。 また、その後で時間があれば、近くの別の顧客も訪問する予定です。 そのような場合は、[場所でレポートをフィルター処理してこれらの顧客を見つける](../consumer/mobile/mobile-apps-geographic-filtering.md)ことができます。

> [!NOTE]
> モバイル アプリを使用して場所でフィルター処理できるのは、レポート内の地名が英語で書かれている場合のみです ("New York City"、"Germany" など)。
> 
> 

## <a name="identify-geographic-data-in-your-report"></a>レポートで地理的データを識別する
1. Power BI Desktop でデータ ビュー ![[データ ビュー] アイコンに切り替えます](media/desktop-mobile-geofiltering/pbi_desktop_data_icon.png)。
2. 地理的データを含む列を選択します ([市区町村] 列など)。
   
    ![[市区町村] 列](media/desktop-mobile-geofiltering/power-bi-desktop-geo-column.png)
3. **[モデリング]** タブで **[データ カテゴリ]** を選択し、適切なカテゴリ (この例では **[市区町村]** ) を選択します。
   
    ![[データ カテゴリ] ボックス](media/desktop-mobile-geofiltering/power-bi-desktop-geo-category.png)
4. モデルの他のフィールドの地理的データ カテゴリの設定の続けます。 
   
   > [!NOTE]
   > モデルの各データ カテゴリに対して複数の列を設定できますが、そうした場合、Power BI モバイル アプリでは地理的にモデルをフィルター処理できません。 モバイル アプリで地理的フィルタリングを使用するには、データ カテゴリごとにただ 1 つの列を設定します (ただ 1 つの **[市区町村]** 列、1 つの **[値道府県]** 列、1 つの **[国]** 列など)。 
   > 
   > 

## <a name="create-visuals-with-your-geographic-data"></a>地理的なデータでビジュアルを作成する
1. レポート ビュー ![レポート ビュー](media/desktop-mobile-geofiltering/power-bi-desktop-report-icon.png)に切り替えて、データ内の地理的フィールドを使用するビジュアルを作成します。 
   
    ![マップを使用したレポート](media/desktop-mobile-geofiltering/power-bi-desktop-geo-report.png)
   
    この例では、モデルには市区町村と都道府県を 1 つの列にする計算列も含まれます。 [Power BI Desktop での計算列の作成](desktop-calculated-columns.md)について参照してください。
   
    ![市区町村と都道府県を 1 つにしたフィールド](media/desktop-mobile-geofiltering/power-bi-desktop-city-state-column.png)
2. Power BI サービスにレポートを発行します。

## <a name="view-the-report-in-power-bi-mobile-app"></a>Power BI モバイル アプリでレポートを表示する
1. 任意の[Power BI モバイル アプリ](../consumer/mobile/mobile-apps-for-mobile-devices.md)でレポートを開きます。
2. レポートにデータがある地理的な場所にいる場合、その場所に自動的にフィルター処理できます。
   
    ![モバイル アプリの地理フィルター](media/desktop-mobile-geofiltering/power-bi-mobile-geo-map-set-filter.png)

「[Power BI モバイル アプリで場所によるレポートをフィルターする](../consumer/mobile/mobile-apps-geographic-filtering.md)」を参照してください。

## <a name="next-steps"></a>次のステップ
* [Power BI Desktop でのデータ分類](desktop-data-categorization.md)  
* ご質問 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
