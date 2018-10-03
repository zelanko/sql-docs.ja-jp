---
title: SQL Server のコンテナーの always On 可用性グループ
description: この記事で SQL Server のコンテナーの可用性グループが導入されています
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6df953eed1226e6be62ba694651f3b3244736a5a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47626170"
---
# <a name="always-on-availability-groups-for-sql-server-containers"></a>SQL Server のコンテナーの always On 可用性グループ

SQL Server 2019 では、Kubernetes でコンテナーの可用性グループをサポートしています。 可用性グループには、SQL Server を展開[Kubernetes 演算子](http://coreos.com/blog/introducing-operators.html)Kubernetes クラスターにします。 演算子では、パッケージ、展開、およびクラスター内の可用性グループを管理することができます。

![Kubernetes コンテナーでの AG](media/tutorial-sql-server-ag-containers-kubernetes/KubernetesCluster.png)

上記の図では、4 つのノードの kubernetes クラスターは、3 つのレプリカを可用性グループをホストします。 ソリューションには、次のコンポーネントが含まれています。

* Kubernetes [*展開*](http://kubernetes.io/docs/concepts/workloads/controllers/deployment/)します。 展開には、演算子と構成のマップが含まれています。 これらは、コンテナー イメージ、ソフトウェア、および可用性グループの SQL Server インスタンスをデプロイするために必要な手順を提供します。

* 各ホストの 3 つのノード、 [ *StatefulSet*](http://kubernetes.io/docs/concepts/workloads/controllers/statefulset/)します。 含まれています、StatefulSet、 [*ポッド*](http://kubernetes.io/docs/concepts/workloads/pods/pod-overview/)します。 それぞれのポッドが含まれます。
  * SQL Server の 1 つのインスタンスを実行している SQL Server のコンテナー。
  * 可用性グループのエージェント。 

* 2 つ[ *ConfigMaps* ](http://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-configmap/)可用性グループに関連します。 ConfigMaps に関する情報を提供します。
  * 演算子の配置。
  * 可用性グループです。

 * [*永続ボリューム*](http://kubernetes.io/docs/concepts/storage/persistent-volumes/)記憶域の断片です。 A*永続ボリューム要求*(PVC) は、ユーザーがストレージ要求です。 各コンテナーには、データおよびログ ストレージの PVC 関係します。 Azure Kubernetes Service (AKS) でする[永続ボリューム要求を作成](http://docs.microsoft.com/azure/aks/azure-disks-dynamic-pv)にストレージ クラスに基づく記憶域に自動的にします。


また、クラスターを格納[*シークレット*](http://kubernetes.io/docs/concepts/configuration/secret/)パスワード、証明書、キー、および他の機密情報。

## <a name="deploy-the-availability-group-in-kubernetes"></a>Kubernetes で可用性グループを展開します。

Kubernetes で可用性グループを展開するには。

1. Kubernetes クラスターを作成します。

   可用性グループでは、master の SQL Server と、ノードには少なくとも 3 つのノードを作成します。

1. 演算子をデプロイします。

1. ストレージを構成します。

1. StatefulSet をデプロイします。

   演算子は、StatefulSet をデプロイする手順をリッスンします。 自動的に、3 つの個別のノードに SQL Server のインスタンスを作成し、外部のクラスター マネージャーで、可用性グループを構成します。

1. データベースを作成し、可用性グループに関連付ける

詳細については、次を参照してください。 [Kubernetes での高可用性 SQL Server Always On 可用性グループを構成する](tutorial-sql-server-ag-kubernetes.md)します。

## <a name="sql-server-kubernetes-operator"></a>SQL Server の Kubernetes 演算子

演算子を展開した後は、カスタムの SQL Server リソースを登録します。 演算子を使用して、このリソースをデプロイします。  各リソースは、SQL Server のインスタンスに対応しなどの特定のプロパティが含まれています`sapassword`と`monitoring policy`します。 演算子は、リソースを解析し、Kubernetes StatefulSet をデプロイします。

StatfulSet が含まれます。

* mssql server コンテナー

* mssql-ha-スーパーバイザー コンテナー

演算子、HA supervisor、および SQL Server のコードが呼び出す Docker イメージにパッケージ化`mcr.microsoft.com/mssql/ha`します。 このイメージには、次のバイナリが含まれています。

* `mssql-operator`

    このプロセスは、個別の Kubernetes デプロイとしてデプロイされます。 登録、 [Kubernetes カスタム リソース](http://kubernetes.io/docs/concepts/extend-kubernetes/api-extension/custom-resources/)と呼ばれる`SqlServer`(sqlservers.mssql.microsoft.com)。 このようなリソースの作成中または Kubernetes クラスターで更新をリッスンします。 このようなすべてのイベントの作成または更新プログラムの対応するインスタンスの Kubernetes リソース (たとえば、StatefulSet、または`mssql-server-k8s-init-sql`ジョブ)。

* `mssql-server-k8s-health-agent`

    この web サーバー機能の Kubernetes[存続性のプローブ](http://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-probes/)SQL Server インスタンスの正常性を判断します。 呼び出すことによって、ローカルの SQL Server インスタンスの正常性の監視`sp_server_diagnostics`監視ポリシーの結果を比較するとします。

* `mssql-ha-supervisor`

   Ag の証明書とエンドポイントを保持します。 

* `mssql-server-k8s-ag-agent`
  
    このプロセスは、1 つの SQL Server インスタンス上の可用性グループ レプリカの正常性を監視し、フェールオーバーを実行します。

    リーダーの選定も保持されます。

* `mssql-server-k8s-init-sql`
  
    この Kubernetes[ジョブ](http://kubernetes.io/docs/concepts/workloads/controllers/jobs-run-to-completion/)の desired state configuration を SQL Server インスタンスに適用されます。 Sql Server リソースの作成または更新するたびに、演算子によって、ジョブが作成されます。 カスタムのリソースに対応するターゲットの SQL Server インスタンスが、リソースで説明されている必要な構成を持つようになります。

    たとえば、次の設定のいずれかが必要な場合、それを完了しました。
  * SA パスワードを更新します。
  * エージェントの SQL ログインを作成します。
  * DBM エンドポイントを作成します。

* `mssql-server-k8s-rotate-creds`
  
    この Kubernetes ジョブは、回転の資格情報のタスクを実装します。 SA パスワード、エージェントの SQL ログインのパスワード、DBM の証明書などの更新を要求するには、このジョブを作成します。SA パスワードは、ジョブのパラメーターとして指定されます。 それ以外は自動生成されます。

* `mssql-server-k8s-failover`

   手動フェールオーバーのワークフローを実装する Kubernetes ジョブを指定します。

### <a name="notes"></a>注

AG の構成に関係なく、演算子は、HA supervisor を常にデプロイされます。 Sql Server リソースにすべての可用性グループが表示されない場合、オペレーターはこのコンテナーがデプロイされます。

演算子のイメージのバージョンでは、SQL Server イメージのバージョンと同じです。

## <a name="next-steps"></a>次の手順

> [Kubernetes での SQL Server のコンテナー](tutorial-sql-server-containers-kubernetes.md)
