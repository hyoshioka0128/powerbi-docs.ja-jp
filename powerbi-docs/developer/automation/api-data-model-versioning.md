---
title: Power BI データ モデルのバージョン管理
description: OData サービスによって公開されるデータ モデル
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 76947b1e311bbd1a21e09ce39461a70bed61d926
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "79079602"
---
# <a name="data-model-versioning"></a>データ モデルのバージョン管理

Power BI データ モデルなど、OData サービスによって公開されるデータ モデルは、OData サービスとクライアントの間のコントラクトを定義します。 サービスのモデルは、既存のクライアントに障害を発生させない範囲内でのみ、拡張可能です。 プロパティの削除や既存のプロパティの型の変更など、障害につながる変更を行う場合は、新しいモデル用の別のサービス ルート URL でサービスの新バージョンを提供する必要があります。  
  
次のデータ モデルの追加は安全と見なされ、エントリ ポイントをバージョン管理するサービスは必要ありません。  
  
* Null 許容値のプロパティまたは既定値が設定されたプロパティの追加。既存の動的なプロパティと同じ名前が設定されている場合は、既存の動的なプロパティと同じ型 (または基本データ型) を設定する必要があります。  
* Null 許容値またはコレクション値のナビゲーション プロパティの追加。既存の動的なナビゲーション プロパティと同じ名前が設定されている場合は、既存の動的なナビゲーション プロパティと同じ型 (または基本データ型) を設定する必要があります。  
* モデルへの新しいエンティティ型の追加  
* モデルへの新しい複合型の追加  
* 新しいエンティティ セットの追加  
* 新しいシングルトンの追加  
* アクション、関数、アクション インポート、関数インポートの追加
* Null 許容のアクション パラメーターの追加。  
* 型定義または列挙型の追加  
* サービスと正しく対話するために、クライアントによって認識される必要がないモデル要素への注釈の追加  
  
サービスのためにクライアントを準備し、この増分の変更をモデルに加える "***必要があります***"。 特にクライアントは、以前にサービスで定義されていないプロパティと派生型を受け取る準備をする必要があります。  
  
サービスでは、認証されたユーザーに応じてそのデータ モデルを変更する "***べきではありません***"。 データ モデルがユーザーやユーザー グループに依存する場合は、認証が制限されているユーザーに表示されるモデルと完全なモデルを比較するときに、このセクションで定義されているように、すべての変更は安全な変更である必要があります。  
  
OData データ モデル標準の詳細については、[「OData バージョン 4.0 パート 1: Protocol Plus Errata 02」](https://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html) をご覧ください。  
  
## <a name="see-also"></a>参照
[Power BI REST API の概要](https://docs.microsoft.com/rest/api/power-bi/)