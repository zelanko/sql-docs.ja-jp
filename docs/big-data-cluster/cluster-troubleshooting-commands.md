---
title: 監視とトラブルシューティング
titleSuffix: SQL Server big data clusters
description: この記事では、監視、および SQL Server 2019 ビッグ データ クラスター (プレビュー) のトラブルシューティングに便利なコマンドを提供します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 51e6f11460e7a7c1f650b68624cc09d7cea76399
ms.sourcegitcommit: 6193aa9b4967302424270d67c27dbc601ca6849a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/29/2019
ms.locfileid: "64877663"
---
# <a name="monitoring-and-troubleshoot-sql-server-big-data-clusters"></a>監視とビッグ データの SQL Server クラスターのトラブルシューティング

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、監視し、SQL Server 2019 ビッグ データ クラスター (プレビュー) のトラブルシューティングに使用できるいくつかの便利な Kubernetes コマンドについて説明します。 ポッドのビッグ データ クラスターに配置されている Kubernetes の他の成果物の詳細を表示する方法を示します。 この記事では、SQL Server のビッグ データ クラスター サービスのいずれかの操作を実行しているコンテナーとの間にファイルをコピーするなどの一般的なタスクも説明します。

> [!TIP]
> 次の実行**kubectl** (cmd または PS)、Windows または Linux (bash) クライアント コンピューターでコマンド。 クラスターでコマンドを実行するクラスター コンテキストを以前の認証が必要です。 たとえば、以前に作成された AKS クラスターで行うことができます`az aks get-credentials --name <aks_cluster_name> --resource-group <azure_resource_group_name>`を Kubernetes クラスターの構成ファイルをダウンロードし、クラスター コンテキストを設定します。

## <a name="get-status-of-pods"></a>ポッドの状態を取得します。

使用することができます、`kubectl get pods`コマンドをすべての名前空間またはビッグ データ クラスターの名前空間のいずれかのクラスターのポッドの状態を取得します。 次のセクションでは、両方の例を示します。

### <a name="show-status-of-all-pods-in-the-kubernetes-cluster"></a>Kubernetes クラスターにすべてのポッドの状態を表示します。

SQL Server でビッグ データ クラスター ポッドが作成されたすべてのポッドと名前空間の一部であるポッドを含め、その状態を取得するには、次のコマンドを実行します。

```bash
kubectl get pods --all-namespaces
```

### <a name="show-status-of-all-pods-in-the-sql-server-big-data-cluster"></a>SQL Server のビッグ データ クラスター内のすべてのポッドの状態を表示します。

使用して、`-n`パラメーターを特定の名前空間を指定します。 展開構成ファイルで指定されたクラスター名に基づくクラスターのブートス トラップ時に作成された新しい名前空間で、SQL Server のビッグ データ クラスター ポッドが作成されたことに注意してください。 既定の名前、 `mssql-cluster`、ここで使用されます。

```bash
kubectl get pods -n mssql-cluster
```

実行されているビッグ データ クラスターの一覧を次のような出力が表示されます。

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
> ポッド数、展開中に、**状態**の**ContainerCreating**も起動します。 何らかの理由で、展開がハングした場合このことができますが理解できる問題があります。 見ても、**準備**列。 これは、コンテナーの数が、pod で開始します。 展開が、構成とネットワークによって 30 分以上かかることができることに注意してください。 この時間の大半はさまざまなコンポーネントのコンテナー イメージのダウンロードに費やされました。

## <a name="get-pod-details"></a>ポッドの詳細を取得します。

JSON 形式の出力で特定のポッドの詳細な説明を取得するのには、次のコマンドを実行します。 ポッドは、ポッドとコンテナーをブートス トラップするために使用するイメージ内で実行されているコンテナーに配置している現在の Kubernetes ノードなどの詳細情報が含まれています。 また、ラベル、状態などの他の詳細を示していて、ポッドに関連付けられているボリュームの信頼性情報を永続化します。

```bash
kubectl describe pod  <pod_name> -n <namespace_name>
```

次の例の詳細を示しています、`master-0`という名前のビッグ データ クラスターの pod `mssql-cluster`:

```bash
kubectl describe pod  master-0 -n mssql-cluster
```

すべてのエラーが発生した場合は、pod の最近のイベントのエラーも確認できます。

## <a name="get-pod-logs"></a>ポッド ログを取得します。

ポッドで実行されているコンテナーのログを取得することができます。 次のコマンドは、という名前のポッドで実行されているすべてのコンテナーのログを取得`master-0`名前のファイルに出力して`master-0-pod-logs.txt`:

```bash
kubectl logs master-0 --all-containers=true -n mssql-cluser > master-0-pod-logs.txt
```

## <a id="services"></a> サービスの状態を取得します。

ビッグ データ クラスター サービスの詳細を取得するには、次のコマンドを実行します。 これらの詳細は、その型を含めるし、ip アドレスは、それぞれのサービスとポートに関連付けられています。 SQL Server のビッグ データ クラスター サービスが展開構成ファイルで指定されたクラスター名に基づくクラスターのブートス トラップ時に作成された新しい名前空間で作成されたことに注意してください。

```bash
kubectl get svc -n <namespace_name>
```

次の例では、サービスの状態が表示されますという名前のビッグ データ クラスター `mssql-cluster`:

```bash
kubectl get svc -n mssql-cluster
```

次のサービスでは、ビッグ データ クラスターへの外部接続をサポートします。

| サービス | 説明 |
|---|---|
| **master-svc-external** | マスター インスタンスへのアクセスを提供します。<br/>(**EXTERNAL-IP、31433**と**SA**ユーザー) |
| **controller-svc-external** | ツールと、クラスターを管理するクライアントをサポートしています。 |
| **mgmtproxy-svc-external** | アクセスできるように、[クラスター管理ポータル](cluster-admin-portal.md)します。<br/>(https://**EXTERNAL-IP**: 30777/ポータル) |
| **gateway-svc-external** | HDFS/Spark ゲートウェイへのアクセスを提供します。<br/>(**EXTERNAL-IP**と**ルート**ユーザー) |
| **appproxy-svc-external** | アプリケーションの展開シナリオをサポートします。 |

> [!TIP]
> これでサービスを表示する方法は、 **kubectl**を使用することも、`mssqlctl cluster endpoints list`これらのエンドポイントを表示するコマンド。 詳細については、次を参照してください。[ビッグ データ クラスター エンドポイントを取得](deployment-guidance.md#endpoints)します。

## <a name="get-service-details"></a>サービスを詳細します。

JSON 形式の出力に、サービスの詳細な説明を取得するには、このコマンドを実行します。 詳細情報が含まれるようなラベル、セレクターで、IP では、外部 ip アドレス (サービスが LoadBalancer 型の場合)、ポートなど。

```bash
kubectl describe service <service_name> -n <namespace_name>
```

次の例の詳細を取得、 **svc 外部のマスター**サービス。

```bash
kubectl describe service master-svc-external -n mssql-cluster
```

## <a name="run-commands-in-a-container"></a>コンテナー内のコマンドの実行

使用して、コンテナーにログインすることができる場合、既存のツールやインフラストラクチャは、実際に、コンテナーのコンテキストではなく、特定のタスクを実行する無効`kubectl exec`コマンド。 たとえば、特定のファイルが存在するか、コンテナー内のサービスを再起動する必要がありますを確認する必要があります。 

使用する、`kubectl exec`コマンドで、次の構文を使用します。

```bash
kubectl exec -it <pod_name>  -c <container_name> -n <namespace_name> -- /bin/bash <command name> 
```

次の 2 つのセクションでは、コマンドを実行して、特定のコンテナー内の 2 つの例を提供します。

### <a id="restartsql"></a> 特定のコンテナーにログインし、SQL Server プロセスの再起動

次の例で、SQL Server プロセスを再開する方法を示しています、`mssql-server`内のコンテナー、 `master-0` pod:

```bash
kubectl exec -it master-0  -c mssql-server -n mssql-cluster -- /bin/bash 
supervisorctl restart mssql
```

### <a id="restartservices"></a> 特定のコンテナーにログインし、コンテナー内のサービスを再起動
 
次の例は、によって管理されるすべてのサービスを再起動する方法を示しています**supervisord**:。 

```bash
kubectl exec -it master-0  -c mssql-server -n mssql-cluster -- /bin/bash 
supervisorctl -c /opt/supervisor/supervisord.conf reload
```

## <a id="copy"></a> ファイルのコピー

コンテナーからファイルをローカル コンピューターにコピーする必要がある場合を使用して、`kubectl cp`コマンドと、次の構文。

```bash
kubectl cp <pod_name>:<source_file_path> -c <container_name> -n <namespace_name> <target_local_file_path>
```

同様に、使用`kubectl cp`ローカル コンピューターから、特定のコンテナーにファイルをコピーします。

```bash
kubectl cp <source_local_file_path> <pod_name>:<target_container_path> -c <container_name>  -n <namespace_name>
```

### <a id="copyfrom"></a> コンテナーからファイルをコピーします。

次の例では、SQL Server のログ ファイルをコピーするためのコンテナーから、 `~/temp/sqlserverlogs` (この例では、ローカル コンピューターは、Linux クライアント) では、ローカル コンピューター上のパス。

```bash
kubectl cp master-0:/var/opt/mssql/log -c mssql-server -n mssql-cluster ~/tmp/sqlserverlogs
```

### <a id="copyinto"></a> コンテナーにファイルをコピーします。

次の例をコピー、 **AdventureWorks2016CTP3.bak**ファイルをローカル コンピューターから SQL Server のマスター インスタンス コンテナー (`mssql-server`) で、 `master-0` pod です。 ファイルのコピーを`/tmp`コンテナー内のディレクトリ。 

```bash
kubectl cp ~/Downloads/AdventureWorks2016CTP3.bak master-0:/tmp -c mssql-server -n mssql-cluster
```

## <a id="forcedelete"></a> ポッドの強制削除
 
ポッドを強制的に削除するには推奨されません。 可用性、回復性、またはデータの永続性をテストするには、ポッドの失敗をシミュレートするためにポッドを削除することができますが、`kubectl delete pods`コマンド。

```bash
kubectl delete pods <pod_name> -n <namespace_name> --grace-period=0 --force
```

次の例は、記憶域プールのポッドを削除`storage-0-0`:

```bash
kubectl delete pods storage-0-0 -n mssql-cluster --grace-period=0 --force
```

## <a id="getip"></a> ポッド IP を取得します。
 
トラブルシューティングの目的でポッドが実行されている現在のノードの IP を取得する必要があります。 IP アドレスを取得する、`kubectl get pods`コマンドと、次の構文。

```bash
kubectl get pods <pod_name> -o yaml -n <namespace_name> | grep hostIP
```

次の例の取得、ノードの IP アドレス、`master-0`でポッドが実行されています。

```bash
kubectl get pods master-0 -o yaml -n mssql-cluster | grep hostIP
```

## <a name="cluster-administration-portal"></a>クラスターの管理ポータル

使用して、[クラスター管理ポータル](cluster-admin-portal.md)ビッグ データ クラスターの状態を監視します。 たとえば、配置時を使えば、**展開**タブ。待機しなければ、 **mgmtproxy svc-外部**展開の開始時に利用できないようにするために、このポータルにアクセスする前に開始するサービス。

## <a name="kubernetes-dashboard"></a>Kubernetes ダッシュ ボード

詳細については、クラスター、Kubernetes ダッシュ ボードを起動することができます。 次のセクションでは、AKS で Kubernetes と kubeadm を使用してブートス トラップされている Kubernetes ダッシュ ボードを起動する方法を説明します。
 
### <a name="start-dashboard-when-cluster-is-running-in-aks"></a>クラスターが AKS で実行されているときに、ダッシュ ボードを開始します。

実行する Kubernetes ダッシュ ボードを起動するには。

```bash
az aks browse --resource-group <azure_resource_group> --name <aks_cluster_name>
```

> [!Note]
> : 次のエラーが発生した場合*ポート 8001 でリッスンすることができません。すべてのリスナーは、次のエラーを作成できませんでした。リスナーを作成することができません。エラー リッスン tcp4 127.0.0.1:8001: > バインドします。通常、各ソケット アドレス (ネットワーク プロトコル/アドレス/ポート) の 1 つだけを使用できます。リスナーを作成することができません。エラー リッスン tcp6: アドレス [:: 1]: 8001: でのポートがありません > エラーへの対処します。要求されたポートのいずれかでリッスンできません: [{8001 9090}]*、別のウィンドウから既にダッシュ ボードで開始しなかったことを確認します。

お使いのブラウザーでダッシュ ボードを起動すると、AKS クラスターで既定で有効になる RBAC のためのアクセス許可の警告を取得する可能性があります、ダッシュ ボードで使用されるサービス アカウントにはすべてのリソースにアクセスするための十分なアクセス許可がありません (たとえば、 *ポッドは禁止されています。ユーザー"システム: serviceaccount:kube-システム: kubernetes-ダッシュ ボード"、「既定」の名前空間に含まれるポッドを一覧表示できません*)。 必要なアクセス許可を付与するには、次のコマンドを実行`kubernetes-dashboard`、し、ダッシュ ボードを再起動します。

```bash
kubectl create clusterrolebinding kubernetes-dashboard -n kube-system --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard
```

### <a name="start-dashboard-when-kubernetes-cluster-is-bootstrapped--using-kubeadm"></a>Kubeadm を使用して Kubernetes クラスターがブートス トラップ時に、ダッシュ ボードを開始します。

方法の詳細指示を展開し、Kubernetes クラスター内のダッシュ ボードの構成を参照してください[Kubernetes のドキュメント](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/)します。 Kubernetes ダッシュ ボードを起動するには、このコマンドを実行します。

```bash
kubectl proxy
```

## <a name="next-steps"></a>次のステップ

ビッグ データ クラスターに関する詳細については、次を参照してください。 [SQL Server のビッグ データ クラスターは](big-data-cluster-overview.md)します。
