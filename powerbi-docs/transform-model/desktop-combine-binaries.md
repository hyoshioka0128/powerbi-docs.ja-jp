---
title: Power BI Desktop でファイル (バイナリ) を結合する
description: Power BI Desktop でファイル (バイナリ) データ ソースを簡単に結合できます
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: how-to
ms.date: 01/13/2020
LocalizationGroup: Transform and shape data
ms.openlocfilehash: bf75a5656de956be5ddd38330d659cba06e30455
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415843"
---
# <a name="combine-files-binaries-in-power-bi-desktop"></a>Power BI Desktop でファイル (バイナリ) を結合する

**Power BI Desktop** にデータをインポートするための強力なアプローチがあります。同じスキーマを持つ複数のファイルがある場合は、それらを単一の論理テーブルに結合します。 この一般的な手法がさらに使いやすくなり、より広範になっています。

同じフォルダーのファイルを結合するプロセスを始めるには、 **[データの取得]** を選択し、 **[ファイル]**  >  **[フォルダー]** を選択します。次に、 **[接続]** を選択します。

![フォルダー ファイルへの接続、[データの取得] ダイアログ ボックス、Power BI Desktop](media/desktop-combine-binaries/combine-binaries_1.png)

フォルダーのパスを入力し、 **[OK]** を選択します。次に **[データの変換]** を選択して、Power Query エディターにフォルダーのファイルを表示します。

## <a name="combine-files-behavior"></a>ファイルの結合動作

Power Query エディターでバイナリ ファイルを結合するには、 **[コンテンツ]** (最初の列のラベル) を選択し、 **[ホーム]**  >  **[ファイルの結合]** を選択します。 または、 **[コンテンツ]** の横にある **[ファイルの結合]** アイコンを選択できます。

![[ファイルの結合] コマンド、Power Query エディター、Power BI Desktop](media/desktop-combine-binaries/combine-binaries_2a.png)

*ファイルの結合* 変換は次のように動作します。

* ファイルの結合変換では、各入力ファイルが分析され、使用する適切なファイル形式が決定されます ("*テキスト ファイル*"、"*Excel ブック*"、"*JSON ファイル*" など)。
* 変換では、最初のファイルから特定のオブジェクト (Excel ブックなど) を選択して抽出できます。
  
  ![[ファイルの結合] ダイアログ ボックス、Power Query エディター、Power BI Desktop](media/desktop-combine-binaries/combine-binaries_3.png)
* ファイルの結合変換では、次の操作が自動的に実行されます。
  
  * 単一のファイルで必要なすべての抽出手順を実行するクエリの例を作成します。
  * ファイル/バイナリ入力を *見本クエリ* にパラメーター化する *関数クエリ* を作成します。 見本クエリと関数クエリはリンクされており、見本クエリを変更すると関数クエリに反映されます。
  * "*関数クエリ*" を、入力バイナリの元のクエリ ("*フォルダー*" クエリなど) に適用します。 各行のバイナリ入力に関数クエリが適用された後、結果として得られるデータ抽出が最上位レベルの列として展開されます。

    ![ファイルの結合変換の結果、Power Query エディター、Power BI Desktop](media/desktop-combine-binaries/combine-binaries_4.png)

> [!NOTE]
> Excel ブックでの選択範囲は、バイナリ結合の動作に影響を与えます。 たとえば、特定のワークシートを選択してそのワークシートを結合したり、ルートを選択して完全なファイルを結合したりできます。 フォルダーを選択すると、そのフォルダー内のファイルが結合されます。 

ファイルの結合の動作では、ファイルの種類と構造が同じであれば (同じ列のように)、特定のフォルダー内のすべてのファイルを簡単に結合できます。

さらに、自動的に作成される見本クエリを修正することで、追加の変換または抽出手順を簡単に適用できます。関数クエリの手順を変更したり追加作成したりする必要はありません。 見本クエリに対するすべての変更は、リンクされた関数クエリに自動的に生成されます。

## <a name="next-steps"></a>次の手順

Power BI Desktop を使用して、あらゆる種類のデータに接続することができます。 データ ソースの詳細については、次のリソースを参照してください。

* [Power BI Desktop とは何ですか?](../fundamentals/desktop-what-is-desktop.md)
* [Power BI Desktop のデータ ソース](../connect-data/desktop-data-sources.md)
* [Power BI Desktop でのデータの整形と結合](../connect-data/desktop-shape-and-combine-data.md)
* [Power BI Desktop で CSV ファイルに接続する](../connect-data/desktop-connect-csv.md)
* [Power BI Desktop にデータを直接入力する](../connect-data/desktop-enter-data-directly-into-desktop.md)
