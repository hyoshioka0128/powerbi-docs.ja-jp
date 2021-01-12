---
title: 埋め込み BI 分析情報を向上させるための Power BI 埋め込み分析の Power BI ビジュアルでのビジュアル対話
description: この記事では、Power BI ビジュアルでビジュアル対話を許可する必要があるかどうかを確認する方法について説明します。 Power BI 埋め込み分析を使用して、より優れた埋め込み BI インサイトを有効にします。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: a5b46e901b5e8cabc00d48e4ef307b2ae98de2b6
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888514"
---
# <a name="visual-interactions-in-power-bi-visuals"></a>Power BI ビジュアルでのビジュアル対話

ビジュアルでは、`allowInteractions` フラグの値のクエリを実行できます。このフラグでは、ビジュアルでビジュアル対話を許可する必要があるかどうかが示されています。 たとえば、ビジュアルはレポートの表示や編集の間は対話形式になりますが、ダッシュボードで表示されるときは対話形式ではありません。 このような操作には、"*クリック*"、"*パン*"、"*ズーム*"、"*選択*" などがあります。 

> [!NOTE]
> どのフラグが指定されているかに関係なく、すべてのシナリオでツールヒントを有効にする必要があります。

`allowInteractions` フラグは、IVisualHost インターフェイスのメンバーとして、ビジュアルの初期化の間に、ブール値として渡されます。

ビジュアルが対話形式ではない必要がある Power BI のすべてのシナリオにおいて (ダッシュボード タイルなど)、`allowInteractions` フラグは `false` に設定されます。 それ以外の場合 (レポートなど)、`allowInteractions` は `true` に設定されます。

詳細については、[SampleBarChart ビジュアル リポジトリ](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/59a47935d8f5272ce145fe804193599ddb7e2001)に関するページを参照してください。

```typescript
   ...
   let allowInteractions = options.host.allowInteractions;
   bars.on('click', function(d) {
       if (allowInteractions) {
           selectionManager.select(d.selectionId);
           ...
       }
   });
```
