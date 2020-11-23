---
title: Power BI Premium の購入方法
description: Power BI Premium を購入し、組織全体にコンテンツへのアクセスを可能する方法について説明します。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-premium
ms.topic: how-to
ms.date: 11/11/2020
LocalizationGroup: Premium
ms.openlocfilehash: 2250a93d5fc061ff1e9d67217d021686935a8db7
ms.sourcegitcommit: cc20b476a45bccb870c9de1d0b384e2c39e25d24
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2020
ms.locfileid: "94512725"
---
# <a name="how-to-purchase-power-bi-premium"></a>Power BI Premium の購入方法

この記事では、組織に Power BI Premium の容量を購入する方法について説明します。 この記事では、次のシナリオについて説明します。

- P SKU を一般的な運用シナリオで使用する。 P SKU には月単位または年単位のコミットメントが必要で、課金は月単位で行われます。

Power BI Premium の詳細については、「[Microsoft Power BI Premium とは何ですか?](service-premium-what-is.md)」を参照してください。 現在の価格と計画については、[Power BI の料金ページ](https://powerbi.microsoft.com/pricing/)および「[Power BI Premium 計算ツール](https://powerbi.microsoft.com/calculator/)」を参照してください。 ご自分の組織が Power BI Premium を使用している場合でも、コンテンツの作成者には引き続き [Power BI Pro のライセンス](service-admin-purchasing-power-bi-pro.md)が必要です。 組織で Power BI Pro ライセンスを少なくとも 1 つ購入してください。 A SKU では、コンテンツを使用する "_すべてのユーザー_" にも Pro ライセンスが必要です。

> [!NOTE]
> Premium サブスクリプションの有効期限が切れてから 30 日間は、容量への完全なアクセス権があります。 その後、コンテンツは共有された容量に戻ります。 1 GB を超えるモデルは、共有された容量ではサポートされません。

> [!NOTE]
> Power BI Premium に **Premium Gen2** という名前の新しいバージョンの Premium が最近リリースされました。現在はプレビュー段階です。 Premium Gen2 を使用すると、Premium 容量の管理が簡素化され、管理オーバーヘッドが削減されます。 詳細については、[Power BI Premium Generation 2 (プレビュー)](service-premium-what-is.md#power-bi-premium-generation-2-preview) に関する記事を参照してください。

## <a name="purchase-p-skus-for-typical-production-scenarios"></a>一般的な運用シナリオ用に P SKU を購入する

新しいテナントに Power BI Premium P1 SKU を構成して作成することも、既存の組織用に Power BI Premium 容量を購入することもできます。 いずれの場合も、容量は必要に応じて追加できます。

### <a name="create-a-new-tenant-with-power-bi-premium-p1"></a>Power BI Premium P1 で新しいテナントを作成する

既存のテナントをお持ちでない場合は、テナントの作成と同時に Power BI Premium も購入することができます。 次のリンクをクリックすると、新しいテナントを作成するプロセスが案内され、Power BI Premium を購入することができます: [Power BI Premium P1 プラン](https://signup.microsoft.com/Signup?OfferId=b3ec5615-cc11-48de-967d-8d79f7cb0af1)。 テナントを作成すると、そのテナントの Microsoft 365 の全体管理者ロールに自動的に割り当てられます。

容量の購入後は、[容量の管理](service-admin-premium-manage.md#manage-capacity)方法と、容量への[ワークスペースの割り当て](service-admin-premium-manage.md#assign-a-workspace-to-a-capacity)方法を学習してください。

### <a name="purchase-a-power-bi-premium-capacity-for-an-existing-organization"></a>既存の組織用の Power BI Premium 容量を購入する

既存の組織 (テナント) をお持ちの場合、サブスクリプションとライセンスを購入するには、Microsoft 365 の全体管理者ロールまたは課金管理者ロールである必要があります。 詳細については、[Microsoft 365 の管理者ロールについて](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d)のページを参照してください。

Premium 容量を購入するには、以下の手順に従います。

1. Power BI サービス内で、[Microsoft 365 アプリ ピッカー]、 **[管理者]** の順に選択します。

    ![Microsoft 365 アプリ ピッカー](media/service-admin-premium-purchase/o365-app-picker.png)

    または、Microsoft 365 管理センターを参照することができます。

1. **[請求]**  >  **[サービスを購入する]** を選択します。

1. **[その他のプラン]** で、Power BI Premium のオファーを探します。 これは P1 ～ P3、EM3、および P1 (月極め) として一覧表示されます。

1. 省略記号 ( **. . .** ) にポインターを合わせ、 **[今すぐ購入する]** を選択します。

    ![今すぐ購入](media/service-admin-premium-purchase/premium-purchase.png)

1. 以下の手順に従って、購入を完了します。

購入を完了すると、 **[サービスを購入する]** ページに購入したアクティブな項目が表示されます。

![Power BI Premium を購入した場合](media/service-admin-premium-purchase/premium-purchased.png)

容量の購入後は、[容量の管理](service-admin-premium-manage.md#manage-capacity)方法と、容量への[ワークスペースの割り当て](service-admin-premium-manage.md#assign-a-workspace-to-a-capacity)方法を学習してください。

### <a name="purchase-additional-capacities"></a>追加の容量を購入する

これで容量を購入できたので、ニーズの高まりに合わせてさらに容量を追加できます。 組織内で Premium 容量 SKU の任意の組み合わせ (P1 から P3) を使用できます。 異なる SKU は異なるリソース機能を提供します。

1. Microsoft 365 管理センターで、 **[課金]**  >  **[サービスを購入する]** の順に選択します。

1. **[その他のプラン]** で、追加購入する Power BI Premium の項目を探します。

1. **その他のオプション** (...) にポインターを合わせ、 **[ライセンス数の変更]** を選択します。

    ![ライセンス数の変更](media/service-admin-premium-purchase/premium-purchase-more.png)

1. この項目に必要なインスタンス数を変更します。 完了したら **[送信]** を選択します。

   > [!IMPORTANT]
   > **[送信]** を選択すると、登録されているクレジット カードに課金されます。

**[サービスを購入する]** ページに、所有しているインスタンス数が表示されます。 Power BI 管理ポータルの **[容量の設定]** で、購入した新しい容量が利用可能な仮想コア数に反映されます。

![Power BI Premium 容量の利用可能な仮想コア数](media/service-admin-premium-purchase/premium-capacities.png)

### <a name="cancel-your-subscription"></a>サブスクリプションをキャンセルする

Microsoft 365 管理センターから、ご自分のサブスクリプションをキャンセルすることができます。 Premium サブスクリプションをキャンセルするには、次の操作を行います。

1. Microsoft 365 管理センターを参照します。

1. **[請求]**  >  **[サブスクリプション]** の順に選択します。

1. 一覧から Power BI Premium サブスクリプションを選択します。

1. **[More actions]\(その他の操作\)**  >  **[サブスクリプションのキャンセル]** の順に選択します。

1. **[サブスクリプションのキャンセル]** ページに [中途解約料](https://support.office.com/article/early-termination-fees-6487d4de-401a-466f-8bc3-c0beb5cc40d3) を支払う必要があるかどうかが表示されます。 このページでは、サブスクリプションのデータが削除されるタイミングを確認することもできます。

1. 情報に目を通し、続行する場合は、 **[サブスクリプションのキャンセル]** を選択します。

#### <a name="when-canceling-or-your-license-expires"></a>キャンセルした場合、またはライセンスが期限切れになった場合

Premium サブスクリプションをキャンセルした場合、または容量のライセンスが期限切れになった場合でも、その日から 30 日間は、Premium 容量に引き続きアクセスできます。 30 日が経過すると、Premium 容量やその中のワークスペースにアクセスできなくなります。

## <a name="purchase-a-skus-for-testing-and-other-scenarios"></a>テストおよびその他のシナリオ用に A SKU を購入する

また、テストおよびその他のシナリオのために A SKU を購入することもできます。これにより、Premium 容量が時間単位で提供されます。 詳細と手順については、「[テスト用の Power BI Premium を購入する](service-admin-premium-testing.md)」を参照してください。

## <a name="next-steps"></a>次のステップ

[Power BI Premium で容量を構成および管理する](service-admin-premium-manage.md)\
[Power BI の料金ページ](https://powerbi.microsoft.com/pricing/)\
[Power BI Premium 計算ツール](https://powerbi.microsoft.com/calculator/)\
[Power BI Premium のよくあるご質問](service-premium-faq.md)\
[Power BI のエンタープライズ展開の計画に関するホワイト ペーパー](https://aka.ms/pbienterprisedeploy)

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。

Power BI に Power BI Premium Gen2 がプレビュー オファリングとして導入されました。次の改善によって Power BI Premium のエクスペリエンスが向上しています。
* パフォーマンス
* ユーザーごとのライセンス
* より大きなスケール
* メトリックの改善
* 自動スケール
* 管理オーバーヘッドの削減

Power BI Premium Gen2 の詳細については、[Power BI Premium Generation 2 (プレビュー)](service-premium-what-is.md#power-bi-premium-generation-2-preview) に関する記事を参照してください。