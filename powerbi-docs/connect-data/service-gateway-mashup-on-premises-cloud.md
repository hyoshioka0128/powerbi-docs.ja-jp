---
title: オンプレミスとクラウド データ ソースのマージまたはアペンド
description: オンプレミス データ ゲートウェイを使用し、オンプレミスとクラウドのデータ ソースを同じクエリでマージまたはアペンドします。
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: how-to
ms.date: 07/15/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 4da44d0915b981c22b0c334fb5586b97c3b01ea2
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96402388"
---
# <a name="merge-or-append-on-premises-and-cloud-data-sources"></a>オンプレミスとクラウド データ ソースのマージまたはアペンド

[!INCLUDE [gateway-rewrite](../includes/gateway-rewrite.md)]

オンプレミス データ ゲートウェイを使用し、オンプレミスとクラウドのデータ ソースを同じクエリでマージまたはアペンドすることができます。 このソリューションは、個別のクエリを使用せず、複数のソースからデータを結合するときに便利です。

>[!NOTE]
>この記事は、クラウドとオンプレミスのデータ ソースが 1 つのクエリにマージまたはアペンドされているデータセットにのみ適用されます。 個別のクエリを含む (1 つはオンプレミス データソースに接続し、もう一方はクラウド データ ソースに接続する) データセットの場合、ゲートウェイではクラウド データ ソースのクエリが実行されません。

## <a name="prerequisites"></a>前提条件

- ローカル コンピューターに[ゲートウェイがインストールされている](/data-integration/gateway/service-gateway-install)こと。
- オンプレミスとクラウドのデータ ソースを結合するクエリを含む Power BI Desktop ファイル。

>[!NOTE]
>クラウド データ ソースにアクセスするには、確実にゲートウェイがそれらのデータ ソースにアクセスできるようにする必要があります。

1. Power BI サービスの右上にある歯車アイコン ![[設定] 歯車アイコン](media/service-gateway-mashup-on-premises-cloud/icon-gear.png) >  **[ゲートウェイの管理]** の順に選択します。

    ![ゲートウェイを管理する](media/service-gateway-mashup-on-premises-cloud/manage-gateways.png)

2. 構成するゲートウェイを選択します。

3. **[ゲートウェイ クラスターの設定]** で **[Allow user's cloud data sources to refresh through this gateway cluster]\(このゲートウェイ クラスターでユーザーのクラウド データ ソースを更新することを許可します\)**  >  **[適用]** の順に選択します。

    ![このゲートウェイ クラスターで更新する](media/service-gateway-mashup-on-premises-cloud/refresh-gateway-cluster.png)

4. このゲートウェイ クラスターの下で、クエリで使用される[オンプレミス データ ソース](service-gateway-enterprise-manage-scheduled-refresh.md#add-a-data-source)があれば、それを追加します。 ここではクラウド データ ソースを追加する必要がありません。

5. オンプレミスとクラウドのデータ ソースを結合するクエリを含む Power BI Desktop ファイルを Power BI サービスにアップロードします。

6. 新しいデータセットの **[データセットの設定]** ページで:

   - オンプレミス ソースの場合、このデータ ソースに関連付けられているゲートウェイを選択します。
   - **[データ ソースの資格情報]** で、必要に応じて、クラウド データ ソースの資格情報を編集します。

    クラウドとオンプレミスの両方のデータ ソースのプライバシー レベルが適切に設定されていることを確認し、結合が安全に処理されるように確保してください。

     ![データセットの設定](media/service-gateway-mashup-on-premises-cloud/dataset-settings.png)

7. クラウドの資格情報が設定されたので、 **[今すぐ更新]** オプションを利用してデータセットを更新できるようになりました。 または、定期的に更新するようにスケジュールを設定できます。

## <a name="next-steps"></a>次のステップ

ゲートウェイのデータ更新の詳細については、「[スケジュールされた更新でデータ ソースを使用する](service-gateway-enterprise-manage-scheduled-refresh.md#use-the-data-source-for-scheduled-refresh)」を参照してください。
