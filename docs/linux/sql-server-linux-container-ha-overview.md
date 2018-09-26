---
title: SQL Server のコンテナーの高可用性
description: この記事で SQL Server のコンテナーの高可用性が導入されています
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>=sql-server-2017||>=sql-server-linux-2017||=sqlallproducts-allversions'
ms.openlocfilehash: 13c48bf8b5edefbfd86855197128abfd5674067e
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2018
ms.locfileid: "46715162"
---
# <a name="high-availability-for-sql-server-containers"></a>SQL Server のコンテナーの高可用性

作成し、Kubernetes でネイティブに、SQL Server インスタンスを管理します。

SQL サーバーによって管理される docker コンテナーをデプロイ[Kubernetes](https://kubernetes.io/)します。 Kubernetes では、SQL Server インスタンスを使用して、コンテナーをクラスター ノードが失敗した場合に自動的に回復できます。 堅牢な可用性を実現するには、Kubernetes クラスター上のコンテナー内の SQL Server インスタンスで SQL Server Always On 可用性グループを構成します。 この記事では、2 つのソリューションと比較します。

## <a name="compare-sql-server-versions-on-kubernetes"></a>Kubernetes での SQL Server バージョンを比較します。

SQL Server 2017 では、Kubernetes にデプロイできる Docker イメージを提供します。 Kubernetes 永続ボリューム要求 (PVC) には、イメージを構成できます。 Kubernetes では、コンテナー内の SQL Server プロセスを監視します。 プロセス、ポッド、コンテナー、またはノードが失敗した場合、Kubernetes に自動的に別のインスタンスをブートス トラップに再接続して、記憶域。

SQL Server 2019 には、Kubernetes StatefulSet のより堅牢な archicture が導入されています。 これにより、SQL Server Always On 可用性グループに参加できるコンテナー イメージ内の SQL Server のインスタンスを調整するための Kubernetes です。 強化された正常性の監視、高速回復を提供し、バックアップをオフロード読み取りスケールこのできます。  

## <a name="container-with-sql-server-instance-on-kubernetes"></a>Kubernetes 上の SQL Server インスタンスのコンテナー

Kubernetes バージョン 1.6 およびそれ以降はサポートしています[*ストレージ クラス*](http://kubernetes.io/docs/concepts/storage/storage-classes/)、 [*永続ボリューム要求*](http://kubernetes.io/docs/concepts/storage/storage-classes/#persistentvolumeclaims)、および[ *Azure のディスク ボリュームの種類*](https://github.com/kubernetes/examples/tree/master/staging/volumes/azure_disk)します。 

この構成では、Kubernetes は、コンテナー オーケストレーターの役割を果たします。 

![SQL Server の Kubernetes クラスターの図](media/tutorial-sql-server-containers-kubernetes/kubernetes-sql.png)

前の図では、`mssql-server`には SQL Server インスタンス (コンテナー)、 [*ポッド*](http://kubernetes.io/docs/concepts/workloads/pods/pod/)します。 A[レプリカ セット](http://kubernetes.io/docs/concepts/workloads/controllers/replicaset/)ポッドがノード障害の後に自動的に復旧ことにより、します。 アプリケーションは、サービスに接続します。 この場合、サービスが障害の後に同じままの IP アドレスをホストするロード バランサーを表します、`mssql-server`します。

Kubernetes では、クラスター内のリソースを調整します。 ポッドまたはコンテナー内の SQL Server インスタンスをホストするノードが失敗した場合、オーケストレーターは、SQL Server インスタンスでの同じポッド内のコンテナーをブートス トラップし、同じ永続的ストレージに結び付けます。

SQL Server 2017 と Kubernetes 上のそれ以降のサポート コンテナー。

Kubernetes でコンテナーを作成するを参照してください[Kubernetes での SQL Server のコンテナーのデプロイ。](tutorial-sql-server-containers-kubernetes.md)

## <a name="a-sql-server-always-on-availability-group-on-sql-server-containers-in-kubernetes"></a>Kubernetes での SQL Server コンテナー上の SQL Server Always On 可用性グループ

SQL Server 2019 では、Kubernetes でコンテナーの可用性グループをサポートしています。 可用性グループには、SQL Server を展開[Kubernetes 演算子](http://coreos.com/blog/introducing-operators.html)Kubernetes クラスターにします。 演算子では、パッケージ、展開、および SQL Server インスタンスとクラスター内の可用性グループを管理することができます。

![Kubernetes コンテナーでの AG](media/tutorial-sql-server-ag-containers-kubernetes/KubernetesCluster.png)

上記の図では、4 つのノードの kubernetes クラスターは、3 つのレプリカを可用性グループをホストします。 ソリューションには、次のコンポーネントが含まれています。

* Kubernetes [*展開*](http://kubernetes.io/docs/concepts/workloads/controllers/deployment/)します。 展開には、演算子と構成のマップが含まれています。 これらは、コンテナー イメージ、ソフトウェア、および可用性グループの SQL Server インスタンスをデプロイするために必要な手順を提供します。

* 各ホストの 3 つのノード、 [ *StatefulSet*](http://kubernetes.io/docs/concepts/workloads/controllers/statefulset/)します。 StatefulSet には、ポッドが含まれています。 それぞれのポッドが含まれます。
  * SQL Server の 1 つのインスタンスを実行している SQL Server のコンテナー。
  * スーパーバイザー`mcr.microsoft.com/mssql/ha`可用性グループを管理します。

* 2 つ[ *ConfigMaps* ](http://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-configmap/)可用性グループに関連します。 ConfigMaps に関する情報を提供します。
  * 演算子の配置。
  * 可用性グループです。

 * SQL Server の各インスタンスの永続ボリュームは、データとログ ファイルの記憶域を提供します。

また、クラスターを格納[*シークレット*](http://kubernetes.io/docs/concepts/configuration/secret/)パスワード、証明書、キー、および他の機密情報。

## <a name="compare-sql-server-high-availabiltiy-on-containers-with-and-without-the-availability-group"></a>SQL Server の高可用性と可用性グループなしのコンテナーの比較します。

次のようにテーブル compairs Kubernetes でコンテナーの場合とない場合の可用性グループで SQL Server の高可用性の機能:

| |可用性グループで | スタンドアロンのコンテナー インスタンス<br/> 可用性グループなし
|:------|:------|:------
|ノードの障害から自動的に回復します。 | はい | はい
|ポッドの障害から自動的に回復します。 | はい | はい
|高速フェールオーバー |はい |
|SQL Server インスタンスの障害から自動的に回復します。 | はい | 
|データベースの正常性チェックのエラーから自動的に回復します。 | はい | 
|読み取り専用レプリカを指定します。 | はい |
|セカンダリ レプリカのバックアップ | はい | 
|StatefulSet に従って実行されます。 | はい | 

1 つの主な違いは、recovery (またはフェールオーバー) の時間がよりも、コンテナー内の SQL Server の 1 つのインスタンスに可用性グループで高速なことです。 これは、SQL Server 可用性グループがクラスター内の他のノードで、可用性グループのデータベースのセカンダリ レプリカを保持しているためです。 フェールオーバー時は、セカンダリ レプリカが選択され、プライマリに昇格します。 サービスに接続されているアプリケーションは、新しいプライマリ レプリカにリダイレクトされます。 

可用性グループ、コンテナーを作成、ストレージに接続する必要がある Kubernetes では、フェールオーバーを検出するとサービスに接続されているアプリケーションの再接続し。 フェールオーバーの正確な時間が、フェールオーバーであると検出された方法によって異なります。 

一般に、可用性グループのフェールオーバー時間は、最大 10 分間は、コンテナーを復旧する単一のインスタンスに対してフェールオーバー時間 (秒単位) で計測されます。

## <a name="next-steps"></a>次の手順

Azure Kubernetes Service (AKS) での SQL Server コンテナーを展開するには、これらのチュートリアルのいずれかの手順に従います。

* [Docker コンテナーでの SQL Server をデプロイします。](sql-server-linux-configure-docker.md)
* [Kubernetes での SQL Server のコンテナーをデプロイします。](tutorial-sql-server-containers-kubernetes.md)
* [SQL Server Always On 可用性グループを Kubernetes のデプロイします。](tutorial-sql-server-ag-kubernetes.md)

