---
title: Power BI サービスでページ分割されたレポートのパラメーターを作成する
description: この記事では、Power BI サービスでページ分割されたレポートのパラメーターを作成する方法について説明します。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: how-to
ms.date: 09/28/2020
ms.openlocfilehash: 217c1b571c01068d64283df0b25b5e56bbc8b956
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2020
ms.locfileid: "93297214"
---
# <a name="create-parameters-for-paginated-reports-in-the-power-bi-service"></a>Power BI サービスでページ分割されたレポートのパラメーターを作成する

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

この記事では、Power BI サービスでページ分割されたレポートのパラメーターを作成する方法について説明します。  レポート パラメーターは、レポート データを選択し、レポートの体裁を変更する方法を提供します。 既定値や使用可能な値のリストを指定できます。 レポートの閲覧者は、選択内容を変更できます。 また、パラメーター テキスト ボックスに入力して、値を検索することもできます。 Power BI サービスにおけるパラメーターの操作方法を確認するには、[ページ分割されたレポートのパラメーターの表示](../consumer/paginated-reports-view-parameters.md)に関する記事を参照してください。  

次の図は、@BuyingGroup、@Customer、@FromDate、@ToDate の各パラメーターを指定したレポートの Power BI レポート ビルダーのデザイン ビューを示しています。 
  
![レポート ビルダーにおけるパラメーター](media/paginated-reports-parameters/power-bi-paginated-parameters-report-builder.png)
  
1.  レポート データ ペインのレポート パラメーター。  
  
2.  データセット内のいずれかのパラメーターを含むテーブル。  
  
3.  パラメーター ペイン。 パラメーター ペインのパラメーターのレイアウトをカスタマイズすることができます。 
  
4.  @FromDate パラメーターと @ToDate パラメーターのデータ型は **DateTime** です。 レポートを表示する場合は、テキスト ボックスに日付を入力するか、カレンダー コントロールで日付を選択できます。 

5.  **[データセットのプロパティ]** ダイアログ ボックスに表示される 1 つのプロパティ。  

  
## <a name="create-or-edit-a-report-parameter"></a>レポート パラメーターを作成または編集する  
  
1.  ページ分割されたレポートを Power BI レポート ビルダーで開きます。

1. **レポート データ** ペインで、 **[パラメーター]** ノードを右クリックして **[パラメーターの追加]** を選択します。 **[レポート パラメーターのプロパティ]** ダイアログ ボックスが表示されます。  
  
2.  **[名前]** にパラメーターの名前を入力するか、または既定の名前をそのまま使用します。  
  
3.  **[プロンプト]** に、ユーザーがレポートを実行するときにパラメーター テキスト ボックスの横に表示するテキストを入力します。  
  
4.  **[データ型]** で、パラメーター値のデータ型を選択します。  
  
5.  空白の値を含めることができる場合は、 **[空白の値を許可]** をオンにします。  
  
6.  パラメーターに NULL 値を含めることができる場合は、 **[NULL 値を許可]** をオンにします。  
  
7.  パラメーターに複数の値を選択できるようにする場合は、 **[複数の値を許可]** を選択します。  
  
8.  表示オプションを設定します。  
  
    -   パラメーターをレポート上部のツール バーに表示する場合は、 **[表示]** を選択します。  
  
    -   パラメーターを非表示にしてツールバーに表示されないようにするには、 **[非表示]** を選択します。  
  
    -   レポートのパブリッシュ後はパラメーターを非表示にし、レポート サーバーで変更できないよう保護する場合は、 **[内部]** を選択します。 レポート パラメーターは、レポート定義でのみ参照できます。 このオプションを選択した場合は、既定値を設定するか、パラメーターで Null 値を許可するように設定する必要があります。  
  
9. **[OK]** を選択します。 

## <a name="next-steps"></a>次のステップ

Power BI サービスにおけるパラメーターの表示方法を確認するには、「[View parameters for paginated reports](../consumer/paginated-reports-view-parameters.md)」(ページ分割されたレポートのパラメーターを表示する) を参照してください。

ページ分割されたレポートのパラメーターの詳細については、「[Report parameters in Power BI Report Builder](report-builder-parameters.md)」 (Power BI レポート ビルダーのレポート パラメーター) を参照してください。
