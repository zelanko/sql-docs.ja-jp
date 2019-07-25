---
title: mssqlctl アプリのリファレンス
titleSuffix: SQL Server big data clusters
description: Mssqlctl app コマンドのリファレンス記事です。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/26/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d0df3e9ca007fb6546310236f4c23d1775687cc5
ms.sourcegitcommit: d667fa9d6f1c8035f15fdb861882bd514be020d9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68388389"
---
# <a name="mssqlctl-app"></a>mssqlctl アプリ

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

次の記事では、 **mssqlctl**ツールの**アプリ**コマンドのリファレンスを示します。 その他の**mssqlctl**コマンドの詳細については、「 [mssqlctl reference](reference-mssqlctl.md)」を参照してください。

## <a name="commands"></a>コマンド
|     |     |
| --- | --- |
[mssqlctl アプリテンプレート](reference-mssqlctl-app-template.md) | テンプレート.
[mssqlctl アプリの初期化](#mssqlctl-app-init) | Kickstart 新しいアプリケーションスケルトン。
[mssqlctl アプリの作成](#mssqlctl-app-create) | アプリケーションを作成します。
[mssqlctl アプリの更新](#mssqlctl-app-update) | アプリケーションを更新します。
[mssqlctl アプリの一覧](#mssqlctl-app-list) | アプリケーションを一覧表示します。
[mssqlctl アプリの削除](#mssqlctl-app-delete) | アプリケーションを削除します。
[mssqlctl アプリの実行](#mssqlctl-app-run) | アプリケーションを実行します。
[mssqlctl アプリの説明](#mssqlctl-app-describe) | アプリケーションについて説明します。
## <a name="mssqlctl-app-init"></a>mssqlctl アプリの初期化
は、ランタイム環境に基づいて、新しいアプリケーションスケルトンや仕様ファイルを kickstart するのに役立ちます。
```bash
mssqlctl app init [--spec -s] 
                  [--name -n]  
                  [--version -v]  
                  [--template -t]  
                  [--destination -d]  
                  [--url -u]
```
### <a name="examples"></a>使用例
新しいアプリケーション`spec.yaml`のみをスキャフォールディングします。
```bash
mssqlctl app init --spec
```
`r`テンプレートに基づいて新しい R アプリケーションスケルトンをスキャフォールディングします。
```bash
mssqlctl app init --name reduce --template r
```
`python`テンプレートに基づいて新しい Python アプリケーションスケルトンをスキャフォールディングします。
```bash
mssqlctl app init --name reduce --template python
```
`ssis`テンプレートに基づいて新しい SSIS アプリケーションスケルトンをスキャフォールディングします。
```bash
mssqlctl app init --name reduce --template ssis            
```
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--spec -s`
アプリケーション仕様だけを生成します。 yaml。
#### `--name -n`
[アプリケーション名]
#### `--version -v`
アプリケーションのバージョン。
#### `--template -t`
テンプレート名。 サポートされているテンプレート名の実行の完全な一覧については、「`mssqlctl app template list`
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
## <a name="mssqlctl-app-create"></a>mssqlctl アプリの作成
アプリケーションを作成します。
```bash
mssqlctl app create --spec -s 
                    
```
### <a name="examples"></a>使用例
有効な仕様を含むディレクトリから新しいアプリケーションを作成します。 yaml デプロイ仕様。
```bash
mssqlctl app create --spec /path/to/dir/with/spec/yaml
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
## <a name="mssqlctl-app-update"></a>mssqlctl アプリの更新
アプリケーションを更新します。
```bash
mssqlctl app update [--spec -s] 
                    [--yes -y]
```
### <a name="examples"></a>使用例
有効な仕様を含むディレクトリから既存のアプリケーションを更新します。 yaml デプロイ仕様。
```bash
mssqlctl app update --spec /path/to/dir/with/spec/yaml    
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
## <a name="mssqlctl-app-list"></a>mssqlctl アプリの一覧
アプリケーションの一覧を表示します。
```bash
mssqlctl app list [--name -n] 
                  [--version -v]
```
### <a name="examples"></a>使用例
名前とバージョンでアプリケーションを一覧表示します。
```bash
mssqlctl app list --name reduce  --version v1
```
すべてのアプリケーションのバージョンを名前で一覧表示します。
```bash
mssqlctl app list --name reduce
```
すべてのアプリケーションのバージョンを名前で一覧表示します。
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
ログの詳細度を上げて、すべてのデバッグログを表示します。
#### `--help -h`
このヘルプメッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値は json です。
#### `--query -q`
Jのパスのクエリ文字列。 詳細[http://jmespath.org/](http://jmespath.org/])と例については、「」を参照してください。
#### `--verbose`
ログの詳細度を上げます。 完全なデバッグログには--debug を使用します。
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
ログの詳細度を上げて、すべてのデバッグログを表示します。
#### `--help -h`
このヘルプメッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値は json です。
#### `--query -q`
Jのパスのクエリ文字列。 詳細[http://jmespath.org/](http://jmespath.org/])と例については、「」を参照してください。
#### `--verbose`
ログの詳細度を上げます。 完全なデバッグログには--debug を使用します。
## <a name="mssqlctl-app-run"></a>mssqlctl アプリの実行
アプリケーションを実行します。
```bash
mssqlctl app run --name -n 
                 --version -v  
                 [--inputs]
```
### <a name="examples"></a>使用例
入力パラメーターを使用せずにアプリケーションを実行します。
```bash
mssqlctl app run --name reduce --version v1
```
1つの入力パラメーターを使用してアプリケーションを実行します。
```bash
mssqlctl app run --name reduce --version v1 --inputs x=10
```
複数の入力パラメーターを使用してアプリケーションを実行します。
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
## <a name="mssqlctl-app-describe"></a>mssqlctl アプリの説明
アプリケーションを記述します。
```bash
mssqlctl app describe [--spec -s] 
                      [--name -n]  
                      [--version -v]
```
### <a name="examples"></a>使用例
アプリケーションについて説明します。
```bash
mssqlctl app describe --name reduce --version v1    
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

その他の**mssqlctl**コマンドの詳細については、「 [mssqlctl reference](reference-mssqlctl.md)」を参照してください。 **Mssqlctl**ツールのインストール方法の詳細については、「 [install mssqlctl to manage SQL Server 2019 big data クラスター](deploy-install-mssqlctl.md)」を参照してください。