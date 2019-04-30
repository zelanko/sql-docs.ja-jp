---
title: mssqlctl クラスター構成の参照
titleSuffix: SQL Server big data clusters
description: Mssqlctl クラスター コマンドに関する参照記事です。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 04/23/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 3a4693c5ffb68ad555d97d02f983fadf4e6bbd9a
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "63473297"
---
# <a name="mssqlctl-cluster-config"></a>mssqlctl クラスターの構成

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

次の記事への参照を提供する、**クラスターの構成**コマンド、 **mssqlctl**ツール。 その他の詳細については**mssqlctl**コマンドを参照してください[mssqlctl 参照](reference-mssqlctl.md)します。

## <a name="commands"></a>コマンド
|     |     |
| --- | --- |
[mssqlctl クラスター構成を取得します。](#mssqlctl-cluster-config-get) | クラスターの構成 - kube の取得、システム構成が必要です。
[mssqlctl クラスター構成の初期化](#mssqlctl-cluster-config-init) | クラスター構成を初期化します。
[mssqlctl クラスター構成の一覧](#mssqlctl-cluster-config-list) | 使用可能な構成ファイルの選択を一覧表示します。
[mssqlctl クラスターの構成セクション](reference-mssqlctl-cluster-config-section.md) | 構成ファイルの個々 のセクションを操作するコマンド。
## <a name="mssqlctl-cluster-config-get"></a>mssqlctl クラスター構成を取得します。
SQL Server ビッグ データ クラスターの現在の構成ファイルを取得します。
```bash
mssqlctl cluster config get --name -n 
                            [--output-file -f]
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--name -n`
クラスター名 kubernetes 名前空間に使用をします。
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--output-file -f`
結果を格納する出力ファイル。 既定値: は stdout に送られます。
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
指定した既定の種類に基づくユーザーのクラスター構成ファイルを初期化します。
```bash
mssqlctl cluster config init [--target -t] 
                             [--src -s]
```
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--target -t`
既定値はカスタム config.json と cwd 先、構成ファイルとなるファイルのパスが配置されます。
#### `--src -s`
Config source: ['aks-dev-test.json', 'kubeadm-dev-test.json', 'minikube-dev-test.json']
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
mssqlctl cluster config list [--config-file -f] 
                             
```
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--config-file -f`
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