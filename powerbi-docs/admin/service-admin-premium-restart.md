---
title: Power BI Premium 容量を再起動する
description: Power BI Premium 容量を再起動し、パフォーマンスの問題に対処する方法を学習します。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-premium
ms.topic: how-to
ms.date: 04/02/2021
LocalizationGroup: Premium
ms.openlocfilehash: 0bde228e6cc366fba857106066e461c2b53b312a
ms.sourcegitcommit: a3b1ccdd18ef705de960625a9715ad5bbc21b1b6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2021
ms.locfileid: "106226739"
---
# <a name="restart-a-power-bi-premium-capacity"></a>Power BI Premium 容量を再起動する

Power BI 管理者であれば、Premium 容量の再起動が必要になることがあります。 この記事では容量の再起動方法について説明し、再起動とパフォーマンスに関するいくつかの問題を取り扱います。

## <a name="why-does-power-bi-provide-this-option"></a>Power BI でこのオプションが提供される理由

Power BI では、大量のデータに対して複雑な分析を実行できます。 残念ながら、Power BI サービスにジョブが過剰に与えられる、過度に複雑なクエリを記述する、循環する参照を作成するなどの理由でパフォーマンス問題が発生することがあります。

Power BI の共有容量の場合、保護機能として、ファイル サイズ、更新スケジュール、サービスのその他の側面に上限を課すことでそのような事例に対処します。 Power BI Premium 容量の場合、それとは対照的に、そういった上限の多くが上げられています。 結果として、不適切な DAX 式や非常に複雑なモデルがレポートに含まれると、重大なパフォーマンス問題を引き起こすことがあります。 レポートは処理されるとき、容量で利用できるリソースをすべて利用することがあります。 

Power BI では、Premium 容量の利用者をこのような問題から守る方法が継続的に改善されています。 Microsoft はまた、容量に対する負荷が過剰になるタイミングとその理由を分析するためのツールを管理者に提供しています。 詳細については、トレーニング セッション動画をご覧ください。[短め](https://www.youtube.com/watch?v=UgsjMbhi_Bk&feature=youtu.be)のバージョンと[長め](https://powerbi.tips/2018/07/)のバージョンがあります。 また、重大な問題が発生したときは、それを軽減できることを必要です。 そのような問題を軽減する最も簡単な方法は、容量を再起動することです。

> [!NOTE]
> Power BI Premium に **Premium Gen2** という名前の新しいバージョンの Premium が最近リリースされました。現在はプレビュー段階です。 Preview Gen2 の容量は再起動を必要としないため、この機能は Premium Gen2 では使用できません。
>
> **Embedded Gen2** 容量でも再起動する必要はありません。 Power BI Embedded Gen2 の機能強化を確認するには、[Power BI Embedded Generation 2](../developer/embedded/power-bi-embedded-generation-2.md) に関する記事を参照してください。

> [!NOTE]
> このプロセスと機能は Power BI Premium Per User (PPU) の容量またはアクティビティに適用されません。

## <a name="is-the-restart-process-safe-will-i-lose-any-data"></a>再起動プロセスは安全ですか。 データを失ったりしませんか。

容量に保存されているデータ、定義、レポート、ダッシュボードはすべて、再起動後も前の状態を完全に維持しています。 容量を再起動すると、継続的にスケジュールされている更新とアドホックの更新が、更新エンジンによって一時的に停止されます。ほとんどの場合、これらはその後、Power BI に組み込まれた更新再試行ロジックによって再起動されます。 容量が使用可能になると、サービスは影響を受ける更新の再試行を試みます。 再起動プロセス中、ユーザー インターフェイスで更新の状態が変わることはありません。 

ユーザーが容量を操作していた場合、再起動プロセス中に未保存の作業は失われます。 再起動の完了後、ブラウザーを更新する必要があります。

## <a name="how-do-i-restart-a-capacity"></a>容量を再起動する方法は?

次の手順で容量を再起動します。

1. Power BI 管理ポータルの **[容量の設定]** タブで容量に移動します。 

1. **CapacityRestart** "*機能フラグ*" を容量 URL に追加します: `https://app.powerbi.com/admin-portal/capacities/<YourCapacityId>?capacityRestartButton=true`。

1. **[詳細設定]**  >  の **[容量の再起動]** で **[容量を再起動する]** を選択します。

    ![容量を再起動する](media/service-admin-premium-restart/restart-capacity.png)

1. **[容量の再起動]** ダイアログ ボックスで **[はい、容量を再起動します]** を選択します。

    ![再起動を確定する](media/service-admin-premium-restart/confirm-restart.png)

## <a name="how-can-i-prevent-issues-from-happening-in-the-future"></a>今後、問題の発生を防止する方法はありますか。

問題を回避する最良の方法は、効率的なデータ モデリングをユーザーに教えることです。 詳細については、[トレーニング セッション](https://powerbi.tips/2018/07/)をご覧ください。

また、定期的に[容量を監視](service-admin-premium-monitor-capacity.md)し、根本的な問題を示す傾向を探すことをお勧めします。 Microsoft は、ユーザーが容量を一層効果的に監視し、管理できるよう、監視アプリやその他のツールを定期的にリリースする予定です。

## <a name="next-steps"></a>次のステップ

[Power BI Premium とは何ですか?](service-premium-what-is.md)

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
