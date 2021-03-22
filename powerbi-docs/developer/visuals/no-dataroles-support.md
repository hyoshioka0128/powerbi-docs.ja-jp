---
title: データをバインドせずにビジュアルをレンダリングする
description: データをバインドせずにビジュアルをレンダリングする方法について説明します。
author: Demonkratiy
ms.author: v-asemenov
ms.reviewer: kesharab
manager: mgolan
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 02/18/2021
ms.openlocfilehash: 8fcd7c13e7ac654ff3413869ac9cbe2bd3ea9dfc
ms.sourcegitcommit: 89c349500dd0737d80a753403714bceb3fd0a3ef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2021
ms.locfileid: "102639219"
---
# <a name="render-a-visual-without-the-need-to-bind-any-data"></a>データをバインドせずに視覚エフェクトをレンダリングする

`powerbi-visuals-api` バージョン 3.6.0 から、`dataRoles` 機能モデルはサポートされません。 この機能により、データをバインドせずに、Power BI から更新プログラムを受け取ることができます。 つまり、データバケットが空の場合でも、ビジュアルでデータロールがまったく使用されない場合でも、ビジュアルをレンダリングしたり、更新メソッドを利用してビジュアルの書式設定を変更したりできます。

この機能を有効にするには、`capabilities.json` ファイルの 2 つのパラメーターを *true* に設定する必要があります。 

```json
    {
        "supportsLandingPage": true,
        "supportsEmptyDataView": true,
    }
```

次のタブには、Power BI ビジュアルの例が 2 つあります。その 1 つでは、データをバインドする必要があります。もう 1 つでは、新しい機能を使用し、データをバインドする必要がありません。

## <a name="binding-data-required"></a>[データのバインドが必要](#tab/NoDataroles)
   

>[!div class="mx-imgBorder"]
>![API-2.6.0 前の no-dataroles-support のスクリーンショット](media/no-dataroles-support/no-dataroles-1.png)


## <a name="binding-data-not-required"></a>[データのバインドは不要](#tab/NoDatarolesSupport) 

>[!div class="mx-imgBorder"]
>![API-2.6.0 後の no-dataroles-support のスクリーンショット](media/no-dataroles-support/no-dataroles-2.png)

---

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
> [機能を使用する](capabilities.md)
