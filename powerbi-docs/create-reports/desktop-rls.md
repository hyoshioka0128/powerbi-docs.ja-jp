---
title: Power BI Desktop の行レベルのセキュリティを使用してデータ アクセスを制限する
description: Power BI Desktop 内にインポートしたデータセットと DirectQuery の行レベルのセキュリティを構成する方法。
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.custom: ''
ms.date: 01/31/2020
LocalizationGroup: Create reports
ms.openlocfilehash: 0d5501ba8929318081a5db7e34e80722f2ffbf70
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96412853"
---
# <a name="restrict-data-access-with-row-level-security-rls-for-power-bi-desktop"></a>Power BI Desktop の行レベルのセキュリティを使用してデータ アクセスを制限する

Power BI Desktop で行レベル セキュリティ (RLS) を使用すると、特定のユーザーのデータ アクセスを制限できます。 フィルターは、行レベルでデータを制限します。 役割内でフィルターを定義できます。

Power BI Desktop で Power BI にインポートされたデータ モデルの RLS を構成できます。 SQL Server などの [DirectQuery](../connect-data/desktop-use-directquery.md) を使用しているデータセットに RLS を構成することもできます。 これまで、RLS を実装できるのは、Power BI の外部にあるオンプレミスの Analysis Services モデル内だけでした。 Analysis Services のライブ接続では、オンプレミスのモデルに行レベルのセキュリティを構成します。 このセキュリティ オプションは、ライブ接続データセットには表示されません。

> [!IMPORTANT]
> Power BI サービス内で役割とルールを定義した場合は、Power BI Desktop でこれらの役割を再作成し、サービスにレポートを公開する必要があります。 Power BI サービス内の RLS のオプションについては、[こちら](../admin/service-admin-rls.md)を参照してください。

[!INCLUDE [include-short-name](../includes/rls-desktop-define-roles.md)]

[!INCLUDE [include-short-name](../includes/rls-desktop-view-as-roles.md)]

[!INCLUDE [include-short-name](../includes/rls-limitations.md)]

[!INCLUDE [include-short-name](../includes/rls-faq.md)]

## <a name="next-steps"></a>次の手順

この記事に関する詳細については、次のリソースを参照してください。

- [Power BI での行レベルのセキュリティ (RLS)](../admin/service-admin-rls.md)
- [Power BI Desktop での行レベルのセキュリティ (RLS) のガイダンス](../guidance/rls-guidance.md)
- わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
- Power BI チームへのご提案は、 [Power BI を改善するためのアイデアをお寄せください](https://ideas.powerbi.com/)
