---
title: Power BI Desktop でのデータ分類
description: Power BI Desktop でのデータ分類
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: how-to
ms.date: 01/15/2020
LocalizationGroup: Model your data
ms.openlocfilehash: d99eb0355d414a9e1627da0b5629eaf45cbaf18d
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415797"
---
# <a name="specify-data-categories-in-power-bi-desktop"></a>Power BI Desktop でデータ分類を指定する
Power BI Desktop では、ユーザーが列に対して "*データ カテゴリ*" を指定すれば、Power BI Desktop が視覚化するときにその列の値をどのように扱うべきかを自動的に見極めます。

Power BI Desktop を使ってデータをインポートすると、テーブル名、列名、データが主キーかどうかなど、データそのものではない情報が取得されます。 Power BI Desktop はその情報を利用して推測し、視覚化を作成するときの既定のユーザー エクスペリエンスの質を高めます。
たとえば、列に数値がある場合、ユーザーはおそらく何らかの方法で集計することになるため、Power BI Desktop によって **[視覚化]** ペインの **[値]** 領域に配置されます。 または、折れ線グラフに日時の値が含まれている列の場合、Power BI Desktop によって、ユーザーがそれを時間階層軸として使用するだろうと推測されます。

しかし、地理的な場所など、判断がもう少し難しい場合があります。 Excel ワークシートにある次の表について考えてみましょう。

![Power BI Desktop にインポートされる表形式データを示す Excel のスクリーンショット。](media/desktop-data-categorization/datacategorizationtable.png)

Power BI Desktop は **GeoCode** 列に含まれるコードを、国の省略形として扱うべきでしょうか? それとも米国の州の省略形でしょうか?  このようなコードはどちらの意味も持つので、明確にはわかりません。 たとえば、AL はアラバマ州とアルバニア、AR はアーカンソー州とアルゼンチン、CA はカリフォルニア州とカナダの意味になり得ます。 これは、地図上に GeoCode フィールドを表示しようとするときに違いが出ます。 

Power BI Desktop で、国が強調表示された世界の画像を表示する必要はありますか? それとも、州が強調表示された米国の画像を表示する必要がありますか?  このような場合は、データにデータ カテゴリを指定することができます。 データ分類を指定して、Power BI Desktop が使用できる情報をさらに細分化すれば、最適なビジュアルを得ることができます。  

**データ カテゴリを指定するには**

1. **レポート** ビューまたは **データ** ビューの **[フィールド]** 一覧で、異なる分類で並べ替えるフィールドを選択します。
2. リボンの **[モデリング]** タブの **[プロパティ]** 領域で、 **[データ カテゴリ]** の横にあるドロップダウン矢印を選択します。  この一覧には、列に選択できるデータ カテゴリが表示されます。 列の現在のデータ型には使えない項目は選べなくなっています。  たとえば、列が date または time データ型である場合、Power BI Desktop で地理的なデータ カテゴリを選べなくなります。 
3. 目的のカテゴリを選択します。

   ![データ カテゴリ フィルターを示す Power BI Desktop のスクリーンショット。](media/desktop-data-categorization/desktop-data-categorization.png)

関心がある場合は、[Power BI モバイル アプリの地理的フィルタリング](desktop-mobile-geofiltering.md)についても参照してください。