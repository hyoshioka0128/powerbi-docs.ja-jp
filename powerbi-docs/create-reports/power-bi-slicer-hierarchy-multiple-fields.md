---
title: 階層スライサーに複数のフィールドを追加する
description: 階層内に複数のフィールドを含む階層スライサーを作成する方法について説明します。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 01/19/2021
LocalizationGroup: Create reports
ms.openlocfilehash: abed7e9f6da352d5461868e6371ffefb814eb3ff
ms.sourcegitcommit: 96080432af4c8e3fe46c23274478ccffa0970efb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98597628"
---
# <a name="add-multiple-fields-to-a-hierarchy-slicer"></a>階層スライサーに複数のフィールドを追加する

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

単一のスライサー内の複数の関連フィールドに対してフィルター処理を行う場合は、"*階層*" スライサーと呼ばれるものを作成することで、それを行います。 Power BI Desktop または Power BI サービスでこれらのスライサーを作成できます。

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy.png" alt-text="Power BI の階層スライサーのスクリーンショット。":::

スライサーに複数のフィールドを追加すると、既定では、展開して次のレベルの項目を表示できる項目の横に矢印または "*シェブロン*" が表示されます。

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-arrow.png" alt-text="Power BI の階層スライサーのドロップダウンのスクリーンショット。":::
 
 
項目の 1 つ以上の子を選択すると、最上位レベルの項目に半選択された円が表示されます。
 
:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-semi-selected.png" alt-text="Power BI での単一選択の階層スライサーのスクリーンショット。":::

## <a name="format-the-slicer"></a>スライサーの書式設定

スライサーの動作は変更されていません。 スライサーのスタイルを指定することもできます。 たとえば、単一選択モードに設定できます。 または、リストとドロップダウンを入れ替えることができます。 

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-dropdown.png" alt-text="ドロップダウン スライサーとして書式設定された階層スライサーのスクリーンショット。":::

以下の書式設定を変更することもできます。

### <a name="change-the-title"></a>タイトルを変更する

任意のスライサーのタイトルを編集できますが、階層スライサーでは特に役立ちます。 既定では、階層スライサーの名前は階層内のフィールド名の一覧になります。

この例では、スライサーのタイトルとして階層内の 3 つのフィールドの一覧が表示されています:種類、プラットフォーム、名前です。

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-title.png" alt-text="種類、プラットフォーム、名前のフィールドを含む階層スライサーのスクリーンショット。":::

名前を変更するには、スライサーを選択してから **[書式]** ペインを選択します。 **[スライサー ヘッダー]** の下で、 **[タイトルのテキスト]** ボックスにスライサーの現在の名前が表示されます。

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-edit-title.png" alt-text="現在のタイトルが表示されている [書式] ペインのスクリーンショット。":::

テキストを選択して、新しい名前を追加します。

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-new-title.png" alt-text="階層スライサーの新しいタイトルのスクリーンショット。":::


### <a name="change-the-expandcollapse-icon"></a>展開/折りたたみアイコンを変更する

階層スライサーには、他の書式設定オプションがいくつかあります。 展開/折りたたみアイコンを、既定の矢印からプラス/マイナス記号またはキャレットに変更できます。

1. スライサーを選択してから、 **[書式]** を選択します。
1. **[項目]** を展開し、 **[展開/折りたたみアイコン]** を選択します。
1. **[シェブロン]** 、 **[プラス/マイナス]** 、または **[キャレット]** から選択します。
 
    :::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-caret.png" alt-text="階層スライサー用の展開/折りたたみアイコンを選択するスクリーンショット。":::
 
### <a name="change-the-indentation"></a>インデントを変更する

レポートの領域が狭い場合は、子項目をインデントする量を減らすことができます。 既定では、インデントは 15 ピクセルですが、それを増減できます。 

1. スライサーを選択してから、 **[書式]** を選択します。
1. **[項目]** を展開してから、 **[階段状レイアウトのインデント]** をドラッグして、値を小さくするか大きくします。 ボックスに数値を入力することもできます。

    :::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-indentation.png" alt-text="階層スライサーのインデントを設定するスクリーンショット。":::
    
## <a name="limitations-and-considerations"></a>制限事項と考慮事項

- テーブル モデルの場合、この機能には 2017 以降の SQL Server Analysis Services が必要です。
- マルチディメンション モデルの場合、この機能には SuperDAXMD が有効になっている SQL Server Analysis Services 2019 CU5 以降が必要です。 詳細については、[SuperDAXMD](/analysis-services/multidimensional-models/dax-for-multidimensional-models#superdaxmd) を参照してください。

## <a name="next-steps"></a>次の手順

- [Power BI のスライサー](../visuals/power-bi-visualization-slicers.md)
- 他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
