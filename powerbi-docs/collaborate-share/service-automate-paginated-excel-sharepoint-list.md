---
title: Excel Online テーブルまたは SharePoint リスト内の行ごとにページ分割されたレポートをエクスポートする
description: この記事では、Power Automate を使用して、Excel Online テーブルまたは SharePoint Online リストの各行について、ページ分割されたレポートのエクスポートを自動化します。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 12/08/2020
LocalizationGroup: Get started
ms.openlocfilehash: 7a48a9a594364de4261aa66de48c1a4262392364
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97097848"
---
# <a name="export-a-paginated-report-for-each-row-in-an-excel-online-table-or-sharepoint-list"></a>Excel Online テーブルまたは SharePoint リスト内の行ごとにページ分割されたレポートをエクスポートする

[Power Automate](/power-automate/getting-started) を使用すると、サポートされているさまざまな形式やシナリオへの Power BI のページ分割されたレポートのエクスポートと配布を自動化できます。 この記事では、Power Automate のテンプレートを使用して、1 つまたは複数のページ分割されたレポートの定期的なエクスポートの設定を自動化します。 Excel Online テーブルまたは SharePoint Online リストの各行に対して、必要な形式でエクスポートします。 エクスポートされたページ分割されたレポートを OneDrive for Business または SharePoint Online サイトに配布するか、Office 365 Outlook を使用して電子メールで送信することができます。

:::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-overview.png" alt-text="Excel Online テーブルを使用して、ページ分割されたレポートをエクスポートします。":::

Excel Online テーブルまたは SharePoint Online リストの各行は、サブスクリプションごとにページ分割されたレポートを受信する 1 人のユーザーを表します。 または、各行が、配布する一意のページ分割されたレポートを表します。 テーブルまたはリストには、OneDrive、SharePoint Online、Outlook のいずれであるかにかかわらず、レポートの配信方法を指定する列が必要です。 Power Automate フローの Switch ステートメントでこの列が使用されます。

Power BI のページ分割されたレポート用の、その他の Power Automate テンプレートをお探しですか? 「[Power Automate を使用して Power BI のページ分割されたレポートをエクスポートする](service-automate-paginated-integration.md)」を参照してください。

## <a name="prerequisites"></a>前提条件  

先に進むには、次のものがあることを確認してください。

- 予約容量でサポートされている Power BI テナント内に少なくとも 1 つのワークスペース。 この容量は、A4/P1 – A6/P3 SKU のいずれかになります。 詳細については、[Power BI Premium のページ分割されたレポートの予約容量](../admin/service-premium-what-is.md#paginated-reports)に関する記事を参照してください。
- Office 365 サブスクリプションに付属する、Power Automate における標準コネクタへのアクセス。
- Excel Online テーブルを使用している場合は、Excel のテーブルとして書式設定する必要があります。 詳細については、「[表を作成する](https://support.microsoft.com/office/create-a-table-in-excel-bf0ce08b-d012-42ec-8ecf-a2259c9faf3f)」を参照してください。

## <a name="export-a-paginated-report-for-each-row-in-a-table-or-list"></a>テーブルまたはリスト内の行ごとにページ分割されたレポートをエクスポートする

> [!NOTE]
> 次の手順と画像は、 **[Export a Power BI paginated report for each row in an Excel Online table]\(Excel Online テーブルの行ごとにページ分割されたレポートをエクスポートする\)** テンプレートを使用してフローを設定する方法を示しています。 同じ手順に従って、 **[Export a Power BI paginated report for items in a SharePoint Online list]\(SharePoint Online リストの項目に対応した Power BI のページ分割されたレポートをエクスポートする\)** テンプレートを使用してフローを作成します。 SharePoint Online リストには、Excel Online テーブルではなく、ページ分割されたレポートのエクスポート方法に関する情報が含まれます。  

1. Power Automate にサインインします ([flow.microsoft.com](https://flow.microsoft.com/))。 
1. **[テンプレート]** を選択し、 **ページ分割されたレポート** を検索します。 

    :::image type="content" source="media/service-automate-paginated-integration/power-bi-paginate-automate.png" alt-text="Power BI のページ分割されたレポート用の Power Automate テンプレートのスクリーンショット。":::

1. **[Export a Power BI paginated report for each row in an Excel Online table]\(Excel Online テーブルの行ごとに Power BI のページ分割されたレポートをエクスポートする\)** または **[Export a Power BI paginated report for items in a SharePoint Online list]\(SharePoint Online リストの項目に対応した Power BI のページ分割されたレポートをエクスポートする\)** テンプレートを選択します。 Excel Online、Power BI、OneDrive for Business、SharePoint Online、Office 365 Outlook にサインインしていることを確認します。 **[続行]** をクリックします。  

   :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-excel-online-1.png" alt-text="Excel Online テーブルの行ごとに Power BI のページ分割されたレポートをエクスポートします。":::

1. フローの **[繰り返し]** を設定するには、 **[頻度]** でオプションを選択し、目的の **[間隔]** 値を入力します。

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-recurrence-2.png" alt-text="フローの繰り返しを選択します。":::

1. (オプション) **[詳細オプションの表示]** を選択して、 **[繰り返し]** のその他のパラメーターを設定します。これには **[タイム ゾーン]** 、 **[開始時刻]** 、 **[設定曜日]** 、 **[設定時刻 (時間)]** 、 **[設定時刻 (分)]** が含まれます。

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-advanced-recurrence-3.png" alt-text="オプションで、繰り返しの詳細オプションを選択します。":::

1. **[場所]** ボックスで、Excel Online テーブルまたは SharePoint Online リストが保存されている OneDrive for Business または SharePoint Online サイトを選択します。 次に、ドロップダウンから **[ドキュメント ライブラリ]** を選択します。

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-location-4.png" alt-text="Excel Online テーブルの場所を選択します。":::

1. **[ファイル]** ボックスで、Excel Online ファイルまたは SharePoint Online リストを選択します。 **[テーブル]** ボックスのドロップダウンから、テーブルまたはリストの名前を選択します。 
 
    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-file-table-5.png" alt-text="Excel Online ファイルとテーブルの名前を選択します。":::

    > [!TIP]
    > Excel でデータをテーブルとして書式設定する方法については、「[表を作成する](https://support.microsoft.com/office/create-a-table-in-excel-bf0ce08b-d012-42ec-8ecf-a2259c9faf3f)」を参照してください。 

1. ファイル名に使用する変数を初期化します。 **[名前]** と **[値]** は既定値のままにすることも変更することもできますが、 **[型]** は **[文字列]** に等しいままにします。  

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-name-type-6.png" alt-text="[名前] と [値] に入力し、[型] を [文字列] のままにします。":::

1. **[Apply to Each]** で、 **[Select an output from previous step]\(前のステップの出力を選択する\)** ボックスが既定により **[値]** に設定されます。 この設定により、 **[Apply to Each]** に含まれるアクションが、Excel Online テーブルまたは SharePoint Online リスト内の行ごとに反復処理されます。  

1. **[ワークスペース]** ボックスで、予約容量のワークスペースを選択します。 **[レポート]** ボックスで、エクスポートする選択したワークスペース内のページ分割されたレポートを選択します。 ドロップダウンから **[Enter a custom value]\(カスタム値を入力\)** を設定した場合は、 **[ワークスペース]** と **[レポート]** を、Excel Online テーブルまたは SharePoint Online リストの列と同じにすることができます。 これらの列には、それぞれワークスペース ID とレポート ID が含まれている必要があります。  

1. ドロップダウンから **[エクスポート形式]** を選択するか、必要なエクスポート形式を含む Excel Online テーブルの列と同じになるように設定します。 たとえば、PDF、DOCX、または PPTX です。 必要に応じて、ページ分割されたレポートのパラメーターを指定できます。 パラメーターの詳細な説明は、[Power BI REST API のコネクタのリファレンス](/connectors/powerbi/#export-to-file-for-paginated-reports)に記載されています。

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-export-format-9.png" alt-text="[Export to File for Paginated Reports]\(ページ分割されたレポート用のファイルにエクスポートする\) に入力します。":::

1. **[値]** ボックスに、エクスポート後のページ分割されたレポートの名前を入力します。 必ずファイル拡張子を入力してください。 .pdf、.docx、.pptx などを静的に設定できます。 または、必要なエクスポート形式に対応した Excel テーブルの列を選択して、動的に設定します。 

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-output-value-10.png" alt-text="レポートの名前とファイル拡張子を選択します。":::

1. **[スイッチ]** アクションの **[オン]** ボックスに、目的の配信方法に対応した Excel Online テーブルの列を設定します。 **[OneDrive]** 、 **[SharePoint]** 、または **[電子メール]** です。 

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-switch-11.png" alt-text="[スイッチ] で、[オン] ボックスに Excel Online テーブルの列を入力します。":::

1. **[ケース]** 、 **[ケース 2]** 、 **[ケース 3]** に、前の手順で選択した Excel Online テーブル列に存在する値を入力します。  

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-case-1-2-3-12.png" alt-text="[ケース]、[ケース 2]、[ケース 3] の値を入力します。":::

1. ページ分割されたレポートを OneDrive に保存する場合は、それを保存する **フォルダーのパス** を選択します。  

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-case-onedrive-13.png" alt-text="OneDrive に保存する場合。":::

1. ページ分割されたレポートを SharePoint Online に保存する場合は、保存場所の **サイト アドレス** と **フォルダーのパス** を入力します。 

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-case-sharepoint-14.png" alt-text="ページ分割されたレポートを SharePoint Online に保存する場合。":::

1. ページ分割されたレポートを Outlook を使用して電子メールとして送信する場合は、 **[宛先]** 、 **[件名]** 、 **[本文]** ボックスに入力します。 これらのボックスには、静的コンテンツ、または Excel Online テーブルまたは SharePoint Online リストからの動的コンテンツを含めることができます。 Power Automate により、ページ分割されたレポートがこの電子メールに自動的に添付されます。  

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-case-email-15.png" alt-text="ページ分割されたレポートを Outlook を使用して電子メールとして送信する場合。":::

1. 完了したら、 **[次のステップ]**  または **[保存]** を選択します。 Power Automate によってフローが作成および評価され、エラーが検出された場合は通知されます。 

1. エラーが発生した場合は、 **[フローの編集]**   を選択して修正します。 それ以外の場合は、 **[戻る]** の矢印を選択してフローの詳細を表示し、新しいフローを実行します。 


## <a name="next-steps"></a>次のステップ

- [Power Automate を使用して Power BI のページ分割されたレポートをエクスポートする](service-automate-paginated-integration.md)
- [Power Automate の概要](/power-automate/getting-started/)
- 他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。

