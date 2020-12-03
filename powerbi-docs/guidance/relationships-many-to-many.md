---
title: 多対多のリレーションシップのガイダンス
description: 多対多のモデル リレーションシップを築くためのガイダンス。
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 03/02/2020
ms.openlocfilehash: 95383581a258374f2757581e82fa0f2044dcae84
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418626"
---
# <a name="many-to-many-relationship-guidance"></a>多対多のリレーションシップのガイダンス

この記事は、Power BI Desktop を操作するデータ モデラーを対象としています。 3 つの異なる多対多モデリング シナリオについて説明します。 また、モデルで正しく設計する方法についてのガイダンスも提供します。

[!INCLUDE [relationships-prerequisite-reading](includes/relationships-prerequisite-reading.md)]

実際には、3 つの多対多のシナリオがあります。 これらは、次のことが必要な場合に発生する可能性があります。

- [2 つのディメンションの種類のテーブルを関連付ける](#relate-many-to-many-dimensions)
- [2 つのファクトの種類のテーブルを関連付ける](#relate-many-to-many-facts)
- ファクトの種類のテーブルに、ディメンションの種類のテーブル行よりも高い粒度で行を格納する場合に、[より高い粒度のファクトの種類のテーブルを関連付ける](#relate-higher-grain-facts)

## <a name="relate-many-to-many-dimensions"></a>多対多ディメンションを関連付ける

例を使って、最初の多対多シナリオの種類について考えてみましょう。 従来のシナリオでは、銀行の顧客と銀行口座という 2 つのエンティティが関連付けられます。 顧客は複数の口座を持つことができ、口座に対して複数の顧客が存在できるとします。 1 つの口座に対して複数の顧客が存在する場合、それらは一般に "_共同口座名義人_" と呼ばれます。

これらのエンティティのモデリングは簡単です。 1 つのディメンションの種類のテーブルに口座が格納され、もう 1 つのディメンションの種類のテーブルには顧客が格納されます。 ディメンションの種類のテーブルの特性と同様、各テーブルには ID 列があります。 2 つのテーブル間のリレーションシップをモデリングするには、3 番目のテーブルが必要です。 このテーブルは、一般に "_ブリッジング テーブル_" と呼ばれます。 この例では、顧客と口座の関連付けごとに 1 つの行を格納することを目的としています。 興味深いことに、このテーブルに ID 列のみが含まれている場合は、"[_ファクトレス ファクト テーブル_](star-schema.md#factless-fact-tables)" と呼ばれます。

3 つのテーブルのシンプルなモデル図を以下に示します。

![3 つのテーブルを含むモデルを示す図。 設計については、次の段落で説明します。](media/relationships-many-to-many/bank-account-customer-model-example.png)

最初のテーブルには **Account** という名前が付けられ、次の 2 つの列が含まれています: **AccountID** と **Account**。 2 番目のテーブルには **AccountCustomer** という名前が付けられ、次の 2 つの列が含まれています: **AccountID** と **CustomerID**。 3 番目のテーブルには **Customer** という名前が付けられ、次の 2 つの列が含まれています: **CustomerID** と **Customer**。 どのテーブル間にもリレーションシップは存在しません。

テーブルを関連付けるために、2 つの一対多リレーションシップが追加されます。 関連テーブルの更新されたモデル図を以下に示します。 **Transaction** という名前のファクトの種類のテーブルが追加されました。 これには口座取引が記録されています。 ブリッジング テーブルとすべての ID 列が非表示になりました。

![モデルに含まれるテーブルが 4 つになったことを示す図。 すべてのテーブルを関連付けるために、一対多リレーションシップが追加されました。](media/relationships-many-to-many/bank-account-customer-model-related-tables-1.png)

リレーションシップ フィルターの伝達のしくみを説明するのに役立つように、モデル図が変更されてテーブル行が表示されました。

> [!NOTE]
> Power BI Desktop モデル図にテーブル行を表示することはできません。 この記事では、わかりやすい例による説明をサポートするためにこのようにしています。

![モデルでテーブル行が表示されるようになったことを示す図。 4 つのテーブルの行の詳細については、次の段落で説明します。](media/relationships-many-to-many/bank-account-customer-model-related-tables-2.png)

4 つのテーブルの行の詳細については、次の箇条書きで説明します。

- **Account** テーブルには、次の 2 つの行があります。
  - **AccountID** の 1 は Account-01 用です
  - **AccountID** の 2 は Account-02 用です
- **Customer** テーブルには、次の 2 つの行があります。
  - **CustomerID** の 91 は Customer-91 用です
  - **CustomerID** の 92 は Customer-92 用です
- **AccountCustomer** テーブルには、次の 3 つの行があります。
  - **AccountID** の 1 は、**CustomerID** の 91 に関連付けられています
  - **AccountID** の 1 は、**CustomerID** の 92 に関連付けられています
  - **AccountID** の 2 は、**CustomerID** の 92 に関連付けられています
- **Transaction** テーブルには、次の 3 つの行があります。
  - **Date** は 2019 年 1 月 1 日、**AccountID** は 1、**Amount** は 100 です
  - **Date** は 2019 年 2 月 2 日、**AccountID** は 2、**Amount** は 200 です
  - **Date** は 2019 年 3 月 3 日、**AccountID** は 1、**Amount** は -25 です

モデルにクエリを実行するとどうなるかを見てみましょう。

**Transaction** テーブルから **Amount** 列を集計する 2 つのビジュアルを以下に示します。 最初のビジュアルでは口座別にグループ化されているため、**Amount** 列の合計は "_口座残高_" を表します。 2 番目のビジュアルでは顧客別にグループ化されているため、**Amount** 列の合計は "_顧客残高_" を表します。

![2 つのレポート ビジュアルが左右に並べて表示されている図。 ビジュアルについては、次の段落で説明します。](media/relationships-many-to-many/bank-account-customer-model-queried-1.png)

最初のビジュアルには **Account Balance** というタイトルが付いており、次の 2 つの列があります: **Account** と **Amount**。 これには次の結果が表示されています。

- Account-01 の残額は 75 です
- Account-02 の残額は 200 です
- 合計は 275 です

2 番目のビジュアルには **Customer Balance** というタイトルが付いており、次の 2 つの列があります: **Customer** と **Amount**。 これには次の結果が表示されています。

- Customer-91 の残額は 275 です
- Customer-92 の残額は 275 です
- 合計は 275 です

テーブル行と **Account Balance** ビジュアルをひとめ見れば、各口座と合計額の結果が正しいことがわかります。 これは、各口座のグループ化によって、その口座の **Transaction** テーブルにフィルターが伝達されるためです。

しかし、**Customer Balance** ビジュアルでは、何かが正しくないように見えます。 **Customer Balance** の各顧客の残高が、合計残高と同じになっています。 この結果は、すべての顧客がすべての口座の共同口座名義人だった場合にのみ、正しいものになる可能性があります。 この例ではそうではありません。 この問題はフィルターの伝達に関連しています。 **Transaction** テーブルへのフローがありません。

**Customer** テーブルから **Transaction** テーブルへのリレーションシップのフィルター方向をたどってください。 **Account** と **AccountCustomer** テーブル間のリレーションシップが間違った方向に伝達されているのは明らかです。 このリレーションシップのフィルター方向は、**両方** に設定する必要があります。

![モデルが更新されたことを示す図。 これで、両方向にフィルター処理されるようになりました。](media/relationships-many-to-many/bank-account-customer-model-related-tables-3.png)

![同じ 2 つのレポート ビジュアルが左右に並べて表示されている図。 1 番目のビジュアルは変更されていませんが、2 番目のビジュアルは変更されています。](media/relationships-many-to-many/bank-account-customer-model-queried-2.png)

予想どおり、**Account Balance** ビジュアルに変更はありませんでした。

しかし、**Customer Balance** ビジュアルでは、次の結果が表示されるようになりました。

- Customer-91 の残額は 75 です
- Customer-92 の残額は 275 です
- 合計は 275 です

これで、**Customer Balance** ビジュアルで正しい結果が表示されるようになりました。 ご自分でフィルター方向をたどり、顧客残高がどのように計算されたかを確認してください。 また、ビジュアルの合計が "_すべての顧客_" を意味していることを理解してください。

モデル リレーションシップに慣れていないユーザーは、結果が正しくないと判断する可能性があります。 次のように質問するかもしれません: "_**Customer-91** と **Customer-92** の合計残高が 350 (75 + 275) に等しくないのはなぜか?_ "

この質問に対する答えは、多対多リレーションシップを理解することで見つかります。 各顧客残高では、複数の口座残高の加算を表すことができるため、この顧客残高は "_非加算_" となります。

### <a name="relate-many-to-many-dimensions-guidance"></a>多対多ディメンションの関連付けに関するガイダンス

ディメンションの種類のテーブル間に多対多リレーションシップがある場合は、次のガイダンスに従ってください。

- 多対多の関連エンティティをそれぞれモデル テーブルとして追加し、一意識別子 (ID) 列が確実に含まれるようにする
- 関連エンティティを格納するためのブリッジング テーブルを追加する
- 3 つのテーブル間に一対多リレーションシップを作成する
- フィルター伝達がファクトの種類のテーブルまで続くように、**1 つ** の双方向リレーションシップを構成する
- ID 値が欠落していることが適切でない場合は、ID 列の **Is Nullable** プロパティを FALSE に設定する。これで、欠落値が発生した場合に、データ更新が失敗するようになります。
- ブリッジング テーブルを非表示にする (レポートに必要な追加の列やメジャーが含まれている場合を除く)
- レポートに適さない ID 列をすべて非表示にする (ID が代理キーである場合など)
- ID 列を表示したままにすることが妥当である場合は、リレーションシップの "一" 側にあることを確認する。つまり、常に "多" 側の列を非表示にします。 これで、最適なフィルター パフォーマンスが得られます。
- 混乱や誤解を避けるために、レポート ユーザーに説明を伝える。テキスト ボックスや[ビジュアル ヘッダーのヒント](report-page-tooltips.md)で説明を加えることができます

多対多ディメンションの種類のテーブルを直接関連付けることはお勧めしません。 この設計手法では、多対多カーディナリティのリレーションシップを構成する必要があります。 概念的には、これは実現できますが、関連列に重複値が含まれるようになることを意味します。 これは広く受け入れられている設計方法ですが、そのディメンションの種類のテーブルには ID 列があります。 ディメンションの種類のテーブルでは常に、リレーションシップの "一" 側として ID 列を使用する必要があります。

## <a name="relate-many-to-many-facts"></a>多対多ファクトを関連付ける

2 番目の多対多シナリオの種類には、2 つのファクトの種類のテーブルの関連付けが含まれます。 2 つのファクトの種類のテーブルを直接関連付けることができます。 この設計手法は、迅速かつ簡単にデータを探索するのに役立ちます。 しかし、誤解のないように言うと、この設計手法は一般的にはお勧めできません。 その理由については、このセクションで後ほど説明します。

次の 2 つのファクトの種類のテーブルを含む例を考えてみましょう: **Order** と **Fulfillment**。 **Order** テーブルには注文明細行ごとに 1 行が含まれており、**Fulfillment** テーブルには、注文明細行ごとに 0 個以上の行を含めることができます。 **Order** テーブル内の行は、販売注文を表します。 **Fulfillment** テーブル内の行は、出荷された注文品目を表します。 多対多リレーションシップでは、2 つの **OrderID** 列が関連付けられ、フィルターは **Order** テーブルからのみ伝達されます (**Order** で **Fulfillment** をフィルター処理)。

![2 つのテーブルを含むモデルを示す図: Order と Fulfillment。](media/relationships-many-to-many/order-fulfillment-model-example.png)

両方のテーブルでの重複する **OrderID** 値の格納をサポートするために、リレーションシップ カーディナリティが多対多に設定されています。 **Order** テーブルでは、重複する **OrderID** 値が存在できます。これは、1 つの注文に複数の行を含めることができるためです。 **Fulfillment** テーブルでは、重複する **OrderID** 値が存在できます。これは、注文に複数の行が含まれる可能性があり、注文明細行が多数の出荷で満たせるためです。

次は、テーブル行を見てみましょう。 **Fulfillment** テーブルでは、注文明細行を複数の出荷で満たせることに注目してください (注文明細行がない場合は、注文がまだ満たされていないことを意味します)。

![モデルでテーブル行が表示されるようになったことを示す図。 2 つのテーブルの行の詳細については、次の段落で説明します。](media/relationships-many-to-many/order-fulfillment-model-related-tables.png)

2 つのテーブルの行の詳細については、次の箇条書きで説明します。

- **Order** テーブルには、以下の 5 つの行があります。
  - **OrderDate** は 2019 年 1 月 1 日、**OrderID** は 1、**OrderLine** は 1、**ProductID** は Prod-A、**OrderQuantity** は 5、**Sales** は 50 です
  - **OrderDate** は 2019 年 1 月 1 日、**OrderID** は 1、**OrderLine** は 2、**ProductID** は Prod-B、**OrderQuantity** は 10、**Sales** は 80 です
  - **OrderDate** は 2019 年 2 月 2 日、**OrderID** は 2、**OrderLine** は 1、**ProductID** は Prod-B、**OrderQuantity** は 5、**Sales** は 40 です
  - **OrderDate** は 2019 年 2 月 2 日、**OrderID** は 2、**OrderLine** は 2、**ProductID** は Prod-C、**OrderQuantity** は 1、**Sales** は 20 です
  - **OrderDate** は 2019 年 3 月 3 日、**OrderID** は 3、**OrderLine** は 1、**ProductID** は Prod-C、**OrderQuantity** は 5、**Sales** は 100 です
- **Fulfillment** テーブルには、次の 4 つの行があります。
  - **FulfillmentDate** は 2019 年 1 月 1 日、**FulfillmentID** は 50、**OrderID** は 1、**OrderLine** は 1、**FulfillmentQuantity** は 2 です
  - **FulfillmentDate** は 2019 年 2 月 2 日、**FulfillmentID** は 51、**OrderID** は 2、**OrderLine** は 1、**FulfillmentQuantity** は 5 です
  - **FulfillmentDate** は 2019 年 2 月 2 日、**FulfillmentID** は 52、**OrderID** は 1、**OrderLine** は 1、**FulfillmentQuantity** は 3 です
  - **FulfillmentDate** は 2019 年 1 月 1 日、**FulfillmentID** は 53、**OrderID** は 1、**OrderLine** は 2、**FulfillmentQuantity** は 10 です

モデルにクエリを実行するとどうなるかを見てみましょう。 次の表では、注文と調達の数量を **Order** テーブルの **OrderID** 列で比較しています。

![次の 3 つの列を含むテーブル ビジュアルを示す図。OrderID、OrderQuantity、および FulfillmentQuantity という 3 つの列があります。](media/relationships-many-to-many/order-fulfillment-model-queried.png)

ビジュアルには正確な結果が示されています。 しかし、モデルの有用性は限られています。フィルター処理またはグループ化できるのは、**Order** テーブルの **OrderID** 列でのみとなります。

### <a name="relate-many-to-many-facts-guidance"></a>多対多ファクトの関連付けに関するガイダンス

一般には、多対多カーディナリティを使用して、2 つのファクトの種類のテーブルを直接関連付けることはお勧めしません。 主な理由は、モデルでは、ビジュアル フィルターやグループをレポートする方法に柔軟性がないためです。 この例では、ビジュアルでフィルター処理またはグループ化できるのは、**Order** テーブルの **OrderID** 列でのみとなります。 他の理由は、データの品質に関連します。 データに整合性の問題がある場合、"_制限付きリレーションシップ_" の性質により、一部の行がクエリの実行中に省略される可能性があります。 詳細については、[Power BI Desktop でのモデル リレーションシップ (リレーションシップの評価)](../transform-model/desktop-relationships-understand.md#relationship-evaluation) に関する記事をご覧ください。

ファクトの種類のテーブルを直接関連付けるのではなく、[スター スキーマ](star-schema.md)設計原則を採用することをお勧めします。 これを行うには、ディメンションの種類のテーブルを追加します。 一対多リレーションシップを使用して、ディメンションの種類のテーブルをファクトの種類のテーブルに関連付けます。 この設計手法は、柔軟なレポート オプションが提供されるため、堅牢です。 これにより、ディメンションの種類の列のいずれかを使用して、フィルター処理またはグループ化を行い、関連するファクトの種類のテーブルを集計することができます。

より優れたソリューションについて考えてみましょう。

![モデルを示す図には、次の 6 つのテーブルが含まれます。OrderLine、OrderDate、Order、Fulfillment、Product、および FulfillmentDate。](media/relationships-many-to-many/order-fulfillment-model-improved.png)

次の設計変更に注目してください。

- モデルには現在、次の 4 つの追加テーブルがあります: **OrderLine**、**OrderDate**、**Product**、および **FulfillmentDate**
- 4 つの追加テーブルはすべてディメンションの種類のテーブルであり、一対多リレーションシップではこれらのテーブルがファクトの種類のテーブルに関連付けられます
- **OrderLine** テーブルには、**OrderLineID** 列が含まれており、100 を乗算した **OrderID** 値と、**OrderLine** 値 (各注文明細行の一意識別子) を表しています
- **Order** と **Fulfillment** テーブルには現在、**OrderLineID** 列が含まれており、**OrderID** と **OrderLine** 列は含まれなくなりました
- **Fulfillment** テーブルには現在、**OrderDate** と **ProductID** 列が含まれています
- **FulfillmentDate** テーブルは、**Fulfillment** テーブルにのみ関連しています
- すべての一意識別子列は非表示になっています

時間をかけてスター スキーマの設計原則を適用することには、次のような利点があります。

- レポート ビジュアルでは、ディメンションの種類のテーブルの任意の表示列で、"_フィルター処理またはグループ化_" することができます
- レポート ビジュアルでは、ファクトの種類のテーブルの任意の表示列を "_集計_" できます
- **OrderLine**、**OrderDate**、または **Product** テーブルに適用されたフィルターは、両方のファクトの種類のテーブルに伝達されます
- すべてのリレーションシップは一対多であり、各リレーションシップは "_制限付きリレーションシップ_" となります。 データ整合性の問題はマスクされません。 詳細については、[Power BI Desktop でのモデル リレーションシップ (リレーションシップの評価)](../transform-model/desktop-relationships-understand.md#relationship-evaluation) に関する記事をご覧ください。

## <a name="relate-higher-grain-facts"></a>より高い粒度のファクトを関連付ける

この多対多シナリオは、この記事で既に説明した他の 2 つのシナリオとは大きく異なります。

次の 4 つのテーブルを含む例を考えてみましょう: **Date**、**Sales**、**Product**、および **Target**。 **Date** と **Product** はディメンションの種類のテーブルであり、一対多リレーションシップでは、それぞれが **Sales** というファクトの種類のテーブルに関連付けられます。 今のところ、適切なスター スキーマ設計が示されています。 しかし、**Target** テーブルは、まだ他のテーブルに関連付けられていません。

![次の 4 つのテーブルを含むモデルを示す図: Date、Sales、Product、および Target。](media/relationships-many-to-many/sales-targets-model-example.png)

**Target** テーブルには、次の 3 つの列が含まれています: **Category**、**TargetQuantity**、および **TargetYear**。 テーブル行では、年と製品カテゴリの粒度が示されています。 つまり、販売実績を測定するために使用されるターゲットは、各製品カテゴリに対して毎年設定されます。

![Target テーブルに次の 3 つの列が含まれていることを示す図: TargetYear、Category、および TargetQuantity。](media/relationships-many-to-many/sales-targets-model-target-rows.png)

**Target** テーブルでは、ディメンションの種類のテーブルよりも高いレベルのデータが格納されるため、一対多リレーションシップを作成することはできません。 しかし、これはリレーションシップの 1 つにのみ当てはまることです。 ここでは、**Target** テーブルをディメンションの種類のテーブルにどのように関連付けられるかを説明します。

### <a name="relate-higher-grain-time-periods"></a>より高い粒度の期間を関連付ける

**Date** と **Target** テーブルの間のリレーションシップは、一対多リレーションシップである必要があります。 これは、**TargetYear** 列の値が日付であるためです。 この例では、各 **TargetYear** 列の値は、ターゲット年の最初の日付です。

> [!TIP]
> 日よりも高い時間の粒度でファクトを格納する場合は、列のデータ型を **Date** (または、日付キーを使用する場合は **整数**) に設定します。 列には、期間の最初の日を表す値を格納します。 たとえば、年期は年の 1 月 1 日として記録され、月期はその月の最初の日として記録されます。

しかし、月または日付レベルのフィルターで確実に意味のある結果を得るには、注意が必要です。 特別な計算ロジックを使用しないと、レポート ビジュアルで、ターゲットの日付が文字どおり、各年の最初の日であると報告される可能性があります。 それ以外のすべての日 (1 月を除くすべての月) では、ターゲット数量が空白として集計されます。

次のマトリックス ビジュアルでは、レポート ユーザーがある年からその月にドリルダウンしたときの動作が示されています。 このビジュアルでは、**TargetQuantity** 列が集計されています (マトリックス行に対して [[データのない項目を表示する]](../create-reports/desktop-show-items-no-data.md) オプションが有効になっている)。

![マトリックス ビジュアルで、2020 年のターゲット数量が 270 として表示されていることを示す図。](media/relationships-many-to-many/sales-targets-model-matrix-blank-months-bad.png)

この動作を回避するために、メジャーを使用して、ファクト データの集計を制御することをお勧めします。 集計を制御する方法の 1 つは、下位レベルの期間に対してクエリが実行されたときに空白を返すことです。 いくつかの高度な DAX で定義されているもう 1 つの方法は、下位レベルの期間にわたって値を分配することです。

[ISFILTERED](/dax/isfiltered-function-dax) DAX 関数を使用する次のメジャー定義について考えてみます。 **Date** や **Month** 列がフィルター処理されていない場合にのみ、値が返されます。

```dax
Target Quantity =
IF(
    NOT ISFILTERED('Date'[Date])
        && NOT ISFILTERED('Date'[Month]),
    SUM(Target[TargetQuantity])
)
```

これで、次のマトリックス ビジュアルで、**Target Quantity** メジャーが使用されるようになりました。 これは、毎月のターゲット数量がすべて空白であることを示しています。

![2020 年のターゲット数量が 270 で、毎月の値が空白であることが示されているマトリックス視覚エフェクトの図。](media/relationships-many-to-many/sales-targets-model-matrix-blank-months-good.png)

### <a name="relate-higher-grain-non-date"></a>より高い粒度を関連付ける (日付以外)

日付以外の列をディメンションの種類のテーブルからファクトの種類のテーブルに関連付ける (また、ディメンションの種類のテーブルよりも粒度が高い) 場合は、異なる設計手法が必要です。

**Category** 列 (**Product** と **Target** テーブルの両方のもの) には、重複値が含まれています。 そのため、一対多リレーションシップの "一" はありません。 この場合は、多対多リレーションシップを作成する必要があります。 リレーションシップでは、ディメンションの種類のテーブルからファクトの種類のテーブルへの、一方向でフィルターを伝達する必要があります。

![Target テーブルと Product テーブルのモデルを示す図。 多対多リレーションシップでは、2 つのテーブルが関連付けられます。](media/relationships-many-to-many/sales-targets-model-relate-non-date.png)

次は、テーブル行を見てみましょう。

![2 つのテーブルを含むモデルを示す図: Target と Product。 多対多リレーションシップでは、2 つの Category 列が関連付けられます。](media/relationships-many-to-many/sales-targets-model-relate-non-date-tables.png)

**Target** テーブルには、4 つの行、つまり、ターゲット年 (2019 と 2020) ごとに 2 行と、2 つのカテゴリ (Clothing と Accessories) があります。 **Product** テーブルには、3 つの製品があります。 2 つは衣料カテゴリに属し、1 つはアクセサリ カテゴリに属しています。 衣料の色の 1 つは緑で、残りの 2 つは青です。

**Product** テーブルの **Category** 列でグループ化するテーブル ビジュアルでは、次の結果が得られました。

![次の 2 つの列を持つテーブル ビジュアルを示す図: Category と TargetQuantity。 Accessories は 60、Clothing は 40 で、合計は 100 です。](media/relationships-many-to-many/sales-targets-model-visual-category-targets.png)

このビジュアルでは、正しい結果が得られました。 次は、**Product** テーブルの **Color** 列を使用して、ターゲット数量をグループ化するとどうなるかを考えてみましょう。

![次の 2 つの列を持つテーブル ビジュアルを示す図: Color と TargetQuantity。 Blue は 100、Green は 40 で、合計は 100 です。](media/relationships-many-to-many/sales-targets-model-visual-color-targets-bad.png)

このビジュアルでは、データが誤った表示になっています。 ここで何が起きているのでしょうか。

**Product** テーブルの **Color** 列にフィルターを適用すると、2 つの行が生成されます。 行の 1 つは Clothing カテゴリ用で、もう 1 つは Accessories カテゴリ用です。 これら 2 つのカテゴリ値は、フィルターとして **Target** テーブルに伝達されます。 つまり、青色は 2 つのカテゴリの製品で使用されるため、ターゲットのフィルター処理には "_それらのカテゴリ_" が使用されます。

この動作を回避するために、前述のように、メジャーを使用して、ファクト データの集計を制御することをお勧めします。

次のメジャー定義について考えます。 カテゴリ レベルの下にあるすべての **Product** テーブル列が、フィルターに対してテストされていることに注目してください。

```dax
Target Quantity =
IF(
    NOT ISFILTERED('Product'[ProductID])
        && NOT ISFILTERED('Product'[Product])
        && NOT ISFILTERED('Product'[Color]),
    SUM(Target[TargetQuantity])
)
```

これで、次のテーブル ビジュアルで、**Target Quantity** メジャーが使用されるようになりました。 これは、すべての色のターゲット数量が空白であることを示しています。

![次の 2 つの列を持つテーブル ビジュアルを示す図: Color と TargetQuantity。 Blue は空白、Green は空白で、合計は 100 です。](media/relationships-many-to-many/sales-targets-model-visual-color-targets-good.png)

最終的なモデル設計は次のようになります。

![Date および Target テーブルが一対多リレーションシップで関連付けられていることを示す図。](media/relationships-many-to-many/sales-targets-model-example-final.png)

### <a name="relate-higher-grain-facts-guidance"></a>より高い粒度のファクトの関連付けに関するガイダンス

ディメンションの種類のテーブルをファクトの種類のテーブルに関連付ける必要があり、ファクトの種類のテーブルに、ディメンションの種類のテーブル行よりも高い粒度で行を格納する場合は、次のガイダンスに従ってください。

- より高い粒度のファクトの日付の場合:
  - ファクトの種類のテーブルに、期間の最初の日付を格納する
  - 日付テーブルとファクトの種類のテーブルの間に一対多リレーションシップを作成する
- その他のより高い粒度のファクトの場合:
  - ディメンションの種類のテーブルとファクトの種類のテーブルの間に多対多リレーションシップを作成する
- 両方の種類の場合:
  - メジャー ロジックで集計を制御する。フィルター処理またはグループ化を行うために、下位レベルのディメンションの種類の列が使用される場合は空白を返すようにします
  - 集計可能なファクトの種類のテーブル列を非表示にする。この方法では、ファクトの種類のテーブルを集計するためにのみメジャーを使用できます

## <a name="next-steps"></a>次の手順

この記事に関する詳細については、次のリソースを参照してください。

- [Power BI Desktop でのモデル リレーションシップ](../transform-model/desktop-relationships-understand.md)
- [Power BI のスター スキーマおよび重要性について](star-schema.md)
- [リレーションシップのトラブルシューティング ガイダンス](relationships-troubleshoot.md)
- わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
- Power BI チームへのご提案は、 [Power BI を改善するためのアイデアをお寄せください](https://ideas.powerbi.com/)
