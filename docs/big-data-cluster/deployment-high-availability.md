---
title: 高可用性を備えた SQL Server ビッグデータクラスターのデプロイ
titleSuffix: Deploy SQL Server Big Data Cluster with high availability
description: 高可用性を備えた SQL Server ビッグデータクラスターをデプロイする方法について説明します。
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 08/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 43d651c46282d7de0ffdd60f326740e7821b9bbe
ms.sourcegitcommit: 8cb26b7dd40280a7403d46ee59a4e57be55ab462
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2019
ms.locfileid: "72542160"
---
# <a name="deploy-sql-server-big-data-cluster-with-high-availability"></a>高可用性を備えた SQL Server ビッグデータクラスターのデプロイ

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

ビッグデータクラスター (BDC) をデプロイするときに、可用性グループの構成にデプロイする SQL Server マスターを構成できます。 この構成では、Kubernetes インフラストラクチャが組み込みの正常性監視、障害検出、およびフェールオーバーメカニズムを使用して有効にすることで、SQL Server マスターの信頼性が向上します。 可用性グループ (AG) は、SQL Server インスタンスに冗長性を追加します。 この構成では、監視、障害検出、およびフェールオーバータスクは、ビッグデータクラスター管理サービス、つまり制御サービスによって管理されます。

さらに、データベースミラーリングエンドポイントの設定、可用性グループの作成、可用性グループへのデータベースの追加などの管理タスクは、ビッグデータクラスタープラットフォームによって提供されます。

可用性グループによって実現される機能の一部を次に示します。

1. 高可用性の設定が展開構成ファイルで指定されている場合は、`containedag` という名前の1つの可用性グループが作成されます。 既定では、`containedag` にはプライマリを含む3つのレプリカがあります。 可用性グループのすべての CRUD 操作は、内部的に管理されます。
1. すべてのデータベースは、`master` および `msdb` を含む可用性グループに自動的に追加されます。 Polybase 構成データベースには、各レプリカに固有のインスタンスレベルのメタデータが含まれているため、可用性グループには含まれません。
1. 外部エンドポイントは、AG データベースに接続するために自動的にプロビジョニングされます。 このエンドポイント `master-svc-external` は、AG リスナーの役割を果たします。
1. セカンダリレプリカへの読み取り専用接続に対して、2番目の外部エンドポイントがプロビジョニングされます。 


## <a name="deploy"></a>配置

可用性グループに SQL Server マスターをデプロイするには:

1. @No__t_0 機能を有効にする
1. AG のレプリカの数を指定します (最小値は 3)
1. 読み取り専用セカンダリレプリカへの接続用に作成された2番目の外部エンドポイントの詳細を構成します。

次の手順では、これらの設定を含む修正プログラムファイルを作成し、`aks-dev-test` または `kubeadm-dev-test` の構成プロファイルに適用する方法を示します。 これらの手順では、`aks-dev-test` プロファイルに修正プログラムを適用して HA 属性を追加する方法の例を紹介します。Kubeadm クラスターでのデプロイの場合は、同様の修正プログラムが適用されますが、 **[エンドポイント]** セクションで、 **ServiceType**に*nodeport*を使用していることを確認してください。

1. @No__t_0 ファイルを作成する

    ```json
    {
      "patch": [
        {
          "op": "replace",
          "path": "spec.resources.master.spec",
          "value": {
            "type": "Master",
            "replicas": 3,
            "endpoints": [
              {
                "name": "Master",
                "serviceType": "LoadBalancer",
                "port": 31433
              },
              {
                "name": "MasterSecondary",
                "serviceType": "LoadBalancer",
                "port": 31436
              }
            ],
            "settings": {
              "sql": {
                "hadr.enabled": "true"
              }
            }
          }
        }
      ]
    }
    ```

1. ターゲットプロファイルの複製

    ```bash
    azdata bdc config init --source aks-dev-test --target custom-aks
    ```

1. カスタムプロファイルにパッチファイルを適用する

    ```bash
    azdata bdc config patch -c custom-aks/bdc.json --patch-file patch.json
    ```
1. 上で作成したクラスター構成プロファイルを使用してクラスターの展開を開始する

    ```bash
    azdata bdc create --config-profile custom-aks --accept-eula yes
    ```

## <a name="connect-to-sql-server-databases"></a>SQL Server データベースへの接続

SQL Server マスターに対して実行するワークロードの種類に応じて、読み取り/書き込みワークロードの場合はプライマリに、読み取り専用のワークロードの場合はセカンダリレプリカ内のデータベースに接続できます。 接続の種類ごとの概要を次に示します。

### <a name="connect-to-databases-on-the-primary-replica"></a>プライマリレプリカのデータベースに接続する

プライマリレプリカへの接続には、`sql-server-master` エンドポイントを使用します。 このエンドポイントは、AG のリスナーでもあります。 すべての接続は、可用性グループのコンテキスト内にあります。 たとえば、このエンドポイントを使用する既定の接続では、SQL Server インスタンス `master` データベースではなく、AG 内の `master` データベースに接続します。

```bash
azdata bdc endpoint list -e sql-server-master -o table
```

`Description                           Endpoint             Name               Protocol`
`------------------------------------  -------------------  -----------------  ----------`
`SQL Server Master Instance Front-End  13.64.235.192,31433  sql-server-master  tds`

> [!NOTE]
> フェールオーバーイベントは、HDFS やデータプールなどのリモートデータソースからデータにアクセスする分散クエリの実行中に発生する可能性があります。 ベストプラクティスとして、フェールオーバーによる切断が発生した場合の接続再試行ロジックを使用するようにアプリケーションを設計する必要があります。  
>

### <a name="connect-to-databases-on-the-secondary-replicas"></a>セカンダリレプリカのデータベースに接続する

セカンダリレプリカのデータベースに対する読み取り専用接続の場合は、`sql-server-master-readonly` エンドポイントを使用します。 このエンドポイントは、すべてのセカンダリレプリカのロードバランサーのように機能します。 接続文字列にユーザーデータベースコンテキストを指定します。

```bash
azdata bdc endpoint list -e sql-server-master-readonly -o table
```

`Description                                    Endpoint            Name                        Protocol`
`---------------------------------------------  ------------------  --------------------------  ----------`
`SQL Server Master Readable Secondary Replicas  13.64.238.24,31436  sql-server-master-readonly  tds`

### <a id="instance-connect"></a>SQL Server インスタンスに接続する

サーバーレベルの構成を設定する、または可用性グループにデータベースを手動で追加するなどの特定の操作 (データベースが復元ワークフローで作成された場合) には、インスタンスへの接続が必要です。 この接続を提供するには、外部エンドポイントを公開します。 このエンドポイントを公開してから、復元ワークフローで作成したデータベースを可用性グループに追加する方法の例を次に示します。

- @No__t_0 エンドポイントに接続し、次のように実行して、プライマリレプリカをホストするポッドを特定します。

    ```sql
    SELECT @@SERVERNAME
   ```

- 新しい Kubernetes サービスを作成して外部エンドポイントを公開する

    Kubeadm クラスターの場合は、次のコマンドを実行します。 @No__t_0 を、前の手順で返されたサーバーの名前に置き換えます。には、作成された Kubernetes サービスの優先名と、BDC クラスターの名前を `namespaceName` * を `serviceName` ます。

    ```bash
    kubectl -n <namespaceName> expose pod <podName> --port=1533  --name=<serviceName> --type=NodePort
    ```

    Aks クラスターを実行する場合は、同じコマンドを実行します。ただし、作成されたサービスの種類が `LoadBalancer` される点が異なります。 例 : 

    ```bash
    kubectl -n <namespaceName> expose pod <podName> --port=1533  --name=<serviceName> --type=LoadBalancer
    ```

    Aks に対して実行されるこのコマンドの例を次に示します。このコマンドは、プライマリをホストしているポッドが `master-0` ます。

    ```bash
    kubectl -n mssql-cluster expose pod master-0 --port=1533  --name=master-sql-0 --type=LoadBalancer
    ```

    作成された Kubernetes サービスの IP を取得します。

    ```bash
    kubectl get services -n <namespaceName>
    ```

> [!IMPORTANT]
> ベストプラクティスとして、次のコマンドを実行して、上記で作成した Kubernetes サービスを削除してクリーンアップする必要があります。
>
>```bash
>kubectl delete svc master-sql-0 -n mssql-cluster
>```

- 可用性グループにデータベースを追加します。

    データベースを AG に追加するには、完全復旧モードで実行する必要があり、ログバックアップを実行する必要があります。 上で作成した Kubernetes サービスの IP を使用して SQL Server インスタンスに接続し、次に示すように TSQL ステートメントを実行します。

    ```sql
    ALTER DATABASE <databaseName> SET RECOVERY FULL;
    BACKUP DATABASE <databaseName> TO DISK='<filePath>'
    ALTER AVAILABILITY GROUP containedag ADD DATABASE <databaseName>
    ```

    次の例では、インスタンスで復元された `sales` という名前のデータベースを追加します。

    ```sql
    ALTER DATABASE sales SET RECOVERY FULL;
    BACKUP DATABASE sales TO DISK='/var/opt/mssql/data/sales.bak'
    ALTER AVAILABILITY GROUP containedag ADD DATABASE sales
    ```

## <a name="known-limitations"></a>既知の制限事項

ビッグデータクラスターの SQL Server マスターの可用性グループに関する既知の問題と制限事項を次に示します。

- @No__t_1、`CREATE DATABASE FROM SNAPSHOT` などの `CREATE DATABASE` 以外のワークフローの結果として作成されたデータベースは、可用性グループに自動的に追加されません。 [インスタンスに接続](#instance-connect)し、データベースを可用性グループに手動で追加します。
- @No__t_0 でのサーバー構成設定の実行など、一部の操作では master インスタンスに接続する必要があります。 対応するプライマリエンドポイントを使用することはできません。 [指示](#instance-connect)に従って SQL Server インスタンスに接続し、`sp_configure` を実行します。
- BDC をデプロイするときに、高可用性構成を作成する必要があります。 可用性グループの配置後に高可用性構成を有効にすることはできません。

## <a name="next-steps"></a>次のステップ

- ビッグデータクラスターの展開における構成ファイルの使用方法の詳細については、「 [How to deploy [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] On Kubernetes](deployment-guidance.md#configfile)」を参照してください。
- SQL Server の可用性グループの機能の詳細については、「 [Always On 可用性グループの概要 (SQL Server)](https://docs.microsoft.com/en-us/sql/database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server?view=sql-server-2017)」を参照してください。
