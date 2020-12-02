---
title: サポート対象の Python パッケージを確認する
description: Power BI でのサポート対象およびサポート非対象の Python パッケージ
author: otarb
ms.author: otarb
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: conceptual
ms.date: 06/26/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 07b16bb90b548f071472f9f7d22095ccdff78f56
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96401721"
---
# <a name="create-visuals-by-using-python-packages-in-the-power-bi-service"></a>Power BI サービスで Python パッケージを使用して視覚化を作成する
Power BI サービスで視覚化を作成するには、強力な [Python プログラミング言語](https://www.python.org/)を使用できます。 多くの Python パッケージが Power BI サービスでサポートされており、サポート対象は常に増え続けています。

次のセクションでは、Power BI でサポートされている Python パッケージの表をアルファベット順で示します。 

## <a name="request-support-for-a-new-python-package"></a>新しい Python パッケージのサポートを要求する
**Power BI サービス** のサポートされている Python パッケージについては、後の **サポートされているパッケージ** に関するセクションをご覧ください。 その一覧にない Python パッケージのサポートを要求する場合は、要求を [Power BI Ideas](https://ideas.powerbi.com) に送信してください。

## <a name="requirements-and-limitations-of-python-packages"></a>Python パッケージの要件と制限事項
Python パッケージにはいくつかの要件と制限事項があります。

* 現在の Python ランタイム:Python 3.7.7。
* Power BI サービスでは、ほとんどの場合、無料、および GPL-2、GPL-3、MIT+ などのオープンソース ソフトウェア ライセンスの Python パッケージがサポートされています。
* Power BI サービスでは、PyPI に公開されているパッケージがサポートされています。 サービスでは、プライベートまたはカスタムの Python パッケージがサポートされていません。 ユーザーには、Power BI サービスでパッケージを使用可能にすることを要求する前に、PyPI でプライベート パッケージを使用できるようにすることをお勧めします。
* **Power BI Desktop** の Python 視覚化の場合は、カスタム Python パッケージを含む任意のパッケージをインストールできます。
* セキュリティおよびプライバシー上の理由から、サービスで World Wide Web 経由でクライアントとサーバー間のクエリを提供する Python パッケージは、サポートされていません。 このような試みに対してはネットワークがブロックされます。
* 新しい Python パッケージを追加するための承認プロセスには、依存関係のツリーがあります。サービスにインストールする必要がある一部の依存関係はサポートされていません。

## <a name="python-packages-that-are-supported-in-power-bi"></a>Power BI でサポートされている Python パッケージ
次の表では、Power BI サービスで **サポートされている** R パッケージを示します。


|        パッケージ        |   バージョン   |                                   リンク                                   |
|-----------------------|-------------|--------------------------------------------------------------------------|
|matplotlib|3.2.1|https://pypi.org/project/matplotlib|
|numpy|1.18.4|https://pypi.org/project/numpy|
|pandas|1.0.1|https://pypi.org/project/pandas|
|scikit-learn|0.23.0|https://pypi.org/project/scikit-learn|
|scipy|1.4.1|https://pypi.org/project/scipy|
|s  eaborn|0.10.1|https://pypi.org/project/seaborn|
|statsmodels|0.11.1|https://pypi.org/project/statsmodels|
|xgboost|1.1.0|https://pypi.org/project/xgboost|

## <a name="next-steps"></a>次の手順
Power BI での Python の詳細については、次の記事を参照してください。

* [Python を使用して Power BI ビジュアルを作成する](desktop-python-visuals.md)
* [Power BI Desktop での Python スクリプトの実行](desktop-python-scripts.md)
* [クエリ エディターでの Python の使用](desktop-python-in-query-editor.md)
