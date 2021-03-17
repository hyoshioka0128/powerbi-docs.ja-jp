---
title: Power BI Premium で自動スケーリングを使用する
description: Power BI Premium Gen2 の自動スケーリングを使用すると、Power BI ユーザーの要件に合わせて、処理能力を自動的に拡張することができます
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-premium
ms.topic: conceptual
ms.date: 03/02/2021
ms.custom: licensing support
LocalizationGroup: Premium
ms.openlocfilehash: a07ce908a83fa9a620c453cd9990be098edc8b74
ms.sourcegitcommit: 13a150d1aa810f309421bf603fa8581718a4b299
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "101873269"
---
# <a name="using-autoscale-with-power-bi-premium"></a>Power BI Premium で自動スケーリングを使用する

Power BI Premium では、お客様の組織の Power BI コンテンツに応じたスケールとパフォーマンスが提供されます。 Power BI Premium Gen2 (プレビュー) では、パフォーマンスの向上、スケールの強化、メトリックの改善など、多くの機能強化が導入されています。 さらに、Premium Gen2 では、**自動スケーリング** を使用してコンピューティング容量を自動的に追加することで、使用率の増加時にも処理速度が低下しないようにすることができます。

:::image type="content" source="media/service-premium-auto-scale/premium-auto-scale-09.png" alt-text="Power BI Premium で自動スケーリングを使用している画面のスクリーンショット。":::

自動スケーリングでは、Azure サブスクリプションを使用して仮想コア (仮想 CPU コア) が自動的に追加されるので、容量不足によって Power BI Premium サブスクリプションのコンピューティング速度が低下するのを防ぐことができます。 この記事では、Power BI Premium サブスクリプションで自動スケーリングを機能させるために必要な手順について説明します。 自動スケーリングは、Power BI Premium Gen2 でのみ機能します。 

自動スケーリングを有効にするには、次の手順を完了する必要があります。

* 自動スケーリングで使用する Azure サブスクリプションを選択して構成する
* 選択した Azure サブスクリプションを自動スケーリングに使用するように、Power BI Premium を構成する

以下のセクションでは、これらの手順について説明します。

## <a name="configure-an-azure-subscription-to-use-with-autoscale"></a>自動スケーリングで使用する Azure サブスクリプションを構成する

Azure サブスクリプションを選択して自動スケーリングを使用するように構成するには、選択した Azure サブスクリプションに対する *共同作成者* 権限が必要です。 Azure サブスクリプションの *アカウント管理者* 権限を持つユーザーは、ユーザーを *共同作成者* として追加することができます。 また、自動スケーリングを有効にするには、Power BI テナントの管理者である必要があります。

自動スケーリングで使用する Azure サブスクリプションを選択するには、次の手順を実行します。

1. Azure portal にログインし、左側のウィンドウで **[サブスクリプション]** を選択します。 次の図では、*Pay-As-You-Go* というサブスクリプションが強調表示されています。 

    :::image type="content" source="media/service-premium-auto-scale/premium-auto-scale-02.png" alt-text="Azure portal からサブスクリプションを選択する画面のスクリーンショット。":::

2. サブスクリプションを選択します。 選択したら、自動スケーリングで使用する *リソース グループ* を作成する必要があります。 選択したサブスクリプションの **[設定]** で、 *[リソース グループ]* を選択します。 次に、 **[追加]** ボタンを選択して、新しい *リソース グループ* を作成します。 

    :::image type="content" source="media/service-premium-auto-scale/premium-auto-scale-03.png" alt-text="リソース グループを作成する画面のスクリーンショット。":::

3. **[リソース グループの作成]** ウィンドウが表示されます。このウィンドウで、リソース グループに名前を指定できます。 次の図では、*powerBIPremiumAutoscaleCores* というリソース グループ名が入力されています。 リソース グループには好きな名前を付けることができます。 サブスクリプションの名前とリソース グループの名前は、忘れないようにしてください。これらは、Power BI 管理ポータルで自動スケーリングを構成する際に、もう一度選択する必要があります。 

    :::image type="content" source="media/service-premium-auto-scale/premium-auto-scale-04.png" alt-text="リソース グループ名を入力する画面のスクリーンショット。":::

4. リソース グループの名前に問題がなければ、ポータル ウィンドウの左下隅にある **[確認と作成]** ボタンを選択します。 Azure によって情報が検証されたら、 **[作成]** ボタンを選択してリソース グループを作成します。 作成されると、Azure portal の右上隅に次のような通知が表示されます。

    :::image type="content" source="media/service-premium-auto-scale/premium-auto-scale-05.png" alt-text="リソース グループが正常に作成された画面のスクリーンショット。":::
 
ここでは、自動スケーリングに使用する **サブスクリプション** を Azure portal で選択し、そのサブスクリプションの **リソース グループ** を作成しました。 次の手順では、Power BI 管理ポータルで自動スケーリングを有効にし、先ほど作成したリソース グループにリンクします。

### <a name="considerations-for-preview-release"></a>プレビュー リリースに関する考慮事項

プレビューで自動スケーリングが開始されると、ユーザーには、使用レベルと CPU コア使用率に慣れるための期間が提供されます。 この初期期間には、自動スケーリングに使用するよう構成した Azure サブスクリプションに対する課金は適用されません。 通常、この期間は 30 日間となります。 組織の使用レベルに慣れるための最善の方法は、Power BI 管理ポータルで使用率のアラート通知にサインアップし、使用率のアラートを監視することです。

ページ分割されたレポートは、初期期間に使用率レベルを決定したり、自動スケーリングを使用するかどうかを判断するプロセスには含まれません。

## <a name="enable-autoscale-in-the-power-bi-admin-portal"></a>Power BI 管理ポータルで自動スケーリングを有効にする

自動スケーリングで使用する Azure サブスクリプションを選択し、前のセクションで説明したようにリソース グループを作成したら、自動スケーリングを有効にし、作成したリソース グループに関連付けることができます。 これらの手順を正常に完了するには、**自動スケーリング** を構成するユーザーが、少なくとも Azure サブスクリプションの "*共同作成者*" である必要があります。 詳細については、[Azure サブスクリプションの共同作成者ロールにユーザーを割り当てる方法](https://docs.microsoft.com/azure/cost-management-billing/manage/add-change-subscription-administrator)に関する記事を参照してください。 

次の手順は、自動スケーリングを有効にし、それをリソース グループに関連付ける方法を示したものです。

1. **Power BI 管理ポータル** を開き、左側のウィンドウで **[容量の設定]** を選択します。 Power BI Premium 容量に関する情報が表示されます。 

    :::image type="content" source="media/service-premium-auto-scale/premium-auto-scale-06.png" alt-text="Power BI 管理ポータルのスクリーンショット。":::

2. 自動スケーリングは、Power BI Premium Gen2 (プレビュー) でのみ機能します。 Gen2 の有効化は簡単です。 **[Premium Generation 2 (プレビュー)]** ボックスでスライダーを **[有効]** に移動するだけです。 

    :::image type="content" source="media/service-premium-auto-scale/enable-gen2.gif" alt-text="Premium Generation 2 を有効にする操作のビデオ。":::

3. **[自動スケーリングの管理]** ボタンを選択して **自動スケーリング** を有効にし、構成します。そうすると、 **[自動スケールの設定]** ウィンドウが表示されます。 **[自動スケールの有効化]** をオンにします。

    :::image type="content" source="media/service-premium-auto-scale/premium-auto-scale-07.png" alt-text="自動スケーリングを有効にする画面のスクリーンショット。":::

4. その後、自動スケーリングで使用する Azure サブスクリプションを選択できます。 現在のユーザーが使用できるサブスクリプションのみが表示されるので、これを行うユーザーは、少なくともサブスクリプションの "*共同作成者*" である必要があります。 サブスクリプションを選択したら、前のセクションで作成した **リソース グループ** を、サブスクリプションで使用可能なリソース グループの一覧から選択します。 

    :::image type="content" source="media/service-premium-auto-scale/premium-auto-scale-08.png" alt-text="自動スケーリングで使用するリソース グループを選択する画面のスクリーンショット。":::

5. 次に、自動スケーリングに使用する仮想コアの最大数を割り当て、その後、 **[保存]** を選択して設定を保存します。 Power BI によって変更が適用されると、ウィンドウが閉じ、ビューが **[容量の設定]** に戻ります。ここで、設定が適用されていることを確認できます。 次の図では、自動スケーリング用に最大 2 つの仮想コアが構成されています。

    :::image type="content" source="media/service-premium-auto-scale/premium-auto-scale-09.png" alt-text="自動スケーリングを構成する画面のスクリーンショット。":::

次の短いビデオは、Power BI Premium Gen2 の自動スケーリングを構成する操作がいかにスピーディかを示したものです。

:::image type="content" source="media/service-premium-auto-scale/configure-autoscale.gif" alt-text="Premium Generation 2 の自動スケーリングを構成する操作のビデオ。"::: 

これで、Power BI Premium Gen2 サブスクリプションが自動スケーリングを使用するように構成されたので、必要な応答性が自動的に確保されるようになり、使用率が高まった場合でも、組織内のユーザーが Power BI のコンテンツや分析情報を迅速に取得できるようになりました。 


## <a name="next-steps"></a>次のステップ

* [Power BI Premium とは](service-premium-what-is.md)
* [Power BI Premium のよく寄せられる質問](service-premium-faq.md)
* [Power BI Premium Per User に関する FAQ (プレビュー)](service-premium-per-user-faq.md)
* [Azure サブスクリプション管理者を追加または変更する](https://docs.microsoft.com/azure/cost-management-billing/manage/add-change-subscription-administrator)