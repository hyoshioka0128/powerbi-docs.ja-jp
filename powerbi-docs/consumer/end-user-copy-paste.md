---
title: Power BI サービスでの視覚化のコピーと貼り付け
description: Power BI サービスでの視覚化のコピーと貼り付け
author: mihart
ms.author: mihart
ms.reviewer: maggie.tsang
ms.service: powerbi
ms.subservice: pbi-explore
ms.topic: how-to
ms.date: 08/25/2020
LocalizationGroup: Visualizations
ms.openlocfilehash: a0ac7760b766681a70aae3662059256ecffbf07f
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96400640"
---
# <a name="copy-a-visual-as-an-image-to-your-clipboard"></a>ビジュアルをイメージとしてクリップボードにコピーする

[!INCLUDE[consumer-appliesto-yyyn](../includes/consumer-appliesto-yyyn.md)]

Power BI レポートまたはダッシュボードからイメージを共有したいと思ったことはありませんか。 ビジュアルをコピーし、貼り付けがサポートされる他のアプリケーションに貼り付けられるようになりました。 

ビジュアルの静的なイメージをコピーするときに、メタデータと共にビジュアルのコピーを取得します。 これには、以下のことが含まれます。
* Power BI レポートまたはダッシュボードに戻るリンク
* レポートまたはダッシュボードのタイトル
* イメージに機密情報が含まれているかどうかの通知
* 最終更新タイム スタンプ
* ビジュアルに適用されるフィルター

### <a name="copy-from-a-dashboard-tile"></a>ダッシュボード タイルからコピーする

1. コピー元のダッシュボードに移動します。

2. ビジュアルの右上隅にある **[その他のアクション] (...)** を選択し、 **[視覚エフェクトをイメージとしてコピー]** を選択します。 

    ![ドロップダウン メニューに表示される画像オプションとして視覚エフェクトをコピーする](media/end-user-copy-paste/power-bi-copy-dashboard.png)

3. **[Your visual is ready to copy]\(ビジュアルをコピーする準備ができました\)** ダイアログが表示されたら、 **[クリップボードにコピー]** を選択します。

    ![[クリップボードにコピー] オプションを含むダイアログ](media//end-user-copy-paste/power-bi-copied.png)

4. 視覚エフェクトをコピーしたら、**Ctrl + V** キーを使用するか、**右クリック** >  **[貼り付け]** を選択して、別のアプリケーションに貼り付けます。 以下のスクリーンショットでは、ビジュアルが Microsoft Word に貼り付けられています。 

    ![Microsoft Word に貼り付けられた視覚エフェクト](media//end-user-copy-paste/power-bi-paste-word.png)

### <a name="copy-from-a-report-visual"></a>レポートのビジュアルからコピーする 

1. コピー元のレポートに移動します。

2. ビジュアルの右上隅にある **[視覚エフェクトをイメージとしてコピー]** のアイコンを選択します。 

    ![表示されている [視覚エフェクトをイメージとしてコピー] アイコン](media/end-user-copy-paste/power-bi-copy-icon.png)

3. **[Your visual is ready to copy]\(ビジュアルをコピーする準備ができました\)** ダイアログが表示されたら、 **[クリップボードにコピー]** を選択します。

    ![[クリップボードにコピー] オプションを含むダイアログ](media//end-user-copy-paste/power-bi-copied.png)


4. 視覚エフェクトをコピーしたら、**Ctrl + V** キーを使用するか、**右クリック** >  **[貼り付け]** を選択して、別のアプリケーションに貼り付けます。 次のスクリーンショットでは、ビジュアルがメールに貼り付けられています。

    ![Outlook に貼り付けられたビジュアル](media//end-user-copy-paste/power-bi-copy-email.png)

5. レポートにデータの機密ラベルが適用されている場合、コピー アイコンを選択すると警告が表示されます。  

    ![機微なデータの警告](media//end-user-copy-paste/power-bi-sensitive.png)

    また、貼り付けられたビジュアルの下のメタデータには、機密ラベルが追加されます。 

    ![機密情報ラベルを含むビジュアル](media//end-user-copy-paste/power-bi-confidential.png)



## <a name="considerations-and-troubleshooting"></a>考慮事項とトラブルシューティング

   ![コピーを使用できない](media//end-user-copy-paste/power-bi-copy-grey.png)


Q:ビジュアルでコピー アイコンが無効になっているのはなぜですか?    
A:現在、ネイティブ Power BI 視覚化と認定済みカスタム ビジュアルがサポートされています。 次のような特定のビジュアルのサポートは制限されています。 
- ESRI とその他のマップ視覚エフェクト 
- Python のビジュアル 
- R ビジュアル 
- PowerApps の視覚エフェクト   

A:ビジュアルをコピーする機能は、IT 部門または Power BI 管理者が無効にする可能性があります。


Q:ビジュアルが正しく貼り付けられないのはなぜですか?    
A:カスタム ビジュアルとアニメーション視覚化には制限があります。 



## <a name="next-steps"></a>次の手順
[Power BI レポートでの視覚化](end-user-visual-type.md)についての詳細を参照する

レポートの編集アクセス許可を持っている場合は、[同じレポート内で視覚エフェクトをコピーして貼り付けること](../visuals/power-bi-visualization-copy-paste.md)ができます。 

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。

