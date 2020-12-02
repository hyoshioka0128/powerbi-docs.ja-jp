---
title: Power BI サービスから Power BI Desktop にレポートをダウンロードする (プレビュー)
description: Power BI サービスから Power BI Desktop ファイルへのレポートのダウンロード
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 07/14/2020
LocalizationGroup: Reports
ms.openlocfilehash: c83b7d1e52a0d443c52348bec91f935e288830d4
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96388680"
---
# <a name="download-a-report-from-the-power-bi-service-to-power-bi-desktop-preview"></a>Power BI サービスから Power BI Desktop にレポートをダウンロードする (プレビュー)
      
Power BI Desktop では、ローカル コンピューターから Power BI サービスにレポート ( *.pbix* ファイル) を発行できます。 Power BI レポートは反対の方向に発行することもできます。Power BI サービスから Power BI Desktop にレポートをダウンロードできます。 いずれの場合も、Power BI レポートの拡張子は .pbix です。

この記事のセクション「[考慮事項とトラブルシューティング](#considerations-and-troubleshooting)」で説明している、いくつかの制限事項に留意してください。

![[ファイル] ドロップダウン](media/service-export-to-pbix/power-bi-file-export.png)

## <a name="download-the-report-as-a-pbix-file"></a>レポートを .pbix ファイルとしてダウンロードする

2016 年 11 月 23 日以降に [Power BI Desktop で作成され](/learn/modules/publish-share-power-bi/2-publish-reports)、その後更新されたレポートのみダウンロードできます。 作成がそれ以前の場合、Power BI サービスの **[レポートのダウンロード]** メニュー オプションは淡色表示されます。

.pbix ファイルをダウンロードするには、次の手順に従います。

1. Power BI サービスで、ダウンロードするレポートを[編集ビュー](./service-interact-with-a-report-in-editing-view.md)で開きます。

2. 上部のナビ ペインで、 **[ファイル]、[レポートのダウンロード]** の順に選択します。
   
3. レポートがダウンロードされているとき、ステータス バナーに進捗状況が表示されます。 ファイルの用意ができると、.pbix ファイルを保存する場所を問われます。 ファイルの既定の名前はレポートのタイトルと同じです。
   
4. Power BI Desktop をまだインストールしていない場合、[インストール](../fundamentals/desktop-get-the-desktop.md)し、.pbix ファイルを Power BI Desktop で開きます。
   
    レポートを Power BI Desktop で開くと、Power BI サービスのレポートで使用できる一部の機能が Power BI Desktop では使用できないという警告メッセージが表示されることがあります。
   
    ![警告ダイアログ](media/service-export-to-pbix/power-bi-export-to-pbix_2.png)

5. Power BI Desktop のレポート エディターと Power BI サービスのレポート エディターは似ています。  
   
    ![Power BI Desktop レポート エディター](media/service-export-to-pbix/power-bi-desktop.png)

## <a name="considerations-and-troubleshooting"></a>考慮事項とトラブルシューティング

Power BI サービスから .pbix ファイルをダウンロードすることに関しては、重要な考慮事項と制限事項がいくつかあります。

* ファイルをダウンロードするには、レポートの編集アクセス権限が必要です。
* レポートが Power BI Desktop を使用して作成され、Power BI サービスに *発行* されているか、.pbix ファイルが Power BI サービスに *アップロード* されている必要があります。
* レポートは、2016 年 11 月 23 日以降に更新または発行されている必要があります。 それ以前に発行されたレポートはダウンロードできません。
* この機能は、Power BI サービスでもともと作成されたレポートやコンテンツ パックには使用できません。
* ダウンロードしたファイルを開くときは常に最新バージョンの Power BI Desktop を使用してください。 最新バージョンではない Power BI Desktop では、ダウンロードした .pbix ファイルを開くことができない場合があります。
* データをダウンロードする機能を管理者が無効にしている場合、この機能は Power BI サービスに表示されません。
* 増分更新を使用しているデータセットは .pbix ファイルにダウンロードできません。
* [大規模なモデル](../admin/service-premium-large-models.md)に対して有効になっているデータセットは、.pbix ファイルにダウンロードできません。
* [XMLA エンドポイント](../admin/service-premium-connect-tools.md)を使用して変更されたデータセットは、.pbix ファイルにダウンロードできません。
* あるワークスペース内のデータセットに基づいて Power BI レポートを作成してから別のワークスペースに発行した場合、お客様とお客様のユーザーはそれをダウンロードできなくなります。 このシナリオでのダウンロード機能は現在サポートされていません。

## <a name="next-steps"></a>次の手順

この機能に関しては、**Guy in a Cube** の簡単なビデオをご覧ください。

<iframe width="560" height="315" src="https://www.youtube.com/embed/ymWqU5jiUl0" frameborder="0" allowfullscreen></iframe>

Power BI サービスの使い方を知るのに役立つ記事を以下に示します。

* [Power BI のレポート](../consumer/end-user-reports.md)
* [Power BI サービスのデザイナー向けの基本的な概念](../fundamentals/service-basic-concepts.md)

Power BI Desktop をインストールした後、次の記事を参照すると短時間で作業を開始するのに役立ちます。

* [Power BI Desktop の概要](../fundamentals/desktop-getting-started.md)

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。