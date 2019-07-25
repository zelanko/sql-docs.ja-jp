---
title: azdata bdc リファレンス
titleSuffix: SQL Server big data clusters
description: Azdata bdc コマンドのリファレンス記事です。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 488394cbf4b52a952ffc46ab2ec6c9a273466bd5
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426042"
---
# <a name="azdata-bdc"></a>azdata bdc

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

次の記事では、 **azdata**ツールの**bdc**コマンドのリファレンスを示します。 その他の**azdata**コマンドの詳細については、「 [azdata reference](reference-azdata.md)」を参照してください。

## <a name="commands"></a>コマンド

|     |     |
| --- | --- |
[azdata bdc の作成](#azdata-bdc-create) | ビッグデータクラスターを作成します。
[azdata bdc の削除](#azdata-bdc-delete) | ビッグデータクラスターを削除します。
[azdata bdc の構成](reference-azdata-bdc-config.md) | 構成コマンド。
[azdata bdc エンドポイント](reference-azdata-bdc-endpoint.md) | エンドポイントコマンド。
[azdata bdc の状態](reference-azdata-bdc-status.md) | Status コマンド。
[azdata bdc デバッグ](reference-azdata-bdc-debug.md) | デバッグコマンド。
[azdata bdc コントロール](reference-azdata-bdc-control.md) | 制御コマンド。
[azdata bdc プール](reference-azdata-bdc-pool.md) | プールコマンド。
[azdata bdc hdfs](reference-azdata-bdc-hdfs.md) | HDFS モジュールには、HDFS ファイルシステムにアクセスするためのコマンドが用意されています。
[azdata bdc spark](reference-azdata-bdc-spark.md) | Spark コマンドを使用すると、セッション、ステートメント、およびバッチを作成して管理することで、ユーザーは Spark システムと対話できます。
## <a name="azdata-bdc-create"></a>azdata bdc の作成
SQL Server ビッグデータクラスターを作成する-kube config は、次の環境変数 [' CONTROLLER_USERNAME '、' CONTROLLER_PASSWORD '、' MSSQL_SA_PASSWORD '、' KNOX_PASSWORD '] と共に、システムに必要です。
```bash
azdata bdc create [--name -n] 
                  [--config-profile -c]  
                  [--accept-eula -a]  
                  [--node-label -l]  
                  [--force -f]
```
### <a name="examples"></a>使用例

ガイド付き BDC のデプロイエクスペリエンス-必要な値の入力を求めるメッセージが表示されます。

```bash
azdata bdc create
```

引数を使用した BDC デプロイ。

```bash
azdata bdc create --accept-eula yes --config-profile aks-dev-test
```
プロファイルに既定の名前ではなく、指定された名前の BDC 展開。
```bash
azdata bdc create --name <cluster_name> --accept-eula yes --config-profile aks-dev-test --force
```

引数を使用した BDC デプロイ--force フラグが使用されるため、プロンプトは表示されません。

```bash
azdata bdc create --accept-eula yes --config-profile aks-dev-test --force
```

### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--name -n`
ビッグデータクラスター名。 kubernetes 名前空間に使用されます。
#### `--config-profile -c`
クラスターをデプロイするために使用されるビッグデータクラスター構成プロファイル: [' aks ', ' kubeadm ', ' minikube ', ' ']
#### `--accept-eula -a`
ライセンス条項に同意しますか? [はい/いいえ]。 この引数を使用しない場合は、環境変数 ACCEPT_EULA を "yes" に設定します。 この製品のライセンス条項については、 https://aka.ms/azdata-eula 「 https://go.microsoft.com/fwlink/?LinkId=2002534 」および「」を参照してください。
#### `--node-label -l`
ビッグデータクラスターノードラベル。デプロイ先のノードを指定するために使用されます。
#### `--force -f`
強制的に作成すると、ユーザーに値の入力を求められることはなく、すべての問題が stderr の一部として出力されます。
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
## <a name="azdata-bdc-delete"></a>azdata bdc の削除
次の環境変数 [' CONTROLLER_USERNAME ', ' CONTROLLER_PASSWORD '] と共に、システムで kube config が必要な SQL Server を削除します。
```bash
azdata bdc delete --name -n 
                  [--force -f]
```
### <a name="examples"></a>使用例
システム環境で、コントローラーのユーザー名とパスワードが既に設定されている BDC の削除。
```bash
azdata bdc delete --name <cluster_name>
```
### <a name="required-parameters"></a>必要なパラメーター
#### `--name -n`
ビッグデータクラスター名。 kubernetes 名前空間に使用されます。
### <a name="optional-parameters"></a>省略可能なパラメーター
#### `--force -f`
ビッグデータクラスターを強制的に削除します。
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
