---
title: Power BI モバイル アプリで使用するレポートの QR コードを作成する
description: Power BI で QR コードを使用すると、実世界の任意のものを、Power BI モバイル アプリの関連する BI 情報に直接接続することができます。検索の必要はありません。
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 03/13/2018
LocalizationGroup: Reports
ms.openlocfilehash: 6322876bec350ca3d7c3fde4586387d640423f07
ms.sourcegitcommit: 1cad78595cca1175b82c04458803764ac36e5e37
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2021
ms.locfileid: "98565517"
---
# <a name="create-a-qr-code-for-a-report-in-power-bi-to-use-in-the-mobile-apps"></a>モバイル アプリで使用する Power BI のレポートの QR コードを作成する
Power BI で QR コードを使用すると、実世界の任意のものを、関連する BI 情報に直接接続することができます。ナビゲーションや検索の必要がなくなります。

Power BI サービスでは、編集できないレポートの場合でも、すべてのレポートについて QR コードを作成できます。 その後、必要な場所にその QR コードを配置します。 たとえば、メールに貼り付けたり、印刷して特定の場所に貼り付けたりできます。 

レポートを共有している仕事仲間は、レポートにアクセスするため QR コードを[モバイル デバイス](../consumer/mobile/mobile-apps-qr-code.md)から直接スキャンできます。 Power BI アプリに付属の QR コード スキャナーを使用しても、それらのデバイスにインストールされているその他の QR スキャナーを使用しても構いません。 [Power BI for Mixed Reality アプリでレポートの QR コードをスキャンする](../consumer/mobile/mobile-hololens2-app.md#open-reports-with-qr-codes)こともできます。

## <a name="create-a-qr-code-for-a-report"></a>レポートの QR コードを作成する
1. Power BI サービスで、レポートを開きます。
2. 右上隅にある **その他のオプション** (...) を選び、 **[QR コードの生成]** を選びます。 
   
    ![レポートのスクリーンショット。[...] から出たポインターが [QR コードの生成] を指しています。](media/service-create-qr-code-for-report/power-bi-create-qr-code-report.png)
3. QR コードを含むダイアログ ボックスが表示されます。 
   
    ![ダイアログのスクリーンショット。QR コードをダウンロードまたは保存する準備ができています。](media/service-create-qr-code-for-report/powerbi_report_qrcode.png)
4. この画面から QR コードをスキャンするか、ダウンロードして保存すると、次のことを行えます。 
   
   * メールやその他のドキュメントに QR コードを追加する。 
   * QR コードを印刷して、特定の場所に配置する。 

## <a name="print-the-qr-code"></a>QR コードを印刷する
Power BI は QR コードを JPG ファイルとして生成するので、印刷に対応できます。 

1. **[ダウンロード]** を選択し、プリンターに接続されているコンピューターで JPG ファイルを開きます。  
   
   JPG ファイルの名前はタイルと同じです。 例: 売上およびマーケティングのサンプル.jpg。
   
1. ファイルを 100% または「実際のサイズ (原寸大)」で印刷します。  
2. 縁に沿って QR コードを切り取り、そのレポートに関連する場所に貼り付けます。 

## <a name="next-steps"></a>次の手順
* [モバイル アプリで現実世界から Power BI データに接続する](../consumer/mobile/mobile-apps-data-in-real-world-context.md)
* [モバイル デバイスから Power BI QR コードをスキャンする](../consumer/mobile/mobile-apps-qr-code.md)
* [タイルの QR コードを作成する](service-create-qr-code-for-tile.md)
* わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
