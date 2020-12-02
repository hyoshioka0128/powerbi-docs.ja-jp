---
title: Power BI Q&A の制限事項
description: Power BI Q&A の現在の制限事項
author: maggiesMSFT
ms.author: maggies
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 09/09/2020
ms.openlocfilehash: 6ad81bc88ee559fa08400b5ed8a74dd1a9b6051f
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410024"
---
# <a name="limitations-of-power-bi-qa"></a>Power BI Q&A の制限事項

Power BI Q&A には現在いくつかの制限事項があります。

## <a name="data-sources"></a>データ ソース

### <a name="supported-data-sources"></a>サポートされるデータ ソース

Power BI Q&A では、Power BI サービスにおけるデータ ソースの次の構成をサポートしています。

- Import モード
- Analysis Services へのライブ接続
- SQL Server Analysis Services へのライブ接続 (ゲートウェイを使用)
- Power BI データセット。

これらの各構成では、行レベルのセキュリティもサポートされています。

**Q&A の DirectQuery サポート** (プレビュー)

SQL Server 2019、Azure SQL Database、Azure Synapse Analytics などの SQL DirectQuery ソースが、Q&A でサポートされるようになりました。 Q&A を使用すれば、これらのデータ ソースに対して自然言語の質問をすることができます。 DirectQuery モードのときの Q&A の動作には少し変更が加えられています。質問を入力したら、 **[送信]** ボタンを選択します。 この変更により、入力時に不要なクエリで DirectQuery ソースが過負荷になるのを防ぐことができます。

その他の DirectQuery ソースは、Q&A によってサポートされていません。 ご利用のデータセット内に他の DirectQuery ソースが含まれていても、Microsoft が Q&A を完全にブロックすることはありませんが、質問によっては正しい回答が得られなかったり、エラーが返されたりする場合があります。

### <a name="data-sources-not-supported"></a>サポートされていないデータ ソース

Power BI Q&A では、現在、次の構成はサポートされていません。

- オブジェクト レベルのセキュリティ (データ ソースの種類を問わず)
- 複合モデル
- Reporting Services 

## <a name="tooling-limitations"></a>ツールの制限事項

新しいツール ダイアログでは、ユーザーは Q&A の自然言語をカスタマイズおよび改善できます。 ツールの詳細については、[Q&A ツールの概要](q-and-a-tooling-intro.md)に関するページを参照してください。

## <a name="review-question-limitations"></a>[質問の確認] の制限事項

[質問の確認] では、実際のデータ モデルに対して寄せられた質問のみが最長 28 日間保存されます。 新しい [質問の確認] 機能を使用すると、一部の質問が記録されないことがあります。 これらは仕様により記録されません。自然言語エンジンは、ユーザーによるすべてのキー ストロークが記録および表示されないようにするために、一連のデータ クレンジング手順を実行するからです。

Power BI 管理者は、テナント設定を使用して、質問の保存機能を管理できます。 アクセス許可は、セキュリティ グループに基づいています。 

また、ユーザーは、 **[設定]**  >  **[全般]** の順に選択し、 **[Allow Q&A to record my utterance]\(Q&A で自分の発話を記録することを許可する\)** の選択を解除することで、自分の質問が記録されないようにすることもできます。 

## <a name="teach-qa-limitations"></a>[Q&A の学習] の制限事項

[Q&A の学習] を使用すると、次の 2 種類のエラーを修正できます。

- フィールドに単語を割り当てる。
- フィルター条件に単語を割り当てる。

現在、認識された用語の再定義に加え、その他の種類の条件や語句の定義はサポートされていません。 また、フィルター条件を定義するときは、次のような言語の限られたサブセットのみを使用できます。

- Country which is USA
- Country which is not USA
- Products > 100
- Products greater than 100
- Products = 100
- Products is 100
- Products < 100
- Products smaller than 100

> [!NOTE]
> Q&A ツールでは、インポート モードのみがサポートされています。 オンプレミスおよび Azure Analysis Services のデータ ソースへの接続はまだサポートされていません。 この現在の制限は、Power BI の今後のリリースでは削除される予定です。

### <a name="statements-not-supported"></a>サポートされないステートメント

- 複数の条件はサポートされていません。 回避策として、複数条件ステートメントのブール値を評価する DAX 計算列を作成し、このフィールドを代わりに使用します。
- Q&A からデータのサブセットの指定を求められたときにフィルター条件を指定しないと、ステートメント全体に赤色の下線が表示されていない場合でも、定義を保存することはできません。

## <a name="next-steps"></a>次のステップ

自然言語エンジンを強化するためのベスト プラクティスがいくつかあります。 詳細については、「[Q&A ベスト プラクティス](q-and-a-best-practices.md)」を参照してください。
