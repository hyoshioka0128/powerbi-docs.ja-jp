---
title: ページ分割されたレポートを Power BI サービスに発行する
description: このチュートリアルでは、ページ分割されたレポートをローカル コンピューターからアップロードすることによって Power BI サービスに発行することを学びます。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: how-to
ms.date: 05/04/2020
ms.openlocfilehash: 28058161672de9db0cac5093e652e1d551f6a80a
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2020
ms.locfileid: "93297324"
---
# <a name="publish-a-paginated-report-to-the-power-bi-service"></a>ページ分割されたレポートを Power BI サービスに発行する

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

この記事では、ページ分割されたレポートをローカル コンピューターからアップロードすることによって Power BI サービスに発行することについて学びます。 ワークスペースが Premium 容量である限り、ページ分割されたレポートをマイ ワークスペースまたは他のワークスペースにアップロードできます。 ワークスペース名の横にあるダイヤモンド形のアイコン ![Power BI Premium 容量のダイヤモンド形のアイコン](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) を探します。 

レポートのデータ ソースがオンプレミスの場合は、レポートをアップロードした後で、ゲートウェイを作成する必要があります。 この記事の後半の「[ゲートウェイを作成する](#create-a-gateway)」セクションを参照してください。

## <a name="add-a-workspace-to-a-premium-capacity"></a>Premium 容量にワークスペースを追加する

ワークスペースの名前の横にダイヤモンド形のアイコン ![Power BI Premium 容量のダイヤモンド形のアイコン](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) がない場合は、Premium 容量にワークスペースを追加する必要があります。 

1. **[ワークスペース]** を選択し、ワークスペース名の横にある省略記号 **[...]** を選択して、 **[ワークスペースの編集]** を選択します。

    ![[ワークスペースの編集] を選択する](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace.png)

1. **[ワークスペースの編集]** ダイアログ ボックスで、 **[詳細設定]** を展開し、 **[専用の容量]** を **[オン]** にスライドします。

    ![[専用の容量] を選択する](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace-dialog.png)

   変更できない場合があります。 できない場合は、Power BI Premium 容量の管理者に連絡し、ワークスペースを Premium 容量に追加するための割り当て権限を付与してもらってください。

## <a name="from-report-builder-publish-a-paginated-report"></a>レポート ビルダーから、ページ分割されたレポートを発行する

1. レポート ビルダーでページ分割されたレポートを作成し、ローカル コンピューターに保存します。

1. レポート ビルダーの **[ファイル]** メニューで、 **[名前を付けて保存]** を選択します。

    ![[ファイル] メニュー > [保存] > [ファイルとして保存]](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-save-as.png)

    まだ Power BI にサインインしていない場合は、ここでサインインするか、アカウントを作成する必要があります。 レポート ビルダーの右上隅にある **[サインイン]** を選択し、手順を完了します。

2. 左側のワークスペースのリストで、その名前の横にあるダイヤモンド形のアイコン ![Power BI Premium 容量のダイヤモンド形のアイコン](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) が付いたワークスペースを選択します。 ボックスに **ファイル名** を入力して、 **[保存]** を選択します。 

    ![Premium ワークスペースを選択する](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-workspace.png)

4. ブラウザーで Power BI サービスを開き、ページ分割されたレポートを発行する、Premium ワークスペースを参照します。 **[レポート]** タブにレポートが表示されます。

    ![ページ一覧でのページ分割されたレポート](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-wwi-report.png)

5. ページ分割されたレポートを選択して、Power BI サービスで開きます。 パラメーターがある場合は、レポートを表示する前に、選択する必要があります。

    ![パラメーターを選択する](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-parameters.png)

6. レポートのデータ ソースがオンプレミスの場合は、この記事の[ゲートウェイを作成する](#create-a-gateway)方法を参照して、データ ソースにアクセスしてください。

## <a name="from-the-power-bi-service-upload-a-paginated-report"></a>Power BI サービスから、ページ分割されたレポートをアップロードする

Power BI サービスから開始し、ページ分割されたレポートをアップロードすることもできます。

1. レポート ビルダーでページ分割されたレポートを作成し、ローカル コンピューターに保存します。

1. ブラウザーで Power BI サービスを開き、レポートを発行する Premium ワークスペースを参照します。 名前の横にあるダイヤモンド形のアイコン ![Power BI Premium 容量のダイヤモンド形のアイコン](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) を確認します。 

1. **[データを取得]** を選択します。

    ![Power BI でのデータ取得](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-get-data.png)

1. **[ファイル]** ボックスで、 **[取得]** を選択します。

    ![Power BI のファイルの取得](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-files-get.png)

1. **[ローカル ファイル]** を選択し、ページ分割されたレポートを参照して、 **[開く]** を選択します。

    ![[ローカル ファイル] を選択する](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-local-file.png)

1. **[続行]**  >  **[資格情報の編集]** の順に選択します。

    ![[資格情報の編集] を選択する](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-edit-credentials.png)

1. 資格情報を構成し、 **[サインイン]** を選択します。

    ![資格情報を編集](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-credentials.png)

   **[レポート]** タブにレポートが表示されます。

    ![ページ一覧でのページ分割されたレポート](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-wwi-report.png)

1. それを選択して Power BI サービスで開きます。 パラメーターがある場合は、レポートを表示する前に、選択する必要があります。
 
    ![パラメーターを選択する](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-parameters.png)

6. レポートのデータ ソースがオンプレミスの場合は、この記事の[ゲートウェイを作成する](#create-a-gateway)方法を参照して、データ ソースにアクセスしてください。

## <a name="create-a-gateway"></a>ゲートウェイを作成する

他の Power BI レポートと同じように、レポートのデータ ソースがオンプレミスにある場合は、データにアクセスするために、ゲートウェイを作成するか、ゲートウェイに接続する必要があります。

1. レポート名の横にある **[管理]** を選択します。

   ![ページ分割されたレポートを管理する](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-manage.png)

1. 詳細と以降の手順については、Power BI サービスの記事「[オンプレミス データ ゲートウェイ](../connect-data/service-gateway-onprem.md)」をご覧ください。



## <a name="next-steps"></a>次のステップ

- [ページ分割されたレポートを Power BI サービスで表示する](../consumer/paginated-reports-view-power-bi-service.md)
- [Power BI Premium のページ分割されたレポートとは](paginated-reports-report-builder-power-bi.md)
- [チュートリアル: 顧客向けのアプリケーションに Power BI のページ分割されたレポートを埋め込む](../developer/embedded/embed-paginated-reports-customers.md)
