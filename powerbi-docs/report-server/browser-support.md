---
title: Power BI レポート サーバーのブラウザーのサポート
description: Power BI レポート サーバーとレポート ビューアー コントロールで管理および表示するためにサポートされているブラウザーのバージョンについて説明します。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 01/21/2021
ms.openlocfilehash: 71ee66c6cd531a35a53a3263feaf94115b528114
ms.sourcegitcommit: 77912d4f6ef2a2b1ef8ffccc50691fe5b38ee97a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2021
ms.locfileid: "98687490"
---
# <a name="browser-support-for-power-bi-report-server"></a>Power BI レポート サーバーのブラウザーのサポート
Power BI レポート サーバーとレポート ビューアー コントロールで管理および表示するためにサポートされているブラウザーのバージョンについて説明します。

> [!NOTE]
> Microsoft Edge レガシ ブラウザーのサポートは 2021 年 3 月 9 日から停止されます。Microsoft Internet Explorer 11 のサポートは 2021 年 8 月 17 日から停止されます。

## <a name="browser-requirements-for-the-web-portal"></a>Web ポータルのブラウザーの要件
次は、Web ポータルでサポートされているブラウザーの現行リストです。

**Microsoft Windows**  
*Windows 7、8.1、10、Windows Server 2008 R2、2012、2012 R2*

* Microsoft Edge (+)
* Microsoft Internet Explorer 11
* Google Chrome (+)
* Mozilla Firefox (+)

**Apple OS X**  
*OS X 10.9-10.11*

* Apple Safari (+)
* Google Chrome (+)
* Mozilla Firefox (+)

**Apple iOS**  
*iOS 10 の iPhone と iPad*

* Apple Safari (+)

**Google Android**  
*Android 4.4 (KitKat) 以降を内蔵したスマートフォンまたはタブレット*

* Google Chrome (+)
  
  **(+)** 最新公開リリース バージョン

## <a name="browser-requirements-for-the-report-viewer-web-control-2015"></a>レポート ビューアー Web コントロール (2015) のブラウザー要件
レポート ビューアー Web コントロールでサポートされるブラウザーの最新の一覧を次に示します。 レポート ビューアーでは、Web ポータルからのレポートの表示をサポートします。

**Microsoft Windows**  
*Windows 7、8.1、10、Windows Server 2008 R2、2012、2012 R2*

* Microsoft Edge (+)
* Microsoft Internet Explorer 11
* Google Chrome (+)
* Mozilla Firefox (+)

**Apple OS X**  
*OS X 10.9-10.11*

* Apple Safari (+)
  
  **(+)** 最新公開リリース バージョン

### <a name="authentication-requirements"></a>認証の要件
クライアント要求が正常に終了するように、ブラウザーでは、レポート サーバーで処理する必要がある特定の認証方法をサポートしています。 次の表は、Windows オペレーティング システムで実行中の各ブラウザーでサポートされる既定の認証の種類を示しています。

| **ブラウザーの種類** | **サポート** | **ブラウザーの既定値** | **サーバーの既定値** |
| --- | --- | --- | --- |
| **Microsoft Edge** (+) |ネゴシエート、Kerberos、NTLM、基本 |ネゴシエート |はい。 Edge の既定の認証設定を使用します。 |
| **[Microsoft Internet Explorer]** |ネゴシエート、Kerberos、NTLM、基本 |ネゴシエート |はい。 Internet Explorer の既定の認証設定を使用します。 |
| **Google Chrome**(+) |ネゴシエート、NTLM、基本 |ネゴシエート |はい。 Chrome の既定の認証設定を使用します。 |
| **Mozilla Firefox**(+) |NTLM、基本 |NTLM |はい。 Firefox の既定の認証設定を使用します。 |
| **Apple Safari**(+) |NTLM、基本 |Basic |はい。 Safari の既定の認証設定を使用します。 |

 **(+)** 最新公開リリース バージョン

### <a name="script-requirements-for-viewing-reports"></a>レポートを表示するためのスクリプトの要件
レポート ビューアーを使用するには、スクリプトを実行するようにブラウザーを構成する必要があります。

スクリプトが有効になっていない場合は、レポートを開くときに次のようなエラー メッセージが表示されます。

```
Your browser does not support scripts or has been configured to not allow scripts to run. Click here to view this report without scripts
```

 スクリプトを使用せずにレポートを表示することを選択した場合、レポート ツール バーやドキュメント マップなどのレポート ビューアー機能を使用しない HTML でレポートが表示されます。

> [!NOTE]
> レポート ツール バーは HTML ビューアー コンポーネントの一部です。 既定では、ツール バーはブラウザー ウィンドウに表示されるすべてのレポートの上部に表示されます。 レポート ビューアーには、レポート内の情報検索、特定のページへのスクロール、および表示目的でのページ サイズの調整機能があります。 レポート ツール バーまたは HTML ビューアーの詳細については、「 [HTML Viewer and the Report Toolbar](/sql/reporting-services/html-viewer-and-the-report-toolbar)」を参照してください。
> 
> 

## <a name="browser-support-for-report-viewer-web-server-controls-in-visual-studio"></a>Visual Studio でのレポート ビューアー Web サーバー コントロールのブラウザー サポート
レポート ビューアー Web サーバー コントロールは、ASP.NET Web アプリケーションにレポート機能を埋め込むために使用します。 レポート ビューアー コントロールを取得する方法の詳細については、「[Integrating Reporting Services Using Report Viewer Controls - Get Started](/sql/reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls-get-started)」 (レポート ビューアー コントロールを使用して Reporting Services を統合する - はじめに) を参照してください。

スクリプトのサポートが有効になっているブラウザーを使用します。 ブラウザーがスクリプトを実行できない場合、レポートを表示することができません。

**Microsoft Windows**  
*Windows 7、8.1、10、Windows Server 2008 R2、2012、2012 R2*

* Microsoft Edge (+)
* Microsoft Internet Explorer 11
* Google Chrome (+)
* Mozilla Firefox (+)
  
  **(+)** 最新公開リリース バージョン

## <a name="next-steps"></a>次の手順
[管理者の概要](admin-handbook-overview.md)  
[Power BI レポート サーバーのインストール](install-report-server.md)  
[レポート ビルダーのダウンロード](https://www.microsoft.com/download/details.aspx?id=53613)  
[SQL Server Data Tools (SSDT) のダウンロード](/sql/ssdt/download-sql-server-data-tools-ssdt)

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
