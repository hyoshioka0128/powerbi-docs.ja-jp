---
title: 埋め込み BI 分析情報を向上させるため、Power BI 埋め込み分析でデータセットを作成する
description: チュートリアル - データセットにデータをプッシュする - Power BI でデータセットを作成する。 Power BI 埋め込み分析を使用して、より優れた埋め込み BI インサイトを有効にします。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: madia
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: tutorial
ms.date: 02/05/2019
ms.openlocfilehash: e2f1bbd1503ca4adeac626d02fc7bf3e41baa9b5
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887502"
---
# <a name="step-3-create-a-dataset-in-power-bi"></a>手順 3:Power BI でデータセットを作成する
この記事は、チュートリアル「[データセットにデータをプッシュする](walkthrough-push-data.md)」の一部です。

チュートリアル「データセットにデータをプッシュする」の **手順 2**「[認証アクセス トークンを取得する](walkthrough-push-data-get-token.md)」では、**Azure AD** に対する認証トークンを取得しました。 この手順では、そのトークンを使って [PostDataset](/rest/api/power-bi/pushdatasets) 操作を呼び出します。

REST リソースを呼び出すには、リソースを指定する URL を使って、Power BI サービス リソースに JavaScript Object Notation (JSON) 文字列 (データセットを記述したもの) を送信します。 REST リソースは、Power BI サービスのうち操作する部分を識別します。 データセットにデータをプッシュする場合、対象のリソースは **データセット** です。 データセットを識別する URL は、 `https://api.PowerBI.com/v1.0/myorg/datasets` です。 グループ内にデータをプッシュする場合の URL は、 `https://api.PowerBI.com/v1.0/myorg/groups/{group_id}/datasets` です。

Power BI REST 操作を認証するには、[認証アクセス トークンを取得する](walkthrough-push-data-get-token.md)手順で入手したトークンを要求ヘッダーに追加します。

[PostDataset](/rest/api/power-bi/pushdatasets) 操作を呼び出すと、新しいデータセットが作成されます。 

![データセットの作成](media/walkthrough-push-data-create-dataset/powerbi-developer-create-dataset.png)

Power BI でデータセットを作成する手順は次のとおりです。

## <a name="create-a-dataset-in-power-bi"></a>Power BI でデータセットを作成する
> [!NOTE]
> 作業を開始する前に、チュートリアル「[データセットにデータをプッシュする](walkthrough-push-data.md)」の前の手順を完了してください。
> 
> 

1. 「[手順 2: 認証アクセス トークンを取得する](walkthrough-push-data-get-token.md)」で作成したコンソール アプリケーション プロジェクトで、Program.cs に「**using System.Net;** 」と「**using System.IO;** 」を追加します。
2. Program.cs に、以下のコードを追加します。
3. コンソール アプリを実行し、Power BI アカウントにログインします。 コンソール ウィンドウに、 **作成されたデータセット** が表示されるはずです。 また、Power BI にログインして、新しいデータセットを表示することもできます。

**データセットにデータをプッシュするサンプル**

このコードを Program.cs に追加します。

* static void Main(string[] args) では、以下のように入力します。
  
    ```csharp
    static void Main(string[] args)
    {
        //Get an authentication access token
        token = GetToken();
  
        //Create a dataset in Power BI
        CreateDataset();
    }
    ```
* CreateDataset() メソッドを追加します。
  
    ```csharp
    #region Create a dataset in Power BI
    private static void CreateDataset()
    {
        //TODO: Add using System.Net and using System.IO
  
        string powerBIDatasetsApiUrl = "https://api.powerbi.com/v1.0/myorg/datasets";
        //POST web request to create a dataset.
        //To create a Dataset in a group, use the Groups uri: https://api.PowerBI.com/v1.0/myorg/groups/{group_id}/datasets
        HttpWebRequest request = System.Net.WebRequest.Create(powerBIDatasetsApiUrl) as System.Net.HttpWebRequest;
        request.KeepAlive = true;
        request.Method = "POST";
        request.ContentLength = 0;
        request.ContentType = "application/json";
  
        //Add token to the request header
        request.Headers.Add("Authorization", String.Format("Bearer {0}", token));
  
        //Create dataset JSON for POST request
        string datasetJson = "{\"name\": \"SalesMarketing\", \"tables\": " +
            "[{\"name\": \"Product\", \"columns\": " +
            "[{ \"name\": \"ProductID\", \"dataType\": \"Int64\"}, " +
            "{ \"name\": \"Name\", \"dataType\": \"string\"}, " +
            "{ \"name\": \"Category\", \"dataType\": \"string\"}," +
            "{ \"name\": \"IsCompete\", \"dataType\": \"bool\"}," +
            "{ \"name\": \"ManufacturedOn\", \"dataType\": \"DateTime\"}" +
            "]}]}";
  
        //POST web request
        byte[] byteArray = System.Text.Encoding.UTF8.GetBytes(datasetJson);
        request.ContentLength = byteArray.Length;
  
        //Write JSON byte[] into a Stream
        using (Stream writer = request.GetRequestStream())
        {
            writer.Write(byteArray, 0, byteArray.Length);
  
            var response = (HttpWebResponse)request.GetResponse();
  
            Console.WriteLine(string.Format("Dataset {0}", response.StatusCode.ToString()));
  
            Console.ReadLine();
        }
    }
    #endregion
    ```

次の手順では、[Power BI テーブルに行を追加するためにデータセットを取得する](walkthrough-push-data-get-datasets.md)方法を説明します。

以下は、[完全なコード リスト](#code)です。

<a name="code"/>

## <a name="complete-code-listing"></a>完全なコード リスト

```csharp
using System;
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using System.Net;
using System.IO;

namespace walkthrough_push_data
{
    class Program
    {
        private static string token = string.Empty;

        static void Main(string[] args)
        {

            //Get an authentication access token
            token = GetToken();

            //Create a dataset in Power BI
            CreateDataset();

        }

        #region Get an authentication access token
        private static string GetToken()
        {
            // TODO: Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612
            // and add using Microsoft.IdentityModel.Clients.ActiveDirectory

            //The client id that Azure AD created when you registered your client app.
            string clientID = "{Client_ID}";

            //RedirectUri you used when you register your app.
            //For a client app, a redirect uri gives Azure AD more details on the application that it will authenticate.
            // You can use this redirect uri for your client app
            string redirectUri = "https://login.live.com/oauth20_desktop.srf";

            //Resource Uri for Power BI API
            string resourceUri = "https://analysis.windows.net/powerbi/api";

            //OAuth2 authority Uri
            string authorityUri = "https://login.microsoftonline.com/common/";

            //Get access token:
            // To call a Power BI REST operation, create an instance of AuthenticationContext and call AcquireToken
            // AuthenticationContext is part of the Active Directory Authentication Library NuGet package
            // To install the Active Directory Authentication Library NuGet package in Visual Studio,
            //  run "Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory" from the nuget Package Manager Console.

            // AcquireToken will acquire an Azure access token
            // Call AcquireToken to get an Azure token from Azure Active Directory token issuance endpoint
            AuthenticationContext authContext = new AuthenticationContext(authorityUri);
            string token = authContext.AcquireToken(resourceUri, clientID, new Uri(redirectUri)).AccessToken;

            Console.WriteLine(token);
            Console.ReadLine();

            return token;
        }

        #endregion


        #region Create a dataset in Power BI
        private static void CreateDataset()
        {
            //TODO: Add using System.Net and using System.IO

            string powerBIDatasetsApiUrl = "https://api.powerbi.com/v1.0/myorg/datasets";
            //POST web request to create a dataset.
            //To create a Dataset in a group, use the Groups uri: https://api.PowerBI.com/v1.0/myorg/groups/{group_id}/datasets
            HttpWebRequest request = System.Net.WebRequest.Create(powerBIDatasetsApiUrl) as System.Net.HttpWebRequest;
            request.KeepAlive = true;
            request.Method = "POST";
            request.ContentLength = 0;
            request.ContentType = "application/json";

            //Add token to the request header
            request.Headers.Add("Authorization", String.Format("Bearer {0}", token));

            //Create dataset JSON for POST request
            string datasetJson = "{\"name\": \"SalesMarketing\", \"tables\": " +
                "[{\"name\": \"Product\", \"columns\": " +
                "[{ \"name\": \"ProductID\", \"dataType\": \"Int64\"}, " +
                "{ \"name\": \"Name\", \"dataType\": \"string\"}, " +
                "{ \"name\": \"Category\", \"dataType\": \"string\"}," +
                "{ \"name\": \"IsCompete\", \"dataType\": \"bool\"}," +
                "{ \"name\": \"ManufacturedOn\", \"dataType\": \"DateTime\"}" +
                "]}]}";

            //POST web request
            byte[] byteArray = System.Text.Encoding.UTF8.GetBytes(datasetJson);
            request.ContentLength = byteArray.Length;

            //Write JSON byte[] into a Stream
            using (Stream writer = request.GetRequestStream())
            {
                writer.Write(byteArray, 0, byteArray.Length);

                var response = (HttpWebResponse)request.GetResponse();

                Console.WriteLine(string.Format("Dataset {0}", response.StatusCode.ToString()));

                Console.ReadLine();
            }
        }
        #endregion
    }
}
```

[次の手順 >](walkthrough-push-data-get-datasets.md)

## <a name="next-steps"></a>次の手順
* [Power BI テーブルに行を追加するためにデータセットを取得する](walkthrough-push-data-get-datasets.md)  
* [認証アクセス トークンを取得する](walkthrough-push-data-get-token.md)  
* [PostDataset](/rest/api/power-bi/pushdatasets/datasets_postdataset)  
[PostDatasetInGroup](/rest/api/power-bi/pushdatasets/datasets_postdatasetingroup)  
* [Power BI ダッシュボードにデータをプッシュする](walkthrough-push-data.md)  
* [Power BI REST API の概要](overview-of-power-bi-rest-api.md)  
* [Power BI REST API リファレンス](/rest/api/power-bi/)  

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。