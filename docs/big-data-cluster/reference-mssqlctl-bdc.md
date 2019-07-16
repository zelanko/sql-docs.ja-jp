---
title: mssqlctl bdc の参照
titleSuffix: SQL Server big data clusters
description: Mssqlctl bdc コマンドに関する参照記事です。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/26/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: a9da2de60248246bee3daeeaee40d3071da69c4b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67957953"
---
# <a name="mssqlctl-bdc"></a>mssqlctl bdc

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

次の記事への参照を提供する、 **bdc**コマンド、 **mssqlctl**ツール。 その他の詳細については**mssqlctl**コマンドを参照してください[mssqlctl 参照](reference-mssqlctl.md)します。

## <a name="commands"></a>コマンド
|     |     |
| --- | --- |
[mssqlctl bdc を作成します。](#mssqlctl-bdc-create) | ビッグ データ クラスターを作成します。
[mssqlctl bdc の削除](#mssqlctl-bdc-delete) | ビッグ データ クラスターを削除します。
[mssqlctl bdc の構成](reference-mssqlctl-bdc-config.md) | 構成コマンド。
[mssqlctl bdc エンドポイント](reference-mssqlctl-bdc-endpoint.md) | エンドポイントのコマンド。
[mssqlctl bdc の状態](reference-mssqlctl-bdc-status.md) | 状態コマンド。
[mssqlctl bdc のデバッグ](reference-mssqlctl-bdc-debug.md) | コマンドをデバッグします。
[mssqlctl bdc 記憶域プール](reference-mssqlctl-bdc-storage-pool.md) | 記憶域プール コマンド。
[mssqlctl bdc コントロール](reference-mssqlctl-bdc-control.md) | 管理コマンド。
[mssqlctl bdc プール](reference-mssqlctl-bdc-pool.md) | プール コマンド。
## <a name="mssqlctl-bdc-create"></a>mssqlctl bdc を作成します。
SQL Server にビッグ データ クラスターの作成 - ['CONTROLLER_USERNAME'、'CONTROLLER_PASSWORD'、'DOCKER_USERNAME'、'DOCKER_PASSWORD'、'MSSQL_SA_PASSWORD'、'KNOX_PASSWORD'] は、次の環境変数とシステムの kube 構成が必要です。
```bash
mssqlctl bdc create [--config-profile -c] 
                    [--accept-eula -a]  
                    [--node-label -l]  
                    [--force -f]
```
### <a name="examples"></a>使用例
BDC 展開のガイド付きエクスペリエンス - 必要な値のプロンプトが表示されます。
```bash
mssqlctl bdc create
```
引数を持つ BDC 展開します。
```bash
mssqlctl bdc create --accept-eula yes --config-profile aks-dev-test
```
引数 - BDC 展開画面の指示として指定するありません--force フラグが使用されます。
```bash
mssqlctl bdc create --accept-eula yes --config-profile aks-dev-test --force
```
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--config-profile -c`
BDC 構成プロファイル、クラスターをデプロイするために使用します ['aks、開発、テスト '、' kubeadm、開発、テスト ', ' minikube、開発、テスト ']。
#### `--accept-eula -a`
ライセンス条項に同意しますか。 [はい/いいえ] です。 この引数を使用しない場合は、'yes' に ACCEPT_EULA 環境変数を設定することがあります。
#### `--node-label -l`
BDC ノードのラベルを展開するには、どのようなノードを指定するために使用します。
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
## <a name="mssqlctl-bdc-delete"></a>mssqlctl bdc の削除
SQL Server のビッグ データ クラスターを削除する-['CONTROLLER_USERNAME', 'CONTROLLER_PASSWORD'] は、次の環境変数とシステムの kube 構成が必要です。
```bash
mssqlctl bdc delete --name -n 
                    [--force -f]
```
### <a name="examples"></a>使用例
コント ローラーのユーザー名とパスワードが設定される場所既にシステムの環境で BDC を削除します。
```bash
mssqlctl bdc delete --name <cluster_name>
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--name -n`
Kubernetes 名前空間の使用、BDC 名。
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--force -f`
強制では、BDC を削除します。
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

## <a name="next-steps"></a>次の手順

その他の詳細については**mssqlctl**コマンドを参照してください[mssqlctl 参照](reference-mssqlctl.md)します。 インストールする方法について、 **mssqlctl**ツールを参照してください[インストールの SQL Server 2019 ビッグ データ クラスターを管理する mssqlctl](deploy-install-mssqlctl.md)します。
