---
title: mssqlctl bdc config reference
titleSuffix: SQL Server big data clusters
description: Mssqlctl bdc コマンドに関する参照記事です。
author: rothja
ms.author: jroth
manager: jroth
ms.date: 06/26/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: f57ba87ea7cbd770380497bd340b5eaa4d80f29c
ms.sourcegitcommit: ce5770d8b91c18ba5ad031e1a96a657bde4cae55
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2019
ms.locfileid: "67394164"
---
# <a name="mssqlctl-bdc-config"></a>mssqlctl bdc config

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

次の記事への参照を提供する、 **bdc config**コマンドを**mssqlctl**ツール。 その他の詳細については**mssqlctl**コマンドを参照してください[mssqlctl 参照](reference-mssqlctl.md)します。

## <a name="commands"></a>コマンド
|     |     |
| --- | --- |
[mssqlctl bdc config show](#mssqlctl-bdc-config-show) | ビッグ データ クラスターの現在の構成を取得します。
[mssqlctl bdc config init](#mssqlctl-bdc-config-init) | クラスターで使用できる構成プロファイルを作成、ビッグ データ クラスターを初期化します。
[mssqlctl bdc config list](#mssqlctl-bdc-config-list) | 使用可能な構成プロファイルの選択内容を一覧表示します。
[mssqlctl bdc config section](reference-mssqlctl-bdc-config-section.md) | 個々 のセクションでは、「ビッグ データ クラスターの構成プロファイルを操作するコマンド。
## <a name="mssqlctl-bdc-config-show"></a>mssqlctl bdc config show
ビッグ データ クラスターの現在の構成プロファイルを取得し、ターゲット ディレクトリに出力またはかなりし、コンソールに出力します。
```bash
mssqlctl bdc config show [--target -t] 
                         [--force -f]
```
### <a name="examples"></a>使用例
コンソールで、BDC 構成を表示します。
```bash
mssqlctl bdc config show
```
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--target -t`
結果を格納する出力ファイル。 既定値: は stdout に送られます。
#### `--force -f`
ターゲット ファイルの上書きを強制します。
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
## <a name="mssqlctl-bdc-config-init"></a>mssqlctl bdc config init
クラスターで使用できる構成プロファイルを作成、ビッグ データ クラスターを初期化します。 構成プロファイルの特定のソースは、3 つの選択肢から引数を指定できます。
```bash
mssqlctl bdc config init [--target -t] 
                         [--source -s]  
                         [--force -f]
```
### <a name="examples"></a>使用例
BDC config init エクスペリエンス ガイド付き - 必要な値のプロンプトが表示されます。
```bash
mssqlctl bdc config init
```
引数を BDC config init aks、開発、テストでの構成プロファイルを作成します。 カスタム/。
```bash
mssqlctl bdc config init --source aks-dev-test --target custom
```
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--target -t`
既定値はカスタム config.json と cwd 先、構成プロファイルとなるファイルのパスが配置されます。
#### `--source -s`
Config profile source: ['aks-dev-test', 'kubeadm-dev-test', 'minikube-dev-test']
#### `--force -f`
ターゲット ファイルの上書きを強制します。
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
## <a name="mssqlctl-bdc-config-list"></a>mssqlctl bdc config list
使用するため利用可能な構成プロファイルの選択内容を一覧表示されます。 `bdc config init`
```bash
mssqlctl bdc config list [--config-profile -c] 
                         
```
### <a name="examples"></a>使用例
すべての利用可能な構成プロファイル名を示します。
```bash
mssqlctl bdc config list
```
特定の構成プロファイルの json を示しています。
```bash
mssqlctl bdc config list --config-profile aks-dev-test
```
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--config-profile -c`
Default config profile: ['aks-dev-test', 'kubeadm-dev-test', 'minikube-dev-test']
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