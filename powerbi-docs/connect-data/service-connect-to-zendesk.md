---
title: Power BI で Zendesk に接続する
description: Power BI 用 Zendesk
author: paulinbar
ms.author: painbar
ms.reviewer: sarinas
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 05/04/2020
LocalizationGroup: Connect to services
ms.openlocfilehash: d5400830df44055a0f17de72385778a0c06fb06b
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96403032"
---
# <a name="connect-to-zendesk-with-power-bi"></a>Power BI で Zendesk に接続する

この記事では、Power BI テンプレート アプリを使用して Zendesk アカウントからデータをプルする手順について説明します。 Zendesk アプリは、Power BI ダッシュボードと一連の Power BI レポートを提供し、お客様のチケット ボリュームとエージェント パフォーマンスに関する分析情報を示します。 データは、1 日 1 回自動的に更新されます。 

テンプレート アプリをインストールした後、最も関心のある情報が強調表示されるようにダッシュボードとレポートをカスタマイズできます。 その後、組織内の同僚にアプリとして配布することができます。

[Zendesk テンプレート アプリ](https://app.powerbi.com/getdata/services/zendesk)に接続するか、Power BI と [Zendesk との統合](https://powerbi.microsoft.com/integrations/zendesk)について詳細をお読みください。

テンプレート アプリをインストールした後は、ダッシュボードとレポートを変更できます。 その後、組織内の同僚にアプリとして配布することができます。

>[!NOTE]
>接続するには、Zendesk 管理者アカウントが必要です。 [要件](#system-requirements)の詳細については、このあと説明します。

>[!WARNING]
>2019 年 10 月 15 日より前の Zendesk Support Search API では、大規模クエリの改ページを利用して合計 200,000 件の結果を受け取ることができました。 検索使用をその意図された範囲に合わせるため、Zendesk では、返される結果の最大数を合計 1,000 件に制限するようになりました。ページごとの結果最大数は 100 件です。 ただし、現行の Power BI Zendesk コネクタでは引き続き、これらの新しい制限を超えて API を呼び出しできるため、紛らわしい結果が導かれる可能性があります。

## <a name="how-to-connect"></a>接続する方法

[!INCLUDE [powerbi-service-apps-get-more-apps](../includes/powerbi-service-apps-get-more-apps.md)]

3. **[Zendesk]** \> **[今すぐ入手]** の順に選択します。
4. **[この Power BI アプリをインストールしますか?]** で、 **[インストール]** を選択します。
4. **[アプリ]** ペインで、 **[Zendesk]** タイルを選択します。

    ![Power BI Zendesk アプリのタイル](media/service-connect-to-zendesk/power-bi-zendesk-tile.png)

6. **[新しいアプリを開始する]** で **[接続]** を選択します。

    ![新しいアプリを開始する](media/service-connect-to-zendesk/power-bi-new-app-connect-get-started.png)

4. アカウントと関連付けられている URL を指定します。 URL の形式は **https://company.zendesk.com** です。 [これらのパラメーターの見つけ方](#finding-parameters)について詳しくは、後述します。
   
   ![Zendesk に接続](media/service-connect-to-zendesk/pbi_zendeskconnect.png)

5. ダイアログが表示されたら、Zendesk の資格情報を入力します。  認証方法として **[oAuth 2]** を選択し、 **[サインイン]** をクリックします。 Zendesk 認証フローに従います。 (ブラウザーで既に Zendesk にサインインしている場合は、資格情報を求めるダイアログが表示されないことがあります)。
   
   > [!NOTE]
   > テンプレート アプリを使用するには、Zendesk 管理者アカウントを使用して接続する必要があります。 
   > 
   
   ![oAuth2 を使用してサインインする](media/service-connect-to-zendesk/pbi_zendesksignin.png)
6. [ **許可]** をクリックして、Power BI が Zendesk データにアクセスできるようにします。
   
   ![[許可] をクリックする](media/service-connect-to-zendesk/zendesk2.jpg)
7. **[接続]** をクリックしてインポート プロセスを開始します。 
8. Power BI にデータがインポートされると、Zendesk アプリのコンテンツ リスト (新しいダッシュ ボード、レポート、データセット) が表示されます。
9. ダッシュボードを選択して、探索プロセスを開始します。

    ![Zendesk のダッシュボード](media/service-connect-to-zendesk/power-bi-zendesk-dashboard.png)
   
## <a name="modify-and-distribute-your-app"></a>アプリを変更して配布する

Zendesk テンプレート アプリをインストールできました。 これは、Zendesk ワークスペースも作成されたことを意味します。 ワークスペースでは、レポートとダッシュボードを変更して、それを組織内の同僚に "*アプリ*" として配布することができます。 

1. 新しい Zendesk ワークスペースのすべてのコンテンツを表示するには、ナビゲーション ペインで **[ワークスペース]**  >  **[Zendesk]** の順に選択します。 

    ![ナビゲーション ペインの Zendesk ワークスペース](media/service-connect-to-zendesk/power-bi-zendesk-workspace-left-nav.png)

    このビューは、ワークスペースのコンテンツ リストです。 右上隅に、 **[アプリを更新]** が表示されます。 同僚にアプリを配布する準備ができたら、そこが出発地点になります。 

    ![Zendesk コンテンツ リスト](media/service-connect-to-zendesk/power-bi-zendesk-content-list.png)

2. ワークスペース内の他の要素を表示するには、 **[レポート]** および **[データセット]** を選択します。

    同僚に[アプリを配布する](../collaborate-share/service-create-distribute-apps.md)方法に関する記事を参照してください。

## <a name="system-requirements"></a>システム要件
Zendesk テンプレート アプリにアクセスするには、Zendesk 管理者アカウントが必要です。 エージェントまたはエンド ユーザーが Zendesk データを表示する場合は、[Power BI Desktop](desktop-connect-to-data.md) で候補を追加し、Zendesk コネクタを確認します。

## <a name="finding-parameters"></a>パラメーターの見つけ方
Zendesk URL は、Zendesk アカウントにサインインするときに使用した URL と同じになります。 Zendesk URL がよくわからない場合には、Zendesk [ログイン ヘルプ](https://www.zendesk.com/login/)を使用できます。

## <a name="troubleshooting"></a>トラブルシューティング
接続の問題が発生した場合は、Zendesk URL を確認し、Zendesk 管理者アカウントを使用していることを確かめます。

## <a name="next-steps"></a>次の手順

* [Power BI で新しいワークスペースを作成する](../collaborate-share/service-create-the-new-workspaces.md)
* [Power BI にアプリをインストールし、使用する](../consumer/end-user-apps.md)
* [外部サービス用の Power BI アプリに接続する](service-connect-to-services.md)
* わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
