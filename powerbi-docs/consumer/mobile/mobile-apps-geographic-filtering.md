---
title: Power BI モバイル アプリで地理的な場所によりレポートをフィルターする
description: レポート所有者が場所タグを設定している場合に、Microsoft Power BI モバイル アプリで地理的な場所によりレポートをフィルターする方法について説明します。
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 03/11/2020
ms.openlocfilehash: fe5ab9befcf54a617aefa5ad281872f45a59229c
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96388979"
---
# <a name="filter-a-report-by-geographic-location-in-the-power-bi-mobile-apps"></a>Power BI モバイル アプリで地理的な場所によりレポートをフィルターする
適用対象:

| ![iPhone](./media/mobile-apps-geographic-filtering/iphone-logo-50-px.png) | ![iPad](./media/mobile-apps-geographic-filtering/ipad-logo-50-px.png) | ![Android フォン](./media/mobile-apps-geographic-filtering/android-phone-logo-50-px.png) | ![Android タブレット](./media/mobile-apps-view-dashboard/android-tablet-logo-50-px.png) | ![Windows スマートフォン](./media/mobile-apps-geographic-filtering/win-10-logo-50-px.png) |
|:--- |:--- |:--- |:--- |:--- |
| iPhones |iPad |Android フォン |Android タブレット |Windows 10 スマートフォン |

モバイル デバイスで Power BI レポートを開くと、右上に小さなプッシュピン アイコンが表示されることがあります。 プッシュピンが表示される場合、場所に基づいてそのレポートをフィルターできます。

> [!NOTE]
> 場所でフィルター処理できるのは、レポート内の地名が英語で書かれている場合のみです ("New York City"、"Germany" など)。 Windows 10 タブレットと PC は地理的なフィルタリングをサポートしていませんが、Windows 10 スマートフォンはサポートしています。

>[!NOTE]
>**Windows 10 Mobile を使用するスマートフォン** に対する Power BI モバイル アプリのサポートは、2021 年 3 月 16 日に廃止されます。 [詳細情報](/legal/powerbi/powerbi-mobile/power-bi-mobile-app-end-of-support-for-windows-phones)

## <a name="filter-your-report-by-your-geographic-location"></a>地理的な場所でレポートをフィルターする
1. モバイル デバイスの Power BI モバイル アプリでレポートを開きます。
2. レポートに地理的なデータが含まれている場合、Power BI に位置情報へのアクセスを許可するように求めるメッセージが表示されます。 **[許可]** をクリックし、もう一度 **[許可]** をタップします。
3. 押しピン ![押しピン アイコンをタップします。](./media/mobile-apps-geographic-filtering/power-bi-mobile-geo-icon.png)。 レポート内のデータに応じて、市、都道府県、または国/地域でフィルター処理できます。 フィルターを使用すると、現在地に一致する選択肢のみが一覧表示されます。
   
    ![押しピン フィルター](./media/mobile-apps-geographic-filtering/power-bi-mobile-geo-map-set-filter.png)

## <a name="why-dont-i-see-location-tags-on-a-report"></a>レポートに場所タグが表示されない場合
場所タグを表示するには、下の 3 つの条件をすべて満たす必要があります。 

* Power BI Desktop でレポートを作成したユーザーは、少なくとも 1 つの列に対して[地理データを分類](../../transform-model/desktop-mobile-geofiltering.md)している必要があります (市区町村、都道府県、国/地域など)。
* レポートを表示するユーザーが、列内にデータがある場所のいずれかにいること。
* レポートを表示するユーザーが、次のモバイル デバイスのいずれかを使っていること。
  * iOS (iPad、iPhone、iPod)。
  * Android (スマートフォン、タブレット)。
  * Windows 10 スマートフォン (PC やタブレットなどの他の Windows 10 デバイスは、地理的フィルタリングをサポートしません)。

Power BI Desktop での[地理的なフィルターの設定](../../transform-model/desktop-mobile-geofiltering.md)の詳細を参照してください。

### <a name="next-steps"></a>次のステップ
* [モバイル アプリで現実世界から Power BI データに接続する](mobile-apps-data-in-real-world-context.md)
* [Power BI Desktop でのデータ分類](../../transform-model/desktop-data-categorization.md) 
* ご質問 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。