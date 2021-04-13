---
title: ダッシュボードとレポートにコメントを追加する
description: このドキュメントでは、ダッシュボード、レポート、またはビジュアルにコメントを追加する方法と、コメントを使用して共同作業者と会話する方法を示します。
author: mihart
ms.author: mihart
ms.reviewer: mihart
featuredvideoid: ''
ms.service: powerbi
ms.subservice: pbi-explore
ms.topic: how-to
ms.date: 01/08/2021
LocalizationGroup: Consumer
ms.openlocfilehash: dd680e107be3dea803620ff81e9ecc8b67e1cced
ms.sourcegitcommit: 10dfa074558a78a82f44bdfa6228c07c7d860257
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/07/2021
ms.locfileid: "106549611"
---
# <a name="add-comments-to-a-dashboard-or-report"></a>ダッシュボードまたはレポートにコメントを追加する

[!INCLUDE[consumer-appliesto-ynny](../includes/consumer-appliesto-ynny.md)]

個人のコメントを追加するか、同僚とダッシュボードまたはレポートに関する会話を開始します。 **コメント** 機能は、"*ビジネス ユーザー*" が他のユーザーと共同作業するための方法の 1 つにすぎません。 

![コメントのビデオ](media/end-user-comment/comment.gif)

> [!NOTE]
> 共有レポートにコメントを追加するなど、他のユーザーと共同作業するには、Power BI Pro ライセンスを使用するか、Power BI Premium 容量でコンテンツをホストする必要があります。 [私のライセンスの種類は何ですか?](end-user-license.md)

## <a name="how-to-use-the-comments-feature"></a>コメント機能を使用する方法
コメントは、ダッシュボード全体、ダッシュボード上の個々のビジュアル、レポート ページ、ページ分割されたレポート、レポート ページ上の個々のビジュアルに追加することができます。 一般的なコメントを追加するか、特定の同僚に宛てたコメントを追加します。 コメントには、他のユーザーの @mentions とスペースを含め、最大 500 文字を指定できます。

レポートにコメントを追加すると、Power BI によって現在のフィルターとスライサーの値がキャプチャされ、[ブックマーク](end-user-bookmarks.md)が作成されます。 つまり、コメントを選択またはコメントに応答すると、レポート ページまたはレポートのビジュアルが変更されて、コメントが最初に追加されたときにアクティブだったフィルターとスライサーの選択が表示される場合があります。  

![フィルター付きレポートのビデオ](media/end-user-comment/power-bi-comment.gif)

これが重要である理由 たとえば、同僚が、チームと共有したい興味深い分析情報を示すフィルターを適用したとします。 そのフィルターが選択されていないと、コメントに意味がない場合があります。

ページ分割されたレポートを使用している場合、レポートに関する一般的なコメントのみを残しておくことができます。  ページ番号が付けられた個々のレポート ビジュアルにコメントを残すことはできません。

### <a name="add-a-general-comment-to-a-dashboard-or-report"></a>ダッシュボードまたはレポートに一般的なコメントを追加する
ダッシュボードまたはレポートにコメントを追加するプロセスは似ています。  この例では、ダッシュボードを使用しています。 

1. Power BI ダッシュボードまたはレポートを開き、 **[コメント]** アイコンを選択します。 これによって [コメント] ダイアログが開きます。

    ![メニュー バーの [コメント] アイコン](media/end-user-comment/power-bi-comment-icon.png)

    ここでは、ダッシュ ボードの作成者が既に一般的なコメントを追加しています。  このコメントは、このダッシュボードにアクセスできるすべてのユーザーが参照できます。

    ![[コメント] セクションが選択されているダッシュボードのスクリーンショット](media/end-user-comment/power-bi-first-comments.png)

2. 返信するには、 **[返信]** を選択し、返信を入力し、 **[投稿]** を選択します。  

    ![返信画面を選択します](media/end-user-comment/power-bi-comments-reply.png)

    Power BI では、既定で、コメントのスレッドを開始した同僚に返信が送られます。この場合は、Aaron です。 

    ![返信付きのコメント](media/end-user-comment/power-bi-respond.png)

 3. 既存のスレッドの一部ではないコメントを追加する場合は、コメントを上部のテキスト フィールドに入力します。

    ![新しいスレッドを示すスクリーンショット](media/end-user-comment/power-bi-new-commenting.png)

    このダッシュボードに対するコメントは、次のように表示されます。

    ![コメントの会話](media/end-user-comment/power-bi-conversation.png)

### <a name="add-a-comment-to-a-specific-dashboard-or-report-visual"></a>特定のダッシュボードまたはレポートのビジュアルにコメントを追加する
ダッシュボード全体またはレポート ページ全体にコメントを追加するだけでなく、個々のダッシュボード タイルと個々のレポート ビジュアルにコメントを追加することができます。 これらのプロセスは似ています。この例では、レポートを使用しています。

1. ビジュアルの上にカーソルを置き、 **[その他のアクション]** (...) を選択します。    
2. ドロップダウンから、**[コメントの追加]** を選択します。

    ![[コメントの追加] が最初の選択肢](media/end-user-comment/power-bi-comment-reports.png)  

3.  **[コメント]** ダイアログが開き、ページの他のビジュアルがグレーで表示されます。このビジュアルには、まだコメントがありません。 

    ![ビジュアルが選択され、[コメント] ダイアログが開いているスクリーンショット](media/end-user-comment/power-bi-comments-column.png)  

4. コメントを入力し、 **[投稿]** を選択します。

    ![新しいメッセージが表示されている [コメント] ダイアログ](media/end-user-comment/power-bi-comment-spikes.png)  

    - レポート ページで、ビジュアルに対して作成されたコメントを選択すると、そのビジュアルが強調表示されます (以下を参照)。

    - ダッシュボードでは、グラフ アイコン ![[グラフ] アイコン付きのコメント](media/end-user-comment/power-bi-comment-chart-icon.png) で、コメントが特定のビジュアルに関連付けられていることがわかります。 ダッシュボード全体に適用されるコメントには、特別なアイコンがありません。 グラフ アイコンを選択すると、ダッシュボード上の関連するビジュアルが強調表示されます。
    

    ![強調表示された関連ビジュアル](media/end-user-comment/power-bi-highlights.png)

5. **[閉じる]** を選択して、ダッシュボードまたはレポートに戻ります。

### <a name="get-your-colleagues-attention-by-using-the--sign"></a>@ 記号を使用して同僚の注目を得る
ダッシュボード、レポート、タイル、ビジュアル コメントのいずれを作成する場合でも、"\@" 記号を使用して同僚の注目を集めることができます。  "\@" 記号を入力すると、Power BI では、組織のユーザーを検索および選択できるドロップダウンが開かれます。 "\@" 記号が前につく検証済みのすべての名前は、青のフォントで表示されます。 @mentioned された個人は、受信トレイにすぐに電子メールが届きます。Power BI Mobile アプリを使用している場合は、デバイスでプッシュ通知を受信します。 通知から直接レポートまたはダッシュボードを開いたり、コメントを表示したり、データを表示したり、それに応じて応答したりすることができます。

これは、視覚エフェクトの *デザイナー* と行っている会話です。 @ 記号を使用して、確実にコメントを見ることができるようにしています。 通知を受け取り、このダッシュボードと関連する会話を開くためのリンクを選択します。  

![コメントのメンションを追加する](media/end-user-comment/power-bi-comment-conversation.png)  

## <a name="considerations-and-troubleshooting"></a>考慮事項とトラブルシューティング

- コメントには、他のユーザーの @mentions とスペースを含め、500 文字までに制限されています。
- 会話に返信しても、ブックマークはキャプチャされません。 会話の最初のコメントのみがブックマークを作成します。
- ページ分割されたレポートを使用している場合、レポートに関する一般的なコメントのみを残しておくことができます。  ページ番号が付けられた個々のレポート ビジュアルにコメントを残すことはできません。

## <a name="next-steps"></a>次の手順
[ビジネス ユーザー向けの視覚エフェクト](end-user-visualizations.md)  に戻る  
[視覚化を選択してレポートを開く](end-user-report-open.md)
