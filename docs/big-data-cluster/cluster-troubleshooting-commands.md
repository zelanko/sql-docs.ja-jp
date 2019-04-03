---
title: Kubectl を使用してモニター/トラブルシューティング
titleSuffix: SQL Server big data clusters
description: この記事では、監視、および SQL Server 2019 ビッグ データ クラスター (プレビュー) のトラブルシューティングに役立ちます kubectl コマンドを提供します。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 8b9be0566725822e0241c65c7f8324b153cca072
ms.sourcegitcommit: 2de5446fbc57787f18a907dd5deb02a7831ec07d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58860373"
---
# <a name="kubectl-commands-for-monitoring-and-troubleshooting-sql-server-big-data-clusters"></a>監視とトラブルシューティングのビッグ データの SQL Server クラスターの Kubectl コマンド

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

この記事では、監視し、SQL Server 2019 ビッグ データ クラスター (プレビュー) のトラブルシューティングに使用できるいくつかの便利な Kubernetes コマンドについて説明します。 この記事では、SQL Server のビッグ データ クラスター サービスのいずれかの操作を実行しているコンテナーとの間にファイルをコピーするなどの一般的なタスクについて説明します。 ポッドのビッグ データ クラスターに配置されている Kubernetes の他の成果物の詳細を表示する方法も示します。

## <a name="kubectl-command-examples"></a>Kubectl コマンドの例

次の実行**kubectl** (cmd または PS)、Windows または Linux (bash) クライアント コンピューターでコマンド。 クラスターでコマンドを実行するクラスター コンテキストを以前の認証が必要です。 たとえば、以前に作成された AKS クラスターで行うことができます`az aks get-credentials --name <aks_cluster_name> --resource-group <azure_resource_group_name>`を Kubernetes クラスターの構成ファイルをダウンロードし、クラスター コンテキストを設定します。

## <a name="get-status-of-pods"></a>ポッドの状態を取得します。

使用することができます、`kubectl get pods`コマンドをすべての名前空間またはビッグ データ クラスターの名前空間のいずれかのクラスターのポッドの状態を取得します。 次のセクションでは、両方の例を示します。

### <a name="show-status-of-all-pods-in-the-kubernetes-cluster"></a>Kubernetes クラスターにすべてのポッドの状態を表示します。

SQL Server でビッグ データ クラスター ポッドが作成されたすべてのポッドと名前空間の一部であるポッドを含め、その状態を取得するには、次のコマンドを実行します。

```bash
kubectl get pods --all-namespaces
```

### <a name="show-status-of-all-pods-in-the-sql-server-big-data-cluster"></a>SQL Server のビッグ データ クラスター内のすべてのポッドの状態を表示します。

使用して、`-n`パラメーターを特定の名前空間を指定します。 SQL Server のクラスターのブートス トラップ時に作成された新しい名前空間でビッグ データ クラスター ポッドが作成されますで指定されたクラスター名に基づくことに注意してください、`mssqlctl cluster create --name <cluster_name>`コマンド。

```bash
kubectl get pods -n <namespace_name>
```

次のコマンドがという名前のビッグ データ クラスターでのポッドの状態を表示するなど、 `big_data_cluster`:

```bash
kubectl get pods -n big_data_cluster
```

## <a name="get-pod-details"></a>ポッドの詳細を取得します。

Json 形式の出力で特定のポッドの詳細な説明を取得するのには、次のコマンドを実行します。 ポッドは、ポッドとコンテナーをブートス トラップするために使用するイメージ内で実行されているコンテナーに配置している現在の Kubernetes ノードなどの詳細情報が含まれています。 また、ラベル、状態などの他の詳細を示していて、ポッドに関連付けられているボリュームの信頼性情報を永続化します。

```bash
kubectl describe pod  <pod_name> -n <namespace_name>
```

次の例の詳細を示しています、`mssql-data-pool-master-0`という名前のビッグ データ クラスターの pod `big_data_cluster`:

```bash
kubectl describe pod  mssql-data-pool-master-0 -n big_data_cluster
```

## <a name="get-status-of-services"></a>サービスの状態を取得します。

ビッグ データ クラスター サービスの詳細を取得するには、次のコマンドを実行します。 これらの詳細は、その型を含めるし、ip アドレスは、それぞれのサービスとポートに関連付けられています。 SQL Server のビッグ データ クラスター サービスがで指定されたクラスター名に基づくクラスターのブートス トラップ時に作成された新しい名前空間で作成されたことに注意してください、`mssqlctl cluster create --name <cluster_name>`コマンド。

```bash
kubectl get svc -n <namespace_name>
```

次の例では、サービスの状態が表示されますという名前のビッグ データ クラスター `big_data_cluster`:

```bash
kubectl get svc -n big_data_cluster
```

## <a name="get-service-details"></a>サービスを詳細します。

Json 形式の出力に、サービスの詳細な説明を取得するには、このコマンドを実行します。 詳細情報が含まれるようなラベル、セレクターで、IP では、外部 ip アドレス (サービスが LoadBalancer 型の場合)、ポートなど。
```
kubectl describe pod  <pod_name> -n <namespace_name>
```

例:
```
kubectl describe pod  mssql-data-pool-master-0 -n big_data_cluster
```

## <a name="run-commands-in-a-container"></a>コンテナー内のコマンドの実行

使用して、コンテナーにログインすることができる場合、既存のツールやインフラストラクチャは、実際に、コンテナーのコンテキストではなく、特定のタスクを実行する無効`kubectl exec`コマンド。 たとえば、特定のファイルが存在するか、コンテナー内のサービスを再起動する必要がありますを確認する必要があります。 

使用する、`kubectl exec`コマンドで、次の構文を使用します。

```bash
kubectl exec -it <pod_name>  -c <container_name> -n <namespace_name> -- /bin/bash <command name> 
```

次の 2 つのセクションでは、コマンドを実行して、特定のコンテナー内の 2 つの例を提供します。

### <a id="restartsql"></a> 特定のコンテナーにログインし、SQL Server プロセスの再起動

次の例で、SQL Server プロセスを再開する方法を示しています、`mssql-server`内のコンテナー、 `mssql-master-pool-0` pod:

```bash
kubectl exec -it mssql-master-pool-0  -c mssql-server -n big_data_cluster -- /bin/bash 
supervisorctl restart mssql
```

### <a id="restartservices"></a> 特定のコンテナーにログインし、コンテナー内のサービスを再起動
 
次の例は、によって管理されるすべてのサービスを再起動する方法を示しています**supervisord**:。 

```bash
kubectl exec -it mssql-master-pool-0  -c mssql-server -n big_data_cluster -- /bin/bash 
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
kubectl cp mssql-master-pool-0:/var/opt/mssql/log -c mssql-server -n big_data_cluster ~/tmp/sqlserverlogs
```

### <a id="copyinto"></a> コンテナーにファイルをコピーします。

次の例をコピー、 **AdventureWorks2016CTP3.bak**ファイルをローカル コンピューターから SQL Server のマスター インスタンス コンテナー (`mssql-server`) で、 `mssql-master-pool-0` pod です。 ファイルのコピーを`/tmp`コンテナー内のディレクトリ。 

```bash
kubectl cp ~/Downloads/AdventureWorks2016CTP3.bak mssql-master-pool-0:/tmp -c mssql-server -n big_data_cluster
```

## <a id="forcedelete"></a> ポッドの強制削除
 
ポッドを強制的に削除するには推奨されません。 可用性、回復性、またはデータの永続性をテストするには、ポッドの失敗をシミュレートするためにポッドを削除することができますが、`kubectl delete pods`コマンド。

```bash
kubectl delete pods <pod_name> -n <namespace_name> --grace-period=0 --force
```

次の例は、記憶域プールのポッドを削除`mssql-storage-pool-default-0`:

```bash
kubectl delete pods mssql-storage-pool-default-0 -n big_data_cluster --grace-period=0 --force
```

## <a id="getip"></a> ポッド IP を取得します。
 
トラブルシューティングの目的でポッドが実行されている現在のノードの IP を取得する必要があります。 IP アドレスを取得する、`kubectl get pods`コマンドと、次の構文。

```bash
kubectl get pods <pod_name> -o yaml -n <namespace_name> | grep hostIP
```

次の例の取得、ノードの IP アドレス、`mssql-master-pool-0`でポッドが実行されています。

```bash
kubectl get pods mssql-master-pool-0 -o yaml -n big_data_cluster | grep hostIP
```

## <a name="start-the-kubernetes-dashboard"></a>Kubernetes ダッシュ ボードを起動します。

詳細については、クラスター、Kubernetes ダッシュ ボードを起動することができます。 次のセクションでは、AKS で Kubernetes と kubeadm を使用してブートス トラップされている Kubernetes ダッシュ ボードを起動する方法を説明します。
 
### <a name="start-dashboard-when-cluster-is-running-in-aks"></a>クラスターが AKS で実行されているときに、ダッシュ ボードを開始します。

実行する Kubernetes ダッシュ ボードを起動するには。
 
```bash
az aks browse --resource-group <azure_resource_group> --name <aks_cluster_name>
```

> [!Note]
> : 次のエラーが発生した場合*ポート 8001 でリッスンすることができません。すべてのリスナーは、次のエラーを作成できませんでした。リスナーを作成することができません。エラー リッスン tcp4 127.0.0.1:8001: > バインドします。通常、各ソケット アドレス (ネットワーク プロトコル/アドレス/ポート) の 1 つだけを使用できます。リスナーを作成することができません。エラー リッスン tcp6: アドレス [:: 1]: 8001: でのポートがありません > エラーへの対処します。要求されたポートのいずれかでリッスンできません: [{8001 9090}]*、別のウィンドウから既にダッシュ ボードで開始しなかったことを確認します。

お使いのブラウザーでダッシュ ボードを起動すると、AKS クラスターで既定で有効になる RBAC のためのアクセス許可の警告を取得する可能性があります、ダッシュ ボードで使用されるサービス アカウントにはすべてのリソースにアクセスするための十分なアクセス許可がありません (たとえば、 *ポッドは禁止されています。ユーザー"システム: serviceaccount:kube-システム: kubernetes-ダッシュ"、「既定」の名前空間に含まれるポッドを一覧表示できません*)。 必要なアクセス許可を付与するには、次のコマンドを実行`kubernetes-dashboard`、し、ダッシュ ボードを再起動します。

```
kubectl create clusterrolebinding kubernetes-dashboard -n kube-system --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard
```

### <a name="start-dashboard-when-kubernetes-cluster-is-bootstrapped--using-kubeadm"></a>Kubeadm を使用して Kubernetes クラスターがブートス トラップ時に、ダッシュ ボードを開始します。

方法の詳細指示を展開し、Kubernetes クラスター内のダッシュ ボードの構成を参照してください[Kubernetes のドキュメント](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/)します。 Kubernetes ダッシュ ボードを起動するには、このコマンドを実行します。

```
kubectl proxy
```

## <a name="next-steps"></a>次のステップ

監視とトラブルシューティングは SQL Server に固有ビッグ データ クラスターを参照してください、[クラスター管理ポータル](cluster-admin-portal.md)します。