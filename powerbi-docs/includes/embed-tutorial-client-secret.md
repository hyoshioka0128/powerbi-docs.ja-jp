---
title: 埋め込み分析チュートリアルのクライアント シークレット取得
description: 埋め込み分析チュートリアルのクライアント シークレットを取得します。
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 12/09/2020
ms.custom: include file
ms.openlocfilehash: e1ccc592d7480befe6fb8c8b18b8b8c649312dfa
ms.sourcegitcommit: 4a0ad7612281c187892912b1bfe8102a9fd23de7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106450537"
---
クライアント シークレットを取得するには、これらの手順に従います。

1. [Microsoft Azure](https://ms.portal.azure.com/#allservices) にログインします。

2. **[アプリの登録]** を検索し、 **[アプリの登録]** リンクを選択します。

3. Power BI コンテンツを埋め込むために使用する Azure AD アプリを選択します。

4. **[管理]** で、 **[証明書とシークレット]** を選択します。

5. **[クライアント シークレット]** で、 **[新しいクライアント シークレット]** を選択します。

6. **[クライアント シークレットの追加]** ポップアップ ウィンドウで、アプリケーション シークレットの説明を入力し、アプリケーション シークレットの有効期限を選択し、 **[追加]** を選択します。

7. **[クライアント シークレット]** セクションで、新しく作成されたアプリケーション シークレットの **[値]** 列にある文字列をコピーします。 そのクライアント シークレットの値が "*クライアント ID*" です。

>[!NOTE]
>クライアント シークレットの値が最初に表示されときに、必ずそれをコピーしてください。 このページから移動すると、クライアント シークレットは表示されなくなり、その値を取得できなくなります。
