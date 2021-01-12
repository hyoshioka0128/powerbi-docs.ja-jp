---
title: Power BI サービスのページ分割されたレポートをサブスクライブする
description: この記事では、Power BI サービスのページ分割されたレポートをサブスクライブする際の留意点について説明します。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: maggies
ms.service: powerbi
ms.subservice: pbi-explore
ms.topic: how-to
ms.date: 01/04/2021
ms.openlocfilehash: 67efe0e7abd23792f46561f78b0b048b431561a4
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888008"
---
# <a name="subscribe-yourself-and-others-to-paginated-reports-in-the-power-bi-service"></a>Power BI サービスのページ分割されたレポートを自分および他のユーザーがサブスクライブする 

Power BI サービスのページ分割されたレポートに対して自分および他のユーザー用の電子メール サブスクリプションを設定できるようになりました。 一般に、[Power BI サービスのレポートおよびダッシュボードをサブスクライブ](end-user-subscribe.md)する場合とプロセスは同じです。 この記事では、違いと考慮事項について詳しく説明します。 

サブスクリプションの設定時には、メールの受信頻度 (毎日、毎週、毎月、毎時間) を選択します。 サブスクリプションを実行する時間を選択することもできます。 すべてのレポートに対して設定できるサブスクリプションの数に制限はありません。 

## <a name="considerations-for-paginated-report-subscriptions"></a>ページ分割されたレポート サブスクリプションに関する考慮事項 

- ダッシュボードまたは Power BI レポート用のサブスクリプションとは異なり、ご利用のサブスクリプションには、レポート出力全体の添付ファイルが含まれています。  次の添付ファイルの種類がサポートされています: PDF、PowerPoint プレゼンテーション (PPTX)、Excel ブック (XLSX)、Word 文書 (DOCX)、CSV ファイル、および XML。

- レポートのプレビュー画像を電子メールの本文に含めることができます。  これは省略可能であり、選択した添付ファイル形式によっては、添付したレポート ドキュメントの最初のページと多少異なる場合があります。 

- レポート添付ファイルの最大サイズは 24 MB です。 

- Azure Analysis Services や Power BI のデータセットなど、現在サポートされているデータ ソースに接続する、他のユーザーのページ分割されたレポートをサブスクライブすることができます。 SQL Server Reporting Services で現在の方法と同様に、レポート添付ファイルでもご利用のアクセス許可に基づいてデータが反映されることに留意してください。 

- 電子メール サブスクリプションは、ご利用のレポートに対して現在選択されているパラメーターまたは既定のパラメーターのいずれかを使用して送信できます。  ご利用のレポート用に作成するサブスクリプションごとに異なるパラメーター値を設定してもかまいません。 

- レポートの作成者が式ベースのパラメーターを設定している場合 (たとえば、既定値が常に今日の日付である場合)、サブスクリプションでは既定値としてそれが使用されます。 他のパラメーター値を変更して、現在の値を使用することを選択できますが、その値も明示的に変更しない限り、サブスクリプションでは式ベースのパラメーターが使用されます。

- ページ分割されたレポートには、頻度を設定する **[データ更新後]** オプションはありません。 基になるデータ ソースから常に最新の値を取得します。 

## <a name="next-steps"></a>次の手順

[Power BI サービスのレポートとダッシュボードを自分および他のユーザーがサブスクライブする](../collaborate-share/service-report-subscribe.md)

[Power BI サービスでのページ分割されたレポート](end-user-paginated-report.md)
