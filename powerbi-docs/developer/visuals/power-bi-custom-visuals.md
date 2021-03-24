---
title: 埋め込み BI インサイトの品質を向上させるための Power BI 埋め込み分析の Power BI のビジュアル
description: この記事では、Power BI のカスタム ビジュアルについて説明します。 Power BI 埋め込み分析を使用して、より優れた埋め込み BI インサイトを有効にします。
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: overview
ms.date: 07/14/2020
LocalizationGroup: Visualizations
ms.openlocfilehash: 2e20d28d14788f15d8f654d3449ab3641626faf9
ms.sourcegitcommit: 644e5a3872f2a8e020fe44c4ec62a26ccc9a6a4e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2021
ms.locfileid: "105007203"
---
# <a name="visuals-in-power-bi"></a>Power BI のビジュアル

Power BI には、すぐに使用できる Power BI ビジュアルが多数用意されています。 それらのビジュアルは、[Power BI Desktop](https://powerbi.microsoft.com/desktop/) と [Power BI サービス](https://app.powerbi.com)の両方の [視覚化] ペインで使用可能であり、Power BI コンテンツの作成と編集に使用できます。

:::image type="content" source="media/power-bi-custom-visuals/power-bi-visualizations.png" alt-text="Power BI Desktop と Power BI サービスに表示されたときの Power BI の [視覚化] ウィンドウのスクリーンショット。":::

その他多くの Power BI ビジュアルを Microsoft [AppSource](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fappsource.microsoft.com%2Fen-us%2Fmarketplace%2Fapps%3Fpage%3D1%26product%3Dpower-bi-visuals&data=02%7C01%7CKesem.Sharabi%40microsoft.com%7C6d9286afacb3468d4cde08d740b76694%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637049028749147718&sdata=igWm0e1vXdgGcbyvngQBrHQVAkahPnxPC1ZhUPntGI8%3D&reserved=0) または Power BI から入手できます。 それらのビジュアルは、Microsoft および Microsoft パートナーによって作成され、AppSource 検証チームによってテストおよび検証されています。

ユーザーが独自の Power BI ビジュアルを開発することもできます。これは、ユーザー、ユーザーの組織、または Power BI コミュニティ全体で使用できます。

## <a name="default-power-bi-visuals"></a>既定の Power BI ビジュアル

*Power BI Desktop* および *Power BI サービス* の [視覚化] ペインから利用できる、すぐに使用できる Power BI ビジュアルです。

[視覚化] ペインから Power BI ビジュアルのピン留めを外すには、ビジュアルを右クリックし、 **[ピン留めを外す]** を選択します。

[視覚化] ペインで既定の Power BI ビジュアルを復元するには、 **[カスタム ビジュアルのインポート]** をクリックし、 **[既定の視覚化の復元]** を選択します。 

## <a name="appsource-power-bi-visuals"></a>AppSource の Power BI ビジュアル

Microsoft とコミュニティのメンバーは公共の利益のために Power BI ビジュアルを作成し、[AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals) マーケットプレースに公開しています。 このようなビジュアルをダウンロードして、自身の Power BI レポートに追加することができます。 このような Power BI ビジュアルは Microsoft が機能と品質をテストし、承認しています。

>[!NOTE]
>* SDK で作成された Power BI ビジュアルを使用することで、Power BI テナントの地域、コンプライアンス境界、または各国のクラウド インスタンスの外部にあるサードパーティまたはその他のサービスにデータをインポートしたり、データを送信したりすることができます。
>* Power BI の認定済みビジュアルとは、ビジュアルが外部のサービスまたはリソースにアクセスしないことを確認するために追加でテストされた AppSource のビジュアルです。
>* AppSource から Power BI ビジュアルがインポートされると、追加の通知なしにビジュアルが自動的に更新される可能性があります。

### <a name="what-is-appsource"></a>AppSource とは

[AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals) は Microsoft のソフトウェアのアプリ、アドイン、拡張機能のための場所です。 AppSource は、Microsoft 365、Azure、Dynamics 365、Cortana、Power BI などの製品の何百万人ものユーザーを、これまでより効率よく、洞察力のある方法で仕事をするのに役立つソリューションに結び付けます。

### <a name="certified-power-bi-visuals"></a>認定済み Power BI ビジュアル

認定済み Power BI ビジュアルとは、[AppSource](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fappsource.microsoft.com%2Fen-us%2Fmarketplace%2Fapps%3Fpage%3D1%26product%3Dpower-bi-visuals&data=02%7C01%7CKesem.Sharabi%40microsoft.com%7C6d9286afacb3468d4cde08d740b76694%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637049028749147718&sdata=igWm0e1vXdgGcbyvngQBrHQVAkahPnxPC1ZhUPntGI8%3D&reserved=0) 上のビジュアルのうち、指定された特定のコード要件を満たし、Microsoft Power BI チームによってテストおよび承認されたものです。 テストは、ビジュアルで外部のサービスやリソースへのアクセスが行われないことを確認するように設計されています。

認定済み Power BI ビジュアルの一覧を表示する場合、または自作のものを送信する場合は、[認定済み Power BI ビジュアル](power-bi-custom-visuals-certified.md)に関する記事を参照してください。

### <a name="samples-for-power-bi-visuals"></a>Power BI ビジュアルのサンプル

AppSource 上の各 Power BI ビジュアルには、ビジュアルの動作を示すデータのサンプルが用意されています。 サンプルをダウンロードするには、[AppSource](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fappsource.microsoft.com%2Fen-us%2Fmarketplace%2Fapps%3Fpage%3D1%26product%3Dpower-bi-visuals&data=02%7C01%7CKesem.Sharabi%40microsoft.com%7C6d9286afacb3468d4cde08d740b76694%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637049028749147718&sdata=igWm0e1vXdgGcbyvngQBrHQVAkahPnxPC1ZhUPntGI8%3D&reserved=0) で Power BI ビジュアルを選択し、 *[サンプルを試す]* セクションの **[サンプル レポート]** リンクをクリックします。

## <a name="organizational-store"></a>組織のストア

Power BI 管理者は、Power BI ビジュアルを承認して組織に展開します。 これにより、レポート作成者は、これらの Power BI ビジュアルを簡単に検出、更新、使用できます。 管理者は、バージョンの更新、Power BI ビジュアルの無効化と有効化などのアクションを使用して、これらのビジュアルを簡単に管理できます。

組織のストアにアクセスするには、 *[視覚化]* ペインで **[カスタム ビジュアルのインポート]** をクリックし、 **[Marketplace からインポートする]** を選択してから、 *[Power BI ビジュアル]* ウィンドウの上部にある **[自分の所属組織]** タブを選択します。

[組織のビジュアルに関する詳細は、こちらをご覧ください](power-bi-custom-visuals-organization.md)。

## <a name="visual-files"></a>ビジュアル ファイル

Power BI ビジュアルはパッケージであり、特定の目的を果たすデータをレンダリングするためのコードが含まれています。 カスタム ビジュアルは誰でも作成し、単一の `.pbiviz` ファイルとしてパッケージ化できます。このファイルはその後 Power BI レポートにインポートできます。

Power BI ビジュアルをインポートするには、 *[視覚化]* ペインで **[カスタム ビジュアルのインポート]** をクリックし、 **[ファイルからインポートする]** を選択します。

独自の視覚化を作成して AppSource に追加することに関心がある Web 開発者の場合は、[Power BI の円形カード視覚化の開発](develop-circle-card.md)および [AppSource への Power BI の視覚化の発行](office-store.md)に関する記事で方法を学習できます。

> [!WARNING]
> Power BI ビジュアルには、セキュリティやプライバシーのリスクがあるコードが含まれる場合があります。 レポートにインポートする前に、作成者と Power BI ビジュアルのソースが信頼できることを確認してください。

## <a name="next-steps"></a>次の手順

>[!div class="nextstepaction"]
>[Power BI の円形カード視覚化を開発する](develop-circle-card.md)

>[!div class="nextstepaction"]
>[Power BI ビジュアル プロジェクトの構造](visual-project-structure.md)

>[!div class="nextstepaction"]
>[Power BI ビジュアルのガイドライン](guidelines-powerbi-visuals.md)

>[!div class="nextstepaction"]
>[よく寄せられる質問](power-bi-custom-visuals-faq.yml)

>[!div class="nextstepaction"]
>[Power BI コミュニティ](https://community.powerbi.com/)