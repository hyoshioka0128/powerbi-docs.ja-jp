---
title: Power BI Desktop で Analysis Services の表形式データに接続する
description: Power BI Desktop では、ライブ接続を使用するか、項目を選択して Power BI Desktop にインポートするという方法で SQL Server Analysis Services 表形式モデルに接続し、データを取得できます。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 01/28/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 6c31079bc0ad517a1b2bb37f8da0c0ed5240595f
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411519"
---
# <a name="connect-to-analysis-services-tabular-data-in-power-bi-desktop"></a>Power BI Desktop で Analysis Services の表形式データに接続する
Power BI Desktop では、2 つの方法で SQL Server Analysis Services 表形式モデルに接続し、データを取得することができます。ライブ接続を使用するか、項目を選択して Power BI Desktop にインポートして探索してみてください。

詳しく見てみましょう。

**ライブ接続を使って探索する**:ライブ接続を使用するとき、テーブル、列、メジャーなどの表形式モデルやパースペクティブに含まれる項目が Power BI Desktop の **[フィールド]** ウィンドウ一覧に表示されます。 Power BI Desktop の高度な視覚化とレポート ツールを使用して、新しい高度な対話型方式で表形式モデルを探索することができます。

ライブ接続しているときは、表形式モデルのデータが Power BI Desktop にインポートされることはありません。 視覚化と対話するたびに、Power BI Desktop によって表形式モデルが照会され、表示結果が計算されます。 最後の処理時間から、または表形式モデルで使用できる DirectQuery テーブルから、表形式モデルで利用できる最新データを常に確認できます。 

なお、表形式モデルは高度なセキュリティを備えています。 Power BI Desktop に表示される項目は、接続している表形式モデルに対するユーザーのアクセス許可によって異なります。

Power BI Desktop で動的なレポートを作成したら、Power BI サイトに発行してレポートを共有することができます。 表形式モデルにライブ接続して Power BI Desktop ファイルを Power BI サイトに発行するとき、管理者がオンプレミス データ ゲートウェイをインストールし、構成する必要があります。 詳細については、「[オンプレミス データ ゲートウェイ](service-gateway-onprem.md)」をご覧ください。

**項目を選択し、Power BI Desktop にインポートする**:このオプションで接続すると、表形式モデルまたはパースペクティブのテーブル、列、メジャーなどの項目を選択し、それらを Power BI Desktop モデルに読み込むことができます。 Power BI Desktop の Power Query エディターを使用し、必要なものとそれをモデル化する特徴をさらに形作り、データをさらにモデル化します。 Power BI Desktop と表形式モデルの間にはライブ接続が維持されないため、Power BI Desktop モデルをオフラインで探索したり、Power BI サイトに発行したりできます。

## <a name="to-connect-to-a-tabular-model"></a>表形式モデルに接続するには
1. Power BI Desktop の **[ホーム]** タブで、 **[データの取得]** 、 **[詳細]** 、 **[データベース]** の順に選択します。
   
1. **[SQL Server Analysis Services データベース]** を選択し、 **[接続]** を選択します。
   
   ![[SQL Server Analysis Services データベース] を選択する](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata_as.png)
3. **[SQL Server Analysis Services データベース]** ウィンドウで **[サーバー]** 名を入力し、接続モードを選択し、 **[OK]** を選択します。
   
   ![[SQL Server Analysis Services データベース] ウィンドウ](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata_as_server.png)
4. **[ナビゲーター]** ウィンドウのこの手順は、選択した接続モードによって異なります。

   - ライブ接続している場合は、表形式モデルまたはパースペクティブを選択します。
  
      ![[ナビゲーター] で表形式モデルまたはパースペクティブを選択する](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata_as_live.png)
   - 項目を選択し、データを取得する場合、表形式モデルかパースペクティブを選択し、読み込む特定の表か列を選択します。 読み込む前にデータの形を変更するには、 **[クエリを編集]** を選択して Power Query エディターを開きます。 準備ができたら、 **[読み込み]** を選択して Power BI Desktop にデータをインポートします。

      ![[ナビゲーター] で読み込む表か列を選択する](media/desktop-analysis-services-tabular-data/pbid_sqlas_getdata_as_select.png)

## <a name="frequently-asked-questions"></a>よく寄せられる質問
**質問:** オンプレミス データ ゲートウェイが必要ですか?

**回答:** 場合によって異なります。 Power BI Desktop を使用して表形式モデルにライブ接続していても、Power BI サイトに発行するつもりがないなら、ゲートウェイは必要ありません。 一方、Power BI サイトに発行する予定がある場合、Power BI サービスとオンプレミスの Analysis Services サーバー間の安全な通信を確保するために、データ ゲートウェイが必要です。 データ ゲートウェイをインストールする前に、必ず Analysis Services サーバー管理者に相談してください。

項目を選択してデータを取得する場合、Power BI Desktop ファイルに表形式モデルのデータを直接インポートするため、ゲートウェイは必要ありません。

**質問:** Power BI サービスから表形式モデルにライブ接続する場合と、Power BI Desktop からライブ接続する場合の違いは何ですか?

**回答:** Power BI サービス内のサイトから組織の設備内にある Analysis Services データベースの表形式モデルにライブ接続するとき、両者間の通信をセキュリティで保護するためにオンプレミス データ ゲートウェイが必要になります。 Power BI Desktop から表形式モデルにライブ接続する場合、Power BI Desktop と接続先の Analysis Services サーバーはいずれも組織の設備内で動作しているため、ゲートウェイは必要ありません。 ただし、Power BI Desktop ファイルを Power BI サイトに発行する場合、ゲートウェイが必要です。

**質問:** ライブ接続を作成したら、同じ Power BI Desktop ファイル内の別のデータ ソースに接続できますか?

**回答:** いいえ。 ライブ データを探索したり、同じファイルでも別の種類のデータ ソースに接続したりすることはできません。 既にデータをインポートしているか、Power BI Desktop ファイル内の別のデータ ソースに接続している場合、ライブで探索するには、新しいファイルを作成する必要があります。

**質問:** ライブ接続を作成したら、Power BI Desktop でモデルやクエリを編集できますか?

**回答:** Power BI Desktop でレポート レベル メジャーを作成できますが、その他のクエリおよびモデル化機能はすべて、ライブ データの探索中は無効になっています。

**質問:** ライブ接続を作成しましたが、セキュリティで保護されていますか。

**回答:** はい。 現在の Windows 資格情報が、Analysis Services サーバーへの接続に使用されます。 ライブでいろいろ試すとき、Power BI サービスでも Power BI Desktop でも、基本資格情報や保存された資格情報は使用できません。

**質問:** ナビゲーターに、モデルとパースペクティブが表示されています。 違いは何ですか?

**回答:** パースペクティブは、表形式モデルの特定のビューです。 固有のデータ分析のニーズに応じて、特定のテーブル、列、またはメジャーのみが含まれています。 表形式モデルには、常に 1 つ以上のパースペクティブがあり、それにはモデル内のすべてを含めることができます。 選択すべきパースペクティブがわからない場合、管理者に確認してください。

**質問:** Power BI の動作方法を変更する Analysis Services の機能はありますか?

**回答:** はい。 テーブル モデルで使用される機能によっては、Power BI Desktop のエクスペリエンスが変わることがあります。 次に例をいくつか示します。
* モデル内のメジャーは、列の横にあるテーブルの中ではなく、 **[フィールド]** ウィンドウ リストの先頭にグループ化されて表示されることがあります。 通常どおり使用できるのでご心配なく。この方が簡単に見つけることができます。

* 表形式モデルに計算グループが定義されている場合、ビジュアルに数値フィールドを追加することにより、暗黙的に作成されるメジャーではなく、モデル メジャーとの組み合わせでのみ、その計算グループを使用できます。 モデルには、**DiscourageImplicitMeasures** フラグが手動で設定されている場合もありますが、効果は同じです。 詳細については、[Analysis Services での計算グループ](/analysis-services/tabular-models/calculation-groups#benefits)に関するページを参照してください。

## <a name="to-change-the-server-name-after-initial-connection"></a>初回接続後にサーバー名を変更するには
ライブ接続で探索する目的で Power BI Desktop ファイルを作成した後、その接続を別のサーバーに切り替えることがあります。 たとえば、開発サーバーに接続して Power BI Desktop ファイルを作成した後に、接続を実稼働サーバーに切り替えてから Power BI サービスに発行したい場合などです。

サーバー名を変更するには:

1. **[ホーム]** タブで **[クエリを編集]** を選択します。

2. **[SQL Server Analysis Services データベース]** ウィンドウで新しい **[サーバー]** 名を入力し、 **[OK]** を選択します。

   
## <a name="troubleshooting"></a>トラブルシューティング 
次の一覧には、SQL Server Analysis Services (SSAS) か Azure Analysis Services に接続したときに発生する既知の問題がすべてまとめられています。 

* **エラー:モデル スキーマを読み込むことができません**:このエラーは通常、Analysis Services に接続するユーザーに、データベースまたはモデルにアクセスする許可が与えられていないときに発生します。