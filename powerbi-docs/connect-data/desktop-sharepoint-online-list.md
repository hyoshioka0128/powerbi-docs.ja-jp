---
title: SharePoint リスト上にレポートを作成する
description: このチュートリアルでは、ご利用の SharePoint リスト データを Power BI レポートに変換する方法について説明します。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 01/10/2020
LocalizationGroup: Visualizations
ms.openlocfilehash: 5347405c13f71fa0932c48eb218618b28a9f03c8
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96404527"
---
# <a name="create-a-report-on-a-sharepoint-list"></a>SharePoint リスト上にレポートを作成する

SharePoint Online のリストは、設定するのが簡単であることに加えて、ユーザーが更新を簡単に行えるため、多くのチームや組織で使用されています。  ユーザーがデータをすばやく理解する上で、グラフはリスト自体を見るよりもはるかに簡単な方法である場合があります。 このチュートリアルでは、SharePoint リストのデータを Power BI レポートに変換する方法について説明します。

この 5 分間のチュートリアル ビデオをご覧になるか、下にスクロールして詳細な手順を確認してください。

<iframe width="400" height="450" src="https://www.youtube.com/embed/OZO3x2NF8Ak" frameborder="0" allowfullscreen></iframe>

## <a name="part-1-connect-to-your-sharepoint-list"></a>パート 1:ご利用の SharePoint リストに接続する

1. それをまだお持ちでない場合は、[Power BI Desktop](https://powerbi.microsoft.com/desktop/) をダウンロードしてインストールします。
2. Power BI Desktop を開き、リボンの [ホーム] タブで **[データの取得]**  >  **[その他]** の順に選択します。
3. **[Online Services]** を選択してから、 **[SharePoint Online リスト]** を選択します。  

    <img src="media/desktop-sharepoint-online-list/desktop-sharepoint-online-list-getdata.png" alt="Screenshot shows the Get Data dialog box with Online Services selected." width="350"/>

4. **[接続]** を選択します。
4. ご利用のリストを含む SharePoint Online サイトのアドレス (URL とも呼ばれる) を見つけます。  SharePoint Online のページから、サイトのアドレスを取得するには、通常、ナビゲーション ウィンドウ内の **[ホーム]** を選択するか、または上部にあるサイトのアイコンを選択して、ご利用の Web ブラウザーのアドレス バーからアドレスをコピーします。

   この手順のビデオをご覧ください。
   <iframe width="400" height="300" src="https://www.youtube.com/embed/OZO3x2NF8Ak?start=48&end=90" frameborder="0" allowfullscreen></iframe>

5. Power BI Desktop で、[開く] ダイアログ ボックス内の **[サイト URL]** フィールドにアドレスを貼り付けます。

6. 次の画像のような SharePoint アクセス画面が表示される場合もあれば表示されない場合もあります。  表示されない場合は、手順 10 に進みます。  表示される場合は、ページの左側にある **[Microsoft アカウント]** を選択します。

    <img src="media/desktop-sharepoint-online-list/desktop-sharepoint-online-list-auth1.png" alt="choose Microsoft account" width="500"/>

7. **[サインイン]** を選択し、Microsoft 365 へのサインインに使用するユーザー名とパスワードを入力します。

    <img src="media/desktop-sharepoint-online-list/desktop-sharepoint-online-list-auth2.png" alt="sign in" width="500"/>

8. サインインが完了したら、 **[接続]** を選択します。

9. ナビゲーターの左側で、接続先の SharePoint リストの横にあるチェックボックスを選択します。

    <img src="media/desktop-sharepoint-online-list/desktop-sharepoint-online-list-select-list.png" alt="Screenshot shows the Navigator page with BudgetRequests selected." width="450"/>

10. **[読み込み]** を選択します。  Power BI によって、ご利用のリスト データが新しいレポートに読み込まれます。

## <a name="part-2-create-a-report"></a>パート 2:レポートの作成

1. 左側で、 **[データ]** アイコンを選択して、SharePoint リストのデータが読み込まれたことを確認します。

2. 数値が含まれているリスト列に、右側の **[フィールド] ペイン** にある [合計] または [シグマ] アイコンが表示されていることを確認します。  そうでない場合は、テーブル ビューで列ヘッダーを選択し、 **[モデリング]** タブを選択してから、データに応じて **[データ型]** を **[10 進数]** または **[整数]** に変更します。  自分の変更の確認を求めるメッセージが表示されたら、 **[はい]** を選択します。  使用する数値が通貨などの特殊な形式である場合は、 **[形式]** を設定して選択することもできます。

   この手順のビデオをご覧ください。
   <iframe width="400" height="300" src="https://www.youtube.com/embed/OZO3x2NF8Ak?start=147&end=204" frameborder="0" allowfullscreen></iframe>

3. 左側で、 **[レポート]** アイコンを選択します。
4. 視覚化する列を選択するために、右側の **[フィールド]** ペインで、それらの列の横にあるチェックボックスをオンにします。

   この手順のビデオをご覧ください。
   <iframe width="400" height="300" src="https://www.youtube.com/embed/OZO3x2NF8Ak?start=215&end=252" frameborder="0" allowfullscreen></iframe>

5. 必要に応じて、ビジュアルの種類を変更します。
6. 同じレポートに複数の視覚エフェクトを作成することができます。それには、既存のビジュアルを選択解除してから、 **[フィールド]** ペインで他の列のチェックボックスをオンにします。
7. **[保存]** を選択してレポートを保存します。
