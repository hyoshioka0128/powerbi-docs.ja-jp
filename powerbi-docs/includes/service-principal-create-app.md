---
title: サービス プリンシパル作成アプリ
description: サービス プリンシパル作成アプリ
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 05/20/2020
ms.custom: include file
ms.openlocfilehash: 0fe3e1743cb8853d6626b59b748d70bfcc292dbd
ms.sourcegitcommit: cd64ddd3a6888253dca3b2e3fe24ed8bb9b66bc6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/03/2020
ms.locfileid: "84315816"
---
1. [Microsoft Azure](https://ms.portal.azure.com/#allservices) にログインします。

2. **[アプリの登録]** を検索し、 **[アプリの登録]** リンクをクリックします。

    ![Azure アプリの登録](media/embedded-service-principal/azure-app-registration.png)

3. **[新規登録]** をクリックします。

    ![新しい登録](media/embedded-service-principal/new-registration.png)

4. 必要な情報を入力します。
    * **名前** - 自分のアプリケーションの名前を入力します
    * **サポートされているアカウントの種類** - サポートされているアカウントの種類を選択します
    * (省略可能) **リダイレクト URI** - 必要に応じて URI を入力します

5. **[登録]** をクリックします。

6. 登録した後、 **[概要]** タブで "*アプリケーション ID*" を使用できます。後で使用できるように、"*アプリケーション ID*" をコピーして保存します。

    ![アプリケーション ID](media/embedded-service-principal/application-id.png)