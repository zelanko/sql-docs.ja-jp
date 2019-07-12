---
title: Kubernetes クラスター上の SQL Server Always On 可用性グループをデプロイします。
description: この記事では、要件については、SQL Server Kubernetes Always On 可用性グループ演算子グローバル パラメーターを説明します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
manager: jroth
ms.date: 10/02/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 88b3b2a8c955c628284bec59c9e9fead98e174b8
ms.sourcegitcommit: 93d1566b9fe0c092c9f0f8c84435b0eede07019f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67833241"
---
# <a name="deploy-a-sql-server-always-on-availability-group-on-a-kubernetes-cluster"></a>Kubernetes クラスター上の SQL Server Always On 可用性グループをデプロイします。

この記事の例では、3 つのレプリカでの Kubernetes クラスター上の SQL Server Always On 可用性グループをデプロイします。 セカンダリ レプリカは同期コミット モードです。

Kubernetes で、展開には、SQL Server の演算子では、SQL Server のコンテナー、および負荷が含まれていますバランサー サービス。 演算子は、可用性グループを自動的に調整します。 この記事で説明する方法。

- 演算子、SQL Server のコンテナー、および負荷分散サービスをデプロイします。
- サービスと可用性グループに接続します。
- データベースを可用性グループに追加します。

## <a name="requirements"></a>必要条件

- 最新のバージョンで、AKS の Kubernetes クラスター
- 少なくとも 3 つのノード
- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
- アクセス、 [sql server のサンプル](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files)GitHub リポジトリ

> [!NOTE]
> Kubernetes クラスターの任意の型を使用することができます。 Azure Kubernetes Service (AKS) での Kubernetes クラスターを作成するを参照してください。 [AKS クラスターの作成](https://docs.microsoft.com/azure/aks/create-cluster)です。
>
> Kubernetes の最新バージョンを使用します。 特定のバージョンは、お客様のサブスクリプションとリージョンに依存します。 参照してください[AKS で Kubernetes のサポートされているバージョン](https://docs.microsoft.com/en-us/azure/aks/supported-kubernetes-versions)します。  
>
> 次のスクリプトでは、Azure で 4 つのノードの Kubernetes クラスターを作成します。 スクリプトの置換を実行する前に`<latest version>`で最新のバージョン。 たとえば、 `1.12.5`があります。
>
> ```azure-cli
> az aks create --resource-group myResourceGroup --name myAKSCluster --node-count 4 --kubernetes-version <latest version> --generate-ssh-keys
> ```

## <a name="deploy-the-operator-sql-server-containers-and-load-balancing-services"></a>演算子、SQL Server のコンテナー、およびサービスの負荷分散展開します。

1. 作成、[名前空間](https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces/)します。

      この例と呼ばれる名前空間を使用して`ag1`します。 名前空間を作成するには、次のコマンドを実行します。
    
      ```azurecli
      kubectl create namespace ag1
      ```
    
      このソリューションに属するすべてのオブジェクトは、`ag1`名前空間。

1. 構成し、SQL Server の演算子のマニフェストをデプロイします。

      SQL Server のコピー [ `operator.yaml` ](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/operator.yaml)ファイルから[sql server のサンプル](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files)します。
    
      `operator.yaml`ファイルは、Kubernetes の演算子の配置マニフェスト。
    
      マニフェストは、Kubernetes クラスターに適用されます。
    
      ```azurecli
      kubectl apply -f operator.yaml --namespace ag1
      ```
    
1. Kubernetes 用のパスワードを持つシークレットの作成、`sa`アカウントと SQL Server インスタンスのマスター _ キー。

      シークレットの作成`kubectl`です。
      
      次の例では、という名前のシークレットを作成する`sql-secrets`で、`ag1`名前空間。 シークレットは、2 つのパスワードを格納します。
      
      - `sapassword` SQL Server のパスワードを格納`sa`アカウント。
      - `masterkeypassword` SQL Server のマスター _ キーの作成に使用するパスワードを格納します。 
    
   ターミナルに、スクリプトをコピーします。 各を置き換える`<>`複雑なパスワードおよびシークレットを作成するスクリプトを実行します。
    
   >[!NOTE]
   >パスワードは使用できません`&`または`` ` ``文字。
    
   ```azurecli
   kubectl create secret generic sql-secrets --from-literal=sapassword="<>" --from-literal=masterkeypassword="<>"  --namespace ag1
   ```

1. SQL Server のカスタム リソースをデプロイします。

      SQL Server のマニフェストをコピー [ `sqlserver.yaml` ](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/sqlserver.yaml)から[sql server のサンプル](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files)します。
    
      >[!NOTE]
      >`sqlserver.yaml`ファイルは、SQL Server のコンテナー、永続ボリューム要求、永続ボリューム、および SQL Server インスタンスごとに必要な負荷分散サービスについて説明します。
    
      マニフェストは、Kubernetes クラスターに適用されます。
    
      ```azurecli
      kubectl apply -f sqlserver.yaml --namespace ag1
      ```
      
次の図は、成功したアプリケーションの`kubectl apply`この例です。

![sqlservers を作成します。](./media/sql-server-linux-kubernetes-deploy/create-sqlservers.png)

SQL Server のマニフェストを適用した後、演算子は、SQL Server のコンテナーを展開します。

Kubernetes では、pod でコンテナーを配置します。 使用`kubectl get pods --namespace ag1`ポッドの状態を確認します。 次の図は、SQL Server のポッドを展開した後に、展開の例を示します。 

![ポッドの構築](./media/sql-server-linux-kubernetes-deploy/builtpods.png)

### <a name="monitor-the-deployment"></a>展開を監視します。

使用することができます、 [Azure Kubernetes Service の Kubernetes ダッシュ ボード](https://docs.microsoft.com/azure/aks/kubernetes-dashboard)展開の監視。

使用`az aks browse`をダッシュ ボードを起動します。 

## <a name="connect-to-the-availability-group-with-the-services"></a>サービスと可用性グループへの接続します。

[ `ag-services.yaml` ](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/ag-services.yaml)から[sql server のサンプル](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files)の例は、可用性グループ レプリカに接続できる負荷分散サービスをについて説明します。 

- `ag1-primary` プライマリ レプリカに接続するエンドポイントを提供します。
- `ag1-secondary` 任意のセカンダリ レプリカに接続するエンドポイントを提供します。

マニフェスト ファイルを適用すると、Kubernetes には、レプリカの種類ごとに負荷分散サービスが作成されます。 負荷分散サービスには、IP アドレスが含まれています。 この IP アドレスを使用する必要があるレプリカの種類に接続します。

サービスをデプロイするには、次のコマンドを実行します。

```azurecli
kubectl apply -f ag-services.yaml --namespace ag1
```

サービスをデプロイした後を使用して、`kubectl get services --namespace ag1`サービスの IP アドレスを識別します。

IP アドレスを持つことができますに接続する SQL Server インスタンスをホストするレプリカの各型。

次の図を示しています。

- 出力`kubectl get services`名前空間の`ag1`します。

- SQL Server の各コンテナーに対して作成された負荷分散サービスです。 エンドポイントとしてこれらの IP アドレスを使用して、クラスター内の SQL Server のインスタンスに直接接続します。

- `sqlcmd` 、プライマリ レプリカへの接続で、`sa`ロード バランサーのエンドポイントを使用してアカウント。

![接続](./media/sql-server-linux-kubernetes-deploy/connect.png)

## <a name="add-a-database-to-the-availability-group"></a>可用性グループにデータベースを追加する

>[!NOTE]
>現時点では、SQL Server Management Studio は、可用性グループにデータベースを追加することはできません。 TRANSACT-SQL を使用します。

Kubernetes では、SQL Server のコンテナーが作成された後は、データベースを可用性グループに追加する次の手順を完了します。

1. [接続](sql-server-linux-kubernetes-connect.md)クラスター内の SQL Server インスタンスにします。

1. データベースの作成。

      ```sql
      CREATE DATABASE [demodb]
      ```

1. 完全なログ チェーンを開始するデータベースのバックアップを実行します。

      ```sql
      USE MASTER
      GO
      BACKUP DATABASE [demodb] 
      TO DISK = N'/var/opt/mssql/data/demodb.bak'
      ```

1. データベースを可用性グループに追加します。

      ```sql
      ALTER AVAILABILITY GROUP [ag1] ADD DATABASE [demodb]
      ```
    
SQL Server がセカンダリ レプリカを自動的に作成できるように、自動シード処理では、可用性グループが作成されます。

SQL Server Management Studio の可用性グループ ダッシュ ボードから可用性グループの状態を表示することができます。

![ダッシュボード](./media/sql-server-linux-kubernetes-deploy/dashboard.png)

## <a name="next-steps"></a>次の手順

- [Kubernetes クラスター上の SQL Server 可用性グループへの接続します。](sql-server-linux-kubernetes-connect.md)

- [Kubernetes クラスター上の SQL Server 可用性グループを管理します。](sql-server-linux-kubernetes-manage.md)

- [SQL Server は、Kubernetes クラスター内のコンテナーの可用性グループをサポートしています](sql-server-ag-kubernetes.md)
