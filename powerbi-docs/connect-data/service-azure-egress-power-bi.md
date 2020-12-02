---
title: Power BI と Azure エグレス
description: Azure エグレスの料金と Power BI をテナントの場所と Power BI Premium に基づいて理解する
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 05/08/2019
LocalizationGroup: Data from databases
ms.openlocfilehash: 8fec8f4fa7a78a69693d4a200baa14e905cee943
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410691"
---
# <a name="power-bi-and-azure-egress"></a>Power BI と Azure エグレス

Power BI と共に Azure データ ソースを使用するとき、Power BI テナントを Azure データ ソースと同じリージョンに置くことで Azure エグレス料金を回避できます。

Power BI テナントがデータ ソースをデプロイしたリージョンと同じ Azure リージョンにデプロイされているとき、スケジュールした更新と DirectQuery のやりとりに対してエグレス料金が発生しません。 

## <a name="determining-where-your-power-bi-tenant-is-located"></a>Power BI テナントの場所を確認する

Power BI テナントの場所を見つける方法については、「[Power BI テナントの場所](../admin/service-admin-where-is-my-tenant-located.md)」という記事を参照してください。

Power BI Premium Multi-Geo のお客様については、Power BI テナントが一部の Azure ベース データ ソースにとって最適な場所にない場合、目的の Azure リージョンに Power BI Premium Multi-Geo をデプロイし、Power BI テナントと Azure データ ソースを同じ Azure リージョンに置くことの利点を得ることができます。

## <a name="next-steps"></a>次のステップ

Power BI Premium または Multi-Geo に関する詳細については、次のリソースをご覧ください。

* [Microsoft Power BI Premium とは何ですか?](../admin/service-premium-what-is.md)
* [Power BI Premium の購入方法](../admin/service-admin-premium-purchase.md)
* [Power BI Premium の Multi-Geo のサポート (プレビュー)](../admin/service-admin-premium-multi-geo.md)
* [Power BI テナントの場所がわからない](../admin/service-admin-where-is-my-tenant-located.md)
* [Power BI Premium のよく寄せられる質問](../admin/service-premium-faq.md)
