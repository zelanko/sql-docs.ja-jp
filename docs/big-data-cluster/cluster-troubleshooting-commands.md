---
title: 監視とトラブルシューティング
titleSuffix: SQL Server big data clusters
description: この記事では、SQL Server 2019 ビッグデータクラスター (プレビュー) の監視とトラブルシューティングに役立つコマンドについて説明します。
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 272249b7bd6c22895b7d10e7fbce4a20cb647a49
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419482"
---
# <a name="monitoring-and-troubleshoot-sql-server-big-data-clusters"></a>SQL Server ビッグデータクラスターの監視とトラブルシューティング

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、SQL Server 2019 ビッグデータクラスター (プレビュー) の監視とトラブルシューティングに使用できる、いくつかの便利な Kubernetes コマンドについて説明します。 ここでは、ビッグデータクラスターに配置されているポッドまたはその他の Kubernetes 成果物の詳細を表示する方法を示します。 この記事では、SQL Server ビッグデータクラスターサービスのいずれかを実行しているコンテナーとの間でのファイルのコピーなど、一般的なタスクについても説明します。

> [!TIP]
> Windows (cmd または PS) クライアントコンピューターまたは Linux (bash) クライアントコンピューターで、次の**kubectl**コマンドを実行します。 クラスターでの以前の認証と、実行対象のクラスターコンテキストが必要です。 たとえば、以前に作成した AKS クラスターの場合、 `az aks get-credentials --name <aks_cluster_name> --resource-group <azure_resource_group_name>`を実行して Kubernetes クラスター構成ファイルをダウンロードし、クラスターコンテキストを設定できます。

## <a name="get-status-of-pods"></a>ポッドの状態を取得します。

`kubectl get pods`コマンドを使用して、すべての名前空間またはビッグデータクラスターの名前空間のクラスター内のポッドの状態を取得できます。 次のセクションでは、両方の例を示します。

### <a name="show-status-of-all-pods-in-the-kubernetes-cluster"></a>Kubernetes クラスター内のすべてのポッドの状態を表示する

次のコマンドを実行して、すべてのポッドとその状態を取得します。これには、SQL Server ビッグデータクラスターポッドが作成される名前空間の一部であるポッドも含まれます。

```bash
kubectl get pods --all-namespaces
```

### <a name="show-status-of-all-pods-in-the-sql-server-big-data-cluster"></a>SQL Server ビッグデータクラスター内のすべてのポッドの状態を表示します

特定の`-n`名前空間を指定するには、パラメーターを使用します。 SQL Server ビッグデータクラスターポッドは、展開構成ファイルで指定されたクラスター名に基づいて、クラスターのブートストラップ時間に作成された新しい名前空間に作成されることに注意してください。 ここでは、 `mssql-cluster`既定の名前であるが使用されます。

```bash
kubectl get pods -n mssql-cluster
```

実行中のビッグデータクラスターについては、次のような出力が表示されます。

```output
PS C:\> kubectl get pods -n mssql-cluster
NAME              READY   STATUS    RESTARTS   AGE
appproxy-f2qqt    2/2     Running   0          110m
compute-0-0       3/3     Running   0          110m
control-zlncl     4/4     Running   0          118m
data-0-0          3/3     Running   0          110m
data-0-1          3/3     Running   0          110m
gateway-0         2/2     Running   0          109m
logsdb-0          1/1     Running   0          112m
logsui-jtdnv      1/1     Running   0          112m
master-0          7/7     Running   0          110m
metricsdb-0       1/1     Running   0          112m
metricsdc-shv2f   1/1     Running   0          112m
metricsui-9bcj7   1/1     Running   0          112m
mgmtproxy-x6gcs   2/2     Running   0          112m
nmnode-0-0        1/1     Running   0          110m
storage-0-0       7/7     Running   0          110m
storage-0-1       7/7     Running   0          110m
```

> [!NOTE]
> デプロイ中は、 **ContainerCreating**の**状態**を持つポッドが引き続き使用されます。 何らかの理由で展開がハングした場合は、問題が発生する可能性があると考えられます。 **READY (準備完了**)」列も参照してください。 これにより、ポッドで開始されたコンテナーの数がわかります。 デプロイには、構成とネットワークに応じて30分以上かかることがあります。 この時間の大半は、さまざまなコンポーネントのコンテナーイメージのダウンロードに費やされています。

## <a name="get-pod-details"></a>ポッドの詳細を取得する

次のコマンドを実行して、JSON 形式の出力で特定のポッドの詳細な説明を取得します。 これには、ポッドが配置されている現在の Kubernetes ノード、ポッド内で実行されているコンテナー、およびコンテナーのブートストラップに使用されるイメージなどの詳細が含まれます。 また、ラベル、状態、ポッドに関連付けられている永続化ボリューム要求など、その他の詳細も表示されます。

```bash
kubectl describe pod  <pod_name> -n <namespace_name>
```

次の例は、という名前`master-0` `mssql-cluster`のビッグデータクラスター内のポッドの詳細を示しています。

```bash
kubectl describe pod  master-0 -n mssql-cluster
```

エラーが発生した場合は、ポッドの最近のイベントにエラーが表示されることがあります。

## <a name="get-pod-logs"></a>ポッドログを取得する

ポッドで実行されているコンテナーのログを取得できます。 次のコマンドは、という名前`master-0`のポッドで実行されているすべてのコンテナーのログを取得し、ファイル名`master-0-pod-logs.txt`に出力します。

```bash
kubectl logs master-0 --all-containers=true -n mssql-cluser > master-0-pod-logs.txt
```

## <a id="services"></a>サービスの状態を取得する

次のコマンドを実行して、ビッグデータクラスターサービスの詳細を取得します。 これらの詳細には、それぞれのサービスおよびポートに関連付けられている種類と Ip が含まれます。 SQL Server ビッグデータクラスターサービスは、「展開構成ファイル」で指定されているクラスター名に基づいて、クラスターのブートストラップ時間に作成された新しい名前空間に作成されることに注意してください。

```bash
kubectl get svc -n <namespace_name>
```

次の例は、という名前`mssql-cluster`のビッグデータクラスター内のサービスの状態を示しています。

```bash
kubectl get svc -n mssql-cluster
```

次のサービスは、ビッグデータクラスターへの外部接続をサポートしています。

| サービス | 説明 |
|---|---|
| **マスター-svc-外部** | Master インスタンスへのアクセスを提供します。<br/>(**外部 IP、31433** 、および**SA**ユーザー) |
| **コントローラー-svc-外部** | では、クラスターを管理するツールとクライアントがサポートされています。 |
| **ゲートウェイ-svc-外部** | HDFS/Spark ゲートウェイへのアクセスを提供します。<br/>(**外部 IP**および**ルート**ユーザー) |
| **appproxy-svc-外部** | アプリケーションの展開シナリオをサポートします。 |

> [!TIP]
> これは**kubectl**を使用してサービスを表示する方法ですが、コマンドを使用`azdata bdc endpoint list`してこれらのエンドポイントを表示することもできます。 詳細については、「[ビッグデータクラスターエンドポイントの取得](deployment-guidance.md#endpoints)」を参照してください。

## <a name="get-service-details"></a>サービスの詳細の取得

次のコマンドを実行して、JSON 形式の出力でサービスの詳細な説明を取得します。 これには、ラベル、セレクター、IP、外部 IP (サービスの種類が LoadBalancer の場合)、ポートなどの詳細が含まれます。

```bash
kubectl describe service <service_name> -n <namespace_name>
```

次の例では、マスターサービスの**外部**サービスの詳細を取得します。

```bash
kubectl describe service master-svc-external -n mssql-cluster
```

## <a name="run-commands-in-a-container"></a>コンテナー内のコマンドを実行する

既存のツールまたはインフラストラクチャで、実際にはコンテナーのコンテキスト内に存在しない特定のタスクを実行できない場合は、コマンドを使用し`kubectl exec`てコンテナーにログインできます。 たとえば、特定のファイルが存在するかどうか、またはコンテナー内のサービスを再起動する必要があるかどうかを確認することが必要になる場合があります。 

`kubectl exec`コマンドを使用するには、次の構文を使用します。

```bash
kubectl exec -it <pod_name>  -c <container_name> -n <namespace_name> -- /bin/bash <command name> 
```

次の2つのセクションでは、特定のコンテナーでコマンドを実行する2つの例について説明します。

### <a id="restartsql"></a>特定のコンテナーにログインして SQL Server プロセスを再起動する

次の例は、 `mssql-server` `master-0`ポッド内のコンテナー内の SQL Server プロセスを再起動する方法を示しています。

```bash
kubectl exec -it master-0  -c mssql-server -n mssql-cluster -- /bin/bash 
supervisorctl restart mssql
```

### <a id="restartservices"></a>特定のコンテナーにログインし、コンテナー内のサービスを再起動します。
 
次の例は、 **supervisord**によって管理されるすべてのサービスを再起動する方法を示しています。 

```bash
kubectl exec -it master-0  -c mssql-server -n mssql-cluster -- /bin/bash 
supervisorctl -c /opt/supervisor/supervisord.conf reload
```

## <a id="copy"></a>ファイルのコピー

コンテナーからローカルコンピューターにファイルをコピーする必要がある場合は、 `kubectl cp`次の構文でコマンドを使用します。

```bash
kubectl cp <pod_name>:<source_file_path> -c <container_name> -n <namespace_name> <target_local_file_path>
```

同様に、を使用`kubectl cp`して、ローカルコンピューターから特定のコンテナーにファイルをコピーすることもできます。

```bash
kubectl cp <source_local_file_path> <pod_name>:<target_container_path> -c <container_name>  -n <namespace_name>
```

### <a id="copyfrom"></a>コンテナーからファイルをコピーする

次の例では、SQL Server ログファイルをコンテナーからローカル`~/temp/sqlserverlogs`コンピューター上のパスにコピーします (この例では、ローカルコンピューターは Linux クライアントです)。

```bash
kubectl cp master-0:/var/opt/mssql/log -c mssql-server -n mssql-cluster ~/tmp/sqlserverlogs
```

### <a id="copyinto"></a>コンテナーへのファイルのコピー

次の例では、 **AdventureWorks2016CTP3**ファイルをローカルコンピューターから`mssql-server` `master-0` pod 内の SQL Server マスターインスタンスコンテナー () にコピーします。 ファイルは、コンテナー内の`/tmp`ディレクトリにコピーされます。 

```bash
kubectl cp ~/Downloads/AdventureWorks2016CTP3.bak master-0:/tmp -c mssql-server -n mssql-cluster
```

## <a id="forcedelete"></a>ポッドを強制的に削除する
 
ポッドを強制的に削除することはお勧めしません。 ただし、可用性、回復性、またはデータの永続性をテストするために、ポッドを削除し`kubectl delete pods`て、コマンドでポッドエラーをシミュレートすることができます。

```bash
kubectl delete pods <pod_name> -n <namespace_name> --grace-period=0 --force
```

次の例では、記憶域プールポッド`storage-0-0`を削除します。

```bash
kubectl delete pods storage-0-0 -n mssql-cluster --grace-period=0 --force
```

## <a id="getip"></a>ポッド IP を取得する
 
トラブルシューティングのために、ポッドが現在実行されているノードの IP を取得することが必要になる場合があります。 IP アドレスを取得するには、 `kubectl get pods`次の構文でコマンドを使用します。

```bash
kubectl get pods <pod_name> -o yaml -n <namespace_name> | grep hostIP
```

次の例では、 `master-0`ポッドが実行されているノードの IP アドレスを取得します。

```bash
kubectl get pods master-0 -o yaml -n mssql-cluster | grep hostIP
```

## <a name="kubernetes-dashboard"></a>Kubernetes ダッシュボード

Kubernetes ダッシュボードを起動して、クラスターに関する追加情報を確認できます。 以下のセクションでは、AKS で Kubernetes のダッシュボードを起動する方法と、kubeadm を使用して Kubernetes ブートストラップを実行する方法について説明します。
 
### <a name="start-dashboard-when-cluster-is-running-in-aks"></a>AKS でクラスターが実行されているときにダッシュボードを開始する

Kubernetes ダッシュボードを起動するには、次のように実行します。

```bash
az aks browse --resource-group <azure_resource_group> --name <aks_cluster_name>
```

> [!Note]
> 次のエラーが表示された場合:*ポート8001でリッスンできません。次のエラーにより、すべてのリスナーの作成に失敗しました:リスナーを作成できません:エラーリッスン tcp4 127.0.0.1: 8001: > bind:通常は、各ソケットアドレス (プロトコル/ネットワークアドレス/ポート) の1つの使用のみが許可されます。リスナーを作成できません:エラーリッスン tcp6: address [[:: 1]]: 8001: 見つからないポートが > アドレスエラーです:要求されたポート [{8001 9090}]* をリッスンできません。別のウィンドウから既にダッシュボードを開始していないことを確認してください。

ブラウザーでダッシュボードを起動すると、AKS クラスターで RBAC が既定で有効になっているため、アクセス許可の警告が表示される場合があります。また、ダッシュボードで使用されるサービスアカウントには *、すべてのリソースにアクセスするための十分なアクセス許可がありません (たとえば、ポッドは禁止されています。ユーザー "system: serviceaccount: kube: kubernetes" は、名前空間 "default"* のポッドを一覧表示できません。 次のコマンドを実行して`kubernetes-dashboard`、必要なアクセス許可を付与し、ダッシュボードを再起動します。

```bash
kubectl create clusterrolebinding kubernetes-dashboard -n kube-system --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard
```

### <a name="start-dashboard-when-kubernetes-cluster-is-bootstrapped--using-kubeadm"></a>Kubeadm を使用して Kubernetes クラスターがブートストラップされたときにダッシュボードを開始する

Kubernetes クラスターでダッシュボードをデプロイして構成する方法の詳細については、 [Kubernetes のドキュメント](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/)を参照してください。 Kubernetes ダッシュボードを起動するには、次のコマンドを実行します。

```bash
kubectl proxy
```

## <a name="next-steps"></a>次の手順

ビッグデータクラスターの詳細については、「 [SQL Server ビッグデータクラスターとは](big-data-cluster-overview.md)」を参照してください。
