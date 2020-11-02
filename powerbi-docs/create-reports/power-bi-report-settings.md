---
title: Power BI レポートの設定を変更する
description: Power BI サービスでレポートの設定を変更する
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 10/14/2020
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: dd87501a6865b9ea450e3154ee2ac56e0710a067
ms.sourcegitcommit: fddba666c6ea90d525a1c3188bbd3c4a03410cdc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2020
ms.locfileid: "92463083"
---
# <a name="change-settings-for-power-bi-reports"></a>Power BI レポートの設定を変更する

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Power BI Desktop および Power BI サービスのレポート設定を使用すると、レポート閲覧者が行うレポート操作の方法を制御することができます。 たとえば、彼らがレポートのフィルターを保存したり、レポート内のビジュアルを個人用に設定したり、レポート ページを側部に沿ってではなくレポートの下部にわたってタブとして表示したりするのを許可することができます。

:::image type="content" source="media/power-bi-report-settings/service-report-settings-pane.png" alt-text="Power BI サービスでの [レポートの設定] ウィンドウのスクリーンショット":::

まず、次の記事を読むことをお勧めします。

- [Power BI サービスでデータセットをインポートすることでレポートを作成する](service-report-create-new.md)。レポート作成のエクスペリエンスを理解できます。
- [Power BI のレポート](../consumer/end-user-reports.md)。レポートの閲覧者のエクスペリエンスを理解できます。

 それでは作業を始めましょう。

## <a name="prerequisites"></a>前提条件

- Power BI Desktop を使用したレポート作成については、[Desktop のレポート ビュー](desktop-report-view.md)に関するページをご覧ください。
- [Power BI サービスにサインアップする](../fundamentals/service-self-service-signup-for-power-bi.md)。 
- Power BI サービス内のレポートに対する編集アクセス許可を取得している必要があります。 アクセス許可の詳細については、「[新しいワークスペースのロール](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces)」を参照してください。
- Power BI サービス内にレポートがまだない場合は、ダッシュボード、レポート、およびデータセットを含む[サンプル コンテンツ パックをインストールする](sample-datasets.md#install-built-in-content-packs)ことができます。

## <a name="open-the-settings-pane-in-power-bi-desktop"></a>Power BI Desktop で [設定] ウィンドウを開く

1. **[ファイル]**  >  **[オプションと設定]**  >  **[オプション]** の順に選択します。
1. **[現在のファイル]** の **[レポートの設定]** を選択します。

    :::image type="content" source="media/power-bi-report-settings/desktop-report-settings-pane.png" alt-text="Power BI サービスでの [レポートの設定] ウィンドウのスクリーンショット":::

    この記事の残りの部分では、いくつかの特定のレポート設定に注目します。

## <a name="open-the-settings-pane-in-the-power-bi-service"></a>Power BI サービスで [設定] ウィンドウを開く

1. レポートの読み取りビューで、 **[ファイル]**  >  **[設定]** の順に選択します。

    :::image type="content" source="media/power-bi-report-settings/service-report-file-settings.png" alt-text="Power BI サービスでの [レポートの設定] ウィンドウのスクリーンショット":::

1. **[設定]** ウィンドウに、このレポートに対して設定できるトグルが複数表示されます。 この記事の残りの部分では、それらのいくつかに注目します。

## <a name="set-featured-content"></a>おすすめのコンテンツを設定する

ダッシュボード、レポート、アプリをおすすめに登録し、同僚の Power BI ホーム ページの [おすすめ] セクションに表示させることができます。 詳細については、[コンテンツをおすすめに登録する方法](../collaborate-share/service-featured-content.md)に関するページを参照してください。

## <a name="set-the-pages-pane"></a>[ページ ウィンドウ] を設定する

現在、Power BI サービス内で変更できるのは [ページ ウィンドウ] 設定のみです。 **[ページ ウィンドウ]** をオンに切り替えると、レポートの閲覧者にはレポート ページ タブが、読み取りビュー内のレポートの側部に沿ってではなく、下部に沿って表示されます。 編集ビューでは、レポート ページ タブは既にレポートの下部に配置されています。

:::image type="content" source="media/power-bi-report-settings/report-settings-pages-pane.png" alt-text="Power BI サービスでの [レポートの設定] ウィンドウのスクリーンショット":::

## <a name="control-filters"></a>フィルターを制御する

レポートの **[設定]** ウィンドウには、レポートに対して閲覧者が行うフィルターの操作を制御するための設定が 3 つあります。 以下のリンクから記事「[Power BI レポートでフィルターをデザインする](power-bi-report-filter.md)」にアクセスすれば、各設定の詳細を確認できます。

- **[固定フィルター]** を使用すると、[レポートに対するフィルターを保存する](power-bi-report-filter.md#allow-saving-filters)ことを閲覧者に許可できます。
- **[フィルター処理エクスペリエンス]** に、さらに次の 2 つの設定があります。
    
    [フィルターの種類を変更する](power-bi-report-filter.md#restrict-changes-to-filter-type)ことをレポートの閲覧者に許可できます。

    [フィルター ウィンドウ内での検索](power-bi-report-filter.md#filters-pane-search)を有効にします。

## <a name="export-data"></a>データのエクスポート

既定では、レポート内のビジュアルから、[レポートの閲覧者は概要または基本のデータをエクスポートすることができます](../consumer/end-user-export.md)。 **[データのエクスポート]** を使用すると、彼らに、概要データのみのエクスポートを許可することも、レポートからのデータのエクスポートを一切許可しないこともできます。

## <a name="personalize-visuals"></a>ビジュアルのカスタマイズ

レポート内のビジュアルを変更し、個人用に設定することを閲覧者に許可できます。 詳細については、[レポートの閲覧者がビジュアルを個人用に設定できるようにする方法](power-bi-personalize-visuals.md)に関するページを参照してください。

## <a name="next-steps"></a>次のステップ

* [他のホーム ページ上でコンテンツをおすすめに登録する](../collaborate-share/service-featured-content.md)
* [レポートの閲覧者がレポート内のビジュアルを個人用に設定できるようにする](power-bi-personalize-visuals.md)
* 他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。
