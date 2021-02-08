---
title: Power BI Desktop で Snowflake Computing ウェアハウスに接続する
description: Power BI Desktop で Snowflake Computing ウェアハウスに簡単に接続して使用する
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 01/04/2021
LocalizationGroup: Connect to data
ms.openlocfilehash: 377ede2171a721a33aa0b70819ef511d721f2590
ms.sourcegitcommit: f7330dabb9cd8bce90bb2efec3e3273a11578f10
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2021
ms.locfileid: "99494445"
---
# <a name="connect-to-snowflake-in-power-bi-desktop"></a>Power BI Desktop で Snowflake に接続する
Power BI Desktop では、**Snowflake** Computing ウェアハウスに接続し、Power BI Desktop の他のデータ ソースの場合と同様に基になっているデータを使用できます。 

## <a name="connect-to-a-snowflake-computing-warehouse"></a>Snowflake Computing ウェアハウスに接続する
**Snowflake** Computing ウェアハウスに接続するには、Power BI Desktop の **[ホーム]** リボンで **[データの取得]** を選択します。 左側のカテゴリから **[データベース]** を選ぶと、 **[Snowflake]** が表示されます。

![Snowflake データベースの選択を示す、[データの取得] ダイアログのスクリーンショット。](media/desktop-connect-snowflake/connect-snowflake-2b.png)

表示された **[Snowflake]** ウィンドウ内のボックスに Snowflake Computing ウェアハウスの名前を入力するか、貼り付け、 **[OK]** をクリックします。 Power BI にデータを直接 **インポート** したり、**DirectQuery** を使用したりできます。 詳しくは、「[Power BI Desktop の DirectQuery](desktop-use-directquery.md)」をご覧ください。 AAD SSO は DirectQuery にのみ対応していることにご注意ください。

![[インポート] ラジオ ボタンが選択されていることを示す、[Snowflake] ダイアログのスクリーンショット。](media/desktop-connect-snowflake/connect-snowflake-3.png)

プロンプトが表示されたら、ユーザー名とパスワードを入力します。

![[ユーザー名] と [パスワード] のフィールドを示す、Snowflake の資格情報プロンプトのスクリーンショット。](media/desktop-connect-snowflake/connect-snowflake-4.png)

> [!NOTE]
> 特定の **Snowflake** サーバーのユーザー名とパスワードを入力すると、Power BI Desktop は以降もその資格情報を使用して接続を試みます。 これらの資格情報を変更するには、 **[ファイル]、[オプションと設定]、[データ ソース設定]** の順に移動します。
> 
> 

Microsoft アカウント オプションを使用する場合、Snowflake 側で Snowflake AAD 統合を構成する必要があります。 これを行うには、[こちらのトピック](https://docs.snowflake.net/manuals/user-guide/oauth-powerbi.html#power-bi-sso-to-snowflake)の Snowflake ドキュメントの「Getting Started」 (はじめに) セクションをお読みください。

![Snowflake コネクタでの Microsoft アカウントの認証の種類。](media/desktop-connect-snowflake/connect-snowflake-6.png)


接続が正常に行われたら、 **[ナビゲーター]** ウィンドウが開き、サーバー上で使用可能なデータが表示されます。その中から 1 つまたは複数の要素を選択し、**Power BI Desktop** にインポートして使用することができます。

![ODBC エラー 28000 により発生した接続エラー。](media/desktop-connect-snowflake/connect-snowflake-5.png)

選択したテーブルを **読み込んで**、テーブル全体を **Power BI Desktop** に取り込むことができます。またはクエリを **編集** して **クエリ エディター** を開き、使用するデータのセットをフィルターし、絞り込んでから、その絞り込んだデータのセットを **Power BI Desktop** に取り込むこともできます。

## <a name="custom-roles"></a>カスタム ロール

現在のところ、Snowflake コネクタの "カスタム役割" は基本認証でのみ機能します。 これは近い将来、解決される予定です。

## <a name="next-steps"></a>次のステップ
Power BI Desktop を使用して接続できるデータの種類は他にもあります。 データ ソースの詳細については、次のリソースを参照してください。

* [Power BI Desktop とは何ですか?](../fundamentals/desktop-what-is-desktop.md)
* [Power BI Desktop のデータ ソース](desktop-data-sources.md)
* [Power BI Desktop でのデータの整形と結合](desktop-shape-and-combine-data.md)
* [Power BI Desktop で Excel ブックに接続する](desktop-connect-excel.md)   
* [Power BI Desktop にデータを直接入力する](desktop-enter-data-directly-into-desktop.md)   
