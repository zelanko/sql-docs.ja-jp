---
title: SQL Server Always On 可用性グループを Kubernetes の管理します。
description: この記事では、SQL Server Always On 可用性グループで Kubernetes を管理する方法について説明します。
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 09/24/2018
ms.topic: article
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: ad4f310ce6c0e200d5e658b3d5814131000d0004
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2018
ms.locfileid: "52518492"
---
# <a name="manage-sql-server-always-on-availability-group-kubernetes"></a>SQL Server Always On 可用性グループの Kubernetes を管理します。

Always On 可用性グループで Kubernetes を管理するには、マニフェストを作成し、クラスターに適用します。 マニフェストは、`.yaml`ファイル。  

この記事の例では、すべての Kubernetes クラスターに適用されます。 これらの例のシナリオは、Azure Kubernetes サービス上のクラスターに対して適用されます。

完全な展開の例を参照してください。 [、SQL Server Always On 可用性グループに Kubernetes クラスターをデプロイ](sql-server-linux-kubernetes-deploy.md)します。

## <a name="fail-over---sql-server-availability-group-on-kubernetes"></a>フェールオーバー - Kubernetes 上の SQL Server 可用性グループ

フェールオーバーまたはプライマリ レプリカを可用性グループ内の異なるノードに移動に、次の手順を行います。

1. マニフェスト ファイルで、ジョブを定義します。

  [`failover.yaml`](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/failover.yaml) -で、 [sql server のサンプル](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files)github リポジトリには、フェールオーバー ジョブがについて説明します。

  ターミナルに管理するには、マニフェスト ファイルをコピーします。

  環境内のファイルを更新します。

  - 置換`<containerName>`で期待される可用性グループのターゲットのポッド名 (例: mssql2-0)。
  - 可用性グループが含まれていない場合、`ag1`名前空間、置き換える`ag1`名前空間を持つ。

  このファイルは、という名前のフェールオーバー ジョブを定義します。`manual-failover`します。

1. ジョブをデプロイするには使用`kubectl apply`します。 次のスクリプトは、ジョブをデプロイします。

  ```azurecli
  kubectl apply -f failover.yaml
  ```

  ジョブが配置されると、kubernetes では、SQL サーバーの操作では、次のタスクを行います。
  
  - プライマリ レプリカをセカンダリへ降格します。
  
  - 指定したレプリカをプライマリに昇格させます
  
  マニフェスト ファイルを適用した後、Kubernetes は、ジョブを実行します。 ジョブは、新しいリーダーを選択して、supervisor を行い、リーダーの SQL Server インスタンスにプライマリ レプリカを移動します。

1. ジョブが完了したことを確認します。
  
  Kubernetes は、ジョブを実行した後、ログを確認できます。
  
  次の例は、という名前のジョブの状態を返します`manual-failover`します。

  ```azurecli
  kubectl describe jobs/manual-failover --namespace ag1
  ```

1. 手動のフェールオーバー ジョブを削除します。 

  >[!IMPORTANT]
  >別の手動フェールオーバーを実行する前に、ジョブを手動で削除する必要があります。
  > 
  >Kubernetes でのジョブ オブジェクトは、その状態を表示できるように完了した後が維持されます。 それらの状態を記録した後、古いジョブを手動で削除する必要があります。 ジョブを削除すると、Kubernetes のログも削除されます。 ジョブを削除しない場合、ジョブの名前と、ポッドのセレクターを変更しない限り、今後のフェールオーバー ジョブは失敗します。 詳細については、[- ジョブが完了するまで実行](https://kubernetes.io/docs/concepts/workloads/controllers/jobs-run-to-completion/)を参照してください。

  次のコマンドは、ジョブを削除します。

  ```azurecli
  kubectl delete jobs manual-failover --namespace ag1
  ```

## <a name="rotate-credentials"></a>資格情報を交換します。

SQL Server のパスワードをリセットする資格情報の交換`sa`アカウントと SQL Server[サービス マスター _ キー](../relational-databases/security/encryption/service-master-key.md)します。 

このタスクを完了するには、は、Kubernetes クラスターで新しいシークレットが作成され、資格情報を交換するジョブを作成します。

資格情報を交換する前に、パスワードと、マスター _ キーの新しいシークレットを作成します。

次のスクリプト作成という名前のシークレット`new-sql-secrets`します。 スクリプトを実行する前に置き換える`<>`の複雑なパスワードを持つ、 `sapassword` 、`masterkeypassword`します。 それぞれの値ごとに異なるパスワードを使用します。

```azurecli
kubectl create secret generic new-sql-secrets --from-literal=sapassword="<>" --from-literal=masterkeypassword="<>"  --namespace ag1
```

マスター _ キーが必要な SQL Server のインスタンスごとに、次の手順を完了または`sa`パスワード。

1. コピー [ `rotate-creds.yaml` ](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/rotate-creds.yaml)ターミナルに管理します。

  [`rotate-creds.yaml`](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/rotate-creds.yaml) [sql server のサンプル](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-deployment-script/)github リポジトリは、このジョブのマニフェストの例を示します。

  このマニフェストを適用する前に、環境内のマニフェストを更新します。 確認し、必要に応じて、次の設定を変更します。

  - 名前空間を確認します。 必要に応じて更新します。 マニフェストで次の例は、名前空間に適用`ag1`します。

    ```yaml
    metadata:
      name: rotate-creds
      namespace: ag1
    ```

  - SQL Server インスタンスの名前を確認します。 必要に応じて更新します。 マニフェストの仕様では、次の例は、という名前の SQL Server インスタンスに適用`mssql1`します。

    ```yaml
    env:
      - name: MSSQL_K8S_SQL_SERVER_NAME
        value: mssql1
    ```

  更新されたマニフェスト ファイルをワークステーションに保存します。

1. 使用`kubectl`ジョブをデプロイします。

  ```azurecli
  kubectl apply -f rotate-creds.yaml --namespace ag1
  ```

  Kubernetes は、マスター _ キーを更新し、 `sa` SQL Server の可用性グループ内の 1 つのインスタンスのパスワード。

1. ジョブが完了したことを確認します。 次のコマンドを実行します。ジョブが完了したことを確認するに次のように実行します。 

  ```azcli
  kubectl describe job rotate-creds --namespace ag1
  ```

  ジョブが成功すると、マスター _ キーと`sa`SQL Server のインスタンスを 1 つのパスワードを更新します。


1. ジョブをもう一度実行する前に、ジョブを削除します。 各ジョブの名前は一意である必要があります。

  ```azurecli
  kubectl delete job rotate-creds --namespace ag1
  ```

同じように設定する`sa`、SQL Server のすべてのインスタンスのパスワードは、SQL Server のインスタンスごとに上記の手順を繰り返します。

## <a name="next-steps"></a>次の手順

[Azure Kubernetes Service (AKS) での Kubernetes ダッシュ ボードにアクセスします。](https://docs.microsoft.com/azure/aks/kubernetes-dashboard)

[Kubernetes クラスター上の SQL Server 可用性グループ](sql-server-ag-kubernetes.md)
