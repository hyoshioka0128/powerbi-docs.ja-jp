---
title: Power BI の計画メンテナンス
description: Power BI の計画メンテナンスによって組織に及ぼされる影響と、次に実行する必要がある手順に関する管理者向けの情報を示します。
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/30/2020
ms.author: kfollis
ms.custom: MC
ROBOTS: NOINDEX
LocalizationGroup: Admin
ms.openlocfilehash: 68cd001995603fec3a64e4b2c79ee2216bfe9ac0
ms.sourcegitcommit: 8861dac6724202a5b3be456a6aff8f3584e0cccf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2020
ms.locfileid: "93132300"
---
# <a name="power-bi-planned-maintenance"></a>Power BI の計画メンテナンス

Power BI サービスの計画メンテナンスは、お客様に信頼性の高い製品を提供するための取り組みの一環として必要です。 計画メンテナンスが行われているときは、組織ではしばらくの間、Power BI サービスを使用できなくなります。 ユーザーは Power BI サービスにアクセスできない場合があります。また、バックグラウンド操作は失敗する可能性があります。 メンテナンス期間が終了すると、サービスが正常に動作して、対話型操作とバックグラウンド操作の両方が正常に実行されることが想定されます。  

組織への影響を最小限に抑えるために、メンテナンスは通常業務の時間外に行われるよう計画されています。 Microsoft では、世界中にユーザーがいる組織では、"通常業務の時間外" によってもたらされる影響がさまざまになることを認識しています。 お客様のユーザーに影響がある場合について、お詫び致します。 Microsoft では、Power BI を改善してメンテナンス期間を最小限に抑えるために、精力的な取り組みを行っています。

お客様の組織が影響を受ける場合は、事前に通知をお送りします。 Microsoft 365 の管理者は、Microsoft 365 メッセージ センター上で事前通知を確認し、電子メールを受信します。 さらに、Premier サポート契約をお持ちのお客様には、Microsoft アカウント チームからの通知が行われます。

## <a name="actions-to-take-now"></a>今すぐに実行するアクション

* Microsoft 365 の管理者は、Power BI の計画メンテナンスに関するメッセージについて、[メッセージ センターを確認](https://admin.microsoft.com/Adminportal/Home#/MessageCenter)する必要があります。 認識しておく必要があるのに、メッセージ センターへのアクセス権を保持していない可能性があるユーザーに、メッセージを共有してください。
* Microsoft 365 の管理者でない場合は、IT 部門または社内のサポート チームに連絡して、今後のメンテナンスについて質問してください。

## <a name="actions-to-take-when-maintenance-is-complete"></a>メンテナンスが完了したときに実行するアクション

* ユーザーは、開いているブラウザー ウィンドウを更新する必要があります。
* Power BI Mobile アプリ ユーザーは、最新バージョンを使用していることを確認し、サインアウトしてからアプリにサインインし直す必要があります。 お使いの携帯電話のアプリ ストアを確認するか、[Power BI Mobile](https://powerbi.microsoft.com/mobile/) のページを確認してください。
* ローカルであれ OneDrive や SharePoint の場所からであれ、組織の視覚化を使用するレポートをアクティブに編集または発行していたお客様は、組織の視覚化ストアを介してその視覚化を再インポートするか、または更新された PBIX をダウンロードしてから、再発行する必要があります。 組織の視覚化の詳細については、「[組織の視覚化](organizational-visuals.md)」を参照してください。
* [Excel で分析] 機能が使用された Excel ブックが更新されない場合は、接続文字列を更新するか、そのデータセットの ODC 接続を再ダウンロードする必要が生じることがあります。 詳細については、「[Excel で分析](../collaborate-share/service-analyze-in-excel.md#connect-to-power-bi-data)」を参照してください。
* メンテナンスの完了時には、コンテンツに埋め込まれている Power BI へのリンクが接続されなくなる場合があります。 たとえば、SharePoint または Teams 内の埋め込みのリンクを使用すると、ユーザー エラーが発生する場合があります。 この問題を解決するには、Power BI で埋め込みのリンクを再生成して、それらが使用されている場所を更新する必要があります。 埋め込みのリンクの詳細については、「[SharePoint Online にレポート Web パーツを埋め込む](../collaborate-share/service-embed-report-spo.md)」と [Power BI による Microsoft Teams での共同作業](../collaborate-share/service-collaborate-microsoft-teams.md)に関する記事を参照してください。
* メンテナンスより前に回収された使用データの一部は、メンテナンスの完了後は利用できません。 この使用データには次のものが含まれます。

  * [Power BI アクティビティ ログ](service-admin-auditing.md#use-the-activity-log)。 ユーザーはメンテナンスより前のアクティビティ ログをダウンロードしてください。 [Office 365 監査ログ データ](service-admin-auditing.md#access-your-audit-logs)を使用し、同等のアクティビティ詳細を取得することもできます。
  * [データ系列ビュー](../collaborate-share/service-data-lineage.md#explore-lineage-view)でカウントを表示する
  * [データ保護メトリック レポート](service-security-data-protection-metrics-report.md)
  * [使用状況メトリック (プレビュー)](../collaborate-share/service-modern-usage-metrics.md)

## <a name="next-steps"></a>次の手順

* [サービス中断の通知を有効にする](service-interruption-notifications.md)
* [メッセージ センターで今後の変更を追跡する](/microsoft-365/admin/manage/message-center)