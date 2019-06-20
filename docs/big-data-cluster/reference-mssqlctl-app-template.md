---
title: mssqlctl アプリ テンプレート リファレンス
titleSuffix: SQL Server big data clusters
description: Mssqlctl アプリ テンプレート コマンドに関する参照記事です。
author: rothja
ms.author: jroth
manager: jroth
ms.date: 04/23/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 9e73b0ddf9e30c5e38fd54d34ab93526213fe061
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66800971"
---
# <a name="mssqlctl-app-template"></a>mssqlctl アプリ テンプレート

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

次の記事への参照を提供する、**アプリ テンプレート**コマンド、 **mssqlctl**ツール。 その他の詳細については**mssqlctl**コマンドを参照してください[mssqlctl 参照](reference-mssqlctl.md)します。

## <a name="commands"></a>コマンド
|     |     |
| --- | --- |
[mssqlctl アプリ テンプレートの一覧](#mssqlctl-app-template-list) | サポートされているテンプレートをフェッチします。
[mssqlctl アプリ テンプレートのプル](#mssqlctl-app-template-pull) | サポートされているテンプレートをダウンロードします。
## <a name="mssqlctl-app-template-list"></a>mssqlctl アプリ テンプレートの一覧
[URL] の指定した github リポジトリでサポートされているテンプレートをフェッチします。
```bash
mssqlctl app template list [--url -u] 
                           
```
### <a name="examples"></a>使用例
既定のテンプレート リポジトリの場所のすべてのテンプレートをフェッチします。
```bash
mssqlctl app template list
```
別のリポジトリ場所のすべてのテンプレートをフェッチします。
```bash
mssqlctl app template list --url https://github.com/diffrent/templates.git
```
### <a name="optional-parameters"></a>省略可能なパラメーター
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
## <a name="mssqlctl-app-template-pull"></a>mssqlctl アプリ テンプレートのプル
[URL] の指定した github リポジトリでサポートされているテンプレートをダウンロードします。
```bash
mssqlctl app template pull [--name -n] 
                           [--url -u]  
                           [--destination -d]
```
### <a name="examples"></a>使用例
既定のテンプレート リポジトリの場所のすべてのテンプレートをダウンロードします。
```bash
mssqlctl app template pull
```
別のリポジトリ場所のすべてのテンプレートをダウンロードします。
```bash
mssqlctl app template list --url https://github.com/diffrent/templates.git
```
名前では、個々 のテンプレートをダウンロードします。
```bash
mssqlctl app template pull --name ssis            
```
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--name -n`
テンプレートの名前。 サポートされているテンプレート namesrun オフの完全な一覧について `mssqlctl app template list`
#### `--url -u`
別のテンプレート リポジトリの場所を指定します。 既定値: https://github.com/Microsoft/SQLBDC-AppDeploy.git
#### `--destination -d`
アプリケーションのスケルトン テンプレートを配置する場所。
`./templates`
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