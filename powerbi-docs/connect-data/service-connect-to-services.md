---
title: Power BI で使用するサービスに接続する
description: Salesforce、Microsoft Dynamics CRM、Google Analytics など、ビジネスに使用する数多くのサービスに接続します。
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 08/29/2019
LocalizationGroup: Connect to services
ms.openlocfilehash: a2151f80a9c8da7230338355fb10b9a0820286a1
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410507"
---
# <a name="connect-to-the-services-you-use-with-power-bi"></a>Power BI で使用するサービスに接続する
Power BI では、Salesforce、Microsoft Dynamics、Google Analytics など、ビジネスに使用する数多くのサービスに接続できます。 Power BI は、資格情報を使用してサービスに接続することで開始します。 これは、データを自動表示し、ビジネスに関する分析を視覚的に示すダッシュボードと一連の Power BI レポートで Power BI "*ワークスペース*" を作成します。

>[!IMPORTANT]
>サービス コンテンツ パックは、[テンプレート アプリ](./service-template-apps-overview.md)に置き換えられています。 2019 年 9 月 25 日の時点で、多くのコンテンツ パックが既に非推奨となっています。 インストールされている非推奨のコンテンツ パックはご利用のアカウントに残りますが、それに対するドキュメントやサポートは提供されません。また、もう一度インストールすることもできません。

Power BI にサインインし、[接続できるすべてのサービス](https://app.powerbi.com/getdata/services)を表示します。 

![AppSource アプリ](media/service-connect-to-services/overview.png)

アプリをインストールすると、アプリ内のダッシュボードやレポート、および Power BI サービス内のワークスペース ([https://app.powerbi.com](https://app.powerbi.com)) を表示できます。 これらは、Power BI モバイル アプリで表示することもできます。 このワークスペースでは、組織のニーズに合わせてダッシュボードやレポートを変更し、その後それらを *アプリ* として同僚に配布できます。 

![Power BI モバイル アプリの Google アナリティクス アプリ](media/service-connect-to-services/power-bi-service-mobile-app-240.png)

## <a name="get-started"></a>はじめに
[!INCLUDE [powerbi-service-apps-get-more-apps](../includes/powerbi-service-apps-get-more-apps.md)]

## <a name="edit-the-dashboard-and-reports"></a>ダッシュ ボードとレポートを編集する
インポートが完了すると、新しいアプリが [アプリ] ページに表示されます。

1. ナビ ペインで **[アプリ]** を選んでから、アプリを選びます。
   
     ![[アプリ] ページ](media/service-connect-to-services/power-bi-service-apps-open-app.png)
2. Q&A ボックスに質問を入力したり、タイルをクリックして基になっているレポートを開いたりできます。 
   
    ![Google アナリティクス ダッシュボード](media/service-connect-to-services/googleanalytics2.png)
   
    組織のニーズに合わせて、ダッシュボードとレポートを変更します。 その後、[アプリを同僚に配布します。](../collaborate-share/service-create-distribute-apps.md)

## <a name="whats-included"></a>含まれるもの
サービスに接続すると、ダッシュボード、レポート、データセットを含む、新しく作成されたアプリとワークスペースが表示されます。 サービスからのデータは特定のシナリオに重点を置いたものであり、そのサービスのすべての情報が入っているとは限りません。 データは、1 日に 1 回自動的に更新されます。 データセットを選択し、このスケジュールを変更できます。

また、Google Analytics など [Power BI Desktop の数多くのサービスに接続](desktop-data-sources.md)して、独自にカスタマイズしたダッシュボードとレポートを作成することもできます。  

特定のサービスに接続する方法については、個々のヘルプ ページを参照してください。

## <a name="troubleshooting"></a>トラブルシューティング
**タイルが空になっている**  
Power BI が初めてサービスに接続するとき、ダッシュボードに空のタイル セットが表示されることがあります。 2 時間後、空のダッシュボードが依然として表示される場合、接続に失敗した可能性があります。 問題の修正の関する情報を含むエラー メッセージが表示されなかった場合、サポート チケットを利用してください。

* 右上隅にある疑問符アイコン ( **?** ) を選択し、 **[ヘルプを取得]** を選択します。
  
    ![[ヘルプを取得] アイコン](media/service-connect-to-services/power-bi-service-get-help.png)

**情報が不足している**  
ダッシュボードとレポートには、特定のシナリオに重点を置いたサービスのコンテンツが含まれています。 アプリで特定のメトリックを探していて、それが表示されていない場合は、[Power BI サポート](https://support.powerbi.com/forums/265200-power-bi) ページにアイデアを追加してください。

## <a name="suggesting-services"></a>サービスを提案する
Power BI アプリにしてほしいサービスがある場合は、 [[Power BI サポート]](https://support.powerbi.com/forums/265200-power-bi) ページでお知らせください。

自分で配布するテンプレート アプリを作成する場合、「[Create a template app in Power BI](service-template-apps-create.md)」 (Power BI でテンプレート アプリを作成する) を参照してください。 Power BI パートナーは、ほとんどまたはまったくコーディングせずに Power BI アプリを作成し、Power BI ユーザーに展開することができます。 

## <a name="next-steps"></a>次のステップ
* [同僚にアプリを配布する](../collaborate-share/service-create-distribute-apps.md)
* [Power BI で新しいワークスペースを作成する](../collaborate-share/service-create-the-new-workspaces.md)
* ご質問 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。