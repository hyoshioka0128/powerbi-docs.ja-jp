---
title: Power BI Desktop の起動時の問題を解決する
description: Power BI Desktop の起動時の問題を解決する
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: troubleshooting
ms.date: 01/14/2020
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: ba59a08ee1b50e44af71312a25d77fb67c8fca2d
ms.sourcegitcommit: a453ba52aafa012896f665660df7df7bc117ade5
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "85485440"
---
# <a name="troubleshoot-opening-power-bi-desktop"></a>Power BI Desktop の起動に関するトラブルシューティング

Power BI Desktop では、以前のバージョンの *Power BI オンプレミス データ ゲートウェイ*をインストールして実行していたユーザーが Power BI Desktop を開くことができないことがあります。これは、Power BI オンプレミス データ ゲートウェイによってローカル コンピューター上の名前付きパイプに設定された管理ポリシー制限が原因で発生します。

## <a name="resolve-issues-with-the-on-premises-data-gateway-and-power-bi-desktop"></a>オンプレミス データ ゲートウェイと Power BI Desktop での問題を解決する

オンプレミス データ ゲートウェイに関する問題を解決して、Power BI Desktop を開くことができるようにするには、3 つのオプションがあります。

### <a name="resolution-1-install-the-latest-version-of-power-bi-on-premises-data-gateway"></a>解決方法 1:最新バージョンの Power BI オンプレミス データ ゲートウェイをインストールする

Power BI オンプレミス データ ゲートウェイの最新バージョンでは、ローカル コンピューター上の名前付きパイプに制限が設定されないため、Power BI Desktop を正常に開くことができます。 引き続き Power BI オンプレミス データ ゲートウェイを使う必要がある場合、推奨される解決方法はそれを更新することです。 [最新バージョンの Power BI オンプレミス データ ゲートウェイ](https://go.microsoft.com/fwlink/?LinkId=698863)をダウンロードできます。 このリンクは、インストール用の実行可能ファイルの直接ダウンロード リンクです。

### <a name="resolution-2-uninstall-or-stop-the-power-bi-on-premises-data-gateway-microsoft-service"></a>解決方法 2:Power BI オンプレミス データ ゲートウェイの Microsoft サービスをアンインストールまたは停止する

Power BI オンプレミス データ ゲートウェイが不要になった場合は、アンインストールできます。 または、Power BI オンプレミス データ ゲートウェイ Microsoft サービスを停止できます。これにより、ポリシー制限が削除され、Power BI Desktop を開くことができるようになります。

### <a name="resolution-3-run-power-bi-desktop-with-administrator-privilege"></a>解決方法 3:管理者特権を使って Power BI Desktop を実行する

代わりに、Power BI Desktop を管理者として正常に起動できます。これにより、Power BI Desktop も正常に開くことができます。 この場合でも、前述のとおり Power BI オンプレミス データ ゲートウェイの最新バージョンをインストールすることを勧めします。

Power BI Desktop はマルチプロセス アーキテクチャとして設計されており、複数のプロセスが Windows 名前付きパイプを使って通信を行っています。 これらの名前付きパイプを干渉する他のプロセスがある可能性があります。 このような干渉の最も一般的な理由はセキュリティであり、ウイルス対策ソフトウェアやファイアウォールによってパイプがブロックされたり、トラフィックが特定のポートにリダイレクトされたりする場合があります。 管理者特権で Power BI Desktop を開くと、その問題が解決する可能性があります。 管理者特権で開くことができない場合は、管理者に連絡して、名前付きパイプが適切に通信できない原因となっているセキュリティ規則を確認してください。 次に、Power BI Desktop とそれぞれのサブプロセスを許可リストに追加します。

## <a name="resolve-issues-when-connecting-to-sql-server"></a>SQL Server に接続するときの問題を解決する

SQL Server データベースに接続しようとすると、次のテキストのようなエラー メッセージが表示される場合があります。

`"An error happened while reading data from the provider:`\
`'Could not load file or assembly 'System.EnterpriseServices, Version=4.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxx' or one of its dependencies.`\
`Either a required impersonation level was not provided, or the provided impersonation level is invalid. (Exception from HRESULT: 0x80070542)'"`

多くの場合、SQL Server 接続を行う前に管理者として Power BI Desktop を開くと、この問題を解決できます。

Power BI Desktop を管理者として起動して接続を確立すると、必要な DLL が適切に登録されます。 その後は、管理者として Power BI Desktop を開く必要はありません。

## <a name="get-help-with-other-launch-issues"></a>他の起動時の問題に関するヘルプを得る

Power BI Desktop で発生する多くの問題にできる限り対応するように作業しています。 多くのお客様に影響を与える可能性がある問題を常に注視し、記事にしています。

Power BI Desktop を開くときの問題がオンプレミス データ ゲートウェイに関連していない場合、または前記の解決方法で解決しないときは、"*Power BI のサポート*" (<https://support.powerbi.com>) にサポート インシデントを送信して、問題の特定と解決を依頼できます。

今後、Power BI Desktop で他の問題が発生した場合は、トレースを有効にし、ログ ファイルを収集することをお勧めします。 ログ ファイルは、問題を分離して特定するのに役立つ可能性があります。 トレースを有効にするには、 **[ファイル]**  >  **[オプションと設定]**  >  **[オプション]** を選択します。 **[診断]** を選択し、 **[トレースを有効にする]** を選択します。 このオプションを設定するには Power BI Desktop が実行されている必要がありますが、それは Power BI Desktop を開くことに関する将来の問題で役に立ちます。
