---
title: Power BI レポートのフィルター処理と共有
description: Power BI レポートをフィルター処理し、組織内の同僚と共有する方法を説明します。
author: maggiesMSFT
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/29/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 16041ebc9ba293ab166178e008b12277d94e89c3
ms.sourcegitcommit: 64a270362c60581a385af7fbc31394e3ebcaca41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "76894925"
---
# <a name="filter-and-share-a-power-bi-report"></a>Power BI レポートのフィルター処理と共有
"*共有*" は、自分のダッシュボードおよびレポートに他のユーザーがアクセスできるようにするのによい方法です。 フィルター処理されたバージョンのレポートを共有したい場合は、どうすればよいでしょうか。 特定の都市または営業担当者または年のデータのみをレポートに表示したい場合があります。 この記事では、レポートをフィルター処理し、フィルター処理されたバージョンのレポートを共有する方法について説明します。 フィルター処理されたレポートを共有するには、[レポートの URL にクエリ パラメーターを追加する](service-url-filters.md)方法もあります。 いずれの場合でも、受信者が最初にレポートを開くときにレポートがフィルター処理されます。 レポートのフィルター選択は、クリアすることができます。

![フィルター処理されたレポート](media/service-share-reports/power-bi-share-filter-pane-report.png)

Power BI では、[レポートの共同作業や配布を行う他の方法](service-how-to-collaborate-distribute-dashboards-reports.md)も用意されています。 共有する際、共有元と共有先の双方に [Power BI Pro ライセンス](service-features-license-type.md)が必要です。または、コンテンツを [Premium 容量](service-premium-what-is.md)に格納する必要があります。 

## <a name="follow-along-with-sample-data"></a>サンプル データに沿ってフォローする

この記事では、マーケティングと売上のサンプル テンプレート アプリを使用します。 試してみたいですか。 

1. [マーケティングと売上サンプル テンプレート アプリ](https://appsource.microsoft.com/product/power-bi/microsoft-retail-analysis-sample.salesandmarketingsample?tab=Overview)をインストールします。
2. アプリを選択し、 **[アプリを探索]** を選択します。

   ![サンプル データを探索する](media/service-share-reports/power-bi-sample-explore-data.png)

3. 鉛筆アイコンを選択して、アプリと共にインストールしたワークスペースを開きます。

    ![アプリの編集の鉛筆](media/service-share-reports/power-bi-edit-pencil-app.png)

4. ワークスペースのコンテンツ一覧で **[レポート]** を選択し、**売上およびマーケティングのサンプル PBIX** のレポートを選択します。

    ![サンプル レポートを開く](media/service-share-reports/power-bi-open-sample-report.png)

    これで、先に進むことができます。

## <a name="set-a-filter-in-the-report"></a>レポートにフィルターを設定する

[編集ビュー](consumer/end-user-reading-view.md)でレポートを開き、フィルターを適用します。

この例では、マーケティングと売上サンプル テンプレート アプリの YTD Category ページをフィルター処理して、**Region** が **Central** と等しい値のみを表示しています。 
 
![[レポート フィルター] ウィンドウ](media/service-share-reports/power-bi-share-report-filter.png)

レポートを保存します。

## <a name="share-the-filtered-report"></a>フィルター処理されたレポートを共有する

1. **[共有]** を選択します。

   ![[共有] を選択します。](media/service-share-reports/power-bi-share.png)

2. **[受信者に電子メールの通知を送信する]** をオフにして、代わりにフィルター処理されたリンクを送信できるようにします。また、 **[現在のフィルターとスライサーでレポートを共有する]** を選択し、 **[共有]** を選択します。

    ![フィルターを使用してレポートを共有する](media/service-share-reports/power-bi-share-with-filters.png)

4. **[共有]** をもう一度選択します。

   ![[共有] を選択します。](media/service-share-reports/power-bi-share.png)

5. **[アクセス]** タブを選択し、 **[共有レポート ビューの管理]** を選択します。

    ![共有レポート ビューの管理](media/service-share-reports/power-bi-manage-shared-report-views.png)

6. 目的の URL を右クリックし、 **[リンクのコピー]** を選択します。

    ![フィルター処理されたリンクのコピー](media/service-share-reports/power-bi-copy-filtered-link.png)

7. このリンクを共有すると、受信者にはフィルター処理されたレポートが表示されます。 


## <a name="next-steps"></a>次の手順
* [Power BI で作業を共有する方法](service-how-to-collaborate-distribute-dashboards-reports.md)
* [ダッシュボードの共有](service-share-dashboards.md)
* 他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。
* ご意見およびご提案がある場合は、 [Power BI コミュニティ サイト](https://community.powerbi.com/)をご利用ください。

