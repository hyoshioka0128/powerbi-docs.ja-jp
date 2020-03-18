---
title: Power BI ビジュアルにランディング ページを追加する
description: この記事では、Power BI ビジュアルにランディング ページを追加する方法を説明します。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: 6f1590d5635ed6e55833350027c52379e5d7cf51
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79379964"
---
# <a name="add-a-landing-page-to-your-power-bi-visuals"></a>Power BI ビジュアルにランディング ページを追加する

API 2.3.0 では、Power BI のビジュアルにランディング ページを追加できます。 それを行うには、機能に `supportsLandingPage` を追加して、true に設定します。 これにより、データを追加する前にビジュアルが初期化されて更新されます。 ビジュアルにはウォーターマークが表示されなくなるため、ビジュアルにデータがないときにビジュアルに表示される独自のランディング ページをデザインできます。

```typescript
export class BarChart implements IVisual {
    //...
    private element: HTMLElement;
    private isLandingPageOn: boolean;
    private LandingPageRemoved: boolean;
    private LandingPage: d3.Selection<any>;

    constructor(options: VisualConstructorOptions) {
            //...
            this.element = options.element;
            //...
    }

    public update(options: VisualUpdateOptions) {
    //...
        this.HandleLandingPage(options);
    }

    private HandleLandingPage(options: VisualUpdateOptions) {
        if(!options.dataViews || !options.dataViews.length) {
            if(!this.isLandingPageOn) {
                this.isLandingPageOn = true;
                const SampleLandingPage: Element = this.createSampleLandingPage(); //create a landing page
                this.element.appendChild(SampleLandingPage);
                this.LandingPage = d3.select(SampleLandingPage);
            }

        } else {
                if(this.isLandingPageOn && !this.LandingPageRemoved){
                    this.LandingPageRemoved = true;
                    this.LandingPage.remove();
                }
        }
    }
```

次の図に、ランディング ページの例を示します。

![ランディング ページのスクリーンショット](media/landing-page/app-landing-page.png)
