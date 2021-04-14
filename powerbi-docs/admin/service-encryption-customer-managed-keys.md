---
title: Power BI でカスタマー マネージド キーを使用する
description: Power BI でカスタマー マネージド キーを使用する方法について学習します。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 11/11/2020
LocalizationGroup: Premium
ms.openlocfilehash: a2f41487f77956749718ae27e0b30a60274fee3f
ms.sourcegitcommit: 8cccc80f30ee5a4138ce48e44d3442a5ec6bce54
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2021
ms.locfileid: "107219869"
---
# <a name="use-customer-managed-keys-in-power-bi"></a>Power BI でカスタマー マネージド キーを使用する

Power BI では、保存データと処理中のデータが暗号化されます。 既定では、Power BI で Microsoft マネージド キーを使用してデータを暗号化します。 組織は、レポート イメージから Premium 容量にインポートされたデータセットまで、Power BI 全体で保存時のユーザー コンテンツの暗号化に独自のキーを使用することを選択できます。 

## <a name="why-use-customer-managed-keys"></a>カスタマー マネージド キーを使用する理由

組織は Power BI カスタマー マネージド キー (CMK) を使用して、クラウド サービス プロバイダー (この場合は Microsoft) と共に保存データの暗号化に関するコンプライアンス要件を満たすことができます。 CMK は新しい Power BI Premium のお客様にのみ提供されます。指定し、管理するキーを利用し、組織は Power BI ユーザー コンテンツを暗号化できます。 カスタマー マネージド キーを失効させると、1 時間以内に Power BI 内のユーザーのコンテンツを、Microsoft を含む全員が読み取ることができなくなります。 BYOK オファリングと比較すると、CMK では、Premium 容量でホストされるレポートとデータセットにインポートされる顧客データに加え、サービスによって生成されるユーザー コンテンツもカバーされます。より厳しいキャッシュ ポリシーが適用され、すべてのデータを暗号化するために 1 つのキーを適用することのみ可能です。


## <a name="how-to-use-customer-managed-keys"></a>カスタマー マネージド キーを使用する方法
Power BI のカスタマー マネージド キーを選択するには、組織はその Microsoft アカウント マネージャーに連絡し、CMK を有効にするために必要な特定のサイズ要件を組織が満たしていることを確認する必要があります。  


## <a name="next-steps"></a>次のステップ

次のリンクには、カスタマー マネージド キーに役立つ可能性がある情報が用意されています。

* [Power BI で独自の暗号化キーを使用する](service-encryption-byok.md)
* [Power BI Premium の Multi-Geo のサポートを構成する](service-admin-premium-multi-geo.md)
* [容量はどのように機能するのか](service-premium-what-is.md#how-capacities-function)
