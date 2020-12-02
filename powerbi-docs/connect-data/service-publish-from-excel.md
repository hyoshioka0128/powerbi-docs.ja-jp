---
title: Microsoft Excel から Power BI へ発行する
description: Excel ブックを Power BI サイトに発行する方法について説明します。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 05/05/2020
LocalizationGroup: Data from files
ms.openlocfilehash: 1473cdace4a1c6435ea7c2cf405785f144616d87
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410185"
---
# <a name="publish-to-power-bi-from-microsoft-excel"></a>Microsoft Excel から Power BI へ発行する
Microsoft Excel 2016 以降では、Excel ブックのデータに基づいて対話性の高いレポートやダッシュボードを作成できる [Power BI](https://powerbi.microsoft.com) ワークスペースに Excel ブックを直接発行できます。 これにより、分析情報を組織内のユーザーと共有できます。

![ブックを Power BI に発行する](media/service-publish-from-excel/pbi_uploadexport2.png)

ブックを Power BI に発行する場合、次の点に注意する必要があります。

* Office、OneDrive for Business (そこに保存したブックを使用する場合)、Power BI へのサインインに使用するアカウントは同じアカウントである必要があります。
* 空白のブックや、Power BI でサポートされているコンテンツが含まれていないブックを発行することはできません。
* 暗号化されたブック、パスワードで保護されたブック、または Information Protection Management が使用されているブックは発行できません。
* Power BI に発行するには、先進認証が有効 (既定値) になっている必要があります。 無効になっている場合、[ファイル] メニューの [発行] オプションは使用できません。

## <a name="publish-your-excel-workbook"></a>Excel ブックを発行する
Excel ブックを発行するには、Excel で **[ファイル]**  >  **[発行]** を選択し、 **[アップロード]** または **[エクスポート]** を選択します。

ブックを Power BI に **アップロード** すると、Excel Online を操作する場合と同様にブックを操作できます。 ブックから Power BI ダッシュボードに選択項目をピン留めすることや、Power BI を使用してブックや選択した要素を共有することができます。

**[エクスポート]** を選択した場合は、テーブル データとそのデータ モデルを Power BI データセットにエクスポートすることができ、これを使用して Power BI レポートとダッシュボードを作成できます。

### <a name="local-file-publishing"></a>ローカル ファイルの発行
Excel では、ローカルの Excel ファイルを発行することがサポートされています。 OneDrive for Business や SharePoint Online に保存する必要はありません。

> [!IMPORTANT]
> ローカル ファイルを発行できるのは、Microsoft 365 サブスクリプションで Excel 2016 (またはそれ以降) を使用している場合のみです。 Excel 2016 スタンドアロンのインストールで Power BI に発行できますが、ブックが OneDrive for Business または SharePoint Online に保存されている場合に限ります。
> 

**[発行]** を選択する際に、発行先のワークスペースを選択できます。 Excel ファイルが OneDrive for Business に存在する場合は、*マイ ワークスペース* にのみ発行できます。 Excel ファイルがローカル ドライブにある場合は、*マイ ワークスペース* またはアクセス権のある共有ワークスペースに発行できます。

![Power BI に発行する画面のスクリーンショット。マイ ワークスペースが選択されています。](media/service-publish-from-excel/pbi_choose_workspace.png)

Power BI でブックを取得する方法に関する 2 つのオプションがあります。

![発行画面のスクリーンショット。マイ ワークスペースが選択されています。](media/service-publish-from-excel/pbi_uploadexport3.png)

発行すると、発行したブックの内容がローカル ファイルとは別の Power BI にインポートされます。 Power BI でファイルを更新した場合は、更新したバージョンを再度発行する必要があります。または、ブックまたは Power BI のデータセットに対するスケジュールされた更新を構成して、データを更新することができます。

### <a name="publishing-from-a-standalone-excel-installation"></a>スタンドアロンの Excel インストールからの発行
スタンドアロンの Excel インストールから発行する場合は、ブックを OneDrive for Business に保存する必要があります。 **[クラウドに保存]** を選択し、OneDrive for Business 内の場所を選択します。

![OneDrive for Business への保存](media/service-publish-from-excel/pbi_savetoonedrive2.png)

OneDrive for Business にブックを保存してから **[発行]** を選択すると、Power BI でブックを取得する方法に関する 2 つのオプション ( **[アップロード]** または **[エクスポート]** ) が表示されます。

![Power BI 用オプション](media/service-publish-from-excel/pbi_uploadexport2.png)

#### <a name="upload-your-workbook-to-power-bi"></a>Power BI にブックをアップロード
**[アップロード]** オプションを選択すると、ブックは、Excel Online を使用しているときと同じように Power BI に表示されます。 ただし、Excel Online とは異なり、ワークシートの要素をダッシュボードにピン留めするのに役立ついくつかのオプションを利用できます。

Power BI ではブックを編集できません。 変更を加える必要がある場合は、 **[編集]** を選択して、Excel Online でブックを編集するかまたは自分のコンピューターの Excel で開くかを選択できます。 ブックに加えたすべての変更は、OneDrive for Business 上のブックに保存されます。

ブックを **アップロード** するとき、Power BI にデータセットは作成されません。 ブックは、ワークスペース ナビ ペインの [レポート] に表示されます。 Power BI にアップロードされたブックは、アップロード済みの Excel ブックであることを示す特殊な Excel アイコンで表示されます。

**[アップロード]** オプションは、データがワークシートにのみ存在する場合や、Power BI で表示したいピボットテーブルやグラフがある場合に選択します。

Excel の [Power BI への発行] から [アップロード] を使用することは、ブラウザーの Power BI から **[データの取得] > [ファイル] > [OneDrive for Business] > [Power BI で Excel に接続し、管理し、表示する]** を選択するのと同様のエクスペリエンスです。

#### <a name="export-workbook-data-to-power-bi"></a>Power BI にブックのデータをエクスポートする
**[エクスポート]** オプションを選択すると、テーブルやデータ モデル内のサポートされているデータがすべて、Power BI の新しいデータセットにエクスポートされます。 ブック内に Power View シートがある場合は、Power BI でレポートとして再作成されます。

ブックは引き続き編集できます。 変更を保存すると、通常約 1 時間以内に Power BI のデータセットと同期されます。 より迅速に更新する必要がある場合は、Excel からもう一度 **[発行]** を選択すると、変更が直ちにエクスポートされます。 レポートとダッシュボードの視覚エフェクトも更新されます。

**[発行]** オプションは、データの取得と変換機能または Power Pivot 機能を使用してデータをデータ モデルに読み込んでいる場合や、Power BI で表示したい視覚エフェクトが含まれる Power View シートがブックにある場合に選択します。

**[エクスポート]** を使用することは、ブラウザーの Power BI から **[データの取得] > [ファイル] > [OneDrive for Business] > [Export Excel data into Power BI]\(Excel データを Power BI にエクスポートする\)** を選択することとよく似ています。

## <a name="publishing"></a>発行
いずれかのオプションを選択すると、現在のアカウントで Power BI へのサインインが行われ、ブックが Power BI ワークスペースに発行されます。 Excel のステータス バーを監視して、発行プロセスの進行状況を確認できます。

![Power BI への発行のステータス バー](media/service-publish-from-excel/pbi_publishingstatus.png)

完了したら、Excel から Power BI に直接移動できます。

![Power BI に移動](media/service-publish-from-excel/pbi_gotopbi.png)

## <a name="next-steps"></a>次の手順
[Power BI の Excel データ](service-excel-workbook-files.md)  
他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。

