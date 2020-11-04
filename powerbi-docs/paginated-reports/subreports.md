---
title: Power BI のページ分割された レポートでのサブレポート
description: この記事では、Power BI サービスのページ分割されたレポートでサポートされるデータ ソースについて説明します。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: how-to
ms.date: 04/29/2020
ms.openlocfilehash: d2cd4e9f5d6cb8872e266fabacb9f8a5a3e318cb
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2020
ms.locfileid: "93298013"
---
# <a name="subreports-in-power-bi-paginated-reports"></a>Power BI のページ分割された レポートでのサブレポート

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

*サブレポート* は、ページ分割されたメインのレポート本文内に別のページ分割されたレポートを表示する、ページ分割されたレポート アイテムです。 概念上、レポート内のサブレポートは Web ページ内のフレームとほぼ同じです。 これは、レポートをレポート内に埋め込むために使用します。 任意のレポートをサブレポートとして使用できます。 サブレポートとして表示されるレポートは、親レポートと同じ Premium ワークスペースに保存します。 親レポートからサブレポートにパラメーターを渡すようにも設定できます。 パラメーターを使用してサブレポートの各インスタンスのデータをフィルター処理することにより、サブレポートをデータ領域内で繰り返し使用することができます。  
  
 ![ページ分割されたレポート内のサブレポート](media/subreports/paginated-report-subreport.png "ページ分割されたレポートのサブレポート")  
  
 この図の Sales Order メイン レポートに表示されている連絡先情報は、実際には Contacts サブレポートから取得されたものです。  
  
Power BI レポート ビルダーで、ページ分割されたレポート定義 (.rdl) ファイルを作成および変更します。 SQL Server Reporting Services に格納されているサブレポートは、Power BI サービスの Premium ワークスペースにアップロードできます。 メイン レポートとサブレポートは、同じワークスペースにパブリッシュする必要があります。 [Power BI レポート ビルダー](https://aka.ms/pbireportbuilder)をインストールしてください。
  
## <a name="work-with-report-builder-and-the-power-bi-service"></a>レポート ビルダーと Power BI サービスを操作する

Power BI レポート ビルダーは、コンピューター上のページ分割されたレポート (ローカル レポートと呼ばれます)、または Power BI サービスに関するレポートを操作できます。  レポート ビルダーを初めて開くと、Power BI アカウントにサインインするように求められます。 まだサインインしていない場合、右上隅にある **[サインイン]** を選択します。

:::image type="content" source="media/subreports/report-builder-sign-in.png" alt-text="Power BI へのサインイン":::

サインインすると Power BI レポート ビルダーの **[Power BI サービス]** オプションが、 **[ファイル]** メニューの **[開く]** および **[名前を付けて保存]** オプションとして表示されます。 レポートを保存するための **[Power BI サービス]** オプションを選択した場合は、Power BI レポート ビルダーと Power BI サービスの間にライブ接続が作成されます。 

:::image type="content" source="media/subreports/report-builder-subreport-open-service.png" alt-text="Power BI サービスから開く":::

## <a name="save-a-local-report-to-the-power-bi-service"></a>ローカル レポートを Power BI サービスに保存する

サブレポートをメイン レポートに追加する前に、この 2 つのレポートをまず作成し、それらを同じ Power BI Premium ワークスペースに保存します。 

1. 既存のローカル レポートを開くには、 **[ファイル]** メニューで、 **[開く]**  >  **[この PC]** を選択し、.rdl ファイルを選択します。  

2. **[ファイル]** メニューで、 **[名前を付けて保存]**  >  **[Power BI サービス]** を選択します。  詳細については、「[ページ分割されたレポートを Power BI サービスに発行する](paginated-reports-save-to-power-bi-service.md)」を参照してください。

    > [!NOTE]
    > Power BI サービスから開始して、レポートをアップロードすることもできます。 詳細については、同じ記事「[ページ分割されたレポートを Power BI サービスに発行する](paginated-reports-save-to-power-bi-service.md)」にあります。

3. **[名前を付けて保存]** ダイアログ ボックスで、ページ分割されたレポートを保存できる Power BI Premium ワークスペースを選択します。  Premium ワークスペースには、名前の横にダイヤモンド形のアイコン ![Premium のダイヤモンド形アイコン](media/subreports/report-builder-premium-diamond.png) が表示されます。

    :::image type="content" source="media/subreports/report-builder-subreport-save-as-service.png" alt-text="Power BI サービスの [名前を付けて保存]":::

4. **[保存]** を選択します。

## <a name="add-a-subreport-to-a-report"></a>サブレポートをレポートに追加する

両方のレポートを同じ Premium ワークスペースに保存したので、1 つのレポートをもう一方にサブレポートとして追加できます。 サブレポートを追加するには、次の 2 つの方法があります。 

1. **[挿入]** のリボンで **[サブレポート]** ボタンを選択するか、レポート キャンバスを右クリックして、 **[挿入]**  >  **[サブレポート]** を選択します。

    :::image type="content" source="media/subreports/report-builder-insert-subreport.png" alt-text="レポートにサブレポートを挿入する":::

    **[サブレポートのプロパティ]** ダイアログ ボックスが開きます。  

2. **[参照]** ボタンを選択し、サブレポートとして使用するレポートに移動し、 **[名前]** テキスト ボックスにサブレポートの名前を指定します。

3. 必要に応じて、[パラメーター](#use-parameters-in-subreports)を含むその他のプロパティを構成します。

## <a name="use-parameters-in-subreports"></a>サブレポートのパラメーターを使用する  
 親レポートからサブレポートにパラメーターを渡すには、サブレポートとして使用するレポートでレポート パラメーターを定義します。 親レポートにサブレポートを配置するときに、レポート パラメーターと、親レポートからサブレポート内のレポート パラメーターに渡す値を選択できます。  
  
> [!NOTE]  
> サブレポートから選択するパラメーターは、 *クエリ* パラメーターではなく *レポート* パラメーターです。  
  
 サブレポートは、レポート本文内またはデータ領域内に配置できます。 データ領域にサブレポートを配置する場合、同じサブレポートがグループのインスタンスまたはデータ領域の行ごとに配置されます。 グループまたは行からサブレポートに値を渡すことができます。 サブレポートの値のプロパティで、サブレポート パラメーターに渡す値を含むフィールド用のフィールド式を使用します。  
  
 パラメーターおよびサブレポートの操作の詳細については、SQL Server Reporting Services のドキュメントの[サブレポートおよびパラメーターを追加する](/sql/reporting-services/report-design/add-a-subreport-and-parameters-report-builder-and-ssrs)方法に関する記事を参照してください。  

## <a name="preview-paginated-reports-in-report-builder"></a>ページ分割されたレポートをレポート ビルダーでプレビューする

レポート ビルダーでレポートをプレビューすることができます。

- **[ホーム]** リボンで、 **[実行]** をクリックします。 

レポート ビルダーはデザインツールであるため、レポートのプレビューは、Power BI サービスでのレポートのレンダリングと異なる場合があります。

### <a name="notes-about-previewing"></a>プレビューに関する注意事項

- レポート ビルダーは、レポートで使用されるデータ ソースの資格情報を格納しません。  レポート ビルダーはプレビュー期間中、資格情報のセットを入力するようユーザーに求めます。  
- レポート データ ソースがオンプレミスの場合は、レポートを Power BI ワークスペースに保存した後でゲートウェイを構成する必要があります。
- プレビュー中にレポート ビルダーにエラーが発生した場合、汎用メッセージが返されます。  エラーのデバッグが難しい場合は、Power BI サービスでレポートをレンダリングすることを検討してください。  

## <a name="considerations"></a>考慮事項

### <a name="maintaining-the-connection"></a>接続の維持

ユーザーがファイルを閉じると、レポートビルダーから Power BI への接続は保持されません。  Power BI ワークスペースに格納されているサブレポート付きのローカルのメイン レポートを操作することができます。 メイン レポートを Power BI ワークスペースに保存してから、レポートを閉じるようにしてください。  そうしないと、プレビュー中に 'not found' というメッセージが表示されることがあります。これは、Power BI サービスへのライブ接続がないためです。  このような場合、サブレポートにアクセスし、そのプロパティを選択します。  Power BI サービスからサブレポートを再び開きます。  これによって接続が再確立され、その他のすべてのサブレポートは問題なく動作します。

### <a name="renaming-a-subreport"></a>サブレポートの名前の変更

ワークスペースでサブレポートの名前を変更する場合は、メイン レポートの名前参照を修正する必要があります。 そうしないと、サブレポートはレンダリングされなくなります。 その場合もメインレポートはレンダリングされますが、サブレポート項目内にエラー メッセージが表示されます。

## <a name="migrate-large-reports"></a>サイズの大きいレポートを移行する

サイズの大きいレポートを Power BI に移行する場合は、[RdlMigration ツール](../guidance/migrate-ssrs-reports-to-power-bi.md)を使用することを検討してください。  RdlMigration ツールは、重複するサブレポート名を処理するように更新されました。  複数のレポートが同じ名前を共有し、異なるサブディレクトリに存在する場合、サブレポート名の重複が発生する可能性があります。  名前が一意に解決されない場合は、最初のサブレポートのみが認識されます。

レポート ビルダーを使用してサイズの大きいレポートを移行する場合は、まずサブレポートを操作することをお勧めします。 レポート名が重複しないように、Power BI ワークスペースにそれぞれを保存します。

## <a name="share-reports-with-subreports"></a>レポートとサブレポートを共有する

既に説明したように、メイン レポートとサブレポートは同じワークスペースになければなりません。 そうしないと、サブレポートはレンダリングされなくなります。 メイン レポートを共有する場合は、サブレポートも共有する必要があります。 アプリでメイン レポートを共有する場合は、そのアプリにサブレポートも含めるようにしてください。 メイン レポートをユーザーまたはユーザー グループと直接共有する場合は、各サブレポートを同じ一連のユーザーまたはユーザー グループとも共有していることを確認してください。
  
## <a name="next-steps"></a>次の手順

[Power BI のページ分割されたレポートでのサブレポートのトラブルシューティング](subreports-troubleshoot.md)

[ページ分割されたレポートを Power BI サービスで表示する](../consumer/paginated-reports-view-power-bi-service.md)

その他の質問 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。