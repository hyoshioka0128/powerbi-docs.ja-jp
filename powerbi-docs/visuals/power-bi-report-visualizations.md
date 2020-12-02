---
title: Power BI サービスおよび Power BI Desktop でのレポートの視覚エフェクトの概要
description: Microsoft Power BI でのレポートの視覚エフェクト (ビジュアル) の概要
author: mihart
ms.author: mihart
ms.reviewer: mihart
featuredvideoid: ''
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: how-to
ms.date: 05/05/2020
LocalizationGroup: Visualizations
ms.openlocfilehash: b6b4ebb7d07ec73f8b2c51b7b2fabb75b197d91f
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96387438"
---
# <a name="visualizations-in-power-bi-reports"></a>Power BI レポートでの視覚エフェクト

[!INCLUDE[consumer-appliesto-yyyn](../includes/consumer-appliesto-yyyn.md)]    

視覚エフェクト (略してビジュアルとも呼ばれる) には、データ内で検出された分析情報が表示されます。 Power BI レポートは、ビジュアルが 1 つ使用された単一のページのこともあれば、ビジュアルが多数含まれる複数ページから成ることもあります。 Power BI サービスでは、ビジュアルを[レポートからダッシュボードにピン留め](../create-reports/service-dashboard-pin-tile-from-report.md)することができます。

レポートの "*デザイナー*" とレポートの "*コンシューマー*" とを区別することは重要です。  レポートのビルドまたは修正を行うのであれば、デザイナーということになります。  デザイナーには、レポートとその基になるデータセットに対して編集のためのアクセス許可が付与されます。 これは、Power BI Desktop では、データ ビューでデータセットを開き、レポート ビューでビジュアルを作成できることを意味し、 Power BI サービスでは、レポート エディターの[編集ビュー](../consumer/end-user-reading-view.md)で、データセットまたはレポートを開くことができることを意味します。 自分がレポートまたはダッシュボードの [共有相手](../consumer/end-user-shared-with-me.md)である場合は、レポート *コンシューマー* となります。 レポートとそのビジュアルを表示および操作することはできますが、"*デザイナー*" ほど多くの変更をすることはできません。

さまざまな種類のビジュアルを Power BI の [Visualizations]\(ビジュアル\) ペインで直接使用できます。

![各ビジュアルの種類のアイコンがあるペイン](media/power-bi-report-visualizations/power-bi-icons.png)

その他の Power BI の視覚エフェクトは、[Microsoft AppSource コミュニティ サイト](https://appsource.microsoft.com)から入手できます。 AppSource を使用すると、Microsoft とコミュニティによって提供される Power BI の視覚化を参照して[ダウンロード](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals)することができます。

Power BI を初めて使用する場合や、復習したい場合は、以下のリンクを使用して、Power BI 視覚エフェクトの基本を確認してください。  または、目次 (この記事の左側) を使用して役に立つ情報を見つけます。

## <a name="add-a-visualization-in-power-bi"></a>Power BI での視覚化の追加

レポートのページに[視覚エフェクトを作成](power-bi-report-add-visualizations-i.md)します。 [使用できる視覚エフェクトと使用できる視覚エフェクトのチュートリアルの一覧を参照](power-bi-visualization-types-for-reports-and-q-and-a.md)します。 

## <a name="upload-a-visualization-from-a-file-or-from-appsource"></a>ファイルまたは AppSource から視覚化をアップロードする

自分で作成した視覚化、または [Microsoft AppSource コミュニティ サイト](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals)で見つけた視覚化を追加します。 自分でカスタマイズする場合は、 ソース コードを調べ、[開発ツール](../developer/visuals/environment-setup.md)を使用して新しい視覚化の種類を作成し、[コミュニティと共有](../developer/visuals/office-store.md)します。 Power BI の視覚エフェクトの開発について詳しくは、[Power BI の視覚エフェクトの開発](../developer/visuals/develop-circle-card.md)に関する記事をご覧ください。

## <a name="personalize-your-visualization-pane"></a>[視覚化] ペインをカスタマイズする

[視覚化] ペインをカスタマイズするには、それに対して Power BI の視覚エフェクトを追加および削除します。 [視覚化] ペインから既定の視覚エフェクトを削除した場合は、ペインを既定の状態に復元して、既定の視覚エフェクトをすべて元に戻すことができます。

### <a name="add-a-visual-to-the-visualization-pane"></a>[視覚化] ペインに視覚エフェクトを追加する

多数のレポート間で同じ視覚エフェクトを使用している場合は、その視覚エフェクトを [視覚化] ペインに追加できます。 視覚エフェクトの追加は、AppSource の視覚エフェクト、組織の視覚エフェクト、およびファイルからの視覚エフェクトに適用されます。 視覚エフェクトを追加するには、視覚エフェクトを右クリックします。

![[視覚化] ウィンドウへのピン留め](media/power-bi-report-visualizations/power-bi-pin-custom-visual-option.png)

視覚エフェクトがピン留めされると、上に移動し、他の既定の視覚エフェクトとともにライブになります。 このビジュアルは、サインインしているアカウントに関連付けられます。そのため、ビルドするすべての新しいレポートで、サインインしているという想定で、このビジュアルが自動的に含められます。 あらゆるレポートに対して、定期的に使用する特定の視覚エフェクトを追加する必要がなくなりました。

![個人設定された [視覚化] ウィンドウ](media/power-bi-report-visualizations/power-bi-personalized-visualization-pane.png)

### <a name="remove-a-visual-from-the-visualization-pane"></a>[視覚化] ペインから視覚エフェクトを削除する

視覚エフェクトを定期的に使用しなくなった場合は、それを右クリックして [視覚化] ペインから削除することができます。 すべての種類の視覚エフェクトを [視覚化] ペインから削除できます。これには、既定、ファイル、組織、および AppSource の視覚エフェクトが含まれます。

![[視覚化] ペインへのピン留めを外す](media/power-bi-report-visualizations/unpin-visual.png)

### <a name="restore-the-visualization-pane"></a>[視覚化] ペインを復元する

[視覚化] ペインの復元は、既定の視覚エフェクトにのみ適用されます。 [視覚化] ペインに追加された視覚エフェクトは影響を受けず、引き続き [視覚化] ペインから使用できます。 [視覚化] ペインから AppSource またはファイルの視覚エフェクトを削除する場合は、手動で行う必要があります。

[視覚化] ペインを既定値に戻すには、その他のオプションをクリックして **[既定の視覚化の復元]** を選択します。

![[視覚化] ペインを既定値に復元する](media/power-bi-report-visualizations/restore-default.png)

## <a name="change-the-visualization-type"></a>視覚化の種類の変更

[視覚エフェクトの種類の変更](power-bi-report-change-visualization-type.md)を試して、そのデータに関して最も効果的な視覚エフェクトを確認します。

## <a name="pin-the-visualization"></a>視覚化のピン留め

Power BI サービスでは、希望する視覚エフェクトができたら、タイルとしてその[視覚エフェクトをダッシュボードにピン留め](../create-reports/service-dashboard-pin-tile-from-report.md)します。 ピン留めした後でレポートで使用されている視覚化を変更しても、ダッシュボード上のタイルは変更されません。 折れ線グラフの場合、それをレポートでドーナツ グラフに変更しても、折れ線グラフのままになります。

## <a name="limitations-and-considerations"></a>制限事項と考慮事項
- データ ソースやフィールド数 (メジャーまたは列) によっては、ビジュアルの読み込みが遅い場合があります。  読みやすさとパフォーマンス上の理由により、ビジュアルを合計 10 から 20 個のフィールドに制限することをお勧めします。 

- ビジュアルの上限は、フィールド 100 個です (メジャーまたは列)。 ビジュアルの読み込みに失敗した場合は、フィールド数を減らします。

## <a name="next-steps"></a>次の手順

* [Power BI での視覚化の種類](power-bi-visualization-types-for-reports-and-q-and-a.md)
* [Power BI ビジュアル](../developer/visuals/power-bi-custom-visuals.md)
