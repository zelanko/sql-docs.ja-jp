---
title: mssqlctl ストレージ マウント リファレンス
titleSuffix: SQL Server big data clusters
description: Mssqlctl 記憶域のマウント コマンドに関する参照記事です。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 04/23/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 523253e8d1ff2d621d9f7a5ef90dbc957fba82ec
ms.sourcegitcommit: d5cd4a5271df96804e9b1a27e440fb6fbfac1220
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64774689"
---
# <a name="mssqlctl-storage-mount"></a>mssqlctl ストレージのマウント

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

次の記事への参照を提供します、**ストレージ マウント**コマンド、 **mssqlctl**ツール。 その他の詳細については**mssqlctl**コマンドを参照してください[mssqlctl 参照](reference-mssqlctl.md)します。

## <a name="commands"></a>コマンド
|     |     |
| --- | --- |
[mssqlctl 記憶域のマウントを作成します。](#mssqlctl-storage-mount-create) | HDFS では、リモートのストアのマウントを作成します。
[mssqlctl storage mount delete](#mssqlctl-storage-mount-delete) | HDFS 内の各店舗のマウントを削除します。
[mssqlctl storage mount status](#mssqlctl-storage-mount-status) | Mount(s) の状態です。
## <a name="mssqlctl-storage-mount-create"></a>mssqlctl 記憶域のマウントを作成します。
HDFS では、リモートのストアのマウントを作成します。
```bash
mssqlctl storage mount create --remote-uri 
                              --mount-path  
                              [--credential-file]
```
### <a name="examples"></a>使用例
共有キーを使用して HDFS パス/mounts/adlsv2/data にジェネレーション 2 の ADLS アカウント"adlsv2example"コンテナー「データ」をマウントするには
```bash
mssqlctl storage mount create --remote-uri abfs://data@adlsv2example.dfs.core.windows.net/
    --mount-path /mounts/adlsv2/data --credentials credential_file
```
リモートの HDFS クラスターにマウントする (hdfs://namenode1:8080/) のローカル HDFS パス/mounts hdfs/
```bash
mssqlctl storage mount create --remote-uri hdfs://namenode1:8080/ --mount-path /mounts/hdfs/
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--remote-uri`
マウントされた (マウントのソース) が、リモート ストアの URI。
#### `--mount-path`
マウントでは、(のマウント先) を作成する場所の HDFS パス。
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--credential-file`
リモート ストアへのアクセス資格情報を含むファイルです。 資格情報キーとして指定する必要は値のペアを = 1 つのキーを持つ 1 行の値を = です。 エスケープする必要はキーまたは値は任意です。 既定では、資格情報は必要ありません。 必要なキーは、マウントされているリモートのストアの種類と使用する認証の種類によって異なります。
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
## <a name="mssqlctl-storage-mount-delete"></a>mssqlctl storage mount delete
HDFS 内の各店舗のマウントを削除します。
```bash
mssqlctl storage mount delete --mount-path 
                              
```
### <a name="examples"></a>使用例
マウント/mounts/adlsv2/data ADLS ジェネレーション 2 のストレージ アカウントの作成を削除します。
```bash
mssqlctl storage mount delete --mount-path /mounts/adlsv2/data
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
## <a name="mssqlctl-storage-mount-status"></a>mssqlctl storage mount status
Mount(s) の状態です。
```bash
mssqlctl storage mount status [--mount-path] 
                              
```
### <a name="examples"></a>使用例
パスでマウント状態を取得します。
```bash
mssqlctl storage mount status --mount-path /mounts/hdfs
```
すべてのマウントの状態を取得します。
```bash
mssqlctl storage mount status
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

## <a name="next-steps"></a>次のステップ

その他の詳細については**mssqlctl**コマンドを参照してください[mssqlctl 参照](reference-mssqlctl.md)します。 インストールする方法について、 **mssqlctl**ツールを参照してください[インストールの SQL Server 2019 ビッグ データ クラスターを管理する mssqlctl](deploy-install-mssqlctl.md)します。