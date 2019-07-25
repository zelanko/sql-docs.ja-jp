---
title: azdata アプリのリファレンス
titleSuffix: SQL Server big data clusters
description: Azdata アプリのコマンドに関するリファレンス記事です。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 793edde26ebebf9e55c5751adbedf662142280de
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426282"
---
# <a name="azdata-app"></a>azdata アプリ

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

次の記事では、 **azdata**ツールでの**アプリ**コマンドのリファレンスを示します。 その他の**azdata**コマンドの詳細については、「 [azdata reference](reference-azdata.md)」を参照してください。

## <a name="commands"></a>コマンド
|     |     |
| --- | --- |
[azdata アプリテンプレート](reference-azdata-app-template.md) | テンプレート.
[azdata アプリの初期化](#azdata-app-init) | Kickstart 新しいアプリケーションスケルトン。
[azdata アプリの作成](#azdata-app-create) | アプリケーションを作成します。
[azdata アプリの更新](#azdata-app-update) | アプリケーションを更新します。
[azdata アプリの一覧](#azdata-app-list) | アプリケーションを一覧表示します。
[azdata アプリの削除](#azdata-app-delete) | アプリケーションを削除します。
[azdata アプリの実行](#azdata-app-run) | アプリケーションを実行します。
[azdata アプリの説明](#azdata-app-describe) | アプリケーションについて説明します。
## <a name="azdata-app-init"></a>azdata アプリの初期化
は、ランタイム環境に基づいて、新しいアプリケーションスケルトンや仕様ファイルを kickstart するのに役立ちます。
```bash
azdata app init [--spec -s] 
                [--name -n]  
                [--version -v]  
                [--template -t]  
                [--destination -d]  
                [--url -u]
```
### <a name="examples"></a>使用例
新しいアプリケーション`spec.yaml`のみをスキャフォールディングします。
```bash
azdata app init --spec
```
`r`テンプレートに基づいて新しい R アプリケーションスケルトンをスキャフォールディングします。
```bash
azdata app init --name reduce --template r
```
`python`テンプレートに基づいて新しい Python アプリケーションスケルトンをスキャフォールディングします。
```bash
azdata app init --name reduce --template python
```
`ssis`テンプレートに基づいて新しい SSIS アプリケーションスケルトンをスキャフォールディングします。
```bash
azdata app init --name reduce --template ssis            
```
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--spec -s`
アプリケーション仕様だけを生成します。 yaml。
#### `--name -n`
[アプリケーション名]
#### `--version -v`
アプリケーションのバージョン。
#### `--template -t`
テンプレート名。 サポートされているテンプレート名の実行の完全な一覧については、「`azdata app template list`
#### `--destination -d`
アプリケーションスケルトンを配置する場所。 既定値: 現在の作業ディレクトリ。
#### `--url -u`
別のテンプレートリポジトリの場所を指定してください。 標準 https://github.com/Microsoft/SQLBDC-AppDeploy.git
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
## <a name="azdata-app-create"></a>azdata アプリの作成
アプリケーションを作成します。
```bash
azdata app create --spec -s 
                  
```
### <a name="examples"></a>使用例
有効な仕様を含むディレクトリから新しいアプリケーションを作成します。 yaml デプロイ仕様。
```bash
azdata app create --spec /path/to/dir/with/spec/yaml
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--spec -s`
アプリケーションを説明する YAML 仕様ファイルを含むディレクトリへのパス。
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
## <a name="azdata-app-update"></a>azdata アプリの更新
アプリケーションを更新します。
```bash
azdata app update [--spec -s] 
                  [--yes -y]
```
### <a name="examples"></a>使用例
有効な仕様を含むディレクトリから既存のアプリケーションを更新します。 yaml デプロイ仕様。
```bash
azdata app update --spec /path/to/dir/with/spec/yaml    
```
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--spec -s`
アプリケーションを説明する YAML 仕様ファイルを含むディレクトリへのパス。
#### `--yes -y`
CWD の spec. yaml ファイルからアプリケーションを更新するときに、確認を求めるメッセージを表示しません。
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
## <a name="azdata-app-list"></a>azdata アプリの一覧
アプリケーションの一覧を表示します。
```bash
azdata app list [--name -n] 
                [--version -v]
```
### <a name="examples"></a>使用例
名前とバージョンでアプリケーションを一覧表示します。
```bash
azdata app list --name reduce  --version v1
```
すべてのアプリケーションのバージョンを名前で一覧表示します。
```bash
azdata app list --name reduce
```
すべてのアプリケーションのバージョンを名前で一覧表示します。
```bash
azdata app list
```
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--name -n`
[アプリケーション名]
#### `--version -v`
アプリケーションのバージョン。
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
## <a name="azdata-app-delete"></a>azdata アプリの削除
アプリケーションを削除します。
```bash
azdata app delete --name -n 
                  --version -v
```
### <a name="examples"></a>使用例
名前とバージョンでアプリケーションを削除します。
```bash
azdata app delete --name reduce --version v1    
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--name -n`
[アプリケーション名]
#### `--version -v`
アプリケーションのバージョン。
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
## <a name="azdata-app-run"></a>azdata アプリの実行
アプリケーションを実行します。
```bash
azdata app run --name -n 
               --version -v  
               [--inputs]
```
### <a name="examples"></a>使用例
入力パラメーターを使用せずにアプリケーションを実行します。
```bash
azdata app run --name reduce --version v1
```
1つの入力パラメーターを使用してアプリケーションを実行します。
```bash
azdata app run --name reduce --version v1 --inputs x=10
```
複数の入力パラメーターを使用してアプリケーションを実行します。
```bash
azdata app run --name reduce --version v1 --inputs x=10,y5.6    
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--name -n`
[アプリケーション名]
#### `--version -v`
アプリケーションのバージョン。
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--inputs`
CSV `name=value`形式のアプリケーション入力パラメーター。
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
## <a name="azdata-app-describe"></a>azdata アプリの説明
アプリケーションを記述します。
```bash
azdata app describe [--spec -s] 
                    [--name -n]  
                    [--version -v]
```
### <a name="examples"></a>使用例
アプリケーションについて説明します。
```bash
azdata app describe --name reduce --version v1    
```
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--spec -s`
アプリケーションを説明する YAML 仕様ファイルを含むディレクトリへのパス。
#### `--name -n`
[アプリケーション名]
#### `--version -v`
アプリケーションのバージョン。
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
