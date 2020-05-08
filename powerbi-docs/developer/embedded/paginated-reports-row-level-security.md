---
title: Power BI の埋め込みコンテンツで行レベルのセキュリティを使用する
description: ここでは、アプリケーション内に Power BI コンテンツを埋め込むために必要な手順について説明します。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: nishalit
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 11/04/2019
ms.openlocfilehash: 8d3068453ea2d166b0b55fbba45d8452431de319
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "79491734"
---
# <a name="implementing-row-level-security-in-embedded-paginated-reports-preview"></a>埋め込みのページ分割されたレポート (プレビュー) での行レベルのセキュリティの実装

ページ分割されたレポートを埋め込むときに、どのデータが表示されるかを制御できます。 これにより、ユーザーごとに表示される情報を調整できます。 たとえば、グローバルな売上結果を含む、Power BI のページ分割されたレポートがある場合は、特定の地域の売上結果のみを使用できるように埋め込むことができます。

この機能を使用すると、データのサブセットを安全に表示することができ、データの残りの部分が侵害されることがありません。 これは、[行レベル セキュリティ (RLS)](embedded-row-level-security.md) 機能に似ています。この機能では、Power BI レポート (ページ分割されていないもの)、ダッシュボード、タイル、およびデータセットで、データを安全に表示することができます。  

> [!NOTE]
> この機能は、顧客向けにページ分割されたレポートを埋め込む場合に使用します。

## <a name="configuring-a-parameter-to-filter-the-dataset"></a>データセットをフィルター処理するためのパラメーターを構成する

Power BI のページ分割されたレポートに行レベルのセキュリティを適用する場合は、[UserID 属性](../../paginated-reports/report-builder-parameters.md)に**パラメーター**を割り当てる必要があります。 このパラメーターは、レポートが埋め込まれる前に、データセットからプルされるデータを制限します。

パラメーターを **UserID** に割り当てた後、[Reports GenerateTokenForCreateInGroup](https://docs.microsoft.com/rest/api/power-bi/embedtoken/reports_generatetokenforcreateingroup) API を使用して、埋め込みトークンを取得します。

## <a name="use-userid-as-a-filter-at-report-or-query-level"></a>レポートまたはクエリのレベルで UserID をフィルターとして使用する

**UserId** は、"*フィルター*" として使用することや、*Power BI Report Builder* で、データソースに対する "[クエリ](../../paginated-reports/report-builder-power-bi.md)" に使用することができます。

### <a name="using-the-filter"></a>フィルターの使用

1. **[データセットのプロパティ]** ウィンドウの左側のペインで、 **[フィルター]** を選択します。

    ![Power BI レポート ビルダーでのフィルター](media/paginated-reports-row-level-security/filter.png)

2. **[式]** ドロップダウン メニューで、データのフィルター処理に使用するパラメーターを選択します。

     ![Power BI レポート ビルダーでの式](media/paginated-reports-row-level-security/expression.png)

3. **[値]** 関数ボタンをクリックします。 

    ![Power BI レポート ビルダーでの値](media/paginated-reports-row-level-security/function.png)

4. **[式]** ウィンドウの **[カテゴリ]** の一覧で、 **[組み込みフィールド]** を選択します。

    ![Power BI レポート ビルダーでの式](media/paginated-reports-row-level-security/built-in-fields.png)

5. **[アイテム]** の一覧で **[UserID]** を選択し、 **[OK]** をクリックします。

    ![Power BI レポート ビルダーでの UserID](media/paginated-reports-row-level-security/userid.png)

6. **[データセットのプロパティ]** ウィンドウで、式が " *<選択したパラメーター> = UserID*" であることを確認し、 **[OK]** をクリックします。

    ![Power BI レポート ビルダーのデータセットのプロパティ](media/paginated-reports-row-level-security/verify.png)

### <a name="using-a-query"></a>クエリの使用

1. **[データセットのプロパティ]** ウィンドウの左側のペインで **[パラメーター]** を選択し、 **[追加]** をクリックします。

    ![Power BI レポート ビルダーでのパラメーター](media/paginated-reports-row-level-security/parameters.png)

2. **[パラメーター名]** に「 **\@UserID**」と入力し、 **[パラメーター値]** に **[&UserID]** を追加します。

    ![Power BI レポート ビルダーでのパラメーター名](media/paginated-reports-row-level-security/parameter-name.png) 

3. 左側のペインで、 **[クエリ]** を選択し、[クエリ] で **UserID** パラメーターをクエリの一部として追加し、 **[OK]** をクリックします。
    > [!NOTE]
    > 下のスクリーンショットでは、color パラメーターが例として使用されています (whereFinalTable.Color = @UserID)。 必要に応じて、より複雑なクエリを作成することもできます。

    ![Power BI レポート ビルダーでのクエリの編集](media/paginated-reports-row-level-security/query-edit.png)

## <a name="passing-the-configured-parameter-using-the-embed-token"></a>埋め込みトークンを使用して構成済みのパラメーターを渡す

顧客向けのページ分割されたレポートを埋め込むときに、[Reports GenerateTokenForCreateInGroup](https://docs.microsoft.com/rest/api/power-bi/embedtoken/reports_generatetokenforcreateingroup) API を使用して、埋め込みトークンが取得されます。 このトークンを使用して、ページ分割されたレポートからプルされるデータの一部をフィルター処理することもできます。

データの一部のみを公開するには、表示する情報を `username` フィールドに割り当てます。 たとえば、color パラメーターを持つページ分割されたレポートで、 *フィールドに「* green`username`」と入力すると、埋め込みトークンによって埋め込みデータが制限され、color 列の値が *green* であるデータのみが表示されます。

```JSON
{
    "accessLevel": "View",
    "reportId": "cfafbeb1-8037-4d0c-896e-a46fb27ff229",
    "identities": [
            {
                    // Replace the 'username' with a paginated report parameter
                    "username":     "...",
                    "reports: [
                        "cfafbeb1-8037-4d0c-896e-a46fb27ff229"
                    ]
            }
    ]
}
```
