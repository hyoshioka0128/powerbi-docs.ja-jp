---
title: Power BI での外部ツールの使用 (プレビュー)
description: 外部ツールで Power BI Desktop の使用を拡張します
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 12/10/2020
LocalizationGroup: Create reports
ms.openlocfilehash: 98e27491147fa0e7ed7028925671d40a84fd9e6e
ms.sourcegitcommit: 772c65b7b440ab082510bf3f64b871d19139d451
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/12/2020
ms.locfileid: "97353383"
---
# <a name="using-external-tools-in-power-bi-desktop-preview"></a>Power BI Desktop での外部ツールの使用 (プレビュー)

Power BI Desktop の 2020 年 7 月のリリース以降、外部ツールを使用して、Power BI Desktop に追加の機能と価値を付与できるようになりました。 外部ツールのサポートにより、DAX クエリや DAX 式の最適化と作成、アプリケーション ライフサイクル管理 (ALM) など、BI プロフェッショナル向けの Analysis Services で多くのコミュニティ ツールを活用できるようになります。

Power BI Desktop の **[外部ツール]** リボンには、コンピューターにインストールされている外部ツールと、Power BI Desktop に登録されている外部ツール用のボタンが含まれています。 Power BI Desktop から起動した外部ツールは、Power BI Desktop の一部として動作する Analysis Services エンジンに自動的に接続され、シームレスなエクスペリエンスがユーザーに提供されます。

![Power BI Desktop の外部ツール リボン](media/desktop-external-tools/desktop-external-tools-01.png)

これらのおすすめの外部ツールには次のものが含まれており、そのインストール場所へのリンク付きで示します。 各外部ツールは、それぞれのツール作成者によってサポートされています。

* [Tabular Editor](https://tabulareditor.com/)
* [DAX Studio](https://daxstudio.org)
* [ALM Toolkit](http://alm-toolkit.com)


以下のセクションでは、外部ツールでサポートされる操作、Power BI Desktop に含まれているおすすめのツールの一覧、および追加のツールを登録する手順について説明します。

> [!NOTE]
> 外部ツールは、Power BI Desktop の Power BI Report Server バージョンでは使用できません。

## <a name="supported-write-operations"></a>サポートされる書き込み操作

外部ツールでは、Power BI Desktop データセット (Analysis Services モデル) に接続して、次のオブジェクトを編集できます。 Power BI Desktop テンプレート (PBIT) ファイルの編集はサポートされていません。

* 計算の[メジャー](/analysis-services/tabular-models/measures-ssas-tabular)
* 複雑なモデルにおける計算の再利用性のための[計算グループ](/analysis-services/tabular-models/calculation-groups)
* データセット メタデータの的を絞ったビジネス ドメイン固有ビューを定義するための[パースペクティブ](/analysis-services/tabular-models/perspectives-ssas-tabular)

外部ツールを使用してメタデータの翻訳を管理することは可能かもしれませんが、現在、このプレビュー バージョンではサポートされていません。 現在のユーザーのロケールが翻訳されたロケールである場合、現在のバージョンの Power BI Desktop を使用してフィールド リスト内のオブジェクトを編集しても、正しく機能しません。 

すべての[表形式オブジェクト モデル](/analysis-services/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo) データセットのメタデータは読み取り専用でアクセスできますが、[表形式オブジェクト モデル](/analysis-services/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo)の記事で説明されている一覧に含まれていないオブジェクトは、Power BI Desktop Analysis Services インスタンスでの編集がまだサポートされていません。


## <a name="featured-external-tools"></a>おすすめの外部ツール

次のオープンソース コミュニティ ツールは、Power BI Desktop と連動します。 これらは、それぞれのツール作成者によってサポートされています。 各ツールの個別のインストーラーによって、インストール時にそのツールが Power BI Desktop に登録されます。

* Tabular Editor
* DAX Studio
* ALM Toolkit

各ツールについて順番に見ていきましょう。

### <a name="tabular-editor"></a>Tabular Editor

[Tabular Editor](https://tabulareditor.com/) は次のリンクからインストールできます: [Tabular Editor の Web サイト](https://tabulareditor.com/)

Tabular Editor を使うと、BI プロフェッショナルは直感的で軽量なエディターを使用して、表形式モデルの構築、保守、管理を簡単に実行できるようになります。 表形式モデル内のすべてのオブジェクトが、表示フォルダーで整理されて階層ビューに表示されます。複数選択プロパティの編集と DAX 構文の強調表示がサポートされています。

![Tabular Editor のスクリーンショット](media/desktop-external-tools/desktop-external-tools-02.png)

Tabular Editor のソース コードは、次の GitHub リポジトリにあります: [GitHub 上の Tabular Editor](https://github.com/otykier/TabularEditor)

Tabular Editor の主要なツール作成者は [Daniel Otykier](https://www.linkedin.com/in/daniel-otykier-2231876) です。


### <a name="dax-studio"></a>DAX Studio

[DAX Studio](https://daxstudio.org) は次のリンクからインストールできます: [DAX Studio の Web サイト](https://daxstudio.org)

DAX Studio は、DAX の作成、診断、パフォーマンス チューニング、および分析を完備したツールとして知られています。 その機能には、オブジェクトの参照、統合されたトレース、詳細な統計情報を含むクエリ実行の分析結果、DAX 構文の強調表示と書式設定などがあります。 次の図は Dax Studio の画面を示しています。 

![DAX Studio のスクリーンショット](media/desktop-external-tools/desktop-external-tools-03.png)

DAX Studio のソース コードは、次の GitHub リポジトリにあります: [GitHub 上の DAX Studio](https://github.com/DaxStudio/DaxStudio)

DAX Studio の主要なツール作成者は [Darren Gosbell](https://www.linkedin.com/in/darrengosbell) です。

### <a name="alm-toolkit"></a>ALM Toolkit

[ALM Toolkit](http://alm-toolkit.com) は次のリンクからインストールできます: [ALM Toolkit の Web サイト](http://alm-toolkit.com)

ALM Toolkit は、アプリケーション ライフサイクル管理 (ALM) のシナリオで使用される、Power BI データセット用のスキーマ比較ツールです。 これにより、複数の環境にわたってわかりやすい配置を実行し、増分更新の履歴データを保持できます。 ALM Toolkit を使うと、メタデータ ファイル、ブランチ、リポジトリを比較してマージできます。 また、データセット間で共通の定義を再利用することもできます。

![ALM Toolkit のスクリーンショット](media/desktop-external-tools/desktop-external-tools-04.png)

ALM Toolkit のソース コードは、次の GitHub リポジトリにあります: [GitHub 上の ALM Toolkit](https://github.com/microsoft/analysis-services)

ALM Toolkit の主要なツール作成者は [Christian Wade](https://www.linkedin.com/in/christianwade1) です。


## <a name="how-to-register-external-tools"></a>外部ツールを登録する方法

その他の外部ツールを Power BI Desktop に登録するには、次の内容を含む JSON ファイルを作成します。

```json
{
    "name": "<tool name>",
    "description": "<tool description>",
    "path": "<tool executable path>",
    "arguments": "<optional command line arguments>",
    "iconData": "image/png;base64,<encoded png icon data>"
}
```

次の一覧では、JSON ファイルに含まれている要素の一覧について説明します。
 
* **name:** ツールの名前を指定します。これは Power BI Desktop 内の [外部ツール] リボンに、ボタンのキャプションとして表示されます。
* **description:** (省略可能) 説明を指定します。これは Power BI Desktop 内の [外部ツール] リボンのボタンに、ヒントとして表示されます。
* **path:** ツールの実行可能ファイルへの完全修飾パスを指定します。
* **arguments:** (省略可能) ツールの実行可能ファイルの起動時に指定する必要があるコマンド ライン引数の文字列を指定します。 次の任意のプレースホルダーを使用できます。
    * **%server%:** インポートされた、または DirectQuery のデータ モデルに対する Analysis Services 表形式のローカル インスタンスのサーバー名とポート番号に置き換えられます。
    * **%database%:** インポートされた、または DirectQuery のデータ モデルに対する Analysis Services 表形式のローカル インスタンスでホストされるモデルのデータベース名に置き換えられます。
* **iconData:** Power BI Desktop 内の [外部ツール] リボンにボタン アイコンとして表示される画像データを指定します。 文字列は、データ URI の構文から "data:" プレフィックスを除いた形式にする必要があります。
 
ファイルに `"<tool name>.pbitool.json"` という名前を付け、次のフォルダーに配置します。

* `%commonprogramfiles%\Microsoft Shared\Power BI Desktop\External Tools`

64 ビット環境の場合は、次のフォルダーにファイルを配置します。

* **Program Files (x86)\Common Files\Microsoft Shared\Power BI Desktop\External Tools**

この指定した場所にある **.pbitool.json** 拡張子を持つファイルが、Power BI Desktop によって起動時に読み込まれます。

## <a name="disabling-external-tools-using-the-registry"></a>レジストリを使用して外部ツールを無効にする

外部ツールは、**グループ ポリシー** を使用して、またはレジストリを編集することによって無効にすることができます。これは、**カスタム ビジュアル** を無効にするプロセスと似ています。

* Registry key:*Software\Policies\Microsoft\Power BI Desktop\\*

* Registry value:*EnableExternalTools*

値が 1 (10 進数) の場合は、Power BI で外部ツールの使用が有効になります。これは既定値です。

値が 0 (10 進数) の場合は、Power BI で外部ツールの使用が無効になります。


## <a name="next-steps"></a>次のステップ

次の記事にも興味をもたれるかもしれません。

* [Power BI でレポート間のドリルスルーを使用する](desktop-cross-report-drill-through.md)
* [Power BI Desktop でスライサーを使用する](../visuals/power-bi-visualization-slicers.md)