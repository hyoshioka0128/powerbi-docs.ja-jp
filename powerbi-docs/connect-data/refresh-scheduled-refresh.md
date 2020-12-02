---
title: スケジュールされた更新の構成
description: ここでは、ゲートウェイを選択して、スケジュールされた更新を構成する手順を説明します。
author: davidiseminger
ms.author: davidi
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 06/06/2019
LocalizationGroup: Data refresh
ms.openlocfilehash: 9298171a98837a6e8dd16cc89865770e7d88c8c2
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96403906"
---
# <a name="configure-scheduled-refresh"></a>スケジュールされた更新の構成

>[!NOTE]
>2 か月間操作が行われなかった場合、データセットに対するスケジュールされた更新は一時停止されます。 詳しくは、この記事で後述する「[*スケジュールされた更新*](#scheduled-refresh)」をご覧ください。

この記事では、[オンプレミス データ ゲートウェイ (個人用モード)](service-gateway-personal-mode.md) と[オンプレミス データ ゲートウェイ](service-gateway-onprem.md)のスケジュールされた更新に使用可能なオプションを説明します。 Power BI サービスの次の領域で、更新オプションを指定します: **ゲートウェイの接続**、**データ ソースの資格情報**、**更新のスケジュール設定**。 それぞれを順番に見ていきます。 更新スケジュールに関する制限など、データ更新の詳細については、「[データ更新](refresh-data.md#data-refresh)」を参照してください。

**[スケジュールされている更新]** 画面にアクセスするには、次のようにします。

1. ナビゲーション ウィンドウの **[データセット]** で、一覧表示されているデータセットの横にある **[その他のオプション]** (...) を選択します。
2. **[更新のスケジュール設定]** を選択します。

    ![更新のスケジュール設定](media/refresh-scheduled-refresh/dataset-menu.png)

## <a name="gateway-connection"></a>ゲートウェイ接続

パーソナル ゲートウェイまたはエンタープライズ ゲートウェイのどちらをオンラインにして使用できるようにしているかによって、ここに表示されるオプションが変わります。

使用できるゲートウェイがない場合は、 **[ゲートウェイ接続]** が無効になっています。 パーソナル ゲートウェイをインストールする方法を示すメッセージも表示されます。

![ゲートウェイが構成されていません](media/refresh-scheduled-refresh/gateway-not-configured.png)

パーソナル ゲートウェイを構成しており、オンラインになっている場合は選択できます。 選択できない場合は、オフラインとして表示されます。

![ゲートウェイ接続](media/refresh-scheduled-refresh/gateway-connection.png)

エンタープライズ ゲートウェイが使用できる場合は、エンタープライズ ゲートウェイも選択できます。 任意のゲートウェイ用に構成されたデータ ソースの **[ユーザー]** タブにアカウントが表示されている場合は、使用可能なエンタープライズ ゲートウェイのみ表示されます。

## <a name="data-source-credentials"></a>データ ソース資格情報

### <a name="power-bi-gateway---personal"></a>Power BI Gateway - Personal

パーソナル ゲートウェイを使用してデータを更新している場合は、バックエンド データ ソースに接続するために資格情報を指定する必要があります。 オンライン サービスからコンテンツ パックに接続した場合は、接続用に入力した資格情報は、スケジュールされた更新に引き継がれます。

![データ ソース資格情報](media/refresh-scheduled-refresh/data-source-credentials-pgw.png)

必要なのは、データセットで更新を初めて使用するときにデータ ソースにサインインすることだけです。 入力した後は、資格情報はデータセットに保持されます。

> [!NOTE]
> 一部の認証方法では、データ ソースへのサインインに使用するパスワードの有効期限が切れた場合、またはパスワードが変更された場合は、 **[データ ソースの資格情報]** でも、データ ソースのパスワードを変更する必要があります。

うまくいかない場合、問題は Windows にサインインしてサービスを開始できなかったためにゲートウェイがオフラインであること、または Power BI でデータ ソースにサインインできず、更新されたデータに対するクエリを実行できなかったことのいずれかに関係しています。 更新に失敗した場合は、データセットの設定を確認します。 ゲートウェイ サービスがオフラインの場合、 **[状態]** にエラーが表示されています。 Power BI でデータ ソースにサインインできない場合、データ ソースの資格情報でエラーが表示されます。

### <a name="on-premises-data-gateway"></a>オンプレミス データ ゲートウェイ

オンプレミス データ ゲートウェイを使用してデータを更新している場合は、資格情報を指定する必要はありません。ゲートウェイの管理者によってデータ ソースに定義されているためです。

![[更新のスケジュール設定] コマンド](media/refresh-scheduled-refresh/data-source-credentials-egw.png)

> [!NOTE]
> データ更新のためにオンプレミスの SharePoint に接続するとき、Power BI は "*匿名*"、"*基本*"、および "*Windows (NTLM/Kerberos)* " の認証メカニズムのみをサポートします。 オンプレミスの SharePoint データ ソースのデータ更新では、Power BI は "*ADFS*" または "*フォーム ベース認証*" のメカニズムをサポートしません。

## <a name="scheduled-refresh"></a>スケジュールされている更新

**[スケジュールされている更新]** セクションでは、データセットを更新する頻度と時間帯を定義します。 一部のデータ ソースでは、更新を構成できるようにするためにゲートウェイは不要です。その他のデータ ソースでは、ゲートウェイが必要となります。

**[データを最新の状態に保つ]** スライダーを **[オン]** に設定して、設定を構成します。

> [!NOTE]
> スケジュールされた時間枠の 15 分以内に更新を開始することを目標としますが、サービスが必要なリソースを迅速に割り当てることができない場合、最大で 1 時間の遅延が生じる可能性があります。

![[スケジュールされている更新] ダイアログ ボックス](media/refresh-scheduled-refresh/scheduled-refresh.png)

> [!NOTE]
> 2 か月間操作が行われなかった場合、データセットに対するスケジュールされた更新は一時停止されます。 データセットに基づいて作成されたダッシュボードまたはレポートにアクセスするユーザーがいない場合、そのデータセットは非アクティブと見なされます。 その時点で、データセットの所有者には、スケジュールされた更新が一時停止されたことを示す電子メールが送信されます。 データセットの更新スケジュールが **無効** として表示されます。 データセットに基づいて作成されたダッシュボードまたはレポートに再度アクセスするだけで、スケジュールされた更新は再開されます。"

## <a name="whats-supported"></a>サポート対象


> [!NOTE]
> エラーが 4 つ連続で発生すると、スケジュールされた更新も自動的に無効になります。

スケジュールされた更新のために、さまざまなゲートウェイに応じて一定のデータセットがサポートされています。 ここでは、使用できるデータセットを理解するうえで参考になる情報を紹介します。

### <a name="power-bi-gateway---personal"></a>Power BI Gateway - Personal

**Power BI Desktop**

* Power BI Desktop の **[データの取得]** とクエリ エディターに表示される、すべてのオンライン データ ソース。
* Hadoop ファイル (HDFS) と Microsoft Exchange を除く、Power BI Desktop の **[データの取得]** とクエリ エディターに表示される、すべてのオンプレミスのデータ ソース。

**Excel**

* Power Query に表示されるすべてのオンライン データ ソース
* Hadoop ファイル (HDFS) と Microsoft Exchange を除く、Power Query に表示されるすべてのオンプレミスのデータ ソース
* Power Pivot に表示されるすべてのオンライン データ ソース
* Hadoop ファイル (HDFS) と Microsoft Exchange を除く、Power Pivot に表示されるすべてのオンプレミスのデータ ソース

> [!NOTE]
> Excel 2016 以降では、Power Query はリボンの **[データ]** セクションで、 **[データの取得と変換]** の下に表示されます。

### <a name="power-bi-gateway"></a>Power BI Gateway

サポートされているデータ ソースの詳細については、「[Power BI データソース](power-bi-data-sources.md)」を参照してください。

## <a name="troubleshooting"></a>トラブルシューティング
期待どおりにデータが更新されないことがあります。 通常、これはゲートウェイに関係する問題です。 ツールと既知の問題については、ゲートウェイに関するトラブルシューティングの記事を参照してください。

- [オンプレミス データ ゲートウェイのトラブルシューティング](service-gateway-onprem-tshoot.md)
- [Power BI Gateway - Personal のトラブルシューティング](service-admin-troubleshooting-power-bi-personal-gateway.md)

## <a name="next-steps"></a>次の手順

- [Power BI でのデータの更新](refresh-data.md)  
- [Power BI Gateway - Personal](service-gateway-personal-mode.md)  
- [オンプレミス データ ゲートウェイ (個人用モード)](service-gateway-onprem.md)  
- [オンプレミス データ ゲートウェイのトラブルシューティング](service-gateway-onprem-tshoot.md)  
- [Power BI Gateway - Personal のトラブルシューティング](service-admin-troubleshooting-power-bi-personal-gateway.md)  

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。