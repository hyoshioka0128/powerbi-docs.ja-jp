---
title: Power BI Desktop での証明書失効の確認
description: Power BI Desktop で、UI とレジストリで証明書を失効させる方法
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 01/25/2021
LocalizationGroup: Create reports
ms.openlocfilehash: 482f0f8279de9818b631ff79e7b37a215e7397bd
ms.sourcegitcommit: 7ed995eed0fd6e718748accf87bae384211cd95d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2021
ms.locfileid: "99056368"
---
# <a name="certificate-revocation-in-power-bi-desktop"></a>Power BI Desktop での証明書失効

Power BI で証明書の確認を有効または無効にする方法は、2 つあります。 2020 年 11 月に、Web 接続に関するシンプルなオン/オフの証明書失効の確認が Power BI Desktop に導入されました。 これで、証明書失効の確認をよりきめ細かく制御できるようになりました。

## <a name="simple-certificate-revocation"></a>シンプルな証明書失効

Power BI Desktop のユーザー インターフェイスで、この機能を有効または無効にすることができます。

- **[ファイル]** メニュー > **[オプションと設定]**  >  **[オプション]** で、 **[セキュリティ]** を選択し、その後 **[証明書失効の確認を有効にします]** を選択または選択解除します。

## <a name="more-fine-grained-control"></a>よりきめ細かな制御

3 つめのオプションを使用すると証明書失効の確認をよりきめ細かく制御することができます。 

- **基本** 基本的な確認の場合、証明書によって指定されていないなど、失効状態が不明な証明書が受け入れられます。 この確認は、企業のプロキシ サーバーを使用している組織にとって重要です。 これは Power BI Desktop でチェックボックスをオンにするのと同じです。
- **無効** Power BI Desktop でチェックボックスをオフにした場合と同じです。
- **包括的** "*包括的*" モードの場合、失効の確認を無効または有効にすることができます。失効状態が不明な証明書は受け入れられません。 


|証明書失効の情報の状態 | 包括的な確認 | 基本的な確認 | なし |
|---------|---------|---------|---------|
|取り消し     |  ❌  | ❌  | ✔   |
|Unknown  |  ❌    |  ✔   |    ✔  |
|失効していない  | ✔  |    ✔ |    ✔  |

シンプルな [有効] または [無効] チェックボックスは、引き続き Power BI Desktop のユーザー インターフェイスに存在しています。 よりきめ細かい制御を使用するには、次の DWORD レジストリ値を設定します: `DisableCertificateRevocationCheck`。 この値は Power BI Desktop レジストリ キーに設定します。 ご使用のオペレーティング システムに応じて、次のいずれかになります。

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
|0     | Basic   | 失効状態が不明な証明書が受け入れられます。 Power BI Desktop でチェックボックスをオンにするのと同じです。 |
|1     | 無効  | すべての失効確認が無視されます。 Power BI Desktop でチェックボックスをオフにするのと同じです。  |
|2     | 包括的  |  証明書を失効させないことが必要となります。 失効状態が不明な証明書は受け入れられません。 |

このレジストリ設定を構成することで、現在提供されているよりきめ細かな制御を活用できます。