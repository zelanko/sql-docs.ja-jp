---
title: GPU のサポートと TensorFlow
titleSuffix: SQL Server 2019 big data clusters
description: GPU サポートと共に、ビッグ データ クラスターを展開し、Azure データ Studio ノートブックで TensorFlow を使用します。
author: lgongmsft
ms.author: shivprashant
ms.reviewer: jroth
manager: craigg
ms.date: 03/27/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: f89568860fa656efbb93eb9b72eb647f88ce6089
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58494114"
---
# <a name="deploy-a-big-data-cluster-with-gpu-support-and-run-tensorflow"></a>GPU サポートと共に、ビッグ データ クラスターをデプロイして TensorFlow の実行

この記事では、ビッグ データ クラスター コンピューティング集中型ワークロードの GPU 対応ノード プールをサポートする Azure Kubernetes Service (AKS) でデプロイする方法を示します。 Gpu TensorFlow による画像の分類を実行する Azure Data Studio でのサンプル notebook を実行します。

## <a name="prerequisites"></a>前提条件

- [ビッグ データ ツール](deploy-big-data-tools.md):
  - **mssqlctl**
  - **kubectl**
  - **Azure Data Studio**
  - **SQL Server 2019 の拡張機能**
  - **Azure CLI**

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="create-an-aks-cluster"></a>AKS クラスターを作成します。

次の手順では、Gpu をサポートする AKS クラスターを作成するのに Azure CLI を使用します。

1. コマンド プロンプトで次のコマンドを実行し、Azure サブスクリプションにログインの指示に従います。

    ```azurecli
    az login
    ```

1. 使用してリソース グループを作成、 **az グループ作成**コマンド。 次の例は、という名前のリソース グループを作成します。`sqlbigdatagroupgpu`で、`eastus`場所。

   ```azurecli
   az group create --name sqlbigdatagroupgpu --location eastus
   ```

1. 使用して AKS で Kubernetes クラスターを作成、 [az aks 作成](https://docs.microsoft.com/cli/azure/aks)コマンド。 次の例では、という名前の Kubernetes クラスターを作成する`gpucluster`で、`sqlbigdatagroupgpu`リソース グループ。

   ```azurecli
   az aks create --name gpucluster --resource-group sqlbigdatagroupgpu --generate-ssh-keys --node-vm-size Standard_NC6 --node-count 3 --node-osdisk-size 50 --kubernetes-version 1.11.7 --location eastus
   ```

   > [!NOTE]
   > このクラスターを使用して、 **Standard_NC6** [GPU 最適化済み仮想マシンのサイズ](https://docs.microsoft.com/azure/virtual-machines/linux/sizes-gpu)、1 つまたは複数の NVIDIA Gpu で利用可能な特殊化された仮想マシンの 1 つです。 詳細については、次を参照してください。[コンピューティング集中型ワークロードを Azure Kubernetes Service (AKS) を使用して Gpu](https://docs.microsoft.com/azure/aks/gpu-cluster)します。

1. Kubernetes クラスターに接続するように kubectl を構成するには、実行、 [az aks 資格情報の取得](https://docs.microsoft.com/cli/azure/aks?view=azure-cli-latest#az-aks-get-credentials)コマンド。

   ```azurecli
   az aks get-credentials --overwrite-existing --resource-group=sqlbigdatagroupgpu --name gpucluster
   ```

## <a name="apply-yaml-manifest"></a>YAML マニフェストを適用します。

1. 使用**kubectl**という名前の Kubernetes 名前空間を作成する`gpu-resources`します。

   ```
   kubectl create namespace gpu-resources
   ```

1. 次の YAML ファイルの内容をという名前のファイルに保存**nvidia デバイス プラグイン ds.yaml**します。 これを実行しているコンピューターでの作業ディレクトリに保存**kubectl**から。

   更新プログラム、 `image: nvidia/k8s-device-plugin:1.11` Kubernetes バージョンと一致するマニフェストの途中です。 たとえば、AKS クラスターでは、Kubernetes バージョン 1.12 を実行する場合にタグを更新`image: nvidia/k8s-device-plugin:1.12`します。

   ```yaml
   apiVersion: extensions/v1beta1
   kind: DaemonSet
   metadata:
     labels:
       kubernetes.io/cluster-service: "true"
     name: nvidia-device-plugin
     namespace: gpu-resources
   spec:
     template:
       metadata:
         # Mark this pod as a critical add-on; when enabled, the critical add-on scheduler
         # reserves resources for critical add-on pods so that they can be rescheduled after
         # a failure.  This annotation works in tandem with the toleration below.
         annotations:
           scheduler.alpha.kubernetes.io/critical-pod: ""
         labels:
           name: nvidia-device-plugin-ds
       spec:
         tolerations:
         # Allow this pod to be rescheduled while the node is in "critical add-ons only" mode.
         # This, along with the annotation above marks this pod as a critical add-on.
         - key: CriticalAddonsOnly
           operator: Exists
         containers:
         - image: nvidia/k8s-device-plugin:1.11 # Update this tag to match your Kubernetes version
           name: nvidia-device-plugin-ctr
           securityContext:
             allowPrivilegeEscalation: false
             capabilities:
               drop: ["ALL"]
           volumeMounts:
             - name: device-plugin
               mountPath: /var/lib/kubelet/device-plugins
         volumes:
           - name: device-plugin
             hostPath:
               path: /var/lib/kubelet/device-plugins
         nodeSelector:
           beta.kubernetes.io/os: linux
           accelerator: nvidia
   ```

1. ここで、kubectl を使用してでは、DaemonSet を作成するコマンドが適用されます。 **nvidia デバイス プラグイン ds.yaml**次のコマンドを実行すると、作業ディレクトリである必要があります。

   ```
   kubectl apply -f nvidia-device-plugin-ds.yaml
   ```

## <a name="deploy-the-big-data-cluster"></a>ビッグ データ クラスターをデプロイします。

Gpu をサポートする SQL Server 2019 ビッグ データ クラスター (プレビュー) を展開するには、特定の docker レジストリとリポジトリからデプロイする必要があります。 具体的には、さまざまな値を使用する**DOCKER_REGISTRY**、 **DOCKER_REPOSITORY**、 **DOCKER_USERNAME**、 **DOCKER_PASSWORD**、**DOCKER_EMAIL**します。 次のセクションでは、環境変数を設定する方法の例を提供します。 ビッグ データ クラスターのデプロイに使用しているクライアントのプラットフォームに応じて、Windows または Linux のいずれかのセクションを使用します。

### <a name="windows"></a>Windows

   1. コマンド ウィンドウ (PowerShell ではなく) を使用して、次の環境変数を構成します。 値を囲む引用符は使用しないでください。

      ```cmd
      SET ACCEPT_EULA=yes
      SET CLUSTER_PLATFORM=aks

      SET CONTROLLER_USERNAME=<controller_admin_name - can be anything>
      SET CONTROLLER_PASSWORD=<controller_admin_password - can be anything, password complexity compliant>
      SET KNOX_PASSWORD=<knox_password - can be anything, password complexity compliant>
      SET MSSQL_SA_PASSWORD=<sa_password_of_master_sql_instance, password complexity compliant>

      SET DOCKER_REGISTRY=marinchcreus3.azurecr.io
      SET DOCKER_REPOSITORY=ctp23-8-0-61-gpu
      SET DOCKER_USERNAME=<your username, gpu-specific credentials provided by Microsoft>
      SET DOCKER_PASSWORD=<your password, gpu-specific credentials provided by Microsoft>
      SET DOCKER_EMAIL=<your email address>
      SET DOCKER_PRIVATE_REGISTRY=1
      SET STORAGE_SIZE=10Gi
      ```

   1. ビッグ データ クラスターをデプロイするには。

      ```cmd
      mssqlctl cluster create --name gpubigdatacluster
      ```

### <a name="linux"></a>Linux

   1. 次の環境変数を初期化します。 Bash では、各値を囲む引用符を使用できます。

      ```bash
      export ACCEPT_EULA=yes
      export CLUSTER_PLATFORM="aks"

      export CONTROLLER_USERNAME="<controller_admin_name - can be anything>"
      export CONTROLLER_PASSWORD="<controller_admin_password - can be anything, password complexity compliant>"
      export KNOX_PASSWORD="<knox_password - can be anything, password complexity compliant>"
      export MSSQL_SA_PASSWORD="<sa_password_of_master_sql_instance, password complexity compliant>"

      export DOCKER_REGISTRY="marinchcreus3.azurecr.io"
      export DOCKER_REPOSITORY="ctp23-8-0-61-gpu"
      export DOCKER_USERNAME="<your username, gpu-specific credentials provided by Microsoft>"
      export DOCKER_PASSWORD="<your password, gpu-specific credentials provided by Microsoft>"
      export DOCKER_EMAIL="<your email address>"
      export DOCKER_PRIVATE_REGISTRY="1"
      export STORAGE_SIZE="10Gi"
      ```

   1. ビッグ データ クラスターをデプロイするには。

      ```bash
      mssqlctl cluster create --name gpubigdatacluster
      ```

## <a name="run-the-tensorflow-example"></a>TensorFlow の例を実行します。

次の 2 つのサンプル notebook は、2 つのイメージ分類モデルのトレーニング gpu TensorFlow を使用して Spark クラスターの 1 つのノードで示しています。

| Notebook のダウンロード | 説明 |
|---|---|
| [**tf-cuda8.ipynb**](https://aka.ms/AA4jdgd) | 8 CUDA、CUDNN 6、および TensorFlow 1.4.0 を使用します。  |
| [**tf-cuda9.ipynb**](https://aka.ms/AA4ixzr) | 9 CUDA、CUDNN 7、および 1.12.0 TensorFlow を使用します。 |

ローカル コンピューターに適切なノートブック ファイルを配置し、開く PySpark3 カーネルを使用して Azure Data Studio で実行します。 CUDA や TensorFlow の古いバージョンの特別なニーズがない限り、CUDA 9/CUDNN 7/TensorFlow 1.12.0 を選択します。 ビッグ データ クラスターで notebook を使用する方法の詳細については、次を参照してください。 [SQL Server 2019 プレビューで notebook を使用する方法](notebooks-guidance.md)します。

> [!NOTE]
> ノートブックがシステムの場所でソフトウェアをインストールすることに注意してください。 Notebook は、現在 CTP 2.4 でルート権限で実行されるため、可能です。

GPU の NVIDIA GPU ライブラリと TensorFlow をインストールすると、ノートブックには、使用可能な GPU デバイスが一覧表示します。 適合し、MNIST データ セットを使用して手書きの数字を認識する TensorFlow モデルを評価します。 使用可能なディスク領域を確認するには後の ダウンロードしてから 10 の CIFAR イメージ分類の例を実行する[ https://github.com/tensorflow/models.git](https://github.com/tensorflow/models.git)します。 CIFAR 10 例が別の Gpu クラスターで実行すると、GPU が Azure で使用できるは、各ジェネレーションで提供される速度の増加を確認できます。

## <a name="clean-up-resources"></a>リソースをクリーンアップします。

ビッグ データ クラスターを削除するには、次のコマンドを使用します。

```
mssqlctl cluster delete --name gpubigdatacluster
```

前のコマンドでは、AKS クラスターは削除されません。 AKS クラスターと関連付けられているリソースを削除するには、次のコマンドを使用します。

```azurecli
az group delete -n sqlbigdatagroupgpu
```

## <a name="next-steps"></a>次のステップ

SQL Server 2019 ビッグ データ クラスター (プレビュー) の詳細については、次を参照してください。 [SQL Server 2019 ビッグ データ クラスターには何ですか?](big-data-cluster-overview.md)。