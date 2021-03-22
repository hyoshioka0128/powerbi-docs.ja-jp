---
title: Power BI でのデータ ソースからの秘密度ラベルの継承
description: Power BI データセットに、データ ソースから秘密度ラベルを継承する方法について説明します
author: paulinbar
ms.author: painbar
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-eim
ms.topic: conceptual
ms.custom: ''
ms.date: 03/11/2021
LocalizationGroup: Data from files
ms.openlocfilehash: bc61c222c8c91e78e4c7f1dcc9840ca3bb866342
ms.sourcegitcommit: 583341e8cfd76d2e7751821c554c28f28991e53c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2021
ms.locfileid: "103465084"
---
# <a name="sensitivity-label-inheritance-from-data-sources-preview"></a>データ ソースからの秘密度ラベルの継承 (プレビュー)

サポートされているデータ ソース内の秘密度ラベル付きのデータに接続する Power BI のデータセットが、それらのラベルを継承できるようになります。これにより、そのデータは、分類されセキュリティで保護されたまま、Power BI に取り込まれます。

現在サポートされているデータ ソース:
* Azure Synapse Analytics (旧称 SQL Data Warehouse)
* Azure SQL Database

動作できるようにするには、[そのテナントでデータ ソースからの機密性ラベルの継承を有効にする必要があります](service-admin-portal.md#apply-sensitivity-labels-from-data-sources-to-their-data-in-power-bi-preview)。

## <a name="requirements"></a>要件
* データ ソース内のデータには、Microsoft Information Protection ラベルを付ける必要があります。 これを実現するには、2 段階の Purview フローを使用します。
    1. [秘密度ラベルをデータに自動的に適用します](/azure/purview/create-sensitivity-label)。
    1. [Azure Purview ラベルを使用して Azure SQL データを分類します](/azure/sql-database/scripts/sql-database-import-purview-labels)。
* ラベルのスコープは、 **[Files and emails]\(ファイルとメール\)** と **[Azure Purview assets]\(Azure Purview 資産\)** である必要があります。 「[Azure Purview への秘密度ラベルの拡張](/azure/purview/create-sensitivity-label#extending-sensitivity-labels-to-azure-purview)」と「[新しい秘密度ラベルの作成または既存のラベルの変更](/azure/purview/create-sensitivity-label#creating-new-sensitivity-labels-or-modifying-existing-labels)」を参照してください。
* [Power BI で秘密度ラベルを有効にする必要があります](service-security-enable-data-sensitivity-labels.md)。
* **[[Power BI のデータにデータ ソースの秘密度ラベルを適用する (プレビュー)]](service-admin-portal.md#apply-sensitivity-labels-from-data-sources-to-their-data-in-power-bi-preview)** テナント管理者設定を有効にする必要があります。
* ラベルを適用するためのすべての条件が満たされている必要があります。

## <a name="inheritance-behavior"></a>継承動作
* Power BI サービスでは、データセットがデータ ソースに接続されると、Power BI によってラベルが継承され、それがデータセットに自動的に適用されます。 以降は、サービスでデータセットが更新されると継承が発生します。 
* データ ソースにさまざまなレベルの秘密度ラベルがある場合、継承には最も制限の厳しいものが選択されます。 適用するには、そのラベル (最も制限の厳しいもの) をデータセット所有者に公開する必要があります。
* データ ソースのラベルによって、データセットに手動で適用されたラベルが上書きされることはありません。
* データ ソースの制限の緩いラベルによって、データセットの制限の厳しいラベルが上書きされることはありません。
* 何らかの理由でデータ ソースのラベルが適用されていない場合でも、データセットの更新は成功します。 

>[!NOTE]
> データセットの所有者が Power BI で秘密度ラベルを適用する権限を持っていない場合、または対象の特定のラベルがデータセットの所有者に対して公開されていない場合、継承は行われません。

## <a name="limitations"></a>制限事項
* データ ソースからの継承は、現在 Power BI Desktop ではサポートされていません。 
* データ ソースからの継承は、クラシック ワークスペースにあるデータセットではサポートされていません。
* データ ソースからの継承は、メタデータが拡張されたデータセットでのみサポートされます。 詳細については、「[拡張データセット メタデータの使用](../connect-data/desktop-enhanced-dataset-metadata.md)」を参照してください。
* データ ソースからの継承は、データのインポート接続モードを使用するデータセットでのみサポートされます。 ライブ接続と DirectQuery 接続はサポートされていません。
* データ ソースからの継承は、ゲートウェイまたは Azure Virtual Network (VNet) を介した接続ではサポートされていません。

## <a name="next-steps"></a>次の手順
* [データ ソースからの秘密度ラベルの継承を有効にする](service-admin-portal.md#apply-sensitivity-labels-from-data-sources-to-their-data-in-power-bi-preview)
* [秘密度ラベルの概要](service-security-sensitivity-label-overview.md)