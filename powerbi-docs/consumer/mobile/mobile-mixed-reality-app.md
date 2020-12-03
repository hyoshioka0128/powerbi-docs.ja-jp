---
title: HoloLens の Power BI (第 1 世代)
description: 仮想世界に専念した状態で、または使用環境のコンテキストで、Power BI for Mixed Reality アプリ (プレビュー) でダッシュボードとレポートを表示します。
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 09/22/2020
ms.openlocfilehash: c832217363f726e3eff469238fe9b3f29025837c
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415360"
---
# <a name="power-bi-for-hololens-1st-gen"></a>HoloLens の Power BI (第 1 世代)
仮想世界に専念した状態で Power BI for HoloLens アプリでダッシュボードとレポートを表示するか、使用環境のコンテキストで特定の場所にダッシュボードとレポートを配置します。 

Windows ストアから [Power BI for Mixed Reality アプリをダウンロード](https://www.microsoft.com/p/power-bi-mobile/9nblgggzlxn1?activetab=pivot%3aoverviewtab)します: Windows ストアでは "Power BI Mobile" と呼ばれています。 仮想世界のダッシュボードとレポートで対話してから、配置するものを選択します。 

## <a name="two-views-windows-classic-and-holographic"></a>2 つのビュー: Windows クラシックとホログラフィック

Power BI for Mixed Reality は、複合現実に固有の機能が追加された Power BI Windows モバイル アプリに基づいています。 Power BI for Mixed Reality を起動すると、Power BI の "クラシック" Windows ビューが開きます。 このビューでは、アクセス権があるダッシュボードとレポート間を移動することができます。 必要なものを検索する際に、クラシック Windows ビューからホログラフィック操作に切り替えることができます。 


## <a name="windows-classic-view-basics"></a>Windows クラシック ビューの基本

複合現実での操作が初めての場合は、このセクションが役立ちます。 複合現実アプリとの対話は、コンピューター、タブレット、携帯電話との対話とは異なります。 Windows クラシック ビューでは、複合現実アプリは、従来のマウスとキーボード、または携帯電話のタップに代わる一連のジェスチャと音声コマンドに応答します。 

**エア タップ**

エア タップは、ほとんどすべての複合現実アプリと対話する場合に知っておく必要がある、最も基本的なジェスチャです。 マウス クリックや携帯電話のタップの場合と同じように、手を垂直にした状態で親指と人差し指で同時にタップします。  

![複合現実のエア タップのジェスチャ](./media/mobile-mixed-reality-app/power-bi-hololens-airtap.png)

Power BI の Windows クラシック アプリでは、マウス クリックを使用するあらゆる場所でエア タップできます。 エア タップして、ワークスペースでダッシュボードやレポートを開くことができます。また、ビジュアルの一部をエア タップして、他のビジュアルをフィルター処理したり、クロス強調表示したりすることができます。

![Power BI でのエア タップ](./media/mobile-mixed-reality-app/power-bi-hololens-airtap-hand.png) 

詳細については、[複合現実における Microsoft の手のジェスチャ](https://developer.microsoft.com/windows/mixed-reality/gestures)に関するページを参照してください。

**項目をピン留めする** 

Windows クラシック ビューからホログラフィック ビューにダッシュボードまたはレポートをピン留めするには、**ピン** アイコン ![ピン アイコン](./media/mobile-mixed-reality-app/power-bi-hololens-pin.png) をエア タップします。 ホログラフィック ビューには複数の項目をピン留めすることができます。 

**ホログラフィック ビューに切り替える**

Windows クラシック ビューで項目をピン留めしたら、**全画面表示** アイコン ![全画面表示アイコン](./media/mobile-mixed-reality-app/power-bi-hololens-fullscreen.png) をエア タップして、ホログラフィック ビューに切り替えます。 


## <a name="holographic-view-basics"></a>ホログラフィック ビューの基本

この時点で、ホログラフィック ビューが表示されており、ピン留めした成果物はすべてドッキング ベルトにあります。 物理領域の特定の場所にこれらのピン留めした項目を配置することができます。たとえば、項目が示す機器の部分の横に配置できます。 ホログラフィック ビューの場合、音声コマンドで手のジェスチャを補完します。 一般的な音声コマンドをいくつか以下に示します。

**"フォロー"** 

Power BI の成果物を選択します。これにより、主な視界が保たれ、任意の場所に配置するまで、視線の先を追うことができます。

**"ドッキング"** 

"ドッキング" コマンドを使用して、Power BI ドッキング ベルトに成果物を配置します。これにより、主な視界の外でもフォローして簡単にアクセスすることができます。

**"ここに配置"**

このコマンドにより、壁やオブジェクト、または空間にダッシュボードまたはレポートが配置されます。

![空間でのダッシュボードの配置](./media/mobile-mixed-reality-app/power-bi-hololens-place-visuals.png)

**"ホームに戻る"**

Power BI のクラシック Windows ビューに戻る場合は、"ホームに戻る" と言います。 

**"削除"**

ホログラフィック ビューから成果物を削除する場合は、このコマンドを使用します。

**"すべて削除"** 

ホログラフィック ビューから成果物をすべて削除する場合は、このコマンドを使用します。


## <a name="scan-a-report-qr-code-in-holographic-view"></a>ホログラフィック ビューでレポートの QR コードをスキャンする

iPhone や Android の [Power BI モバイル アプリで QR コードをスキャンする](mobile-apps-qr-code.md)場合と同じように、ホログラフィック ビューでレポートの QR コードをスキャンすることができます。

- ホログラフィック ビューを開いた状態で、QR コードを見つめます。 Power BI で、その QR コードに関連付けられているレポートが開きます。

## <a name="limitations-and-considerations"></a>制限事項と考慮事項

ここでは、ホログラフィック ビューに関するいくつかの制限事項と考慮事項を示します。

- Windows クラシック ビューで設定した可能性のある、クロス フィルター処理や強調表示は表示されません。
- ピン留めしたダッシュボードとレポートのビューはプライベート ビューです。 現在、共有エクスペリエンスはサポートされていません。
- ダッシュボードとレポートは、データの変更に応じて 45 秒ごとに更新されます。


## <a name="next-steps"></a>次のステップ

- [Power BI モバイル アプリで現実世界からデータを取得する](mobile-apps-data-in-real-world-context.md)

 



