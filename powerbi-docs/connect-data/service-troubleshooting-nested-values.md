---
title: Power BI サービスでテキストとして返される、入れ子になった値のトラブルシューティング
description: 不適切なデータ ソースのプライバシー設定を使用したときに、文字列に変換される入れ子になった値を修正する方法について説明します
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.custom: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: troubleshooting
ms.date: 6/4/2019
LocalizationGroup: Reports
ms.openlocfilehash: b34f6ae838122b0b2036a953296d5032bdfe76b8
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96401376"
---
# <a name="troubleshooting-nested-values-returned-as-text-in-power-bi-service"></a>Power BI サービスでテキストとして返される、入れ子になった値のトラブルシューティング

## <a name="cause"></a>原因

以前は、Power BI レポートがデスクトップでは正常に更新されたのに、Power BI サービスでは "値 "[Table]" を型 Table に変換できません" のようなエラーが表示されて失敗することがありました。 このエラーの原因の 1 つは、Data Privacy Firewall でデータ ソースがバッファー処理されるときに、入れ子になった非スカラー値 (テーブル、レコード、リスト、関数など) が、自動的にテキスト値 ("[Table]" や "[Record]" など) に変換されることです。

Power BI サービスでプライバシー レベルの設定 (またはファイアウォールの完全な無効化) がサポートされるようになったので、Power BI サービスで[データ ソースのプライバシー設定を非プライベートに構成](https://powerbi.microsoft.com/blog/privacy-levels-for-cloud-data-sources/)することで、このようなエラーを回避できます。

6 月の Power BI 以降では、ファイアウォールが入れ子になったテーブル/レコード/リストなどの値をサイレント モードでテキストに変換する代わりにバッファー処理すると、次のエラーが生成されます。 

`We cannot return a value of type Table in this context`

## <a name="effect-on-loadrefresh"></a>読み込み/更新への影響

変更はファイアウォール バッファーリングによって促されますが、その影響は、読み込み/更新にも及びます。 ファイアウォール バッファーリング動作に対処するために、入れ子になったテーブル/レコードなどの Power BI モデルおよび PQ for Excel の Excel データ モデルへの読み込みの動作も変更する必要がありました。 以前は、入れ子になったテーブル/レコードなどはテキスト値 (“[Table]” や “[Record]” など) として読み込まれていました。 これらは、今はエラーとして扱われ、読み込まれたテーブルでは null 値となり、読み込み結果のエラー カウントが 1 つ増えます。

これらのエラーは、読み込み/更新中にのみ発生するため、Power Query エディターには表示されません。

### <a name="before"></a>適用前

- エラーなく読み込み/更新
- 読み込まれたテーブルには、"[Table]"、“[Record]” などが含まれている
 

### <a name="after"></a>より後

- 読み込み/更新でエラー
- 読み込まれたテーブルに ("[Table]"、“[Record]” などではなく) NULL 値が含まれる
 

## <a name="resolution"></a>解決方法

非スカラー値 (たとえばテーブル、リスト、レコードなど) を含む列を読み込んでいますか。
その場合、その列を削除することで、エラーを排除できるはずです。
列を削除できない場合は、カスタム列を追加し、次のサンプルのようなロジックを使用して、以前の動作をレプリケートできるはずです。

`if [MyColumn] is table then "[Table]" else if [MyColumn] is record then "[Record]" else if [MyColumn] is list then "[List]" else if [MyColumn] is function then "[Function]" else [MyColumn]`

すべてのデータ ソースのプライバシーの設定をプライベートに設定した場合に、Power BI Desktop で問題が再現しますか。
その場合は、Power BI サービスで[そのデータ ソースのプライバシー設定を非プライベートに構成する](https://powerbi.microsoft.com/blog/privacy-levels-for-cloud-data-sources/)ことで、エラーを解決できるはずです。
