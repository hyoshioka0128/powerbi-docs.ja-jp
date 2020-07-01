---
title: ダッシュボードとは何ですか? それはどのように開きますか?
description: ダッシュボードは、Power BI サービスの主要な機能です。
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 06/19/2020
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 64fa13f3e95f43813c657eb9be195fb03e57a06b
ms.sourcegitcommit: caf60154a092f88617eb177bc34fb784f2365962
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2020
ms.locfileid: "85354917"
---
# <a name="dashboards-for-power-bi-service-consumers"></a>Power BI サービスの利用者向けのダッシュボード

[!INCLUDE[consumer-appliesto-ynny](../includes/consumer-appliesto-ynny.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Power BI の "***ダッシュボード***" は、視覚化を使ってストーリーを伝える単一のページであり、キャンバスと呼ばれることもよくあります。 ダッシュボードは 1 ページに制限されているため、適切に設計されたダッシュボードには、そのストーリーの最も重要な要素のみが含まれます。

![ダッシュボード](media/end-user-dashboards/power-bi-dashboard2.png)

ダッシュボードに表示される視覚エフェクトは*タイル*と呼ばれ、レポート *デザイナー*によってダッシュボードに*ピン留め*されています。 通常、タイルを選択すると、その視覚エフェクトが作成されたレポート ページに移動します。 Power BI を初めて使うときは、[Power BI の基本的な概念](end-user-basic-concepts.md)に関するページを読むと基礎がよくわかります。

> [!NOTE]
> ダッシュボードは、[モバイル デバイス上で表示および共有する](mobile/mobile-apps-view-dashboard.md)ことができます。
>
> 自分と共有されているダッシュボードを表示するためには、Power BI Pro が必要です。

ダッシュボード上の視覚化はレポートから取得され、各レポートは 1 つのデータセットが基になっています。 実際、ダッシュボードは基になっているレポートとデータセットへの入り口と考えることもできます。 視覚化を選ぶと、その作成に使われたレポート (およびデータセット) に行き着きます。

![ダッシュボード、レポート、データセット間の関係を示す図](media/end-user-dashboards/power-bi-diagram.png)

## <a name="advantages-of-dashboards"></a>ダッシュボードの利点
ダッシュボードは、ビジネスを注視し、答えを探し、すべての最も重要なメトリックを一目で見るための、素晴らしい手段です。 ダッシュボード上の視覚化は、1 つまたは複数の基になっているデータセット、および 1 つまたは複数の基になっているレポートから取得できます。 ダッシュボードでは、オンプレミスとクラウドのデータが結合され、データの保存場所に関わらず統合されたビューを利用できます。

ダッシュボードは単なる美しい画像ではありません。対話機能を備え、基になっているデータが変化するとタイルが更新されます。

## <a name="dashboards-versus-reports-for-power-bi-consumers"></a>Power BI "***コンシューマー***" 向けのダッシュボードとレポート
レポートも視覚化が表示されたキャンバスであるため、ダッシュボードと混同されることがよくあります。 しかし、Power BI "*コンシューマー*" の観点からは大きな違いがいくつかあります。

| **機能** | **ダッシュボード** | **レポート** |
| --- | --- | --- |
| ページ |1 ページ |1 ページ以上 |
| [データ ソース] |ダッシュボードごとに、1 つ以上のレポートおよび 1 つ以上のデータセット |レポートごとに 1 つのデータセット |
| フィルター処理 |フィルター処理またはスライスはできません |さまざまな方法でフィルター処理、強調表示、スライスできます |
| 通知の設定 |特定の条件が満たされたときにユーザーにメールを送る通知を作成できます |いいえ |
| おすすめ |1 つのダッシュボードを "おすすめの" ダッシュボードとして設定できます |おすすめのレポートを作成することはできません |
| 基になっているデータセットのテーブルとフィールドの表示 |できません。 データをエクスポートすることはできますが、ダッシュボード自体でテーブルとフィールドを表示することはできません。 |はい。 データセットのテーブル、フィールド、値を表示することができます。 |


## <a name="dashboard-designers-and-dashboard-consumers"></a>ダッシュボードのデザイナーとダッシュボードのコンシューマー
Power BI の "***コンシューマー***" は、"*デザイナー*" からダッシュボードを受け取ります。 次のトピックについて、ダッシュボードに関する学習を続けてください。

* [ダッシュボードの表示](end-user-dashboard-open.md)
* [ダッシュボードのタイル](end-user-tiles.md)およびタイルを選んだときの結果について学習します。
* ダッシュボードの個々のタイルを追跡し、特定のしきい値に達したときにメールを受け取りたい場合は、 [タイルに通知を作成](end-user-alerts.md)します。
* ダッシュボードに質問したい場合は、 [Power BI Q&A](end-user-q-and-a.md) を使ってデータについて質問し、視覚化の形式で回答を受け取る方法を学習します。

> [!TIP]
> 知りたいことがここで見つからない場合は、左側の目次で探してください。
> 

## <a name="next-steps"></a>次のステップ
[ダッシュボードの表示](end-user-dashboard-open.md) 