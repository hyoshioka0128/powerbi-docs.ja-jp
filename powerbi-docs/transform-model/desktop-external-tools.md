---
title: Power BI Desktop での外部ツール
description: 外部ツールで Power BI Desktop の使用を拡張します
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 03/25/2021
LocalizationGroup: Create reports
ms.openlocfilehash: 71b29cc849a19e8099f455350128ff3460f3324e
ms.sourcegitcommit: adbbffc74521c76eb3ad8de92b803785b94c34ee
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "105938022"
---
# <a name="external-tools-in-power-bi-desktop"></a>Power BI Desktop での外部ツール

Power BI には、BI プロフェッショナルおよび開発者の活発なコミュニティがあります。 そのコミュニティのきわめて重要な部分として、Power BI と Analysis Services API を使用して、Power BI Desktop のデータ モデリングやレポート機能を拡張および統合する無料のツールを作成する共同作成者があります。 

**[外部ツール]** リボンを使用すると、ローカルにインストールされ、Power BI Desktop に "*登録されている*" 外部ツールに簡単にアクセスできます。 [外部ツール] リボンから起動されると、Power BI Desktop では、その内部データ モデル エンジン インスタンスの名前とポート番号および現在のモデル名をツールに渡します。 それにより、ツールは自動的に接続され、シームレスな接続エクスペリエンスが提供されます。  

:::image type="content" source="media/desktop-external-tools/external-tools-ribbon.png" border="false" alt-text="Power BI Desktop の外部ツール リボン":::


外部ツールは一般に、次のいずれかのカテゴリに分類されます。

**セマンティック モデリング** - DAX Studio、ALM Toolkit、Tabular Editor、Metadata Translator などのオープンソース ツールによって、Power BI Desktop 機能が DAX クエリや DAX 式の最適化、アプリケーション ライフサイクル管理 (ALM)、メタデータの翻訳などの特定のデータ モデリング シナリオのために拡張されます。

**データ分析** - データをクエリしたり、その他の分析タスクを実行したりするために、読み取り専用でモデルに接続するためのツール。 たとえば、Python、Excel、Power BI レポート ビルダーを起動し、最初に Power BI Desktop (pbix) ファイルを Power BI サービスに発行することなく、テストや分析のために Power BI Desktop でクライアント アプリケーションをモデルに接続するツールがあります。 Power BI データセットを文書化するためのツールもこのカテゴリに分類されます。

**その他** - 一部の外部ツールはまったくモデルに接続しませんが、代わりに Power BI Desktop を拡張して、役立つヒントを作成したり、役立つコンテンツにより簡単にアクセスできるようにしたりします。 たとえば、PBI.tips のチュートリアル、sqlbi.com の DAX ガイドのほか、さまざまな外部ツール (DAX Studio、ALM Toolkit、Tabular Editor、その他多数を含む) のインストールやそれらの Power BI Desktop への登録を簡単にする PowerBI.tips の Product Business Ops コミュニティ ツールがあります。

**カスタム** - *.pbitool.json ドキュメントを Power BI Desktop\External Tools フォルダーに追加することによって、独自のスクリプトやツールを統合します。

外部ツールをインストールする前に、次の点に注意してください。

- Power BI Report Server 向け Power BI Desktop では、外部ツールはサポートされていません。

- 外部ツールは、外部のサードパーティ共同作成者によって提供されます。 Microsoft では、外部ツールのサポートまたはドキュメントを提供していません。

## <a name="featured-open-source-tools"></a>おすすめのオープンソース ツール

多数の外部ツールが公開されています。 すべての Power BI Desktop データ モデラー ツールボックスに含まれている、最も一般的なもののいくつかを次に示します。

|ツール  |説明  |
|---------|---------|
|PowerBI.tips - Business Ops      |   外部ツールの拡張機能を Power BI Desktop に追加するための、使いやすい配置ツール。 Business Ops の目標は、すべての最新バージョンの外部ツールをインストールするためのワンストップ ショップを提供することです。 詳細については、[PowerBI.tips - Business Ops](https://powerbi.tips/product/business-ops/) の Web サイトを参照してください。      |
|Tabular Editor     |   モデル作成者は、直感的で、かつ軽量のエディターを使用して、表形式モデルを簡単に構築、保守、管理できます。 階層ビューには、表形式モデル内のすべてのオブジェクトが表示フォルダーで整理されて表示され、複数選択のプロパティ編集と DAX 構文の強調表示がサポートされます。 詳細については、[tabulareditor.com](https://tabulareditor.com/) を参照してください。       |
|DAX Studio      | DAX の作成、診断、パフォーマンス チューニング、分析のための、機能の豊富なツール。 機能には、オブジェクトの参照、統合されたトレース、詳細な統計情報を含むクエリ実行の分析結果、DAX 構文の強調表示、書式設定などがあります。 最新版を入手するには、GitHub 上の [DAX Studio](https://github.com/DaxStudio/DaxStudio) にアクセスしてください。         |
|ALM Toolkit     |   アプリケーション ライフサイクル管理 (ALM) のシナリオに使用される、Power BI モデルおよびデータセットのためのスキーマ比較ツール。 複数の環境にまたがる簡単な配置を実行したり、増分更新の履歴データを保持したりできます。 メタデータ ファイル、ブランチ、リポジトリを比較してマージできます。 また、データセット間で共通の定義を再利用することもできます。 最新版を入手するには、[alm-toolkit.com](http://alm-toolkit.com/) にアクセスしてください。      |
|Metadata Translator      |    Power BI モデルおよびデータセットのローカライズを効率化します。 このツールでは、Azure Cognitive Services の機械翻訳テクノロジを使用して、テーブル、列、メジャー、階層のキャプション、説明、表示フォルダー名を自動的に翻訳できます。 また、Excel またはローカライズ ツールでの便利な一括編集のために、コンマ区切り値 (.csv) ファイル経由で翻訳をエクスポートおよびインポートすることもできます。 最新版を入手するには、GitHub 上の [Metadata Translator](https://github.com/microsoft/Analysis-Services/tree/master/MetadataTranslator) にアクセスしてください。    |

## <a name="external-tools-integration-architecture"></a>外部ツールの統合アーキテクチャ

Power BI Desktop (pbix) ファイルは、レポート キャンバス、ビジュアル、モデル メタデータのほか、既にデータ ソースから読み込まれている任意のデータを含む複数のコンポーネントで構成されています。 Power BI Desktop では pbix ファイルを開くと、バックグラウンドで Analysis Services プロセスを起動してモデルを読み込み、データ モデリング機能やレポート ビジュアルでモデル メタデータにアクセスしたり、モデル データをクエリしたりできるようにします。

Power BI Desktop では、その分析データ エンジンとして Analysis Services を起動した後、ランダムなポート番号を動的に割り当て、グローバル一意識別子 (GUID) の形式のランダムに生成された名前でモデルを読み込みます。 これらの接続パラメーターは Power BI Desktop セッションごとに変更されるため、外部ツールで、接続先の正しい Analysis Services インスタンスとモデルを独自に検出することは困難です。 外部ツールの統合では、次の図に示すように、[外部ツール] リボンから外部ツールを起動するときに Power BI Desktop からツールに Analysis Services サーバー名、ポート番号、モデル名をコマンド ライン パラメーターとして伝達できるようにすることによって、この問題が解決されます。

:::image type="content" source="media/desktop-external-tools/external-tool-arch.png" border="false" alt-text="外部ツールのアーキテクチャ":::

Analysis Services サーバー名、ポート番号、モデル名により、このツールは Analysis Services クライアント ライブラリを使用して、モデルへの接続を確立したり、メタデータを取得したり、DAX または MDX クエリを実行したりできます。 外部データ モデリング ツールでメタデータが更新されるたびに、Power BI Desktop ではこれらの変更を同期して、Power BI Desktop のユーザー インターフェイスにそのモデルの現在の状態が正確に反映されるようにします。 後で説明されているように、同期機能にはいくつかの制限があることに注意してください。

## <a name="data-modeling-operations"></a>データ モデリングの操作

外部データ モデリング ツールでは変更を適用し、レポート キャンバスによって Power BI でこれらの変更が同期されるようにすることができます。 この同期は、これらの変更が Power BI ビジュアルで常に適用されるようにするためのものです。 たとえば、外部データ モデリング ツールでは、メジャーの元の書式文字列式をオーバーライドしたり、KPI や詳細行を含む任意のメジャー プロパティを編集したりできます。 外部ツールではまた、オブジェクトや行レベルのセキュリティのために新しいロールを作成したり、翻訳を追加したりすることもできます。

### <a name="supported-write-operations"></a>サポートされる書き込み操作

- 計算のための[メジャー](/analysis-services/tabular-models/measures-ssas-tabular?view=power-bi-premium-current&preserve-view=true) (書式文字列、KPI、詳細行の設定を含む) を定義および編集する。
- 複雑なモデルでの計算の再利用性のための[計算グループ](/analysis-services/tabular-models/calculation-groups?view=power-bi-premium-current&preserve-view=true)を追加する。 
- データセット メタデータの的を絞ったビジネス ドメイン固有のビューを定義するための[パースペクティブ](/analysis-services/tabular-models/perspectives-ssas-tabular?view=power-bi-premium-current&preserve-view=true)を作成する。
- 1 つのデータセット内での多言語バージョンをサポートするための[メタデータの翻訳](/analysis-services/tabular-models/translations-in-tabular-models-analysis-services?view=power-bi-premium-current&preserve-view=true)を適用する。
- データ アクセスを制限するために、[行レベルのセキュリティ (RLS)](../guidance/rls-guidance.md) と[オブジェクト レベルのセキュリティ (OLS)](/analysis-services/tabular-models/object-level-security?view=power-bi-premium-current&preserve-view=true) のためのデータセット ロールを追加する。

### <a name="data-modeling-limitations"></a>データ モデリングの制限事項

表形式オブジェクト モデル (TOM) メタデータはすべて、読み取り専用でアクセスできます。 Power BI Desktop は外部の変更と同期されている状態を維持する必要があるため、書き込み操作は制限されます。そのため、次の操作はサポートされていません。

- 「サポートされる書き込み操作」で説明されていないすべての TOM オブジェクトの種類 (テーブルや列など)。
- Power BI Desktop テンプレート (PBIT) ファイルの編集。
- レポート レベルまたはデータ レベルの翻訳。
- テーブルと列の名前の変更は、まだサポートされていません。

## <a name="registering-external-tools"></a>外部ツールの登録

外部ツールは、ツールの `Program Files (x86)\Common Files\Microsoft Shared\Power BI Desktop\External Tools` フォルダーに \*.pbitool.json 登録ファイルが含まれているとき、Power BI Desktop に "*登録されます*"。 ツールが登録され、それにアイコンが含まれているとき、そのツールは [外部ツール] リボンに表示されます。 ALM Toolkit や DAX Studio などの一部のツールでは、ツールのインストール時、登録ファイルが自動的に作成されます。 ただし、SQL Profiler など、多くのツールでは通常、それが行われません。付属のインストーラーでは、Power BI Desktop の登録ファイルが作成されないためです。 Power BI Desktop に自動的に登録されないツールは、\*.pbitool.json 登録ファイルを作成することで手動で登録できます。

json の例など、詳細については、「[外部ツールを登録する](desktop-external-tools-register.md)」を参照してください。

## <a name="disabling-the-external-tools-ribbon"></a>[外部ツール] リボンの無効化

[外部ツール] リボンは既定で有効になっていますが、グループ ポリシーを使用するか、または **EnableExternalTools** レジストリ キーを直接編集することによって無効にすることができます。

- レジストリ キー: Software\Policies\Microsoft\Power BI Desktop\
- Registry value:EnableExternalTools

1 の値 (10 進数) によって [外部ツール] リボンが有効になります。これは、既定値でもあります。

0 の値 (10 進数) によって [外部ツール] リボンが無効になります。

## <a name="see-also"></a>関連項目

[外部ツールを登録する](desktop-external-tools-register.md)  
