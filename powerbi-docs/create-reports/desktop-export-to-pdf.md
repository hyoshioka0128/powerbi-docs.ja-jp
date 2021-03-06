---
title: Power BI Desktop からレポートを PDF 形式にエクスポートする
description: Power BI Desktop から PDF へのエクスポートおよび、それらの PDF レポートの印刷を簡単に行える
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/28/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 5f2412ec7aa548feecc3a6ceb6a2c90036d1623a
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2020
ms.locfileid: "83348323"
---
# <a name="export-reports-to-pdf-from-power-bi-desktop"></a>Power BI Desktop からレポートを PDF にエクスポートする
**Power BI Desktop** または Power BI サービスでは、レポートを PDF ファイルにエクスポートすることができます。これにより、ご利用のレポートをその PDF で容易に共有したり印刷したりできます。

![PDF にエクスポート](media/desktop-export-to-pdf/export-to-pdf_01.png)

**Power BI Desktop** から PDF にレポートをエクスポートすると、その PDF を印刷または他のユーザーと共有できるようになります。このエクスポート処理は簡単です。 Power BI Desktop で **[ファイル] > [PDF にエクスポート]** の順に選択するだけです。

**[PDF にエクスポート]** 処理では、レポート内に*表示されている*すべてのページがエクスポートされ、各レポート ページは PDF 内の単一ページにエクスポートされます。 現在表示されていないレポート ページ (ツール ヒントまたは非表示ページなど) は、PDF ファイルにはエクスポートされません。 

![処理中の [PDF にエクスポート]](media/desktop-export-to-pdf/export-to-pdf_02.png)

**[ファイル]、[PDF にエクスポート]** の順に選択すると、エクスポートが開始され、エクスポート処理が進行中であることを示すダイアログが表示されます。 ダイアログは、エクスポート処理が完了するまで、画面上に表示されたままとなります。 エクスポート処理中には、エクスポート中のレポートとのやりとりはすべて無効になります。 レポートとやりとりするには、エクスポート処理が完了するまで待つか、またはエクスポートをキャンセルするしかありません。 

エクスポートが完了すると、PDF は、コンピューター上の既定の PDF ビューアーに読み込まれます。 

## <a name="considerations-and-limitations"></a>考慮事項と制限事項
**[PDF にエクスポート]** 機能にはいくつかの考慮事項があるので注意してください。

* この機能では、Power BI ビジュアルはエクスポートされますが、レポートに適用されている壁紙はエクスポートされ*ません*。

壁紙は PDF にエクスポートされないので、濃色の壁紙を使用しているレポートには特に注意してください。 濃色の壁紙を背景にしてテキストを目立たせるために、ご利用のレポート内のテキストが明るい色または白色になっている場合、壁紙はレポートの残りの部分と一緒にエクスポートされないので、PDF へのエクスポート処理によってテキストは読みづらくなるか、判読不可能になります。 



## <a name="next-steps"></a>次のステップ
**Power BI Desktop** には、あらゆる種類の興味深いビジュアル要素や機能があります。 詳細については、次のリソースを参照してください。

* [ビジュアル要素を使用して Power BI レポートを強化する](desktop-visual-elements-for-reports.md)
* [Power BI Desktop とは何ですか?](../fundamentals/desktop-what-is-desktop.md)
