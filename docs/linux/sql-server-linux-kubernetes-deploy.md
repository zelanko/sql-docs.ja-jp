---
title: Kubernetes クラスターに SQL Server Always On 可用性グループを展開する
description: この記事では、SQL Server Kubernetes Always On 可用性グループ演算子のグローバル要件のパラメーターについて説明します
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 10/02/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 1e8825336edd4e55812f6037bbb4479a3b225e3f
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028731"
---
# <a name="deploy-a-sql-server-always-on-availability-group-on-a-kubernetes-cluster"></a>Kubernetes クラスターに SQL Server Always On 可用性グループを展開する

この記事の例では、3 つのレプリカを持つ Kubernetes クラスターに SQL Server Always On 可用性グループを展開します。 セカンダリ レプリカは同期コミット モードです。

Kubernetes での展開には、SQL Server 演算子、SQL Server コンテナー、ロード バランサー サービスが含まれます。 演算子によって、可用性グループが自動的に調整されます。 この記事では、以下の方法について説明します。

- 演算子、SQL Server コンテナー、負荷分散サービスを展開する。
- サービスを使用して可用性グループに接続する。
- 可用性グループにデータベースを追加する。

## <a name="requirements"></a>必要条件

- 最新バージョンの AKS Kubernetes クラスター
- 3 つ以上のノード
- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
- [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files) GitHub リポジトリへのアクセス

> [!NOTE]
> 任意の種類の Kubernetes クラスターを使用できます。 Azure Kubernetes Service (AKS) で Kubernetes クラスターを作成する場合は、[AKS クラスターの作成](https://docs.microsoft.com/azure/aks/create-cluster)に関する記述を参照してください。
>
> 最新バージョンの Kubernetes を使用します。 特定のバージョンは、サブスクリプションとリージョンによって異なります。 [AKS でサポートされている Kubernetes のバージョン](https://docs.microsoft.com/azure/aks/supported-kubernetes-versions)に関するページを参照してください。  
>
> 次のスクリプトでは、Azure で 4 ノードの Kubernetes クラスターを作成します。 スクリプトを実行する前に、`<latest version>` を使用可能な最新のバージョンに置き換えます。 たとえば、 `1.12.5`があります。
>
> ```azure-cli
> az aks create --resource-group myResourceGroup --name myAKSCluster --node-count 4 --kubernetes-version <latest version> --generate-ssh-keys
> ```

## <a name="deploy-the-operator-sql-server-containers-and-load-balancing-services"></a>演算子、SQL Server コンテナー、負荷分散サービスを展開する

1. [名前空間](https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces/)を作成します。

      この例では、`ag1` という名前空間を使用します。 次のコマンドを実行して、名前空間を作成します。
    
      ```azurecli
      kubectl create namespace ag1
      ```
    
      このソリューションに属するすべてのオブジェクトは、`ag1` 名前空間にあります。

1. SQL Server 演算子マニフェストを構成して展開します。

      [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files) から SQL Server の [`operator.yaml`](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/operator.yaml) ファイルをコピーします。
    
      `operator.yaml` ファイルは、Kubernetes 演算子の配置マニフェストです。
    
      Kubernetes クラスターにマニフェストを適用します。
    
      ```azurecli
      kubectl apply -f operator.yaml --namespace ag1
      ```
    
1. `sa` アカウントと、SQL Server インスタンスのマスター キーのパスワードを使用して、Kubernetes のシークレットを作成します。

      `kubectl` でシークレットを作成します。
      
      次の例では、`ag1` 名前空間で `sql-secrets` という名前のシークレットを作成します。 シークレットには、次の 2 つのパスワードが格納されます。
      
      - `sapassword` では、SQL Server の `sa`アカウントのパスワードを格納します。
      - `masterkeypassword` では、SQL Server マスター キーの作成に使用されるパスワードを格納します。 
    
   スクリプトをターミナルにコピーします。 各 `<>` を複雑なパスワードに置き換え、スクリプトを実行してシークレットを作成します。
    
   >[!NOTE]
   >パスワードには、`&` や `` ` `` の文字を使用することはできません。
    
   ```azurecli
   kubectl create secret generic sql-secrets --from-literal=sapassword="<>" --from-literal=masterkeypassword="<>"  --namespace ag1
   ```

1. SQL Server カスタム リソースを展開します。

      [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files) から SQL Server のマニフェスト [`sqlserver.yaml`](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/sqlserver.yaml) をコピーします。
    
      >[!NOTE]
      >`sqlserver.yaml` ファイルでは、各 SQL Server インスタンスに必要な SQL Server コンテナー、永続ボリューム要求、永続ボリューム、および負荷分散サービスについて説明されています。
    
      Kubernetes クラスターにマニフェストを適用します。
    
      ```azurecli
      kubectl apply -f sqlserver.yaml --namespace ag1
      ```
      
次の図は、この例で `kubectl apply` が正常に適用されたことを示しています。

![sqlserver を作成する](./media/sql-server-linux-kubernetes-deploy/create-sqlservers.png)

SQL Server マニフェストを適用した後、演算子によって SQL Server コンテナーが展開されます。

Kubernetes によって、ポッドにコンテナーが配置されます。 ポッドの状態を確認するには、`kubectl get pods --namespace ag1` を使用します。 次の図は、SQL Server ポッドが展開された後の展開例を示しています。 

![構築されたポッド](./media/sql-server-linux-kubernetes-deploy/builtpods.png)

### <a name="monitor-the-deployment"></a>展開を監視する

[Azure Kubernetes Service で Kubernetes ダッシュボード](https://docs.microsoft.com/azure/aks/kubernetes-dashboard)を使用して、展開を監視することができます。

ダッシュボードを起動するには、`az aks browse` を使用します。 

## <a name="connect-to-the-availability-group-with-the-services"></a>サービスを使用して可用性グループに接続する

[sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files) の例の [`ag-services.yaml`](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/ag-services.yaml) では、可用性グループのレプリカに接続できる負荷分散サービスについて説明されています。 

- `ag1-primary` では、プライマリ レプリカに接続するためのエンドポイントが提供されます。
- `ag1-secondary` では、任意のセカンダリ レプリカに接続するためのエンドポイントが提供されます。

マニフェスト ファイルを適用すると、Kubernetes によって、レプリカの種類ごとに負荷分散サービスが作成されます。 負荷分散サービスには、IP アドレスが含まれます。 この IP アドレスを使用して、必要な種類のレプリカに接続します。

サービスを展開するには、次のコマンドを実行します。

```azurecli
kubectl apply -f ag-services.yaml --namespace ag1
```

サービスを展開した後、`kubectl get services --namespace ag1` を使用してサービスの IP アドレスを識別します。

IP アドレスを使用して、各種類のレプリカをホストする SQL Server インスタンスに接続できます。

以下の図には、次のことが示されています。

- `ag1` 名前空間の `kubectl get services` からの出力。

- 各 SQL Server コンテナーに対して作成された負荷分散サービス。 これらの IP アドレスをエンドポイントとして使用して、クラスター内の SQL Server のインスタンスに直接接続します。

- ロードバランサー エンドポイント経由で `sa` アカウントを使用する、プライマリ レプリカへの `sqlcmd` 接続。

![接続する](./media/sql-server-linux-kubernetes-deploy/connect.png)

## <a name="add-a-database-to-the-availability-group"></a>可用性グループにデータベースを追加する

>[!NOTE]
>現時点では、SQL Server Management Studio で可用性グループにデータベースを追加することはできません。 Transact-SQL を使用します。

Kubernetes で SQL Server コンテナーが作成された後、次の手順を完了してデータベースを可用性グループに追加します。

1. クラスター内の SQL Server インスタンスに[接続](sql-server-linux-kubernetes-connect.md)します。

1. データベースを作成します。

      ```sql
      CREATE DATABASE [demodb]
      ```

1. データベースの完全バックアップを実行して、ログ チェーンを開始します。

      ```sql
      USE MASTER
      GO
      BACKUP DATABASE [demodb] 
      TO DISK = N'/var/opt/mssql/data/demodb.bak'
      ```

1. 可用性グループにデータベースを追加します。

      ```sql
      ALTER AVAILABILITY GROUP [ag1] ADD DATABASE [demodb]
      ```
    
可用性グループは自動シード処理で作成されるため、SQL Server によってセカンダリ レプリカが自動的に作成されます。

可用性グループの状態は、SQL Server Management Studio の [可用性グループ] ダッシュボードから表示できます。

![ダッシュボード](./media/sql-server-linux-kubernetes-deploy/dashboard.png)

## <a name="next-steps"></a>次の手順

- [Kubernetes クラスターの SQL Server 可用性グループに接続する](sql-server-linux-kubernetes-connect.md)

- [Kubernetes クラスターの SQL Server 可用性グループを管理する](sql-server-linux-kubernetes-manage.md)

- [SQL Server では、Kubernetes クラスター内のコンテナーの可用性グループがサポートされます](sql-server-ag-kubernetes.md)
