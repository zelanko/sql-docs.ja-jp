---
title: SQL Server Always On 可用性グループを Kubernetes のデプロイ スクリプトを作成します。
description: この記事の SQL Server Always On 可用性グループに Kubernetes のデプロイ スクリプトを作成する方法を説明します
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 09/24/2018
ms.topic: article
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6541cae5271e35fd5ad0030ffc8625fc97a46149
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63231144"
---
# <a name="create-deployment-script-for-sql-server-always-on-availability-group"></a>SQL Server Always On 可用性グループのデプロイ スクリプトを作成します。

この記事では、配置スクリプトの例では 1 つのコマンドの Kubernetes クラスターで可用性グループを展開する方法について説明します。 `deploy-ag.py` Python スクリプトを作成するには、`.yaml`クラスター用のファイルし、Kubernetes クラスターにも適用できます。

ファイルのファイルをダウンロード[sql server のサンプル](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-deployment-script)します。

## <a name="before-you-start"></a>開始前の準備

ワークステーションに、次のツールをインストールします。

* [Python](https://www.python.org/downloads/) (3.5 または 3.6)
* [PyYAML](https://pyyaml.org/) -Python パッケージ
* [Kubernetes クライアント](https://github.com/kubernetes-client/python)-Python パッケージ

(Windows) の環境変数に python のパスを追加します。

### <a name="install-the-required-components"></a>必須コンポーネントをインストールします。

上記の次の例では、Python 用 PyYAML と Kubernetes クライアント パッケージをインストールします。

Python をインストールした後は、ダウンロードして、サンプルのフォルダーを抽出します。 

で、必要なファイルを構成するには、次のコマンドを実行します。 置換`<path>`抽出したサンプル ファイルの場所を使用します。

```cmd
pip install --user -r "C:\<path>\requirements.txt"
```

## <a name="create-cluster-and-download-config-file"></a>クラスターを作成し、構成ファイルをダウンロード

次の例では、Azure Kubernetes Service (AKS) クラスターを作成します。

スクリプトを実行する前に、山かっこ - の値を更新`<>`します。

```azcli
az aks create  --resource-group <GroupName> --name <ClusterName> --generate-ssh-keys --node-count 4 --kubernetes-version 1.11.1

az aks get-credentials --resource-group=<GroupName> --name=<ClusterName>
```

>[!NOTE]
>可用性グループには、Kubernetes バージョン 1.11.0 が必要がありますまたはそれ以降。 この例では、1.11.1 を指定します。

## <a name="run-the-deployment-script"></a>デプロイメント スクリプトを実行します。

次の例を実行する方法を示します`deploy-ag.py`します。

### <a name="help"></a>Help

```cmd
python ./deploy-ag.py --help
```

* **使用状況**: `deploy-ag.py [-h] {deploy | failover} ...`
* **省略可能な引数**:
  * `-h, --help` このヘルプ メッセージと終了を表示します。
* **サブコマンド**:
  * K8s エージェント上でアクション {0} 展開 | フェールオーバー}

  `deploy`

   可用性グループ内の SQL サーバーのセットをデプロイします。

  `failover`

   ターゲット レプリカにフェールオーバーします。

### <a name="deploy-help"></a>ヘルプをデプロイします。

```cmd
python ./deploy-ag.py deploy --help
```

* **使用状況**:

  ```
  python ./deploy-ag.py deploy [-h] [--verbose] [--ag AG] [-n NAMESPACE]
    [--dry-run] [-s SQL_SERVERS [SQL_SERVERS ...]]
    [-p SA_PASSWORD] [-e {ON_PREM,AKS}]
    [--skip-create-namespace]
  ```

  SQL Server と namespace(AG name) k8s エージェントを展開します。

* **省略可能な引数**:
  
  `-h, --help`
  
  このヘルプ メッセージと終了を表示します。
  
  `--verbose, -v`
  
  出力の詳細度
  
  `--ag AG`
  
  可用性グループの名前。 既定の ag1 を =
  
  `-n NAMESPACE, --namespace NAMESPACE`
  
  k8s 名前空間の名前です。 既定値は指定されていない場合、AG 名です。

  `--dry-run`
  
  マニフェストの作成が適用されません。
  
  `-s SQL_SERVERS [SQL_SERVERS ...], --sql-servers SQL_SERVERS [SQL_SERVERS ...]`

  SQL Server インスタンスの名前 (最大 5、スペースで区切られた) 既定 = ['mssql1'、'mssql2'、'mssql3']
  
  `-p SA_PASSWORD, --sa-password SA_PASSWORD`
  
  SA パスワードです。 Default='SAPassword2018'
  
  `-e {ON_PREM,AKS}, --env {ON_PREM,AKS}`
  
  `--skip-create-namespace`
  
  名前空間の作成をスキップします。

### <a name="failover-help"></a>フェールオーバーのヘルプ

```cmd
python ./deploy-ag.py failover --help
```
* **使用状況**: 

  ```cmd
  python deploy-ag.py failover [-h] [--verbose] [--ag AG]
    [--namespace NAMESPACE] [--dry-run]
    target_replica
  ```

  手動でフェールオーバー

* **位置指定引数**: `target_replica`

  フェールオーバーのターゲットの SQL Server レプリカの名前

* **省略可能な引数**:

  `-h, --help`
  
  このヘルプ メッセージと終了を表示します。

  `--verbose, -v`
  
  出力の詳細度

  `--ag AG`
  
  可用性グループの名前。 既定の ag1 を =

  `--namespace NAMESPACE`

  k8s 名前空間の名前です。 既定値は指定されていない場合、AG 名

  `--dry-run`
  
  作成するが、マニフェストには適用されません。

### <a name="create-the-manifests---dont-apply"></a>マニフェストの作成 - は適用されません。

次のスクリプトでは、マニフェスト ファイルを作成しますが、それらは適用されません。

```cmd
python ./deploy-ag.py deploy --dry-run
```

次の例は、可用性グループの名前空間でのマニフェストを作成`AG1`3 つのレプリカを使用します。 スクリプトを実行する前に置き換える`<MyC0m91exP@55w0r!>`複雑なパスワード。

```cmd
python ./deploy-ag.py deploy --ag ag1 --namespace AG1 --sa-password '<MyC0m91exP@55w0r!>' --env AKS --dry-run
```

前のコマンドは、サンプルの yaml ファイルのディレクトリを生成します。

この場合、コマンドの出力は、マニフェストのファイルが作成される場所を示しています。

![スクリプトの出力](./media/sql-server-linux-kubernetes-create-deployment/scriptbuild-out.png)
    
### <a name="create-the-manifests-and-apply"></a>マニフェストを作成および適用

次の例は、可用性グループの名前空間でのマニフェストを作成`ag1`3 つのレプリカを使用し、Kubernetes クラスターに適用します。 クラスターは、可用性グループを作成します。 スクリプトを実行する前に置き換える`<MyC0m91exP@55w0r!>`複雑なパスワード。

```
python ./deploy-ag.py deploy --ag ag1 --namespace ag1 --sa-password '<MyC0m91exP@55w0r!>' --env AKS --verbose
```

スクリプトが完了すると、Kubernetes の演算子は、ストレージ、SQL Server インスタンス、ロード バランサーのサービスを作成します。 展開を監視することができます[Kubernetes ダッシュ ボード](https://docs.microsoft.com/azure/aks/kubernetes-dashboard)します。

Kubernetes の後に、SQL Server のコンテナーを作成します。

1. [接続](sql-server-linux-kubernetes-connect.md)クラスター内の SQL Server インスタンスにします。

1. データベースの作成。

1. 完全なログ チェーンを開始するデータベースのバックアップを実行します。

1. データベースを可用性グループに追加します。

SQL Server は、適切なレプリカにセカンダリ データベースを自動的に作成します。 ために、自動シード処理で可用性グループが作成されます。

### <a name="manually-failover"></a>手動でフェールオーバー

次の例は、プライマリ レプリカによってフェールオーバーします。

```cmd
python ./deploy-ag.py failover --ag ag1 --namespace ag1 --verbose mssql1-0
```

## <a name="next-steps"></a>次のステップ

[Kubernetes クラスター上の SQL Server 可用性グループ](sql-server-ag-kubernetes.md)
