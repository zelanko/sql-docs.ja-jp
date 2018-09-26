---
title: Kubernetes での Docker コンテナー上の SQL Server Always On 可用性グループの構成 |Microsoft Docs
description: このチュートリアルでは、Azure Container Service で Kubernetes を使用した SQL Server always on 可用性グループをデプロイする方法を説明します。
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/09/2018
ms.topic: tutorial
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux,mvc
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6d21866f3f7004dff1ea86ca4f608580a79ab754
ms.sourcegitcommit: df21af652d0906ade8cc9ca3985a7ba5569f0db6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2018
ms.locfileid: "47049362"
---
# <a name="configure-a-sql-server-always-on-availability-group-on-docker-containers-in-kubernetes-with-azure-kubernetes-service-aks"></a>Azure Kubernetes Service (AKS) での Kubernetes での Docker コンテナー上の SQL Server Always On 可用性グループを構成します。

このチュートリアルでは、AKS でのコンテナーで高可用性 SQL Server インスタンスを構成する方法を示します。 できます[Kubernetes での SQL Server のコンテナーのデプロイ](tutorial-sql-server-containers-kubernetes.md)します。 2 つの異なる Kubernetes ソリューションを比較するを参照してください。[の高可用性 SQL Server のコンテナーを](sql-server-linux-container-ha-overview.md)します。

このチュートリアルで確認する方法。  

> [!div class="checklist"]
> * ストレージを作成します。
> * SQL Server の演算子を Kubernetes クラスターにデプロイします。 
> * Kubernetes シークレットを作成します。
> * SQL Server インスタンスと正常性エージェントを展開します。
> * プライマリ レプリカに接続します。
> * 可用性グループにデータベースを追加する

このチュートリアルでは、アーキテクチャを示します[Azure Kubernetes Service (AKS)](http://docs.microsoft.com/azure/aks/)します。 Azure サブスクリプションを持っていない場合は、作成、[無料アカウント](https://azure.microsoft.com/free/?WT.mc_id=A261C142F)開始する前にします。

この図では、このチュートリアルでは、ソリューションを表します。

![kubernetes の可用性グループのクラスター](media/tutorial-sql-server-ag-containers-kubernetes/KubernetesCluster.png)

### <a name="deployment-methodology-for-kubernetes"></a>Kubernetes のデプロイ方法

この記事の手順のいくつかは、マニフェストを作成し、クラスター マニフェストをデプロイします。 マニフェストは、展開する Kubernetes オブジェクトの説明で .yaml ファイルです。

この例では .yaml ファイルは、「 [sql server のサンプル](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability)します。

オブジェクトには、ストレージ、演算子、ポッド、コンテナー、およびサービスが含まれます。

## <a name="prerequisites"></a>前提条件

* これらのテクノロジに関する一般的な知識

  * [Kubernetes](http://kubernetes.io)バージョン 1.8
  * [Azure Kubernetes Service (AKS)](http://docs.microsoft.com/azure/aks/)
  * [SQL Server on Docker](quickstart-install-connect-docker.md)
  * [SQL Server Always On 可用性グループ](../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)

* 4 つのノードの Kubernetes クラスター。

  手順についてを参照してください[チュートリアル: Azure Kubernetes Service (AKS) クラスターのデプロイ](http://docs.microsoft.com/azure/aks/tutorial-kubernetes-deploy-cluster)します。

* インストール[ `kubectl`](https://docs.microsoft.com/en-us/azure/aks/tutorial-kubernetes-deploy-cluster#install-the-kubectl-cli)します。

## <a name="configuration-and-deployment-procedures"></a>構成と展開の手順

このチュートリアルでは、Kubernetes クラスターに .yaml ファイルを適用する方法を示します。

## <a name="create-the-secrets"></a>シークレットを作成します。

SQL Server SA アカウントと、SQL Server のマスター _ キーのパスワードを保存する Kubernetes シークレットを作成するには、次のコマンドを実行します。

```azurecli
kubectl create secret generic sql-secrets --from-literal=sapassword="MyC0m9l&xP@ssw0rd" --from-literal=masterkeypassword="MyC0m9l&xP@ssw0rd2"
```

運用環境では、さまざまな、複雑なパスワードを使用します。

## <a name="deploy-the-operator"></a>演算子をデプロイします。

Kubernetes 演算子は、SQL Server のインスタンスをデプロイし、Kubernetes クラスターで可用性グループを構成します。 

例のオペレーターを参照してください。 [`operator.yaml`](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/operator.yaml)

ダウンロード`operator.yaml`から[sql server のサンプル](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/)

Kubernetes のデプロイの 1 つのレプリカとして、演算子を展開します。

演算子を展開するには。

演算子を展開、`kubectl apply`コマンド。

```azurecli
kubectl apply -f operator.yaml
```

## <a name="create-the-sql-server-ag-deployment"></a>SQL Server 可用性グループのデプロイを作成します。

次の手順では、1 つの Kubernetes のデプロイで、SQL Server インスタンスと可用性グループを作成します。 クラスターにこの展開を適用した後、演算子は Docker コンテナーとして、SQL Server インスタンスをデプロイします。 このデプロイは、1 つのポッドと次の 3 つの StatefulSets になります。 すべてのポッドで 2 つのコンテナーが含まれます。

* SQL Server インスタンスに基づいて、`mssql-server`イメージ
* HA スーパーバイザー

さらに、展開が、可用性グループ リスナーのロード バランサーのサービスについて説明します

Mssql server を展開します。

1. コピー [sqlserver.yaml](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/sqlserver.yaml)をコンピューターにします。
2. Update`sqlserver.yaml`環境。


で、SQL Server インスタンスをデプロイして、可用性グループを作成するには、次のコマンドを実行します。

```azurecli
kubectl apply -f sqlserver.yaml
```

## <a name="deploy-ag-services"></a>サービスの可用性グループのデプロイ

Kubernetes クラスターでは、可用性グループ内のレプリカへの直接呼び出しをロード バランサーのサービスを作成します。

[ag services.yaml](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files) 4 つのサービスを作成します。

* ag1 プライマリは、プライマリ レプリカに接続します。
* ag1-sync セカンダリは同期セカンダリ レプリカに接続します。
* ag1-async セカンダリは、非同期のセカンダリ レプリカに接続します。
* ag1-config セカンダリは、構成のみのレプリカに接続します。 

  >[!NOTE]
  >例として、これらのロード バランサーのサービスが提供されます。 このチュートリアルでは構成専用レプリカは。


ロード バランサーのサービスを展開し、可用性グループに接続できるようにします。

サービスをデプロイするには、次のコマンドを実行します。

```azurecli
kubectl apply -f ag-services.yaml
```

### <a name="monitor-the-deployment"></a>展開を監視します。

使用することができます[Azure Kubernetes Service (AKS) での Kubernetes ダッシュ ボード](https://docs.microsoft.com/en-us/azure/aks/kubernetes-dashboard)展開の監視。 

使用`az aks browse`をダッシュ ボードを起動します。 

展開後は、のみ可用性グループのメンバーシップ一覧し、初期化後の T-SQL スクリプトを更新できます。 その他のプロパティを更新することはできません - リソースを削除して再作成する必要があります。 使用して回転できる自動生成されたユーザーの資格情報を`mssql-server-k8s-rotate-creds`ジョブ。

## <a name="connect-to-the-sql-server-instance-hosting-the-primary-replica"></a>プライマリ レプリカをホストする SQL Server インスタンスに接続します。

`ag-services.yaml` Kubernetes のサービス名について説明します`ag1-primary`します。 `ag1-primary` プライマリ レプリカをホストする SQL Server インスタンスをポイントする Azure ロード バランサーを作成します。 サービスの外部 IP アドレスを使用して、対象のサーバーとして`sa`、アカウントし、パスワード」で作成した、`mssql secret`パスワード。

使用`kubectl get services`この IP アドレスを取得します。

以下に例を示します。

![サービスの例を取得します。](media\tutorial-sql-server-ag-containers-kubernetes\KubernetesGetServices.png)

上の図で`ag1-primary`サービスの外部 IP アドレスを持つ`104.42-50.138`します。 

SQL 認証を使用した SQL Server に接続するには、使用、`sa`アカウントの値は、`sapassword`から作成したシークレットとこの IP アドレス。

以下に例を示します。

```cmd
sqlcmd -S 104.42.50.138 -U sa -P "MyC0m9l&xP@ssw0rd"
```

![Sqlcmd を使用した接続します。](./media/tutorial-sql-server-ag-containers-kubernetes/sqlcmdConnect.png)

接続することもできます。 [SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md)します。

接続を確認するには、プライマリ レプリカをホストする SQL Server インスタンスに、次のクエリを実行します。

```sql
SELECT @@SERVERNAME;
```

クエリでは、プライマリ レプリカをホストする SQL Server インスタンスの名前を返します。

この時点では、Kubernetes クラスターは、docker コンテナーでの SQL Server の 3 つのインスタンスを持ちます。 可用性グループは、SQL Server のすべての 3 つのインスタンスをスパンしますが、データベースが可用性グループではありません。 次の手順では、可用性グループにデータベースを追加します。

## <a name="add-a-database-to-the-availability-group"></a>可用性グループにデータベースを追加する

データベースを可用性グループに追加します。

1. データベースの作成

  ```sql
  CREATE DATABASE [DemoDB]
  ```

1. 完全なトランザクションのログ チェーンを開始するデータベースのバックアップします。

  ```sql
  BACKUP DATABASE [DemoDB] 
  TO  DISK = N'/var/opt/mssql/data/DemoDB.bak' 
    WITH NOFORMAT, 
    NOINIT,  
    NAME = N'DemoDB-Full Database Backup', 
    SKIP, 
    NOREWIND, 
    NOUNLOAD,  
    STATS = 10;
  GO
  ```

1. データベースを可用性グループに追加します。

  ```sql
  ALTER AVAILABILITY GROUP ag1 ADD DATABASE [DemoDB]; 
  ```

レプリカは、可用性グループ セカンダリ レプリカにデータベースをシード処理のために自動的に自動シード処理モードで構成されます。

SQL Server Management Studio では、プライマリ レプリカに接続し、ダッシュ ボードで、可用性グループを参照してください。

次の例では、ダッシュ ボードで構成されている 3 つのノードにレプリカを持つ可用性グループを示します。

![AG1 ダッシュ ボード](./media/tutorial-sql-server-ag-containers-kubernetes/ssms_AG1.png)

## <a name="verify-failure-and-recovery"></a>エラーと回復を確認します。

障害の検出とフェールオーバーを確認するには、プライマリ レプリカをホストして、ポッドを削除できます。 Kubernetes は新しいプライマリ レプリカを選択し、リスナーにリダイレクトします。 削除済みのポッドは無視されます。 

このプロセスを示すためには、次の手順を実行します。

1. SQL Server を実行して、ポッドを一覧表示します。

   ```azurecli
   kubectl get pods
   ```

2. プライマリ レプリカを実行して、ポッドを特定します。

   外部の IP とクエリを使用してプライマリ レプリカに接続するか`@@servername`使用または`kubectl`を適切なポッドを取得します。 このコマンドでは、AG のプライマリ レプリカを実行しているコンテナーが含まれるポッドの名前を返します。

   ```azurecli
   kubectl get pods --selector="role.ag.mssql.microsoft.com/ag1"="primary" --output=jsonpath={.items..metadata.name}
   ```

3. ポッドを削除します。

   ```azurecli
   kubectl delete pod <podName>
   ```

置換`<podName>`ポッド名の前の手順から返される値を使用します。 

Kubernetes は、自動的に利用可能な同期セカンダリ レプリカの 1 つにフェールオーバーだけでなく、削除したポッドを再作成されます。

## <a name="clean-up-resources"></a>リソースをクリーンアップします。

不要になったときに、リソース グループとすべての関連リソースを削除します。 次のコマンドを実行します。
>[!WARNING]
>このコマンドでは、リソース グループ内のすべてを完全に削除されます。 リソース グループを削除した後、使用可能な Kubernetes クラスターのコンポーネントの [なし] になります。

```azurecli
az group delete --name <MyResourceGroup>
```

上記のコマンドを実行するには、置換`<MyResourceGroup>`リソース グループの名前に置き換えます。 

Azure では、リソース グループを削除します。

## <a name="summary"></a>まとめ

このチュートリアルでは、以下の使用方法を学習しました:  

> [!div class="checklist"]
> * ストレージを作成します。
> * SQL Server の演算子を Kubernetes クラスターにデプロイします。 
> * Kubernetes シークレットを作成します。
> * SQL Server インスタンスと正常性エージェントを展開します。
> * プライマリ レプリカに接続します。
> * 可用性グループにデータベースを追加する

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
>[Kubernetes の概要](http://docs.microsoft.com/azure/aks/intro-kubernetes)
>[Kubernetes 上の SQL Server の管理](sql-server-linux-kubernetes-manage.md)