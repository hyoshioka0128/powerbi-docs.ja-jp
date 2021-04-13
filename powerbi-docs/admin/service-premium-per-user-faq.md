---
title: Power BI Premium Per User
description: Power BI Premium Per User オファリングについてよく寄せられる質問とその回答の一覧です。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-premium
ms.topic: conceptual
ms.date: 4/02/2021
LocalizationGroup: Premium
ms.openlocfilehash: 12d9ee066309d26c9c6f2f906e43cf44a0cd75e7
ms.sourcegitcommit: a3b1ccdd18ef705de960625a9715ad5bbc21b1b6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2021
ms.locfileid: "106225842"
---
# <a name="power-bi-premium-per-user"></a>Power BI Premium Per User

Power BI **Premium Per User** を使用することで、組織はユーザーごとに Premium 機能のライセンスを付与できます。 Premium Per User (PPU) には、Power BI Pro ライセンスのすべての機能が含まれるだけでなく、ページ分割されたレポート、AI、Premium サブスクライバーのみが利用できるその他の機能などの機能も追加されています。 

![Premium Per User の有効化](media/service-premium-per-user-faq/premium-per-user-faq-01a.png)

次のセクションでは、Premium Per User (PPU) の使用、管理上の考慮事項、エンド ユーザーが Premium Per User (PPU) ライセンスから期待できることについて説明します。

> [!NOTE]
> この記事には、Premium Per User に関する FAQ の記事に以前含まれていたすべての情報が含まれています。

## <a name="using-premium-per-user-ppu"></a>Premium Per User (PPU) の使用

Premium Per User (PPU) は、Premium 機能をユーザー単位でライセンスするための新しい方法であり、すべての Power BI Pro ライセンス機能と共に、以前は Premium の容量でしか使えなかったページ分割されたレポート、AI などの機能が含まれています。 PPU ライセンスでは、すべての Pro ライセンス機能が PPU に含まれるため、個別の Power BI Pro ライセンスは必要ありません。 

組織で PPU ライセンスが制限されていない限り、Microsoft 365 を通じて Premium Per User (PPU) の試用版を入手できます。 試用版は、Power BI Pro ライセンスを開始する場合と同じく、ポータルを通じて有効になります。

次の表は、Premium 容量に対する Premium Per User (PPU) の機能について説明したものです。


|列 1  |列 2  |列 3  |
|---------|---------|---------|
|モデル サイズの制限     | 100 GB        | 最大 400 GB        |
|[更新頻度]     | 48/日        | 48/日        |
|ページ分割されたレポート     | ✔        | ✔        |
|AI 機能 (AutoML、影響分析、Cognitive Services)     | ✔        | ✔        |
|DirectQuery などの拡張データフロー機能     | ✔        | ✔        |
|使用に基づく集計の最適化     | ✔        | ✔        |
|配置パイプライン     | ✔        | ✔        |
|XMLA エンドポイント接続     | ✔        | ✔        |
|ページの自動更新の機能強化     | ✔        | ✔        |
|Multi-Geo のサポート     | X        | ✔        |
|無制限のディストリビューション     | X        | ✔        |
|オンプレミスの Power BI レポート     | X        | ✔        |
|Bring Your Own Key (BYOK)     | ✔ *       | ✔        |

> [!NOTE]
> Premium Per User (PPU) は、テナント全体で有効になっている場合にのみ BYOK をサポートします。

一部の組織では、Premium 容量を Premium Per User (PPU) ライセンスで補うことを選択します。 ただし、PPU は、既存の Premium 容量にコンテンツを公開するためには必要ありません。


## <a name="administration-of-premium-per-user-ppu"></a>Premium Per User (PPU) の管理

管理者は、**Power BI 管理ポータル** で PPU のライセンス、ユーザー、および設定を管理します。 管理者は、どのユーザーごとの設定を公開するか、どのユーザーに対して PPU ワークスペースの作成が許可されるか、どのワークスペースが Premium または Premium Per User としてマークされているかなどの設定を管理できます。 

Premium Per User (PPU) ライセンスがテナントにプロビジョニングされると、その機能が、有効にするすべてのワークスペースで使用できるようになります。

![Premium Per User の有効化](media/service-premium-per-user-faq/premium-per-user-faq-01a.png)

Premium 容量の設定とは異なり、PPU ライセンスでは、Pro ライセンスでこのような管理を必要としないのと同様に、メモリ管理や CPU 管理は必要ありません。 テナント管理者は、PPU ライセンスの機能設定を選択できますが、特定のワークロードを無効にすることはできません。 

Premium Per User (PPU) と Premium 容量の間で、必要に応じてワークスペースを移動することができます。 そのような移動では、Premium 容量に移行した後、ワークスペース内に存在するデータセットまたはデータフローの完全な更新が必要になります。 ワークスペースの移動を有効にするために使用できる API のセットは限られていますが、ワークロードのオフなどのアクションは含まれていません。


## <a name="end-user-experience"></a>エンド ユーザー エクスペリエンス

ワークスペースが Premium Per User (PPU) ワークスペースとしてマークされると、次の図に示すように、ひし形のアイコンが表示されます。

![Premium Per User アイコン](media/service-premium-per-user-faq/premium-per-user-faq-03.png)    

Premium Per User (PPU) ワークスペースまたはアプリのコンテンツにアクセスするには、ユーザーが Premium Per User ライセンスを持っている必要があります。 この要件には、ユーザーが XMLA エンドポイント、Excel で分析、複合モデルなどを使用してコンテンツにアクセスするシナリオが含まれます。 PPU ライセンスを持っていないユーザーにワークスペースへのアクセスを許可することはできますが、コンテンツにアクセスできないというメッセージが表示されます。 その後、試用版ライセンスを取得するように求められます (資格がある場合)。 資格がない場合、リソースにアクセスするには、管理者によってライセンスが割り当てられている必要があります。

次の表は、どのユーザーが PPU でどの種類のコンテンツを表示できるかを示しています。

![ライセンスの種類に基づいてコンテンツを表示できるユーザーの表](media/service-premium-per-user-faq/premium-per-user-faq-04.png)   

Premium Per User (PPU) は、Power BI Pro ライセンスと同じ方法で埋め込まれた Power BI で動作します。 コンテンツを埋め込むことができ、それを表示するにはユーザーごとに PPU ライセンスが必要です。

### <a name="email-subscriptions-and-ppu"></a>電子メール サブスクリプションと PPU

 添付ファイルがすべてのユーザーについて同じである場合に限り、Premium Per User (PPU) ライセンスまたは Pro ライセンスを持つすべてのユーザーが、サブスクリプションとそれに含まれる添付ファイルを受け取ることができます。 Pro ユーザーは、製品ポータルの内容を表示することはできません。 

受信者ごとに異なるデータを表示できる追加のサブスクリプション機能が導入された場合、それらの機能を使用するには PPU ライセンス (または Premium 容量) が必要になります。 PPU ライセンスでは、外部ユーザーに対する電子メール サブスクリプションは許可されていません。 コンテンツは、外部ユーザーを登録するために Premium 容量でホストされている必要があります。  

Premium Per User (PPU) ワークスペースに存在するデータセットは、そのデータセットを使用して作成されたレポートを含め、ライセンスのないユーザーには表示されません。 たとえば、PPU ワークスペースで Power BI データセットをホストし、それに対してレポートを作成し、非 PPU ワークスペースに公開して、PPU ライセンスを持たないユーザーにレポートへのアクセスを許可することはできません。 同様に、**Web に公開** を使用して共有されている PPU ワークスペースのコンテンツは、Premium 容量でホストされているコンテンツと同じように動作します。

Power BI モバイルは、Premium Per User (PPU) アプリまたはワークスペースに公開されたコンテンツで動作します。

## <a name="considerations-and-limitations"></a>考慮事項と制限事項

Premium Per User ライセンスを使用する場合は、次の考慮事項に注意してください。

* サービス プリンシパルは現在 PPU ではサポートされていません
* PPU の試用版の有効期限が切れても、引き続きワークスペースにはアクセスできますが、ライセンスを必要とするコンテンツは使用できなくなります。 ワークスペースを Premium 容量に移動するか、単に要件をオフにする必要があります
* PPU テナント全体には、Premium 容量に適用されているのと同じ 100 TB のストレージ制限があります
* PPU 用のエクスポート API は、ページ分割されたレポートで使用できます。各ユーザーには 5 分ごとに 1 回の呼び出しという制限があります。 Power BI レポートはサポートされていません。
* 更新の回数は現在制限されていません
* Power BI Premium メトリック アプリは PPU ではサポートされていません
* PPU ワークスペースでデータフローを実行し、別のワークスペースの Power BI データセットにインポートして、PPU ライセンスを持たないユーザーがコンテンツを使用できるようにすることはできません



## <a name="next-steps"></a>次のステップ

* [Power BI Premium とは何ですか?](service-premium-what-is.md)
* [Microsoft Power BI Premium ホワイト ペーパー](https://aka.ms/pbipremiumwhitepaper)
* [Power BI のエンタープライズ展開の計画に関するホワイト ペーパー](https://aka.ms/pbienterprisedeploy)
* [Extended Pro Trial のアクティブ化](../fundamentals/service-self-service-signup-for-power-bi.md)
* [Power BI Embedded のよくあるご質問](../developer/embedded/embedded-faq.md)

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
