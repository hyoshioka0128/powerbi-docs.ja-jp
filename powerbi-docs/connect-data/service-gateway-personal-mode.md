---
title: Power BI で個人用ゲートウェイを使用する
description: オンプレミスのデータに接続するために個人が使用できる、Power BI 用のオンプレミス データ ゲートウェイ (個人用モード) について説明します。
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: how-to
ms.date: 11/09/2020
LocalizationGroup: Gateways
ms.openlocfilehash: 8f69f81d988393e9be2682164933037b2904a396
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410254"
---
# <a name="use-personal-gateways-in-power-bi"></a>Power BI で個人用ゲートウェイを使用する

[!INCLUDE [gateway-rewrite](../includes/gateway-rewrite.md)]

オンプレミス データ ゲートウェイ (個人用モード) は、Power BI でのみ機能するオンプレミス データ ゲートウェイのバージョンです。 個人用ゲートウェイを使用し、自分のコンピューターにゲートウェイをインストールして、オンプレミスのデータにアクセスできます。

> [!NOTE]
> Power BI ユーザーごとに 1 つの個人用モード ゲートウェイのみを実行できます。 同じユーザーに別の個人用モード ゲートウェイをインストールする場合、コンピューターが違っていても、一番新しいインストールが前のインストールに取って代わります。

## <a name="on-premises-data-gateway-vs-on-premises-data-gateway-personal-mode"></a>オンプレミス データ ゲートウェイとオンプレミス データ ゲートウェイ (個人用モード)

次の表では、オンプレミス データ ゲートウェイとオンプレミス データ ゲートウェイ (個人用モード) の違いについて説明します。

|   |オンプレミス データ ゲートウェイ | オンプレミス データ ゲートウェイ (個人用モード) |
| ---- | ---- | ---- |
|**サポートされているクラウド サービス** |Power BI、PowerApps、Azure Logic Apps、Power Automate、Azure Analysis Services、データフロー |Power BI |
|**計** |ゲートウェイへのアクセス権を持つユーザーによる構成に応じて |Windows 認証の場合はゲートウェイのユーザーとして、他の認証の種類の場合はゲートウェイのユーザーによる構成に応じて |
|**コンピューター管理者としてのみインストールできる** |はい |いいえ |
|**ゲートウェイとデータ ソースの一元管理** |はい |いいえ |
|**データをインポートして更新をスケジュールする** |はい |はい |
|**DirectQuery のサポート** |はい |いいえ |
|**Analysis Services に対する LiveConnect のサポート** |はい |いいえ |

## <a name="install-the-on-premises-data-gateway-personal-mode"></a>オンプレミス データ ゲートウェイ (個人用モード) をインストールする

オンプレミス データ ゲートウェイ (個人用モード) をインストールするには:

1. [オンプレミス データ ゲートウェイをダウンロードします](https://go.microsoft.com/fwlink/?LinkId=820925&clcid=0x409)。

2. インストーラーで [オンプレミス データ ゲートウェイ (個人用モード)] を選択し、 **[次へ]** を選択します。

   ![オンプレミス データ ゲートウェイ (個人用モード) を選択する](media/service-gateway-personal-mode/personal-gateway-select.png)

ゲートウェイ ファイルは、 _"%localappdata%\Microsoft\On-premises data gateway (personal mode)_ にインストールされます。 インストールが正常に完了し、サインインすると、次の画面が表示されます。

![成功したオンプレミス データ ゲートウェイ (個人用モード)](media/service-gateway-personal-mode/personal-gateway-complete.png)

## <a name="use-fast-combine-with-the-personal-gateway"></a>個人ゲートウェイで高速結合を使用する

個人用ゲートウェイで高速結合を使用すると、指定されたプライバシー レベルをクエリの実行中に無視できます。 オンプレミス データ ゲートウェイ (個人用モード) で動作するように高速結合を有効にするには:

1. エクスプローラーを利用し、次のファイルを開きます。

   `%localappdata%\Microsoft\On-premises data gateway (personal mode)\Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config`

2. ファイルの下部に次のテキストを追加します。

    ```xml
    <setting name="EnableFastCombine" serializeAs="String">
       <value>true</value>
    </setting>
    ```

3. 完了すると、約 1 分で設定が有効になります。 正常に動作していることを確認するには、Power BI サービスでオンデマンド更新を試み、高速結合が動作していることを確認します。

## <a name="frequently-asked-questions-faq"></a>よく寄せられる質問 (FAQ)

**質問:** オンプレミス データ ゲートウェイ (個人用モード) とオンプレミス データ ゲートウェイ (以前、Enterprise バージョンと呼ばれていたもの) は並列実行できますか。
  
**回答:** はい、両方のゲートウェイを同時に実行できます。

**質問:** オンプレミス データ ゲートウェイ (個人用モード) はサービスとして実行できますか。
  
**回答:** いいえ。 オンプレミス データ ゲートウェイ (個人用モード) はアプリケーションとしてのみ実行できます。 ゲートウェイをサービスとして実行する必要がある場合、あるいは管理者モードで実行する必要がある場合、[オンプレミス データ ゲートウェイ](/data-integration/gateway/service-gateway-onprem) (以前、Enterprise ゲートウェイと呼ばれていたもの) を検討する必要があります。

**質問:** オンプレミス データ ゲートウェイ (個人用モード) はどのくらいの頻度で更新されますか。
  
**回答:** 個人ゲートウェイは毎月更新する予定です。

**質問:** 資格情報の更新を求められるのはなぜですか。
  
**回答:** さまざまな状況で資格情報が要求されます。 最も一般的な状況は、Power BI - Personal ゲートウェイとは異なるコンピューターにオンプレミス データ ゲートウェイ (個人用モード) を再インストールした場合です。 データ ソースに問題がある、Power BI でテスト接続を実行でなかった、タイムアウトが発生した、システム エラーが発生したなども考えられます。 Power BI サービスで資格情報を更新するには、歯車アイコンを選択し、 **[設定]**  >  **[データセット]** を選択します。 問題のデータセットを見つけて、 **[データ ソースの資格情報]** を選択します。

**質問:** アップグレードの間、以前の個人ゲートウェイはどのくらいの間オフラインになりますか。
  
**回答:** 個人ゲートウェイの最新版への更新は数分で完了します。

**質問:** R と Python のスクリプトを使用しています。 これらはサポートされていますか。
  
**回答:** R と Python のスクリプトは、個人用モードでサポートされています。

## <a name="next-steps"></a>次の手順

* [ゲートウェイのデータ ソースの追加または削除](service-gateway-data-sources.md)
* [オンプレミス データ ゲートウェイのプロキシ設定を構成する](/data-integration/gateway/service-gateway-proxy)  

他にわからないことがある場合は、 [Power BI コミュニティ](https://community.powerbi.com/)を利用してください。
