---
title: mssqlctl クラスターの参照
titleSuffix: SQL Server big data clusters
description: Mssqlctl クラスター コマンドに関する参照記事です。
author: rothja
ms.author: jroth
manager: jroth
ms.date: 05/22/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 654888bc27fec43abb8a8f511b0de7a4972e4377
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66779257"
---
# <a name="mssqlctl-cluster"></a>mssqlctl クラスター

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

次の記事への参照を提供する、**クラスター**コマンド、 **mssqlctl**ツール。 その他の詳細については**mssqlctl**コマンドを参照してください[mssqlctl 参照](reference-mssqlctl.md)します。

## <a name="commands"></a>コマンド
|     |     |
| --- | --- |
[mssqlctl クラスターを作成します。](#mssqlctl-cluster-create) | クラスターを作成します。
[mssqlctl cluster delete](#mssqlctl-cluster-delete) | クラスターを削除します。
[mssqlctl クラスターの構成](reference-mssqlctl-cluster-config.md) | クラスターの構成コマンド。
[mssqlctl クラスター エンドポイント](reference-mssqlctl-cluster-endpoint.md) | エンドポイントのコマンド。
[mssqlctl クラスターの状態](reference-mssqlctl-cluster-status.md) | 状態コマンド。
[mssqlctl クラスター デバッグ](reference-mssqlctl-cluster-debug.md) | コマンドをデバッグします。
[mssqlctl クラスター記憶域プール](reference-mssqlctl-cluster-storage-pool.md) | クラスターの記憶域プールを管理します。
## <a name="mssqlctl-cluster-create"></a>mssqlctl クラスターを作成します。
SQL Server にビッグ データ クラスターの作成 - ['CONTROLLER_USERNAME'、'CONTROLLER_PASSWORD'、'DOCKER_USERNAME'、'DOCKER_PASSWORD'、'MSSQL_SA_PASSWORD'、'KNOX_PASSWORD'] は、次の環境変数とシステムの kube 構成が必要です。
```bash
mssqlctl cluster create [--config-file -c] 
                        [--accept-eula -a]  
                        [--node-label -l]  
                        [--force -f]
```
### <a name="examples"></a>使用例
クラスターのデプロイ操作のガイド付きの値が必要なメッセージが表示されます。
```bash
mssqlctl cluster create
```
引数を持つクラスターのデプロイ。
```bash
mssqlctl cluster create --accept-eula yes --config-file aks-dev-test.json
```
フラグの使用-force として引数 - プロンプトなしでクラスターのデプロイが与えられます。
```bash
mssqlctl cluster create --accept-eula yes --config-file aks-dev-test.json --force
```
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--config-file -c`
Cluster config profile, used for deploying the cluster: ['aks-dev-test.json', 'kubeadm-dev-test.json', 'minikube-dev-test.json']
#### `--accept-eula -a`
ライセンス条項に同意しますか。 [はい/いいえ] です。 この引数を使用しない場合は、'yes' に ACCEPT_EULA 環境変数を設定することがあります。
#### `--node-label -l`
クラスター ノードのラベルを展開するには、どのようなノードを指定するために使用します。
#### `--force -f`
列の値もないユーザーを求めるを強制の作成、およびすべての問題が標準エラー出力の一部として使用されます。
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
## <a name="mssqlctl-cluster-delete"></a>mssqlctl cluster delete
SQL Server のビッグ データ クラスターを削除する-['CONTROLLER_USERNAME', 'CONTROLLER_PASSWORD'] は、次の環境変数とシステムの kube 構成が必要です。
```bash
mssqlctl cluster delete --name -n 
                        [--force -f]
```
### <a name="examples"></a>使用例
コント ローラーのユーザー名とパスワードが設定される場所既にシステムの環境でクラスターを削除します。
```bash
mssqlctl cluster delete --name <cluster_name>
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--name -n`
クラスター名 kubernetes 名前空間に使用をします。
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--force -f`
強制削除クラスター。
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
