---
title: Microsoft Teams と Power BI で共同作業する
description: 分散された環境で働くことが標準になるにつれて、リモートでの仕事を可能にし、従業員の同期を維持するために Microsoft Teams を利用する組織が増えています。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 04/02/2021
ms.openlocfilehash: 7b1e22c52e2698b1be0349a6ea3bdda7142600f2
ms.sourcegitcommit: a3b1ccdd18ef705de960625a9715ad5bbc21b1b6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2021
ms.locfileid: "106229177"
---
# <a name="collaborate-in-microsoft-teams-with-power-bi"></a>Microsoft Teams と Power BI で共同作業する

分散された環境で働くことが標準になるにつれて、リモートでの仕事を可能にし、従業員の同期を維持するために Microsoft Teams を利用する組織が増えています。この記事では、Microsoft Teams のチャネルとチャットで、対話型の Power BI コンテンツを共有および共同作業を行うためのオプションについて概要を説明します。 

- Microsoft Teams の **[Power BI]** タブを使用すると、[対話形式のレポートを Microsoft Teams のチャネルおよびチャットに埋め込む](service-embed-report-microsoft-teams.md)ことができます。 [Power BI] タブを使用すると、仕事仲間があなたのチームのデータを検索し、あなたのチームのチャネル内のデータについて話し合うことができます。 
- ご自分のレポート、ダッシュボード、およびアプリへのリンクを [Microsoft Teams] メッセージ ボックスに貼り付けるときに、[リンク プレビュー](service-teams-link-preview.md)を作成します。 リンク プレビューには、リンクに関する情報が表示されます。 
- Power BI サービスでレポートやダッシュボードを表示しているときに Microsoft Teams で会話をすばやく開始するには、[[Microsoft Teams でのチャット]](service-share-report-teams.md) を使用します。
- [Microsoft Teams 内の Power BI アプリ](service-microsoft-teams-app.md)を使用すると、基本的な Power BI サービス エクスペリエンス全体を Microsoft Teams に取り込むことができます。
 
:::image type="content" source="media/service-collaborate-microsoft-teams/power-bi-embed-teams-report.png" alt-text="Microsoft Teams チャネルに埋め込まれた Power BI レポートのスクリーンショット。":::

## <a name="requirements"></a>要件

一般に、Microsoft Teams で Power BI を機能させるには、次の要素を確認します。

- お客様のユーザーが Power BI Pro または Premium Per User (PPU) のライセンスを所有している。または、Power BI ライセンスのある [Power BI Premium 容量 (EM または P SKU)](../admin/service-premium-what-is.md) にレポートが含まれている。
- ユーザーが Power BI サービスにサインインし、自分の Power BI ライセンスをアクティブ化している。
- Microsoft Teams の **[Power BI]** タブを使用するための要件をユーザーが満たしている。

## <a name="grant-access-to-reports"></a>レポートへのアクセスを許可する

Microsoft Teams にレポートを埋め込んだり、項目へのリンクを送信しても、レポートを表示するためのアクセス許可が自動的にユーザーに与えられることはありません。 [Power BI でユーザーにレポートの表示を許可する](service-share-dashboards.md)必要があります。 チーム用に Microsoft 365 グループを使用すると、作業を容易にすることができます。

> [!IMPORTANT]
> Power BI サービスでレポートを表示できるユーザーを確認し、一覧に含まれないユーザーにアクセスを許可します。

チーム内のすべてのユーザーがレポートに確実にアクセスできるようにする方法の 1 つは、1 つのワークスペースにレポートを配置し、チームの Microsoft 365 グループにアクセス権を付与することです。

## <a name="share-with-external-users"></a>外部ユーザーと共有する

チーム内の Power BI レポートを統合し、外部ユーザーと共有することができます。 実行する手順は次のとおりです。

1.  組織に外部ユーザーを招待し、そのユーザーが招待状を受け入れます。 詳細については、「[Azure Active Directory B2B を使用して外部ゲスト ユーザーに Power BI コンテンツを配布する](../guidance/whitepaper-azure-b2b-power-bi.md)」を参照してください。
2.  レポートに対するアクセス許可を外部ユーザーに付与します。 個別にアクセス許可を割り当てるのが最適です。
3.  外部ユーザーに Power BI ライセンスが割り当てられていることを確認します。 コンテンツが Premium 容量にある場合、ユーザーに必要なのは無料ライセンスのみです。 それ以外の場合、ユーザーは [Power BI Pro の個人向け試用版にサインアップ](../fundamentals/service-self-service-signup-for-power-bi.md#sign-up-for-an-individual-trial-of-power-bi-pro)するか、Premium Per User (PPU) ライセンスを取得することができます。

## <a name="known-issues-and-limitations"></a>既知の問題と制限事項

- Power BI では、Microsoft Teams と同じローカライズされた言語はサポートされていません。 そのため、埋め込みのレポートが適切にローカライズされていない可能性があります。
- Power BI ダッシュボードを Microsoft Teams の **[Power BI]** タブに埋め込むことはできません。
- Power BI のライセンスまたはレポートへのアクセス許可を持たないユーザーには、"コンテンツは利用できません" というメッセージが表示されます。
- Internet Explorer 10 を使用している場合、問題が発生する可能性があります。 <!--You can look at the [browsers support for Power BI](../fundamentals/power-bi-browsers.md) and for [Microsoft 365](https://products.office.com/office-system-requirements#Browsers-section). -->
- [URL フィルター](service-url-filters.md)は、Microsoft Teams の **[Power BI]** タブではサポートされていません。
- 国内のクラウドでは、この新しい **[Power BI]** タブは使用できません。 Power BI アプリの新しいワークスペース エクスペリエンスやレポートがサポートされていない古いバージョンを使用できる可能性があります。
- タブを保存したら、タブの設定からタブ名を変更することはできません。 変更するには、 **[名前変更]** オプションを使用します。
- リンク プレビューは、チャットまたはプライベート チャネルでは機能しません。

## <a name="microsoft-power-platform-in-microsoft-teams"></a>Microsoft Teams の Microsoft Power Platform

他の Microsoft Power Platform アプリも、Microsoft Teams と統合されています。

- [Power Platform の管理者エクスペリエンス](/power-platform/admin/about-teams-environment)
- [Power Automate](/power-automate/teams/overview)
- [Power Apps](/powerapps/teams/overview)
- [Power Virtual Agents](/power-virtual-agents/)

## <a name="next-steps"></a>次のステップ

- [Microsoft Teams に Power BI コンテンツを埋め込む](service-embed-report-microsoft-teams.md)
- [Microsoft Teams で Power BI リンク プレビューを入手する](service-teams-link-preview.md)
- [Power BI サービスから直接、Microsoft Teams でチャットする](service-share-report-teams.md)

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
