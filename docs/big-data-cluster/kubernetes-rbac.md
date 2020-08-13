---
title: Kubernetes RBAC
titleSuffix: SQL Server big data clusters
description: この記事では、SQL Server ビッグ データ クラスターで RBAC と Kubernetes がどのように使用されるかについて説明します。
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 06/22/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 5d2e3f379402f16f32020f9cd34103919f13a30c
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/21/2020
ms.locfileid: "86552977"
---
# <a name="kubernetes-rbac-model--impact-on-users-managing-bdc"></a>Kubernetes RBAC モデルと BDC を管理するユーザーへの影響

このセクションでは、ビッグ データ クラスターを管理するユーザーに必要なアクセス許可について説明します。

> [!NOTE]
> Kubernetes RBAC モデルのその他のリソースについては、「[Using RBAC Authorization - Kubernetes](https://kubernetes.io/docs/reference/access-authn-authz/rbac/)」 (RBAC 承認の使用 - Kubernetes) と「[Using RBAC to define and apply permissions - OpenShift](https://docs.openshift.com/container-platform/4.4/authentication/using-rbac.html)」 (RBAC を使用してアクセス許可を定義および適用する - OpenShift) を参照してください。

## <a name="role-required-for-deployment"></a>デプロイに必要なロール

BDC では、サービス アカウント (`sa-mssql-controller` や `master` など) を使用して、クラスター ポッド、サービス、高可用性、監視などのプロビジョニングを調整します。BDC のデプロイが開始されると (たとえば、`azdata bdc create`)、`azdata` によって以下が行われます。

1. 指定された名前空間が存在するかどうかが確認されます。
2. 存在しない場合は作成され、`MSSQL_CLUSTER` ラベルが適用されます。
3. `sa-mssql-controller` サービス アカウントが作成されます。
4. クラスター レベルのアクセス許可ではなく、名前空間またはプロジェクトに対する完全なアクセス許可を持つ `<namespaced>-admin` ロールが作成されます。
5. そのロールに対して、そのサービス アカウントのロールの割り当てが作成されます。

これらの手順が完了すると、コントロール プレーン ポッドがプロビジョニングされ、サービス アカウントによって残りのビッグ データ クラスターがデプロイされます。  

そのため、デプロイするユーザーには次のアクセス許可が必要です。

- クラスター内の名前空間を一覧表示する (1)。
- 新規または既存の名前空間にラベルを適用する (2)。
- サービス アカウント `sa-mssql-controller`、`<namespaced>-admin` ロールおよびロール バインディングを作成する (3-5)。

既定の `admin` ロールにはこれらのアクセス許可がないため、ビッグ データ クラスターをデプロイするユーザーには、少なくとも名前空間レベルの管理者アクセス許可が必要です。

## <a name="cluster-role-required-for-pods-and-nodes-metrics-collection"></a>ポッドとノードのメトリック コレクションに必要なクラスターのロール

SQL Server 2019 CU5 以降、ポッドとノードのメトリックを収集するには、Telegraf にクラスター全体のロール アクセス許可を持つサービス アカウントが必要です。 デプロイ (または既存のデプロイのアップグレード) 時に、必要なサービス アカウントとクラスターのロールの作成が試行されます。ただし、クラスターをデプロイしたり、アップグレードを実行したりするユーザーに十分なアクセス許可がない場合でも、デプロイまたはアップグレードは警告は生成されますが続行され、成功します。 この場合、ポッドとノードのメトリックは収集されません。 クラスターをデプロイするユーザーは、(デプロイまたはアップグレードの前または後に) クラスター管理者にロールとサービス アカウントの作成を依頼する必要があります。 それらが作成されると、BDC によって使用されます。 

必要な成果物を作成する方法を示すスクリプトを次に示します。

```console
export CLUSTER_NAME=mssql-cluster
kubectl create -f - <<EOF
---
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRole
metadata:
  name: ${CLUSTER_NAME}:cr-mssql-metricsdc-reader
rules:
- apiGroups:
  - '*'
  resources:
  - pods
  - nodes/stats
  verbs:
  - get
---
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRoleBinding
metadata:
  name: ${CLUSTER_NAME}:crb-mssql-metricsdc-reader
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: ${CLUSTER_NAME}:cr-mssql-metricsdc-reader
subjects:
- kind: ServiceAccount
  name: sa-mssql-metricsdc-reader
  namespace: ${CLUSTER_NAME}
EOF
```

サービス アカウント、クラスター ロール、およびクラスター ロールのバインドは、BDC デプロイの前または後に作成できます。 Kubernetes によって、Telegraf サービス アカウントのアクセス許可が自動的に更新されます。 これらがポッドのデプロイとして作成されている場合、ポッドとノードのメトリックが収集されるまでに数分の遅延が発生します。

> [!NOTE]
> SQL Server 2019 CU5 では、ポッドとノードのメトリックのコレクションを制御する 2 つの機能スイッチが導入されました。 既定では、これらのパラメーターは、既定値がオーバーライドされている OpenShift を除き、すべての環境ターゲットで true に設定されています。 

これらの設定は、`control.json` デプロイ構成ファイルのセキュリティ セクションでカスタマイズできます。

```json
  "security": {
    …
    "allowNodeMetricsCollection": false,
    "allowPodMetricsCollection": false
  }
```

これらの設定が `false` に設定されている場合、BDC デプロイのワークフローでは、サービス アカウント、クラスター ロール、および Telegraf のバインディングの作成が試行されます。
