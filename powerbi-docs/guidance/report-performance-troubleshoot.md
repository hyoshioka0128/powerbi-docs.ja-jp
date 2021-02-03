---
title: Power BI でのレポートのパフォーマンスのトラブルシューティング
description: Power BI でレポートのパフォーマンスが遅い場合に診断するためのトラブルシューティング ガイドです。
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: troubleshooting
ms.date: 04/15/2020
ms.openlocfilehash: 9e9d3fa59defa1c33ba39ed7491ce099f350a0bf
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2021
ms.locfileid: "99088214"
---
# <a name="troubleshoot-report-performance-in-power-bi"></a>Power BI でのレポートのパフォーマンスのトラブルシューティング

この記事で提供するガイダンスを利用すると、開発者と管理者は、レポートのパフォーマンスが遅い問題をトラブルシューティングできます。 Power BI レポートだけでなく、Power BI のページ分割されたレポートにも適用されます。

遅いレポートとは、レポートのユーザーが、レポートを読み込むときや、スライサーや他の機能を使用していて更新するときに、遅いと感じるものです。 レポートが Premium 容量でホストされている場合は、[Power BI Premium メトリック アプリ](../admin/service-admin-premium-monitor-capacity.md)を監視することにより、遅いレポートを特定することもできます。 このアプリは、Power BI Premium サブスクリプションの正常性と容量を監視するのに役立ちます。

## <a name="follow-flowchart-steps"></a>フローチャートの手順に従う

次のフローチャートを使用すると、パフォーマンスが低い原因を理解し、対応を決定できます。

:::image type="content" source="media/report-performance-troubleshoot/flowchart.png" alt-text="記事のテキストで詳しく説明されているフローチャートを示す図。" border="true":::

6 つのフローチャート ターミネータがあり、それぞれで実行するアクションが説明されています。

|ターミネータ|アクション|
|---------|---------|
|![フローチャート ターミネータ 1。](media/common/icon-01-red-30x30.png)|容量の管理<br />容量のスケーリング |
|![フローチャート ターミネータ 2。](media/common/icon-02-red-30x30.png)|普通にレポートを使用しながら容量のアクティビティを調査する|
|![フローチャート ターミネータ 3。](media/common/icon-03-red-30x30.png)|アーキテクチャを変更する<br />Azure Analysis Services を検討する<br />オンプレミスのゲートウェイを調べる|
|![フローチャート ターミネータ 4。](media/common/icon-04-red-30x30.png)|Azure Analysis Services を検討する<br />Power BI Premium を検討する|
|![フローチャート ターミネータ 5。](media/common/icon-05-red-30x30.png)|Power BI Desktop のパフォーマンス アナライザーを使用する<br />レポート、モデル、または DAX を最適化する|
|![フローチャート ターミネータ 6。](media/common/icon-06-red-30x30.png)|サポート チケットを提出する|

## <a name="take-action"></a>アクションの実行

最初の考慮事項は、遅いレポートが Premium 容量でホストされているかどうかを確認することです。

### <a name="premium-capacity"></a>Premium 容量

レポートが Premium 容量でホストされている場合は、**Power BI Premium Metrics アプリ** を使用して、レポート ホスティング容量が頻繁に容量リソースを超えているかどうかを判断します。 CPU については、80% を頻繁に超える場合です。 メモリについては、[アクティブ メモリ メトリック](../admin/service-premium-metrics-app.md#the-active-memory-metric)が 50 を超える場合です。 リソースに負荷がかかっているときは、[容量の管理やスケーリング](../admin/service-admin-premium-manage.md) (フローチャート ターミネータ 1) が必要になる場合があります。 十分なリソースがある場合は、通常のレポートの使用状況において容量のアクティビティを調査します (フローチャート ターミネータ 2)。

### <a name="shared-capacity"></a>共有された容量

レポートが共有容量でホストされている場合、容量の正常性を監視することはできません。 別の調査方法を採用する必要があります。

最初に、1 日または 1 月の間の特定の時間帯にパフォーマンスの低下が発生しているかどうかを確認します。 そうであり、その時間帯に多くのユーザーがレポートを開いている場合は、次の 2 つの方法を検討します。

- データセットを [Azure Analysis Services](/azure/analysis-services/analysis-services-overview) または Premium 容量に移行することで、クエリのスループットを増やします (フローチャート ターミネータ 4)。
- Power BI Desktop の[パフォーマンス アナライザー](../create-reports/desktop-performance-analyzer.md)を使用して、レポートの各要素 (ビジュアルや DAX の数式など) がどのように動作しているかを確認します。 これは、パフォーマンスの問題に影響しているのが、クエリか、またはビジュアルのレンダリングのどちらであるかを判断する場合に、特に役に立ちます (フローチャート ターミネータ 5)。

時間のパターンがないと判断した場合は、次に、パフォーマンスの低下が特定の場所またはリージョンだけのものであるかどうかを検討します。 そうである場合は、データ ソースがリモートであり、ネットワーク通信が遅い可能性があります。 この場合は、次の点を考慮します。

- [Azure Analysis Services](/azure/analysis-services/analysis-services-overview) を使用したアーキテクチャの変更 (フローチャート ターミネータ 3)。
- [オンプレミス データ ゲートウェイのパフォーマンス](/data-integration/gateway/service-gateway-performance)の最適化 (フローチャート ターミネータ 3)。

最後に、時間的なパターンがなく "_かつ_" すべてのリージョンでパフォーマンスの低下が発生している場合は、特定のデバイス、クライアント、または Web ブラウザーでパフォーマンスの低下が発生しているかどうかを調査します。 そうでない場合は、前に説明したように Power BI Desktop の[パフォーマンス アナライザー](../create-reports/desktop-performance-analyzer.md)を使用して、レポートまたはモデルを最適化します (フローチャート ターミネータ 5)。

特定のデバイス、クライアント、または Web ブラウザーがパフォーマンス低下の原因になっていると判断した場合は、[Power BI のサポート ページ](https://powerbi.microsoft.com/support/)でサポート チケットを作成することをお勧めします (フローチャート ターミネータ 6)。

## <a name="next-steps"></a>次の手順

この記事に関する詳細については、次のリソースを参照してください。

- [Power BI ガイダンス](index.yml)
- [レポートのパフォーマンスの監視](monitor-report-performance.md)
- [パフォーマンス アナライザー](../create-reports/desktop-performance-analyzer.md)
- ホワイト ペーパー:[Power BI のエンタープライズ展開の計画](https://go.microsoft.com/fwlink/?linkid=2057861)
- わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
- Power BI チームへのご提案は、 [Power BI を改善するためのアイデアをお寄せください](https://ideas.powerbi.com/)
