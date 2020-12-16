---
title: ページ分割されたレポートの URL パラメーター - Power BI レポート ビルダー
description: URL にパラメーターを追加することによって Power BI のページ分割されたレポートにコマンドを送信する方法について説明します。これは、メールまたは Web ページに含めることができます。
author: maggiesMSFT
ms.author: maggies
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.reviewer: cfinlan
ms.custom: ''
ms.date: 12/15/2020
ms.openlocfilehash: 4dc7d3dbb68a06f1b18714d2070b7c305390ef6b
ms.sourcegitcommit: fef29a5c5bf1e0dae663c42c9ce5ae50e29ae9be
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/16/2020
ms.locfileid: "97558472"
---
# <a name="url-parameters-in-paginated-reports-in-power-bi"></a>Power BI のページ分割されたレポートの URL パラメーター

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

URL にパラメーターを追加することで、Power BI のページ分割されたレポートにコマンドを送信できます。 たとえば、特定のレポート パラメーター値セットを使用してレポートを表示しているとします。 定義済みの URL アクセス パラメーターを使用して、URL にこの情報をカプセル化します。 さらに、レンダリング フォーマットやレポート ツールバーの外観と雰囲気のパラメーターを埋め込んで Power BI のレポートの処理方法をカスタマイズします。 次に、この URL をメールまたは Web ページに直接貼り付けて、他のユーザーがブラウザーで同じ方法でレポートを使用できるようにします。 

URL アクセス パラメーターを使用して実行できるアクションを次に示します。 

- レポート パラメーターをレポートに送信します。 
- サポートされているファイル形式でレポート コンテンツのエクスポートを開始します。 
- パラメーター ウィンドウの表示と非表示を切り替えます。 
- DeviceInfo 設定を指定します。 

URL アクセスで使用できるコマンドと設定の詳細な一覧については、この記事で後述する  [URL アクセス パラメーターのリファレンス](#url-access-parameter-reference)に関する記事を参照してください。 

## <a name="url-access-concepts"></a>URL アクセスの概念 

Power BI への URL 要求には、サービスによって処理されるパラメーターが含まれます。 サービスによって URL 要求が処理される方法は、URL に含まれるパラメーター、パラメーターのプレフィックス、および項目の種類によって変わります。 ページ分割されたレポートの URL 機能は、標準的な URL アドレス指定をサポートするほとんどのブラウザーやアプリケーションと互換性があります。 

## <a name="url-access-syntax"></a>URL アクセスの構文 

URL 要求には、任意の順序で列挙した複数のパラメーターを含めることができます。 複数のパラメーターはアンパサンド (&) で区切られます。 名前と値のペアは等号 (=) で区切られます。 例:

```
powerbiserviceurl?rp:parametervalueh&rdl:parameter=value  
```

## <a name="syntax-description"></a>構文の説明 

### <a name="powerbiserviceurl"></a>powerbiserviceurl 

Power BI テナントの Web サービス URL。 例: 

**&** URL アクセス パラメーターの名前と値のペアを区切るために使用されます。

**プレフィックス** Power BI サービスのアクションを指定する URL パラメーターのプレフィックス (たとえば、rp: または rdl:)。 

> [!NOTE]
> レポート パラメーターにはパラメーターのプレフィックスが必要であり、大文字と小文字が区別されます。 

**パラメーター** パラメーター名。 

### <a name="value"></a>値 

使用されるパラメーターの値に対応する URL テキスト。 

URL でレポート パラメーターを渡す例については、 [URL 内でレポート パラメーターを渡す](report-builder-url-pass-parameters.md)方法に関する記事を参照してください。

## <a name="url-access-parameter-reference"></a>URL アクセス パラメーターのリファレンス

次のパラメーターを URL の一部として使用すると、Power BI のページ分割されたレポートの外観と雰囲気を構成できます。 このセクションでは、最も一般的なパラメーターについて説明します。 パラメーターは大文字と小文字が区別されず、出力形式に関連する場合はパラメーター プレフィックス  `rdl:`  で始まります。  

### <a name="report-commands-rdl"></a>レポート コマンド (`rdl:`) 

**エクスポート形式** レポートをレンダリングおよびエクスポートする形式を指定します。

例: rdl:format=PDF

使用可能な値は次のとおりです。
 
- PPTX (PowerPoint)
- MHTML 
- イメージ 
- EXCELOPENXML (Excel) 
- WORDOPENXML (Word) 
- CSV 
- PDF 
- ACCESSIBLEPDF (PDF)
- XML 

**レポート ビュー** レポートを表示するために使用するビューの種類を指定します。

-   rdl:reportView

    - 'interactive' (既定値): 対話型モードでレポートを読み込みます。
    - 'pageView': ページ ビュー モードでレポートを読み込みます。

**パラメーター パネル** レポートの読み込み時にパラメーター パネルを閉じるか、開くか、または完全に非表示にするかを指定します。

-   rdl:parameterPanel

    - 'collapsed': パラメーター パネルが閉じられた状態でレポートを読み込みます。 ユーザーがボタンをクリックして展開できるように、パラメーター ボタンが有効になっています。
    - 'hidden': パラメーター パネルが閉じられ、パラメーター ボタンが無効な状態でレポートを読み込みます。
    - 'expanded' (既定値): パラメーター パネルが開かれ、パラメーター ボタンが有効な状態でレポートを読み込みます。

**デバイス情報** 次のエクスポート形式に対して追加の出力パラメーターを指定できます。 

PDF / ACCESSIBLEPDF:

- rdl:AccessiblePDF=true/false
- rdl:Columns=integer
- rdl:ColumnSpacing=decimal(in)
- rdl:DpiX=integer
- rdl:DpiY=integer
- rdl:EndPage=integer
- rdl:HumanReadablePDF=true/false
- rdl:MarginBottom=decimal(in)
- rdl:MarginLeft=decimal(in)
- rdl:MarginRight=decimal(in)
- rdl:MarginTop=decimal(in)
- rdl:PageHeight=decimal(in)
- rdl:PageWidth=decimal(in)
    - rdl:StartPage=integer
    
CSV:

- rdl:Encoding=string
- rdl:ExcelMode=true/false
- rdl:FieldDelimiter=string
- rdl:NoHeader=true/false
- rdl:Qualifier=string
- rdl:RecordDelimiter=string
- rdl:SuppressLineBreaks=true/false
    - rdl:UseFormattedValues=true/false
    
WORDOPENXML (WORD):

- rdl:AutoFit=string -> True/False/Never/Default
- rdl:ExpandToggles=true/false
- rdl:FixedPageWidth=true/false
- rdl:OmitHyperlinks=true/false
- rdl:OmitDrillthroughs=true/false

EXCELOPENXML (EXCEL):

- rdl:OmitDocumentMap=true/false
- rdl:OmitFormulas=true/false
    - rdl:SimplePageHeaders=true/false
    
PPTX (PowerPoint):
 
- rdl:Columns=integer
- rdl:ColumnSpacing=decimal(in)
- rdl:DpiX=integer
- rdl:DpiY=integer
- rdl:EndPage=integer
- rdl:MarginBottom=decimal(in)
- rdl:MarginLeft=decimal(in)
- rdl:MarginRight=decimal(in)
- rdl:MarginTop=decimal(in)
- rdl:PageHeight=decimal(in)
- rdl:PageWidth=decimal(in)
- rdl:StartPage=integer
    - rdl:UseReportPageSize=true/false

XML:

- rdl:UseFormattedValues=true/false
- rdl:Indented=true/false
- rdl:OmitNamespace=true/false
- rdl:OmitSchema=true/false
- rdl:Encoding=string
- rdl:Schema=true/false

**同じブラウザー ウィンドウでハイパーリンクを開く** レポートのハイパーリンク URL に 'rdl:targetSameWindow=true' を追加すると、Power BI ではこのハイパーリンクを同じブラウザー ウィンドウで開くようにすることができます。 レポートにハイパーリンクを追加する方法の詳細については、SQL Server Reporting Services のドキュメント内の [URL へのハイパーリンクの追加](/sql/reporting-services/report-design/add-a-hyperlink-to-a-url-report-builder-and-ssrs)に関するページを参照してください。

## <a name="next-steps"></a>次の手順

- [Power BI のページ分割されたレポートの URL 内でレポート パラメーターを渡す](report-builder-url-pass-parameters.md)
- [Power BI Premium のページ分割されたレポートとは](paginated-reports-report-builder-power-bi.md)
