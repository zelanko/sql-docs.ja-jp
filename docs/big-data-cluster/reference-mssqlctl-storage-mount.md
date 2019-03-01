---
title: mssqlctl ストレージ マウント リファレンス
titleSuffix: SQL Server 2019 big data clusters
description: Mssqlctl ストレージ コマンドに関する参照記事です。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: a8580c3c52cda484581f1c88ccfc039d8bd0bf78
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/01/2019
ms.locfileid: "57018458"
---
# <a name="mssqlctl-storage-mount"></a>mssqlctl 記憶域のマウント

次の記事への参照を提供します、**ストレージ マウント**コマンド、 **mssqlctl**ツール。 その他の詳細については**mssqlctl**コマンドを参照してください[mssqlctl 参照](reference-mssqlctl.md)します。

## <a id="commands"></a> コマンド

|||
|---|---|
| [create](#create) | HDFS では、リモートのストアのマウントを作成します。 |
| [delete](#delete) | HDFS 内の各店舗のマウントを削除します。 |
| [status](#status) | Mount(s) の状態です。 |

## <a id="create"></a> mssqlctl 記憶域のマウントを作成します。

HDFS では、リモートのストアのマウントを作成します。

```
mssqlctl storage mount create
   --mount-path
   --remote-uri
   [--credential-file]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|---|---|
| **--mount-path** | マウントには、HDFS パス (のマウント先) を作成します。 必須。 |
| **--remote-uri** | マウントされた (マウントのソース) が、リモート ストアの URI。 必須。 |
| **--credential-file** | リモート ストアへのアクセス資格情報を含むファイルです。 資格情報キーとして指定する必要は値のペアを = 1 つのキーを持つ 1 行の値を = です。 エスケープする必要はキーまたは値は任意です。 既定では、資格情報は必要ありません。 必要なキーは、マウントされているリモートのストアの種類と使用する認証の種類によって異なります。 |

### <a name="examples"></a>使用例

ジェネレーション 2 の ADLS アカウント"adlsv2example"コンテナー「データ」を HDFS パスにマウントする`/mounts/adlsv2/data`共有キーを使用します。

```
mssqlctl storage mount create --remote-uri abfs://data@adlsv2example.dfs.core.windows.net/ --mount-path /mounts/adlsv2/data --credentials credential_file
```

リモートの HDFS クラスターにマウントする (`hdfs://namenode1:8080/`) ローカルの HDFS パスで`/mounts/hdfs/`:

```
mssqlctl storage mount create --remote-uri hdfs://namenode1:8080/ --mount-path /mounts/hdfs/
```

## <a id="delete"></a> mssqlctl storage mount delete

HDFS 内の各店舗のマウントを削除します。

```
mssqlctl storage mount delete
   --mount-path
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|---|---|
| **--mount-path** | 削除するマウントに対応する HDFS パス。 必須。 |

### <a name="examples"></a>使用例

マウント/mounts/adlsv2/data ADLS ジェネレーション 2 のストレージ アカウントの作成を削除します。

```
mssqlctl storage mount delete --mount-path /mounts/adlsv2/data
```

## <a id="status"></a> mssqlctl storage mount status

Mount(s) の状態です。

```
mssqlctl storage mount status
   --mount-path
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|---|---|
| **--mount-path** | マウントのパス。 必須。 |

### <a name="examples"></a>使用例

パスでマウント状態を取得します。

```
mssqlctl storage mount status --mount-path /mounts/hdfs
```

すべてのマウントの状態を取得します。

```
mssqlctl storage mount status
```

## <a name="next-steps"></a>次のステップ

その他の詳細については**mssqlctl**コマンドを参照してください[mssqlctl 参照](reference-mssqlctl.md)します。 インストールする方法について、 **mssqlctl**ツールを参照してください[インストールの SQL Server 2019 ビッグ データ クラスターを管理する mssqlctl](deploy-install-mssqlctl.md)します。