---
title: Apple Watch のモバイル アプリで Power BI のデータを探索する
description: Power BI Apple Watch アプリ
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 03/11/2020
ms.openlocfilehash: 1a2dfd19f2366003555aa5fa673bbf1c81c0a050
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96413267"
---
# <a name="explore-your-data-in-the-power-bi-mobile-app-on-your-apple-watch"></a>Apple Watch の Power BI モバイル アプリでデータを探索する
Power BI Apple Watch アプリを使用すると、ウォッチ上で Power BI ダッシュボードから KPI とカード タイルを表示できます。 KPI とカード タイルは、小さな画面でハートビートを測定するのに最適です。 iPhone から、または Watch 自体から、ダッシュボードを更新できます。

## <a name="install-the-apple-watch-app"></a>Apple Watch アプリのインストール
Power BI Apple Watch アプリは Power BI for iOS アプリにバンドルされているため、Apple App Store から [iPhone にこの Power BI アプリをダウンロード](https://go.microsoft.com/fwlink/?LinkId=522062 "iPhone アプリのダウンロード")すると、自動的に Power BI Watch アプリもダウンロードされます。 Apple のガイドでは、[Apple Watch アプリケーションをインストールする](https://support.apple.com/HT204784)方法を説明しています。

## <a name="use-the-power-bi-app-on-the-apple-watch"></a>Apple Watch での Power BI アプリの使用
Power BI Apple Watch アプリケーションに移動するには、ウォッチのスプリングボードから、または直接ウォッチの文字盤で Power BI ウィジェット (構成されている場合) をクリックします。

![写真は、Apple Watch の Power BI アプリを示しています。](./media/mobile-apple-watch/pbi_aplwatch_complicatn240arrow.png)

Power BI Apple Watch アプリは、2 つの部分で構成されます。

* **インデックス画面** には、すべての KPI とカード タイルの概要を同期済みのダッシュボードからすばやく表示できます。
  
  ![写真は、Apple Watch でのインデックス画面を示しています。](./media/mobile-apple-watch/pbi_aplwatch_indexscreen240.png)
* **フォーカスが置かれているタイル**: インデックス画面のタイルをクリックすると、特定のタイルの詳細なビューが表示されます。
  
  ![写真は、Apple Watch でタイルを表示した様子を示しています。](./media/mobile-apple-watch/pbi_aplwatch_kpi.png)

## <a name="refresh-a-dashboard-from-your-apple-watch"></a>Apple Watch からダッシュ ボードを更新する
同期されたダッシュ ボードを Watch から直接更新できます。

* Watch アプリのダッシュボード ビューで、画面を強めに押し、 **[更新]** を選びます。

Watch アプリによって、ダッシュボードが Power BI サービスからのデータと同期されます。

> [!NOTE]
> Watch アプリは、iPhone 上の Power BI モバイル アプリを使って Power BI と通信します。 そのため、Watch アプリのダッシュボードが更新するためには、iPhone 上で、Power BI アプリが少なくともバックグラウンドで実行している必要があります。
> 
> 

## <a name="refresh-a-dashboard-on-your-apple-watch-from-your-iphone"></a>iPhone から Apple Watch 上のダッシュ ボードを更新する
Apple Watch 上のダッシュ ボードを iPhone から更新することもできます。

1. iPhone の Power BI で、Apple Watch と同期するダッシュボードを開きます。 
2. **その他のオプション** (...) を選択し、 **[Watch との同期]** を選択します。

Power BI では、ダッシュボードがウォッチと同期していることを示すインジケーターが表示されます。

一度にウォッチと同期できるダッシュボードは 1 つだけです。

> [!TIP]
> ウォッチで複数のダッシュボードからタイルを表示するには、Power BI サービスに新しいダッシュボードを作成し、それに関連するすべてのタイルをピン留めします。
> 
> 

## <a name="set-a-custom-power-bi-widget"></a>カスタムの Power BI ウィジェットの設定
Power BI タイルは、Apple Watch の文字盤で指定して直接表示することもできるため、いつでも見たり、アクセスしたりすることができます。

Power BI Apple Watch ウィジェットは、データの更新時刻に近い時刻に更新されるため、必要な情報が常に最新の状態に保たれます。

### <a name="add-a-power-bi-widget-to-your-watch-face"></a>ウォッチの文字盤への Power BI ウィジェットの追加
Apple のガイドの「[Apple Watch の文字盤をカスタマイズする](https://support.apple.com/HT205536)」をご覧ください。

### <a name="change-the-text-on-the-widget"></a>ウィジェットのテキストの変更
Apple Watch の文字盤のスペースは小さいため、Power BI Apple Watch アプリでは、小さなスペースに収まるようウィジェットのタイトルを変更できます。

* iPhone で、Apple Watch コントロール アプリに移動して、Power BI を選択します。ウィジェットの名前のフィールドに移動して、新しい名前を入力します。
  
  ![写真は、iPhone で My Watch アプリが開かれ、Power BI アイコンが表示されている様子を示しています。](./media/mobile-apple-watch/pbi_aplwatch_oniphone.png)

> [!NOTE]
> 名前を変更しなかった場合には、Power BI ウィジェットの名前の文字数がウォッチの文字盤の小さなスペースに収まるよう短くなります。 
> 
> 

## <a name="next-steps"></a>次のステップ
Power BI モバイル アプリで使用したいその他の機能にぜひ投票してください。お客様からのフィードバックは、将来実装する機能を決めるのに役立ちます。 

* [Power BI iPhone モバイル アプリ](https://go.microsoft.com/fwlink/?LinkId=522062)をダウンロードする
* Twitter で [@MSPowerBI をフォローする](https://twitter.com/MSPowerBI)
* [Power BI コミュニティの会話](https://community.powerbi.com/)に参加する

