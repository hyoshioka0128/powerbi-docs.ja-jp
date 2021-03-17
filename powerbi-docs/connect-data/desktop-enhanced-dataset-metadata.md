---
title: Power BI Desktop での拡張データセット メタデータの使用
description: この記事では、Power BI で拡張データセット メタデータを使用する方法について説明します。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: conceptual
ms.date: 12/08/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: d240cacaa7aeb02e5ebe8dc05b4781fb104c27bc
ms.sourcegitcommit: 13a150d1aa810f309421bf603fa8581718a4b299
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "101843414"
---
# <a name="using-enhanced-dataset-metadata"></a>拡張データセット メタデータの使用

Power BI Desktop によってレポートが作成されると、対応する PBIX ファイルと PBIT ファイルにデータセット メタデータも作成されます。 以前は、メタデータは Power BI Desktop に固有の形式で格納されていました。 メタデータには、Base-64 でエンコードされた M 式とデータ ソースが使用されていました。 そのメタデータの格納方法は Power BI によって想定されていました。

**拡張データセット メタデータ** 機能のリリースにより、これらの制限事項の多くはなくなります。 PBIX ファイルは、ファイルを開いたときに自動的に拡張メタデータにアップグレードされます。 **拡張データセット メタデータ** を使用すると、Power BI Desktop によって作成されたメタデータでは、[表形式オブジェクト モデル](/analysis-services/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo)に基づいて、Analysis Services 表形式モデルに使用されるものと同様の形式が使用されます。


**拡張データセット メタデータ** は、戦略的かつ基本的な機能です。 今後の Power BI 機能は、そのメタデータに基づいて構築されることになります。 他に次の機能でも、拡張データセット メタデータが活用されます。

- Power BI データセットを管理するための [XMLA の読み取り/書き込み](/power-platform-release-plan/2019wave2/business-intelligence/xmla-readwrite)
- 次世代の機能を活用するための、Analysis Services ワークロードから Power BI への移行。

## <a name="upgrade"></a>アップグレード
レポートは、最新バージョンの Power BI Desktop で開くと、拡張メタデータ形式へと自動的にアップグレードされます。 未適用のクエリ変更があるレポートを保存した場合や、自動アップグレード中にエラーが発生した場合は、アップグレードが必要であることを示す警告がレポート キャンバスに表示されます。 [レポートのアップグレード] をクリックすると、保留中の変更が適用され、データ モデルが新しい形式にアップグレードされます。 

## <a name="limitations"></a>制限事項
SQL Server、Oracle、Teradata、従来の HANA の各接続に対して拡張メタデータをサポートする前に、Power BI Desktop によってデータ モデルがネイティブ クエリに追加されています。 このクエリは Power BI サービス データ モデルによって使用されます。 拡張メタデータ サポートを使用すると、Power BI サービス データ モデルによって実行時にネイティブ クエリが再生成されます。 Power BI Desktop によって作成されたクエリは使用されません。 ほとんどの場合、この取得は自動的に正しく解決されますが、一部の変換は、基になるデータを読み取らないと機能しません。 以前は機能していたレポートでも、いくつかのエラーが表示される場合があります。 たとえば、次のようなエラーが発生します。 

"テーブル 'Dimension City' の M クエリをネイティブ ソース クエリに変換できません。 後でもう一度お試しいただくか、サポートにお問い合わせください。 サポートにお問い合わせいただく場合、これらの詳細をお伝えください。" 

クエリは、Power BI Desktop 内の次の 3 つの場所で修正することができます。

- 変更を適用する場合または更新を行う場合。
- Power Query エディターの警告バー (式をデータソースに折りたたむことができなかったことが通知されます)。
    :::image type="content" source="media/desktop-enhanced-dataset-metadata/enhanced-metadata-apply-query-changes.png" alt-text="[クエリ変更の適用] メッセージのスクリーンショット:データ ソースに式を折りたためませんでした。":::
- レポートを開いたときに評価を実行して、サポートされていないクエリがあるかどうかを確認する場合。 これらの評価を実行すると、パフォーマンスに影響が生じるおそれがあります。


## <a name="next-steps"></a>次の手順

Power BI Desktop では、あらゆる種類の操作を実行できます。 そのような機能について詳しくは、次のリソースをご覧ください。

* [Power BI Desktop とは何ですか?](../fundamentals/desktop-what-is-desktop.md)
* [Power BI Desktop の新機能](../fundamentals/desktop-latest-update.md)
* [Power BI Desktop でのクエリの概要](../transform-model/desktop-query-overview.md)
* [Power BI Desktop でのデータ型](desktop-data-types.md)
* [Power BI Desktop でのデータの整形と結合](desktop-shape-and-combine-data.md)
* [Power BI Desktop での一般的なクエリ タスク](../transform-model/desktop-common-query-tasks.md)
