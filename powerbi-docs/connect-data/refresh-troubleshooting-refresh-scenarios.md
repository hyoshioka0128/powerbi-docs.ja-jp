---
title: 更新に関するトラブルシューティング シナリオ
description: 更新に関するトラブルシューティング シナリオ
author: davidiseminger
ms.author: davidi
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: troubleshooting
ms.date: 03/10/2021
LocalizationGroup: Data refresh
ms.openlocfilehash: 3d6117878dee2f72a65a1754c94c067615a79978
ms.sourcegitcommit: 89c349500dd0737d80a753403714bceb3fd0a3ef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2021
ms.locfileid: "102628278"
---
# <a name="troubleshooting-refresh-scenarios"></a>更新に関するトラブルシューティング シナリオ

ここでは、Power BI サービス内のデータを更新するときに直面する可能性のあるさまざまなシナリオに関する情報を提供します。

> [!NOTE]
> 以下に記載されていないシナリオが発生し、問題を引き起こしている場合は、[コミュニティ サイト](https://community.powerbi.com/)でさらに支援を求めることや、[サポート チケット](https://powerbi.microsoft.com/support/)を作成することができます。
>

更新の基本要件が満たされ、検証されていることを常に確認してください。 これらの基本要件の内容は次のとおりです。

* ゲートウェイのバージョンが最新であることを確認する
* レポートでゲートウェイが選択されていることを確認する - 選択されていない場合、データソースが変更されているか、失われている可能性があります

それらの要件が満たされていることを確認したら、後続のセクションで詳しいトラブルシューティング方法をご覧ください。 


## <a name="email-notifications"></a>電子メールによる通知

電子メールによる通知からこの記事にアクセスしている場合で、かつ更新の問題についてのメール通知を今後希望しない場合は、Power BI 管理者にお問い合わせください。受信登録しているメールまたはメール リストを、Power BI 内の適切なデータセットから削除するよう依頼してください。 この設定は、Power BI 管理ポータルの次の領域で行えます。

![更新通知のメール](media/refresh-troubleshooting-refresh-scenarios/refresh-email.png)

## <a name="refresh-using-web-connector-doesnt-work-properly"></a>Web コネクタを使用した更新が正常に動作しない

[**Web.Page**](/powerquery-m/web-page) 関数を使用している Web コネクタ スクリプトがあり、2016 年 11 月 18 日より後にデータセットまたはレポートを更新した場合は、更新が適切に機能するようにゲートウェイを使用する必要があります。

## <a name="unsupported-data-source-for-refresh"></a>更新用にサポートされていないデータ ソース

データセットを構成しているときに、データセットが更新用にサポートされていないデータ ソースを使用していることを示すエラーが発生する場合があります。 詳細については、[更新用にサポートされていないデータ ソースのトラブルシューティング](service-admin-troubleshoot-unsupported-data-source-for-refresh.md)を参照してください

## <a name="dashboard-doesnt-reflect-changes-after-refresh"></a>更新後にダッシュボードに変更が反映されない

ダッシュボードのタイルに更新が反映されるまで約 10 から 15 分お待ちください。 それでも表示されない場合は、視覚化をもう一度ダッシュボードにピン留めします。

## <a name="gatewaynotreachable-when-setting-credentials"></a>資格情報を設定するときの GatewayNotReachable

データ ソースの資格情報を設定するときに、`GatewayNotReachable` が発生する可能性があります。 これは、ゲートウェイが期限切れになった場合に発生する可能性があります。 最新のゲートウェイをインストールし、もう一度お試しください。

## <a name="processing-error-the-following-system-error-occurred-type-mismatch"></a>処理エラー:次のシステム エラーが発生しました:型が一致しません

Power BI Desktop ファイルまたは Excel ブック内の M スクリプトに問題がある可能性があります。 Power BI Desktop のバージョンが古いことが原因である可能性もあります。

## <a name="tile-refresh-errors"></a>タイルの更新エラー

ダッシュボードのタイルで発生する可能性があるエラーの一覧とその説明については、「[タイルのエラーのトラブルシューティング](refresh-troubleshooting-tile-errors.md)」をご覧ください。

## <a name="refresh-fails-when-updating-data-from-sources-that-use-aad-oauth"></a>AAD OAuth を使用するソースのデータを更新すると、更新に失敗する

Azure Active Directory (**AAD**) OAuth トークンはさまざまなデータ ソースで利用されていますが、約 1 時間で失効します。 データの読み込みにかかる時間が、トークンの有効期限 (1 時間) を超えてしまうという状況になる場合があります。データを読み込むとき、Power BI サービスが待機するのは最大 2 時間であるためです。 このような状況では、資格情報エラーでデータの読み込みプロセスに失敗することがあります。

AAD OAuth を使用するデータ ソースには、**Microsoft Dynamics CRM Online** や **SharePoint Online** (SPO) などが含まれます。 このようなデータ ソースに接続するとき、データの読み込みに 1 時間以上かかり、資格情報エラーが表示される場合、これが理由として考えられます。

Microsoft は、データの読み込みプロセスでトークンが更新され、続行されるソリューションを研究しています。 ただし、Dynamics CRM Online または SharePoint Online (あるいはその他の AAD OAuth データ ソース) インスタンスが非常に大きく、2 時間のデータ読み込みしきい値に達するようであれば、Power BI サービスでもデータ読み込みタイムアウトが発生する場合があります。

また、更新が正常に動作するように、AAD OAuth を使って **SharePoint Online** データ ソースに接続するときは、**Power BI サービス** へのサインインに使ったものと同じアカウントを使う必要があることにも注意してください。

## <a name="uncompressed-data-limits-for-refresh"></a>更新の際に適用される非圧縮データの制限

**Power BI サービス** にインポートできるデータセットの最大サイズは 1 GB です。 このデータセットは圧縮されており、その圧縮率は、高いパフォーマンスを実現するためにかなり高くなっています。 また、共有された容量では、更新中に処理される非圧縮データ量が 10 GB に制限されます。 この制限は、圧縮を考慮しているため、1 GB をかなり上回っています。 Power BI Premium のデータセットには、この制限は適用されません。 この理由により Power BI サービスでの更新が失敗した場合は、Power BI にインポートするデータの量を減らしたうえで、もう一度やり直してください。

## <a name="scheduled-refresh-timeout"></a>スケジュールされた更新のタイムアウト

インポートされたデータセットに対してスケジュールされた更新の 2 時間後のタイムアウト。 **Premium** ワークスペースのデータセットの場合、このタイムアウトは 5 時間に延長されます。 この制限がある場合は、データセットのサイズまたは複雑さを軽減することを検討するか、データセットをより細かく分けることを検討してください。

## <a name="scheduled-refresh-failures"></a>スケジュールした更新のエラー

スケジュールした更新が 4 回連続で失敗した場合、Power BI ではその更新が無効になります。 根底のある問題に対処し、スケジュールした更新をもう一度有効にしてください。

## <a name="access-to-the-resource-is-forbidden"></a>リソースへのアクセスが禁止されています  

このエラーは、キャッシュされた資格情報の有効期限が切れていることが原因で発生する可能性があります。 Power BI にサインインし、 `https://app.powerbi.com?alwaysPromptForContentProviderCreds=true` に移動して、インターネット ブラウザーのキャッシュをクリアしてください。 これで、資格情報が強制的に更新されます。

## <a name="data-refresh-failure-because-of-password-change-or-expired-credentials"></a>パスワードが変更されたか、資格情報の有効期限が切れているため、データを更新できない

キャッシュされた資格情報の有効期限が切れているため、データを更新できない可能性もあります。 Power BI にサインインし、 `https://app.powerbi.com?alwaysPromptForContentProviderCreds=true` に移動して、インターネット ブラウザーのキャッシュをクリアしてください。 これで、資格情報が強制的に更新されます。

## <a name="refresh-a-column-of-the-any-type-containing-truefalse-results-in-unexpected-values"></a>TRUE/FALSE が含まれる ANY 型の列を更新すると、予想外の値が返される

ANY データ型列が含まれるレポートを Power BI Desktop で作成するとき、その列に TRUE/FALSE 値が含まれている場合、更新後、その列の値が Power BI Desktop と Power BI サービスの間で異なることがあります。 Power BI Desktop では、基盤となるエンジンによってブール値が文字列に変換され、TRUE または FALSE 値が保持されます。 Power BI サービスでは、基盤となるエンジンによって値がオブジェクトに変換され、続いて値が -1 または 0 に変換されます。

このような列を利用して Power BI Desktop で作成されたビジュアルは、更新イベント前に設計されたように見えたり、振る舞ったりすることがありますが、更新イベント後に変更されるかもしれません (TRUE または FALSE が -1 または 0 に変換されるため)。


## <a name="next-steps"></a>次の手順

- [Power BI でのデータの更新](refresh-data.md)  
- [オンプレミス データ ゲートウェイのトラブルシューティング](service-gateway-onprem-tshoot.md)  
- [Power BI Gateway - Personal のトラブルシューティング](service-admin-troubleshooting-power-bi-personal-gateway.md)  

他にわからないことがある場合は、 [Microsoft Power BI コミュニティで質問してみる](https://community.powerbi.com/)
