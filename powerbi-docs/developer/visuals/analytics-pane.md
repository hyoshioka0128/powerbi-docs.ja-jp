---
title: Power BI ビジュアルの分析ウィンドウ
description: この記事では、Power BI ビジュアルで動的な参照行を作成する方法について説明します。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 06/18/2019
ms.openlocfilehash: 43fcc0873006cfd42c97a287c7bff66f5995bfef
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "79380953"
---
# <a name="the-analytics-pane-in-power-bi-visuals"></a>Power BI ビジュアルの分析ウィンドウ

2018 年 11 月に、**分析**ウィンドウが[ネイティブ ビジュアル](https://docs.microsoft.com/power-bi/desktop-analytics-pane)に導入されました。
この記事では、API v2.5.0 を使用する Power BI ビジュアルで**分析**ウィンドウにそれらのプロパティを表示して管理する方法について検討します。

![分析ウィンドウ](media/analytics-pane/visualization-pane-analytics-tab.png)

## <a name="manage-the-analytics-pane"></a>分析ウィンドウを管理する

[**書式**ウィンドウ](https://docs.microsoft.com/power-bi/developer/visuals/custom-visual-develop-tutorial-format-options)でプロパティを管理するように、ビジュアルの **capabilities.json** ファイルでオブジェクトを定義することで、*分析*ウィンドウを管理します。

**分析**ウィンドウでは、次のような違いがあります。

* オブジェクトの定義で、値が 2 の **objectCategory** フィールドを追加します。

    > [!NOTE]
    > 省略可能な `objectCategory` フィールドは、API 2.5.0 で導入されました。 オブジェクトによって制御されるビジュアルの側面が定義されます (1 = 書式設定、2 = 分析)。 `Formatting` は、外観、色、軸、ラベルなどの要素に使用されます。 `Analytics` は、予測、近似曲線、参照行、図形などの要素に使用されます。
    >
    > 値が指定されていない場合、`objectCategory` は既定で "書式設定" になります。

* オブジェクトには、次の 2 つのプロパティが必要です。
    * `show` 型の `bool`。既定値は `false` です。
    * `displayName` 型の `text`。 選択する既定値が、インスタンスの最初の表示名になります。

```json
{
  "objects": {
    "YourAnalyticsPropertiesCard": {
      "displayName": "Your analytics properties card's name",
      "objectCategory": 2,
      "properties": {
        "show": {
          "type": {
            "bool": true
          }
        },
        "displayName": {
          "type": {
            "text": true
          }
        },
      ... //any other properties for your Analytics card
      }
    }
  ...
  }
}
```

他のプロパティは、**書式**オブジェクトの場合と同じ方法で定義できます。 また、**書式**ウィンドウの場合と同様に、オブジェクトを列挙することもできます。

## <a name="known-limitations-and-issues-of-the-analytics-pane"></a>分析ウィンドウの既知の制限事項と問題

* **分析**ウィンドウでは、まだマルチインスタンスはサポートされていません。 オブジェクトに静的以外の[セレクター](https://microsoft.github.io/PowerBI-visuals/docs/concepts/objects-and-properties/#selector)を含めることはできません (つまり、"selector": null)。また、Power BI ビジュアルでは、ユーザー定義の複数のカード インスタンスを含めることはできません。
* `integer` 型のプロパティが正しく表示されません。 回避策として、代わりに `numeric` 型を使用します。

> [!NOTE]
> * **分析**ウィンドウは、新しい情報を追加するか、表示された情報に新たな光を当てるオブジェクトに対してのみ使用します (たとえば、重要な傾向を示す動的な参照行)。
> * ビジュアルの外観 (つまり、書式設定) を制御するオプションはすべて、**書式設定**ウィンドウに限定する必要があります。
