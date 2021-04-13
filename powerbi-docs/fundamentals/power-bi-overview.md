---
title: Power BI とは?
description: Power BI の概要と、さまざまなパーツ (Power BI Desktop、Power BI サービス、Power BI モバイル、Report Server、および Power BI Embedded) がどのように組み合わさっているか。
author: mihart
ms.author: mihart
ms.service: powerbi
ms.subservice: pbi-fundamentals
ms.topic: overview
ms.date: 03/29/2021
LocalizationGroup: Get started
ms.openlocfilehash: 398272e6bcb08e8c456d6f32a03cd231173b153e
ms.sourcegitcommit: 10dfa074558a78a82f44bdfa6228c07c7d860257
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/07/2021
ms.locfileid: "106549542"
---
# <a name="what-is-power-bi"></a>Power BI とは?
**Power BI** はソフトウェア サービス、アプリ、コネクタのコレクションで、これらを組み合わせることで、関連性のないデータ ソースから、まとまりがあり、実体験的な対話型洞察を得ることができます。 Excel スプレッドシートや、クラウド ベースとオンプレミスのハイブリッド データ ウェアハウスのコレクションなど、さまざまなデータを使えます。 Power BI を使うと、ご利用のデータ ソースへの接続、重要事項の視覚化と検出、必要に応じた任意のユーザーまたはすべてのユーザーとの共有を、簡単に実行できます。

## <a name="the-parts-of-power-bi"></a>Power BI の構成要素
Power BI は、次の 3 つの基本的なものを始めとして、すべてが連携して機能する複数の要素で構成されています。 
- **Power BI Desktop** と呼ばれる Windows デスクトップ アプリケーション
- **Power BI サービス** と呼ばれるオンラインの SaaS (*サービスとしてのソフトウェア*) サービス 
- Windows、iOS、Android デバイス向けの Power BI **モバイル アプリ**

![Power BI Desktop、サービス、およびモバイルの統合を示す図のスクリーンショット。](media/power-bi-overview/power-bi-overview-blocks.png)

この 3 つの要素 (Power BI Desktop、サービス、モバイル アプリ) は、ユーザーおよびそのロールに対して最も効果的な方法で、ビジネス上の分析情報を作成、共有、使用できるように設計されています。

この 3 つの要素以外にも、Power BI には次の 2 つの要素があります。

- **Power BI Report Builder**。Power BI サービスで共有するページ分割されたレポートを作成するためのものです。 詳細については、この記事で後述する[ページ分割されたレポート](#paginated-reports-in-the-power-bi-service)に関する説明を参照してください。
- **Power BI Report Server**。Power BI Desktop で Power BI レポートを作成してから、それを発行することができるオンプレミスのレポート サーバーです。 詳細については、この記事で後述する [Power BI Report Server](#on-premises-reporting-with-power-bi-report-server) に関する説明を参照してください。

## <a name="how-power-bi-matches-your-role"></a>Power BI とロールの対応
Power BI の使用方法は、プロジェクトまたはチームにおけるユーザーのロールによって異なる場合があります。 ロールが異なれば Power BI の使用方法も異なる可能性があります。

たとえば、あなたはレポートとダッシュボードを表示するために、**Power BI サービス** を主に使うことができます。 大量の計算を行ったりビジネス レポートを作成する同僚は、レポートを作成し、そのレポートをあなたが参照する Power BI サービスに発行するために、**Power BI Desktop** または **Power BI Report Builder** を重点的に使うことができます。 営業担当の別の同僚は、売上ノルマの達成状況の観察や、新しい潜在顧客の詳細を確認するために、**Power BI のスマートフォン アプリ** を主に使うことができます。

開発者であれば、Power BI API を使用してデータをデータセットにプッシュしたり、ダッシュボードとレポートをカスタム アプリケーションに埋め込んだりする可能性があります。 新しいビジュアルのアイデアがあれば、 それを自分で作成して、他のユーザーと共有できます。  

また、作業の目的や、特定のプロジェクトにおけるご自分のロールに応じて、Power BI の各要素をさまざまなタイミングで使い分ける場合もあります。

Power BI の使用方法は、Power BI のどの機能またはサービスがご自分の状況に対して最適なツールとなるかに基づいています。 たとえば、Power BI Desktop を使用して、顧客契約統計に関するレポートを自分のチーム用に作成したり、Power BI サービスのリアルタイム ダッシュボードで在庫や製造の進行状況を確認したりすることができます。 Power BI データセットに基づいて、郵送可能な請求書のページ分割されたレポートを作成できます。 Power BI の各部分を利用できることが、その柔軟性と魅力の理由です。

ご自身のロールに関連するドキュメントについては、次をご覧ください。
- ["*ビジネス ユーザー*"](../consumer/end-user-consumer.md) 向けの Power BI
- ["*レポート作成者*"](desktop-what-is-desktop.md) 向けの Power BI Desktop
- ["*エンタープライズ レポート作成者*"](../paginated-reports/paginated-reports-report-builder-power-bi.md) 向けの Power BI Report Builder
- [*管理者*](../admin/service-admin-administering-power-bi-in-your-organization.md)向け Power BI
- "*開発者向け*" Power BI
    * [Power BI を使用した埋め込み分析](../developer/embedded/embedding.md)
    * [Azure の Power BI Embedded とは何か](../developer/embedded/azure-pbie-what-is-power-bi-embedded.md)
    * [Power BI のビジュアル](../developer/visuals/power-bi-custom-visuals.md)
    * [Power BI API の開発者向け機能](../developer/automation/overview-of-power-bi-rest-api.md)

## <a name="the-flow-of-work-in-power-bi"></a>Power BI のワークフロー
Power BI での一般的なワークフローは、Power BI Desktop でデータ ソースに接続し、レポートを作成することから始まります。 次に、そのレポートを Power BI Desktop から Power BI サービスに発行し、それを共有することで、Power BI サービスとモバイル デバイスのビジネス ユーザーがレポートを表示して操作できるようにします。

このワークフローは一般的で、Power BI の 3 つの主な要素がお互いを補完するしくみを示しています。

こちらに詳細な [Power BI Desktop と Power BI サービスの比較](../fundamentals/service-service-vs-desktop.md)があります。

### <a name="use-the-deployment-pipeline-tool"></a>配置パイプライン ツールを使用する

Power BI サービスでは、ユーザーにリリースする前に、[配置パイプライン ツール](../create-reports/deployment-pipelines-overview.md)を使用して内容をテストできます。 配置パイプライン ツールを使用すると、レポート、ダッシュボード、データセット、およびページ分割されたレポートの配置に役立ちます。 Power BI サービスで[配置パイプラインの使用を開始する](../create-reports/deployment-pipelines-get-started.md?tabs=paginated-reports)方法を参照してください。

## <a name="paginated-reports-in-the-power-bi-service"></a>Power BI サービスでのページ分割されたレポート

別のワークフローには、Power BI サービスのページ分割されたレポートが含まれます。 エンタープライズ レポート作成者は、印刷または共有できるようにページ分割されたレポートをデザインします。 また、これらのレポートを Power BI サービスで共有することもあります。 これらは、1 ページにちょうど収まるように設定されているため "*ページ分割された*" と呼ばれます。 これらは、運用レポート用に、または請求書やトランスクリプトなどのフォームの印刷用に使われることがよくあります。 テーブルが複数のページにまたがる場合でも、テーブルのすべてのデータが表示されます。 Power BI レポート ビルダーは、ページ分割されたレポートを作成するためのスタンドアロン ツールです。

:::image type="content" source="media/power-bi-overview/paginated-report-invoice-power-bi-service.png" alt-text="Power BI サービスでのページ分割されたレポートのスクリーンショット。":::

詳細については、Power BI サービスでの[ページ分割されたレポート](../paginated-reports/paginated-reports-report-builder-power-bi.md)に関する説明を参照してください。

## <a name="on-premises-reporting-with-power-bi-report-server"></a>Power BI Report Server を使用したオンプレミスのレポート

ファイアウォールの背後など、レポートをオンプレミスに保持する必要がある場合はどうすればよいでしょうか。  読み続けてください。

Power BI Report Server によって提供されるすぐに使用できるツールとサービスを使用すれば、Power BI Desktop で Power BI レポートを、そして Report Builder でページ分割されたレポートを作成、展開、管理することができます。

![Power B I Report Server、サービス、モバイルの統合を示すスクリーンショット。](media/power-bi-overview/power-bi-report-server2.png)

Power BI Report Server は、ファイアウォールの背後に展開するソリューションであり、適切なユーザーにさまざまな方法でレポートを配信します。これは、Web ブラウザーでもモバイル デバイスでも表示でき、電子メールとして送信することもできます。 Power BI Report Server は、クラウドの Power BI に対応するため、準備ができたらクラウドに移行することができます。 

[Power BI レポート サーバー](../report-server/get-started.md)の詳細をお読みください。

## <a name="next-steps"></a>次の手順
- [クイック スタート:Power BI サービスの使用方法を学ぶ](../consumer/end-user-experience.md)   
- [チュートリアル: Power BI サービスの概要](service-get-started.md)
- [クイック スタート:Power BI Desktop でデータに接続する](../connect-data/desktop-quickstart-connect-to-data.md)
