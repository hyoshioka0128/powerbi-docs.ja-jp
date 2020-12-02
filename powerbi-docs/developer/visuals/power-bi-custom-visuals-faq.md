---
title: Power BI ビジュアルに関してよく寄せられる質問
description: Power BI ビジュアルについてよく寄せられる質問とその回答の一覧です
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.custom: ''
ms.date: 09/30/2020
ms.openlocfilehash: f38aaf9ea5bcb62cabae6ce2b7aca99f97c75960
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96386437"
---
# <a name="power-bi-visuals-faq"></a>Power BI ビジュアルに関する FAQ

## <a name="organizational-power-bi-visuals"></a>組織の Power BI ビジュアル

管理ポータルを使用すると、組織の Power BI ビジュアルを管理できます。

### <a name="how-can-the-admin-manage-organizational-power-bi-visuals"></a>管理者が組織の Power BI ビジュアルを管理するにはどうすればよいですか?

管理ポータルの *[組織のビジュアル]* タブから、管理者は [企業内のすべての組織の Power BI ビジュアルを管理](../../admin/organizational-visuals.md#organizational-visuals)および確認できます。 たとえば、Power BI ビジュアルの追加、無効化、有効化、削除などです。

組織内のユーザーは、Power BI Desktop またはサービスから Power BI ビジュアルを簡単に見つけて直接レポートにインポートすることができます。

管理者が新しいバージョンの組織の Power BI ビジュアルをアップロードすると、組織内のすべてのユーザーが同じ更新されたバージョンを取得できます。 更新された Power BI ビジュアルを使用するすべてのレポートは自動的に更新されます。

ユーザーは、組み込みの Power BI Desktop と Power BI サービス組織ストアの *[自分の所属組織]* タブで組織の Power BI ビジュアルを見つけることができます。 

### <a name="if-an-admin-uploads-a-power-bi-visual-from-the-public-marketplace-to-the-organization-store-using-add-visual--from-appsource-is-it-automatically-updated-once-a-vendor-updates-the-visual-in-the-public-marketplace"></a>管理者が *[視覚化の追加] > [AppSource から]* を使用してパブリック マーケットプレースから組織のストアに Power BI 視覚エフェクトをアップロードする場合、ベンダーがパブリック マーケットプレースの視覚エフェクトを更新したらそれは自動的に更新されますか?

はい、視覚化はパブリック マーケットプレースから自動的に更新されます。 視覚化が認定されている場合、PDF または PowerPoint へのエクスポートなどの追加機能を含め、認定が保持されます。

### <a name="is-there-a-way-to-disable-the-organization-store"></a>組織のストアを無効にする方法はありますか?

いいえ。Power BI Desktop と Power BI サービスには *[自分の所属組織]* タブが常に表示されます。 管理者が管理ポータルから組織の Power BI ビジュアルをすべて無効にした場合、または削除した場合、組織のストアは空になります。
  
### <a name="if-the-admin-disables-power-bi-visuals-from-the-admin-portal-tenant-settings-do-users-still-have-access-to-the-organizational-power-bi-visuals"></a>管理者が管理ポータルから Power BI ビジュアルを無効にした場合 (テナント設定)、ユーザーは引き続き組織の Power BI ビジュアルにアクセスできますか?

はい、管理者が管理ポータルから Power BI ビジュアルを無効にしても、組織のストアには影響しません。

一部の組織は、Power BI ビジュアルを無効にし、Power BI 管理者によって組織のストアにインポートおよびアップロードされた、手動で選択されたビジュアルのみを有効にする場合があります。

管理ポータルから Power BI ビジュアルを無効にしても、Power BI Desktop では適用されません。 デスクトップのユーザーは、引き続きパブリック マーケットプレースから Power BI ビジュアルを追加し、自分のレポートで使用することができます。 ただし、それらのパブリックな Power BI ビジュアルは、Power BI サービスに公開されるとレンダリングされなくなり、該当するエラーが発行されます。 

管理ポータルで Power BI ビジュアル設定が適用されている場合、Power BI サービスのユーザーはパブリック マーケットプレースから Power BI ビジュアルをインポートできません。 組織ストアのビジュアルのみをインポートできます。

### <a name="what-are-the-advantages-of-power-bi-visuals-in-the-organizational-store"></a>組織ストアの Power BI ビジュアルの利点は何ですか?

* すべてのユーザーが、Power BI 管理者によって制御される同じバージョンのビジュアルを取得できます。管理者が管理ポータルでビジュアルのバージョンを更新すると、組織内のすべてのユーザーが更新されたバージョンを自動的に取得できます。

* ビジュアルのファイルを電子メールや共有フォルダーで共有する必要はありません。 組織ストアのオファーは、ログインしているすべてのメンバーに表示されます。

* セキュリティとサポート性、新しいバージョンの組織の Power BI ビジュアルは、すべてのレポートで自動的に更新されます。

* 管理者は、組織全体で使用できる Power BI ビジュアルを制御できます。

* 管理者は、テスト用のビジュアルを管理ポータルから有効または無効にできます。

## <a name="certified-power-bi-visuals"></a>認定済み Power BI ビジュアル

### <a name="what-are-certified-power-bi-visuals"></a>認定済み Power BI ビジュアルとは何ですか?

認定済み Power BI ビジュアルは、特定の[要件](power-bi-custom-visuals-certified.md)を満たし、Microsoft によって認定されている Power BI ビジュアルです。

[マーケットプレース](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals)では、認定済み Power BI ビジュアルに認定済みであることを示す黄色いバッジが表示されます。

Microsoft は、サードパーティの Power BI ビジュアルの作成者ではありません。 サードパーティのビジュアルの機能については、作成者に直接お問い合わせいただくことをお客様にお勧めしています。

### <a name="what-tests-are-done-during-the-certification-process"></a>認定プロセス中はどのようなテストが行われますか? 

認定プロセスのテストには、次のようなものがあります (ただし、これらに限定されません)。 
* コード レビュー
* スタティック コード分析
* データ漏えい
* データのファジー化
* 侵入テスト
* アクセス XSS テスト
* 悪意のあるデータ挿入
* 入力の検証
* 機能テスト
 
### <a name="are-certified-power-bi-visual-checked-again-with-every-new-submission-upgrade"></a>認定済み Power BI ビジュアルは新しい送信 (アップグレード) ごとにチェックを受けますか?

はい。 認定済みビジュアルの新しいバージョンが Marketplace に送信されるたびに、ビジュアルのバージョン更新プログラムは、同じ認定チェックを受けます。

バージョン更新プログラムの認定は自動的に更新されます。 更新プログラムが拒否される違反が見つかった場合、必要な修正内容が記載されたメールが開発者に送信されます。

### <a name="can-a-certified-power-bi-visual-stop-lose-its-certification-after-a-new-update"></a>更新プログラムのリリース後に認定済み Power BI ビジュアルに対して行われる認定を省略することはできますか?

いいえ、それはできません。 更新プログラムのリリース後に認定済みビジュアルに対して行われる認定を省略することはできません。 更新プログラムは拒否されます。
 
### <a name="do-i-need-to-share-my-code-in-a-public-repository-if-im-certifying-my-power-bi-visual"></a>自作の Power BI ビジュアルを自分で認定している場合、パブリック リポジトリでコードを共有する必要がありますか?

いいえ、ご自分のコードをパブリックに共有する必要はありません。

Power BI ビジュアルのコードを確認できるように読み取りアクセス許可を付与してください。 たとえば、GitHub でプライベート リポジトリを使用します。
 
### <a name="does-a-certified-power-bi-visual-have-to-be-in-the-marketplace"></a>認定済み Power BI ビジュアルはマーケットプレースに公開する必要がありますか?

はい。 プライベート ビジュアルは認定されません。
 
### <a name="how-long-does-it-take-to-certify-my-visual"></a>ビジュアルの認定にはどれくらいの時間がかかりますか? 

新しい Power BI ビジュアル (初回認証) の認定には、最長で 4 週間かかることがあります。 

更新されたバージョンの Power BI ビジュアルを認定するには、最長で 3 週間かかることがあります。 

### <a name="does-the-certification-process-ensure-that-there-is-no-data-leakage"></a>認定プロセスでは、データ漏えいが発生しないことが保証されていますか?

実行されたテストは、ビジュアルが外部のサービスやリソースにアクセスしないことを確認するように作られています。 

Microsoft は、サードパーティの Power BI ビジュアルの作成者ではありません。 サードパーティの Power BI ビジュアルの機能については、作成者に直接お問い合わせいただくことをお客様にお勧めしています。
 
### <a name="are-uncertified-power-bi-visuals-safe-to-use"></a>未認定 Power BI ビジュアルは使用しても安全ですか?

未認定 Power BI ビジュアルは、安全ではないビジュアルを意味するわけではありません。

一部のビジュアルは 1 つまたは複数の[認定要件](power-bi-custom-visuals-certified.md#certification-requirements)を満たしていないために認定されていません。 たとえば、地図ビジュアルのような外部サービスや商用ライブラリを利用するビジュアルに接続する場合です。
 
## <a name="visuals-with-additional-purchases"></a>ビジュアルの追加購入

### <a name="what-is-a-visual-with-additional-purchases"></a>ビジュアルの追加購入とは何ですか?

ビジュアルの追加購入は、アプリ内購入 (IAP) アドインに似ています。 このようなアドインには、 **[追加購入が必要になる場合があります]** という値札が付けられています。

IAP Power BI ビジュアルは無料のダウンロード可能な Power BI ビジュアルです。 マーケットプレースからこれらの Power BI ビジュアルをダウンロードするために料金はかかりません。

高度な機能をアプリ内でオプション購入することもできます。  

### <a name="what-is-changing-in-the-submission-process"></a>送信プロセスの変更点は何ですか?

IAP Power BI ビジュアルをマーケットプレースに送信するプロセスは無料の Power BI ビジュアルの場合と同じプロセスです。 認定を受ける Power BI ビジュアルの送信には、[パートナー センター](/partner-center/)を使用します。


Power BI ビジュアルを登録するときは、 *[Product setup]\(製品の設定\)* タブに移動し、 *[My product requires the purchase of a service]\(この製品にはサービスの購入が必要です\)* チェック ボックスをオンにします。

### <a name="what-should-i-do-beforesubmittingmy-iap-power-bi-visual"></a>IAP Power BI ビジュアルを提出する前に何をすればよいですか?

IAP Power BI ビジュアルを作成している場合は、[ガイドライン](guidelines-powerbi-visuals.md)に準拠していることを確認してください。  

> [!NOTE]
> IAP 機能が追加された無料の Power BI ビジュアルの場合、以前に提出したものと同じ無料機能を保持する必要があります。 古い無料機能の上に、オプションの高度な有料機能が追加されることがあります。 IAP Power BI ビジュアルは、古い無料のものを更新するのではなく、高度な機能を備える新しい Power BI ビジュアルとして提出することをお勧めします。

### <a name="do-iap-power-bi-visuals-need-to-be-certified"></a>IAP Power BI ビジュアルは認定を受ける必要がありますか?

[認定](power-bi-custom-visuals-certified.md)プロセスは任意です。 IAP Power BI ビジュアルの認定を受けるかどうかは、開発者が任意に判断できます。

### <a name="can-i-get-my-iap-power-bi-visual-certified"></a>自作の IAP Power BI ビジュアルは認定を受けられますか?

はい。AppSource チームによって IAP Power BI ビジュアルが承認されると、ご自分の Power BI ビジュアルを提出して[認定](power-bi-custom-visuals-certified.md)を受けることができます。

認定は任意のプロセスです。IAP ビジュアルの認定を受けるかどうかは、ご自身で判断してください。

## <a name="additional-questions"></a>その他の質問

### <a name="how-to-get-support"></a>サポートを受ける方法は?

ご質問、ご意見、問題がございましたら、Power BI ビジュアルのサポート チームまでお気軽にお問い合わせください。アドレスは pbicvsupport@microsoft.com です。  

## <a name="next-steps"></a>次の手順

詳細については、[Power BI ビジュアルのトラブルシューティング](power-bi-custom-visuals-troubleshoot.md)に関する記事を参照してください。