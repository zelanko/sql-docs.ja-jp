---
title: SQL Server Always On 可用性グループ Kubernetes を管理する
description: この記事では、Kubernetes の SQL Server Always On 可用性グループを管理する方法について説明します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 09/24/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 893e502c35ae33ce6ff87efd88049db97a40f875
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2019
ms.locfileid: "67952543"
---
# <a name="manage-sql-server-always-on-availability-group-kubernetes"></a>SQL Server Always On 可用性グループ Kubernetes を管理する

Kubernetes の Always On 可用性グループを管理するには、マニフェストを作成し、それをクラスターに適用します。 マニフェストは `.yaml` ファイルです。  

この記事の例は、すべての Kubernetes クラスターに適用されます。 これらの例のシナリオは、Azure Kubernetes Service のクラスターに対して適用されます。

完全な展開の例については、「[Kubernetes クラスターに SQL Server Always On 可用性グループを展開する](sql-server-linux-kubernetes-deploy.md)」を参照してください。

## <a name="fail-over---sql-server-availability-group-on-kubernetes"></a>フェールオーバーする - Kubernetes の SQL Server 可用性グループ

プライマリ レプリカを可用性グループ内の別のノードにフェール オーバーまたは移動するには、次の手順を完了します。

1. マニフェスト ファイルでジョブを定義します。

  [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files) github リポジトリの [`failover.yaml`](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/failover.yaml) では、フェールオーバー ジョブについて説明されています。

  マニフェスト ファイルを管理ターミナルにコピーします。

  環境に合わせてファイルを更新します。

  - `<containerName>` を、予想される可用性グループ ターゲットのポッド名 (例: mssql2-0) に置き換えます。
  - 可用性グループが `ag1` 名前空間にない場合は、`ag1` を名前空間に置き換えます。

  このファイルでは、`manual-failover` という名前のフェールオーバー ジョブを定義します。

1. ジョブを展開するには、`kubectl apply` を使用します。 次のスクリプトでは、ジョブを展開します。

  ```azurecli
  kubectl apply -f failover.yaml
  ```

  ジョブが展開された後、Kubernetes では SQL Server 演算子を使用して次のタスクを行います。
  
  - プライマリ レプリカをセカンダリに降格する
  
  - 指定されたレプリカをプライマリに昇格する
  
  マニフェスト ファイルを適用した後、Kubernetes でジョブが実行されます。 このジョブでは、スーパーバイザーは新しいリーダーを選択し、プライマリ レプリカがリーダーの SQL Server インスタンスに移動されます。

1. ジョブが完了したことを確認します。
  
  Kubernetes でジョブが実行された後、ログを確認できます。
  
  次の例では、`manual-failover` という名前のジョブの状態が返されます。

  ```azurecli
  kubectl describe jobs/manual-failover --namespace ag1
  ```

1. 手動フェールオーバー ジョブを削除します。 

  >[!IMPORTANT]
  >別の手動フェールオーバーを実行する前に、手動でジョブを削除する必要があります。
  > 
  >Kubernetes のジョブ オブジェクトは完了後も維持されるので、その状態を確認できます。 古いジョブは、その状態を確認した後、手動で削除する必要があります。 ジョブを削除すると、Kubernetes ログも削除されます。 ジョブを削除しないと、ジョブ名とポッド セレクターを変更しない限り、今後のフェールオーバー ジョブは失敗します。 詳細については、「[ジョブ - 実行から完了まで](https://kubernetes.io/docs/concepts/workloads/controllers/jobs-run-to-completion/)」を参照してください。

  次のコマンドではジョブが削除されます。

  ```azurecli
  kubectl delete jobs manual-failover --namespace ag1
  ```

## <a name="rotate-credentials"></a>資格情報を交換する

資格情報を交換し、SQL Server の `sa` アカウントと SQL Server の[サービス マスター キー](../relational-databases/security/encryption/service-master-key.md) のパスワードをリセットします。 

このタスクを完了するには、Kubernetes クラスターで新しいシークレットを作成してから、資格情報を交換するためのジョブを作成します。

資格情報を交換する前に、パスワードとマスター キーの新しいシークレットを作成します。

次のスクリプトでは、`new-sql-secrets` という名前のシークレットを作成します。 スクリプトを実行する前に、`<>` を、`sapassword` および `masterkeypassword` の複雑なパスワードに置き換えます。 それぞれの値に対して異なるパスワードを使用します。

```azurecli
kubectl create secret generic new-sql-secrets --from-literal=sapassword="<>" --from-literal=masterkeypassword="<>"  --namespace ag1
```

マスター キーまたは `sa` パスワードを必要とする SQL Server のすべてのインスタンスについて、次の手順を完了します。

1. [`rotate-creds.yaml`](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/rotate-creds.yaml) を管理ターミナルにコピーします。

  [sql-server-samples](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-deployment-script/) github リポジトリの [`rotate-creds.yaml`](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/rotate-creds.yaml) は、このジョブのマニフェストの例です。

  このマニフェストを適用する前に、環境に合わせてマニフェストを更新します。 次の設定を確認し、必要に応じて変更します。

  - 名前空間を確認します。 必要に応じて更新します。 マニフェストの次の例は、`ag1` という名前空間に適用されます。

    ```yaml
    metadata:
      name: rotate-creds
      namespace: ag1
    ```

  - SQL Server インスタンスの名前を確認します。 必要に応じて更新します。 マニフェスト仕様の次の例は、`mssql1` という名前の SQL Server インスタンスに適用されます。

    ```yaml
    env:
      - name: MSSQL_K8S_SQL_SERVER_NAME
        value: mssql1
    ```

  更新されたマニフェスト ファイルをワークステーションに保存します。

1. `kubectl` を使用してジョブを展開します。

  ```azurecli
  kubectl apply -f rotate-creds.yaml --namespace ag1
  ```

  Kubernetes では、可用性グループ内の SQL Server の 1 つのインスタンスのマスターキーと `sa` パスワードを更新します。

1. ジョブが完了したことを確認します。 次のコマンドを実行します。ジョブが完了したことを確認するには、以下を実行します。 

  ```azcli
  kubectl describe job rotate-creds --namespace ag1
  ```

  ジョブが成功した後、SQL Server の 1 つのインスタンスのマスター キーと `sa` パスワードが更新されます。


1. ジョブを再度実行する前に、ジョブを削除します。 各ジョブ名は一意である必要があります。

  ```azurecli
  kubectl delete job rotate-creds --namespace ag1
  ```

SQL Server のすべてのインスタンスに同じ `sa` パスワードを設定するには、SQL Server の各インスタンスに対して上記の手順を繰り返します。

## <a name="next-steps"></a>次の手順

[Azure Kubernetes Service (AKS) を使用して Kubernetes ダッシュボードにアクセスする](https://docs.microsoft.com/azure/aks/kubernetes-dashboard)

[Kubernetes クラスターの SQL Server 可用性グループ](sql-server-ag-kubernetes.md)
