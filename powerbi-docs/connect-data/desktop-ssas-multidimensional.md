---
title: Power BI Desktop の Analysis Services 多次元データ
description: Power BI Desktop の SQL Server Analysis Services (SSAS) 多次元データ
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 01/15/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 9567c0511a771b9b92de74171dec5fed3110e2d8
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410898"
---
# <a name="connect-to-ssas-multidimensional-models-in-power-bi-desktop"></a>Power BI Desktop で SSAS 多次元モデルに接続する

Power BI Desktop を利用して、*SSAS 多次元モデル* (一般に *SSAS MD* と呼ばれる) にアクセスできます。

SSAS MD データベースに接続するには、 **[データの取得]** 、 **[データベース]** 、 **[SQL Server Analysis Services データベース]** 、 **[接続]** の順に選択します。

![SQL Server Analysis Services (SSAS) データベース、[データの取得] ダイアログ ボックス、Power BI Desktop](media/desktop-ssas-multidimensional/ssas-multidimensional-2.png)

ライブ接続モードの SSAS 多次元モデルは、Power BI サービスと Power BI Desktop の両方でサポートされます。 ライブ モードの **SSAS 多次元モデル** を使用するレポートを Power BI サービスに公開およびアップロードすることができます。

## <a name="capabilities-and-features-of-ssas-md"></a>SSAS MD の能力と機能

次のセクションでは、Power BI および SSAS MD 接続の機能と能力について説明します。

### <a name="tabular-metadata-of-multidimensional-models"></a>多次元モデルの表形式のメタデータ

次の表は、多次元オブジェクトと Power BI Desktop に返される表形式のメタデータ間の対応を示しています。 Power BI は、表形式のメタデータをモデルに照会します。 返されたメタデータに基づいて、Power BI Desktop は、視覚化 (テーブル、マトリックス、グラフ、スライサーなど) の作成時に、SSAS に対して適切な DAX クエリを実行します。

| BISM 多次元オブジェクト | 表形式のメタデータ |
| --- | --- |
| キューブ |モデル |
| キューブ ディメンション |テーブル |
| ディメンション属性 (キー)、名前 |列 |
| メジャー グループ |テーブル |
| メジャー |メジャー |
| 関連付けられたメジャー グループのないメジャー |*メジャー* という名前のテーブル内 |
| [メジャー グループ] -> [キューブ ディメンションのリレーションシップ] |リレーションシップ |
| パースペクティブ |パースペクティブ |
| KPI |KPI |
| ユーザー階層/親子階層 |階層 |

### <a name="measures-measure-groups-and-kpis"></a>メジャー、メジャー グループ、および KPI

多次元キューブのメジャー グループは、テーブルとして公開され、 **[フィールド]** ウィンドウで横にシグマ (∑) が付けられます。 関連付けられたメジャー グループがない計算メジャーは、表形式のメタデータ内で "*メジャー*" という名前の特別なテーブルの下にグループ化されます。

多次元モデルで複雑なモデルを簡素化するには、キューブ内の一連のメジャーまたは KPI を定義して、"*表示フォルダー*" 内に配置します。 Power BI は、表形式のメタデータの表示フォルダーを認識し、表示フォルダー内にメジャーと KPI を表示します。 多次元データベースの KPI は *値*、*目標*、*状態マーク*、および *傾向マーク* をサポートします。

### <a name="dimension-attribute-type"></a>ディメンション属性の種類

多次元モデルでは、ディメンション属性と特定ディメンション属性の種類の関連付けもサポートしています。 たとえば、**Geography** ディメンションで、*City*、*State-Province*、*Country*、および *Postal Code* ディメンション属性に適切な地理の種類が関連付けられている場合、ディメンションは表形式のメタデータで公開されます。 Power BI はメタデータを認識し、マップの視覚エフェクトを作成できるようにします。 これらの関連は、Power BI の *[フィールド]* ウィンドウで、要素の隣にある **[マップ]** アイコンによって識別されます。

イメージの URL (Uniform Resource Locator) を含むフィールドを指定すると、Power BI はイメージのレンダリングも行うことができます。 これらのフィールドは、SQL Server Data Tools 内で (または後で Power BI 内で)、*ImageURL* 型として指定できます。 次に、その型情報が表形式のメタデータで Power BI に提供され、 Power BI は、イメージを URL から取得してビジュアルに表示することができます。

### <a name="parent-child-hierarchies"></a>親子の階層

多次元モデルは親子階層をサポートしており、表形式のメタデータで *階層* として表示されます。 親子階層の各レベルは、表形式のメタデータで非表示の列として公開されます。 親子ディメンションのキー属性は、表形式のメタデータでは公開されません。

### <a name="dimension-calculated-members"></a>ディメンションが計算されるメンバー

多次元モデルはさまざまな型の *計算されるメンバー* の作成をサポートしています。 最も一般的な種類の計算メンバーは、次の 2 つです。

* "*すべて*" の兄弟ではない、属性階層の計算メンバー
* ユーザー階層の計算されるメンバー

多次元モデルは列の値として、*属性階層の計算されるメンバー* を公開します。 この種類の計算メンバーを公開する場合、他にもいくつかのオプションと制約があります。

* ディメンションの属性に、オプションの *UnknownMember* を含めることができます。

* ディメンションの唯一の属性である場合を除いて、計算メンバーを含む属性をディメンションのキー属性にすることはできません。

* 計算メンバーを含む属性を親子属性にすることはできません。

ユーザー階層の計算メンバーは、Power BI で公開されません。 代わりに、ユーザー階層の計算メンバーを含むキューブに接続できます。 ただし、前述の箇条書きで説明した制約を満たしていない場合は、計算メンバーを表示できません。

### <a name="security"></a>セキュリティ

多次元モデルでは、*ロール* を使用してディメンションおよびセル レベルのセキュリティをサポートします。 Power BI でキューブに接続する場合、認証が行われ、適切なアクセス許可の有無が評価されます。 ユーザーに "*ディメンション セキュリティ*" が適用されている場合、Power BI のユーザーがそれぞれのディメンション メンバーを表示することはできません。 ただし、ユーザーが "*セル セキュリティ*" のアクセス許可を定義しており、特定のセルが制限されている場合、そのユーザーは Power BI を使用してキューブに接続することはできません。

## <a name="considerations-and-limitations"></a>考慮事項と制限事項

SSAS MD 使用には、次のようないくつかの制限があります。

* ライブ接続は、SQL Server 2014 の Enterprise エディションと BI エディションのみでサポートされます。 SQL Server の標準エディションの場合、ライブ接続には SQL Server 2016 以降が必要です。

* "*アクション*" と "*名前付きセット*" は Power BI に公開されません。 ビジュアルおよびレポートを作成するために、アクションまたは名前付きセットも含むキューブに接続することはできます。

* Power BI に SSAS モデルのメタデータが表示されても、モデルのデータを取得できない場合があります。 このシナリオは、32 ビット版の MSOLAP プロバイダーがインストールされ、64 ビット版がインストールされていない場合に発生する可能性があります。 64 ビット版をインストールすると、この問題が解決することがあります。

* SSAS 多次元モデルにライブ接続されるレポートを作成する場合、"*レポート レベル*" のメジャーを作成することはできません。 使用できるメジャーは、MD モデルで定義されたメジャーのみです。

## <a name="supported-features-of-ssas-md-in-power-bi-desktop"></a>Power BI Desktop でサポートされる SSAS MD の機能

このリリースの SSAS MD では、次の要素の使用がサポートされます。 これらの機能の詳細については、「[多次元モデルの Power View について](/sql/analysis-services/multidimensional-models/understanding-power-view-for-multidimensional-models?view=sql-server-2014)」を参照してください。

* 既定メンバー
* [ディメンションの属性]
* ディメンションの属性の種類
* ディメンション計算メンバー:
  * ディメンションに複数の属性がある場合、単一の実メンバーである必要があります。
  * 唯一の属性である場合を除いて、ディメンションのキー属性にすることはできません。
  * 親子属性にすることはできません。
* 次元セキュリティ
* フォルダーの表示
* 階層
* ImageUrls
* KPI
* KPI 傾向
* メジャー (メジャー グループあり、またはメジャー グループなし)
* バリアントとしてのメジャー

## <a name="troubleshooting"></a>トラブルシューティング

次の一覧は、SQL Server Analysis Services (SSAS) に接続するときのすべての既知の問題を示しています。

* **エラー:モデル スキーマを読み込むことができません** - このエラーは通常、Analysis Services に接続するユーザーがデータベースまたはキューブへのアクセス許可っていない場合に発生します。
