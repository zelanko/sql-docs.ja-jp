---
title: mssqlctl アプリ リファレンス
titleSuffix: SQL Server big data clusters
description: Mssqlctl アプリ コマンドに関する参照記事です。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: b418f1ded8d9911143b431ae9793c467c4e26eb4
ms.sourcegitcommit: 2de5446fbc57787f18a907dd5deb02a7831ec07d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58860653"
---
# <a name="mssqlctl-app"></a>mssqlctl アプリ

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

次の記事への参照を提供する、**アプリ**コマンド、 **mssqlctl**ツール。 その他の詳細については**mssqlctl**コマンドを参照してください[mssqlctl 参照](reference-mssqlctl.md)します。

## <a id="commands"></a> コマンド

|||
|---|---|
| [作成](#create) | アプリケーションを作成します。 |
| [delete](#delete) | アプリケーションを削除します。 |
| [について説明します](#describe) | アプリケーションをについて説明します。 |
| [Init](#init) | Kickstart の新しいアプリケーションのスケルトンです。 |
| [一覧](#list) | アプリケーションの一覧を表示します。 |
| [実行](#run) | アプリケーションを実行します。 |
| [update](#update) | アプリケーションを更新します。 |
| [テンプレート](reference-mssqlctl-app-template.md) | テンプレート コマンド。 |

## <a id="create"></a> mssqlctl アプリを作成します。

アプリケーションを作成します。

```
mssqlctl app create
   --assets
   --code
   --description
   --entrypoint
   --inputs
   --name
   --outputs
   --runtime
   --spec
   --version
   --yes
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|---|---|
| **--資産-a** | 含まれる追加のアプリケーション ファイル資産の一覧。 |
| **--code -c** | R または Python のコード ファイルへのパス。 |
| **--description -d** | アプリケーションの説明。 |
| **--entrypoint** |  |
| **-入力** | 入力パラメーターのスキーマです。 |
| **--name -n** | [アプリケーション名] |
| **-出力** | 出力パラメーターのスキーマです。 |
| **--runtime -r** | アプリケーション ランタイム。  有効な値:Mleap、Python、R では、SSIS します。 |
| **--s の仕様** | アプリケーションを記述する YAML spec ファイルのディレクトリへのパス。 |
| **-バージョン v** | アプリケーションのバージョン。 |
| **--y を [はい]** | 求めない確認 CWD の spec.yaml ファイルからアプリケーションを作成するときにします。 |

### <a name="examples"></a>使用例

Spec.yaml (推奨) を使用して新しいアプリケーションを作成します。

```
mssqlctl app create --spec /path/to/dir/with/spec/yaml
```

引数を使用して新しい Python アプリのインラインを作成します。

```
mssqlctl app create --name add --version v1 --inputs x=float, y=float --outputs result=float --runtime Python --code add.py  --init init.py
```

引数を使用して、新しい R アプリケーション インラインを作成します。

```
mssqlctl app create --name add --version v1 --inputs x=numeric, y=numeric --outputs result=numeric --runtime R --code add.R  --init init.R
```

含まれる追加のファイルのアセットには、新しい R アプリケーション インラインを作成します。

```
mssqlctl app create --name add --version v1 --runtime R --code  add.R --assets file.RData,/path/to/more/files
```

## <a id="delete"></a> mssqlctl アプリの削除

アプリケーションを削除します。

```
mssqlctl app delete
   --name
   --version
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|---|---|
| **--name -n** | [アプリケーション名] |
| **-バージョン v** | アプリケーションのバージョン。 |

### <a name="examples"></a>使用例

名前とバージョンでアプリケーションを削除します。

```
mssqlctl app delete --name reduce --version v1
```

## <a id="describe"></a> mssqlctl アプリについて説明します

アプリケーションをについて説明します。

```
mssqlctl app describe
   --name
   --spec
   --version
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|---|---|
| **--name -n** | [アプリケーション名] |
| **--s の仕様** | アプリケーションを記述する YAML spec ファイルのディレクトリへのパス。 |
| **-バージョン v** | アプリケーションのバージョン。 |

### <a name="examples"></a>使用例

アプリケーションをについて説明します。

```
mssqlctl app describe --name reduce --version v1
```

## <a id="init"></a> mssqlctl アプリの初期化

Kickstart の新しいアプリケーションのスケルトンです。

```
mssqlctl app init
   --destination
   --name
   --spec
   --template
   --url
   --version
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|---|---|
| **--destination -d** | アプリケーションのスケルトンを配置する場所。 現在の作業ディレクトリ既定値:。 |
| **--name -n** | [アプリケーション名] |
| **--s の仕様** | アプリケーション spec.yaml だけを生成します。 |
| **-テンプレート -t** | テンプレートの名前。 サポートされているテンプレートの名前を完全な一覧については、実行`mssqlctl app template list`します。 |
| **--url -u** | 別のテンプレート リポジトリの場所を指定します。 既定値:https://github.com/Microsoft/sql-server-samples.gitします。 |
| **-バージョン v** | アプリケーションのバージョン。 |

### <a name="examples"></a>使用例

新しいアプリケーションのスキャフォールディング`spec.yaml`のみです。

```
mssqlctl app init --spec
```

基づく新しい R アプリケーション アプリケーション スケルトンのスキャフォールディング、`r`テンプレート。

```
mssqlctl app init --name reduce --template r
```

基づく新しい Python アプリケーション アプリケーション スケルトンのスキャフォールディング、`python`テンプレート。

```
mssqlctl app init --name reduce --template python
```

基づく新しい SSIS アプリケーション アプリケーション スケルトンのスキャフォールディング、`ssis`テンプレート。

```
mssqlctl app init --name reduce --template ssis
```

## <a id="list"></a> mssqlctl アプリの一覧

アプリケーションの一覧を表示します。

```
mssqlctl app list
   --name
   --version
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|---|---|
| **--name -n** | [アプリケーション名] |
| **-バージョン v** | アプリケーションのバージョン。 |

### <a name="examples"></a>使用例

名前およびバージョン別のアプリケーションの一覧を表示します。

```
mssqlctl app list --name reduce  --version v1
```

名前では、アプリケーションのすべてのバージョンを一覧表示します。

```
mssqlctl app list --name reduce
```

すべてのアプリケーションの一覧を表示します。

```
mssqlctl app list
```

## <a id="run"></a> mssqlctl アプリの実行

アプリケーションを実行します。

```
mssqlctl app run
   --name
   --version
   --inputs
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|---|---|
| **--name -n** | [アプリケーション名] |
| **-バージョン v** | アプリケーションのバージョン。 |
| **-入力** | アプリケーションの入力を CSV パラメーター`name=value`形式。 |

### <a name="examples"></a>使用例

入力パラメーターなしでアプリケーションを実行します。

```
mssqlctl app run --name reduce --version v1
```

1 つの入力パラメーターを使用してアプリケーションを実行します。

```
mssqlctl app run --name reduce --version v1 --inputs x=10
```

複数の入力パラメーターを持つアプリケーションを実行します。

```
mssqlctl app run --name reduce --version v1 --inputs x=10,y5.6
```

## <a id="update"></a> mssqlctl アプリの更新プログラム

アプリケーションを更新します。

```
mssqlctl app update
   --spec
   --yes
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|---|---|
| **--s の仕様** | アプリケーションを記述する YAML spec ファイルのディレクトリへのパス。 |
| **--y を [はい]** | 求めない確認 CWD の spec.yaml ファイルからアプリケーションを更新するときにします。 |

## <a name="next-steps"></a>次のステップ

その他の詳細については**mssqlctl**コマンドを参照してください[mssqlctl 参照](reference-mssqlctl.md)します。 インストールする方法について、 **mssqlctl**ツールを参照してください[インストールの SQL Server 2019 ビッグ データ クラスターを管理する mssqlctl](deploy-install-mssqlctl.md)します。