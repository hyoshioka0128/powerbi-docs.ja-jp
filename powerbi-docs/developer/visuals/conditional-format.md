---
title: Power BI 埋め込み分析の条件付き書式設定
description: Power BI の視覚化プロジェクトに条件付き書式を適用する方法について説明します。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.topic: how-to
ms.subservice: powerbi-custom-visuals
ms.date: 03/15/2021
ms.openlocfilehash: c319df4a3ad20fc417fb6997ffa6ea6c1f4165ff
ms.sourcegitcommit: a0ef8f57ff867b38af20a851ff7c65bbc6164397
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/16/2021
ms.locfileid: "103486785"
---
# <a name="add-conditional-formatting"></a>条件付き書式を追加する

[条件付き書式設定](../../visuals/service-tips-and-tricks-for-color-formatting.md#conditional-formatting-for-visualizations)を使用すると、レポートの作成者は数値に従って、レポート上での色の表示方法を指定できます。

この記事では、Power BI 視覚化に条件付き書式機能を追加する方法について説明します。

条件付き書式は、次のプロパティの型にのみ適用できます。
* Color
* Text
* アイコン
* Web URL

## <a name="add-conditional-formatting-to-your-project"></a>条件付き書式をプロジェクトに追加する

このセクションでは、既存の Power BI 視覚化に条件付き書式を追加する方法について説明します。 この記事のサンプル コードは、[SampleBarChart](https://github.com/microsoft/PowerBI-visuals-sampleBarChart) 視覚エフェクトに基づいています。 [barChart.ts](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/master/src/barChart.ts) のソース コードを調べることができます。

### <a name="add-a-conditional-color-formatting-entry-in-the-format-pane"></a>[書式] ウィンドウに条件付きの色の書式設定エントリを追加する

このセクションでは、[書式] ウィンドウのデータ ポイントに、条件付きの色の書式設定エントリを追加する方法について説明します。

1. `VisualObjectInstance` 内の `propertyInstanceKind` 配列を使用します。これは `powerbi-visuals-api` によって公開されています。 最初の手順として、ファイルに次のインポートが含まれていることを確認します。

    ```typescript
    import powerbiVisualsApi from "powerbi-visuals-api";
    ```

2. 適切な種類の書式 (*Constant*、*ConstantOrRule*、または *Rule*) を指定するには、`VisualEnumerationInstanceKinds` 列挙型を使用します。 次のインポートをファイルに追加します。

    ```typescript
    import VisualEnumerationInstanceKinds = powerbiVisualsApi.VisualEnumerationInstanceKinds;
    ```

3. `propertyInstanceKind` 配列に、条件付き書式をサポートするすべてのプロパティを一覧表示します。 `enumerateObjectInstances` メソッドにこれらのプロパティを定義します。

    ```typescript
    public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration {
            …
            case 'colorSelector':
                …
                    objectEnumeration.push({
                        objectName: objectName,
                        displayName: barDataPoint.category,
                        properties: {
                            fill: {
                                solid: {
                                    color: barDataPoint.color
                                }
                            }
                        },
                        selector: dataViewWildcard.createDataViewWildcardSelector(dataViewWildcard.DataViewWildcardMatchingOption.InstancesAndTotals),
                        altConstantValueSelector: barDataPoint.selectionId.getSelector(),

                        // List your conditional formatting properties
                        propertyInstanceKind: {
                            fill: VisualEnumerationInstanceKinds.ConstantOrRule
                        }
                    });
                }
            …
    }

    ```

    `VisualEnumerationInstanceKinds.ConstantOrRule` によって、定数の書式設定 UI 要素と共に、条件付き書式設定 UI のエントリが作成されます。

    >[!div class="mx-imgBorder"]
    >![Power BI で標準色のボタンの横に表示される [条件付き書式] ボタンのスクリーンショット。](media/conditional-formatting/conditional-formatting-ui.png)

### <a name="define-how-conditional-formatting-behaves"></a>条件付き書式の動作方法を定義する

書式がデータ ポイントに適用される方法を定義します。

`powerbi-visuals-utils-dataviewutils` 下に宣言された `createDataViewWildcardSelector` を使用して、条件付き書式をインスタンス、合計、またはその両方に適用するかどうかを指定します。 詳細については、「[DataViewWildcard](utils-dataview.md#)」を参照してください。

`enumerateObjectInstances` で、条件付き書式を適用するオブジェクトに対して、次の変更を行います。

 * `selector` 値を `dataViewWildcard.createDataViewWildcardSelector(dataViewWildcardMatchingOption)` 呼び出しに置き換えます。 `DataViewWildcardMatchingOption` によって、条件付き書式をインスタンス、合計、またはその両方に適用するかどうかを定義します。

* `selector` プロパティ用に以前に定義した値を使用して、`altConstantValueSelector` プロパティを追加します。

```typescript
case 'colorSelector':
         …
            objectEnumeration.push({
                objectName: objectName,
                displayName: barDataPoint.category,
                properties: {
                    fill: {
                        solid: {
                            color: barDataPoint.color
                        }
                    }
                },

                // Define whether the conditional formatting will apply to instances, totals, or both
                selector: dataViewWildcard.createDataViewWildcardSelector(dataViewWildcard.DataViewWildcardMatchingOption.InstancesAndTotals),

                // Add this property with the value previously defined for the selector property
                altConstantValueSelector: barDataPoint.selectionId.getSelector(),

                propertyInstanceKind: { 
                    fill: VisualEnumerationInstanceKinds.ConstantOrRule
                }
            });
        }

```

## <a name="limitations-and-considerations"></a>制限事項と考慮事項

条件付き書式は、次のビジュアルではサポートされていません。

* テーブル ベースのビジュアル

* マトリックス ベースのビジュアル

系列では条件付き書式を使用しないことをお勧めします。 代わりに、顧客が各系列を個別に書式設定できるようにする必要があります。これにより、系列を視覚的に区別しやすくなります。 系列を使用した大多数のすぐに使用できるビジュアルで、この方法を共有しています。

## <a name="next-steps"></a>次の手順

>[!div class="nextstepaction"]
>[DataViewUtils](utils-dataview.md)
