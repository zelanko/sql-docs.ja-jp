---
title: mssqlctl クラスター構成の参照
titleSuffix: SQL Server big data clusters
description: Mssqlctl クラスター コマンドに関する参照記事です。
author: rothja
ms.author: jroth
manager: jroth
ms.date: 05/22/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 74097057702ad32a803c440d92b0ed7c8f855880
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66779419"
---
# <a name="mssqlctl-cluster-config"></a>mssqlctl クラスターの構成

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

次の記事への参照を提供する、**クラスターの構成**コマンド、 **mssqlctl**ツール。 その他の詳細については**mssqlctl**コマンドを参照してください[mssqlctl 参照](reference-mssqlctl.md)します。

## <a name="commands"></a>コマンド
|     |     |
| --- | --- |
[mssqlctl クラスター構成の表示](#mssqlctl-cluster-config-show) | SQL Server ビッグ データ クラスターの現在の構成を取得します。
[mssqlctl クラスター構成の初期化](#mssqlctl-cluster-config-init) | クラスターで使用できるクラスターの構成プロファイルの作成を初期化します。
[mssqlctl クラスター構成の一覧](#mssqlctl-cluster-config-list) | 使用可能な構成ファイルの選択を一覧表示します。
[mssqlctl クラスターの構成セクション](reference-mssqlctl-cluster-config-section.md) | クラスターの構成ファイルの個々 のセクションを操作するコマンド。
## <a name="mssqlctl-cluster-config-show"></a>mssqlctl cluster config show
SQL Server ビッグ データ クラスターの現在の構成ファイルを取得およびターゲット ファイルに出力またはかなりし、コンソールに出力します。
```bash
mssqlctl cluster config show [--target -t] 
                             [--force -f]
```
### <a name="examples"></a>使用例
コンソールで、クラスターの構成を表示します。
```bash
mssqlctl cluster config show
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
## <a name="mssqlctl-cluster-config-init"></a>mssqlctl cluster config init
クラスターで使用できるクラスターの構成プロファイルの作成を初期化します。 構成プロファイルの特定のソースは、3 つの選択肢から引数を指定できます。
```bash
mssqlctl cluster config init [--target -t] 
                             [--src -s]  
                             [--force -f]
```
### <a name="examples"></a>使用例
クラスター構成の init 画面 - の指示に従って必要な値のメッセージが表示されます。
```bash
mssqlctl cluster config init
```
クラスターの引数を持つ構成 init、aks、開発、テストでの構成プロファイルを作成します。/custom.json します。
```bash
mssqlctl cluster config init --src aks-dev-test.json --target custom.json
```
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--target -t`
既定値はカスタム config.json と cwd 先、構成プロファイルとなるファイルのパスが配置されます。
#### `--src -s`
Config profile source: ['aks-dev-test.json', 'kubeadm-dev-test.json', 'minikube-dev-test.json']
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
## <a name="mssqlctl-cluster-config-list"></a>mssqlctl cluster config list
クラスター構成の初期化で使用するための使用可能な構成ファイルの選択を一覧表示されます。
```bash
mssqlctl cluster config list [--config-file -c] 
                             
```
### <a name="examples"></a>使用例
すべての利用可能な構成プロファイル名を示します。
```bash
mssqlctl cluster config list
```
特定の構成プロファイルの json を示しています。
```bash
mssqlctl cluster config list --config-file aks-dev-test.json
```
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--config-file -c`
Default config file: ['aks-dev-test.json', 'kubeadm-dev-test.json', 'minikube-dev-test.json']
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