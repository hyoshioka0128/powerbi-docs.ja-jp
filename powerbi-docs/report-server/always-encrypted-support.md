---
title: Power BI Report Server の Always Encrypted
description: この記事では、データ ソースの種類 Microsoft SQL Server および Microsoft Azure SQL Database を使用する場合に Power BI Report Server でサポートされる Always Encrypted について説明します。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: cfinlan
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 01/22/2020
ms.openlocfilehash: 4851a20ecd406ffe2a460ba52833cca420b517da
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415544"
---
# <a name="always-encrypted-in-power-bi-report-server"></a>Power BI Report Server の Always Encrypted

この記事では、データ ソースの種類 Microsoft SQL Server および Microsoft Azure SQL Database を使用する場合に Power BI Report Server でサポートされる Always Encrypted について説明します。 SQL Server の Always Encrypted 機能の詳細については、記事「[Always Encrypted](/sql/relational-databases/security/encryption/always-encrypted-database-engine)」を参照してください。

## <a name="always-encrypted-user-isolation"></a>Always Encrypted ユーザーの分離

現時点では、ユーザーがレポートへのアクセス権を持っている場合、Power BI Report Server はレポート内の Always Encrypted 列へのアクセスを制限しません。  このため、列マスター キーによる列暗号化キーへのアクセス権がサーバーに付与されている場合、ユーザーはアクセス可能なレポートのすべての列にアクセスできます。

## <a name="always-encrypted-column-usage"></a>Always Encrypted 列の使用法

### <a name="key-storage-strategies"></a>キーの格納戦略

|ストレージ  |サポートされています  |
|---------|---------|
|Windows 証明書ストア | はい |
|Azure Key Vault | いいえ |
| Cryptography Next Generation (CNG) | いいえ |

### <a name="certificate-storage-and-access"></a>証明書の格納とアクセス

証明書にアクセスする必要があるアカウントはサービス アカウントです。 証明書は、ローカル コンピューターの証明書ストアに格納する必要があります。 詳細については、次のトピックを参照してください。

- [レポート サーバー サービス アカウントの構成](/sql/reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager) (Configuration Manager)
- SQL Server に関する記事「Always Encrypted の列マスター キーを作成して保存する」の「[証明書をアプリケーションとユーザーが使用できるようにする](/sql/relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted#making-certificates-available-to-applications-and-users)」セクション。

### <a name="column-encryption-strategy"></a>列暗号化戦略

Power BI Report Server では、列暗号化戦略として、*決定論的* 暗号化または *ランダム化* を使用できます。 次の表では、使用する戦略による違いについて説明します。

|用途  |決定的  |ランダム化  |
|---------|---------|---------|
|クエリ (SELECT ステートメントなど) の結果でそのまま読み取ることができる。 | はい  | はい  |
|クエリで Group By エントリとして使用できる。 | はい | いいえ |
|COUNT および DISTINCT を除いて、集計フィールドとして使用できる。 | いいえ (COUNT および DISTINCT を除く) | いいえ |
|レポート パラメーターとして使用できる。 | はい | いいえ |

詳細については、[決定論的暗号化とランダム化暗号化の比較](/sql/relational-databases/security/encryption/always-encrypted-database-engine#selecting--deterministic-or-randomized-encryption)に関するページを参照してください。

### <a name="parameter-usage"></a>パラメーターの使用法

パラメーターの使用法は決定論的暗号化にのみ適用されます。

**単一値パラメーター**。  Always Encrypted 列に対して単一値パラメーターを使用できます。

**複数値パラメーター**。 Always Encrypted 列に対して複数の値を持つ複数値パラメーターを使用することはできません。

**カスケード パラメーター**。 次の条件を "*すべて*" 満たす場合、Always Encrypted でカスケード パラメーターを使用できます。

- すべての Always Encrypted 列は、決定論的戦略による Always Encrypted 列である必要がある。
- Always Encrypted 列に対して使用されるパラメーターはすべて単一値パラメーターである。
- すべての SQL 比較で、等号 (=) 演算子を使用する。

## <a name="datatype-support"></a>データ型のサポート

| SQL データ型 | フィールドの読み取りをサポート | Group By 要素としての使用をサポート | サポートされる集計 (COUNT、DISTINCT、MAX、MIN、SUM など) | パラメーターを使用した等値によるフィルター処理をサポート | メモ |
| --- | --- | --- | --- | --- | --- |
| int | はい | はい | COUNT、DISTINCT | はい (Integer として) |   |
| float | はい | はい | COUNT、DISTINCT | はい (Float として) |   |
| nvarchar | はい | はい | COUNT、DISTINCT | はい (Text として) | 明確な暗号化では、バイナリ 2 文字型の列の並べ替え順序を持つ列の照合順序を使用する必要があります。 詳細については、SQL Server の「[Always Encrypted](/sql/relational-databases/security/encryption/always-encrypted-database-engine#selecting--deterministic-or-randomized-encryption)」の記事を参照してください。  |
| varchar | はい | はい | COUNT、DISTINCT | いいえ |   |
| decimal | はい | はい | COUNT、DISTINCT | いいえ |   |
| numeric | はい | はい | COUNT、DISTINCT | いいえ |   |
| datetime | はい | はい | COUNT、DISTINCT | いいえ |   |
| datetime2 | はい | はい | COUNT、DISTINCT | はい (Date/Time として) | 列にミリ秒の精度がない (つまり、datetime2(0) が指定されていない) 場合にサポート |

## <a name="aggregation-alternatives"></a>集計の代替方法

現在、決定論的 Always Encrypted 列に対してサポートされている集計は、等号 (=) 演算子を直接使用する集計のみです。 SQL Server のこの制限は、Always Encrypted 列の性質に起因します。 ユーザーは、データベースではなくレポート内で集計する必要があります。

## <a name="always-encrypted-in-connection-strings"></a>接続文字列内の Always Encrypted

SQL Server データ ソースの接続文字列で Always Encrypted を有効にする必要があります。 有効化の詳細については、「[アプリケーション クエリで Always Encrypted を有効にする](/sql/relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider#enabling-always-encrypted-for-application-queries)」を参照してください。

## <a name="next-steps"></a>次のステップ

SQL Server および Azure SQL Database での [Always Encrypted](/sql/relational-databases/security/encryption/always-encrypted-database-engine)

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。