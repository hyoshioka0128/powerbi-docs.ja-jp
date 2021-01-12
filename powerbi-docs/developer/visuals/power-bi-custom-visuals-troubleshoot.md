---
title: 埋め込み BI 分析情報を向上させるための、Power BI 埋め込み分析で Power BI ビジュアルを開発する方法に関するトラブルシューティング
description: この記事では、Power BI カスタム ビジュアルの開発または作成時に発生する一般的な問題について説明します。 Power BI 埋め込み分析を使用して、より優れた埋め込み BI インサイトを有効にします。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: troubleshooting
ms.date: 11/06/2018
ms.openlocfilehash: 440bb6648dca1eaa85b697a10e9fd41180c66d7e
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888100"
---
# <a name="troubleshoot-power-bi-visuals"></a>Power BI ビジュアルのトラブルシューティング

## <a name="debug"></a>デバッグ

**Pbiviz コマンドが見つかりません (または類似のエラー)**

ターミナルのコマンド ラインで `pbiviz` を実行すると、ヘルプ画面が表示されるはずです。 ヘルプ画面が表示されない場合、コマンドは正しくインストールされていません。 バージョン 4.0 以降の NodeJS がインストールされていることを確認します。

**[視覚化] タブで "ビジュアルのデバッグ" が見つかりません**

"ビジュアルのデバッグ" は、[**視覚化**] タブ内でプロンプト アイコンのように表示されます。

![ビジュアルの選択](media/power-bi-custom-visuals-troubleshoot/powerbi-developer-visual-selection.png)

表示されない場合は、Power BI の設定内で有効にされていることを確認してください。

> [!NOTE]
> ビジュアルのデバッグ機能は、現時点では、Power BI サービスでのみ使用可能で、Power BI Desktop とモバイル アプリでは使用できません。 パッケージ化したビジュアルはあらゆる場所で機能します。

**ビジュアル サーバーに接続できません**

ビジュアル プロジェクトのルートから、ターミナルのコマンド ラインで `pbiviz start` コマンドを使用してビジュアル サーバーを実行します。 サーバーが動作していない場合、SSL 証明書が正しくインストールされていない可能性があります。

ご質問、ご意見、問題がございましたら、Power BI ビジュアルのサポート チーム (pbicvsupport@microsoft.com) までお気軽にお問い合わせください。

## <a name="next-steps"></a>次のステップ

詳細については、「[Power BI ビジュアルに関してよく寄せられる質問](power-bi-custom-visuals-faq.md#organizational-power-bi-visuals)」を参照してください。