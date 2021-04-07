---
title: 証明書失効の確認、Power BI Desktop
description: Power BI Desktop の UI とレジストリで失効した証明書を使用しているかどうかを確認する方法
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 03/10/2021
LocalizationGroup: Create reports
ms.openlocfilehash: 7962529bec11dc05d0abceecae41b9a10effcd36
ms.sourcegitcommit: 644e5a3872f2a8e020fe44c4ec62a26ccc9a6a4e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2021
ms.locfileid: "105008157"
---
# <a name="certificate-revocation-check-power-bi-desktop"></a>証明書失効の確認、Power BI Desktop

証明書によって、オンライン データ ソースへの接続のセキュリティが確保されます。 接続する前に、証明書が失効しているかどうかを確認できます。 Power BI では、証明書の確認を有効または無効にする次の 2 つの方法を提供しています。 

- Power BI Desktop の [オプション] の使用。
- レジストリの編集。

## <a name="revocation-check-options"></a>失効確認のオプション

どちらの方法にも、可能性のある設定として次の 3 つがあります。

- **包括的な確認**: 失効している証明書と、失効情報のない証明書を拒否します。
- **基本的な確認**: 失効している証明書のみを拒否します。 失効情報のない証明書は許可されます。 これは、企業のプロキシ サービスを使用している一部の組織にとって重要です。
- **[なし]** または **[無効]** : Power BI では失効情報を確認しません。 有効な証明書はすべて許可されます。

|証明書の失効情報の状態 | 包括的な確認 | 基本的な確認 | なし/無効 |
|---------|---------|---------|---------|
|取り消し     |  ❌  | ❌  | ✔   |
|Unknown  |  ❌    |  ✔   |    ✔  |
|失効していない  | ✔  |    ✔ |    ✔  |

## <a name="in-power-bi-desktop"></a>Power BI Desktop の場合

Power BI Desktop のユーザー インターフェイスで、確認を有効または無効にすることができます。 **[ファイル]** メニュー > **[オプションと設定]**  >  **[オプション]** で、 **[セキュリティ]** を選択してから、次の 3 つのオプションのいずれかを選択します。

- **包括的な確認**
- **基本的な確認**
- **なし**

**[基本的な確認]** が既定の選択です。

:::image type="content" source="media/desktop-certificate-revocation/desktop-check-certificate-revocation.png" alt-text="証明書失効確認のダイアログ ボックス":::

## <a name="in-registry-settings"></a>レジストリの設定の場合

証明書失効の確認は、DWORD レジストリ値 `DisableCertificateRevocationCheck` を設定して制御することもできます。 また、管理者はこの方法を使用して、組織全体の設定を制御することもできます。

- **Basic**
- **[無効]** は、Power BI Desktop での **[なし]** と同じです。
- **包括的**

Power BI Desktop のレジストリ キーで DWORD レジストリ値 `DisableCertificateRevocationCheck` を設定します。 このキーは、オペレーティング システムに応じて、次のいずれかの形式になります。

```
HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Microsoft Power BI Desktop
```

または:

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Power BI Desktop
```

レジストリ値を次のいずれかの値に設定します。 

|値  |モード  |構成  |
|---------|---------|---------|
|0     | Basic   | 失効状態が不明な証明書が受け入れられます。 Power BI Desktop での [基本的な確認] に相当します。 |
|1     | 無効  | すべての失効確認が無視されます。 Power BI Desktop での [なし] に相当します。  |
|2     | 包括的  |  証明書を失効させないことが必要となります。 失効状態が不明な証明書は受け入れられません。 Power BI Desktop での [包括的な確認] に相当します。 |
