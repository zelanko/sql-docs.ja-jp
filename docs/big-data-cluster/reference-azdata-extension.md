---
title: azdata 拡張機能リファレンス
titleSuffix: SQL Server big data clusters
description: azdata 拡張機能コマンドのリファレンス記事です。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/22/2020
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 9e2585a77c3117df8514622728d0f09df93d7bc2
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/28/2020
ms.locfileid: "87243000"
---
# <a name="azdata-extension"></a>azdata 拡張機能

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

以下の記事では、`azdata` ツールの `sql` コマンドに関するリファレンスを提供します。 `azdata` の他のコマンドに関する詳細については、[azdata のリファレンス](reference-azdata.md)に関するページをご覧ください。

## <a name="commands"></a>コマンド
| command | 説明 |
| --- | --- |
[azdata extension add](#azdata-extension-add) | 拡張機能を追加します。
[azdata extension remove](#azdata-extension-remove) | 拡張機能を削除します。
[azdata extension list](#azdata-extension-list) | インストールされているすべての拡張機能を一覧表示します。
## <a name="azdata-extension-add"></a>azdata extension add
拡張機能を追加します。
```bash
azdata extension add --source -s 
                     [--index]  
                     
[--pip-proxy]  
                     
[--pip-extra-index-urls]  
                     
[--yes -y]
```
### <a name="examples"></a>例
URL から拡張機能を追加します。
```bash
azdata extension add --source https://contoso.com/some_ext-0.0.1-py2.py3-none-any.whl
```
ローカル ディスクから拡張機能を追加します。
```bash
azdata extension add --source ~/some_ext-0.0.1-py2.py3-none-any.whl
```
ローカル ディスクから拡張機能を追加し、依存関係に pip プロキシを使用します。
```bash
azdata extension add --source ~/some_ext-0.0.1-py2.py3-none-any.whl --pip-proxy https://user:pass@proxy.server:8080
```
### <a name="required-parameters"></a>必須のパラメーター
#### `--source -s`
ディスク上の拡張機能ホイールへのパスまたは拡張機能の URL
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--index`
Python パッケージ インデックスのベース URL (既定: https://pypi.org/simple) 。 これは、PEP 503 (simple repository API) に準拠しているリポジトリ、または同じ形式でレイアウトされたローカル ディレクトリを指している必要があります。
#### `--pip-proxy`
[user:passwd@]proxy.server:port の形式で拡張機能の依存関係に使用する pip のプロキシ
#### `--pip-extra-index-urls`
使用するパッケージ インデックスの追加 URL のスペース区切りの一覧です。 これは、PEP 503 (simple repository API) に準拠しているリポジトリ、または同じ形式でレイアウトされたローカル ディレクトリを指している必要があります。
#### `--yes -y`
確認のダイアログを表示しません。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
すべてのデバッグ ログを表示するようにログの詳細レベルを上げます。
#### `--help -h`
このヘルプ メッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値: json。
#### `--query -q`
JMESPath クエリ文字列。 詳細と例については、[http://jmespath.org/](http://jmespath.org) を参照してください。
#### `--verbose`
ログの詳細レベルを上げます。 詳細なデバッグ ログを表示するには --debug を使います。
## <a name="azdata-extension-remove"></a>azdata extension remove
拡張機能を削除します。
```bash
azdata extension remove --name -n 
                        [--yes -y]
```
### <a name="examples"></a>例
拡張機能を削除します。
```bash
azdata extension remove --name some-ext
```
### <a name="required-parameters"></a>必須のパラメーター
#### `--name -n`
拡張機能の名前
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--yes -y`
確認のダイアログを表示しません。
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
すべてのデバッグ ログを表示するようにログの詳細レベルを上げます。
#### `--help -h`
このヘルプ メッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値: json。
#### `--query -q`
JMESPath クエリ文字列。 詳細と例については、[http://jmespath.org/](http://jmespath.org) を参照してください。
#### `--verbose`
ログの詳細レベルを上げます。 詳細なデバッグ ログを表示するには --debug を使います。
## <a name="azdata-extension-list"></a>azdata extension list
インストールされているすべての拡張機能を一覧表示します。
```bash
azdata extension list 
```
### <a name="examples"></a>例
拡張機能を一覧表示します。
```bash
azdata extension list
```
### <a name="global-arguments"></a>グローバル引数
#### `--debug`
すべてのデバッグ ログを表示するようにログの詳細レベルを上げます。
#### `--help -h`
このヘルプ メッセージを表示して終了します。
#### `--output -o`
出力形式。  使用できる値: json、jsonc、table、tsv。  既定値: json。
#### `--query -q`
JMESPath クエリ文字列。 詳細と例については、[http://jmespath.org/](http://jmespath.org) を参照してください。
#### `--verbose`
ログの詳細レベルを上げます。 詳細なデバッグ ログを表示するには --debug を使います。

## <a name="next-steps"></a>次のステップ

`azdata` の他のコマンドに関する詳細については、[azdata のリファレンス](reference-azdata.md)に関するページをご覧ください。 `azdata` ツールのインストール方法の詳細については、[SQL Server 2019 ビッグ データ クラスターを管理する azdata のインストール](deploy-install-azdata.md)に関するページを参照してください。
