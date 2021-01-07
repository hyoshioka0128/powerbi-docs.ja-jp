---
title: Power BI ビジュアルの作成に使用されたデータを表示する
description: このドキュメントでは、Power BI でビジュアルを作成するために使用されたデータを表示する方法、およびそのデータを .csv ファイルにエクスポートする方法について説明します。
author: mihart
ms.author: mihart
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: how-to
ms.date: 12/4/2019
LocalizationGroup: Visualizations
ms.openlocfilehash: 7aa15bae7ab94619a9f652aa20da9222e3d4af41
ms.sourcegitcommit: 0711972326521944fdd8572403c0b15f31b916da
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2020
ms.locfileid: "97721641"
---
# <a name="display-a-visualizations-underlying-data"></a>視覚エフェクトの基になるデータを表示する

[!INCLUDE[consumer-appliesto-yyyn](../includes/consumer-appliesto-nyyn.md)]    

## <a name="show-data"></a>データの表示
Power BI のビジュアルは、データセットからのデータを使用して作成されます。 目に見えない部分を確認する場合は、ビジュアルの作成に使用されているデータを Power BI によって *表示* することができます。 **[データの表示]** を選択すると、ビジュアルの下 (または横に) データが表示されます。

また、ビジュアルの作成に使用されているデータを .xlsx ファイルまたは .csv ファイルとしてエクスポートして Excel で表示することもできます。 詳細については、「[Power BI ビジュアルからデータをエクスポートする](power-bi-visualization-export-data.md)」を参照してください。

> [!NOTE]
> [*データの表示*] と [*データのエクスポート*] は両方とも、Power BI サービスと Power BI Desktop で使用できます。 ただし、Power BI Desktop では、詳細を示すレイヤーが 1 つ追加されています。[[*レコードの表示*] にはデータセットからの実際の行が表示されます](../create-reports/desktop-see-data-see-records.md)。
> 
> 

## <a name="using-show-data"></a>"*データの表示*" の使用 
1. Power BI Desktop でビジュアルを選択してアクティブにします。

2. **[その他の操作]** (...) を選択し、 **[データの表示]** を選択します。 
    ![[データの表示] の表示オプション](media/service-reports-show-data/power-bi-more-action.png)


3. 既定では、データはビジュアルの下に表示されます。
   
   ![ビジュアルとデータの縦表示](media/service-reports-show-data/power-bi-show-data-below.png)

4. 方向を変更するには、ビジュアルの右上隅にある縦方向のレイアウト ![縦方向のレイアウトに変更するために使用されるアイコンの小さいスクリーンショット](media/service-reports-show-data/power-bi-vertical-icon-new.png) を選択します。
   
   ![ビジュアルとデータの横表示](media/service-reports-show-data/power-bi-show-data-side.png)
5. データを .csv ファイルにエクスポートするには、省略記号を選択し、 **[データのエクスポート]** を選択します。
   
    ![[データのエクスポート] の選択](media/service-reports-show-data/power-bi-export-data-new.png)
   
    Excel へのデータのエクスポートの詳細については、「[Power BI ビジュアルからデータをエクスポートする](power-bi-visualization-export-data.md)」を参照してください。
6. データを非表示にするには、 **[探索]**  >  **[データの表示]** の選択を解除します。

## <a name="using-show-records"></a>レコードの確認の使用
視覚エフェクト内の 1 つのデータ レコードに注目して、その背後にある詳細にドリルダウンできます。 

1. **[レコードの確認]** を使用するには、アクティブにするビジュアルを選択します。 

2. [デスクトップ] リボンで、 **[ビジュアル ツール]** のタブ >  **[データ/ドリル]**  >  **[レコードの確認]** の順に選択します。 

    ![[レコードの確認] が選択されているスクリーンショット。](media/service-reports-show-data/power-bi-see-record.png)

3. ビジュアルのデータ ポイントまたは行を選択します。 この例では、左から 4 つ目の列を選択しています。 Power BI によって、このデータ ポイントのデータセット レコードが表示されます。

    ![データセットの単一レコードのスクリーンショット。](media/service-reports-show-data/power-bi-row.png)

4. **[レポートに戻る]** を選択して、Desktop のレポート キャンバスに戻ります。 

## <a name="considerations-and-troubleshooting"></a>考慮事項とトラブルシューティング

- リボンで **[レコードの確認]** ボタンが無効になって淡色表示されている場合は、選択したビジュアルで [レコードの確認] がサポートされていないことを意味します。
- [レコードの確認] ビューでデータを変更してレポートに保存することはできません。
- 視覚化で多次元モデルの計算メジャーが使用されている場合、[レコードの確認] を使用することはできません。
- ライブ多次元 (MD) モデルに接続されている場合は、[レコードの確認] を使用できません。  

## <a name="next-steps"></a>次の手順
[Power BI ビジュアルからデータをエクスポートする](power-bi-visualization-export-data.md)    

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。


