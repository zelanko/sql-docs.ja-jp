---
title: azdata bdc hdfs のマウントリファレンス
titleSuffix: SQL Server big data clusters
description: Azdata bdc hdfs のマウントコマンドに関するリファレンス記事です。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 7f0b259a3ac4ac0850fa05de3867e928b035307b
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426272"
---
# <a name="azdata-bdc-hdfs-mount"></a>azdata bdc hdfs のマウント

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

次の記事では、 **azdata**ツールでの**bdc hdfs マウント**コマンドのリファレンスを示します。 その他の**azdata**コマンドの詳細については、「 [azdata reference](reference-azdata.md)」を参照してください。

## <a name="commands"></a>コマンド
|     |     |
| --- | --- |
[azdata bdc hdfs のマウント作成](#azdata-bdc-hdfs-mount-create) | HDFS にリモートストアのマウントを作成します。
[azdata bdc hdfs のマウントの削除](#azdata-bdc-hdfs-mount-delete) | HDFS 内のリモートストアのマウントを削除します。
[azdata bdc hdfs のマウント状態](#azdata-bdc-hdfs-mount-status) | マウントの状態。
[azdata bdc hdfs のマウント更新](#azdata-bdc-hdfs-mount-refresh) | HDFS でマウントの内容を更新します。
## <a name="azdata-bdc-hdfs-mount-create"></a>azdata bdc hdfs のマウント作成
HDFS にリモートストアのマウントを作成します。 リモートストアにアクセスするための資格情報 (存在する場合) は、環境変数 MOUNT_CREDENTIALS を使用して、キーと値のペアのコンマ区切りリストとして指定する必要があります。 キーまたは値のコンマは、エスケープする必要があります。
```bash
azdata bdc hdfs mount create --remote-uri -r 
                             --mount-path -m
```
### <a name="examples"></a>使用例
共有キーを使用して HDFS パス/mounts/adlsv2/data の ADLS Gen 2 アカウント "adlsv2example" にコンテナー "データ" をマウントするには
```bash
Set the MOUNT_CREDENTIALS environment variable as "fs.azure.abfs.account.name=<your-storage-account-name>.dfs.core.windows.net,fs.azure.account.key.<your-storage-account-name>.dfs.core.windows.net=<storage-account-access-key>".
azdata bdc hdfs mount create --remote-uri abfs://data@adlsv2example.dfs.core.windows.net/
    --mount-path /mounts/adlsv2/data
```
リモート HDFS BDC (hdfs://namenode1:8080/) をローカルの HDFS パス/mounts/hdfs/にマウントするには
```bash
azdata bdc hdfs mount create --remote-uri hdfs://namenode1:8080/ --mount-path /mounts/hdfs/
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--remote-uri -r`
マウントされるリモートストアの URI (マウントのソース)。
#### `--mount-path -m`
マウントを作成する必要がある HDFS パス (マウント先)。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
ログの詳細度を上げて、すべてのデバッグログを表示します。
#### `--help -h`
このヘルプメッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値は json です。
#### `--query -q`
Jのパスのクエリ文字列。 詳細[http://jmespath.org/](http://jmespath.org/])と例については、「」を参照してください。
#### `--verbose`
ログの詳細度を上げます。 完全なデバッグログには--debug を使用します。
## <a name="azdata-bdc-hdfs-mount-delete"></a>azdata bdc hdfs のマウントの削除
HDFS 内のリモートストアのマウントを削除します。
```bash
azdata bdc hdfs mount delete --mount-path -m 
                             
```
### <a name="examples"></a>使用例
ADLS Gen 2 ストレージアカウントの/mounts/adlsv2/data で作成されたマウントを削除します。
```bash
azdata bdc hdfs mount delete --mount-path /mounts/adlsv2/data
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--mount-path -m`
削除する必要があるマウントに対応する HDFS パス。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
ログの詳細度を上げて、すべてのデバッグログを表示します。
#### `--help -h`
このヘルプメッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値は json です。
#### `--query -q`
Jのパスのクエリ文字列。 詳細[http://jmespath.org/](http://jmespath.org/])と例については、「」を参照してください。
#### `--verbose`
ログの詳細度を上げます。 完全なデバッグログには--debug を使用します。
## <a name="azdata-bdc-hdfs-mount-status"></a>azdata bdc hdfs のマウント状態
マウントの状態。
```bash
azdata bdc hdfs mount status [--mount-path -m] 
                             
```
### <a name="examples"></a>使用例
パス別のマウント状態の取得
```bash
azdata bdc hdfs mount status --mount-path /mounts/hdfs
```
すべてのマウントの状態を取得します。
```bash
azdata bdc hdfs mount status
```
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--mount-path -m`
マウントパス。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
ログの詳細度を上げて、すべてのデバッグログを表示します。
#### `--help -h`
このヘルプメッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値は json です。
#### `--query -q`
Jのパスのクエリ文字列。 詳細[http://jmespath.org/](http://jmespath.org/])と例については、「」を参照してください。
#### `--verbose`
ログの詳細度を上げます。 完全なデバッグログには--debug を使用します。
## <a name="azdata-bdc-hdfs-mount-refresh"></a>azdata bdc hdfs のマウント更新
HDFS でマウントの内容を更新します。
```bash
azdata bdc hdfs mount refresh --mount-path -m 
                              
```
### <a name="examples"></a>使用例
/Mounts/adlsv2/data. で作成された更新マウント
```bash
azdata bdc hdfs mount refresh --mount-path /mounts/adlsv2/data
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--mount-path -m`
更新する必要があるマウントに対応する HDFS パス。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
ログの詳細度を上げて、すべてのデバッグログを表示します。
#### `--help -h`
このヘルプメッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値は json です。
#### `--query -q`
Jのパスのクエリ文字列。 詳細[http://jmespath.org/](http://jmespath.org/])と例については、「」を参照してください。
#### `--verbose`
ログの詳細度を上げます。 完全なデバッグログには--debug を使用します。

## <a name="next-steps"></a>次の手順

その他の**azdata**コマンドの詳細については、「 [azdata reference](reference-azdata.md)」を参照してください。 **Azdata**ツールをインストールする方法の詳細については、「 [Azdata をインストールして SQL Server 2019 ビッグデータクラスターを管理する](deploy-install-azdata.md)」を参照してください。
