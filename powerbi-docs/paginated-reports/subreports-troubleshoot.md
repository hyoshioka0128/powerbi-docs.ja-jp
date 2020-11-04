---
title: Power BI のページ分割されたレポートでのサブレポートのトラブルシューティング
description: ページ分割されたレポート内のレポート アイテムであるサブレポートを使用する際の一般的な問題を解決する方法について説明します。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: troubleshooting
ms.date: 04/29/2020
ms.openlocfilehash: 06d9b0fc60d9b44f98108cf46bc35c5de15316d6
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2020
ms.locfileid: "93297979"
---
# <a name="troubleshoot-subreports-in-power-bi-paginated-reports"></a>Power BI のページ分割されたレポートでのサブレポートのトラブルシューティング

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

ページ分割されたサブレポートの使用中に、予期しない結果が出る場合や、機能が期待どおりに動作しない場合があります。 この記事では、サブレポートの使用中に発生する一般的な問題の解決方法を説明します。 *サブレポート* は、ページ分割されたメインのレポート本文内に別のレポートを表示するレポート アイテムです。 背景については、「[Power BI のページ分割された レポートでのサブレポート](subreports.md)」をご覧ください。

## <a name="subreport-couldnt-be-found"></a>サブレポートが見つかりませんでした

**説明:** サブレポートがレンダリングされません。 代わりに、エラー メッセージが表示されます。

### <a name="message"></a>メッセージ

"サブレポート 'Subreport1 ' が指定された場所 'CustomerDetails' に見つかりませんでした。 このサブレポートがパブリッシュされているかどうか、指定した名前が正しいかどうかを確認してください。"

### <a name="possible-reasons"></a>考えられる原因

- 指定された名前のサブレポートが、メイン レポートと同じワークスペースまたはアプリに存在しません。
- ユーザーにサブレポートへのアクセス権がありません。
- メイン レポート内のサブレポートの数が、サブレポートの制限 (50 サブレポート) に達しました。

### <a name="troubleshooting-steps"></a>トラブルシューティングの手順

**ワークスペースの場合**

- エラー メッセージ内に名前があるレポートが存在することを確認します。 名前の大文字と小文字は区別されます。

**アプリの場合**

- エラー メッセージ内に名前があるレポートがアプリ内に存在することを確認します。 詳細については、アプリの作成者にお問い合わせください。

**レポートが共有されている場合**

1. エラー メッセージ内に名前があるレポートが、自分と共有されていることを確認します。
2. レポートが存在する場合は、メイン レポートとサブレポートで所有者名が同じであることを確認します。 次に、メイン レポートの所有者にその情報を問い合わせます。

## <a name="subreport-renders-with-unexpected-content"></a>サブレポートに予期しないコンテンツがレンダリングされる

### <a name="possible-reason"></a>考えられる理由

Power BI を使用すると、同じワークスペースに同じ名前のレポートを複数含めることができます。

### <a name="troubleshooting-steps-for-report-authors"></a>トラブルシューティングの手順 (レポート作成者の場合)

1. Power BI レポート ビルダーでメイン レポートを開き、サブレポートの名前を確認します。
2. ワークスペース内で同じ名前のレポートを探します。
3. 予期されるレポートを見つけ、残りレポートの名前を変更します。

**作成者以外の場合:** 作成者に連絡してください。

## <a name="data-retrieval-fails"></a>データの取得に失敗する

**説明:** サブレポートのレンダリング中にデータ取得が失敗します。 サブレポートがレンダリングされません。 代わりに、エラー メッセージが表示されます。

### <a name="message"></a>メッセージ

'InvoiceDetails' に配置されているサブレポート 'Subreport1' 用にデータを取得できませんでした。 詳細については、ログ ファイルを確認してください。"

### <a name="troubleshooting-steps"></a>トラブルシューティングの手順

データ アクセスに問題があるレポートの一般的なトラブルシューティング手順と同じです。

## <a name="rendering-fails-unspecified-parameters"></a>レンダリングの失敗:指定されていないパラメーター

**説明:** パラメーターが指定されていないため、サブレポートのレンダリングに失敗します。 サブレポートには必須のパラメーターがありますが、メイン レポートではこれらがすべてが設定されていません。

### <a name="message"></a>メッセージ 
'''SubreportAWithDS' に配置されているサブレポート 'Subreport1' 用に指定されなかったパラメーターが 1 つ以上あります。"

### <a name="troubleshooting-steps-for-the-report-author"></a>トラブルシューティングの手順 (レポート作成者の場合)

1. Power BI レポート ビルダーでメイン レポートを開きます。
2. Power BI レポート ビルダーでサブレポートを開きます。
3. メイン レポート内のサブレポート レポート アイテム内に渡されたパラメーターのセットが、サブレポート内のパラメーターのセットと一致していることを確認します。

**作成者以外の場合:** 作成者に連絡してください。

## <a name="rendering-fails-recursion-limit"></a>レンダリングの失敗:再帰の制限

**説明:** 再帰の制限のため、サブレポートのレンダリングに失敗します。 サブレポートを 20 レベルより深く入れ子にすることはできません。

### <a name="message"></a>メッセージ

"レポートまたはサブレポートに含まれている再帰サブレポート 'Subreport1' が、許可されている再帰回数の上限値を超えています。"

### <a name="troubleshooting-steps-for-report-authors"></a>トラブルシューティングの手順 (レポート作成者の場合)

- 入れ子を減らします。
- レポートの構造を再設計します。

## <a name="other-errors"></a>その他のエラー

**説明:** 前のいずれのカテゴリにも分類されないエラー。

### <a name="message"></a>メッセージ

"エラー: サブレポートを表示できませんでした。"

### <a name="possible-reasons"></a>考えられる原因

- サブレポートのレンダリング中に複数のエラーが発生した場合 (たとえば、データ取得の問題とパラメーターが一致していない場合)。
- 予期しないエラー。

### <a name="troubleshooting-steps-for-report-authors"></a>トラブルシューティングの手順 (レポート作成者の場合)

1. サブレポートが直接レンダリングされることを確認します。
2. サブレポートをレンダリングできる場合は、サブレポートとメイン レポートの両方でパラメーターを確認します。
3. メイン レポートに 50 個を超える一意のサブレポートが含まれていないこと、およびサブレポートが 20 レベルを超えて入れ子になっていないことを確認します。
4. 問題を解決できない場合は、Power BI サポートにお問い合わせください。

**作成者以外の場合:** 作成者に連絡してください。

## <a name="next-steps"></a>次の手順

[Power BI のページ分割された レポートでのサブレポート](subreports.md)

[ページ分割されたレポートを Power BI サービスで表示する](../consumer/paginated-reports-view-power-bi-service.md)

その他の質問 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。
