---
title: Power BI サービスでページ分割されたレポートのパラメーターを作成する
description: この記事では、Power BI サービスでページ分割されたレポートのパラメーターを作成する方法について説明します。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 12/03/2019
ms.openlocfilehash: 42b9057ccfaa918593e1be8a182c7b0ee57f9760
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "78920989"
---
# <a name="create-parameters-for-paginated-reports-in-the-power-bi-service"></a>Power BI サービスでページ分割されたレポートのパラメーターを作成する

この記事では、Power BI サービスでページ分割されたレポートのパラメーターを作成する方法について説明します。  レポート パラメーターは、レポート データを選択し、レポートの体裁を変更する方法を提供します。 ユーザーが既定値および使用可能な値の一覧を指定し、レポート閲覧者が選択内容を変更できます。  

次の図は、@BuyingGroup、@Customer、@FromDate、@ToDate の各パラメーターを指定したレポートの Power BI レポート ビルダーのデザイン ビューを示しています。 
  
![レポート ビルダーにおけるパラメーター](media/paginated-reports-parameters/power-bi-paginated-parameters-report-builder.png)
  
1.  レポート データ ペインに表示されるレポート パラメーター。  
  
2.  データセット内のいずれかのパラメーターを含むテーブル。  
  
3.  パラメーター ペイン。 パラメーター ペインでは、パラメーターのレイアウトをカスタマイズできます。 
  
4.  @FromDate パラメーターと @ToDate パラメーターのデータ型は **DateTime** です。 レポートを表示する場合は、テキスト ボックスに日付を入力するか、カレンダー コントロールで日付を選択できます。 

5.  **[データセットのプロパティ]** ダイアログ ボックスに表示される 1 つのプロパティ。  

  
## <a name="create-or-edit-a-report-parameter"></a>レポート パラメーターを作成または編集する  
  
1.  ページ分割されたレポートを Power BI レポート ビルダーで開きます。

1. **レポート データ** ペインで、 **[パラメーター]** ノードを右クリックして **[パラメーターの追加]** を選択します。 **[レポート パラメーターのプロパティ]** ダイアログ ボックスが表示されます。  
  
2.  **[名前]** にパラメーターの名前を入力するか、または既定の名前をそのまま使用します。  
  
3.  **[プロンプト]** に、ユーザーがレポートを実行するときにパラメーター テキスト ボックスの横に表示するテキストを入力します。  
  
4.  **[データ型]** で、パラメーター値のデータ型を選択します。  
  
5.  パラメーターに空白の値を含めることができるようにする場合は、 **[空白の値を許可する]** を選択します。  
  
6.  パラメーターに null 値を含めることができるようにする場合は、 **[NULL 値を許可する]** を選択します。  
  
7.  ユーザーが 1 つのパラメーターに対して複数の値を選択できるようにするには、 **[複数の値を許可]** を選択します。  
  
8.  表示オプションを設定します。  
  
    -   レポートの上部にあるツール バーにパラメーターを表示するには、 **[表示]** を選択します。  
  
    -   パラメーターを非表示にしてツール バーに表示されないようにするには、 **[非表示]** を選択します。  
  
    -   パラメーターを非表示にして、レポートの発行後にレポート サーバーでパラメーターを変更できないようにするには、 **[内部]** を選択します。 これにより、レポート パラメーターをレポート定義でのみ確認することができます。 このオプションでは、既定値を設定するか、パラメーターが null 値を受け入れるようにする必要があります。  
  
9. **[OK]** を選択します。 

## <a name="considerations-and-troubleshooting"></a>考慮事項とトラブルシューティング

- データ ソースとして Power BI データセットまたは Analysis Services モデルを使用している場合、DAX の制限により、1 つの要求で 1,000 を超えるパラメーター値を渡すことはできません。 

 
## <a name="next-steps"></a>次のステップ

Power BI サービスにおけるパラメーターの表示方法を確認するには、「[View parameters for paginated reports](../consumer/paginated-reports-view-parameters.md)」(ページ分割されたレポートのパラメーターを表示する) を参照してください。

ページ分割されたレポートのパラメーターの詳細については、「[Report parameters in Power BI Report Builder](report-builder-parameters.md)」 (Power BI レポート ビルダーのレポート パラメーター) を参照してください。
