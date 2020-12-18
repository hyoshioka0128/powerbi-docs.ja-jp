---
title: Power BI 埋め込み分析で動的バインドを使用してレポートをデータセットに接続する
description: 動的バインドを使用して、レポートを埋め込む方法について学習します。
author: KesemSharabi
ms.author: kesharab
ms.topic: how-to
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 11/07/2019
ms.openlocfilehash: d8a460f68838faab11cdab6d39f0e757a9789899
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97098377"
---
# <a name="connect-a-report-to-a-dataset-using-dynamic-binding"></a>動的バインドを使用してレポートをデータセットに接続する 

レポートがデータセットに接続されている場合は、動的バインドを使用することができます。 レポートとデータセット間の接続は、"*バインド*" と呼ばれます。 バインドが事前に決定されるのではなく、埋め込みの時点で決定される場合、そのバインドは動的バインドと呼ばれます。

"*動的バインド*" を使用して、Power BI レポートを埋め込む場合は、ユーザーの資格情報に応じて、同じレポートを異なるデータセットに接続することができます。

これは、1 つのレポートを使用し、接続されているデータセットに応じて、異なる情報を表示できることを意味します。 たとえば、小売売上の値を示すレポートを別の小売業者のデータセットに接続し、接続されている小売業者のデータセットに応じて、異なる結果を得ることができます。

レポートとデータセットは、必ずしも同じワークスペースに存在している必要はありません。 両方のワークスペース (レポートが含まれるものとデータセットが含まれるもの) が、[容量](azure-pbie-create-capacity.md)に割り当てられている必要があります。

埋め込みプロセスの一環として、確実に、"*十分なアクセス許可を持つトークンを生成*" し、"*構成オブジェクトを調整*" してください。

## <a name="generating-a-token-with-sufficient-permissions"></a>十分なアクセス許可を持つトークンの生成

動的バインドは、"*組織向けの埋め込み*" と "*顧客向けの埋め込み*" の両方のシナリオでサポートされます。 次の表では、各シナリオの考慮事項について説明します。

|シナリオ  |データ所有権  |トークン  |必要条件  |
|---------|---------|---------|---------|
|*組織向けの埋め込み*    |ユーザー所有データ         |Power BI ユーザーのアクセス トークン         |使用する Azure AD トークンを所有するユーザーには、すべての成果物に対する適切なアクセス許可があることが必要です。         |
|*顧客向けの埋め込み*     |アプリ所有データ         |Power BI ユーザーではないユーザーのアクセス トークン         |レポートと動的にバインドされたデータセットの両方に対するアクセス許可を含んでいることが必要です。 複数の成果物をサポートする埋め込みトークンを生成するには、[複数の項目の埋め込みトークンを生成するための API](/rest/api/power-bi/embedtoken/generatetoken) を使用します。         |

## <a name="adjusting-the-config-object"></a>構成オブジェクトを調整する
構成オブジェクトに `datasetBinding` を追加します。 以下の例を参照として使用します。

```javascript
var config = {
    type: 'report',
    tokenType: models.TokenType.Embed,
    accessToken: accessToken,
    embedUrl: embedUrl,
    id: "reportId", // The wanted report id
    permissions: permissions,

    // -----  Adjustment required for dynamic binding ---- //
    datasetBinding: {
        datasetId: "notOriginalDatasetId",  // </The wanted dataset id
    }
    // ---- End of dynamic binding adjustment ---- //
};

// Get a reference to the embedded report HTML element
var embedContainer = $('#embedContainer')[0];

// Embed the report and display it within the div container
var report = powerbi.embed(embedContainer, config);
```

## <a name="next-steps"></a>次のステップ

Power BI での埋め込みに馴染みのない方は、Power BI のコンテンツを埋め込む方法を次のチュートリアルでご覧いただけます。
* [チュートリアル:顧客向けのアプリケーションに Power BI コンテンツを埋め込む](embed-sample-for-customers.md)
* [チュートリアル:組織向けのアプリケーションに Power BI コンテンツを埋め込む](embed-sample-for-your-organization.md)