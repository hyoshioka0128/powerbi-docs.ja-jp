---
title: Power BI Desktop でおすすめのテーブルを設定する
description: Excel の組織データ型ギャラリーに表示されるように、Power BI Desktop でおすすめのテーブルを作成します。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 12/07/2020
LocalizationGroup: Share your work
ms.openlocfilehash: 8c03263e7cc3a8833c06523601fcc12ef14484e1
ms.sourcegitcommit: 30d0668434283c633bda9ae03bc2aca75401ab94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/09/2020
ms.locfileid: "96906890"
---
# <a name="set-featured-tables-in-power-bi-desktop-to-show-in-excel-organization-data-types-gallery"></a>Excel の組織データ型ギャラリーに表示されるように、おすすめのテーブルを Power BI Desktop で設定する

Excel のデータ型ギャラリーでは、ユーザーが Power BI データセットの "*おすすめのテーブル*" からのデータを検索することができます。 この記事では、データセットの *おすすめの* テーブルを設定する方法について説明します。 これらのタグを使用すると、ユーザーが Excel シートにエンタープライズ データを簡単に追加できるようになります。 おすすめのテーブルを設定して共有するための基本的な手順を次に示します。

1. Power BI Desktop でデータセット内のおすすめのテーブルを識別します (この記事)。
1. おすすめのテーブルを含むこれらのデータセットを、新しいワークスペースのいずれかに保存します。 レポート作成者は、これらのおすすめのテーブルを使用してレポートを作成できます。 
1. 組織の残りの部分は、関連する更新可能なデータのために、これらのおすすめのテーブル (*Excel ではデータ型と呼ばれる*) に接続できます。 「[Excel で Power BI のおすすめのテーブルにアクセスする](service-excel-featured-tables.md)」の記事に、Excel でこれらのおすすめのテーブルを使用する方法が説明されています。

> [!NOTE]
> [Power BI でデータセットを昇格または認定](../collaborate-share/service-endorse-content.md)することができます。 これは "*承認*" と呼ばれます。 Excel によって、データ型ギャラリーで承認されたデータセット内のテーブルの優先順位が設定されます。 Excel によって、最初に認定済みデータセットのおすすめのテーブルが一覧表示され、次に昇格されたデータセットのテーブルが一覧表示されます。 Excel によって、その後、承認されていないデータセットのおすすめのテーブルが一覧表示されます。 

> [!NOTE]
> Power BI Desktop の 2020 年 12 月のバージョン以降では、既定でおすすめテーブルを作成できるようになっています。 以前のバージョンを使用している場合は、Power BI Desktop をアップグレードするか、あるいは **[おすすめのテーブル]** 機能を有効にします (それには、 **[ファイル]**  >  **[オプションと設定]**  >  **[オプション]**  >  **[プレビュー機能]** の順に選択します)。

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
    - 一部のデータセットはサポートされていません。 それらのデータセット内で定義されているおすすめのテーブルは、Excel には表示されません。 詳細については、次のセクションの「考慮事項と制限事項」を参照してください。

## <a name="considerations-and-limitations"></a>考慮事項と制限事項

現在の制限事項は次のとおりです。

- 統合は、現在のチャネルの Excel で使用できます。
- 次の機能を使用する Power BI データセットのおすすめのテーブルは、Excel に表示されません。 

    - DirectQuery データセット。
    - ライブ接続を使用するデータセット。

- Excel には、おすすめのテーブルで定義されている列、計算列、およびメジャーのデータのみが表示されます。 次のものは表示されません。
   
    - 関連テーブル上で定義されているメジャー。
    - リレーションシップから算出される暗黙的なメジャー。

- Excel には、新しい Power BI ワークスペースに格納されているおすすめのテーブル ("*データ型*") のみが表示されます。 クラシック ワークスペースに格納されているおすすめのテーブルは、Excel ではデータ型として表示されません。 Power BI で[クラシック ワークスペースを新しいワークスペースにアップグレードする](service-upgrade-workspaces.md)ことができます。

Excel でのデータ型のエクスペリエンスは、lookup 関数に似ています。 Excel シートから提供されるセル値を受け取り、Power BI のおすすめのテーブルで一致する行が検索されます。 検索エクスペリエンスには、次のような動作があります。

- 行の一致は、おすすめのテーブルに含まれるテキスト列に基づいています。 これには Power BI Q&A 機能と同じインデックスが使用されます。これは英語での検索用に最適化されています。 その他の言語で検索すると、正確な一致が得られない場合があります。 
- ほとんどの数値列は、照合の対象とは見なされません。 行ラベルまたはキー列が数値である場合は、それらは照合の対象に含められます。
- 一致は、個々の検索語句の完全一致とプレフィックス一致に基づいています。 セルの値は、スペース、またはタブのようなその他の空白文字に基づいて分割されます。 その後、各単語が検索語句と見なされます。 行のテキスト フィールドの値が、完全一致とプレフィックス一致で各検索語句と比較されます。 行のテキスト フィールドがその検索語句で始まる場合は、プレフィックス一致が返されます。 たとえば、セルに "Orange County" が含まれていた場合、"Orange" と "County" が個別の検索語句になります。 

    - 値が "Orange" または "County" と完全に一致するテキスト列を含む行が返されます。 
    - 値が "Orange" または "County" で始まるテキスト列を含む行が返されます。 
    - 重要なこととして、"Orange" または "County" を含んでいても、それらの語句で始まらない行は返されません。

- Power BI では、各セルに対して最大 100 行の候補が返されます。
- 一部のシンボルはサポートされていません。
- XMLA エンドポイントでのおすすめのテーブルの設定または更新はサポートされていません
- データ モデルを含む Excel ファイルを使用して、おすすめのテーブルを発行することができます。 そのデータを Power BI Desktop に読み込んでから、おすすめのテーブルを発行します。
- おすすめのテーブル内のテーブル名、行ラベル、またはキー列を変更すると、そのテーブルの行にリンクされたセルを使用する Excel ユーザーに影響を及ぼす場合があります。 
- Excel では、データが Power BI データセットから取得された日時が表示されます。 今回は、Power BI でデータが更新された時間、またはデータセット内の最新のデータ ポイントの時間であるとは限りません。 たとえば、Power BI のデータセットが 1 週間前に更新されましたが、基になるソース データは更新が行われた時点で 1 週間経過していたとします。 実際のデータは 2 週間前のものになりますが、Excel によって、データが Excel に取り込まれた日付/時刻として、取得されたデータが表示されます。
- その他の Excel の考慮事項については、「Excel で Power BI のおすすめのテーブルにアクセスする」の記事にある「[注意点と制限事項](service-excel-featured-tables.md#considerations-and-limitations)」を参照してください。

## <a name="next-steps"></a>次の手順

- [Excel で Power BI のおすすめのテーブルにアクセスする](service-excel-featured-tables.md)
- [Power BI からの Excel のデータ型の使用](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9)について、Excel のドキュメントを参照します。
- わからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。

