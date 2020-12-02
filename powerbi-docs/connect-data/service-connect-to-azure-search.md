---
title: Power BI で Azure Search に接続する
description: Power BI 用 Azure Search
author: davidiseminger
ms.author: davidi
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
LocalizationGroup: Connect to services
ms.openlocfilehash: 5c2c5d3b6382fdb85125a71829d62624dab31e83
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96403377"
---
# <a name="connect-to-azure-search-with-power-bi"></a>Power BI で Azure Search に接続する
Azure Search のトラフィック分析を使うと、Azure Search サービスへのトラフィックを監視し、把握できます。 Power BI 用の Azure Search コンテンツ パックは、過去 30 日間の検索、インデックス作成、サービス統計情報、待機時間など、検索データの詳細な洞察を提供します。 詳細については、[Azure のブログ投稿](https://azure.microsoft.com/blog/analyzing-your-azure-search-traffic/)をご覧ください。

[!INCLUDE [include-short-name](../includes/service-deprecate-content-packs.md)]

Power BI 用 [Azure Search コンテンツ パック](https://app.powerbi.com/getdata/services/azure-search)に接続します。

## <a name="how-to-connect"></a>接続する方法
1. ナビ ペインの下部にある **[データの取得]** を選択します。
   
   ![ナビ ペインのボタンを示す、Power B I Desktop の [データの取得] のスクリーンショット。](media/service-connect-to-azure-search/pbi_getdata.png) 
2. **[サービス]** ボックスで、 **[取得]** を選択します。
   
   ![[サービス] ダイアログのスクリーンショット。[取得] ボタンが表示されます。](media/service-connect-to-azure-search/pbi_getservices.png) 
3. **[Azure Search]** \> **[取得]** を選択します。
   
   ![[Azure サービス] ダイアログのスクリーンショット。[取得] リンクが表示されます。](media/service-connect-to-azure-search/azuresearch.png)
4. Azure Search 分析が格納されているテーブル ストレージ アカウントの名前を指定します。
   
   ![[Connect Azure Search]\(Azure Search 接続\) ダイアログのスクリーンショット。[Azure ストレージ アカウント名] フィールドが表示されています。](media/service-connect-to-azure-search/params.png)
5. 認証メカニズムとして **[キー]** を選び、ストレージ アカウント キーを指定します。 **[サインイン]** をクリックして、読み込みプロセスを開始します。
   
   ![[Connect Azure Search]\(Azure Search 接続\) ダイアログのスクリーンショット。[認証方法] フィールドに [キー] が入力されています。](media/service-connect-to-azure-search/creds.png)
6. 読み込みが完了すると、新しいダッシュボード、レポート、モデルがナビ ペインに表示されます。 インポートされたデータを表示するダッシュボードを選択します。
   
    ![ナビゲーション ウィンドウのスクリーンショット。ダッシュボード、レポート、モデルが表示されています。](media/service-connect-to-azure-search/dashboard2.png)

**実行できる操作**

* ダッシュボード上部にある [Q&A ボックスで質問](../consumer/end-user-q-and-a.md)してみてください。
* ダッシュボードで[タイルを変更](../create-reports/service-dashboard-edit-tile.md)できます。
* [タイルを選択](../consumer/end-user-tiles.md)して基になるレポートを開くことができます。
* データセットは毎日更新するようにスケジュール設定されますが、更新のスケジュールは変更でき、また **[今すぐ更新]** を使えばいつでも必要なときに更新できます。

## <a name="system-requirements"></a>システム要件
Azure Search コンテンツ パックを使うには、Azure Search のトラフィック分析をアカウントで有効にする必要があります。

## <a name="troubleshooting"></a>トラブルシューティング
ストレージ アカウント名とフル アクセス キーを正しく指定したことを確認します。 ストレージ アカウント名は、Azure Search のトラフィック分析機能を構成したアカウントに対応している必要があります。

## <a name="next-steps"></a>次の手順
[Power BI とは?](../fundamentals/power-bi-overview.md)

[Power BI サービスのデザイナー向けの基本的な概念](../fundamentals/service-basic-concepts.md)
