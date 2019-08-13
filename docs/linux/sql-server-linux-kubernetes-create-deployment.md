---
title: Kubernetes 上の SQL Server Always On 可用性グループ用の配置スクリプトを作成する
description: この記事では、Kubernetes 上の SQL Server Always On 可用性グループ用の配置スクリプトを作成する方法を説明します
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 09/24/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 181773a19e87c34a1931cae05f5a329aedbc1239
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2019
ms.locfileid: "68000134"
---
# <a name="create-deployment-script-for-sql-server-always-on-availability-group"></a>SQL Server Always On 可用性グループ用の配置スクリプトを作成する

この記事では、配置スクリプトの例で 1 つのコマンドを使って Kubernetes クラスターに可用性グループを配置する方法について説明します。 `deploy-ag.py` はクラスター用の `.yaml` ファイルを作成する Python スクリプトであり、Kubernetes クラスターに適用できます。

[sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-deployment-script) からファイルをダウンロードしてください。

## <a name="before-you-start"></a>開始前の準備

次のツールをワークステーションにインストールします。

* [Python](https://www.python.org/downloads/) (3.5 または 3.6)
* [PyYAML](https://pyyaml.org/) - Python パッケージ
* [Kubernetes クライアント](https://github.com/kubernetes-client/python) - Python パッケージ

Python のパスを環境変数に追加します (Windows の場合)。

### <a name="install-the-required-components"></a>必須コンポーネントをインストールする

次の例では、Python 用の PyYAML パッケージと Kubernetes クライアント パッケージをインストールします。

Python をインストールした後、サンプル フォルダーをダウンロードして抽出します。 

必要なファイルを構成するには、次のコマンドを実行します。 `<path>` は、抽出したサンプル ファイルの場所に置き換えます。

```cmd
pip install --user -r "C:\<path>\requirements.txt"
```

## <a name="create-cluster-and-download-config-file"></a>クラスターを作成して構成ファイルをダウンロードする

次の例では、Azure Kubernetes Service (AKS) でクラスターを作成します。

スクリプトを実行する前に、山かっこ `<>` 内の値を更新します。

```azcli
az aks create  --resource-group <GroupName> --name <ClusterName> --generate-ssh-keys --node-count 4 --kubernetes-version 1.11.1

az aks get-credentials --resource-group=<GroupName> --name=<ClusterName>
```

>[!NOTE]
>可用性グループでは、Kubernetes バージョン1.11.0 以降が必要です。 例では、1.11.1 を指定します。

## <a name="run-the-deployment-script"></a>配置スクリプトを実行する

次の例では、`deploy-ag.py` を実行する方法を示します。

### <a name="help"></a>ヘルプ

```cmd
python ./deploy-ag.py --help
```

* **使用方法**: `deploy-ag.py [-h] {deploy | failover} ...`
* **省略可能な引数**:
  * `-h, --help` は、このヘルプ メッセージを表示して終了します
* **サブコマンド**:
  * k8s エージェントでのアクション {deploy | failover}

  `deploy`

   可用性グループに SQL Server のセットを配置します

  `failover`

   ターゲット レプリカにフェールオーバーします。

### <a name="deploy-help"></a>配置のヘルプ

```cmd
python ./deploy-ag.py deploy --help
```

* **使用方法**:

  ```
  python ./deploy-ag.py deploy [-h] [--verbose] [--ag AG] [-n NAMESPACE]
    [--dry-run] [-s SQL_SERVERS [SQL_SERVERS ...]]
    [-p SA_PASSWORD] [-e {ON_PREM,AKS}]
    [--skip-create-namespace]
  ```

  名前空間 (AG 名) に SQL Server エージェントと k8s エージェントを配置します

* **省略可能な引数**:
  
  `-h, --help`
  
  このヘルプ メッセージを表示して終了します
  
  `--verbose, -v`
  
  出力の詳細度
  
  `--ag AG`
  
  可用性グループの名前。 既定値 = ag1
  
  `-n NAMESPACE, --namespace NAMESPACE`
  
  k8s 名前空間の名前。 指定されていない場合、既定で AG 名になります。

  `--dry-run`
  
  マニフェストを作成しますが、適用しません。
  
  `-s SQL_SERVERS [SQL_SERVERS ...], --sql-servers SQL_SERVERS [SQL_SERVERS ...]`

  SQL Server インスタンスの名前 (最大 5 つ、スペース区切り) 既定値 = ['mssql1', 'mssql2', 'mssql3']
  
  `-p SA_PASSWORD, --sa-password SA_PASSWORD`
  
  SA パスワード。 既定値 = 'SAPassword2018'
  
  `-e {ON_PREM,AKS}, --env {ON_PREM,AKS}`
  
  `--skip-create-namespace`
  
  名前空間の作成をスキップします。

### <a name="failover-help"></a>フェールオーバーのヘルプ

```cmd
python ./deploy-ag.py failover --help
```
* **使用方法**: 

  ```cmd
  python deploy-ag.py failover [-h] [--verbose] [--ag AG]
    [--namespace NAMESPACE] [--dry-run]
    target_replica
  ```

  手動でフェールオーバーします

* **位置引数**: `target_replica`

  フェールオーバーのターゲット SQL Server レプリカの名前

* **省略可能な引数**:

  `-h, --help`
  
  このヘルプ メッセージを表示して終了します

  `--verbose, -v`
  
  出力の詳細度

  `--ag AG`
  
  可用性グループの名前。 既定値 = ag1

  `--namespace NAMESPACE`

  k8s 名前空間の名前。 指定されていない場合、既定で AG 名になります

  `--dry-run`
  
  マニフェストを作成しますが、適用しません。

### <a name="create-the-manifests---dont-apply"></a>マニフェストを作成する - 適用しない

次のスクリプトでは、マニフェスト ファイルが作成されますが、適用されません。

```cmd
python ./deploy-ag.py deploy --dry-run
```

次の例では、`AG1` 名前空間の可用性グループに 3 つのレプリカを持つマニフェストが作成されます。 スクリプトを実行する前に、`<MyC0m91exP@55w0r!>` を複雑なパスワードに置き換えます。

```cmd
python ./deploy-ag.py deploy --ag ag1 --namespace AG1 --sa-password '<MyC0m91exP@55w0r!>' --env AKS --dry-run
```

前のコマンドでは、サンプルの yaml ファイルのディレクトリが生成されます。

この場合、コマンドの出力では、マニフェスト ファイルが作成された場所が示されます。

![スクリプトの出力](./media/sql-server-linux-kubernetes-create-deployment/scriptbuild-out.png)
    
### <a name="create-the-manifests-and-apply"></a>マニフェストを作成して適用する

次の例では、`ag1` 名前空間の可用性グループに 3 つのレプリカを持つマニフェストが作成され、Kubernetes クラスターにそれが適用されます。 その後、クラスターによって可用性グループが作成されます。 スクリプトを実行する前に、`<MyC0m91exP@55w0r!>` を複雑なパスワードに置き換えます。

```
python ./deploy-ag.py deploy --ag ag1 --namespace ag1 --sa-password '<MyC0m91exP@55w0r!>' --env AKS --verbose
```

スクリプトが完了した後、Kubernetes オペレーターはストレージ、SQL Server インスタンス、ロード バランサー サービスを作成します。 [Kubernetes ダッシュボード](https://docs.microsoft.com/azure/aks/kubernetes-dashboard)で配置を監視できます。

Kubernetes で SQL Server コンテナーが作成された後:

1. クラスター内の SQL Server インスタンスに[接続](sql-server-linux-kubernetes-connect.md)します。

1. データベースの作成。

1. データベースの完全バックアップを実行して、ログ チェーンを開始します。

1. 可用性グループにデータベースを追加します。

可用性グループは自動シード処理で作成されるため、SQL Server によって適切なレプリカにセカンダリ データベースが自動的に作成されます。

### <a name="manually-failover"></a>手動でフェールオーバーします

次の例では、プライマリ レプリカがフェールオーバーされます。

```cmd
python ./deploy-ag.py failover --ag ag1 --namespace ag1 --verbose mssql1-0
```

## <a name="next-steps"></a>次の手順

[Kubernetes クラスターの SQL Server　可用性グループ](sql-server-ag-kubernetes.md)
