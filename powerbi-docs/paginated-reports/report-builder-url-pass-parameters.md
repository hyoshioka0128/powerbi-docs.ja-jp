---
title: ページ分割されたレポートの URL 内でレポート パラメーターを渡す - Power BI レポート ビルダー
description: このトピックでは、レポート パラメーターをページ分割されたレポートの URL に含めることでレポートに渡す方法について説明します。
ms.service: powerbi
ms.subservice: report-builder
ms.topic: how-to
author: maggiesMSFT
ms.author: maggies
ms.reviewer: cfinlan
ms.custom: ''
ms.date: 05/01/2020
ms.openlocfilehash: f103f29c61d1a4e4a5340d97598d80a86c708701
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2020
ms.locfileid: "93298029"
---
# <a name="pass-a-report-parameter-in-a-url-for-a-paginated-report-in-power-bi"></a>Power BI のページ分割されたレポートの URL 内でレポート パラメーターを渡す 

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

レポート パラメーターをページ分割されたレポート URL に含めることで、レポートに渡すことができます。 すべてのクエリ パラメーターには、対応するレポート パラメーターを指定できます。 そのため、対応するレポート パラメーターを渡すことで、クエリ パラメーターをレポートに渡すことができます。 Power BI で URL 内のパラメーター名が認識されるには、名前の前に `rp:` を付ける必要があります。 

レポート パラメーターは大文字と小文字が区別され、次の特殊文字が使用されます。 

- URL のパラメーター部分のスペースは、正符号 (+) に置き換えられます。  次に例を示します。 

    ```rp:Holiday=Christmas+Day```

- 文字列の任意の部分にあるセミコロンは、文字 `%3A` で置き換えられます。

通常、適切な URL エンコードはブラウザーによって自動的に行われます。 文字を手動でエンコードする必要はありません。 

URL 内にレポート パラメーターを設定するには、次の構文を使用します。 

```
rp:parameter=value
```

たとえば、[マイ ワークスペース] のレポートで定義されている "Salesperson" と "State" の 2 つのパラメーターを指定するには、次の URL を使用します。 

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:Salesperson=Tie+Bear&rp:State=Utah 
```

アプリでレポートに定義されているものと同じ 2 つのパラメーターを指定するには、次の URL を使用します。 

```
https://app.powerbi.com/groups/me/apps/xxxxxxx-c4c4-4217-afd9-3920a0d1e2b0/rdlreports/b1d5e659-639e-41d0-b733-05d2bca9853c?rp:Salesperson=Tiggee&rp:State=Utah 
```

パラメーターに NULL 値を渡すには、次の構文を使用します。 

```
parameter:isnull=true
```

次に例を示します。

```
rp:SalesOrderNumber:isnull=true
```

ブール値を渡すには、false には 0 を、true には 1 を使用します。 浮動小数点型の値を渡すには、サーバー ロケールの小数点区切り記号を含めます。

> [!NOTE]
> 既定値を持つレポート パラメーターがレポートに含まれ、 **[プロンプト]** プロパティの値が **false** (つまり、 **[ユーザーにメッセージを表示]** プロパティがレポート マネージャーで選択されていない場合)、URL 内のそのレポート パラメーターの値を渡すことはできません。 これにより、管理者は、エンド ユーザーが特定のレポート パラメーターの値を追加または変更できないようにすることができます。
> 
> Power BI では、2,000 文字を超えるクエリ文字列はサポートしていません。  この値は、ご自分のページ分割されたレポートを参照するために url パラメーターを使用している場合に超過することがあります。  これは、特に値が複数あるパラメーターを使用するときに当てはまります。

## <a name="additional-examples"></a>追加の例 

次の URL 例には、複数値のパラメーター "Salesperson" が含まれています。 複数値パラメーターの形式として、値ごとにパラメーター名を繰り返します。 

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:Salesperson=Tie+Bear&rp:Salesperson=Mickey 
```

次の URL の例では、ネイティブ モードのレポート サーバーに対して、値が "7/1/2005" の SellStartDate の 1 つのパラメーターが渡されます。

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:SellStartDate=7/1/2005
```

## <a name="next-steps"></a>次のステップ

- [Power BI のページ分割されたレポートの URL パラメーター](report-builder-url-parameters.md)
- [Power BI Premium のページ分割されたレポートとは](paginated-reports-report-builder-power-bi.md)
