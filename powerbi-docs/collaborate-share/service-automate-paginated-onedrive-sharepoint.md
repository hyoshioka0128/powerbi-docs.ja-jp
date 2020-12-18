---
title: ページ分割されたレポートを OneDrive for Business または SharePoint Online に保存する
description: この記事では、Power Automate を使用して、Power BI のページ分割されたレポートを OneDrive for Business または SharePoint Online フォルダーに保存する方法を自動化します。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 11/17/2020
LocalizationGroup: Get started
ms.openlocfilehash: 6aaad48fb3e97aa6c1b4fc51834ee593a49a8192
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97097733"
---
# <a name="save-a-paginated-report-to-onedrive-for-business-or-sharepoint-online"></a>ページ分割されたレポートを OneDrive for Business または SharePoint Online に保存する

[Power Automate](/power-automate/getting-started) を使用すると、サポートされているさまざまな形式やシナリオへの Power BI のページ分割されたレポートのエクスポートと配布を自動化できます。 この記事では、Power Automate を使用して、Power BI のページ分割されたレポートを OneDrive for Business または SharePoint Online フォルダーに保存する方法を自動化します。


:::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/paginated-onedrive-flow.png" alt-text="ページ分割されたレポートを OneDrive または SharePoint Online に保存するための Power Automate フローのスクリーンショット":::

Power BI のページ分割されたレポート用の、その他の Power Automate テンプレートをお探しですか? 「[Power Automate を使用して Power BI のページ分割されたレポートをエクスポートする](service-automate-paginated-integration.md)」を参照してください。 

## <a name="prerequisites"></a>前提条件  

先に進むには、次のものがあることを確認してください。

- 予約容量でサポートされている Power BI テナント内に少なくとも 1 つのワークスペース。 この容量は、A4/P1 – A6/P3 SKU のいずれかになります。 詳細については、[Power BI Premium のページ分割されたレポートの予約容量](../admin/service-premium-what-is.md#paginated-reports)に関する記事を参照してください。
- Office 365 サブスクリプションに付属する、Power Automate における標準コネクタへのアクセス。

## <a name="save-a-paginated-report-to-onedrive-for-business-or-a-sharepoint-online-folder"></a>ページ分割されたレポートを OneDrive for Business または SharePoint Online フォルダーに保存する 

これらのテンプレートのいずれかを使用して、必要な形式のページ分割されたレポートを OneDrive for Business または SharePoint Online フォルダーに定期的にエクスポートするように設定します。 Power Automate フローで [Export to File for Paginated Reports]\(ページ分割されたレポート用のファイルにエクスポートする\) アクションを初めて使用する場合は、前提条件を確認してください。 

> [!NOTE]
> 次の手順と画像は、 **[Save a Power BI paginated report to OneDrive for Business]\(Power BI のページ分割されたレポートを OneDrive for Business に保存する\)** テンプレートを使用してフローを設定する方法を示しています。 同じ手順に従って、 **[Save a Power BI paginated report to a SharePoint Online folder]\(Power BI のページ分割されたレポートを SharePoint Online フォルダーに保存する\)** テンプレートを使用してフローを作成します。 ページ分割されたレポートをエクスポートする場所を選択するときは、OneDrive for Business フォルダーではなく、SharePoint Online フォルダーを選択します。 

1. Power Automate にサインインします ([flow.microsoft.com](https://flow.microsoft.com/))。 
1. **[テンプレート]** を選択し、 **ページ分割されたレポート** を検索します。 

    :::image type="content" source="media/service-automate-paginated-integration/power-bi-paginate-automate.png" alt-text="Power BI のページ分割されたレポート用の Power Automate テンプレートのスクリーンショット。":::

1. **[Save a Power BI paginated report to OneDrive for Business]\(Power BI のページ分割されたレポートを OneDrive for Business に保存する\)** または **[Save a Power BI paginated report to a SharePoint Online folder]\(Power BI のページ分割されたレポートを SharePoint Online フォルダーに保存する\)** を選択します。 Power BI と OneDrive for Business または SharePoint Online にサインインしていることを確認します。

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-step1.png" alt-text="Power BI と OneDrive for Business テンプレートを選択しているスクリーンショット。":::
1. **[続行]** をクリックします。  


1. フローの **[繰り返し]** を設定するには、 **[頻度]** でオプションを選択し、目的の **[間隔]** 値を入力します。

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-2-recurrence.png" alt-text="フローの繰り返しを選択しています。":::

1. (オプション) **[詳細オプションの表示]** を選択して、 **[繰り返し]** のその他のパラメーターを設定します。これには **[タイム ゾーン]** 、 **[開始時刻]** 、 **[設定曜日]** 、 **[設定時刻 (時間)]** 、 **[設定時刻 (分)]** が含まれます。  

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-3-advanced-recurrence.png" alt-text="繰り返しの詳細オプションを表示しています。":::

1. **[ワークスペース]** ボックスで、予約容量のワークスペースを選択します。 **[レポート]** ボックスで、エクスポートする選択したワークスペース内のページ分割されたレポートを選択します。 **[エクスポート形式]** ボックスで、目的のエクスポート形式を選択します。 必要に応じて、ページ分割されたレポートのパラメーターを指定できます。 パラメーターの詳細な説明は、[Power BI REST API のコネクタのリファレンス](/connectors/powerbi/#export-to-file-for-paginated-reports)に記載されています。  

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-4-export-format.png" alt-text="ページ分割されたレポート、ワークスペース、エクスポート形式を選択しています。":::

1. **[フォルダー パス]** で、ページ分割されたレポートをエクスポートする OneDrive for Business または SharePoint Online フォルダーを選択します。

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-5-create-file.png" alt-text="宛先を選択してファイルを作成しています。":::

1. **[ファイル名]** と **[ファイルの内容]** は Power Automate によって自動的に生成されます。 ファイル名を変更することはできますが、動的に生成された **[ファイルの内容]** 値のままにします。 

1. 完了したら、 **[次のステップ]**  または **[保存]** を選択します。 Power Automate によってフローが作成および評価され、エラーが検出された場合は通知されます。 

1. エラーが発生した場合は、 **[フローの編集]**   を選択して修正します。 それ以外の場合は、 **[戻る]** の矢印を選択してフローの詳細を表示し、新しいフローを実行します。 

    フローを実行すると、Power Automate によって、指定した形式のページ分割されたレポートが OneDrive for Business または SharePoint Online にエクスポートされます。  

## <a name="next-steps"></a>次のステップ

- [Power Automate を使用して Power BI のページ分割されたレポートをエクスポートする](service-automate-paginated-integration.md)
- [Power Automate の概要](/power-automate/getting-started/)
- 他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。
