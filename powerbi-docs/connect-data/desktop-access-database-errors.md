---
title: Power BI Desktop での Access と .XLS のインポートに関する問題を解決する
description: Power BI Desktop と Power Query での Access データベースと .XLS スプレッドシートのインポート問題を解決する
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 10/21/2019
LocalizationGroup: Troubleshooting
ms.openlocfilehash: f8d24c672fa3e9d5cda007e061eac8c4ea9c6d4c
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96406045"
---
# <a name="troubleshoot-importing-access-and-excel-xls-files-in-power-bi-desktop"></a>Power BI Desktop での Access と Excel の .xls ファイルのインポートに関するトラブルシューティング

Power BI Desktop では、Access データベースと初期バージョンの Excel ブック (Excel 97-2003 タイプの .XLS ファイル) の両方で "*Access データベース エンジン*" が使用されます。 Access データベース エンジンが正常に動作しない場合、一般的に、次の 3 つの状況が考えられます。

## <a name="situation-1-no-access-database-engine-is-installed"></a>状況 1:Access データベース エンジンがインストールされていない

Power BI Desktop のエラー メッセージで Access データベース エンジンがインストールされていないことが判明した場合、お使いの Power BI Desktop のバージョンに合わせて、32 ビット版か 64 ビット版の Access データベース エンジンをインストールする必要があります。 Access Database Engine は[ダウンロード ページ](https://www.microsoft.com/download/details.aspx?id=13255)からインストールできます。

>[!NOTE]
>インストールした Access データベース エンジンのビット版がお使いの Microsoft Office のビット版と異なる場合、Office アプリケーションで Access データベース エンジンを利用できません。

## <a name="situation-2-the-access-database-engine-bit-version-32-bit-or-64-bit-is-different-from-your-power-bi-desktop-bit-version"></a>状況 2:Access データベース エンジンのビット版 (32 ビットまたは 64 ビット) がお使いの Power BI Desktop のビット版と異なる

この状況は、多くの場合、インストールした Microsoft Office のバージョンが 32 ビットで、Power BI Desktop のバージョンが 64 ビットのときに発生します。 また、反対の場合もあります。ビット版の不一致はいずれの場合にも発生します。 Microsoft 365 サブスクリプションを使用している場合は、「[状況 3](#situation-3-trouble-using-access-or-xls-files-with-a-microsoft-365-subscription)」で別の問題と解決策を参照してください。 次のどの解決策でも、このビット版不一致エラーを解決できます。

### <a name="solution-1"></a>解決策 1

お使いの Microsoft Office のビット版に合わせて Power BI Desktop のバージョンを変更します。 

1. Power BI Desktop のビット版を変更するには、Power BI Desktop をアンインストールし、お使いの Office に一致するバージョンの Power BI Desktop をインストールします。 

1. Power BI Desktop のバージョンを選択するには、Power BI Desktop のダウンロード ページで、 **[ダウンロードの詳細オプション]** を選択します。
   
   ![Power BI Desktop ダウンロード ページのダウンロードの詳細オプション](media/desktop-access-database-errors/desktop-access-errors-1.png)
   
1. [ダウンロード] ページが表示されたら、言語を選択し、 **[ダウンロード]** ボタンを選択します。 
 
1. 表示された画面で、32 ビット版の場合は PBIDesktop.msi の横にあるチェック ボックスをオンにし、64 ビット版の場合は PBIDesktop_x64.msi の横にあるチェック ボックスをオンにします。 

   次のスクリーン ショットでは、64 ビット版が選択されています。
   
   ![Power BI Desktop のダウンロードの種類を選択する](media/desktop-access-database-errors/desktop-access-errors-2.png)
   
   >[!NOTE]
   >32 ビット版の Power BI Desktop を使用する場合、非常に大きなデータ モデルを作成すると、メモリ不足の問題が発生する可能性があります。

### <a name="solution-2"></a>解決策 2

お使いの Power BI Desktop のビット版に合わせて Microsoft Office のビット版を変更します。

1. Microsoft Office をアンインストールします

2. Power BI Desktop インストールに一致するバージョンの Office をインストールします。

### <a name="solution-3"></a>解決策 3

.XLS ファイル (Excel 97-2003 ワークブック) を開こうとしてエラーが発生する場合、Excel で .XLS ファイルを開き、XLSX ファイルとして保存することで Access データベース エンジンの使用を回避できます。

### <a name="solution-4"></a>解決策 4

以上の 3 つの解決策が実施できない場合、両方のバージョンの Access データベース エンジンをインストールできます。 ただし、この回避策はお勧めしません。 両方のバージョンをインストールことで、Power Query for Excel と Power BI Desktop のこの問題が解消されますが、先にインストールされたビット版の Access データベース エンジンがアプリケーションで (既定で) 自動的に使用される場合、エラーや問題が発生します。 

両方のビット版の Access データベース エンジンをインストールするには、次の手順に従います。

1. [ダウンロード ページ](https://www.microsoft.com/download/details.aspx?id=13255)から、両方のビット版の Access データベース エンジンをインストールします。 

1. */passive* スイッチを使用して、Access データベース エンジンの各バージョンを実行します。 例:

   ```console
   c:\users\joe\downloads\AccessDatabaseEngine.exe /passive

   c:\users\joe\downloads\AccessDatabaseEngine_x64.exe /passive
   ```

## <a name="situation-3-trouble-using-access-or-xls-files-with-a-microsoft-365-subscription"></a>状況 3:Microsoft 365 サブスクリプションで Access または .XLS ファイルを使うことによる問題

Microsoft 365 サブスクリプション (**Office 2013** または **Office 2016**) を使用している場合、Access データベース エンジン プロバイダーは、Microsoft Office プロセス "*だけ*" がアクセスできる仮想レジストリの場所に登録されます。 その結果、Office プロセスではない Mashup エンジン (Office 365 ではない Excel および Power BI Desktop を実行します) は、Access データベース エンジン プロバイダーを使うことができません。

このような状況を解決するには、Power BI Desktop のインストールのビット版と一致する [Access データベース エンジン再頒布可能パッケージをダウンロードしてインストール](https://www.microsoft.com/download/details.aspx?id=13255)します。 ビット版の詳細については、この記事の前の方のセクションを参照してください。

## <a name="other-situations-that-can-cause-import-issues"></a>インポートの問題が発生する可能性があるその他の状況

Access または .XLS ファイルで発生するできる限り多くの問題に対応するように作業しています。 この記事で説明されていない問題が発生した場合は、問題に関する質問を [Power BI サポート](https://powerbi.microsoft.com/support/)にお送りください。 多くのお客様に影響を与える可能性がある問題を常に注視し、記事にしています。

