---
title: mssqlctl bdc storage-pool mount reference
titleSuffix: SQL Server big data clusters
description: Mssqlctl bdc 記憶域プールのマウント コマンドに関する参照記事です。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
manager: jroth
ms.date: 06/26/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 4204e87e96fd0d91a9bfbf64813583ef92d3202b
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727480"
---
# <a name="mssqlctl-bdc-storage-pool-mount"></a>mssqlctl bdc 記憶域プールのマウント

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

次の記事への参照を提供する、 **bdc 記憶域プールのマウント**コマンド、 **mssqlctl**ツール。 その他の詳細については**mssqlctl**コマンドを参照してください[mssqlctl 参照](reference-mssqlctl.md)します。

## <a name="commands"></a>コマンド
|     |     |
| --- | --- |
[mssqlctl bdc 記憶域プールのマウントを作成します。](#mssqlctl-bdc-storage-pool-mount-create) | HDFS では、リモートのストアのマウントを作成します。
[mssqlctl bdc storage-pool mount delete](#mssqlctl-bdc-storage-pool-mount-delete) | HDFS 内の各店舗のマウントを削除します。
[mssqlctl bdc storage-pool mount status](#mssqlctl-bdc-storage-pool-mount-status) | Mount(s) の状態です。
## <a name="mssqlctl-bdc-storage-pool-mount-create"></a>mssqlctl bdc storage-pool mount create
HDFS では、リモートのストアのマウントを作成します。 キーのコンマ区切りリストとして MOUNT_CREDENTIALS 環境変数を使用して、存在する場合に、リモートのストアにアクセスするための資格情報を指定する必要があります値のペアします。 キーまたは値のコンマをエスケープする必要があります。
```bash
mssqlctl bdc storage-pool mount create --remote-uri 
                                       --mount-path
```
### <a name="examples"></a>使用例
共有キーを使用して HDFS パス/mounts/adlsv2/data にジェネレーション 2 の ADLS アカウント"adlsv2example"コンテナー「データ」をマウントするには
```bash
Set the MOUNT_CREDENTIALS environment variable as "fs.azure.abfs.account.name=<your-storage-account-name>.dfs.core.windows.net,fs.azure.account.key.<your-storage-account-name>.dfs.core.windows.net=<storage-account-access-key>".
mssqlctl bdc storage-pool mount create --remote-uri abfs://data@adlsv2example.dfs.core.windows.net/
    --mount-path /mounts/adlsv2/data
```
リモートの HDFS BDC をマウントする (hdfs://namenode1:8080/) のローカル HDFS パス/mounts hdfs/
```bash
mssqlctl bdc storage-pool mount create --remote-uri hdfs://namenode1:8080/ --mount-path /mounts/hdfs/
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--remote-uri`
マウントされた (マウントのソース) が、リモート ストアの URI。
#### `--mount-path`
マウントでは、(のマウント先) を作成する場所の HDFS パス。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
すべてのデバッグ ログを表示するログの詳細度を向上します。
#### `--help -h`
このヘルプ メッセージと終了を示します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv です。  既定: json。
#### `--query -q`
JMESPath クエリ文字列。 参照してください[ http://jmespath.org/ ](http://jmespath.org/])詳細と例。
#### `--verbose`
ログ記録を上げます。 完全なデバッグ ログのデバッグ - 使用します。
## <a name="mssqlctl-bdc-storage-pool-mount-delete"></a>mssqlctl bdc storage-pool mount delete
HDFS 内の各店舗のマウントを削除します。
```bash
mssqlctl bdc storage-pool mount delete --mount-path 
                                       
```
### <a name="examples"></a>使用例
マウント/mounts/adlsv2/data ADLS ジェネレーション 2 のストレージ アカウントの作成を削除します。
```bash
mssqlctl bdc storage-pool mount delete --mount-path /mounts/adlsv2/data
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--mount-path`
削除するマウントに対応する HDFS パス。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
すべてのデバッグ ログを表示するログの詳細度を向上します。
#### `--help -h`
このヘルプ メッセージと終了を示します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv です。  既定: json。
#### `--query -q`
JMESPath クエリ文字列。 参照してください[ http://jmespath.org/ ](http://jmespath.org/])詳細と例。
#### `--verbose`
ログ記録を上げます。 完全なデバッグ ログのデバッグ - 使用します。
## <a name="mssqlctl-bdc-storage-pool-mount-status"></a>mssqlctl bdc storage-pool mount status
Mount(s) の状態です。
```bash
mssqlctl bdc storage-pool mount status [--mount-path] 
                                       
```
### <a name="examples"></a>使用例
パスでマウント状態を取得します。
```bash
mssqlctl bdc storage-pool mount status --mount-path /mounts/hdfs
```
すべてのマウントの状態を取得します。
```bash
mssqlctl bdc storage-pool mount status
```
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--mount-path`
マウントのパス。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
すべてのデバッグ ログを表示するログの詳細度を向上します。
#### `--help -h`
このヘルプ メッセージと終了を示します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv です。  既定: json。
#### `--query -q`
JMESPath クエリ文字列。 参照してください[ http://jmespath.org/ ](http://jmespath.org/])詳細と例。
#### `--verbose`
ログ記録を上げます。 完全なデバッグ ログのデバッグ - 使用します。

## <a name="next-steps"></a>次の手順

その他の詳細については**mssqlctl**コマンドを参照してください[mssqlctl 参照](reference-mssqlctl.md)します。 インストールする方法について、 **mssqlctl**ツールを参照してください[インストールの SQL Server 2019 ビッグ データ クラスターを管理する mssqlctl](deploy-install-mssqlctl.md)します。