---
title: Power BI Q&A を使用してビジュアルを探索および作成する
description: Power BI Q&A を使ってダッシュボードとレポートに新しい視覚化を作成する方法。
author: maggiesMSFT
ms.author: maggies
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 05/13/2019
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 01ab8e63785680ea4fcd30cee170297f1cf1d674
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96396132"
---
# <a name="use-power-bi-qa-to-explore-your-data-and-create-visuals"></a>Power BI Q&A を使用してデータを探索しビジュアルを作成する

自然言語を使用して質問するのが、データから回答を得る最も速い方法である場合があります。 Power BI の Q&A 機能では、自分の言葉でご利用のデータを探索することができます。  この記事の最初の部分では、Power BI サービスのダッシュボードで Q&A を使用する方法について説明します。 2 番目の部分は、Power BI サービスまたは Power BI Desktop でレポートを作成するときに Q&A でできることを示しています。 背景情報については、[コンシューマー向けの Q&A](../consumer/end-user-q-and-a.md) に関する記事を参照してください。 

[Power BI モバイル アプリの Q&A](../consumer/mobile/mobile-apps-ios-qna.md) および [Power BI Embedded の Q&A ](../developer/embedded/qanda.md) については、別の記事で説明します。 

Q&A は対話型で、楽しく行えます。 視覚化によってさらに調べるべき点が見つかるため、多くの場合は 1 つの質問が他の質問につながります。 Q&A を使って視覚エフェクトを作成し、それを詳しく調べて、ダッシュボードに表示する、Amanda のデモンストレーションをご覧ください。

<iframe width="560" height="315" src="https://www.youtube.com/embed/qMf7OLJfCz8?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="part-1-use-qa-on-a-dashboard-in-the-power-bi-service"></a>パート 1:Power BI サービスのダッシュボードで Q&A を使用する

Power BI サービス (app.powerbi.com) のダッシュボードには 1 つ以上のデータセットからピン留めされたタイルが含まれているので、いずれかのデータセットに含まれるいずれかのデータに関して質問することができます。 ダッシュボードの作成に使われたレポートとデータセットを見るには、メニュー バーの **[関連の表示]** を選択します。

![関連するレポートおよびデータセットを表示する](media/power-bi-tutorial-q-and-a/power-bi-view-related.png)

ダッシュボードの左上隅には Q&A 質問ボックスがあり、ここに自然言語を使って質問を入力します。 Q&A ボックスが表示されませんか。 **コンシューマー向けの Q&A** に関する記事の「[考慮事項とトラブルシューティング](../consumer/end-user-q-and-a.md#considerations-and-troubleshooting)」を参照してください。  Q&A は、入力した用語を認識して、回答を探す場所 (データセット) を見つけ出します。 さらに、オートコンプリート、書き換え、その他のテキストや視覚による支援を使用して質問の作成を助けます。

![「データについて質問する」というオプションが表示されている Power B I ダッシュボードのスクリーンショット。](media/power-bi-tutorial-q-and-a/powerbi-qna.png)

質問を変更すると、質問に対する回答は、対話型の視覚化と更新として表示されます。

1. ダッシュボードを開き、質問ボックスにカーソルを置きます。 右上隅の **[New Q&A experience]\(新しい Q&A エクスペリエンス\)** を選択します。

    ![Power BI の新しい Q&A エクスペリエンス](media/power-bi-tutorial-q-and-a/power-bi-qna-new-experience.png)

1. 入力を開始する前に、Q & A で質問を作るときに役立つ情報が新しい画面に表示されます。 基になっているデータセットのテーブルの名前を含む語句と完全な質問が表示され、データセットの所有者が[お勧めの質問](service-q-and-a-create-featured-questions.md)を作成している場合は完全な質問が一覧表示されることもあります。

   ![Q&A によって提案された質問](media/power-bi-tutorial-q-and-a/power-bi-qna-suggested-questions.png)

   開始点としてこれらの質問のいずれかを選び、質問を繰り返し絞り込んで、特定の回答を見つけることができます。 あるいは、テーブル名を使用して、新しい質問を言葉で表すことができます。

2. 質問の一覧から選ぶか、独自の質問を少し入力してドロップダウンから候補を選びます。

   ![一覧から質問を選択する](media/power-bi-tutorial-q-and-a/power-bi-qna-select-a-question-how-many-stores.png)

3. 質問を入力すると、Q&A は回答を表示するために最適な視覚化を選択します。

   ![Q&A。州別の店舗数](media/power-bi-tutorial-q-and-a/power-bi-qna-how-many-stores-by-state.png)

4. 質問を変更すると、視覚化は動的に変更されます。

   ![Q&A。横棒グラフで表された州別の店舗数](media/power-bi-tutorial-q-and-a/power-bi-qna-stores-by-state-bar-chart.png)

1. 質問を入力すると、Power BI によりダッシュボードにタイルがあるデータセットを使って最善の回答が検索されます。  すべてのタイルが *datasetA* のものである場合、回答は *datasetA* から取得されます。  タイルが *datasetA* と *datasetB* のものである場合、Q&A はそれら 2 つのデータセットで最適な回答を検索します。

   > [!TIP]
   > そのため *datasetA* からのタイルが 1 つしかない場合は、それをダッシュボードから削除すると、Q&A が *datasetA* にアクセスできなくなるのでご注意ください。
   >

5. 結果に満足したら、右上隅にあるピンのアイコンを選んで、ダッシュボードに視覚化をピン留めします。 他のユーザーから共有を受けているダッシュボード、またはアプリの一部であるダッシュボードの場合は、ピン留めできません。

   ![Q&A。ビジュアルをピン留めする](media/power-bi-tutorial-q-and-a/power-bi-qna-pin-visual.png)

## <a name="part-2-use-qa-in-a-report-in-power-bi-service-or-power-bi-desktop"></a>パート 2:Power BI サービスおよび Power BI Desktop のレポートで Q&A を使う

Q&A を使ってデータセットを探索し、レポートとダッシュボードに視覚エフェクトを追加します。 レポートは単一のデータセットに基づいており、完全に空白にすることも、ページいっぱいに視覚エフェクトを表示することもできます。 ただし、レポートが空白でも探索するデータが何もないということではありません。データセットはレポートにリンクされており、ユーザーが探索を行って視覚エフェクトを作成するのを待っているのです。  レポートの作成に使われているデータセットを確認するには、Power BI サービスの読み取りビューでレポートを開き、メニュー バーから **[関連の表示]** を選びます。

![関連データセットを表示する](media/power-bi-tutorial-q-and-a/power-bi-view-related.png)

レポートで Q&A を使うには、レポートと基になっているデータセットの編集アクセス許可が必要です。 [コンシューマー向けの Q&A](../consumer/end-user-q-and-a.md) に関する記事では、これを "*作成者*" のシナリオと呼んでいます。 代わりに、自分と共有されているレポートを "*利用*" している場合は、Q&A を使うことはできません。

1. 編集ビュー (Power BI サービス) またはレポート ビュー (Power BI Desktop) でレポートを開き、メニュー バーの **[質問する]** を選びます。

    **Power BI Desktop**    
    ![Power BI Desktop で [質問する] を選択する](media/power-bi-tutorial-q-and-a/power-bi-desktop-question.png)

    **サービス**    
    ![Power BI サービスで [質問する] を選択する](media/power-bi-tutorial-q-and-a/power-bi-service.png)

2. Q&A 質問ボックスがレポート キャンバスに表示されます。 次の例では、別の視覚エフェクトの上に質問ボックスが表示されています。 これでも問題はありませんが、質問する前にレポートに空のページを追加した方がよい場合があります。

    ![視覚エフェクト上に質問ボックスを表示するキャンバスのスクリーンショット。](media/power-bi-tutorial-q-and-a/power-bi-ask-question.png)

3. 質問ボックスにカーソルを置きます。 入力を進めるにつれて、質問の作成に役立つ候補が表示されます。

   ![Q&A 質問ボックスに入力する](media/power-bi-tutorial-q-and-a/power-bi-q-and-a-suggestions.png)

4. 質問を入力していくと、Q&A は回答の表示に最適な[視覚エフェクト](../visuals/power-bi-visualization-types-for-reports-and-q-and-a.md)を選び、質問を変更するにつれ視覚エフェクトが動的に変化します。

   ![Q&A によって視覚化が作成される](media/power-bi-tutorial-q-and-a/power-bi-q-and-a-visual.png)

5. 好みの視覚エフェクトが表示されたら、Enter キーを押します。 視覚エフェクトをレポートと共に保存するには、 **[ファイル] > [保存]** を選びます。

6. 新しい視覚エフェクトを操作します。 視覚エフェクトをどのようにして作成したかは関係ありません。どの場合でも同じ操作、書式設定、機能を利用できます。

   ![視覚化を操作する](media/power-bi-tutorial-q-and-a/power-bi-q-and-a-ellipses.png)

   Power BI サービスで視覚エフェクトを作成した場合は、[視覚エフェクトをダッシュボードにピン留めする](service-dashboard-pin-tile-from-q-and-a.md)こともできます。

## <a name="tell-qa-which-visualization-to-use"></a>使用する視覚化を Q&A で指定する
Q&A では、データ自身に語らせるだけでなく、Power BI に回答の表示方法を指示することもできます。 質問の最後に "as a <visualization type>" を追加して、視覚化の種類を指定するだけです。  たとえば、「show inventory volume by plant as a map」(工場ごとの在庫量をマップとして表示する)、「show total inventory as a card」(在庫合計をカードとして表示する) などです。  自分で試してみてください。

## <a name="considerations-and-troubleshooting"></a>考慮事項とトラブルシューティング
- ライブ接続またはゲートウェイを使ってデータセットに接続した場合は、Q&A を[そのデータセットで有効にする](service-q-and-a-direct-query.md)必要があります。

- レポートを開いていた場合、Q&A のオプションは表示されません。 Power BI サービスを使っている場合は、編集ビューでレポートを開いていることを確認します。 編集ビューを開くことができない場合は、そのレポートの編集アクセス許可がなく、その特定のレポートで Q&A を使用できることを意味します。

## <a name="next-steps"></a>次の手順

- [コンシューマー向けの Q&A](../consumer/end-user-q-and-a.md)   
- [Q&A で質問するためのヒント](../consumer/end-user-q-and-a-tips.md)   
- [Q&A のためのブックの準備](service-prepare-data-for-q-and-a.md)  
- [Q&A 用にオンプレミスのデータセットを準備する](service-q-and-a-direct-query.md)   
- [Q&A からダッシュボードにタイルをピン留めする](service-dashboard-pin-tile-from-q-and-a.md)
