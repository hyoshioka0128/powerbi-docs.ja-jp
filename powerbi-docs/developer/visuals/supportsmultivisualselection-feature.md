---
title: supportsMultiVisualSelection 機能
description: この記事では Power BI ビジュアルの supportsMultiVisualSelection 機能の使用方法とその要件について説明します。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 04/30/2020
ms.openlocfilehash: 6ad986308fb82f8191829d29654bb96b55d0fbd0
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2020
ms.locfileid: "83272697"
---
# <a name="use-the-supportsmultivisualselection-feature"></a>supportsMultiVisualSelection 機能を使用する

`supportsMultiVisualSelection` 機能を使用すると、レポート内の複数のビジュアルに選択内容を適用できるようになります。

## <a name="example"></a>例

複数のビジュアルが含まれるレポートで、2 つの値を選択して、その値が他のビジュアルに適用されるようにします。 たとえば、[小売の分析のサンプル](../../create-reports/sample-retail-analysis.md)の 1 つのビジュアルで **[Fashions Direct]** を選択します。 Ctrl キーを押しながら、別のビジュアルで **[Jan]** を選択します。 レポートでは、この選択内容が、この機能の使用をサポートする他のビジュアルに適用されます。 他のビジュアルでも、 **[Fashions Direct]** と **[Jan]** にスコープが適用されます。

## <a name="requirements"></a>要件

この機能には、API v3.2.0 以上が必要です。

画像のビジュアルに、この機能を適用することはできません。 高度なビジュアル (主要なインフルエンサ、分解ツリー、Q&A ビジュアル、テキストボックス、ゲージ グラフなど) には適用できません。

## <a name="usage"></a>使用

`supportsMultiVisualSelection` 機能を使用するには、ビジュアルの `capabilities.json` ファイルに次のコードを追加します。

```json
    {   
            ...
        "supportsMultiVisualSelection": true
            ...
    }
```

## <a name="next-steps"></a>次の手順

Power BI の概念については、「[Power BI のビジュアル](power-bi-visuals-concept.md)」を参照してください。

Power BI の開発を試すには、[Power BI のビジュアル開発](custom-visual-develop-tutorial.md)に関するチュートリアルをご覧ください。
