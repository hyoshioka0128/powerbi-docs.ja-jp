---
title: Power BI ビジュアル プロジェクトの構造
description: この記事では、Power BI ビジュアル プロジェクトのフォルダーとファイルの構造について説明します。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 01/12/2020
ms.openlocfilehash: df7a2909e3ccd745fdaa990ba5281a723ef6360d
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96416717"
---
# <a name="power-bi-visual-project-structure"></a>Power BI ビジュアル プロジェクトの構造

新しい Power BI ビジュアルを作り始める場合は、Power BI ビジュアル [pbiviz](https://www.npmjs.com/package/powerbi-visuals-tools) ツールを使用することをお勧めします。

新しいビジュアルを作成するには、Power BI ビジュアルを配置するディレクトリに移動し、次のコマンドを実行します。

`pbiviz new <visual project name>`

このコマンドを実行すると、次のファイルを含む Power BI ビジュアル フォルダーが作成されます。

```markdown
project
├───.vscode
│   ├───launch.json
│   └───settings.json
├───assets
│   └───icon.png
├───node_modules
├───src
│   ├───settings.ts
│   └───visual.ts
├───style
│   └───visual.less
├───capabilities.json
├───package-lock.json
├───package.json
├───pbiviz.json
├───tsconfig.json
└───tslint.json
```

## <a name="folder-and-file-description"></a>フォルダーとファイルの説明

このセクションでは、Power BI ビジュアルの **pbiviz** ツールを使って作成されるディレクトリ内の各フォルダーとファイルについて説明します。  

### <a name="vscode"></a>.vscode

このフォルダーには、VS Code プロジェクトの設定が含まれています。

ワークスペースを構成するには、`.vscode/settings.json` ファイルを編集します。

詳細については、「[ユーザーとワークスペースの設定](https://code.visualstudio.com/docs/getstarted/settings)」を参照してください。

### <a name="assets"></a>資産

このフォルダーには `icon.png` ファイルが含まれています。

Power BI ビジュアル ツールでは、このファイルが Power BI ビジュアル ペインの新しい Power BI ビジュアル アイコンとして使用されます。

### <a name="src"></a>src

このフォルダーには、ビジュアルのソース コードが含まれています。

このフォルダーには、Power BI ビジュアル ツールによって次のファイルが作成されます。
* `visual.ts` - ビジュアルの主要なソース コード。
* `settings.ts` - ビジュアルの設定のコード。 ファイルのクラスには、[ビジュアルのプロパティ](./objects-properties.md#properties)を定義するためのインターフェイスが用意されています。

### <a name="style"></a>スタイル

このフォルダーには、ビジュアルのスタイルを保持する `visual.less` ファイルが含まれています。

### <a name="capabilitiesjson"></a>capabilities.json

このファイルには、ビジュアルの主なプロパティと設定 (または[機能](./capabilities.md)) が含まれています。 これにより、ビジュアルは、サポートされている機能、オブジェクト、プロパティ、[データ ビュー マッピング](./dataview-mappings.md)を宣言できます。

### <a name="package-lockjson"></a>package-lock.json

このファイルは、*npm* によって `node_modules` ツリーまたは `package.json` ファイルのいずれかが変更されるすべての操作に対して、自動的に生成されます。

このファイルの詳細については、公式の [npm-package-lock.json](https://docs.npmjs.com/files/package-lock.json) のドキュメントを参照してください。

### <a name="packagejson"></a>package.json

このファイルには、プロジェクト パッケージが記述されています。 作成者、説明、プロジェクトの依存関係などのプロジェクトに関する情報が含まれます。

このファイルの詳細については、公式の [npm-package.json](https://docs.npmjs.com/files/package.json.html) のドキュメントを参照してください。

### <a name="pbivizjson"></a>pbiviz.json

このファイルには、ビジュアルのメタデータが含まれています。

メタデータ エントリを説明するコメントを含む `pbiviz.json` ファイルの例については、「[メタデータ エントリ](#metadata-entries)」セクションを参照してください。

### <a name="tsconfigjson"></a>tsconfig.json

[TypeScript](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) の構成ファイルです。

このファイルには、`pbiviz.json` ファイルの `visualClassName` プロパティに指定されているように、ビジュアルのメイン クラスが配置されている **\*.ts** ファイルのパスが含まれている必要があります。

### <a name="tslintjson"></a>tslint.json

このファイルには [TSLint の構成](https://palantir.github.io/tslint/usage/configuration/)が含まれています。

## <a name="metadata-entries"></a>メタデータ エントリ

`pbiviz.json` ファイルの次のコード キャプションのコメントは、メタデータ エントリを説明するものです。

> [!NOTE]
> * **pbiviz** ツールのバージョン 3.x.x から、`externalJS` はサポートされません。
> * ローカライズをサポートするには、[ビジュアルに Power BI ロケールを追加します](./localization.md)。

```json
{
  "visual": {
     // The visual's internal name.
    "name": "<visual project name>",

    // The visual's display name.
    "displayName": "<visual project name>",

    // The visual's unique ID.
    "guid": "<visual project name>23D8B823CF134D3AA7CC0A5D63B20B7F",

    // The name of the visual's main class. Power BI creates the instance of this class to start using the visual in a Power BI report.
    "visualClassName": "Visual",

    // The visual's version number.
    "version": "1.0.0",
    
    // The visual's description (optional)
    "description": "",

    // A URL linking to the visual's support page (optional).
    "supportUrl": "",

    // A link to the source code available from GitHub (optional).
    "gitHubUrl": ""
  },
  // The version of the Power BI API the visual is using.
  "apiVersion": "2.6.0",

  // The name of the visual's author and email.
  "author": { "name": "", "email": "" },

  // 'icon' holds the path to the icon file in the assets folder; the visual's display icon.
  "assets": { "icon": "assets/icon.png" },

  // Contains the paths for JS libraries used in the visual.
  // Note: externalJS' isn't used in the Power BI visuals tool version 3.x.x or higher.
  "externalJS": null,

  // The path to the 'visual.less' style file.
  "style": "style/visual.less",

  // The path to the `capabilities.json` file.
  "capabilities": "capabilities.json",

  // The path to the `dependencies.json` file which contains information about R packages used in R based visuals.
  "dependencies": null,

  // An array of paths to files with localizations.
  "stringResources": []
}
```

## <a name="next-steps"></a>次の手順

* ビジュアル、ユーザー、および Power BI 間の相互作用を理解するには、「[Power BI ビジュアルの概念](./power-bi-visuals-concept.md)」を参照してください。

* [ステップ バイ ステップ ガイド](./develop-circle-card.md)を使って、独自の Power BI ビジュアルをゼロから開発しましょう。
