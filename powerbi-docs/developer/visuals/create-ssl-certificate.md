---
title: 埋め込み BI 分析情報を向上させるため、Power BI 埋め込み分析で Power BI ビジュアルの SSL 証明書を作成する
description: Windows、Mac、Linux で Power BI Visual Tools を使用して、または手動で、SSL 証明書を生成する方法について説明します。 Power BI 埋め込み分析を使用して、より優れた埋め込み BI インサイトを有効にします。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 05/08/2020
ms.openlocfilehash: 7897d25f3ac49c0f1b728f2aaf05b8612de67055
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2021
ms.locfileid: "97885524"
---
# <a name="create-an-ssl-certificate"></a>SSL 証明書を作成する

この記事では Power BI ビジュアル用の Secure Sockets Layer (SSL) 証明書を生成してインストールする方法について説明します。

Windows、macOS X、Linux の各手順を実行するには、Power BI Visual Tools **pbiviz** パッケージがインストールされている必要があります。 詳細については、「[Power BI の視覚化の開発用に環境をセットアップする](./environment-setup.md)」を参照してください。 

## <a name="create-a-certificate-on-windows"></a>Windows で証明書を作成する

Windows 8 以降で PowerShell コマンドレット `New-SelfSignedCertificate` を使用して証明書を作成するには、次のコマンドを実行します。

```powershell
pbiviz --install-cert
```

Windows 7 の場合、`pbiviz` ツールを使用するには、コマンド ラインから OpenSSL ユーティリティを使用できるようにする必要があります。 OpenSSL をインストールするには、[OpenSSL](https://www.openssl.org) または [OpenSSL バイナリ](https://wiki.openssl.org/index.php/Binaries)にアクセスします。

証明書をインストールする方法の詳細と手順については、[Windows 用の証明書の作成およびインストール](./environment-setup.md#create-and-install-a-certificate)に関するページをご覧ください。

## <a name="create-a-certificate-on-macos-x"></a>macOS で証明書を作成する

OpenSSL ユーティリティは通常、macOS X オペレーティング システムで使用できます。

また、次のコマンドのどちらかを実行して、OpenSSL ユーティリティをインストールすることができます。

- *Brew* パッケージ マネージャーからの場合:
  
  ```cmd
  brew install openssl
  brew link openssl --force
  ```

- *MacPorts* を使用する場合:
  
  ```cmd
  sudo port install openssl
  ```

OpenSSL ユーティリティをインストールしたら、次のコマンドを実行して新しい証明書を生成します。

```cmd
pbiviz --install-cert
```

詳細と手順については、「[証明書を作成してインストールする](./environment-setup.md#create-and-install-a-certificate)」の「OSX」タブを参照してください。

## <a name="create-a-certificate-on-linux"></a>Linux で証明書を作成する

OpenSSL ユーティリティは通常、Linux オペレーティング システムで使用できます。

開始する前に、次のコマンドを実行して `openssl` および `certutil` がインストールされていることを確認してください。

```sh
which openssl
which certutil
```

`openssl` と `certutil` がインストールされていない場合は、`openssl` および `libnss3` ユーティリティをインストールします。

### <a name="create-the-ssl-configuration-file"></a>SSL 構成ファイルを作成する

次のテキストを含む */tmp/openssl.cnf* という名前のファイルを作成します。

```
authorityKeyIdentifier=keyid,issuer
basicConstraints=CA:FALSE
keyUsage = digitalSignature, nonRepudiation, keyEncipherment, dataEncipherment
subjectAltName = @alt_names

[ alt_names ]
DNS.1=localhost
```

### <a name="generate-root-certificate-authority"></a>ルート証明機関を生成する

ローカル証明書に署名するためのルート証明機関 (CA) を生成するには、次のコマンドを実行します。

```sh
touch $HOME/.rnd
openssl req -x509 -nodes -new -sha256 -days 1024 -newkey rsa:2048 -keyout /tmp/local-root-ca.key -out /tmp/local-root-ca.pem -subj "/C=US/CN=Local Root CA/O=Local Root CA"
openssl x509 -outform pem -in /tmp/local-root-ca.pem -out /tmp/local-root-ca.crt
```

### <a name="generate-a-certificate-for-localhost"></a>localhost の証明書を生成する 

生成された CA および *openssl.cnf* を使用して `localhost` の証明書を生成するには、次のコマンドを実行します。

```sh
PBIVIZ=`which pbiviz`
PBIVIZ=`dirname $PBIVIZ`
PBIVIZ="$PBIVIZ/../lib/node_modules/powerbi-visuals-tools/certs"
# Make sure that $PBIVIZ contains the correct certificate directory path. ls $PBIVIZ should list 'blank' file.
openssl req -new -nodes -newkey rsa:2048 -keyout $PBIVIZ/PowerBIVisualTest_private.key -out $PBIVIZ/PowerBIVisualTest.csr -subj "/C=US/O=PowerBI Visuals/CN=localhost"
openssl x509 -req -sha256 -days 1024 -in $PBIVIZ/PowerBIVisualTest.csr -CA /tmp/local-root-ca.pem -CAkey /tmp/local-root-ca.key -CAcreateserial -extfile /tmp/openssl.cnf -out $PBIVIZ/PowerBIVisualTest_public.crt
```

### <a name="add-root-certificates"></a>ルート証明書を追加する

Chrome ブラウザーのデータベースにルート証明書を追加するには、次のコマンドを実行します。

```sh
certutil -A -n "Local Root CA" -t "CT,C,C" -i /tmp/local-root-ca.pem -d sql:$HOME/.pki/nssdb
```

Mozilla Firefox ブラウザーのデータベースにルート証明書を追加するには、次のコマンドを実行します。

```sh
for certDB in $(find $HOME/.mozilla* -name "cert*.db")
do
certDir=$(dirname ${certDB});
certutil -A -n "Local Root CA" -t "CT,C,C" -i /tmp/local-root-ca.pem -d sql:${certDir}
done
```

システム全体のルート証明書を追加するには、次のコマンドを実行します。

```sh
sudo cp /tmp/local-root-ca.pem /usr/local/share/ca-certificates/
sudo update-ca-certificates
```

### <a name="remove-root-certificates"></a>ルート証明書を削除する

ルート証明書を削除するには、次のコマンドを実行します。

```sh
sudo rm /usr/local/share/ca-certificates/local-root-ca.pem
sudo update-ca-certificates --fresh
```

## <a name="generate-a-certificate-manually"></a>証明書を手動で生成する

OpenSSL を使用して、手動で SSL 証明書を生成することもできます。 証明書を生成する任意のツールを指定できます。

OpenSSL ユーティリティが既にインストールされている場合は、次のコマンドを実行して新しい証明書を作成します。

```cmd
openssl req -x509 -newkey rsa:4096 -keyout PowerBIVisualTest_private.key -out PowerBIVisualTest_public.crt -days 365
```

通常は、次のコマンドのどちらかを実行することで、`PowerBI-visuals-tools` Web サーバー証明書を見つけることができます。

- ツールのグローバル インスタンスの場合:
  
  ```cmd
  %appdata%\npm\node_modules\PowerBI-visuals-tools\certs
  ```

- ツールのローカル インスタンスの場合:
  
  ```cmd
  <Power BI visual project root>\node_modules\PowerBI-visuals-tools\certs
  ```

### <a name="pem-format"></a>PEM 形式

Privacy Enhanced Mail (PEM) 証明書形式を使用する場合は、証明書ファイルを *PowerBIVisualTest_public.crt* として保存し、秘密キーを *PowerBIVisualTest_private.key* として保存します。

### <a name="pfx-format"></a>PFX 形式

Personal Information Exchange (PFX) 証明書形式を使用する場合は、証明書ファイルを *PowerBIVisualTest_public.pfx* として保存します。

PFX 証明書ファイルにパスフレーズが必要な場合は、次のようにします。

1. 構成ファイルで、次のように指定します。
   
   ```cmd
   \PowerBI-visuals-tools\config.json
   ```
   
1. `server` セクションで、\<YOUR PASSPHRASE> プレースホルダーを置き換えることによってパスフレーズを指定します。

    ```cmd
    "server":{
        "root":"webRoot",
        "assetsRoute":"/assets",
        "privateKey":"certs/PowerBIVisualTest_private.key",
        "certificate":"certs/PowerBIVisualTest_public.crt",
        "pfx":"certs/PowerBIVisualTest_public.pfx",
        "port":"8080",
        "passphrase":"<YOUR PASSPHRASE>"
    }
    ```

## <a name="next-steps"></a>次の手順
- [Power BI の円形カード視覚化を開発する](develop-circle-card.md)
- [Power BI ビジュアルのサンプル](samples.md)
- [Power BI ビジュアルを AppSource に発行する](office-store.md)