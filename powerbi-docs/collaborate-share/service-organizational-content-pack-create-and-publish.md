---
title: 組織のコンテンツ パックを作成して発行する - Power BI
description: このチュートリアルでは、組織のコンテンツ パックを作成して、特定のグループにアクセスを制限し、そのコンテンツ パックを Power BI の組織のコンテンツ パック ライブラリに発行します。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 08/06/2019
LocalizationGroup: Share your work
ms.openlocfilehash: 0a72582a54903c97dd9594f6a4a1c5980aea8e16
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411726"
---
# <a name="tutorial-create-and-publish-a-power-bi-organizational-content-pack"></a>チュートリアル:Power BI の組織のコンテンツ パックを作成して発行する

このチュートリアルでは、組織のコンテンツ パックを作成して、特定のグループにアクセス許可を付与し、そのコンテンツ パックを Power BI の組織のコンテンツ パック ライブラリに発行します。

コンテンツ パックの作成は、ダッシュ ボードを共有すること、またはグループ内でダッシュボードで共同作業を行うこととは異なります。 [Power BI で作業を共有する方法](service-how-to-collaborate-distribute-dashboards-reports.md)を読んで、ご自分の状況に最適なオプションを決定します。

組織のコンテンツ パックを作成するには、あなたとあなたの同僚が使用する [Power BI Pro アカウント](https://powerbi.microsoft.com/pricing)が必要となります。

> [!NOTE]
> 新しいワークスペース エクスペリエンスでは、組織のコンテンツ パックを作成したり、インストールしたりすることはできません。 コンテンツ パックをアプリにまだアップグレードしていない場合は、今がそのよい機会です。 新しいワークスペース エクスペリエンスの詳細については、[こちら](service-create-the-new-workspaces.md)を参照してください。

## <a name="create-and-publish-a-content-pack"></a>コンテンツ パックの作成および公開

あなたは Contoso のリリース マネージャーで、新製品の発売の準備をしています。  共有するレポートを含むダッシュボードを作成しました。 起動を管理している他の従業員にとって役立つ場合があります。 同僚が使用できるようにソリューションとしてダッシュボードとレポートをパッケージする手段が必要です。

どうしたらよいでしょうか? [Power BI サービス](https://powerbi.com)で **[マイ ワークスペース]** に移動します。 次に、 **[データの取得]**  >  **[サンプル]**  >  **[営業案件の分析のサンプル]**  >  **[接続]** に移動し、自分用のコピーを取得します。

1. ナビ ペインで、 **[ワークスペース]**  >  **[マイ ワークスペース]** の順に選択します。

1. 上部のナビ ペインで、歯車アイコン ![歯車アイコンのスクリーンショット](media/service-organizational-content-pack-create-and-publish/cog.png) を選択します。 >  **[コンテンツ パックの作成]** の順に選択します。

   ![歯車アイコンと [コンテンツパックの作成] オプションにフォーカスがある UI のスクリーンショット。](media/service-organizational-content-pack-create-and-publish/pbi_create_contpk.png)

1. **[コンテンツ パックの作成]** ウィンドウで、次の情報を入力します。  

   組織のコンテンツ パック ライブラリがすぐにいっぱいになる可能性があることに注意してください。 このライブラリには、最終的に、組織やグループに対して発行された何百ものコンテンツ パックが格納される可能性があります。 時間をとって、コンテンツ パックにわかりやすい名前を付け、ふさわしい説明を追加して、対象ユーザーを適切に絞り込んでください。  あなたのコンテンツ パックが検索で簡単に見つかるような語を使用してください。 これにより、将来、検索が容易になります。

      ![完全な [コンテンツ パックの作成] フォームのスクリーンショット。](media/service-organizational-content-pack-create-and-publish/cpwindow.png)

    1. **[特定のグループ]** を選択します。

    1. 個々のユーザーの完全なメール アドレス、[Microsoft 365 グループ](https://support.office.com/article/Create-a-group-in-Office-365-7124dc4c-1de9-40d4-b096-e8add19209e9)、配布グループ、またはセキュリティ グループを入力します。 例: salesmgrs@contoso.com、sales@contoso.com

        このチュートリアルでは、あなたのグループのメール アドレスを使用してみてください。

    1. コンテンツ パックに「*営業案件*」という名前を付けます。

        > [!TIP]
        > コンテンツ パックの名前には、ダッシュボードの名前を含めることをお勧めします。 そうすると、同僚がコンテンツ パックに接続した後、ダッシュボードを見つけやすくなります。

    1. 推奨:説明を追加します。 これにより、同僚が必要とするコンテンツ パックを簡単に見つけやすくなります。 説明に加えて、同僚がこのコンテンツ パックを検索するときに使用する可能性があるキーワードを追加します。 同僚が質問したり、サポートを必要としたりするときに備えて連絡先情報を含めます。

    1. グループ メンバーがコンテンツ パックを簡単に見つけられるように、画像またはロゴをアップロードします。

        テキストをスキャンするよりも、画像をスキャンする方が高速です。 このスクリーンショットは、**営業案件数** の縦棒グラフ タイルの画像を示しています。

    1. **[営業案件の分析のサンプル]** ダッシュボードを選択し、コンテンツ パックに追加します。

        Power BI によって、関連するレポートとデータセットが自動的に追加されます。 必要に応じて、他にも追加することができます。

       > [!NOTE]
       > Power BI には、編集できるダッシュボード、レポート、データセット、およびブックの一覧のみが表示されます。 このため、アプリでは共有されていたものは表示されません。

   1. Excel ブックがある場合は、 **[レポート]** の下に Excel アイコン付きで表示されます。 この Excel ブックをコンテンツ パックに追加することもできます。

      ![[レポート] セクションと選択可能なレポートのスクリーンショット。](media/service-organizational-content-pack-create-and-publish/pbi_orgcontpkexcel.png)

      > [!NOTE]
      > グループのメンバーが Excel ブックを表示できない場合は、必要に応じて [OneDrive for Business でメンバーとブック](https://support.office.com/article/Share-documents-or-folders-in-Office-365-1fe37332-0f9a-4719-970e-d2578da4941c)を共有します。

1. **[発行]** を選択し、グループの組織コンテンツ パック ライブラリにコンテンツ パックを追加します。  

   正常に発行されると、成功メッセージが表示されます。

1. グループのメンバーが **[データの取得]**  >  **[組織のコンテンツパック]** に移動すると、あなたのコンテンツ パックが表示されます。

   ![[AppSource] ダイアログ ボックスの [営業案件] コンテンツ パックのスクリーンショット。](media/service-organizational-content-pack-create-and-publish/powerbi-find-content-pack-organization.png)

   > [!TIP]
   > ブラウザーに表示される URL は、このコンテンツ パックの一意のアドレスです。  この新しいコンテンツ パックについて同僚に知らせる場合には、  この URL を電子メールに貼り付けてください。

1. グループ メンバーが **[接続]** を選ぶと、[あなたのコンテンツ パックを表示して作業](service-organizational-content-pack-copy-refresh-access.md)できるようになります。

## <a name="next-steps"></a>次の手順

* [Power BI での組織のコンテンツ パックの概要](service-organizational-content-pack-introduction.md)。

* [組織のコンテンツ パックを管理、更新、削除する](service-organizational-content-pack-manage-update-delete.md)。

* [Power BI でアプリを発行する](service-create-distribute-apps.md)。

* [OneDrive for Business とは?](https://support.office.com/article/What-is-OneDrive-for-Business-187f90af-056f-47c0-9656-cc0ddca7fdc2)

* 他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。
