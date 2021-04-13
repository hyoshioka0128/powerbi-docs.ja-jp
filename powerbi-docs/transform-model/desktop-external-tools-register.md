---
title: Power BI Desktop で外部ツールを登録する
description: Power BI Desktop で外部ツールを登録する方法について説明します。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 03/25/2021
LocalizationGroup: Create reports
ms.openlocfilehash: 519f62f659e78dec765a57f3f5e6864bc46f0353
ms.sourcegitcommit: adbbffc74521c76eb3ad8de92b803785b94c34ee
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "105938038"
---
# <a name="register-an-external-tool"></a>外部ツールを登録する

一部のツールは Power BI Desktop に手動で登録する必要があります。 外部ツールを登録するには、次の内容で JSON ファイルを作成します。

```json
{
    "name": "<tool name>",
    "description": "<tool description>",
    "path": "<tool executable path>",
    "arguments": "<optional command line arguments>",
    "iconData": "image/png;base64,<encoded png icon data>"
}
```

pbitool.json ファイルには、次の要素が含まれています。
 
* **name:** ツールの名前を指定します。これは Power BI Desktop 内の [外部ツール] リボンに、ボタンのキャプションとして表示されます。
* **description:** (省略可能) 説明を指定します。これは Power BI Desktop 内の [外部ツール] リボンのボタンに、ヒントとして表示されます。
* **path:** ツールの実行可能ファイルへの完全修飾パスを指定します。
* **arguments:** (省略可能) ツールの実行可能ファイルの起動時に指定する必要があるコマンド ライン引数の文字列を指定します。 次の任意のプレースホルダーを使用できます。
    * **%server%:** インポートされた、または DirectQuery のデータ モデルに対する Analysis Services 表形式のローカル インスタンスのサーバー名とポート番号に置き換えられます。
    * **%database%:** インポートされた、または DirectQuery のデータ モデルに対する Analysis Services 表形式のローカル インスタンスでホストされるモデルのデータベース名に置き換えられます。
* **iconData:** Power BI Desktop 内の [外部ツール] リボンにボタン アイコンとして表示される画像データを指定します。 文字列は、データ URI の構文から "data:" プレフィックスを除いた形式にする必要があります。

ファイルに `"<tool name>.pbitool.json"` という名前を付け、次のフォルダーに配置します。

- `%commonprogramfiles%\Microsoft Shared\Power BI Desktop\External Tools`

64 ビット環境の場合は、次のフォルダーにファイルを配置します。

- **Program Files (x86)\Common Files\Microsoft Shared\Power BI Desktop\External Tools**

この指定した場所にある **.pbitool.json** 拡張子を持つファイルが、Power BI Desktop によって起動時に読み込まれます。

## <a name="example"></a>例

次の *.pbitool.json ファイルでは、[外部ツール] リボンから powershell.exe を起動し、pbiToolsDemo.ps1 という名前のスクリプトを実行して、-Server パラメーターでサーバー名とポート番号を、-Database パラメーターでデータセット名を渡します。

```json
{ 
    "version": "1.0.0", 
    "name": "External Tools Demo", 
    "description": "Launches PowerShell and runs a script that outputs server and database parameters. (Requires elevated PowerShell permissions.)", 
    "path": "C:\\Windows\\System32\\WindowsPowerShell\\v1.0\\powershell.exe", 
    "arguments": "C:\\pbiToolsDemo.ps1 -Server \"%server%\" -Database \"%database%\"", 
    "iconData": "image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAADsEAAA7BAbiRa+0AAAANSURBVBhXY/jH9+8/AAciAwpql7QkAAAAAElFTkSuQmCC" 
} 
```

対応する pbiToolsDemo.ps1 スクリプトでは、Server および Database パラメーターをコンソールに出力します。

```powershell
[CmdletBinding()] 
param 
( 
        [Parameter(Mandatory = $true)]         
[string] $Server, 
        [Parameter(Mandatory = $true)]         
[string] $Database   
) 
Write-Host "" 
Write-Host "Analysis Services instance: " -NoNewline 
Write-Host "$Server" -ForegroundColor Yellow 
Write-Host "Dataset name: " -NoNewline 
Write-Host "$Database" -ForegroundColor Green 
Write-Host "" 
Read-Host -Prompt 'Press [Enter] to close this window'  
```

:::image type="content" source="media/desktop-external-tools-register/json-example-output.png" border="false" alt-text="PowerShell コンソールの出力":::

## <a name="icon-data-uris"></a>アイコンのデータ URI

[外部ツール] リボンにアイコンを含めるには、pbitool.json 登録ファイルに iconData 要素を含める必要があります。

:::image type="content" source="media/desktop-external-tools-register/tool-ribbon.png" alt-text="[外部ツール] リボンとツール アイコン":::

iconData 要素は、**data:** プレフィックスのないデータ URI を受け取ります。 たとえば、1 ピクセルのマゼンタ png 画像のデータ URI は次のようになります。

`data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAADsEAAA7BAbiRa+0AAAANSURBVBhXY/jH9+8/AAciAwpql7QkAAAAAElFTkSuQmCC`

前の pbitool.json の例に示すように、**data:** プレフィックスは必ず削除してください。

.png またはその他の画像ファイルの種類をデータ URI に変換するには、次の C# コード スニペットに示されているようなオンライン ツールまたはカスタム ツールを使用します。

```c#
string ImageDataUri; 
OpenFileDialog openFileDialog1 = new OpenFileDialog(); 
openFileDialog1.Filter = "PNG Files (.png)|*.png|All Files (*.*)|*.*"; 
openFileDialog1.FilterIndex = 1; 
openFileDialog1.Multiselect = false; 
openFileDialog1.CheckFileExists = true; 
bool? userClickedOK = openFileDialog1.ShowDialog(); 
if (userClickedOK == true) 
{ 
    var fileName = openFileDialog1.FileName; 
    var sb = new StringBuilder(); 
    sb.Append("image/") 
        .Append((System.IO.Path.GetExtension(fileName) ?? "png").Replace(".", "")) 
        .Append(";base64,") 
        .Append(Convert.ToBase64String(File.ReadAllBytes(fileName))); 
    ImageDataUri = sb.ToString(); 
} 
```

## <a name="see-also"></a>関連項目

[Power BI Desktop での外部ツール](desktop-external-tools.md)  
[Analysis Services に接続するためのクライアント ライブラリ](/analysis-services/client-libraries?view=power-bi-premium-current&preserve-view=true)  
[表形式オブジェクト モデル (TOM)](/analysis-services/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo?view=power-bi-premium-current&preserve-view=true)  
