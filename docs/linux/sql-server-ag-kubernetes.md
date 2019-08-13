---
title: Linux を実行するコンテナーの Always On 可用性グループ
titleSuffix: SQL Server
description: この記事では、SQL Server コンテナーの可用性グループを紹介します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 3910c74be803b7fc63c8bf560fc637387e06ee15
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2019
ms.locfileid: "67910474"
---
# <a name="always-on-availability-groups-for-sql-server-containers"></a>SQL Server のコンテナー用の Always On 可用性グループ

SQL Server 2019 では、Kubernetes クラスター内のコンテナーの可用性グループがサポートされます。 可用性グループの場合、SQL Server [Kubernetes オペレーター](https://coreos.com/blog/introducing-operators.html)を Kubernetes クラスターに展開します。 このオペレーターにより、クラスターの可用性グループのパッケージ化、展開、管理が支援されます。

![Kubernetes コンテナーの AG](media/tutorial-sql-server-ag-containers-kubernetes/KubernetesCluster.png)

上の図では、4 ノードの Kubernetes クラスターが 3 つのレプリカを持つ可用性グループをホストしています。 ソリューションには、次のコンポーネントが含まれています。

* Kubernetes [*の展開*](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)。 展開には、オペレーターと構成マップが含まれます。 それらにより、可用性グループの SQL Server インスタンスを展開するために必要なコンテナー イメージ、ソフトウェア、指示が与えられます。

* 3 つのノードのそれぞれで [*StatefulSet*](https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/) がホストされます。 StatefulSet には[*ポッド*](https://kubernetes.io/docs/concepts/workloads/pods/pod-overview/)が含まれています。 各ポッドの内容:
  * SQL Server のインスタンスを 1 つ実行している SQL Server コンテナー。
  * 可用性グループのエージェント。 

* 可用性グループに関連する 2 つの [*ConfigMaps*](https://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-configmap/)。 ConfigMaps から提供される情報:
  * オペレーターの展開。
  * 可用性グループです。

 * [*永続ボリューム*](https://kubernetes.io/docs/concepts/storage/persistent-volumes/)はストレージの断片です。 *永続ボリューム要求* (PVC) とは、ユーザーがストレージを要求することです。 データとログのストレージに関して、各コンテナーは PVC に関連付けられます。 Azure Kubernetes Service (AKS) では、[永続ボリューム要求を作成し](https://docs.microsoft.com/azure/aks/azure-disks-dynamic-pv)、ストレージ クラスに基づいて自動的にストレージをプロビジョニングします。


さらに、クラスターでは、パスワード、証明書、キー、その他の機密情報のための[*シークレット*](https://kubernetes.io/docs/concepts/configuration/secret/)が保管されます。

## <a name="deploy-the-availability-group-in-kubernetes"></a>Kubernetes で可用性グループを展開する

Kubernetes で可用性グループを展開するには:

1. Kubernetes クラスターを作成する

   可用性グループの場合、SQL Server に少なくとも 3 つのノードを作成し、マスターに 1 つのノードを作成します。

1. オペレーターを展開する

1. ストレージを構成する

1. StatefulSet を展開する

   オペレーターは、StatefulSet を展開する指示を待ちます。 3 つの別個のノードで SQL Server のインスタンスを自動的に作成し、外部クラスター マネージャーで可用性グループを構成します。

1. データベースを作成し、それを可用性グループにアタッチする

詳細な手順については、「[SQL Server コンテナーの Always On 可用性グループ](sql-server-ag-kubernetes.md)」を参照してください。

## <a name="sql-server-kubernetes-operator"></a>SQL Server Kubernetes オペレーター

オペレーターを展開すると、カスタム SQL Server リソースが登録されます。 オペレーターを使用してこのリソースを展開します。  各リソースは SQL Server のインスタンスに対応し、`sapassword` や `monitoring policy` など、特定のプロパティが含まれています。 オペレーターによってリソースが解析され、Kubernetes StatefulSet が展開されます。

StatfulSet の内容:

* mssql-server コンテナー

* mssql-ha-supervisor コンテナー

オペレーター、HA スーパーバイザー、SQL Server のコードは、`mcr.microsoft.com/mssql/ha` という名称の Docker イメージにパッケージされています。 このイメージには、次のバイナリが含まれています。

* `mssql-operator`

    このプロセスは、別個の Kubernetes 展開として配置されます。 `SqlServer` という名前の [Kubernetes カスタム リソース](https://kubernetes.io/docs/concepts/extend-kubernetes/api-extension/custom-resources/)が登録されます (sqlservers.mssql.microsoft.com)。 その後、これは登録されたリソースが Kubernetes クラスターで作成されるか、更新されるのを待ちます。 そのようなイベントのたびに、対応するインスタンスに対して Kubernetes リソースが作成されるか、更新されます (StatefulSet や `mssql-server-k8s-init-sql` ジョブなど)。

* `mssql-server-k8s-health-agent`

    この Web サーバーは Kubernetes [liveness probe](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-probes/) として機能し、SQL Server インスタンスの正常性を判断します。 `sp_server_diagnostics` を呼び出し、結果とモニター ポリシーを比較することで、ローカル SQL Server の正常性を監視します。

* `mssql-ha-supervisor`

   AG の証明書とエンドポイントを保守管理します。 

* `mssql-server-k8s-ag-agent`
  
    このプロセスにより、1 つの SQL Server インスタンスで AG レプリカの正常性を監視し、フェールオーバーを実行します。

    リーダーの選定も保守管理されます。

* `mssql-server-k8s-init-sql`
  
    この Kubernetes [ジョブ](https://kubernetes.io/docs/concepts/workloads/controllers/jobs-run-to-completion/)により、望まれる状態の構成が SQL Server インスタンスに適用されます。 このジョブは、SqlServer リソースが作成されるか、更新されるたびにオペレーターによって作成されます。 カスタム リソースに対応するターゲット SQL Server インスタンスに、リソースで説明されている望ましい構成が与えられていることが確認されます。

    たとえば、次のいずれかの設定が必要な場合、それを完了します。
  * SA パスワードを更新する
  * エージェントの SQL ログインを作成する
  * DBM エンドポイントを作成する

* `mssql-server-k8s-rotate-creds`
  
    この Kubernetes ジョブにより、資格情報交換タスクが実装されます。 このジョブを作成し、SA パスワード、エージェント SQL ログイン パスワード、DBM 証明書などの更新を要求します。SA パスワードはジョブ パラメーターとして指定されます。 その他は自動生成されます。

* `mssql-server-k8s-failover`

   手動フェールオーバー ワークフローを実装する Kubernetes ジョブ。

### <a name="notes"></a>注

AG の構成に関係なく、オペレーターは常に HA スーパーバイザーを展開します。 SqlServer リソースに AG が記載されていない場合でも、オペレーターによってこのコンテナーが展開されます。

オペレーター イメージのバージョンは SQL Server イメージのバージョンと同じです。

## <a name="next-steps"></a>次の手順

> [Kubernetes の SQL Server コンテナー](tutorial-sql-server-containers-kubernetes.md)
