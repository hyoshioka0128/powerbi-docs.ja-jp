---
title: Power BI モバイル アプリの特定の場所へのリンクを作成する
description: URI (Uniform Resource Identifier) で Power BI モバイル アプリの特定のダッシュボード、タイル、またはレポートへのディープ リンクを作成する方法について説明します。
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 11/16/2020
ms.openlocfilehash: 1c2260fdc3df201a655e6641c351319e366eac6b
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96413129"
---
# <a name="create-a-link-to-a-specific-location-in-the-power-bi-mobile-apps"></a>Power BI モバイル アプリの特定の場所へのリンクを作成する
リンクを使用して、特定のレポート、レポート ページ、ダッシュボード、タイルなどの特定の Power BI コンテンツに直接アクセスできます。

リンクを使用して Power BI モバイル アプリのコンテンツにアクセスするには、主に次の 2 つのシナリオがあります。 

* **モバイル アプリの外部** から Power BI を開き、特定のコンテンツにアクセスするため。 これは通常、別のアプリから Power BI モバイル アプリを開いている統合シナリオです。 
* Power BI 内で **移動** するため。 これは通常、Power BI でカスタム ナビゲーションを作成する場合に行います。

この記事では、以下の場合について説明します。
* リンクを使用して、モバイル アプリの外部から特定の Power BI コンテンツを開きます。 2 つのリンク形式が紹介されています。 1 つはリダイレクト メソッドを使用するもので、Power BI をどこで開くかに関係なく使用できます。 もう 1 つは Power BI モバイル アプリで直接開き、モバイル アプリがインストールされているモバイル デバイスでのみ機能します。
* Power BI 内のリンクを使用して、特定の Power BI コンテンツに移動します。

## <a name="use-links-from-outside-the-mobile-app"></a>モバイル アプリの外部からリンクを使用する
モバイル アプリの外部から Power BI の特定の項目にリンクする場合は、リンクを開く場所に応じて、次の 2 つのオプションがあります。

* コンピューター ブラウザーとモバイル デバイスのどちらでクリックされてもリンクが正しく開くようにするには、クリックされた場所に関係なく確実に正しく開くリンクを作成できます。 このリンクには、このスマート動作を可能にする特別なリダイレクト構文が含まれます。

* Power BI モバイル アプリがインストールされているモバイル デバイスでのみリンクが開くことがわかっている場合は、上記の方法のリダイレクト オーバーヘッドを回避し、モバイル デバイスの Power BI モバイル アプリで直接リンクを開く別のリンク構文を使用できます。 ただし、このリンクを使用すると、最初の方法のリダイレクト オーバーヘッドが回避されますが、Power BI モバイル アプリがインストールされているモバイル デバイス以外の場所で開かれた場合は動作しません。

### <a name="create-a-link-that-works-anywhere"></a>あらゆる場所で動作するリンクを作成する
このセクションで説明するリンク形式では、リダイレクトを使用して、リンクがクリックされた場所に関係なく動作するようにします。
* モバイル デバイスでリンクがクリックされた場合は、デバイスで Power BI モバイル アプリを使用して確実にリンクが開かれます。 デバイスにモバイル アプリがインストールされていない場合は、ユーザーに対して、ストアに移動して取得するように提案されます。
* PC でリンクがクリックされると、関連する項目が Power BI Web ポータルに表示されます。

リンクは、先頭に特別なプレフィックス、その後にクエリ パラメーターを指定する必要があります。

https<nolink>://app.powerbi.com/Redirect? **[QUERYPARAMETERS]** </code>

> [!IMPORTANT]
> コンテンツが政府、中国などの特別なデータセンターでホストされている場合、リンクの先頭は該当する Power BI アドレス (**app.powerbigov.us** や **app.powerbi.cn** など) である必要があります。

クエリ パラメーターは次のとおりです。

|パラメーター  | 値  | 説明 |
|---------|---------|---------|
|**action** (必須)    | OpenApp<br>OpenReport<br>OpenDashboard<br>OpenTile | |
|**appId**| 36 文字の GUID | アプリに含まれているレポートまたはダッシュボードを開く場合に指定する必要があります。<br>例: **appId=baf4b16d-b5bd-4360-8a3a-51d11242c09b** |
|**groupObjectId**| 36 文字の GUID | マイ ワークスペースに含まれていないレポートまたはダッシュボードを開く場合にワークスペースを指定します。<br>例: **groupObjectId=9a3841c6-74b3-46f1-85fd-bdd78f27b30e** |
| **dashboardObjectId** | 36 文字の GUID | ダッシュボード オブジェクト ID (action が OpenDashboard または OpenTile の場合)。<br>例: **dashboardObjectId=033bb049-5b68-4392-b3ef-ae9a43738a4a** |
| **reportObjectId** | 36 文字の GUID | レポート オブジェクト ID (action が OpenReport の場合)。<br>例: **reportObjectId=6114cec7-78e1-4926-88ff-0bc5338452cf** |
| **tileObjectId** | 36 文字の GUID | タイル オブジェクト ID (action が OpenTile の場合)。<br>例: **tileObjectId=a845dcb8-a289-43a8-94ea-67a8c0a068f9** |
| **reportPage** | ReportSection&lt;num&gt; | 特定のレポート ページを開く場合、ページ名 (action が OpenReport の場合)。<br>例: **reportPage=ReportSection6**  |
| **bookmarkGuid** | 36 文字の GUID | 特定のブックマーク付きビューを開く場合、ブックマーク ID (action が OpenReport の場合)。<br>例: **bookmarkGuid=18e8872f-6db8-4cf8-8298-3b2ab254cc7f** |
| **ctid** | 36 文字の GUID | 項目の編成 ID (B2B シナリオ関連。 ユーザーの組織に項目が属する場合、これは省略できます)。<br>例: **ctid=5367c770-09d0-4110-bf6a-d760cb5ef681** |
||||

**例:**

次の例では、パラメーター値のプレースホルダーが太字で強調表示されています。 実際の値を取得するには、Power BI サービスに移動し、リンク先となる項目を開いて、項目の URL から必要な値を抽出します。

* **アプリを開く**

    https<nolink>://app.powerbi.com/Redirect?action=OpenApp&appId= **&lt;appid-guid&gt;** &ctid= **&lt;ctid-guid&gt;**
   
* **アプリに含まれるダッシュボードを開く**

    https<nolink>://app.powerbi.com/Redirect?action=OpenDashboard&appId= **&lt;appid-guid&gt;** &dashboardObjectId= **&lt;dashboardid-guid&gt;** &ctid= **&lt;ctid-guid&gt;**

* **マイ ワークスペース以外のワークスペースに含まれているレポートを開く**

    https<nolink>://app.powerbi.com/Redirect?Action=OpenReport&reportObjectId= **&lt;reportid-guid&gt;** &groupObjectId= **&lt;groupobjectid-guid&gt;** &reportPage=**ReportSection&lt;num&gt;**

### <a name="how-to-get-the-correct-link-format"></a>正しいリンク形式を取得する方法

#### <a name="links-to-apps-and-items-in-apps"></a>アプリに含まれるアプリおよび項目のリンク

**アプリに含まれるアプリ、レポート、ダッシュボード** については、リンクを取得する最も簡単な方法はアプリ ワークスペースに移動し、"**アプリを更新**" を選択します。 これにより、"アプリの発行" エクスペリエンスが開きます。 アクセス許可タブを開き、リンク セクションを展開して、アプリとそのすべてのコンテンツへのリンクを表示します。 外部 Power BI からこれらのリンクを使用して、アプリとそのコンテンツに直接アクセスできます。

![Power BI でアプリ リンクを発行する ](./media/mobile-apps-links/mobile-link-copy-app-links.png)

#### <a name="links-to-items-that-are-not-in-an-app"></a>アプリに含まれていない項目のリンク 

アプリに含まれていないレポートやダッシュボードの場合は、項目の URL から必要なオブジェクト ID を抽出する必要があります。 これを行うには、Power BI サービスに移動し、リンク先となる項目に移動して、ブラウザーのアドレス バーに表示される URL に必要な値を見つけます。

次の例では、リンク先となる項目の URL に必要な ID が見つかる場所を示します。

* 36 文字のダッシュボード オブジェクト ID を見つけるには、Power BI サービスでリンク先となる特定のダッシュボードに移動し、次に示す場所で、ダッシュボード オブジェクト ID およびその他の必要な ID を見つけます。

    https<nolink>://app.powerbi.com/groups/me/dashboards/ **&lt;dashboard-object-id&gt;** ?ctid= **&lt;org-object-id&gt;**

* 36 文字のレポート オブジェクト ID を見つけるには、Power BI サービスでリンク先となる特定のレポートに移動し、次に示すように必要な ID を見つけます。 この例には、特定のレポート ページと特定のブックマークへの参照が含まれています。

    https<nolink>://app.powerbi.com/groups/me/reports/ **&lt;report-object-id&gt;** /**ReportSection&lt;num&gt;** ?bookmarkGuid= **&lt;bookmark-id&gt;**

* マイ ワークスペース以外のワークスペースの項目にリンクするには、グループ オブジェクト ID を抽出する必要があります。 この例では、マイ ワークスペース以外のワークスペースのレポートを示します。

    https<nolink>://app.powerbi.com/groups/ **&lt;group-object-id&gt;** /reports/ **&lt;report-object-id&gt;** /**ReportSection&lt;report-section-num&gt;** ?ctid= **&lt;org-object-id&gt;**

### <a name="create-a-link-that-opens-only-on-a-device-that-has-the-power-bi-mobile-app-installed"></a>Power BI モバイル アプリがインストールされているデバイスでのみ開くリンクを作成する

このセクションで説明するリンク形式は、すべてのモバイル プラットフォーム (iOS、Android デバイス、Windows 10) 上の Power BI モバイル アプリ内の特定の場所にリンクされます。 このリンク形式では、前のセクションで説明した方法に関与しているリダイレクトを使用せずに、場所が直接開きます。 **この形式は、Power BI モバイル アプリがインストールされているモバイル デバイスでのみ開くことができます**。

この形式のリンクを使用して、ダッシュボード、タイル、レポートを直接参照できます。 ディープ リンクのリンク先により、その形式が決まります。 異なる場所へのディープ リンクを作成するには、次の手順のようにします。 

* **Power BI モバイル アプリを開く**

    任意のデバイスで Power BI モバイル アプリを開くには、次のリンクを使用します。

    mspbi://app/

* **特定のダッシュボードを開く**

    Power BI モバイル アプリの特定のダッシュボードを開くには、次のリンクを使用します。

    mspbi://app/OpenDashboard?DashboardObjectId= **<36-character-dashboard-id>**

    36 文字のダッシュボード オブジェクト ID を取得するには、Power BI サービスで特定のダッシュボードに移動し、URL から抽出します。 たとえば、Power BI サービスの次の URL では、ダッシュボード オブジェクト ID が強調表示されています。

    https<nolink>://app.powerbi.com/groups/me/dashboards/ **&lt;61b7e871-cb98-48ed-bddc-6572c921e270&gt;**

    ダッシュボードがマイ ワークスペースに含まれていない場合は、ダッシュボード ID の前または後に、グループ オブジェクト ID も追加する必要があります。 次に示すディープ リンクには、ダッシュボード オブジェクト ID の後にグループ オブジェクト ID パラメーターが追加されています。

    mspbi://app/OpenDashboard?DashboardObjectId=**e684af3a-9e7f-44ee-b679-b9a1c59b5d60**&GroupObjectId=**8cc900cc-7339-467f-8900-fec82d748248**</code>

    2 つのパラメーター間のアンパサンド (&) に注意してください。

* **特定のタイルにフォーカスを設定して開く**

    Power BI モバイル アプリの特定のタイルにフォーカス モードを設定して開くには、次のリンクを使用します。

    mspbi://app/OpenTile?DashboardObjectId= **<36-character-dashboard-id>** &TileObjectId= **<36-character-tile-id>**

    ダッシュボードとタイルの 36 文字のオブジェクト ID を見つけるには、Power BI サービスで特定のダッシュボードに移動し、フォーカス モードでタイルを開きます。 次の例では、ダッシュボードとタイル ID が強調表示されています。

    https<nolink>://app.powerbi.com/groups/me/dashboards/**3784f99f-b460-4d5e-b86c-b6d8f7ec54b7**/tiles/**565f9740-5131-4648-87f2-f79c4cf9c5f5**/infocus

    このタイルを直接開くには、リンクは次のようになります。

    mspbi://app/OpenTile?DashboardObjectId=3784f99f-b460-4d5e-b86c-b6d8f7ec54b7&TileObjectId=565f9740-5131-4648-87f2-f79c4cf9c5f5

    2 つのパラメーター間のアンパサンド (&) に注意してください。

    ダッシュボードがマイ ワークスペースに含まれていない場合は、GroupObjectId パラメーターを追加します (例: &GroupObjectId=<36-character-group-id>)。

* **特定のレポートを開く**

    Power BI モバイル アプリの特定のレポートを開くには、次のリンクを使用します。

    mspbi://app/OpenReport?ReportObjectId= **<36-character-report-id>**

    36 文字のレポート オブジェクト ID を見つけるには、Power BI サービスでその特定のレポートに移動します。 Power BI サービスの次の URL は、抽出する必要があるレポート ID を示しています。

    https<nolink>://app.powerbi.com/groups/me/reports/**df9f0e94-31df-450b-b97f-4461a7e4d300**

    レポートがマイ ワークスペースに含まれていない場合は、レポート ID の前または後に **&GroupObjectId=<36-character-group-id>** も追加する必要があります。 たとえば、この例ではディープ リンクは次のようになります。

    mspbi://app/OpenReport?ReportObjectId=**e684af3a-9e7f-44ee-b679-b9a1c59b5d60**&GroupObjectId=**8cc900cc-7339-467f-8900-fec82d748248**

    2 つのパラメーター間のアンパサンド (&) に注意してください。

* **特定のレポート ページを開く**

    Power BI モバイル アプリの特定のレポート ページを開くには、次のリンクを使用します。

    mspbi://app/OpenReport?ReportObjectId= **<36-character-report-id>** &reportPage=**ReportSection&lt;number&gt;**

    レポート ページを呼び出すには、**ReportSection** に続けて番号を指定します。 ここでも、必要な値を確認するには、Power BI サービスでレポートを開き、特定のレポート ページに移動して、URL から必要な値を抽出します。 たとえば、この URL の強調表示されたセクションは、特定のレポート ページを開くために必要な値を表します。

    https<nolink>://app.powerbi.com/groups/me/reports/**df9f0e94-31df-450b-b97f-4461a7e4d300**/**ReportSection11**</code>

* **全画面表示モードで開く (Windows デバイスのみ)**

    Windows デバイスの場合は、**openFullScreen** パラメーターを追加して、特定のレポートを全画面表示モードで開くこともできます。 次の例では、レポート ページを全画面表示モードで開きます。

    mspbi://app/OpenReport?ReportObjectId=500217de-50f0-4af1-b345-b81027224033&**openFullScreen=true**

* **コンテキストを追加する** (省略可能)

    文字列にコンテキストを追加することもできます。 Microsoft へお問い合わせになる場合は、Microsoft はそのコンテキストを使用してデータをフィルター処理し、お客様のアプリに関連する内容を見つけることができます。 コンテキストを追加するには、パラメーター **context=&lt;app-name&gt;** をリンクに追加します。

    たとえば、次の例は、コンテキスト パラメーターを含むリンクを示しています。 

    mspbi://app/OpenReport?ReportObjectId=**e684af3a-9e7f-44ee-b679-b9a1c59b5d60**&GroupObjectId=**8cc900cc-7339-467f-8900-fec82d748248**&**context=SlackDeepLink**

## <a name="use-links-inside-power-bi"></a>Power BI 内でリンクを使用する

Power BI モバイル アプリでは、Power BI 内のリンクは Power BI サービスで動作する場合と同じように動作します。

別の Power BI 項目を指すレポートにリンクを追加する場合は、ブラウザーのアドレス バーからその項目の URL をコピーします。 レポートのテキスト ボックスにハイパーリンクを追加する方法については[こちら](https://docs.microsoft.com/power-bi/service-add-hyperlink-to-text-box)をご覧ください。

## <a name="next-steps"></a>次のステップ
Power BI モバイル アプリで使用したいその他の機能にぜひ投票してください。お客様からのフィードバックは、将来実装する機能を決めるのに役立ちます。 

* [モバイル デバイス用の Power BI アプリ](mobile-apps-for-mobile-devices.md)
* Twitter で @MSPowerBI をフォローする
* [Power BI コミュニティの会話](http://community.powerbi.com/)に参加する
* [Power BI とは?](../../power-bi-overview.md)
