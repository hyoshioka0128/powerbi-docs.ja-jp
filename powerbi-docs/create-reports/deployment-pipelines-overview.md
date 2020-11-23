---
title: デプロイ パイプラインの概要
description: Power BI のデプロイ パイプラインについて説明します
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: contperfq1
ms.date: 10/21/2020
ms.openlocfilehash: b0b8d61224a91cd069caf48a2d321979ac2d291d
ms.sourcegitcommit: cc20b476a45bccb870c9de1d0b384e2c39e25d24
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2020
ms.locfileid: "94513300"
---
# <a name="introduction-to-deployment-pipelines"></a>デプロイ パイプラインの概要

現代の組織にとって、分析は意思決定を行う上で必要不可欠な要素です。 Power BI を分析ツールとして使用することが増えたことで、より多くのデータを使用し、より魅力的に、そしてよりわかりやすいようにする必要性が出てきました。 ただし、これだけでなく、Power BI は常に利用可能で信頼性の高いものである必要があります。 これらの要件を満たすため、BI 作成者は効率的に共同作業を行う必要があります。

デプロイ パイプライン ツールを使用すると、BI 作成者は組織のコンテンツのライフサイクルを管理できます。 これは、Premium 容量を持つ企業内の作成者にとって、効率的で再利用可能なツールです。 デプロイ パイプラインを使用すると、ユーザーがコンテンツを使用する前に、作成者が Power BI コンテンツを開発してテストできます。 コンテンツの種類には、レポート、ダッシュボード、データセットが含まれます。

このツールは、次の 3 つのステージからなるパイプラインとして設計されています。

* **<a name="development"></a>開発**
    
    このステージは、他の作成者と共に新しいコンテンツを設計、構築、アップロードするために使用されます。 これは、デプロイ パイプラインの最初のステージです。

* **<a name="test"></a>テスト**

    コンテンツにすべての変更を加えると、テスト ステージに入ることができます。 このテスト ステージに移動できるように、変更されたコンテンツをアップロードします。 テスト環境で実行できることの 3 つの例を次に示します。

    * テスト担当者およびレビュー担当者とコンテンツを共有する

    * 大量のデータがあるテストを読み込んで実行する

    * アプリをテストして、エンド ユーザー向けにどのように表示されるかを確認する

* **<a name="production"></a>運用**

    コンテンツのテスト後、運用ステージを使用して、コンテンツの最終バージョンを組織内のビジネス ユーザーと共有します。

![開発、テスト、運用という 3 つのステージすべてが設定された、動作中のデプロイ パイプラインのスクリーンショット。](media/deployment-pipelines-overview/deployment-pipelines.png)

## <a name="next-steps"></a>次の手順

>[!div class="nextstepaction"]
>[デプロイ パイプラインの使用を開始する](deployment-pipelines-get-started.md)

>[!div class="nextstepaction"]
>[デプロイ パイプライン プロセスを理解する](deployment-pipelines-process.md)

>[!div class="nextstepaction"]
>[デプロイ パイプラインのトラブルシューティング](deployment-pipelines-troubleshooting.md)

>[!div class="nextstepaction"]
>[デプロイ パイプラインのベスト プラクティス](deployment-pipelines-best-practices.md)
