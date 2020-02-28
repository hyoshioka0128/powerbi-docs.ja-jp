---
title: Power BI Desktop で Snowflake Computing ウェアハウスに接続する
description: Power BI Desktop で Snowflake Computing ウェアハウスに簡単に接続して使用する
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: e7534fd0da2039a2dafaf3ca80ee6957fa8d8754
ms.sourcegitcommit: cde65bb8b1bed1ee8cf512651afeb829ddc155de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2020
ms.locfileid: "77464303"
---
# <a name="connect-to-a-snowflake-computing-warehouse-in-power-bi-desktop"></a>Power BI Desktop で Snowflake Computing ウェアハウスに接続する
Power BI Desktop では、**Snowflake** Computing ウェアハウスに接続し、Power BI Desktop の他のデータ ソースの場合と同様に基になっているデータを使用できます。 

> [!NOTE]
> 32 ビットまたは 64 ビットのいずれかの **Power BI Desktop** のインストールに合致するアーキテクチャを使用して、**Snowflake** コネクタを使用するコンピューターに **Snowflake ODBC ドライバー**をインストールする*必要があります*。 次のリンクに従って、[適切な Snowflake ODBC ドライバーをダウンロード](https://go.microsoft.com/fwlink/?LinkID=823762)します。
> 
> 

## <a name="connect-to-a-snowflake-computing-warehouse"></a>Snowflake Computing ウェアハウスに接続する
**Snowflake** Computing ウェアハウスに接続するには、Power BI Desktop の **[ホーム]** リボンで **[データの取得]** を選択します。 左側のカテゴリから **[データベース]** を選ぶと、 **[Snowflake]** が表示されます。

![](media/desktop-connect-snowflake/connect-snowflake-2b.png)

表示された **[Snowflake]** ウィンドウ内のボックスに Snowflake Computing ウェアハウスの名前を入力するか、貼り付け、 **[OK]** をクリックします。 Power BI にデータを直接**インポート**したり、**DirectQuery** を使用したりできます。 詳しくは、「[Power BI Desktop の DirectQuery](desktop-use-directquery.md)」をご覧ください。 AAD SSO は DirectQuery にのみ対応していることにご注意ください。

![](media/desktop-connect-snowflake/connect-snowflake-3.png)

プロンプトが表示されたら、ユーザー名とパスワードを入力します。

![](media/desktop-connect-snowflake/connect-snowflake-4.png)

> [!NOTE]
> 特定の **Snowflake** サーバーのユーザー名とパスワードを入力した場合、Power BI Desktop は以降もその資格情報を使用して接続を試みます。 これらの資格情報を変更するには、 **[ファイル]、[オプションと設定]、[データ ソース設定]** の順に移動します。
> 
> 

Microsoft アカウント オプションを使用する場合、Snowflake 側で Snowflake AAD 統合を構成する必要があります。 これを行うには、[こちらのトピック](https://docs.snowflake.net/manuals/user-guide/oauth-powerbi.html#power-bi-sso-to-snowflake)の Snowflake ドキュメントの「Getting Started」 (はじめに) セクションをお読みください。

![Snowflake コネクタでの Microsoft アカウントの認証の種類。](media/desktop-connect-snowflake/connect-snowflake-6.png)


接続が正常に行われたら、 **[ナビゲーター]** ウィンドウが開き、サーバー上で使用可能なデータが表示されます。その中から 1 つまたは複数の要素を選択し、**Power BI Desktop** にインポートして使用することができます。

![ODBC エラー 28000 により発生した接続エラー。](media/desktop-connect-snowflake/connect-snowflake-5.png)

選択したテーブルを**読み込んで**、テーブル全体を **Power BI Desktop** に取り込むことができます。またはクエリを**編集**して**クエリ エディター**を開き、使用するデータのセットをフィルターし、絞り込んでから、その絞り込んだデータのセットを **Power BI Desktop** に取り込むこともできます。

## <a name="next-steps"></a>次の手順
Power BI Desktop を使用して接続できるデータの種類は他にもあります。 データ ソースの詳細については、次のリソースを参照してください。

* [Power BI Desktop とは何ですか?](desktop-what-is-desktop.md)
* [Power BI Desktop のデータ ソース](desktop-data-sources.md)
* [Power BI Desktop でのデータの整形と結合](desktop-shape-and-combine-data.md)
* [Power BI Desktop で Excel ブックに接続する](desktop-connect-excel.md)   
* [Power BI Desktop にデータを直接入力する](desktop-enter-data-directly-into-desktop.md)   

