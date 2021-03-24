---
title: Q&A で質問するヒントとテクニック
description: Power BI の Q&A で質問するヒントとテクニック
author: mihart
ms.author: mihart
ms.reviewer: Mohammad.ali
ms.service: powerbi
ms.subservice: pbi-explore
ms.topic: how-to
ms.date: 09/23/2020
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 9902a88a6e2ff119aa9bc4ed3bfe3b42c2160df5
ms.sourcegitcommit: 644e5a3872f2a8e020fe44c4ec62a26ccc9a6a4e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2021
ms.locfileid: "105007824"
---
# <a name="tips-for-asking-questions-in-power-bi-qa"></a>Power BI Q&A で質問するためのヒント

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

## <a name="words-and-terminology-that-qa-recognizes"></a>Q&A で認識される語句と用語
このページにある一覧に含まれていないキーワードもあります。  Power BI でキーワードが認識されるかどうかを確認する最良の方法は、質問ボックスに入力して試してみることです。  語句または用語が灰色で表示されている場合、それは Power BI で認識されていません。

以下のリストでは現在形を使用していますが、ほとんどの場合はすべての時制が認識されます。 たとえば、"is" には **are**、**was**、**were**、**will be**、**have**、**has**、**had**、**will have**、**has got**、**do**、**does**、**did** が含まれます。  "sort" には **sorted** および **sorting** が含まれます。  また、Power BI では単語の単数形と複数形の両方が認識されます。 

> [!NOTE]
> [iPad、iPhone、iPod Touch デバイスの iOS 用の Microsoft Power BI アプリ](mobile/mobile-apps-ios-qna.md)で Q&A も利用できます。
>  


|カテゴリ  |キーワード  |
|---------|---------|
|**集計**     | total、sum、amount、number、quantity、count、average、most、least、fewest、largest、smallest、highest、biggest、maximum、max、greatest、lowest、littlest、minimum、min          |
**冠詞**     |  a、an、the              |
|**空白とブール値**     |   blank、empty、null、"non" または "non-" のプレフィックス付きの語句、empty string、empty text、true、t、false、f          |
|**比較**     |   vs、versus、compared to、compared with            |
|**接続詞**     |  and、or、each of、with、versus、&、and、but、nor、along with、in addition to       |
|**短縮系**     |  Q&A ではほぼあらゆる短縮形が認識されます。試してみてください。例: didn't、haven't、he'd、he's、isn't、it's、she'll、they'd、weren't、who's、won't、wouldn't          |
|**日付**     |       Power BI では、ほとんどの日付の用語 (day、week、month、year、quarter、decade など) と、さまざまな形式 (下記参照) で記述された日付が認識されます。 Power BI では、次のキーワードも認識されます:MonthName、Days 1-31、decade 例:January 3rd of 1995、January 3rd 1995、jan 03 1995、3 Jan 1995、the 3rd of January、January 1995、1995 January、1995-01、01/1995、月の名前         |
|**相対日付**     |   today、right now、current time、yesterday、tomorrow、the current、next、the coming、last、previous、ago、before now、sooner than、after、later than、from、at、on、from now、after now、in the future、past、last、previous、within、in、over、N days ago、N days from now、next、once、twice|
|    |  例: count of orders in the past 6 days (過去 6 日間の注文数)  |
|**等しさ (範囲)**     |   in、equal to、=、after、is more than、in、between、before  |
|  |例:Order year is before 2012? (注文した年が 2012 年より前であるか?) Price equals between 10 and 20? (価格が 10 と 20 の間に等しいか?)  Is the age of John greater than 40? (John の年齢は 40 より上か?)  Total sales in 200-300? (売上合計が 200-300 の範囲か?)              |
|**等しさ (値)**     |   is、equal、equal to、in、of、for、within、is in、is on |
|   | 例:Which products are green? (どの商品が緑ですか?) Order date equals 2012. (注文日が 2012 に等しい) Is the age of John 40? (John の年齢は 40 か?)  Total sales that aren't equal to 200? (200 に等しくない売上合計は?) Order date of 1/1/2016. (注文日が 1/1/2016)  10 in price? (価格が 10?) Green for color? (色は緑?) 10 in price? (価格が 10?)              |
|**名前**     |       データセット内の列に "name" (名) という語が含まれている場合 (EmployeeName (社員名) など)、Q&A ではその列の値が名前であると理解されます。 "which employees are named robert" (robert という名前の社員はどれか) のような質問をすることができます。          |
|**代名詞**  | he、him、himself、his、she、herself、her、hers、it、itself、its、they、their、them、themselves、theirs、this、these、that、those|
|**クエリ コマンド**     |    sorted、sort by、direction、group、group by、by、show、list、display、give me、name、just、only、arrange、rank、compare、to、with、against、alphabetically、ascending、descending、order             |
|**範囲**     |      greater、more、larger、above、over、>、less、smaller、fewer、below、under、<、at least、no less than、>=、at most、no more than、<=、in、between、in the range of、from、later、earlier、sooner、after、on、at、later than、after、since、starting with、starting from、ending with           |
|**時刻**  |am、pm、o'clock、noon、midnight、hour、minute、second、hh:mm:ss  |
|  |  例:10 pm、10:35 pm、10:35:15 pm、10 o clock、noon、midnight、hour、minute、second  |
|**上位 N**     |     (順序、順位付け): top、bottom、highest、lowest、first、last、next、earliest、newest、oldest、latest、most recent、next            |
|**ビジュアルの種類**     |  すべてのビジュアルの種類は Power BI に固有です。  [視覚化] ウィンドウのオプションである場合は質問に含めることができます。  このルールの例外は、[視覚化] ウィンドウに手動で追加した [Power BI カスタム ビジュアル](../developer/visuals/power-bi-custom-visuals.md)です。  |
|  |  例: show districts by month and sales total as bar chart (地区を月別および売上合計別に棒グラフとして示す)               |
|**Wh (関係、限定)**  | when、where、which、who、whom、how many、how much、how many times、how often、how frequently、amount、number、quantity、how long、what                |

## <a name="qa-helps-you-phrase-the-question"></a>Q&A は質問の言い回しの作成を手助けする
Q&A は、質問の内容を理解して回答するために、できる限りのことを行います。 また、いくつかの方法で実行されます。 どの言い回しについても、全部を採用するか、一部を採用するかは自由です。 質問を入力する過程で、Q&A は次のようなアクションをとります。

* 語句や質問をオートコンプリートします。 認識された単語のオートコンプリートや、保存されている質問、以前に適切な回答が返された質問など、さまざまな方法が使用されます。 複数のオートコンプリート オプションが使用可能な場合は、ドロップダウン リストとして表示されます。
* スペル チェックによる修正を加えます。
* 回答のプレビューがビジュアルの形式で提供されます。 質問を入力および編集すると (Enter キーを押さなくても)、ビジュアルが更新されます。
* カーソルを質問ボックスに戻すと、基になるデータセットから用語の置換が提案されます。
* 基になるデータセット内のデータに基づいて質問を言い換えます。 Q&A では、使われた語句が基になるデータセットの同意語に置き換えられます。 言い換えを読むことで、Q&A が質問を理解したかどうかを把握できます。 
* 理解できない語句に二重下線を追加します。
* 理解できた語句に一重下線を追加します。
* 用語が見つからない場合や、質問の結果が得られなかった場合は、レポートまたはダッシュボードの所有者に連絡できます。

## <a name="dont-stop-now"></a>これで終わりではありません
Q&A の結果が表示された後も、対話を続けてください。 ビジュアルと Q&A の対話型の機能を使用すると、さらに詳しい分析情報を得られます。

## <a name="next-steps"></a>次の手順
「[Power BI での Q&A](end-user-q-and-a.md)」に戻る  

[Power BI - 基本的な概念](end-user-basic-concepts.md)  

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。

