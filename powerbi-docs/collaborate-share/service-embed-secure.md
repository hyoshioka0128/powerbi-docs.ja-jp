---
title: セキュリティで保護されたポータルまたは Web サイトにレポートを埋め込む
description: Power BI の埋め込み機能を使うと、ユーザーは簡単かつ安全に内部 Web ポータルにレポートを埋め込むことができます。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 04/27/2020
LocalizationGroup: Share your work
ms.openlocfilehash: a7f8c6d52acff8cbaaa00004448a3fae300afb9b
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411910"
---
# <a name="embed-a-report-in-a-secure-portal-or-website"></a>セキュリティで保護されたポータルまたは Web サイトにレポートを埋め込む

Power BI レポートの新しい **埋め込み** オプションを使うと、ユーザーは簡単かつ安全に内部 Web ポータルにレポートを埋め込むことができます。 ポータルは **クラウドベース** か、SharePoint 2019 など、**ホステッド オンプレミス** になります。 埋め込まれたレポートでは、[行レベルのセキュリティ (RLS)](../admin/service-admin-rls.md) を使ってすべての項目のアクセス許可とデータのセキュリティが守られます。 URL または iFrame の埋め込みを受け取るあらゆるポータルにノーコードで埋め込むことができます。 

**[埋め込み]** オプションでは [URL フィルター](service-url-filters.md)と URL 設定がサポートされています。 HTML と JavaScript の基本的な知識のみを必要とする、コードの少ない手法でポータルと統合できます。

## <a name="how-to-embed-power-bi-reports-into-portals"></a>Power BI レポートをポータルに埋め込む方法

1. Power BI サービスで、レポートを開きます。

2. **[その他のオプション (...)]** メニューで、 **[埋め込む]**  >   **[Web サイトまたはポータル]** の順に選択します。

    ![[Web サイトまたはポータル] オプション](media/service-embed-secure/power-bi-more-options-website.png)

2. **[埋め込む]** オプションを選択するとダイアログが開きますが、そのダイアログにはレポートを安全に埋め込む目的で利用できる iFrame とリンクがあります。

    ![[埋め込む] オプションのダイアログ ボックス](media/service-embed-secure/secure-embed-code-dialog.png)

3. ユーザーがレポート URL を直接開くか、Web ポータルに埋め込まれているものを開くかに関係なく、レポートにアクセスするとき、認証が要求されます。 次の画面は、ユーザーがブラウザー セッションで Power BI にサインインしていない場合に表示されます。 **[サインイン]** を選択すると、新しいブラウザー ウィンドウまたはタブが開くことがあります。 サインインが求められない場合、ポップアップをブロックしていないか確認してもらいます。

    ![サインインしてこのレポートを表示する](media/service-embed-secure/secure-embed-sign-in.png)

4. ユーザーがサインインすると、レポートが開き、データが表示され、ページ ナビゲーションとフィルター設定が許可されます。 Power BI でレポートを表示できるのは、表示権限を持つユーザーだけです。 [行レベルのセキュリティ (RLS)](../admin/service-admin-rls.md) 規則もすべて適用されます。 最後に、ユーザーに正しいライセンスが与えられている必要があります – Power BI Pro ライセンスが必要であるか、またはレポートが Power BI Premium 容量内にあるワークスペースに置かれている必要があります。 ユーザーは、新しいブラウザー ウィンドウを開くたびにサインインする必要があります。 ただし、一度サインインすると、他のレポートは自動的に読み込まれます。

    ![レポートを埋め込む](media/service-embed-secure/secure-embed-report.png)

5. iFrame を使用するとき、場合によっては、ポータルの Web ページに収まるように **高さ** と **幅** を編集する必要があります。

    ![高さと幅を設定する](media/service-embed-secure/secure-embed-size.png)

## <a name="granting-report-access"></a>レポート アクセス権の付与

**[埋め込む]** オプションによって、ユーザーがレポートを表示することが自動的に許可されるわけではありません。 表示権限は Power BI サービスで設定されます。

Power BI サービスでは、アクセスを必要とするユーザーと埋め込みレポートを共有できます。 Microsoft 365 グループを使用している場合、ワークスペースのメンバーとしてユーザーを指定できます。 詳細については、「[Power BI と Microsoft 365 でワークスペースを管理する](service-manage-app-workspace-in-power-bi-and-office-365.md)」をご覧ください。

## <a name="licensing"></a>ライセンス

埋め込まれたレポートをユーザーが表示するには、Power BI Pro ライセンスが必要です。あるいは、コンテンツを [Power BI Premium 容量 (EM または P SKU)](../admin/service-admin-premium-purchase.md) 内のワークスペースに置く必要があります。

## <a name="customize-your-embed-experience-using-url-settings"></a>URL 設定を使って埋め込みエクスペリエンスをカスタマイズする

埋め込み URL の入力設定を使用し、ユーザー エクスペリエンスをカスタマイズできます。 指定の iFrame では、URL の **src** 設定を更新できます。

| プロパティ  | Description  |
|-----------|--------------|
| pageName  | **pageName** クエリ文字列パラメーターを使用し、開くレポート ページを設定します。 次に示すように、この値は、Power BI サービスでレポートを表示するとき、レポートの URL の終わりにあります。 |
| URL フィルター  | Power BI UI から受け取った埋め込み URL の [URL フィルター](service-url-filters.md)を使用し、埋め込みコンテンツをフィルター処理できます。 この方法では、基本的な HTML および JavaScript エクスペリエンスのみとのローコードの統合を構築できます。  |

## <a name="set-which-page-opens-for-an-embedded-report"></a>埋め込まれたレポートに対して開くページを設定する 

**pageName** 値は、Power BI サービスでレポートを表示するとき、レポートの URL の終わりにあります。

1. Web ブラウザーで Power BI サービスからレポートを開き、アドレス バーの URL をコピーします。

    ![レポート セクション](media/service-embed-secure/secure-embed-report-section.png)

2. **pageName** 設定を URL に追加します。

    ![pageName を追加する](media/service-embed-secure/secure-embed-append-page-name.png)

## <a name="filter-report-content-using-url-filters"></a>URL フィルターを使ってレポートの内容をフィルター処理する 

[URL フィルター](service-url-filters.md)を使用し、さまざまなレポート ビューを提供できます。 たとえば、以下の URL では、レポートをフィルター処理してエネルギー業界のデータを表示します。

**pageName** と [URL フィルター](service-url-filters.md)を組み合わせて使うと強力です。 基本的な HTML と JavaScript を使ってエクスペリエンスを構築できます。

たとえば、次のようなボタンを HTML ページに追加できます。

```html
<button class="textLarge" onclick='show("ReportSection", "Energy");' style="display: inline-block;">Show Energy</button>
```

ボタンを選択すると、関数が呼び出され、エネルギー業界のフィルターを含む更新後の URL で iFrame が更新されます。

```javascript
function show(pageName, filterValue)

{

var newUrl = baseUrl + "&pageName=" + pageName;

if(null != filterValue && "" != filterValue)

{

newUrl += "&$filter=Industries/Industry eq '" + filterValue + "'";

}

//Assumes there's an iFrame on the page with id="iFrame"

var report = document.getElementById("iFrame")

report.src = newUrl;

}
```

![フィルター](media/service-embed-secure/secure-embed-filter.png)

ボタンを好きなだけ追加して、ローコードのカスタム エクスペリエンスを作成できます。 

## <a name="considerations-and-limitations"></a>考慮事項と制限事項

* ページ分割されたレポートはセキュリティで保護された埋め込みシナリオでサポートされています。URL パラメーターを使用したページ分割されたレポートもサポートされています。 詳細については、[ページ分割されたレポートの URL でレポート パラメーターを渡す方法](../paginated-reports/report-builder-url-pass-parameters.md)に関するページを参照してください。

* セキュリティで保護された埋め込みは Power BI サービスに公開されたレポートに対して機能します。

* ユーザーは、新しいブラウザー ウィンドウを開くたびに、サインインしてレポートを表示する必要があります。

* 一部のブラウザーでは、サインイン後にページを更新する必要があります (特に InPrivate または Incognito モードを使っている場合)。

* サポートされていないブラウザー バージョンを使用すると、問題が発生する可能性があります。 Power BI は、[次の一覧のブラウザー](../fundamentals/power-bi-browsers.md)をサポートしています。

* クラシック SharePoint Server はサポートされていません。11 より前の Internet Explorer バージョンが必要か、互換表示モードを有効にする必要があるためです。

* シングル サインオンを実現するために、[[SharePoint Online に埋め込む]](service-embed-report-spo.md) オプションを使用するか、[ユーザー所有データ](../developer/embedded/embed-sample-for-your-organization.md)という埋め込み方法でカスタムの統合を構築します。 

* **[埋め込む]** オプションを使って提供される自動認証機能は、Power BI JavaScript API では動作しません。 Power BI JavaScript API の場合、[ユーザー所有データ](../developer/embedded/embed-sample-for-your-organization.md)という埋め込み方法を使用します。 

* 認証トークンの有効期間は AAD 設定に基づいて制御されます。 認証トークンの有効期限が切れると、ユーザーはブラウザーを更新し、更新された認証トークンを取得する必要があります。 既定の有効期間は 1 時間ですが、組織によってはこれより短くなることも、長くなることもあります。  このシナリオでは、トークンを自動的に更新することはできません。

## <a name="next-steps"></a>次の手順

* [Power BI で作業を共有する方法](service-how-to-collaborate-distribute-dashboards-reports.md)

* [URL のクエリ文字列パラメーターを使用してレポートをフィルター処理する](service-url-filters.md)

* [SharePoint Online にレポート Web パーツを埋め込む](service-embed-report-spo.md)

* [Power BI から Web への公開](service-publish-to-web.md)
