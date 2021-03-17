---
title: Power BI Desktop のモデル ビュー
description: Power BI Desktop のモデル ビュー
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: how-to
ms.date: 02/23/2021
LocalizationGroup: Model your data
ms.openlocfilehash: 637bdd5713b2f403196352fa3c0893a667dbbcb8
ms.sourcegitcommit: 13a150d1aa810f309421bf603fa8581718a4b299
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "101841355"
---
# <a name="work-with-model-view-in-power-bi-desktop"></a>Power BI Desktop でモデル ビューを操作する

"*モデル ビュー*" には、モデル内のすべてのテーブル、列、リレーションシップが表示されます。 このビューは、モデルに多数のテーブル間の複雑な関係がある場合に特に役立ちます。

ウィンドウの横にある **[モデル]** アイコンを選択すると、既存のモデルのビューが表示されます。 リレーションシップ行の上にカーソルを置くと、使用されている列が表示されます。

:::image type="content" source="media/desktop-relationship-view/model-view-03.png" alt-text="リレーションシップを示すモデル ビュー":::

この画像では、*Connections* テーブルに *Seat ID* 列があり、それが *Unique Seats* テーブルに関連付けられています。そしてそのテーブルにも、*seatId* 列が含まれています。 2 つのテーブルには "*多対一*" (\*:1) のリレーションシップがあります。 線の中央の矢印は、フィルター コンテキスト フローの方向を示しています。 二重矢印は、クロス フィルターの方向が "*両方*" に設定されていることを意味します。

リレーションシップをダブルクリックすると、**[リレーションシップの編集]** ダイアログ ボックスで開くことができます。 リレーションシップについて詳しくは、「[Power BI Desktop でのリレーションシップの作成と管理](desktop-create-and-manage-relationships.md)」をご覧ください。


## <a name="new-model-view-preview"></a>新しいモデル ビュー (プレビュー)

最新リリースの Power BI Desktop には、新しい **モデル ビュー** のプレビュー バージョンが用意されており、ユーザーはこれを有効にすることができます。 新しいモデル ビューに切り替えると、その変更は永続的に維持されます。

:::image type="content" source="media/desktop-relationship-view/model-view-01.png" alt-text="更新前のモデル ビュー":::

更新を行うと、テーブルと接続が更新されていることが確認できます。

:::image type="content" source="media/desktop-relationship-view/model-view-02.png" alt-text="更新後のモデル ビュー":::

テーブル カード ヘッダーの色は、使用しているレポート テーマで選択した色と自動的に一致します。 色が白に近い場合、その色はモデル ビューのテーマ ヘッダーでは使用されません。これは、デュアル モードでテーブルを区別するのが困難になるのを回避するためです。

モデルのテーブル数が 75 未満の場合は、すべてのテーブルがモデル ビューに表示されます。 モデルのテーブル数が 75 を超える場合は、すべてのテーブルが表示されるのではなく、次の画像が表示されます。

:::image type="content" source="media/desktop-relationship-view/model-view-04.png" alt-text="75 を超える数のテーブル":::

モデルのテーブル数が 75 を超える場合は、カスタム レイアウトを作成することをお勧めします ( *[カスタム レイアウトの作成]* ボタンを選択します)。これにより、表示されるテーブルの数が 75 を超える場合でも、CPU やメモリの使用率が大幅に増えるのを軽減できます。

## <a name="next-steps"></a>次の手順
Power BI Desktop を使用すると、さまざまなことを行えます。 データ ソースの詳細については、次のリソースを参照してください。

* [Power BI Desktop とは何ですか?](../fundamentals/desktop-what-is-desktop.md)
* [Power BI Desktop のデータ ソース](../connect-data/desktop-data-sources.md)
* [Power BI Desktop でのデータの整形と結合](../connect-data/desktop-shape-and-combine-data.md)
* [Power BI Desktop で Excel ブックに接続する](../connect-data/desktop-connect-excel.md)   
* [Power BI Desktop にデータを直接入力する](../connect-data/desktop-enter-data-directly-into-desktop.md)   
