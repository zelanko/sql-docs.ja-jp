---
title: mssqlctl アプリ リファレンス
titleSuffix: SQL Server big data clusters
description: Mssqlctl アプリ コマンドに関する参照記事です。
author: rothja
ms.author: jroth
manager: jroth
ms.date: 05/22/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 75ada3528ab287cf49f717f99efa2405e4aad1db
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66800947"
---
# <a name="mssqlctl-app"></a>mssqlctl アプリ

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

次の記事への参照を提供する、**アプリ**コマンド、 **mssqlctl**ツール。 その他の詳細については**mssqlctl**コマンドを参照してください[mssqlctl 参照](reference-mssqlctl.md)します。

## <a name="commands"></a>コマンド
|     |     |
| --- | --- |
[mssqlctl アプリ テンプレート](reference-mssqlctl-app-template.md) | テンプレート。
[mssqlctl アプリの初期化](#mssqlctl-app-init) | Kickstart の新しいアプリケーションのスケルトンです。
[mssqlctl アプリを作成します。](#mssqlctl-app-create) | アプリケーションを作成します。
[mssqlctl アプリの更新プログラム](#mssqlctl-app-update) | アプリケーションを更新します。
[mssqlctl アプリの一覧](#mssqlctl-app-list) | アプリケーションの一覧を表示します。
[mssqlctl アプリの削除](#mssqlctl-app-delete) | アプリケーションを削除します。
[mssqlctl アプリの実行](#mssqlctl-app-run) | アプリケーションを実行します。
[mssqlctl アプリについて説明します](#mssqlctl-app-describe) | アプリケーションをについて説明します。
## <a name="mssqlctl-app-init"></a>mssqlctl アプリの初期化
Kickstart の新しいアプリケーションのスケルトンやランタイム環境に基づいて、spec ファイルにできます。
```bash
mssqlctl app init [--spec -s] 
                  [--name -n]  
                  [--version -v]  
                  [--template -t]  
                  [--destination -d]  
                  [--url -u]
```
### <a name="examples"></a>使用例
新しいアプリケーションのスキャフォールディング`spec.yaml`のみです。
```bash
mssqlctl app init --spec
```
基づく新しい R アプリケーション アプリケーション スケルトンのスキャフォールディング、`r`テンプレート。
```bash
mssqlctl app init --name reduce --template r
```
基づく新しい Python アプリケーション アプリケーション スケルトンのスキャフォールディング、`python`テンプレート。
```bash
mssqlctl app init --name reduce --template python
```
基づく新しい SSIS アプリケーション アプリケーション スケルトンのスキャフォールディング、`ssis`テンプレート。
```bash
mssqlctl app init --name reduce --template ssis            
```
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--spec -s`
アプリケーション spec.yaml だけを生成します。
#### `--name -n`
[アプリケーション名]
#### `--version -v`
アプリケーションのバージョン。
#### `--template -t`
テンプレートの名前。 実行のサポートされているテンプレート名を完全な一覧について `mssqlctl app template list`
#### `--destination -d`
アプリケーションのスケルトンを配置する場所。 現在の作業ディレクトリ既定値:。
#### `--url -u`
別のテンプレート リポジトリの場所を指定します。 既定値: https://github.com/Microsoft/SQLBDC-AppDeploy.git
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
## <a name="mssqlctl-app-create"></a>mssqlctl アプリを作成します。
アプリケーションを作成します。
```bash
mssqlctl app create --spec -s 
                    
```
### <a name="examples"></a>使用例
有効な spec.yaml 配置の仕様を含むディレクトリから新しいアプリケーションを作成します。
```bash
mssqlctl app create --spec /path/to/dir/with/spec/yaml
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--spec -s`
アプリケーションを記述する YAML spec ファイルのディレクトリへのパス。
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
## <a name="mssqlctl-app-update"></a>mssqlctl アプリの更新プログラム
アプリケーションを更新します。
```bash
mssqlctl app update [--spec -s] 
                    [--yes -y]
```
### <a name="examples"></a>使用例
有効な spec.yaml 配置の仕様を含むディレクトリから既存のアプリケーションを更新します。
```bash
mssqlctl app update --spec /path/to/dir/with/spec/yaml    
```
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--spec -s`
アプリケーションを記述する YAML spec ファイルのディレクトリへのパス。
#### `--yes -y`
求めない確認 CWD の spec.yaml ファイルからアプリケーションを更新するときにします。
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
## <a name="mssqlctl-app-list"></a>mssqlctl アプリの一覧
アプリケーションの一覧を表示します、。
```bash
mssqlctl app list [--name -n] 
                  [--version -v]
```
### <a name="examples"></a>使用例
名前およびバージョン別のアプリケーションの一覧を表示します。
```bash
mssqlctl app list --name reduce  --version v1
```
名前では、アプリケーションのすべてのバージョンを一覧表示します。
```bash
mssqlctl app list --name reduce
```
名前では、アプリケーションのすべてのバージョンを一覧表示します。
```bash
mssqlctl app list
```
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--name -n`
[アプリケーション名]
#### `--version -v`
アプリケーションのバージョン。
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
## <a name="mssqlctl-app-delete"></a>mssqlctl アプリの削除
アプリケーションを削除します。
```bash
mssqlctl app delete --name -n 
                    --version -v
```
### <a name="examples"></a>使用例
名前とバージョンでアプリケーションを削除します。
```bash
mssqlctl app delete --name reduce --version v1    
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--name -n`
[アプリケーション名]
#### `--version -v`
アプリケーションのバージョン。
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
## <a name="mssqlctl-app-run"></a>mssqlctl アプリの実行
アプリケーションを実行します。
```bash
mssqlctl app run --name -n 
                 --version -v  
                 [--inputs]
```
### <a name="examples"></a>使用例
入力パラメーターなしでアプリケーションを実行します。
```bash
mssqlctl app run --name reduce --version v1
```
1 つの入力パラメーターを使用してアプリケーションを実行します。
```bash
mssqlctl app run --name reduce --version v1 --inputs x=10
```
複数の入力パラメーターを持つアプリケーションを実行します。
```bash
mssqlctl app run --name reduce --version v1 --inputs x=10,y5.6    
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--name -n`
[アプリケーション名]
#### `--version -v`
アプリケーションのバージョン。
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--inputs`
アプリケーションの入力を CSV パラメーター`name=value`形式。
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
## <a name="mssqlctl-app-describe"></a>mssqlctl アプリについて説明します
アプリケーションを記述します。
```bash
mssqlctl app describe [--spec -s] 
                      [--name -n]  
                      [--version -v]
```
### <a name="examples"></a>使用例
アプリケーションをについて説明します。
```bash
mssqlctl app describe --name reduce --version v1    
```
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--spec -s`
アプリケーションを記述する YAML spec ファイルのディレクトリへのパス。
#### `--name -n`
[アプリケーション名]
#### `--version -v`
アプリケーションのバージョン。
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