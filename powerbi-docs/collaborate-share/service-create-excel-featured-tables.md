---
title: Power BI Desktop でおすすめのテーブルを設定する (プレビュー)
description: Excel のデータ型ギャラリーに表示されるように、Power BI Desktop でおすすめのテーブルを作成します。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 09/17/2020
LocalizationGroup: Share your work
ms.openlocfilehash: d2d87f16b8100424b47277360354d79ee834d467
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411933"
---
# <a name="set-featured-tables-in-power-bi-desktop-preview"></a>Power BI Desktop でおすすめのテーブルを設定する (プレビュー)

Excel のデータ型ギャラリーでは、ユーザーが Power BI データセットの "*おすすめのテーブル*" からのデータを検索することができます。 この記事では、データセットの *おすすめの* テーブルを設定する方法について説明します。 これらのタグを使用すると、ユーザーが Excel シートにエンタープライズ データを簡単に追加できるようになります。 おすすめのテーブルを設定して共有するための基本的な手順を次に示します。

1. Power BI Desktop でデータセット内のおすすめのテーブルを識別します (この記事)。
1. おすすめのテーブルを含むこれらのデータセットを、新しいワークスペースのいずれかに保存します。 レポート作成者は、これらのおすすめのテーブルを使用してレポートを作成できます。 
1. 組織の残りの部分は、関連する更新可能なデータのために、これらのおすすめのテーブル (*Excel ではデータ型と呼ばれる*) に接続できます。 「[Excel で Power BI のおすすめのテーブルにアクセスする (プレビュー)](service-excel-featured-tables.md)」の記事では、Excel でこれらのおすすめのテーブルを使用する方法について説明します。

> [!NOTE]
> [Power BI でデータセットを昇格または認定](../collaborate-share/service-endorse-content.md)することができます。 これは "*承認*" と呼ばれます。 Excel によって、データ型ギャラリーで承認されたデータセット内のテーブルの優先順位が設定されます。 Excel によって、最初に認定済みデータセットのおすすめのテーブルが一覧表示され、次に昇格されたデータセットのテーブルが一覧表示されます。 Excel によって、その後、承認されていないデータセットのおすすめのテーブルが一覧表示されます。 

## <a name="turn-on-the-featured-table-preview"></a>おすすめのテーブルのプレビューを有効にする

1. Power BI Desktop で、 **[ファイル]**  >  **[オプションと設定]**  >  **[オプション]**  >  **[プレビュー機能]** の順に選択します。
2. **[Featured tables]\(おすすめのテーブル\)** チェック ボックスをオンにします。

    :::image type="content" source="media/service-excel-featured-tables/power-bi-preview-featured-tables.png" alt-text="おすすめのテーブル オプションをプレビューする":::

3. Power BI Desktop を再起動します。

## <a name="select-a-table"></a>テーブルを選択する

1. Power BI Desktop でモデル ビューに移動します。

    :::image type="content" source="media/service-excel-featured-tables/power-bi-model-view.png" alt-text="モデル ビュー":::
 
2. テーブルを選択し、 **[Is featured table]\(おすすめのテーブル\)** を **[はい]** に設定します。

    :::image type="content" source="media/service-excel-featured-tables/power-bi-featured-table-yes.png" alt-text="[Is featured table]\(おすすめのテーブル\) を [はい] に設定する":::

4. **[Set up this featured table]\(このおすすめのテーブルの設定\)** で、必須フィールドを指定します。

    - **[説明]** 。 
        > [!TIP]
        > Power BI レポート作成者が識別できるように、"おすすめのテーブル" で説明を開始します。
    - **[行ラベル]** フィールド値は、ユーザーが行を簡単に識別できるようにするために Excel で使用されます。 これは、リンク セルのセル値として、また **[Data Selector]\(データ セレクター\)** ペインおよび **[情報]** カード内に表示されます。 
    - **[キー列]** フィールド値により、行の一意の ID が指定されます。 この値により、Excel でセルをテーブル内の特定の行にリンクすることが可能になります。

    :::image type="content" source="media/service-excel-featured-tables/power-bi-set-up-featured-table.png" alt-text="おすすめのテーブルの設定":::

1. Power BI サービスに対してデータセットを発行またはインポートすると、Excel のデータ型ギャラリーにおすすめのテーブルが表示されます。 また、自分や他のレポート作成者がこのデータセットに基づくレポートを作成することもできます。

1. Excel で: 
    - Excel ではデータ型の一覧がキャッシュされるため、新しく発行されたおすすめのテーブルを表示するには、Excel を再起動する必要があります。
    - 一部のデータセットはプレビュー段階ではサポートされておらず、これらのデータセット内で定義されているおすすめのテーブルは Excel に表示されません。 詳細については、次のセクションの「考慮事項と制限事項」を参照してください。

## <a name="considerations-and-limitations"></a>考慮事項と制限事項

初期プレビューの制限事項を次に示します。

- 次の機能を使用する Power BI データセットのおすすめのテーブルは、Excel に表示されません。

    - DirectQuery データセット。
    - ライブ接続を使用するデータセット。

- Excel には、おすすめのテーブルの列および計算列のデータのみが表示されます。 関連テーブルに定義されているメジャー、リレーションシップから計算された暗黙のメジャーは、初期プレビューでは提供されません。
- Excel には、新しい Power BI ワークスペースに格納されているおすすめのテーブルのみが表示されます。 クラシック ワークスペースに格納されているおすすめのテーブルは、Excel ではデータ型として表示されません。 Power BI で[クラシック ワークスペースを新しいワークスペースにアップグレードする](service-upgrade-workspaces.md)ことができます。
- その他の Excel の考慮事項については、「Excel で Power BI のおすすめのテーブルにアクセスする」の記事にある「[注意点と制限事項](service-excel-featured-tables.md#considerations-and-limitations)」を参照してください。

## <a name="next-steps"></a>次の手順

- [Excel で Power BI のおすすめのテーブルにアクセスする](service-excel-featured-tables.md)
- [Power BI からの Excel のデータ型の使用](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9)について、Excel のドキュメントを参照します。
- わからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。

