---
title: Power Automate を使用してレポートをエクスポートしてメールで送信する
description: この記事では、Power Automate を使用して、サポートされているさまざまな形式とシナリオで、Power BI レポートのエクスポートと配布を自動化します。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 12/10/2020
LocalizationGroup: Get started
ms.openlocfilehash: 45bccbefc6e499375d33aa049ead8a6c6e47bc8c
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97098829"
---
# <a name="export-and-email-a-power-bi-report-with-power-automate"></a>Power Automate を使用して、Power BI レポートをエクスポートし、電子メールで送信する

[Power Automate](/power-automate/getting-started) を使用すると、Power BI のページ分割されたレポートをさまざまな形式やシナリオに自動的にエクスポートして配布できます。 この記事では、独自のフローをゼロから作成します。 Power BI レポートを電子メールで自動的に配布するには、[Export to File for Power BI Reports\(Power BI レポートのファイルにエクスポートする\)] アクションを使用します。

:::image type="content" source="media/service-automate-power-bi-report-export/automate-power-bi-report-overview.png" alt-text="レポートをエクスポートしてメールで送信するための Power Automate の手順。":::

## <a name="prerequisites"></a>前提条件  

先に進むには、次のものがあることを確認してください。

- 予約容量でサポートされている Power BI テナント内に少なくとも 1 つのワークスペース。 この容量は、A1/EM1 から A6/P3 SKU のいずれかになります。 Power BI Premium の予約容量の詳細については、[こちら](../admin/service-premium-what-is.md)を参照してください。
- Office 365 サブスクリプションに付属する、Power Automate における標準コネクタへのアクセス。

## <a name="create-a-flow-from-scratch"></a>ゼロからフローを作成する 

このタスクでは、単純なフローをゼロから作成します。 フローでは、Power BI レポートを PDF としてエクスポートし、週単位で送信される電子メールに添付します。  

1. Power Automate にサインインします (flow.microsoft.com)。
2. **[作成]**  >  **[予定フロー]** の順に選択します。 

    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-scheduled-flow-2.png" alt-text="Power Automate で予定フローを作成します。":::

3. **[予定フローを作成]** で、フローに名前を付けます。 
4. **[このフローを実行する]** で、フローの開始日時と繰り返しの頻度を選択します。
5. **[設定曜日]** で、フローを実行する曜日を選択し、 **[作成]** を選択します。

    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-build-flow-5.png" alt-text="Power Automate を使用して、フローのスケジュール設定を行います。":::

6. **[繰り返し]** で、 **[詳細オプションの表示]** を選択して、 **[設定時刻 (時間)]** および **[設定時刻 (分)]** に値を入力し、フローを実行する指定時刻を設定します。
 
    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-recurrence-6.png" alt-text="Power Automate で繰り返しを設定します。":::

7. **[新しいステップ]** を選択します。
8. **[アクションの選択]** で、 **[Power BI]** を検索して **[Export to File for Power BI Reports\(Power BI レポート用のファイルにエクスポートする\)]** を選択します。
 
    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-choose-action-8.png" alt-text="Power Automate でのアクションを選択します。":::

9. **[Export to File for Power BI Reports\(Power BI レポート用のファイルにエクスポートする\)]** で、 **[ワークスペース]** と **[レポート]** を各ドロップダウンから選択します。
10. Power BI レポートに必要な **[エクスポート形式]** を選択します。
 
    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-export-file-10.png" alt-text="Power Automate でのエクスポート形式を選択します。":::

11. 必要に応じて、 **[Pages pageName -1\(ページ pageName -1\)]** フィールドでエクスポートする特定のページを指定します。 ページ名のパラメーターは表示ページ名とは異なることに注意してください。 Power BI サービスのページに移動し、URL の最後の部分をコピーして、ページ名を検索します。
 
     :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-copy-url-11.png" alt-text="URL でのページ名を選択します。":::

12. 必要に応じて、 **[Pages Bookmark Name]\(ページのブックマーク名\)** フィールドに表示する特定のブックマークを指定します。 ページ名のパラメーターと同様に、レポートの URL でブックマーク名のパラメーターを見つけます。 Power BI レポートに対して、追加のパラメーターを指定できます。 これらのパラメーターの詳細な説明は、[Power BI REST API のコネクタのリファレンス](/connectors/powerbi/#export-to-file-for-power-bi-reports)で確認できます。

    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-bookmark-url-12.png" alt-text="URL でのブックマーク名を選択します。":::

13. **[新しいステップ]** を選択します。
14. **[アクションの選択]** で、 **[Outlook]** を検索して **[メールの送信 (V2)]** を選択します。
15. **[メールの送信 (V2)]** で、電子メールの **[宛先]** 、 **[件名]** 、および **[本文]** フィールドを入力します。
16. **[詳細オプションの表示]** 　を選択します。 **[Attachments Name – 1\(添付ファイル名 – 1\)]** で、添付ファイルの名前を入力します。 ファイル名に目的の **[エクスポート形式]** に合ったファイル拡張子 (PDF など) を追加します。
17. **[添付ファイルの内容]** で、 **[ファイルの内容]** を選択して、エクスポートした Power BI レポートを添付します。  
 
    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-send-email-17.png" alt-text="電子メールにエクスポートしたレポートを選択します。":::

18. 完了したら、 **[次のステップ]** または **[保存]** を選択します。 Power Automate によってフローが作成および評価され、エラーが検出された場合は通知されます。
1. エラーが発生した場合は、 **[フローの編集]**   を選択して修正します。 それ以外の場合は、 **[戻る]** の矢印を選択してフローの詳細を表示し、新しいフローを実行します。
    フローを実行すると、Power Automate によって、指定した形式で Power BI レポートがエクスポートされ、スケジュールに従って電子メールの添付ファイルとして送信されます。  

## <a name="next-steps"></a>次のステップ

- [Power BI データ アラートを Power Automate と統合する](service-flow-integration.md)
- [Power Automate の概要](/power-automate/getting-started/)
- 他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。
