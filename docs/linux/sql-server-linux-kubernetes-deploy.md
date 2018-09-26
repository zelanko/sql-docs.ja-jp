---
title: SQL Server Always On 可用性グループに Kubernetes クラスターをデプロイします。
description: この記事では、要件については、SQL Server Kubernetes Always On 可用性グループ演算子グローバル パラメーターを説明します。
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 4d24cd2ab59e1a7959f5a8ac1c929ff2e5e8e54a
ms.sourcegitcommit: df21af652d0906ade8cc9ca3985a7ba5569f0db6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2018
ms.locfileid: "47049602"
---
# <a name="deploy-a-sql-server-always-on-availability-group-on-kubernetes-cluster"></a>Always On 可用性グループの Kubernetes クラスターで SQL Server をデプロイします。

## <a name="requirements"></a>要件

- Kubernetes クラスター
- Kubernetes バージョン 1.11.0 以降
- 次の 4 つまたは複数のノード
- [kubectl](http://kubernetes.io/docs/tasks/tools/install-kubectl/)します。

  >[!NOTE]
  >Kubernetes クラスターの任意の型を使用することができます。 Azure Kubernetes Service (AKS) での Kubernetes クラスターを作成するを参照してください。 [AKS クラスターの作成](http://docs.microsoft.com/azure/aks/create-cluster.md)です。
  > 次のスクリプトでは、Azure で 4 つのノードの Kubernetes クラスターを作成します。
  >```azure-cli
  az aks create --resource-group myResourceGroup --name myAKSCluster --node-count 4 --kubernetes-version 1.11.1
  >```

## <a name="steps"></a>手順

1. 記憶域を構成します。

  Azure のようなクラウド環境で構成[永続ボリューム](http://kubernetes.io/docs/concepts/storage/persistent-volumes/)SQL Server のインスタンスごとにします。

  Azure では、永続ボリュームを作成するを参照してください。`pv.yaml`と`pvc.yaml`で[sql server のサンプル](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-deployment-script/templates)します。

  次のコマンドを実行して、記憶域を作成します。

  ```azurecli
  kubectl apply -f <pv.yaml>
  ```

1. SA パスワードと、マスター _ キーの Kubernetes シークレットを作成します。

  次の例では、2 つのシークレットを作成します。 `sapassword` SA パスワードと`masterkeypassword`マスター _ キーです。 このスクリプトの置換を実行する前に`<MyC0mp13xP@55w04d!>`それぞれのシークレットの別の複雑なパスワード。

   ```azurecli
   kubectl create secret generic sql-secrets --from-literal='sapassword=<MyC0mp13xP@55w04d!>' --from-literal='masterkeypassword=<MyC0mp13xP@55w04d!>'
   ```

1. 構成し、SQL Server の演算子のマニフェストをデプロイします。

  SQL Server の演算子をコピー`operator.yaml`ファイルから[sql server のサンプル](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files)します。

  `operator.yaml`ファイルは、演算子の Kubernetes デプロイ manifiest します。

  マニフェストを構成するには、更新、`operator.yaml`環境内のファイル。

  マニフェストは、Kubernetes クラスターに適用されます。

  ```azurecli
  kubectl apply -f operator.yaml
  ```

1. SQL Server のカスタム リソースをデプロイします。

  SQL Server のマニフェストをコピー`sqlserver.yaml`から[sql server のサンプル](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files)します。

  マニフェストは、Kubernetes クラスターに適用されます。

  ```azurecli
  kubectl apply -f sqlserver.yaml
  ```

SQL Server のマニフェストを配置した後、演算子では、コンテナー内のポッドとしての SQL Server のインスタンスがデプロイします。

スクリプトが完了すると、Kubernetes の演算子は、ストレージ、SQL Server インスタンス、ロード バランサーのサービスに作成されます。 展開を監視することができます[Kubernetes ダッシュ ボード](http://docs.microsoft.com/azure/aks/kubernetes-dashboard)します。

Kubernetes を作成した後、SQL Server のコンテナーは、データベースを可用性グループに追加する次の手順を完了します。

1. [接続](sql-server-linux-kubernetes-connect.md)クラスター内の SQL Server インスタンスにします。

1. データベースの作成。

1. 完全なログ チェーンを開始するデータベースのバックアップを実行します。

1. データベースを可用性グループに追加します。

SQL Server がセカンダリ レプリカを自動的に作成するため、自動シード処理では、可用性グループが作成されます。

## <a name="next-steps"></a>次の手順

[Kubernetes クラスター上の SQL Server 可用性グループへの接続します。](sql-server-linux-kubernetes-connect.md)

[Kubernetes クラスター上の SQL Server 可用性グループを管理します。](sql-server-linux-kubernetes-manage.md)

[Kubernetes クラスター上の SQL Server 可用性グループ](sql-server-ag-kubernetes.md)