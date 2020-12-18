---
title: Power Automate を使用してページ分割されたレポートをローカル フォルダーに保存する
description: この記事では、テンプレートを使用して、ページ分割されたレポートの定期的なエクスポートを、目的の形式でファイル システムに設定します。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 12/08/2020
LocalizationGroup: Get started
ms.openlocfilehash: a30f0df972c375af4fb284ce3bba5372870d6efb
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97098686"
---
# <a name="save-a-power-bi-paginated-report-to-a-local-folder--with-power-automate"></a>Power Automate を使用して Power BI のページ分割されたレポートをローカル フォルダーに保存する

[Power Automate](/power-automate/getting-started) を使用すると、サポートされているさまざまな形式やシナリオへの Power BI のページ分割されたレポートのエクスポートと配布を自動化できます。 この記事では、テンプレートを使用して、ページ分割されたレポートの定期的なエクスポートを、目的の形式でファイル システムに設定します。 Power Automate フローで [Export to File for Paginated Reports]\(ページ分割されたレポート用のファイルにエクスポートする\) アクションを初めて使用する場合は、前提条件を確認してください。

:::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-overview.png" alt-text="ページ分割されたレポートの定期的なエクスポートを設定します。":::

Power BI のページ分割されたレポート用の、その他の Power Automate テンプレートをお探しですか? 「[Power Automate を使用して Power BI のページ分割されたレポートをエクスポートする](service-automate-paginated-integration.md)」を参照してください。

## <a name="prerequisites"></a>前提条件  

先に進むには、次のものがあることを確認してください。

- 予約容量でサポートされている Power BI テナント内に少なくとも 1 つのワークスペース。 この容量は、A4/P1 – A6/P3 SKU のいずれかになります。 詳細については、[Power BI Premium のページ分割されたレポートの予約容量](../admin/service-premium-what-is.md#paginated-reports)に関する記事を参照してください。
- Office 365 サブスクリプションに付属する、Power Automate における標準コネクタへのアクセス。

## <a name="save-a-power-bi-paginated-report-to-a-local-folder"></a>Power BI のページ分割されたレポートをローカル フォルダーに保存する

1. **[Save a Power BI paginated report to a local file system\(Power BI のページ分割されたレポートをローカル ファイル システムに保存する\)]** テンプレートを選択します。 Power BI にサインインし、ローカル ファイル システムに接続していることを確認します。 **[続行]** をクリックします。 

    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-save-report-local-file-1.png" alt-text="Power BI のページ分割されたレポートをローカル ファイル システムに保存します。":::

2. 必要に応じて、 **[新しい接続を追加]** を選択して、ファイル システムに接続します。 
1. **[接続名]** 、目的の **ルート フォルダー** へのパスを入力し、 **[ユーザー名]** と **[パスワード]** を入力して認証します。 オンプレミス データ ゲートウェイを使用している場合は、ドロップダウンから 1 つの **[ゲートウェイ]** を選択します。

    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-set-file-system-2.png" alt-text="接続名とルート フォルダーを入力します。":::
 
3. フローの **[繰り返し]** の頻度を設定するには、 **[頻度]** ドロップダウンからオプションを選択して、目的の **[間隔]** 値を入力します。  

    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-recurrence-frequency-3.png" alt-text="フローに対する [繰り返し] の頻度を設定します。":::

4. 必要に応じて、 **[詳細オプションの表示]** を選択します。 **[タイム ゾーン]** 、 **[開始時刻]** 、 **[設定曜日]** 、 **[設定時刻 (時間)]** 、 **[設定時刻 (分)]** など、追加の **[繰り返し]** パラメーターを設定します。 
 
    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-recurrence-advanced-4.png" alt-text="繰り返しの詳細オプションを設定します。":::

5. **[ワークスペース]** ボックスで、レポートが配置されている予約容量のワークスペースを選択します。 **[レポート]** ボックスで、エクスポートするワークスペース内のページ分割されたレポートを選択します。 **[エクスポート形式]** ボックスで、目的のエクスポート形式を選択します。 必要に応じて、ページ分割されたレポートのパラメーターを指定できます。 [Power BI Rest API のコネクタのリファレンス](/connectors/powerbi/#export-to-file-for-paginated-reports)にあるパラメーターの詳細な説明をご覧ください。  
 
    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-select-workspace-report-5.png" alt-text="ワークスペースおよびレポートを選択します。":::

6. **[ファイルの作成]** ダイアログの **[フォルダー パス]** で、ページ分割されたレポートをエクスポートするフォルダーを選択します。
 
    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-create-file-6.png" alt-text="ページ分割されたレポートをエクスポートするフォルダーを選択する":::

7. **[ファイル名]** と **[ファイルの内容]** は Power Automate によって自動的に生成されます。 **[ファイル名]** を変更することはできますが、動的に生成された **[ファイルの内容]** 値はそのままにします。
8. 完了したら、 **[次のステップ]** または **[保存]** を選択します。 Power Automate によってフローが作成され、評価されます。
9. Power Automate によってエラーが検出された場合は、 **[フローの編集]** を選択して修正します。 それ以外の場合は、[戻る] の矢印を選択してフローの詳細を表示し、新しいフローを実行します。
10. フローを実行すると、Power Automate によって、指定した形式でページ分割されたレポートが、ファイル システム内の選択されたフォルダーにエクスポートされます。

    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-exported-10.png" alt-text="Power Automate によって、ページ分割されたレポートが指定した形式でエクスポートされます。":::

## <a name="next-steps"></a>次のステップ

- [Power Automate を使用して Power BI のページ分割されたレポートをエクスポートする](service-automate-paginated-integration.md)
- [Power Automate の概要](/power-automate/getting-started/)
- 他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。

