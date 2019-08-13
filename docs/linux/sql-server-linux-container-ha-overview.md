---
title: SQL Server コンテナーの高可用性
description: この記事では、SQL Server コンテナーの高可用性について説明します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-2017||>=sql-server-linux-2017||=sqlallproducts-allversions'
ms.openlocfilehash: aa54849c16ea9dfb821404b553b1e9183b61d66a
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2019
ms.locfileid: "68077477"
---
# <a name="high-availability-for-sql-server-containers"></a>SQL Server コンテナーの高可用性

Kubernetes で ネイティブに SQL Server インスタンスを作成して管理します。

SQL Server を [Kubernetes](https://kubernetes.io/) によって管理される docker コンテナーにデプロイします。 Kubernetes では、クラスター ノードで障害が発生した場合に、SQL Server インスタンスを含むコンテナーを自動的に回復できます。 より堅牢な可用性を実現するには、Kubernetes クラスターのコンテナーで、SQL Server インスタンスを含む SQL Server Always On 可用性グループを構成します。 この記事では 2 つのソリューションを比較します。

## <a name="compare-sql-server-versions-on-kubernetes"></a>Kubernetes 上の SQL Server バージョンの比較

SQL Server 2017 には、Kubernetes にデプロイできる Docker イメージが用意されています。 Kubernetes 永続ボリューム要求 (PVC) を使用してイメージを構成できます。 Kubernetes は、コンテナー内の SQL Server プロセスをモニターします。 プロセス、ポッド、コンテナー、またはノードで障害が発生した場合、Kubernetes は自動的に別のインスタンスをブートストラップし、ストレージに再接続します。

SQL Server 2019 (プレビュー) では、Kubernetes StatefulSet によってさらに堅牢なアーキテクチャが導入されます。 Kubernetes は、SQL Server Always On 可用性グループに参加するコンテナー イメージ内の SQL Server のインスタンスを調整します。 このパターンによって、向上した正常性モニター、迅速な回復、オフロード バックアップ、および読み取りスケールアウトが提供されます。  

## <a name="container-with-sql-server-instance-on-kubernetes"></a>Kubernetes 上の SQL Server インスタンスを含むコンテナー

Kubernetes 1.6 以降では、"[*ストレージ クラス*](https://kubernetes.io/docs/concepts/storage/storage-classes/)"、"[*永続ボリューム要求*](https://kubernetes.io/docs/concepts/storage/storage-classes/#persistentvolumeclaims)"、および "[*Azure ディスク ボリューム タイプ*](https://github.com/kubernetes/examples/tree/master/staging/volumes/azure_disk)" がサポートされます。 

この構成では、Kubernetes はコンテナー オーケストレーターの役割を果たします。 

![Kubernetes SQL Server クラスターの図](media/tutorial-sql-server-containers-kubernetes/kubernetes-sql.png)

上の図で、`mssql-server` は "[*ポッド*](https://kubernetes.io/docs/concepts/workloads/pods/pod/)" 内の SQL Server インスタンス (コンテナー) です。 [レプリカ セット](https://kubernetes.io/docs/concepts/workloads/controllers/replicaset/)によって、ノード障害が発生した後にポッドが自動的に回復されるようになります。 アプリケーションがサービスに接続します。 このケースでは、サービスは、`mssql-server` の障害が発生した後も変化しない IP アドレスをホストするロードバランサーを表します。

Kubernetes は、クラスター内のリソースを調整します。 SQL Server インスタンス コンテナーをホストしているノードで障害が発生すると、SQL Server インスタンスを含む新しいコンテナーがブートストラップされ、同じ永続ストレージにアタッチされます。

SQL Server 2017 以降では、Kubernetes 上のコンテナーがサポートされます。

Kubernetes にコンテナーを作成するには、「[Kubernetes に SQL Server コンテナーをデプロイする](tutorial-sql-server-containers-kubernetes.md)」をご覧ください。

## <a name="a-sql-server-always-on-availability-group-on-sql-server-containers-in-kubernetes"></a>Kubernetes における SQL Server コンテナーの SQL Server Always On 可用性グループ

SQL Server 2019 では、Kubernetes 内のコンテナーの可用性グループがサポートされます。 可用性グループのために、SQL Server [Kubernetes オペレーター](https://coreos.com/blog/introducing-operators.html)を Kubernetes クラスターにデプロイします。 このオペレーターにより、クラスター内の SQL Server と可用性グループのパッケージ化、デプロイ、管理が支援されます。

![Kubernetes コンテナーの AG](media/tutorial-sql-server-ag-containers-kubernetes/KubernetesCluster.png)

上の図では、4 ノードの Kubernetes クラスターが 3 つのレプリカを持つ可用性グループをホストしています。 ソリューションには、次のコンポーネントが含まれています。

* Kubernetes "[*デプロイ*](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)"。 デプロイには、オペレーターと構成マップが含まれます。 デプロイによって、可用性グループの SQL Server インスタンスをデプロイするために必要なコンテナー イメージ、ソフトウェア、指示が示されます。

* それぞれで [*StatefulSet*](https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/) がホストされる 3 つのノード。 StatefulSet にはポッドが含まれています。 各ポッドの内容:
  * SQL Server のインスタンスを 1 つ実行している SQL Server コンテナー。
  * 可用性グループを管理するスーパーバイザー `mcr.microsoft.com/mssql/ha`。

* 可用性グループに関連する 2 つの [*ConfigMaps*](https://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-configmap/)。 ConfigMaps から提供される情報:
  * オペレーターのデプロイ。
  * 可用性グループです。

 * SQL Server の各インスタンスの永続ボリュームは、データとログ ファイルのストレージを提供します。

さらに、クラスターでは、パスワード、証明書、キー、その他の機密情報のための "[*シークレット*](https://kubernetes.io/docs/concepts/configuration/secret/)" が保管されます。

## <a name="compare-sql-server-high-availability-on-containers-with-and-without-the-availability-group"></a>可用性グループの有無に関してコンテナーでの SQL Server 高可用性を比較する

次の表では、Kubernetes 上のコンテナー内の SQL Server 高可用性機能を可用性グループの有無に関して比較しています。

| |可用性グループあり | スタンドアロン コンテナー インスタンス<br/> 可用性グループなし
|:------|:------|:------
|ノード障害からの自動復旧 | はい | はい
|ポッド障害からの自動復旧 | はい | はい
|高速フェールオーバー |はい |
|SQL Server インスタンス障害からの自動復旧 | はい | 
|データベースの正常性チェック エラーからの自動復旧 | はい | 
|読み取り専用レプリカの提供 | はい |
|セカンダリ レプリカのバックアップ | はい | 
|StatefulSet として実行 | はい | 

1 つの大きな違いは、コンテナー内の単一 SQL Server よりも可用性グループの方が復旧 (またはフェールオーバー) の時間が短縮されるということです。 このように機能が向上しているのは、SQL Server 可用性グループがクラスター内の他のノードにセカンダリ レプリカを保持しているためです。 フェールオーバー時には、セカンダ リレプリカが選択されてプライマリに昇格されます。 サービスに接続しているアプリケーションは、新しいプライマリ レプリカにリダイレクトされます。

可用性グループがない場合、Kubernetes がフェールオーバーを検出すると、コンテナーを作成し、ストレージに接続し、その後、サービスに接続しているアプリケーションが再接続されます。 正確なフェールオーバー時間は、フェールオーバーの場所と検出方法によって異なります。 

一般に、可用性グループのフェールオーバー時間は秒単位で測定されますが、1 つのインスタンスがコンテナーを回復するためのフェールオーバー時間は最長で 10 分になります。

## <a name="next-steps"></a>次の手順

SQL Server コンテナーを Azure Kubernetes Service (AKS) にデプロイするには、次の例を参照してください。

* [Docker コンテナーに SQL Server をデプロイする](sql-server-linux-configure-docker.md)
* [Kubernetes に SQL Server コンテナーをデプロイする](tutorial-sql-server-containers-kubernetes.md)
* [SQL Server のコンテナー用の Always On 可用性グループ](sql-server-ag-kubernetes.md)

