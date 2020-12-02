---
title: Power BI Desktop で OneDrive for Business リンクを使用する
description: Power BI Desktop で OneDrive for Business リンクを使用する
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 05/27/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 70607632dd4e93d1b0d5e53f19ef697c6599128d
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410852"
---
# <a name="use-onedrive-for-business-links-in-power-bi-desktop"></a>Power BI Desktop で OneDrive for Business リンクを使用する
多くの人は、Power BI Desktop と相性の良い OneDrive for Business に Excel ブックを格納しています。 Power BI Desktop を使用すると、OneDrive for Business に格納されている Excel ファイルのオンライン リンクを使用して、レポートやビジュアルを作成できます。 OneDrive for Business のグループ アカウントか、個人の OneDrive for Business アカウントを使用できます。

OneDrive for Business からオンライン リンクを取得するには、いくつかの特定の手順が必要です。 次のセクションでは、それらの手順について説明します。グループ間、様々なコンピューター、同僚とファイル リンクを共有できるようになります。

## <a name="get-a-link-from-excel"></a>Excel からリンクを取得する
1. ブラウザーを使用して OneDrive for Business の場所に移動します。 使用するファイルを右クリックし、 **[Excel で開く]** を選びます。
   
   > [!NOTE]
   > ブラウザーのインターフェイスは、次の画像のとおりではない場合もあります。 OneDrive for Business ブラウザー インターフェイスで、ファイルに対して **[Excel で開く]** を選択する方法はたくさんあります。 Excel でファイルを開くためのどのオプションでも使用することができます。
   
   ![[Excel で開く] の選択を示す、ブラウザーの OneDrive のスクリーンショット。](media/desktop-use-onedrive-business-links/odb-links_02.png)

2. Excel で、次の図に示すように、 **[ファイル]**  >  **[情報]** の順に選択し、 **[パスのコピー]** ボタンを選びます。
   
   ![[パスのコピー] ボタンの選択を示す、[情報] メニューのスクリーンショット。](media/desktop-use-onedrive-business-links/onedrive-copy-path.png)

## <a name="use-the-link-in-power-bi-desktop"></a>Power BI Desktop でリンクを使用する
直前にクリップボードにコピーしたリンクを Power BI Desktop で使用できます。 次の手順を実行します。

1. Power BI Desktop で、 **[データの取得]**  >  **[Web]** を選択します。
   
   ![[Web] の選択を示す、Power BI Desktop の [データの取得] リボンのスクリーンショット。](media/desktop-use-onedrive-business-links/power-bi-web-link-onedrive.png)
2. **[Basic]** オプションを選択した状態で、リンクを **[Web から]** ダイアログ ボックスに貼り付けます。
3. Power BI Desktop でファイルに適切に移動できるように、リンクの末尾にある *?web=1* という文字列を削除し、 **[OK]** を選択します。
   
    ![[URL] フィールドからの文字列の削除方法を示す、[Web から] ダイアログのスクリーンショット。](media/desktop-use-onedrive-business-links/power-bi-web-link-confirmation.png) 
4. Power BI Desktop で資格情報の入力を求められた場合は、 **[Windows]** (オンプレミスの SharePoint サイトの場合) または **[組織アカウント]** (Microsoft 365 または OneDrive for Business のサイトの場合) のいずれかを選択します。
   
   ![[Windows] または [組織アカウント] の選択を示す、Power BI Desktop の資格情報プロンプトのスクリーンショット。](media/desktop-use-onedrive-business-links/odb-links_06.png)

   **[ナビゲーター]** ダイアログ ボックスが表示され、Excel ブックにあるテーブル、シート、範囲を一覧から選ぶことができます。 そこから、他の Excel ファイルと同様に OneDrive for Business ファイルを使用できます。 他のデータ ソースと同様に、レポートを作成してデータセットで使用できます。

> [!NOTE]
> Power BI サービスのデータ ソースとして OneDrive for Business ファイルを使うには、そのファイルに対して **[Service Refresh]\(サービスの更新\)** を有効にし、更新の設定を構成するときに **[認証方法]** として **[OAuth2]** を選択します。 このようにしないと、接続または更新しようとしたときに、エラー ("*データ ソースの資格情報の更新に失敗しました*" など) が発生する可能性があります。 認証方法として **OAuth2** を選ぶと、資格情報エラーは発生しません。
>
