---
title: Azure Kubernetes サービス (AKS) での Kubernetes での SQL Server のコンテナーをデプロイします。
description: このチュートリアルでは、Azure Kubernetes Service で Kubernetes を使用した SQL Server の高可用性ソリューションをデプロイする方法を説明します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 01/10/2018
ms.topic: tutorial
ms.prod: sql
ms.custom: mvc
ms.technology: linux
ms.openlocfilehash: 2ae299553c700de7f22976917fa8556f93dbe61b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68032051"
---
# <a name="deploy-a-sql-server-container-in-kubernetes-with-azure-kubernetes-services-aks"></a>Azure Kubernetes サービス (AKS) での Kubernetes での SQL Server のコンテナーをデプロイします。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Azure Kubernetes Service (AKS) では、Kubernetes で高可用性 (HA) の永続的なストレージを SQL Server インスタンスを構成する方法について説明します。 ソリューションでは、回復性を提供します。 SQL Server インスタンスが失敗した場合は、Kubernetes に自動的にし再作成します新しいポッドにします。 Kubernetes では、ノードの障害に対する復元性も提供します。

このチュートリアルでは、AKS でのコンテナーで高可用性 SQL Server インスタンスを構成する方法を示します。 作成することも[Always On 可用性グループの SQL Server のコンテナー](sql-server-ag-kubernetes.md)します。 2 つの異なる Kubernetes ソリューションを比較するを参照してください。[の高可用性 SQL Server のコンテナーを](sql-server-linux-container-ha-overview.md)します。

> [!div class="checklist"]
> * SA パスワードを作成します。
> * ストレージを作成します。
> * 展開を作成します。
> * SQL Server Management Studio (SSMS) による接続します。
> * エラーと回復を確認します。

## <a name="ha-solution-on-kubernetes-running-in-azure-kubernetes-service"></a>Azure Kubernetes サービスで実行されている Kubernetes 上の HA ソリューション

Kubernetes バージョン 1.6 およびそれ以降はサポートしています[ストレージ クラス](https://kubernetes.io/docs/concepts/storage/storage-classes/)、[永続ボリューム要求](https://kubernetes.io/docs/concepts/storage/storage-classes/#persistentvolumeclaims)、および[Azure ディスク ボリュームの種類](https://github.com/kubernetes/examples/tree/master/staging/volumes/azure_disk)します。 作成して Kubernetes でネイティブに、SQL Server インスタンスを管理します。 この記事の例では、作成する方法を示します、[展開](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)共有ディスク フェールオーバー クラスター インスタンスと同様の高可用性構成を実現するためにします。 この構成では、Kubernetes は、クラスター オーケストレーターの役割を果たします。 コンテナー内の SQL Server インスタンスが失敗したときに、orchestrator を別のインスタンスが同じ永続的な記憶域に接続しているコンテナーのブートス トラップします。

![SQL Server の Kubernetes クラスターの図](media/tutorial-sql-server-containers-kubernetes/kubernetes-sql.png)

前の図では、`mssql-server`内のコンテナーを[ポッド](https://kubernetes.io/docs/concepts/workloads/pods/pod/)します。 Kubernetes では、クラスター内のリソースを調整します。 A[レプリカ セット](https://kubernetes.io/docs/concepts/workloads/controllers/replicaset/)ポッドがノード障害の後に自動的に復旧ことにより、します。 アプリケーションは、サービスに接続します。 この場合、サービスが障害の後に同じままの IP アドレスをホストするロード バランサーを表します、`mssql-server`します。

次の図に、`mssql-server`コンテナーが失敗しました。 レプリカの正常なインスタンスの正しい数設定、および構成に従って、新しいコンテナーを開始、オーケストレーターとして Kubernetes が保証されます。 オーケストレーターは、同じノードで、新しいポッドを開始し、`mssql-server`が同じ永続的な記憶域に再接続します。 サービスに再作成された接続`mssql-server`します。

![SQL Server の Kubernetes クラスターの図](media/tutorial-sql-server-containers-kubernetes/kubernetes-sql-after-pod-fail.png)

次の図では、ノードのホスト、`mssql-server`コンテナーが失敗しました。 オーケストレーターは、別のノードに新しいポッドを開始し、`mssql-server`が同じ永続的な記憶域に再接続します。 サービスに再作成された接続`mssql-server`します。

![SQL Server の Kubernetes クラスターの図](media/tutorial-sql-server-containers-kubernetes/kubernetes-sql-after-node-fail.png)

## <a name="prerequisites"></a>前提条件

* **Kubernetes クラスター**
   - このチュートリアルでは、Kubernetes クラスターが必要です。 手順を使用して、 [kubectl](https://kubernetes.io/docs/user-guide/kubectl/)クラスターを管理します。 

   - 参照してください[Azure Container Service (AKS) クラスターのデプロイ](https://docs.microsoft.com/azure/aks/tutorial-kubernetes-deploy-cluster)作成を使用して AKS での単一ノードの Kubernetes クラスターに接続`kubectl`します。 

   >[!NOTE]
   >ノードの障害を防ぐには、Kubernetes クラスターには、1 つ以上のノードが必要です。

* **Azure CLI 2.0.23**
   - このチュートリアルの手順は、Azure CLI 2.0.23 に対して検証されました。

## <a name="create-an-sa-password"></a>SA パスワードを作成します。

Kubernetes クラスターでは、SA のパスワードを作成します。 Kubernetes は、パスワードなどの機密性の高い構成情報を管理できます[シークレット](https://kubernetes.io/docs/concepts/configuration/secret/)します。

次のコマンドでは、SA アカウントのパスワードを作成します。

   ```azurecli
   kubectl create secret generic mssql --from-literal=SA_PASSWORD="MyC0m9l&xP@ssw0rd"
   ```  

   置換`MyC0m9l&xP@ssw0rd`複雑なパスワード。

   という名前の kubernetes シークレットを作成する`mssql`値を保持している`MyC0m9l&xP@ssw0rd`の`SA_PASSWORD`のコマンドを実行します。


## <a name="create-storage"></a>ストレージを作成します。

構成、[永続ボリューム](https://kubernetes.io/docs/concepts/storage/persistent-volumes/)と[永続ボリューム要求](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#persistent-volume-claim-protection)Kubernetes クラスターでします。 次の手順を完了するには。 

1. ストレージ クラスと永続的なボリュームを定義するマニフェストを作成する要求。  マニフェストはストレージ プロビジョナー、パラメーターを指定し、[回収ポリシー](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#reclaiming)します。 Kubernetes クラスターでは、このマニフェストを使用して、永続的なストレージを作成します。 

   次の yaml の例では、ストレージ クラスと永続ボリューム要求を定義します。 ストレージ クラスのプロビジョナーは`azure-disk`この Kubernetes クラスターが Azure ではであるためです。 ストレージ アカウントの種類は`Standard_LRS`します。 永続ボリューム要求の名前は`mssql-data`します。 永続ボリューム要求メタデータには、記憶域クラスへ、再度接続する注釈が含まれています。 

   ```yaml
   kind: StorageClass
   apiVersion: storage.k8s.io/v1beta1
   metadata:
        name: azure-disk
   provisioner: kubernetes.io/azure-disk
   parameters:
     storageaccounttype: Standard_LRS
     kind: Managed
   ---
   kind: PersistentVolumeClaim
   apiVersion: v1
   metadata:
     name: mssql-data
     annotations:
       volume.beta.kubernetes.io/storage-class: azure-disk
   spec:
     accessModes:
     - ReadWriteOnce
     resources:
       requests:
         storage: 8Gi
   ```

   保存します (たとえば、 **pvc.yaml**)。

1. Kubernetes 永続ボリューム要求を作成します。

   ```azurecli
   kubectl apply -f <Path to pvc.yaml file>
   ```

   `<Path to pvc.yaml file>` ファイルを保存した場所です。

   永続ボリュームは自動的に Azure ストレージ アカウントとして作成され、永続ボリューム要求にバインドします。 

    ![永続ボリューム要求コマンドのスクリーン ショット](media/tutorial-sql-server-containers-kubernetes/02_pvc_cmd.png)

1. 永続ボリューム要求を確認します。

   ```azurecli
   kubectl describe pvc <PersistentVolumeClaim>
   ```

   `<PersistentVolumeClaim>` 永続ボリューム要求の名前です。

   前の手順で、永続ボリューム要求の名前は`mssql-data`します。 永続ボリューム要求に関するメタデータを表示するには、次のコマンドを実行します。

   ```azurecli
   kubectl describe pvc mssql-data
   ```

   返されたメタデータには、value という値が含まれています。`Volume`します。 この値は、blob の名前にマップされます。

   ![ボリュームを含む、返されるメタデータのスクリーン ショット](media/tutorial-sql-server-containers-kubernetes/describe-volume.png)

   ボリュームの値には、Azure portal から次の図の blob の名前の一部が一致します。 

   ![スクリーン ショットの Azure ポータルの blob 名](media/tutorial-sql-server-containers-kubernetes/describe-volume-portal.png)

1. 永続ボリュームを確認します。

   ```azurecli
   kubectl describe pv
   ```

   `kubectl` 永続的なボリュームを自動的に作成され、永続ボリューム要求にバインドされたに関するメタデータを返します。 

## <a name="create-the-deployment"></a>展開を作成します。

この例では、SQL Server インスタンスをホストするコンテナーは Kubernetes デプロイ オブジェクトとしてについて説明します。 展開は、レプリカ セットを作成します。 レプリカ セットでは、ポッドを作成します。 

この手順で SQL Server ベースのコンテナーを記述するマニフェストを作成[mssql server-linux](https://hub.docker.com/_/microsoft-mssql-server) Docker イメージです。 マニフェストの参照、`mssql-server`永続ボリューム要求、および`mssql`Kubernetes クラスターに既に適用したシークレットです。 マニフェストについても説明します、[サービス](https://kubernetes.io/docs/concepts/services-networking/service/)します。 このサービスは、ロード バランサーです。 ロード バランサーは、SQL Server インスタンスが回復後に、IP アドレスが解決しないことを保証します。 

1. 展開を記述するマニフェスト (YAML ファイル) を作成します。 次の例では、SQL Server のコンテナー イメージに基づくコンテナーなど、配置について説明します。

   ```yaml
   apiVersion: apps/v1beta1
   kind: Deployment
   metadata:
     name: mssql-deployment
   spec:
     replicas: 1
     template:
       metadata:
         labels:
           app: mssql
       spec:
         terminationGracePeriodSeconds: 10
         containers:
         - name: mssql
           image: mcr.microsoft.com/mssql/server:2017-latest
           ports:
           - containerPort: 1433
           env:
           - name: MSSQL_PID
             value: "Developer"
           - name: ACCEPT_EULA
             value: "Y"
           - name: MSSQL_SA_PASSWORD
             valueFrom:
               secretKeyRef:
                 name: mssql
                 key: SA_PASSWORD 
           volumeMounts:
           - name: mssqldb
             mountPath: /var/opt/mssql
         volumes:
         - name: mssqldb
           persistentVolumeClaim:
             claimName: mssql-data
   ---
   apiVersion: v1
   kind: Service
   metadata:
     name: mssql-deployment
   spec:
     selector:
       app: mssql
     ports:
       - protocol: TCP
         port: 1433
         targetPort: 1433
     type: LoadBalancer
   ```

   という名前の新しいファイルに上記のコードをコピー`sqldeployment.yaml`します。 次の値を更新します。 

   * MSSQL_PID `value: "Developer"`:SQL Server Developer エディションを実行するコンテナーを設定します。 Developer edition では、実稼働データのライセンスがありません。 展開が実稼働環境用の場合は、適切なエディションを設定します。 (`Enterprise`、 `Standard`、または`Express`)。 

      >[!NOTE]
      >詳細については、次を参照してください。 [SQL Server のライセンス方法](https://www.microsoft.com/sql-server/sql-server-2017-pricing)します。

   * `persistentVolumeClaim`:この値には、エントリが必要です。`claimName:`永続ボリューム要求に使用される名前にマップされます。 このチュートリアルでは`mssql-data`します。 

   * `name: SA_PASSWORD`:このセクションで定義されている、SA のパスワードを設定するコンテナー イメージを構成します。

     ```yaml
     valueFrom:
       secretKeyRef:
         name: mssql
         key: SA_PASSWORD 
     ```

     という名前のシークレットを参照して、コンテナーを展開すると、Kubernetes`mssql`パスワードの値を取得します。 

   >[!NOTE]
   >使用して、`LoadBalancer`サービスの種類、SQL Server インスタンスはからリモート (インターネット) にアクセスできますが、ポート 1433 でします。

   保存します (たとえば、 **sqldeployment.yaml**)。

1. 展開を作成します。

   ```azurecli
   kubectl apply -f <Path to sqldeployment.yaml file>
   ```

   `<Path to sqldeployment.yaml file>` ファイルを保存した場所です。

   ![展開コマンドのスクリーン ショット](media/tutorial-sql-server-containers-kubernetes/04_deploy_cmd.png)

   展開とサービスが作成されます。 SQL Server インスタンスは、永続的な記憶域に接続し、コンテナーでです。

   ポッドの状態を表示する次のように入力します。`kubectl get pod`します。

   ![Get pod コマンドのスクリーン ショット](media/tutorial-sql-server-containers-kubernetes/05_get_pod_cmd.png)

   前のイメージで、ポッドには、ステータスの`Running`します。 この状態は、コンテナー準備ができていることを示します。 数分をかかります。

   >[!NOTE]
   >展開が作成された後は、ポッドが表示されるまで数分かかります。 遅延は、クラスターをプルするため、 [mssql server-linux](https://hub.docker.com/_/microsoft-mssql-server) Docker hub からイメージ。 イメージの pull が最初に後、は、キャッシュされたイメージが既にノードへのデプロイが場合以降のデプロイが高速でしょう。 

1. サービスが実行されていることを確認します。 次のコマンドを実行します。

   ```azurecli
   kubectl get services 
   ```

   このコマンドは、実行されているサービスとサービスの内部および外部の IP アドレスを返します。 外部 IP アドレスに注意してください、`mssql-deployment`サービス。 この IP アドレスを使用して、SQL Server に接続します。 

   ![Get service コマンドのスクリーン ショット](media/tutorial-sql-server-containers-kubernetes/06_get_service_cmd.png)

   Kubernetes クラスター内のオブジェクトの状態に関する詳細については、次のコマンドを実行します。

   ```azurecli
   az aks browse --resource-group <MyResourceGroup> --name <MyKubernetesClustername>
   ```  

## <a name="connect-to-the-sql-server-instance"></a>SQL Server インスタンスに接続します。

説明に従って、コンテナーを構成する場合は、Azure の仮想ネットワークの外部からのアプリケーションで接続することができます。 使用して、`sa`アカウントと、外部 IP アドレス、サービス。 Kubernetes シークレットとして構成したパスワードを使用します。 

次のアプリケーションを使用すると、SQL Server インスタンスに接続します。 

* [SSMS](https://docs.microsoft.com/sql/linux/sql-server-linux-manage-ssms)

* [SSDT](https://docs.microsoft.com/sql/linux/sql-server-linux-develop-use-ssdt)

* sqlcmd
   
   使用して接続する`sqlcmd`、次のコマンドを実行します。

   ```cmd
   sqlcmd -S <External IP Address> -U sa -P "MyC0m9l&xP@ssw0rd"
   ```

   次の値に置き換えます。
      
    - `<External IP Address>` IP アドレスを含む、`mssql-deployment`サービス 
    - `MyC0m9l&xP@ssw0rd` 自分のパスワード

## <a name="verify-failure-and-recovery"></a>エラーと回復を確認します。

エラーと回復を確認するには、ポッドを削除できます。 次の手順を実行します。

1. SQL Server を実行して、ポッドを一覧表示します。

   ```azurecli
   kubectl get pods
   ```

   SQL Server を実行して、ポッドの名前に注意してください。

1. ポッドを削除します。

   ```azurecli
   kubectl delete pod mssql-deployment-0
   ```
   `mssql-deployment-0` ポッド名の前の手順から返される値。 

Kubernetes に自動的に再作成ポッドを SQL Server インスタンスを回復し、永続的ストレージに接続します。 使用`kubectl get pods`新しいポッドがデプロイされていることを確認します。 使用`kubectl get services`に新しいコンテナーの IP アドレスが同じであることを確認します。 

## <a name="summary"></a>まとめ

このチュートリアルでは、SQL Server のコンテナーを高可用の Kubernetes クラスターにデプロイする方法について説明しました。 

> [!div class="checklist"]
> * SA パスワードを作成します。
> * ストレージを作成します。
> * 展開を作成します。
> * SQL Server Management Studio (SSMS) の接続します。
> * エラーと回復を確認します。

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
>[Kubernetes の概要](https://docs.microsoft.com/azure/aks/intro-kubernetes)


