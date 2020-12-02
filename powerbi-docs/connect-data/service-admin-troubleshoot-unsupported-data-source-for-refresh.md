---
title: 更新がサポートされていないデータ ソースのトラブルシューティング
description: 更新がサポートされていないデータ ソースのトラブルシューティング
author: davidiseminger
ms.author: davidi
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: troubleshooting
ms.date: 05/08/2020
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 4ab84a4f40acff894416fe2e5b33788c413ad4f5
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410760"
---
# <a name="troubleshooting-unsupported-data-source-for-refresh"></a>更新がサポートされていないデータ ソースのトラブルシューティング
スケジュールされた更新用にデータセットを構成しようとすると、エラーが発生する場合があります。

```output
You cannot schedule refresh for this dataset because it gets data from sources that currently don’t support refresh.
```

これは、使用しているデータ ソースが Power BI Desktop 内では更新用にサポートされていない場合に発生します。 使用しているデータ ソースを検索し、「[Power BI でのデータの更新](refresh-data.md)」のサポートされているデータ ソースの一覧と比較する必要があります。 

## <a name="find-the-data-source"></a>データ ソースの検索
どのデータ ソースを使用しているかが不明な場合は、Power BI Desktop 内で、次の手順を実行して確認できます。  

1. Power BI Desktop で、 **[レポート]** ウィンドウが表示されていることを確認します。  
   ![Desktop の [レポート] ウィンドウ](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-report-pane.png)
2. リボン バーから **[クエリの編集]** を選択します。  
   ![クエリの編集](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-edit-queries.png)
3. **[詳細設定エディター]** を選択します。  
   ![詳細設定エディター](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-advanced-editor.png)
4. ソース用に一覧で示されているプロバイダーをメモしておきます。  この例では、プロバイダーは ActiveDirectory です。  
   ![データ ソースのプロバイダー](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-provider.png)
5. プロバイダーを、「[Power BI データ ソース](power-bi-data-sources.md)」に含まれるサポートされているデータ ソースの一覧と比較します。

> [!NOTE]
> 手動で作成したクエリを含むデータ ソースなど、動的データ ソースに関連する更新の問題については、「[更新と動的データ ソース](refresh-data.md#refresh-and-dynamic-data-sources)」を参照してください。


## <a name="next-steps"></a>次の手順
[データ更新](refresh-data.md)  
[Power BI Gateway - Personal](service-gateway-personal-mode.md)  
[On-premises data gateway (オンプレミス データ ゲートウェイ)](service-gateway-onprem.md)  
[オンプレミス データ ゲートウェイのトラブルシューティング](service-gateway-onprem-tshoot.md)  
[Power BI Gateway - Personal のトラブルシューティング](service-admin-troubleshooting-power-bi-personal-gateway.md)  

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
