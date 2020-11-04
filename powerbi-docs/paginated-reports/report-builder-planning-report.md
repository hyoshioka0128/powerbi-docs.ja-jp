---
title: Power BI レポート ビルダーでのレポートの計画
description: Power BI Report Builder では、さまざまな種類のページ分割されたレポートを作成できます。 便利でわかりやすいレポートを作成するには、まず計画を立てると役立ちます。
ms.date: 07/25/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 79113505-1ce8-4f8c-9260-d861838f7813
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3f075372436723cd8952decd68ecc764bd6e92a0
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2020
ms.locfileid: "93297744"
---
# <a name="planning-a-report-in-power-bi-report-builder"></a>Power BI レポート ビルダーでのレポートの計画

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

Power BI Report Builder では、さまざまな種類のページ分割されたレポートを作成できます。 たとえば、売上データの概要または詳細、マーケティングと売上の傾向、経営報告、またはダッシュボードを示すレポートを作成できます。 また、販売注文、製品カタログ、定型書簡などの高度な書式付きテキストを利用したレポートも作成できます。 これらのレポートはすべて、レポート ビルダーの同じ基本的な構成要素をさまざまに組み合わせて作成されます。 便利でわかりやすいレポートを作成するには、まず計画を立てることが役立ちます。 開始する前に検討すると役立ついくつかの事項を次に示します。  
  
## <a name="in-what-format-do-you-want-the-report-to-appear"></a>レポートをどのような形式で表示するか
  
レポートは、Power BI ポータルなどのブラウザーにオンラインでレンダリングしたり、Excel、Word、PDF などの他の形式にエクスポートしたりできます。 エクスポート形式によっては一部の機能を使用できないので、レポートの最終的な形式を検討することは重要です。 
  
## <a name="in-what-structure-do-you-want-to-present-the-data"></a>データをどのような構造で表示するか
  
テーブル、マトリックス (クロス集計レポートや PivotTable レポートに似ています)、グラフ、自由形式の構造を選択するか、これらの構造を組み合わせてデータを表します。 詳細については、[Power BI レポート ビルダーでのテーブル、マトリックス、およびリスト](report-builder-tables-matrices-lists.md)に関する記事を参照してください。  
  
## <a name="how-do-you-want-your-report-to-look"></a>どのような外観のレポートにするか
  
レポート ビルダーには、レポートを読みやすくしたり、重要な情報を強調したり、対象ユーザーがレポート内を移動しやすくしたりするためにレポートに追加できる多数のレポート アイテムが用意されています。 レポートの希望の表示方法がわかっていれば、テキスト ボックス、四角形、画像、線などのレポート アイテムが必要かどうかを判断できます。 また、アイテムの表示と非表示を切り替えたり、ドキュメント マップを追加したり、詳細レポートまたはサブレポートを含めたり、他のレポートにリンクしたりすることもできます。   
  
## <a name="should-the-data-be-filtered"></a>データのフィルター処理が必要か
  
レポートの範囲を特定のユーザーまたは場所、あるいは特定の期間などに絞り込むことができます。 レポート データをフィルター処理するには、パラメーターを使用して、必要なデータのみを取得して表示します。 詳細については、[Power BI レポート ビルダーでのレポート パラメーター](paginated-reports-parameters.md)に関する記事を参照してください。  
  
## <a name="do-you-need-to-create-calculations"></a>計算を作成する必要があるか 
  
レポートに必要な特定のフィールドがデータ ソースやデータセットに含まれていない場合があります。 そのような状況では、独自の計算フィールドの作成が必要になることがあります。 たとえば、行アイテムの販売額を取得するために数量と単価を乗算するような場合があります。 条件付き書式やその他の拡張機能にも式が使用されます。 詳細については、「[Power BI レポート ビルダーでの式](report-builder-expressions.md)」を参照してください。  
  
## <a name="do-you-want-to-hide-report-items-initially"></a>最初にレポート アイテムを非表示にするかどうか
  
レポートを最初に実行するときにデータ領域、グループ、列などのレポート アイテムを非表示にするかどうかを検討します。 たとえば、最初に概要テーブルを表示しておき、詳細データにドリル ダウンできるようにします。 
  
## <a name="how-are-you-going-to-deliver-your-report"></a>どのようにしてレポートを配信するか  
  
レポートをローカル コンピューターに保存して、引き続き操作したり、独自の情報に関してローカルで実行したりすることができます。 ただし、レポートを他のユーザーと共有するには、レポートを Power BI に保存する必要があります。 Power BI に保存すると、他のユーザーが必要なときにいつでも実行できるようになります。 別の方法として、レポートのサブスクリプションを設定し、レポートを他のユーザーにメールで配信することもできます。 必要に応じて、レポートを特定のエクスポート形式で配信できます。 
  
## <a name="next-steps"></a>次の手順

- [Power BI Premium のページ分割されたレポートとは](paginated-reports-report-builder-power-bi.md)
