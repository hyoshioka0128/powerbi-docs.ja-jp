---
title: Power BI レポート ビルダーでの式の例
description: 式は、Power BI Report Builder のページ分割されたレポートで、内容とレポートの外観を制御するためによく使われます。
author: maggiesMSFT
ms.author: maggies
ms.date: 11/08/2020
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 87ddb651-a1d0-4a42-8ea9-04dea3f6afa4
ms.openlocfilehash: a919efad0b9656327a766986456c533242d40c2e
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96416326"
---
# <a name="expression-examples-in-power-bi-report-builder"></a>Power BI レポート ビルダーでの式の例

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

式は、Power BI Report Builder のページ分割されたレポートで、内容とレポートの外観を制御するためによく使われます。 式を記述するには Microsoft Visual Basic を使い、式では組み込み関数、カスタム コード、レポートとグループ変数、およびユーザー定義変数を使うことができます。 式は等号 (=) で始まります。   

このトピックでは、レポート内で一般的なタスクに使用できる式の例を示します。  
  
-   [Visual Basic の関数](#VisualBasicFunctions): Visual Basic の日付、文字列、変換、条件関数の例。  
  
-   [レポートの関数](#ReportFunctions) 集計および組み込みのレポート関数の例。  
  
-   [レポート データの表示方法](#AppearanceofReportData) レポートの外観を変更する例。  
  
-   [プロパティ](#Properties) 形式または表示を制御するために、レポート アイテムのプロパティを設定する例。  
  
-   [パラメーター](#Parameters) 式の中でパラメーターを使用する例。  
  
-   [カスタム コード](#CustomCode) 埋め込まれたカスタム コードの例。  
  
単純な式と複雑な式、式を使用できる場所、および式に含めることができる参照の種類について詳しくは、「[Expressions in Power BI Report Builder](report-builder-expressions.md)」(Power BI レポート ビルダーでの式) のトピックをご覧ください。 
  
## <a name="functions"></a>関数  
 レポート内の多くの式には、関数が含まれています。 これらの関数を使用して、データの書式を設定し、ロジックを適用し、レポートのメタデータにアクセスできます。 Microsoft Visual Basic ランタイム ライブラリの関数や、`xref:System.Convert` および `xref:System.Math` 名前空間の関数を使って、式を記述することができます。 カスタム コード内の関数への参照を追加できます。 また、`xref:System.Text.RegularExpressions` などの Microsoft .NET Framework のクラスを使うこともできます。  
  
##  <a name="visual-basic-functions"></a><a name="VisualBasicFunctions"></a> Visual Basic の関数  
 Visual Basic の関数を使って、テキスト ボックスに表示されるデータや、パラメーター、プロパティ、またはレポートの他の領域に使われるデータを、操作することができます。 ここでは、このような関数のうち、いくつかの例を紹介します。 各関数の詳細については、MSDN の「 [Visual Basic ランタイム ライブラリのメンバー](/dotnet/visual-basic/language-reference/runtime-library-members) 」を参照してください。  
  
 .NET Framework では、特定の日付形式など、さまざまなカスタム書式オプションが提供されています。 詳細については、[型の書式設定](/dotnet/standard/base-types/formatting-types)に関するページをご覧ください。  
  
### <a name="math-functions"></a>算術関数  
  
-   **Round** 関数は、数値を最も近い整数に丸める場合に役立ちます。 次の式は、1.3 を 1 に丸めます。  
  
    ```  
    = Round(1.3)  
    ```  
  
     Excel の **MRound** 関数のように、指定の倍数値に値を丸める式を記述することもできます。 整数値を作成する係数で値を乗算し、その数値を丸め、同じ係数で除算します。 たとえば、1.3 を最も近い 0.2 の倍数 (1.4) に丸めるには、次の式を使用します。  
  
    ```  
    = Round(1.3*5)/5  
    ```  
  
###  <a name="date-functions"></a><a name="DateFunctions"></a> 日付関数  
  
-   **Today** 関数は現在の日付を返します。 この式は、レポートに日付を表示するテキスト ボックス、または現在の日付に基づいてデータをフィルター処理するパラメーターに使用できます。  
  
    ```  
    =Today()  
    ```  
  
-   **DateInterval** 関数を使用して、日付の特定の部分を抽出します。 有効な **DateInterval** パラメーターの一部を次に示します。

    -   DateInterval.Second
    -   DateInterval.Minute
    -   DateInterval.Hour
    -   DateInterval.Weekday
    -   DateInterval.Day
    -   DateInterval.DayOfYear
    -   DateInterval.WeekOfYear
    -   DateInterval.Month
    -   DateInterval.Quarter
    -   DateInterval.Year

    たとえば、この式は今日の日付が現在の年の何週目かを表示します。
  
    ```  
    =DatePart(DateInterval.WeekOfYear, today()) 
    ```  
  
-   **DateAdd** 関数は、1 つのパラメーターに基づいて日付の範囲を指定する場合に役立ちます。 次の式では、 *StartDate* という名前のパラメーターで指定した日付の 6 か月後の日付が返されます。  
  
    ```  
    =DateAdd(DateInterval.Month, 6, Parameters!StartDate.Value)  
    ```  
  
-   **Year** 関数は、特定の日付の年を表示します。 この関数を使用して、日付をグループ化したり、一連の日付のラベルとして年を表示したりできます。 次の式では、指定した販売注文日グループの年が返されます。 また、 **Month** 関数および他の関数を使用して、日付を操作することもできます。 詳しくは、Visual Basic のドキュメントをご覧ください。  
  
    ```  
    =Year(Fields!OrderDate.Value)  
    ```  
  
-   式の中で関数を組み合わせることで、形式をカスタマイズすることができます。 次の式は、"月-日-年" の日付の形式を "月-週番号" に変更します。 たとえば、"12/23/2009" は "December Week 3" になります。  
  
    ```  
    =Format(Fields!MyDate.Value, "MMMM") & " Week " &   
    (Int(DateDiff("d", DateSerial(Year(Fields!MyDate.Value),   
    Month(Fields!MyDate.Value),1), Fields!FullDateAlternateKey.Value)/7)+1).ToString  
    ```  
  
     この式をデータセット内の計算フィールドとしてグラフで使用すると、各月の週ごとに値を集計できます。  
  
-   次の式は、SellStartDate の値を MMM-YY の書式で設定します。 SellStartDate フィールドは、datetime データ型です。  
  
    ```  
    =FORMAT(Fields!SellStartDate.Value, "MMM-yy")  
    ```  
  
-   次の式は、SellStartDate の値を dd/MM/yyyy の書式で設定します。 SellStartDate フィールドは、datetime データ型です。  
  
    ```  
    =FORMAT(Fields!SellStartDate.Value, "dd/MM/yyyy")  
    ```  
  
-   **CDate** 関数は、値を日付に変換します。 **Now** 関数は、使用中のシステムに応じて、現在の日付と時刻を含む日付値を返します。 **DateDiff** は、2 つの日付値の間にある期間を数値で示す Long 値を返します。  
  
     次の例では、今年の最初の日が表示されます。  
  
    ```  
    =DateAdd(DateInterval.Year,DateDiff(DateInterval.Year,CDate("01/01/1900"),Now()),CDate("01/01/1900"))  
    ```  
  
-   次の例では、現在の月に基づいて、前の月の最初の日が表示されます。  
  
    ```  
    =DateAdd(DateInterval.Month,DateDiff(DateInterval.Month,CDate("01/01/1900"),Now())-1,CDate("01/01/1900"))  
    ```  
  
-   次の式は、SellStartDate と LastReceiptDate の間にある年数を生成します。 これらのフィールドは、DataSet1 と DataSet2 の異なる 2 つのデータセットに含まれます。  
  
    ```  
    =DATEDIFF("yyyy", First(Fields!SellStartDate.Value, "DataSet1"), First(Fields!LastReceiptDate.Value, "DataSet2"))  
    ```  
  
-   **DatePart** 関数は、特定の日付値の指定されたコンポーネントを含む整数値を返します。次の式は、DataSet1 にある SellStartDate の最初の値の年を返します。 レポートに複数のデータセットがあるため、データセット スコープが指定されます。  
  
    ```  
    =Datepart("yyyy", First(Fields!SellStartDate.Value, "DataSet1"))  
  
    ```  
  
-   **DateSerial** 関数は、時間情報が午前 0 時に設定されている、指定の年月日を表す日付値を返します。 次の例では、現在の月に基づいて、前の月の最終日が表示されます。  
  
    ```  
    =DateSerial(Year(Now()), Month(Now()), "1").AddDays(-1)  
    ```  
  
-   次の式では、ユーザーによって選択された日付のパラメーター値に基づくさまざまな日付が表示されます。  
  
|例の説明|例|  
|-------------------------|-------------|  
|[昨日]|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-1)`|  
|2 日前|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-2)`|  
|1 か月前|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-1,Day(Parameters!TodaysDate.Value))`|  
|2 か月前|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-2,Day(Parameters!TodaysDate.Value))`|  
|1 年前|`=DateSerial(Year(Parameters!TodaysDate.Value)-1,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  
|2 年前|`=DateSerial(Year(Parameters!TodaysDate.Value)-2,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  
  
###  <a name="string-functions"></a><a name="StringFunctions"></a> 文字列関数  
  
-   連結演算子と Visual Basic の定数を使って、複数のフィールドを結合します。 次の式では、2 つのフィールドが、同じテキスト ボックス内の別々の行に返されます。  
  
    ```  
    =Fields!FirstName.Value & vbCrLf & Fields!LastName.Value   
    ```  
  
-   **Format** 関数を使用して、文字列内の日付と数値の書式を設定します。 次の式では、 *StartDate* パラメーターおよび *EndDate* パラメーターの値が長い日付形式で表示されます。  
  
    ```  
    =Format(Parameters!StartDate.Value, "D") & " through " &  Format(Parameters!EndDate.Value, "D")    
    ```  
  
     日付または数値のみを格納するテキスト ボックスに書式を適用する場合は、テキスト ボックス内で **Format** 関数を使用するのではなく、テキスト ボックスの Format プロパティを使用する必要があります。  
  
-   **Right**、 **Len**、 **InStr** の各関数は、サブストリングを返す場合に役立ちます。たとえば、 *DOMAIN*\\*username* の文字列からユーザー名だけを返します。 次の式では、\\User *というパラメーターで取得できる文字列のうち、円記号 (* ) より右側の部分のみが返されます。  
  
    ```  
    =Right(Parameters!User.Value, Len(Parameters!User.Value) - InStr(Parameters!User.Value, "\"))  
    ```  
  
     次の式の結果は前の式と同じ値ですが、Visual Basic の関数ではなく、.NET Framework の `xref:System.String` クラスのメンバーを使っています。  
  
    ```  
    =Parameters!User.Value.Substring(Parameters!User.Value.IndexOf("\")+1, Parameters!User.Value.Length-Parameters!User.Value.IndexOf("\")-1)  
    ```  
  
-   複数の値を持つパラメーターから選択した値を表示します。 次の例では、 **Join** 関数を使用して、パラメーター *MySelection* から選択した複数の値を連結して単一の文字列にし、その文字列をレポート アイテム内のテキスト ボックスの値を表す式として設定できるようにしています。  
  
    ```  
    = Join(Parameters!MySelection.Value)  
    ```  
  
     次の例では、前の例と同じ処理を行うだけでなく、選択した値のリストの前にテキスト文字列を表示します。  
  
    ```  
    ="Report for " & JOIN(Parameters!MySelection.Value, " & ")  
  
    ```  
  
-   .NET Framework の `xref:System.Text.RegularExpressions` の **Regex** 関数は、既存の文字列の形式を変更するのに便利です (たとえば、電話番号の書式設定)。 次の式では、フィールドに含まれる、" **nnn** nnn *nnnn*- *" 形式の 10 桁の電話番号を、* -*Replace* 関数を使用して "(*nnn*) *nnn*-*nnnn*" 形式に変更しています。  
  
    ```  
    =System.Text.RegularExpressions.Regex.Replace(Fields!Phone.Value, "(\d{3})[ -.]*(\d{3})[ -.]*(\d{4})", "($1) $2-$3")  
    ```  
  
    > [!NOTE]  
    >  Fields!Phone.Value に余分なスペースがないことと、データ型が `xref:System.String`」を参照してください。  
  
### <a name="lookup"></a>参照  
  
-   キー フィールドを指定することで、 **Lookup** 関数を使用し、1 対 1 のリレーションシップ (キーと値のペアなど) の値をデータセットから取得することができます。 次の式では、入力された製品識別子に一致する製品名をデータセット ("Product") から取得し、表示します。  
  
    ```  
    =Lookup(Fields!PID.Value, Fields!ProductID.Value, Fields.ProductName.Value, "Product")  
    ```  
  
### <a name="lookupset"></a>LookupSet  
  
-   キー フィールドを指定することで、 **LookupSet** 関数を使用し、1 対多のリレーションシップの値のセットをデータセットから取得することができます。 たとえば、1 人の個人が複数の電話番号を持っていることがあります。 次の例では、PhoneList データセットに個人識別子が含まれ、各行に電話番号が格納されているものとしています。 **LookupSet** は、値の配列を返します。 次の例では、返された値を 1 つの文字列として結合し、ContactID で指定される個人の電話番号の一覧を表示します。  
  
    ```  
    =Join(LookupSet(Fields!ContactID.Value, Fields!PersonID.Value, Fields!PhoneNumber.Value, "PhoneList"),",")  
    ```  
  
###  <a name="conversion-functions"></a><a name="ConversionFunctions"></a> 変換関数  
 Visual Basic の関数を使って、フィールドをあるデータ型から別のデータ型に変換できます。 変換関数を使用すると、フィールドの既定のデータ型を、計算やテキストの連結に必要なデータ型に変換できます。  
  
-   次の式では、定数 500 を、フィルター式の Value フィールドで Transact-SQL の通貨データ型と比較するために Decimal 型に変換しています。  
  
    ```  
    =CDec(500)  
    ```  
  
-   次の式では、複数の値を持つパラメーター *MySelection* で選択された値の数が表示されます。  
  
    ```  
    =CStr(Parameters!MySelection.Count)  
    ```  
  
###  <a name="decision-functions"></a><a name="DecisionFunctions"></a> 決定関数  
  
-   **Iif** 関数では、式が True かどうかによって、2 つの値のいずれかが返されます。 次の式では、 **Iif** 関数を使用して、 **の値が 100 を超える場合にブール値** True `LineTotal` が返されます。 それ以外の場合は **False** を返します。  
  
    ```  
    =IIF(Fields!LineTotal.Value > 100, True, False)  
    ```  
  
-   複数の **IIF** 関数 ("入れ子になった IIF" とも呼ばれます) を使用すると、 `PctComplete`の値に応じて 3 つの値のいずれかが返されます。 次の式をテキスト ボックスの塗りつぶしの色に使用すると、テキスト ボックスの値に応じて背景色を変更できます。  
  
    ```  
    =IIF(Fields!PctComplete.Value >= 10, "Green", IIF(Fields!PctComplete.Value >= 1, "Blue", "Red"))  
    ```  
  
     背景は、値が 10 以上の場合は緑色、1 ～ 9 の場合は青色、1 未満の場合は赤色になります。  
  
-   同じ機能を実現するには、 **Switch** 関数を使用するという方法もあります。 **Switch** 関数は、検証する条件が 3 つ以上ある場合に役立ちます。 **Switch** 関数は、True に評価される一連の式のうちの最初の式に関連付けられた値を返します。  
  
    ```  
    =Switch(Fields!PctComplete.Value >= 10, "Green", Fields!PctComplete.Value >= 1, "Blue", Fields!PctComplete.Value = 1, "Yellow", Fields!PctComplete.Value <= 0, "Red")  
    ```  
  
     背景は、値が 10 以上の場合は緑色、1 ～ 9 の場合は青色、1 の場合は黄色、0 以下の場合は赤色になります。  
  
-   `ImportantDate` フィールドの値を調べて、1 週間より古い場合は "Red" を返し、それ以外の場合は "Blue" を返します。 この式を使用して、レポート アイテムに含まれるテキスト ボックスの Color プロパティを制御できます。  
  
    ```  
    =IIF(DateDiff("d",Fields!ImportantDate.Value, Now())>7,"Red","Blue")  
    ```  
  
-   `PhoneNumber` フィールドの値を調べて、**null** (Visual Basic では **Nothing**) の場合は "No Value" を返し、それ以外の場合は電話番号の値を返します。 この式を使用して、レポート アイテムに含まれるテキスト ボックスの値を制御できます。  
  
    ```  
    =IIF(Fields!PhoneNumber.Value Is Nothing,"No Value",Fields!PhoneNumber.Value)  
    ```  
  
-   `Department` フィールドの値を調べて、サブレポートの名前または **null** (Visual Basic では **Nothing**) を返します。 この式は、条件付きドリルスルー サブレポートで使用できます。  
  
    ```  
    =IIF(Fields!Department.Value = "Development", "EmployeeReport", Nothing)  
    ```  
  
-   フィールド値が NULL かどうかを検証します。 この式を使用すると、画像レポート アイテムの **Hidden** プロパティを制御できます。 次の例では、LargePhoto というフィールドの値が NULL でない場合にのみ、このフィールドで指定された画像が表示されます。  
  
    ```  
    =IIF(IsNothing(Fields!LargePhoto.Value),True,False)  
    ```  
  
-   **MonthName** 関数は、指定した月に対応する月名を含む文字列値を返します。 次の例では、フィールドに 0 という値が格納されている場合に、Month フィールドで NA と表示されます。  
  
    ```  
    IIF(Fields!Month.Value=0,"NA",MonthName(IIF(Fields!Month.Value=0,1,Fields!Month.Value)))  
  
    ```  
  
##  <a name="report-functions"></a><a name="ReportFunctions"></a> レポート関数  
 レポートには、これ以外にも、レポート内のデータを操作するレポート関数への参照を追加することができます。 ここでは、このような関数のうち 2 つの例を紹介します。 
  
###  <a name="sum"></a><a name="Sum"></a> Sum  
  
-   **Sum** 関数を使用すると、グループまたはデータ領域内の値を合計できます。 この関数は、グループのヘッダーまたはフッターで役立ちます。 次の式では、Order グループまたは Order データ領域内のデータの合計が表示されます。  
  
    ```  
    =Sum(Fields!LineTotal.Value, "Order")  
    ```  
  
-   **Sum** 関数は、条件付き集計計算にも使用できます。 たとえば、データセットに State という名前のフィールドが存在し、Not Started、Started、Finished という値を設定できる場合、次の式をグループ ヘッダーで使用すると、値 Finished の合計のみが計算されます。  
  
    ```  
    =Sum(IIF(Fields!State.Value = "Finished", 1, 0))  
    ```  
  
###  <a name="rownumber"></a><a name="RowNumber"></a> RowNumber  
  
-   **RowNumber** 関数をデータ領域内のテキスト ボックスで使用すると、式が表示されるテキスト ボックスの各インスタンスの行数が表示されます。 この関数は、テーブル内の行数を数える場合に役立ちます。 また、行数に基づいた改ページの指定など、より複雑なタスクにも役立ちます。 詳細については、このトピックの「 [改ページ](#PageBreaks) 」を参照してください。  
  
     **RowNumber** に指定したスコープによって、どの時点で番号の再設定を開始するかが制御されます。 この関数に **Nothing** キーワードを指定することで、最も外側のデータ領域内の最初の行からカウントが開始されます。 入れ子になったデータ領域内でカウントを開始するには、データ領域の名前を使用します。 グループ内でカウントを開始するには、グループの名前を使用します。  
  
    ```  
    =RowNumber(Nothing)  
    ```  
  
##  <a name="appearance-of-report-data"></a><a name="AppearanceofReportData"></a> レポート データの表示方法  
 式を使用して、レポートにデータを表示する方法を操作できます。 たとえば、2 つのフィールドの値を 1 つのテキスト ボックスに表示したり、レポートに関する情報を表示したり、レポートに改ページを挿入する方法に影響を与えたりすることができます。  
  
###  <a name="page-headers-and-footers"></a><a name="PageHeadersandFooters"></a> ページのヘッダーとフッター  
 レポートをデザインする場合、必要に応じてレポート名とページ番号をレポート フッターに表示できます。 この操作を行うには、以下の式を使用できます。  
  
-   次の式では、レポート名、およびレポートが実行された時刻が返されます。 この式は、レポート フッターまたはレポート本文のテキスト ボックスで使用できます。 時刻の書式は、.NET Framework の短い日付用の書式文字列で設定されてます。  
  
    ```  
    =Globals.ReportName & ", dated " & Format(Globals.ExecutionTime, "d")  
    ```  
  
-   次の式では、レポートのページ番号および全ページ数が返されます。この式は、レポートのフッター内のテキスト ボックスで使用できます。  
  
    ```  
    =Globals.PageNumber & " of " & Globals.TotalPages  
    ```  
  
 以下の例では、ディレクトリの一覧の内容と同様に、ページ ヘッダーにページの最初と最後の値を表示する方法について説明します。 この例では、 `LastName`という名前のテキスト ボックスを含むデータ領域を想定しています。  
  
-   次の式は、ページ ヘッダーの左側にあるテキスト ボックスで使用されます。この式では、そのページの `LastName` テキスト ボックスの最初の値が返されます。  
  
    ```  
    =First(ReportItems("LastName").Value)  
    ```  
  
-   次の式は、ページ ヘッダーの右側にあるテキスト ボックスで使用されます。この式では、そのページの `LastName` テキスト ボックスの最後の値が返されます。  
  
    ```  
    =Last(ReportItems("LastName").Value)  
    ```  
  
 次の例では、合計ページ数の表示方法について説明します。 この例では、 `Cost`という名前のテキスト ボックスを含むデータ領域を想定しています。  
  
-   次の式は、ページ ヘッダーまたはページ フッターで使用されます。この式では、 `Cost` テキスト ボックスの値の合計がそのページに返されます。  
  
    ```  
    =Sum(ReportItems("Cost").Value)  
    ```  
  
> [!NOTE]  
>  ページ ヘッダーまたはページ フッターでは、1 つの式につき 1 つのレポート アイテムしか参照できません。 また、ページ ヘッダーまたはページ フッターの式では、テキスト ボックスの名前を参照することはできますが、テキスト ボックス内の実際のデータ式は参照できません。  
  
###  <a name="page-breaks"></a><a name="PageBreaks"></a> 改ページ  
 レポートによっては、グループやレポート アイテムに改ページを設定せずに、またはグループやレポート アイテムの改ページに追加する形で、指定した行数の最後に改ページを挿入したい場合があります。 この操作を行うには、必要なグループや詳細レコードを含むグループを作成し、そのグループに改ページを追加した後、指定された行数でグループ化を行うグループ式を追加します。  
  
-   次の式をグループ式で使用すると、25 行ごとに数値が割り当てられます。 グループに改ページが定義されている場合は、この式の結果として、25 行ごとに改ページが行われます。  
  
    ```  
    =Ceiling(RowNumber(Nothing)/25)  
    ```  
  
     ユーザーが 1 ページあたりの行数の値を設定できるようにするには、 `RowsPerPage` という名前のパラメーターを作成し、次の式で示すように、そのパラメーターに基づいてグループ式を作成します。  
  
    ```  
    =Ceiling(RowNumber(Nothing)/Parameters!RowsPerPage.Value)  
    ```  
  
##  <a name="properties"></a><a name="Properties"></a> プロパティ  
 式は、テキスト ボックスにデータを表示するためだけに使用するものではありません。 レポート アイテムにプロパティを適用する方法を変更する場合にも使用できます。 レポート アイテムのスタイル情報を変更したり、情報の表示を変更することができます。  
  
###  <a name="formatting"></a><a name="Formatting"></a> 書式設定  
  
-   テキスト ボックスの Color プロパティで次の式を使用すると、 `Profit` フィールドの値に応じてテキストの色が変更されます。  
  
    ```  
    =Iif(Fields!Profit.Value < 0, "Red", "Black")  
    ```  
  
     Visual Basic のオブジェクト変数 `Me` を使うこともできます。 この変数は、テキスト ボックスの値を参照するもう 1 つの手段です。  
  
     `=Iif(Me.Value < 0, "Red", "Black")`  
  
-   データ領域にあるレポート アイテムの BackgroundColor プロパティで次の式を使用すると、各行の背景色に薄緑色と白が交互に設定されます。  
  
    ```  
    =Iif(RowNumber(Nothing) Mod 2, "PaleGreen", "White")  
    ```  
  
     特定のスコープに対して式を使用する場合は、次のように、集計関数に対してデータセットを指定する必要があります。  
  
    ```  
    =Iif(RowNumber("Employees") Mod 2, "PaleGreen", "White")  
    ```  
  
> [!NOTE]  
>  使用できる色は、.NET Framework の KnownColor 列挙型から取得します。  
  
### <a name="chart-colors"></a>グラフの色  
 図形グラフの色を指定するには、色がデータ点にマップされる順序を制御するカスタム コードを使用できます。 これは複数のグラフで同じカテゴリ グループの色を統一するときに役立ちます。 
  
###  <a name="visibility"></a><a name="Visibility"></a> 表示  
 レポート アイテムの表示プロパティを使用して、レポート内のアイテムの表示/非表示を切り替えることができます。 テーブルなどのデータ領域では、最初に、式の値に基づいて詳細行を非表示にできます。  
  
-   グループ内の詳細行の初期表示に次の式を使用すると、 `PctQuota` フィールドで 90% を超えるすべての売上の詳細行が表示されます。  
  
    ```  
    =Iif(Fields!PctQuota.Value>.9, False, True)  
    ```  
  
-   テーブルの Hidden プロパティに次の式を設定すると、テーブルの行数が 12 行を超えた場合にのみテーブルが表示されます。  
  
    ```  
    =IIF(CountRows()>12,false,true)  
    ```  
  
-   列の **Hidden** プロパティに次の式を設定すると、データ ソースからデータが取得された後にレポート データセットにフィールドが存在する場合にのみ列が表示されます。  
  
    ```  
    =IIF(Fields!Column_1.IsMissing, true, false)  
    ```  
  
###  <a name="urls"></a><a name="Hyperlinks"></a> URL  
 レポート データを使用して URL をカスタマイズできます。また、テキスト ボックスに対するアクションとして URL を追加するかどうかを、条件付きで制御することもできます。  
  
-   次の式をテキスト ボックスに対するアクションとして使用すると、URL パラメーターとしてデータセット フィールド `EmployeeID` を指定する、カスタマイズされた URL が生成されます。  
  
    ```  
    ="https://adventure-works/MyInfo?ID=" & Fields!EmployeeID.Value  
    ```  
  
-   次の式では、テキスト ボックス内に URL を追加するかどうかを、条件付きで制御します。 この式では、アクティブ URL をレポートに含めるかどうかをユーザーが決定できるように、 `IncludeURLs` という名前のパラメーターを使用しています。 この式は、テキスト ボックスに対するアクションとして設定されます。 パラメーターを False に設定してからレポートを表示すると、ハイパーリンクなしでレポートを Microsoft Excel にエクスポートできます。  
  
    ```  
    =IIF(Parameters!IncludeURLs.Value,"https://adventure-works.com/productcatalog",Nothing)  
    ```  
  
> [!NOTE]
>  Power BI のページ分割されたレポートは、 **[URL に移動する]** 式内での JavaScript の使用をサポートしていません。  
  
##  <a name="report-data"></a><a name="ReportData"></a> レポート データ  
 式を使用して、レポートで使用するデータを操作できます。 パラメーターおよび他のレポート情報を参照できます。 レポートのデータを取得するために使用されるクエリを変更することもできます。  
  
###  <a name="parameters"></a><a name="Parameters"></a> パラメーター  
 パラメーターの式を使用して、パラメーターの既定値を変更できます。 たとえば、パラメーターを使用して、レポートの実行に使用されるユーザー ID に基づき、特定のユーザーに合わせてデータをフィルター処理することができます。  
  
-   パラメーターの既定値として次の式を使用すると、レポートを実行するユーザーのユーザー ID が収集されます。  
  
    ```  
    =User!UserID  
    ```  
  
-   レポートのクエリ パラメーター、フィルター式、テキスト ボックスなどの領域でパラメーターを参照するには、 **Parameters** グローバル コレクションを使用します。 この例では、パラメーターの名前が *Department* であることを想定しています。  
  
    ```  
    =Parameters!Department.Value  
    ```  
  
-   パラメーターはレポート内に作成できますが、非表示に設定されます。 レポートがレポート サーバーで実行されても、パラメーターはツール バーに表示されず、レポートのユーザーは既定値を変更できません。 既定値に設定された非表示パラメーターは、カスタム定数として使用できます。 この値は、フィールド式など、あらゆる式で使用できます。 次の式では、 *ParameterField* という名前を持つパラメーターの既定値で指定されたフィールドを特定しています。  
  
    ```  
    =Fields(Parameters!ParameterField.Value).Value  
    ```  
  
##  <a name="custom-code"></a><a name="CustomCode"></a> カスタム コード  
 レポートに埋め込まれたカスタム コードを使用できます。 
  
### <a name="using-group-variables-for-custom-aggregation"></a>カスタム集計に対するグループ変数の使用  
 特定のグループ スコープ内のローカルなグループ変数の値を初期化し、その変数を式の中で参照することができます。 カスタム コードでグループ変数を使用するシナリオとしては、カスタム集計の実装が挙げられます。 
  
## <a name="suppressing-null-or-zero-values-at-run-time"></a>実行時に null 値またはゼロ値を表示しない  
 式内の一部の値は、レポート処理時に NULL または未定義と評価されることがあります。 その結果、実行時エラーが発生して、評価した式ではなく **#Error** がテキスト ボックスに表示される場合があります。 **IIF** 関数は特にこの動作の影響を受けます。これは、If-Then-Else ステートメントとは異なり、 **IIF** ステートメントの各部分 (関数呼び出しを含む) が、 **true** であるか **false** であるかを検証するルーチンに渡される前に評価されるためです。 `=IIF(Fields!Sales.Value is NOTHING, 0, Fields!Sales.Value)` ステートメントを実行すると、 **が NOTHING の場合は、表示されたレポートに** #Error `Fields!Sales.Value` と表示されます。  
  
 この状況を回避するには、次のいずれかの方法を使用します。  
  
-   フィールド B の値が 0 または未定義の場合は、分子に 0、分母に 1 を設定します。それ以外の場合は、分子にフィールド A の値、分母にフィールド B の値を設定します。  
  
    ```  
    =IIF(Field!B.Value=0, 0, Field!A.Value / IIF(Field!B.Value =0, 1, Field!B.Value))  
    ```  
  
-   カスタム コード関数を使用して、式の値を返します。 次の例では、現在の値と前の値の差がパーセンテージで返されます。 これを使って、任意の 2 つの連続する値の差を計算でき、最初の比較 (前の値がない場合) のエッジ ケースと、前の値または現在の値のいずれかが **null** (Visual Basic では **Nothing**) であるケースが処理されます。  
  
    ```  
    Public Function GetDeltaPercentage(ByVal PreviousValue, ByVal CurrentValue) As Object  
        If IsNothing(PreviousValue) OR IsNothing(CurrentValue) Then  
            Return Nothing  
        Else if PreviousValue = 0 OR CurrentValue = 0 Then  
            Return Nothing  
        Else   
            Return (CurrentValue - PreviousValue) / CurrentValue  
        End If  
    End Function  
    ```  
  
     次の式に、"ColumnGroupByYear" コンテナーのテキスト ボックスからこのカスタム コードを呼び出す方法を示します (グループまたはデータ領域)。  
  
    ```  
    =Code.GetDeltaPercentage(Previous(Sum(Fields!Sales.Value),"ColumnGroupByYear"), Sum(Fields!Sales.Value))  
    ```  
  
     実行時例外の発生はこのようにして防ぐことができます。 テキスト ボックスの `=IIF(Me.Value < 0, "red", "black")` Color **プロパティで** のような式を使用し、その値が 0 より大きいか小さいかの条件に基づいて、テキストを表示できるようになりました。  
  
## <a name="next-steps"></a>次の手順

- [Power BI Premium のページ分割されたレポートとは](paginated-reports-report-builder-power-bi.md)
