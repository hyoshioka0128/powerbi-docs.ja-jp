---
title: Power BI レポート ビルダーでの式
description: 式は、Power BI Report Builder のページ分割されたレポート全体で、データの取得、計算、表示、グループ化、並べ替え、フィルター処理、パラメーター化、および書式設定を行うために広く使用されます。
author: maggiesMSFT
ms.author: maggies
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 76d3ac86-650c-46fe-8086-8b3edcea3882
ms.openlocfilehash: 24f9348bf23c8e5748121f6967fe7c826984adb9
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96416349"
---
# <a name="expressions-in-power-bi-report-builder"></a>Power BI レポート ビルダーでの式

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

式は、Power BI Report Builder のページ分割されたレポート全体で、データの取得、計算、表示、グループ化、並べ替え、フィルター処理、パラメーター化、および書式設定を行うために広く使用されます。 
  
レポート アイテムのプロパティの多くには、式を設定できます。 式を使用すると、レポートの内容、デザイン、対話性を制御できます。 式は、Microsoft Visual Basic で記述され、レポート定義内に保存され、レポートを実行したときにレポート プロセッサによって評価されます。  
  
 ワークシート内で直接データを操作する Microsoft Office Excel などのアプリケーションとは異なり、レポートでは、データのプレースホルダーである式を操作します。 評価された式の値から実際のデータを確認するには、レポートをプレビューする必要があります。 レポートの実行時に、レポート プロセッサーはテーブルやグラフなどのレポート データ要素とレポート レイアウト要素を組み合わせて、それぞれの式を評価します。  
  
 レポートをデザインする場合、レポート アイテムの式の多くは、自動的に設定されます。 たとえば、データ ペインからレポート デザイン画面のテーブル セルにフィールドをドラッグすると、そのフィールドのテキスト ボックスの値には単純式が設定されます。 次の図では、レポート データ ペインに、データセット フィールドの ID、Name、SalesTerritory、Code、および Sales が表示されています。 テーブルに [Name]、[Code]、[Sales] の 3 つのフィールドが追加されています。 デザイン画面上の [Name] の表記は基になる式 `=Fields!Name.Value`を表しています。  
  
![レポート ビルダー デザイン ビュー](media/report-builder-expressions/report-builder-data-design-preview.png)
  
 レポートをプレビューすると、レポート プロセッサーによってテーブル データ領域がデータ接続からの実際のデータと結合され、結果セット内の各行に対してテーブル内に行が表示されます。  
  
 式を手動で入力するには、デザイン画面でアイテムを選択し、ショートカット メニューおよびダイアログ ボックスを使用して、アイテムのプロパティを設定します。 **(fx)** ボタンまたはドロップダウン リストでの値 `<Expression>` の表示によって、式にプロパティを設定できることがわかります。 
  
##  <a name="understanding-simple-and-complex-expressions"></a><a name="Types"></a> 単純な式と複雑な式を理解する  
 式は等号 (=) で始まり、Microsoft Visual Basic で記述されます。 式には、定数、演算子、および組み込みの値 (フィールド、コレクション、および関数) への参照、拡張またはカスタム コードへの参照の組み合わせを含むことができます。  
  
 式を使用すると、多くのレポート アイテム プロパティの値を指定できます。 最も一般的なプロパティは、テキスト ボックスとプレースホルダーのテキストの値です。 通常、テキスト ボックスに 1 つの式しか含まれていない場合、その式がテキスト ボックス プロパティの値となります。 テキスト ボックスに複数の式が含まれている場合は、各式がテキスト ボックス内のプレースホルダー テキストの値となります。  
  
 既定では、式はレポート デザイン画面上に "単純な式" または "*複雑な式*" として表示されます。  
  
-   **単純** 組み込みコレクション (データセット フィールド、パラメーター、または組み込みフィールドなど) 内の 1 つのアイテムへの参照を含む単純式です。 デザイン画面では、単純式は角かっこ内に表示されます。 たとえば、 `[FieldName]` は基となる式 `=Fields!FieldName.Value`に対応します。 単純式は、レポート レイアウトを作成し、[レポート データ] ペインからデザイン画面にアイテムをドラッグする際に自動的に作成されます。 さまざまな組み込みコレクションを表す記号の詳細については、「 [単純式でのプレフィックス記号について](#DisplayText)」を参照してください。  
  
-   **複合** 複合式には、複数の組み込み参照、演算子、および関数呼び出しへの参照が含まれます。 式の値に単純な参照が複数含まれる場合、複合式は <\<Expr>> として表示されます。 式を表示するには、その上にカーソルを合わせ、ツールヒントを使用します。 式を編集するには、 **[式]** ダイアログ ボックスでそれを開きます。  
  
 次の図は、テキスト ボックスおよびプレースホルダー テキストの両方の典型的な単純式と複合式を示しています。  
  
![レポート ビルダーの式の既定の形式](media/report-builder-expressions/report-builder-expression-default-format.png) 
  
 式のテキストではなくサンプル値を表示するには、テキスト ボックスまたはプレースホルダー テキストに書式を適用します。 次の図は、サンプル値に切り替えられたレポートのデザイン画面を示しています。  
  
![レポート ビルダーでの式形式の例](media/report-builder-expressions/report-builder-expression-sample-values-format.png)  


## <a name="understanding-prefix-symbols-in-simple-expressions"></a><a name="DisplayText"></a> 単純な式でのプレフィックス記号について  

単純式では、記号を使用して、参照先 (フィールド、パラメーター、組み込みコレクション、または ReportItems コレクション) を示します。 表示テキストおよび式のテキストの例を次の表に示します。  
  
|Item|表示テキストの例|式のテキストの例|  
|----------|--------------------------|-----------------------------|  
|データセット フィールド|`[Sales]`<br /><br /> `[SUM(Sales)]`<br /><br /> `[FIRST(Store)]`|`=Fields!Sales.Value`<br /><br /> `=Sum(Fields!Sales.Value)`<br /><br /> `=First(Fields!Store.Value)`|  
|レポート パラメーター|`[@Param]`<br /><br /> `[@Param.Label]`|`=Parameters!Param.Value`<br /><br /> `=Parameters!Param.Label`|  
|組み込みフィールド|`[&ReportName]`|`=Globals!ReportName.Value`|  
|表示テキストに使用されるリテラル文字|`\[Sales\]`|`[Sales]`|  
  
##  <a name="writing-complex-expressions"></a><a name="References"></a> 複雑な式の記述  
 式には、関数、演算子、定数、フィールド、パラメーター、組み込みコレクションのアイテム、および埋め込みのカスタム コードまたはカスタム アセンブリへの参照を含めることができます。  
  
 次の表に、式に含めることのできる参照の種類の一覧を示します。  
  
|References|説明|例|  
|----------------|-----------------|-------------|  
|定数|定数値を必要とするプロパティ (フォントの色など) に対話的にアクセスできる定数について説明します。|`="Blue"`|  
|演算子|式の中で参照を組み合わせる際に使用できる演算子について説明します。 たとえば、 **&** 演算子は、文字列を連結する場合に使用されます。|`="The report ran at: " & Globals!ExecutionTime & "."`|  
|組み込みコレクション|式に含めることができる組み込みコレクション ( `Fields`、 `Parameters`、 `Variables`など) について説明します。|`=Fields!Sales.Value`<br /><br /> `=Parameters!Store.Value`<br /><br /> `=Variables!MyCalculation.Value`|  
|組み込みのレポート関数と集計関数|式からアクセスできる、 `Sum` や `Previous`などの組み込み関数について説明します。|`=Previous(Sum(Fields!Sales.Value))`|  
|レポート ビルダーの式内のカスタム コードとアセンブリ参照 |組み込み CLR クラスの `xref:System.Math` と `xref:System.Convert`、他の CLR クラス、Visual Basic ランタイム ライブラリ関数、または外部アセンブリのメソッドにアクセスする方法を記述します。<br /><br /> レポート内に埋め込まれているカスタム コード、またはレポート クライアントとレポート サーバーの両方でカスタム アセンブリとしてコンパイルしてインストールするカスタム コードへのアクセス方法について説明します。|`=Sum(Fields!Sales.Value)`<br /><br /> `=CDate(Fields!SalesDate.Value)`<br /><br /> `=DateAdd("d",3,Fields!BirthDate.Value)`<br /><br /> `=Code.ToUSD(Fields!StandardCost.Value)`|  
   
##  <a name="validating-expressions"></a><a name="Valid"></a> 式の検証  
 特定のレポート アイテム プロパティの式を作成する場合、式に含めることのできる参照は、レポート アイテム プロパティで受け入れられる値と、プロパティの評価のスコープによって異なります。 次に例を示します。  
  
-   既定では、式 [Sum] は式の評価時のスコープ内のデータの合計を計算します。 テーブル セルの場合、スコープは行と列のグループ メンバーシップによって異なります。 
  
-   Font プロパティの値については、値はフォント名に評価される必要があります。  
  
-   式の構文はデザイン時に検証されます。 式のスコープの検証は、レポートのパブリッシュ時に行われます。 実際のデータに依存する検証の場合、エラーは実行時にしか検出されません。 これらの式の一部では、レンダリングされたレポートでエラー メッセージとして #Error が生成されます。 

## <a name="next-steps"></a>次の手順

- [Power BI Premium のページ分割されたレポートとは](paginated-reports-report-builder-power-bi.md)
