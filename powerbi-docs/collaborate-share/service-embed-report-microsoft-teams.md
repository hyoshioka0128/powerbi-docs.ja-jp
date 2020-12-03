---
title: Microsoft Teams に Power BI レポートを埋め込む
description: 対話形式の Power BI レポートを Microsoft Teams のチャネルまたはチャットに簡単に埋め込むことができます。 .
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 09/21/2020
ms.openlocfilehash: 36973d52f94b806db860b739a84f0c94b2a8945d
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411864"
---
# <a name="embed-power-bi-content-in-microsoft-teams"></a>Microsoft Teams に Power BI コンテンツを埋め込む

対話形式の Power BI レポートを Microsoft Teams のチャネルまたはチャットに簡単に埋め込むことができます。 

## <a name="requirements"></a>要件

Microsoft Teams の **[Power BI]** タブを使用するには、次の要素を確認します。

- Microsoft Teams に **[Power BI]** タブがある。
- Microsoft Teams で **[Power BI]** タブを使用してレポートを追加するには、レポートがホストされているワークスペースで、少なくともビューアー ロールを持っている。 さまざまなロールの詳細については、「[新しいワークスペースのロール](service-new-workspaces.md#roles-in-the-new-workspaces)」をご覧ください。
- Microsoft Teams の **[Power BI]** タブでレポートを表示するには、ユーザーがそのレポートを表示するためのアクセス許可を持っている必要があります。
- ユーザーは、チャネルとチャットにアクセスできる Microsoft Teams ユーザーである必要があります。

Power BI と Microsoft Teams がどのように連携するかの背景とその他の要件については、「[Microsoft Teams と Power BI で共同作業する](service-embed-report-microsoft-teams.md)」を参照してください。

## <a name="embed-a-report-in-microsoft-teams"></a>Microsoft Teams にレポートを埋め込む

Microsoft Teams チャンネルまたはチャットにご利用のレポートを埋め込むには、以下の手順に従ってください。

1. Microsoft Teams でチャネルまたはチャットを開き、 **[+]** アイコンを選択します。

    ![チャネルまたはチャットへのタブの追加のスクリーンショット。](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-add.png)

1. **[Power BI]** タブを選択します。

    ![[Power BI] が表示された Microsoft Teams のタブの一覧のスクリーンショット。](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-tab.png)

1. 提供されているオプションを使用して、ワークスペースまたは Power BI アプリからレポートを選択します。

    ![Microsoft Teams 設定の [Power BI] タブのスクリーンショット。](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-tab-settings.png)

1. タブ名は、レポート名と一致するように自動的に更新されますが、変更することもできます。

1. **[保存]** を選択します。

### <a name="reports-you-can-embed-on-the-power-bi-tab"></a>[Power BI] タブで埋め込むことができるレポート

**[Power BI]** タブでは、次の種類のレポートを埋め込むことができます。

- 対話型レポートとページ分割されたレポート。
- **[マイ ワークスペース]** 、新しいワークスペース エクスペリエンス、およびクラシック ワークスペースのレポート。
- Power BI アプリのレポート。

## <a name="start-a-conversation"></a>会話の開始

Power BI レポート タブを Microsoft Teams に追加すると、レポートに関するタブの会話が Microsoft Teams によって自動的に作成されます。

- 右上隅にある **[[会話] タブを表示します]** アイコンを選択します。

    ![[[会話] タブを表示します] アイコンのスクリーンショット。](media/service-embed-report-microsoft-teams/power-bi-teams-conversation-icon.png)

    最初のコメントは、レポートへのリンクです。 その Microsoft Teams チャネル内のすべてのユーザーが、会話でレポートを表示して話し合うことができます。

    ![タブの会話のスクリーンショット。](media/service-embed-report-microsoft-teams/power-bi-teams-conversation-tab.png)

## <a name="known-issues-and-limitations"></a>既知の問題と制限事項

- Microsoft Teams では、Power BI レポートの視覚エフェクトからデータをエクスポートすると、データは自動的にダウンロード フォルダーに保存されます。 これは "data (*n*).xlsx" (*n* は同じフォルダーにデータをエクスポートした回数) という Excel ファイルです。
- Power BI ダッシュボードを Microsoft Teams の **[Power BI]** タブに埋め込むことはできません。
- [URL フィルター](service-url-filters.md)は、Microsoft Teams の **[Power BI]** タブではサポートされていません。
- 国内のクラウドでは、この新しい **[Power BI]** タブは使用できません。 Power BI アプリの新しいワークスペース エクスペリエンスやレポートがサポートされていない古いバージョンを使用できる可能性があります。
- タブを保存した後は、タブの設定からタブ名を変更しないでください。 変更するには、 **[名前変更]** オプションを使用します。
- その他の問題については、Microsoft Teams での共同作業に関する記事の「[既知の問題と制限事項](service-collaborate-microsoft-teams.md#known-issues-and-limitations)」セクションを参照してください。

## <a name="next-steps"></a>次の手順

- [Microsoft Teams と Power BI で共同作業する](service-collaborate-microsoft-teams.md)

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
