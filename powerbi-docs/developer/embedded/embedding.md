---
title: 埋め込み BI 分析情報を向上させるための Power BI 埋め込み分析による埋め込み分析
description: Power BI には、Power BI 埋め込み分析のダッシュボードとレポートをアプリケーションに埋め込むための API があります。 Power BI 埋め込み分析を使用して、より優れた埋め込み BI インサイトを有効にします。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: overview
helpviewer_keywords:
- embedded analytics
- embedding
- Power BI embedding
- app owns data
- user owns data
- Power BI APIs
ms.custom: seodec18
ms.date: 05/15/2019
ms.openlocfilehash: c7278dee5957e2b63b6821decec0171ba6b628a0
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887134"
---
# <a name="embedded-analytics-with-power-bi"></a>Power BI を使用した埋め込み分析

Power BI サービス (SaaS) と Azure (PaaS) の Power BI Embedded サービスには、ダッシュボードとレポートの埋め込み用の API があります。 それにより、コンテンツを埋め込む際に、ダッシュボード、ゲートウェイ、ワークスペースなどの最新の Power BI 機能にアクセスできます。

[埋め込みセットアップ ツール](https://aka.ms/embedsetup)に移動し、すばやく開始してサンプル アプリケーションをダウンロードすることができます。

適切なソリューションを選択します。

* [組織向けの埋め込み](embedding.md#embedding-for-your-organization)を使って、Power BI サービスを拡張することができます。 これを行うには、[埋め込みセットアップ ツール](https://app.powerbi.com/embedsetup)で、"*組織向けに埋め込む*" ソリューションを実装します。
* [顧客向けの埋め込み](embedding.md#embedding-for-your-customers)では、Power BI アカウントがないユーザーのためにダッシュボードとレポートを埋め込むことができます。 これを行うには、[埋め込みセットアップ ツール](https://app.powerbi.com/embedsetup)で、"*顧客向けの埋め込み*" ソリューションを実装します。

![PBIE サンプル](media/embedding/what-can-you-do-02.png)

## <a name="use-apis"></a>API の使用

Power BI コンテンツを埋め込む主なシナリオは 2 つあります。
- (Power BI ライセンスを所有している) 組織のユーザー向けの埋め込み。 
 
- Power BI ライセンスを要求しない、ユーザーおよび顧客向けの埋め込み。 

[Power BI REST API](/rest/api/power-bi/) は両方のシナリオに対応します。

Power BI ライセンスのない顧客やユーザーの場合、同じ API を使用して、組織用と顧客用のダッシュボードやレポートをカスタム アプリケーションに埋め込むことができます。 顧客には、アプリケーションで管理されるデータが表示されます。 また、組織の Power BI ユーザーには、Power BI で直接か、埋め込みアプリケーションのコンテキストで *自分のデータ* を表示するための追加オプションが与えられます。 埋め込みのニーズに合わせて JavaScript や REST API を最大限に活用できます。

埋め込みのしくみを理解するには、[JavaScript 埋め込みサンプル](https://microsoft.github.io/PowerBI-JavaScript/demo/)をご覧ください。

## <a name="embedding-for-your-organization"></a>組織向けの埋め込み

**組織向けの埋め込み** を使って、Power BI サービスを拡張することができます。 この種類の埋め込みでは、アプリケーションのユーザーがコンテンツを表示するには Power BI サービスにサインインする必要があります。 サインインした組織のユーザーは、自分が所有しているか、誰かが Power BI サービスで自分と共有しているダッシュボードとレポートにのみアクセスできます。

組織向けの埋め込みの例としては、[SharePoint Online](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/)、[Microsoft Teams の統合 (管理者権限が必要です)](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/)、[Microsoft Dynamics](/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard) などの内部のアプリケーションがあります。

組織向けに埋め込むには、「[チュートリアル:組織向けのアプリケーションに Power BI コンテンツを埋め込む](embed-sample-for-your-organization.md)」を参照してください。

編集や保存などのセルフサービス機能は、Power BI ユーザー向けの埋め込みの際に [JavaScript API](https://github.com/Microsoft/PowerBI-JavaScript) を介して使用できます。

[埋め込みセットアップ ツール](https://app.powerbi.com/embedsetup)を利用してサンプル アプリケーションをダウンロードできます。このサンプル アプリケーションでは、組織向けのレポートを段階的に組み込むことができます。

## <a name="embedding-for-your-customers"></a>顧客向けの埋め込み

**顧客向けの埋め込み** では、Power BI アカウントがないユーザーのためにダッシュボードとレポートを埋め込むことができます。 この種類の埋め込みは、*Power BI Embedded* とも呼ばれます。

[Power BI Embedded](azure-pbie-what-is-power-bi-embedded.md) は **Microsoft Azure** サービスの 1 つです。独立系ソフトウェア ベンダー (ISV) と開発者はこのサービスを使用して、ビジュアル、レポート、ダッシュボードをアプリケーションに簡単に埋め込むことができます。 この埋め込みは、容量ベースの時間単位の課金モデルで行われます。

![顧客向けの埋め込みの埋め込みフロー](media/embedding/powerbi-embed-flow.png)

Power BI Embedded は ISV とその開発者、顧客に対して利点があります。 たとえば、ISV は、Power BI Desktop を使用して無料でビジュアルの作成を開始できます。 ビジュアル分析開発の労力を最小化することで、ISV は市場投入までの時間を短縮し、差別化されたデータによって競合他社より抜きんでることができます。 ISV はさらに埋め込み分析によって生じる付加価値に対する追加料金を請求することも選択できます。

Power BI Embedded を使用する場合、顧客は Power BI について何も知る必要がなくなります。 埋め込みアプリケーションを作成するには、2 つの方法を利用できます。
- Power BI Pro アカウント 
- サービス プリンシパル 

Power BI Pro アカウントは、アプリケーションのマスター アカウントとして機能します (プロキシ アカウントと考えることができます)。 このアカウントを使用し、アプリケーションの Power BI ダッシュボードおよびレポートにアクセスできる埋め込みトークンを生成できます。

[サービス プリンシパル](embed-service-principal.md)を使用すると、**アプリ専用** トークンを使用して、アプリケーションに Power BI コンテンツを埋め込むことができます。 また、アプリケーションの Power BI ダッシュボードおよびレポートにアクセスできる埋め込みトークンを生成できます。

開発者は Power BI Embedded を使用すると、ビジュアルと分析の開発ではなく、アプリケーションの中核的機能の構築に時間を費やすことができます。 また、顧客のレポートとダッシュボードの需要をすばやく満たし、完全に文書化された API と SDK に簡単に埋め込むことができます。 ナビゲーションが簡単なデータ探索をアプリで有効にすることで、ISV の顧客は、どのデバイスからでも迅速にデータ ドリブンの意思決定を下すことができるようになります。

> [!IMPORTANT]
> 埋め込みには Power BI サービスが必要ですが、顧客は Power BI アカウントを用意しなくてもアプリケーションの埋め込みコンテンツを表示できます。

運用環境に移行する準備ができたら、ワークスペースを容量に割り当てる必要があります。 アプリケーションで使用できるように、Microsoft Azure で [Power BI Embedded の容量を作成](azure-pbie-create-capacity.md)します。

埋め込みの詳細については、[Power BI コンテンツの埋め込み方法](embed-sample-for-customers.md)に関するページを参照してください。

## <a name="next-steps"></a>次の手順

Power BI コンテンツをアプリケーションに埋め込んだり、顧客向けに Power BI コンテンツを埋め込んだりすることができます。

> [!div class="nextstepaction"]
> [組織向けの埋め込み](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
> [Power BI Embedded とは何ですか?](azure-pbie-what-is-power-bi-embedded.md)

> [!div class="nextstepaction"]
>[顧客向けに埋め込む](embed-sample-for-customers.md)

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。