---
title: "SQL Server のコンテナーを高可用性を Kubernetes の構成 |Microsoft ドキュメント"
description: "このチュートリアルでは、Azure コンテナー サービスで Kubernetes で SQL Server の高可用性ソリューションを展開する方法を示します。"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 01/10/2018
ms.topic: tutorial
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: mvc
ms.technology: database-engine
ms.workload: Inactive
ms.openlocfilehash: 5055a5956ce83dadae3cef13f0855db02a61d01b
ms.sourcegitcommit: 06131936f725a49c1364bfcc2fccac844d20ee4d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/12/2018
---
# <a name="configure-sql-server-container-in-kubernetes-for-high-availability"></a>高可用性を実現 Kubernetes で SQL Server のコンテナーを構成します。

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

永続的なストレージの高可用性を備えた Kubernetes Azure コンテナー サービス (AKS) で SQL Server インスタンスを構成するには、この記事に従います。 ソリューションでは、回復性を提供します。 SQL Server のインスタンスが失敗した場合、Kubernetes 自動的に再作成、新しい pod でします。 AKS は、Kubernetes ノードの障害に対する回復性を提供します。 

このチュートリアルでは、AKS を使用してコンテナーで高可用性 SQL Server インスタンスを構成する方法について説明します。 

> [!div class="checklist"]
> * 作成 SA パスワード
> * ストレージを作成します。
> * 展開を作成します。
> * SQL Server Management Studio (SSMS) で接続します。
> * エラーと回復を確認します。

### <a name="ha-solution-using-kubernetes-running-in-azure-container-service"></a>Azure コンテナー サービスで実行されている Kubernetes を使用して HA ソリューション

Kubernetes 1.6 + をサポートしている[ストレージ クラス](http://kubernetes.io/docs/concepts/storage/storage-classes/)、[永続的なボリューム クレーム](http://kubernetes.io/docs/concepts/storage/storage-classes/#persistentvolumeclaims)、および[Azure ディスク ボリュームのドライバー](http://github.com/Azure/azurefile-dockervolumedriver)です。 作成および Kubernetes でネイティブに、SQL Server インスタンスを管理することができます。 この記事の内容の例を作成する方法を示しています、[展開](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)共有ディスク フェールオーバー クラスター インスタンスと同様の高可用性構成を実現するためにします。 この構成では、Kubernetes は、クラスターの orchestrator の役割を果たします。 コンテナー内の SQL Server インスタンスが失敗すると、orchestrator には、同じ永続的な記憶域に接続しているコンテナーの別のインスタンスがブートス トラップします。

![Kubernetes SQL Server クラスター](media/tutorial-sql-server-containers-kubernetes/kubernetes-sql.png)

上の図で`mssql-server`内のコンテナー、 [pod](http://kubernetes.io/docs/concepts/workloads/pods/pod/)です。 Kubernetes は、クラスター内のリソースを調整します。 A[レプリカ セット](http://kubernetes.io/docs/concepts/workloads/controllers/replicaset/)pod がノード障害の後に自動的に回復することを確認します。 アプリケーションは、サービスに接続します。 この場合、サービスが常に同一の障害が発生した IP アドレスをホストしているロード バランサーを表す、`mssql-server`です。

次の図で、`mssql-server`コンテナーが失敗しました。 Orchestrator では、としては、レプリカの正常なインスタンスの正しい数の設定し、構成に従って、新しいコンテナーを開始 Kubernetes が保証されます。 Orchestrator は、同じノードで、新しい pod を開始し、`mssql-server`が同じ永続的な記憶域に再接続します。 サービスが、再作成された接続`mssql-server`です。

![後に Kubernetes SQL Server クラスター](media/tutorial-sql-server-containers-kubernetes/kubernetes-sql-after-pod-fail.png)

次の図に、ノードをホストしている、`mssql-server`コンテナーが失敗しました。 Orchestrator は、別のノードに新しい pod を起動し、`mssql-server`が同じ永続的な記憶域に再接続します。 サービスが、再作成された接続`mssql-server`です。

![後に Kubernetes SQL Server クラスター](media/tutorial-sql-server-containers-kubernetes/kubernetes-sql-after-node-fail.png)

## <a name="prerequisites"></a>前提条件

* **Kubernetes クラスター**
   - このチュートリアルでは、Kubernetes クラスターが必要です。 手順は、 [kubectl](https://kubernetes.io/docs/user-guide/kubectl/)クラスターを管理します。 

   - 記載された手順を行うことができる[クラスターを展開する Azure コンテナー サービス (AKS)](http://docs.microsoft.com/en-us/azure/aks/tutorial-kubernetes-deploy-cluster)を作成、およびと AKS で 1 つのノード Kubernetes クラスターに接続して`kubectl`です。 

   >[!NOTE]
   >ノードの障害を防ぐためには、Kubernetes クラスターには、複数のノードが必要です。

* **Azure CLI 2.0.23**
   - このチュートリアルの手順は、Azure CLI 2.0.23 に対して検証されました。

## <a name="create-sa-password"></a>作成 SA パスワード

Kubernetes クラスタで SA パスワードを作成します。 Kubernetes としてパスワードのような機密性の高い構成情報を管理できます[シークレット](http://kubernetes.io/docs/concepts/configuration/secret/)です。

次のコマンドでは、SA アカウントのパスワードを作成します。

   ```azurecli
   kubectl create secret generic mssql --from-literal=SA_PASSWORD="MyC0m9l&xP@ssw0rd"
   ```  

   置き換える`MyC0m9l&xP@ssw0rd`複雑なパスワードを使用します。

   Kubernetes という名前で、シークレットを作成する`mssql`値を保持する`MyC0m9l&xP@ssw0rd`の`SA_PASSWORD`コマンドを実行します。


## <a name="create-storage"></a>ストレージを作成します。

構成、[永続的なボリューム](http://kubernetes.io/docs/concepts/storage/persistent-volumes/)、および[永続的なボリューム クレーム](http://kubernetes.io/docs/concepts/storage/persistent-volumes/#persistent-volume-claim-protection)Kubernetes クラスターでします。 次の手順を実行します。 

1. 記憶域クラスおよび永続的なボリュームを定義するマニフェストを作成する要求。  マニフェストで記憶域プロビジョナー、パラメーターを指定し、[ポリシーを再利用](http://kubernetes.io/docs/concepts/storage/persistent-volumes/#reclaiming)です。 Kubernetes クラスターでは、このマニフェストを使用して、永続的な記憶域を作成します。 

   Yaml の次の例では、記憶域クラスおよび永続的なボリュームのクレームを定義します。 記憶域クラス プロビジョナー`azure-disk`この Kubernetes クラスターは、Azure であるためです。 ストレージ アカウントの種類が`Standard_LRS`です。 永続的なボリュームの要求の名前は`mssql-data`します。 永続的なボリュームの要求のメタデータには、ストレージ クラス、再度接続する注釈が含まれます。 

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

   たとえば、ファイルを保存します。 **pvc.yaml**です。

1. Kubernetes で永続的なボリュームのクレームを作成します。

   ```azurecli
   kubectl apply -f <Path to pvc.yaml file>
   ```

   * `<Path to pvc.yaml file>`
      * ファイルを保存した場所です。

   永続的なボリュームは自動的に、Azure ストレージ アカウントとして作成され、永続的なボリュームの要求にバインドされています。 

    ![ボリュームの永続的な要求](media/tutorial-sql-server-containers-kubernetes/02_pvc_cmd.png)

1. 永続的なボリュームの要求を確認します。

   ```azurecli
   kubectl describe pvc <PersistentVolumeClaim>
   ```

   * `<PersistentVolumeClaim>`
      * 永続的なボリュームの要求の名前。

    前の手順では、永続的なボリュームの要求の名前`mssql-data`です。 永続的なボリューム要求に関するメタデータを表示するには、次のコマンドを実行します。

    ```azurecli
    kubectl describe pvc mssql-data
    ```

    返されたメタデータには、value という値が含まれています。`Volume`です。 この値は、blob の名前にマップされます。

    ![ボリュームを説明します。](media/tutorial-sql-server-containers-kubernetes/describe-volume.png)

    ボリューム、Azure ポータルから次の図の blob の名前の一致する部分の値です。 

    ![ボリュームのポータルを説明します。](media/tutorial-sql-server-containers-kubernetes/describe-volume-portal.png)

1. 永続的なボリュームを確認します。

   ```azurecli
   kubectl describe pv
   ```

   `kubectl`永続的なボリュームが自動的に作成された永続的なボリュームの要求にバインドされているに関するメタデータを返します。 

## <a name="create-the-deployment"></a>展開を作成します。

この例では、SQL Server インスタンスをホストしているコンテナーは Kubernetes 展開オブジェクトとして記述されます。 展開では、レプリカ セットを作成します。 レプリカ セットは、pod 型を作成します。 

この手順で、作成、Microsoft SQL Server に基づいて、コンテナーを記述するマニフェストを[mssql サーバー linux](https://hub.docker.com/r/microsoft/mssql-server-linux/) Docker イメージ。 マニフェストの参照、`mssql-server`永続的なボリュームのクレームと`mssql`Kubernetes クラスターに既に適用したシークレット。 マニフェストについても説明します、[サービス](http://kubernetes.io/docs/concepts/services-networking/service/)です。 このサービスは、ロード バランサーです。 ロード バランサーは、SQL Server インスタンスを修復した後に、IP アドレスが解決しないことを保証します。 

1. 配置について詳しく説明するマニフェストを - yaml ファイルを作成します。 次の例では、SQL Server のコンテナー イメージを基にコンテナーを含む配置について説明します。

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
           image: microsoft/mssql-server-linux
           ports:
           - containerPort: 1433
           env:
           - name: ACCEPT_EULA
             value: "Y"
           - name: SA_PASSWORD
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

   という名前の新しいファイルに前のコードをコピー`sqldeployment.yaml`です。 次の値を更新します。 

   * `value: "Developer"`
     * SQL Server Developer edition を実行するコンテナーを設定します。 Developer edition では、実稼働データのライセンスがありません。 展開が運用環境用と場合、は、適切なエディションを設定します。 いずれかの`Enterprise`、 `Standard`、または`Express`です。 

      >[!NOTE]
      >詳細については、次を参照してください。 [SQL Server のライセンス方法](http://www.microsoft.com/sql-server/sql-server-2017-pricing)です。

   * `persistentVolumeClaim`
     * この値には、エントリが必要です。`claimName:`永続的なボリュームの要求に対して使用される名前にマップされます。 この記事では`mssql-data`します。 

   * `name: SA_PASSWORD`
      * このセクションで定義されている SA パスワードを設定するコンテナー イメージを構成します。

      ```yaml
      valueFrom:
        secretKeyRef:
          name: mssql
          key: SA_PASSWORD 
      ```

       名前付きのシークレットを参照して、コンテナーを展開すると、Kubernetes`mssql`パスワードの値を取得します。 

   >[!NOTE]
   >使用して、`LoadBalancer`サービスの種類、SQL Server のインスタンスがリモートで (インターネット) を介してアクセスできる、ポート 1433 でします。

    たとえば、ファイルを保存します。 **sqldeployment.yaml**です。

1. 展開を作成します。

   ```azurecli
   kubectl apply -f <Path to sqldeployment.yaml file>
   ```

   * `<Path to sqldeployment.yaml file>`
      * ファイルを保存した場所です。

   ![展開コマンド](media/tutorial-sql-server-containers-kubernetes/04_deploy_cmd.png)

   展開とサービスが作成されます。 SQL Server インスタンスは、永続的な記憶域に接続 - コンテナー内がします。

   Pod の状態を表示するには、入力`kubectl get pod`です。

   ![Get pod コマンド](media/tutorial-sql-server-containers-kubernetes/05_get_pod_cmd.png)

   >[!NOTE]
   >展開が作成されると、pod を表示するには数分かかる場合があります。 この遅延が、クラスターをプルする必要があるため、 [mssql サーバー linux](https://hub.docker.com/r/microsoft/mssql-server-linux/) Docker hub からイメージ。 初めてプルは後、は、場合は、展開を既にキャッシュされていて、イメージを持つノードでは後続のデプロイが高速にあります。 

1. サービスが実行されていることを確認します。 次のコマンドを実行します。

   ```azurecli
   kubectl get services 
   ```

   このコマンドは、実行されているサービスだけでなく、サービスの内部、および外部の IP アドレスを返します。 外部 IP アドレスに注意してください、`mssql-deployment`サービス。  SQL Server に接続するには、この IP アドレスを使用します。 

   ![サービス コマンドを取得します。](media/tutorial-sql-server-containers-kubernetes/06_get_service_cmd.png)

   Kubernetes クラスター内のオブジェクトの状態に関する詳細については、次のコマンドを実行します。

   ```azurecli
   az aks browse --resource-group <MyResourceGroup> --name <MyKubernetesClustername>
   ```  

## <a name="connect-to-the-sql-server-instance"></a>SQL Server インスタンスに接続します。

説明に従って、コンテナーを構成する場合は、Azure の仮想ネットワークの外部からアプリケーションに接続できます。 使用して、`sa`アカウントと外部 IP アドレス、サービスをします。 Kubernetes シークレットとして構成されているパスワードを使用します。 

次のアプリケーションを使用すると、SQL Server インスタンスに接続します。 

* [SSMS](http://docs.microsoft.com/sql/linux/sql-server-linux-develop-use-ssms)

* [SSDT](http://docs.microsoft.com/en-us/sql/linux/sql-server-linux-develop-use-ssdt)

* 接続するために sqlcmd `sqlcmd`、次のコマンドを実行します。

   ```cmd
   sqlcmd -S <External IP Address> -U sa -P "MyC0m9l&xP@ssw0rd"
   ```

   次の値を置き換えます。
      - `<External IP Address>`IP アドレスを含む、`mssql-deployment`サービス 
      - `MyC0m9l&xP@ssw0rd`自分のパスワード

## <a name="verify-failure-and-recovery"></a>エラーと回復を確認します。

エラーと回復を確認するには、pod を削除できます。 次の手順の操作を行います。

1. SQL Server を実行している pod 型を一覧表示します。

   ```azurecli
   kubectl get pods
   ```

   SQL Server を実行している pod 型の名前に注意してください。

1. Pod を削除します。

   ```azurecli
   kubectl delete pod mssql-deployment-0
   ```
   `mssql-deployment-0`pod 型名の前の手順から返される値。 

Kubernetes には、SQL Server インスタンスを回復し、永続的な記憶域に接続する pod 自動的に再作成します。 使用して`kubectl get pods`新しい pod が展開されていることを確認します。 使用して`kubectl get services`に新しいコンテナーの IP アドレスが同じであることを確認します。 

## <a name="summary"></a>概要

このチュートリアルでは、高可用性を実現 Kubernetes クラスターに SQL Server のコンテナーを展開する方法について学習しました。 

> [!div class="checklist"]
> * 作成 SA パスワード
> * ストレージを作成します。
> * 展開を作成します。
> * SQL Server Management Studio (SSMS) で接続します。
> * エラーと回復を確認します。

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
>[概要 - Kubernetes](http://docs.microsoft.com/en-us/azure/aks/intro-kubernetes)
