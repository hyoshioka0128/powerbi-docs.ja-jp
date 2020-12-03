---
title: ページ分割されたレポートを印刷するときに空白のページを表示しない
description: ページ分割されたレポートを印刷するときに空白のページが発生しないようにデザインするためのガイダンス。
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 01/14/2020
ms.openlocfilehash: 0fa886973105bdb4bc8a35f145168c1775ca12cb
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418465"
---
# <a name="avoid-blank-pages-when-printing-paginated-reports"></a>ページ分割されたレポートを印刷するときに空白のページを表示しない

この記事の対象読者は、Power BI の[ページ分割されたレポート](../paginated-reports/paginated-reports-report-builder-power-bi.md)をデザインするレポート作成者です。 PDF や Microsoft Word などのハードページ形式にレポートをエクスポートするとき、または印刷するときに、空白のページが発生しないようにするための推奨事項が示されています。

## <a name="page-setup"></a>ページ設定

ページの向き、サイズ、および余白は、レポートの [ページ サイズ] のプロパティによって決まります。 これらのレポートのプロパティには、次の方法でアクセスします。

- レポートの **プロパティ ページ** を使用する。レポート キャンバスの外側にある暗い灰色の領域を右クリックし、 _[レポートのプロパティ]_ を選択します。
- [ **[プロパティ]** ペイン](../paginated-reports/paginated-reports-report-design-view.md#4-properties-pane)を使用する。レポート キャンバスの外側にある暗い灰色の領域をクリックし、レポート オブジェクトを選択します。 **[プロパティ]** ペインが開くことを確認します。

レポートの **プロパティ ページ** の **[ページの設定]** ページには、ページ設定のプロパティを表示して更新するためのわかりやすいインターフェイスが表示されます。

![[レポートのプロパティ] ウィンドウを示している図。[ページ設定] ページが強調表示されている。](media/report-paginated-blank-page/report-page-setup-properties.png)

すべての [ページ サイズ] のプロパティが正しく構成されていることを確認します。

|プロパティ|推奨事項|
|---------|---------|
|ページの単位|関連する単位 ([インチ] または [センチメートル]) を選択します。|
|方向|適切なオプション ([縦] または [横]) を選択します。|
|[用紙サイズ]|用紙サイズを選択するか、カスタムの幅と高さの値を割り当てます。|
|余白|[左]、[右]、[上]、および [下] の余白に適切な値を設定します。|
|||

## <a name="report-body-width"></a>レポート本文の幅

[ページ サイズ] のプロパティによって、レポート オブジェクトで使用可能な領域が決まります。 レポート オブジェクトは、データ領域、データ視覚化、またはその他のレポート アイテムにすることができます。

空白のページが出力される一般的な理由は、レポート本文の幅が "_使用可能なページ領域を超えている_" ことです。

レポート本文の幅を表示および設定するには、 **[プロパティ]** ペインを使用する必要があります。 最初に、レポート本文の空の領域内の任意の場所をクリックします。

![[プロパティ] ペインを示している図。レポート本文の [幅] プロパティが強調表示されている。](media/report-paginated-blank-page/report-body-properties-width.png)

幅の値が、使用可能なページ幅を超えていないことを確認します。 次の式を参照してください。

```Report body width <= Report page width - (Left margin + Right margin)```

> [!NOTE]
> 削除する領域にレポート オブジェクトが既に存在する場合は、レポート本文の幅を小さくすることはできません。 幅を小さくする前に、それらの位置を変更するか、サイズを変更する必要があります。
>
> また、新しいオブジェクトを追加したり、既存のオブジェクトのサイズや位置を変更したりすると、レポート本文の幅が自動的に広がることがあります。 レポート デザイナーでは、含まれているオブジェクトの位置とサイズに合わせて、常に本文が拡大されます。

## <a name="report-body-height"></a>レポート本文の高さ

空白のページが出力される別の理由は、レポート本文で、最後のオブジェクトの後ろに余分なスペースがあることです。

末尾のスペースを削除するために、常に本文の高さを小さくすることをお勧めします。

![レポートのデザインを示している図。 Tablix データ領域の下の領域が強調表示され、不要としてマークされている。](media/report-paginated-blank-page/report-body-remove-trailing-space.png)

## <a name="page-break-options"></a>[改ページのオプション]

各データ領域とデータ視覚化には、改ページ オプションがあります。 これらのオプションには、プロパティ ページまたは **[プロパティ]** ペインでアクセスできます。

**[後に改ページを追加する]** プロパティが不必要に有効になっていないことを確認します。

![[Tablix プロパティ] ウィンドウを示している図。 [後に改ページを追加する] プロパティが有効になっている。](media/report-paginated-blank-page/data-region-page-break-option-after.png)

## <a name="consume-container-whitespace"></a>コンテナーの空白文字を使用する

空白のページの問題が引き続き発生する場合は、レポートの **[ConsumeContainerWhitespace]** プロパティの無効化を試すこともできます。 それは、 **[プロパティ]** ペインでのみ設定できます。

![[プロパティ] ペインを示している図。[ConsumeContainerWhitespace] プロパティが強調表示されている。](media/report-paginated-blank-page/report-properties-consumecontainerwhitespace.png)

それは、既定では有効になっています。 それは、レポート本文や四角形など、コンテナー内で最小限のホワイトスペースを使用するかどうかを指示します。 コンテンツの右側と下部のホワイトスペースのみが影響を受けます。

## <a name="printer-paper-size"></a>プリンターの用紙サイズ

最後に、レポートを用紙に印刷する場合は、プリンターに適切な用紙がセットされていることを確認します。 物理的な用紙サイズは、[レポートの用紙サイズ](#page-setup)に対応している必要があります。

## <a name="next-steps"></a>次の手順

この記事に関する詳細については、次のリソースを参照してください。

- [Power BI Premium のページ分割されたレポートとは](../paginated-reports/paginated-reports-report-builder-power-bi.md)
- [Power BI のページ分割されたレポートでの改ページ](../paginated-reports/paginated-reports-pagination.md)
- わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
- Power BI チームへのご提案は、 [Power BI を改善するためのアイデアをお寄せください](https://ideas.powerbi.com)
