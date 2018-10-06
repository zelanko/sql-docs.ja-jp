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
ms.openlocfilehash: 7f713ed7dd5d0260df6441698371b33f94813d7e
ms.sourcegitcommit: 4832ae7557a142f361fbf0a4e2d85945dbf8fff6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2018
ms.locfileid: "48251979"
---
# <a name="manage-sql-server-always-on-availability-group-kubernetes"></a>SQL Server Always On 可用性グループの Kubernetes を管理します。

Always On 可用性グループで Kubernetes を管理するには、マニフェストを作成し、クラスターに適用します。 マニフェストは、`.yaml`ファイル。  

この記事の例では、すべての Kubernetes クラスターに適用されます。 これらの例のシナリオは、Azure Kubernetes サービス上のクラスターに対して適用されます。

完全な展開の例を参照してください。 [Always On 可用性グループの SQL Server のコンテナー](sql-server-ag-kubernetes.md)します。

## <a name="fail-over---sql-server-availability-group-on-kubernetes"></a>フェールオーバー - Kubernetes 上の SQL Server 可用性グループ

Kubernetes で別のノードに可用性グループ プライマリ レプリカをフェールオーバーするには、ジョブを使用します。 この記事では、このジョブの環境変数を識別します。

次のマニフェスト ファイルでは、可用性グループを手動でフェールオーバーするジョブについて説明します。 

例では、新しいファイルの内容と呼ばれるコピー`failover.yaml`します。

[failover.yaml](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-deployment-script/templates/failover.yaml)

ジョブをデプロイするには使用`Kubectl`します。

```azurecli
kubectl apply -f failover.yaml
```

マニフェスト ファイルを適用した後、Kubernetes は、ジョブを実行します。 ジョブは、新しいリーダーを選定 supervisor を行い、リーダーの SQL Server インスタンスにプライマリ レプリカを移動します。

ジョブを実行した後は、それを削除します。 Kubernetes でのジョブ オブジェクトは、その状態を表示できるように完了した後が維持されます。 それらの状態を記録した後、古いジョブを手動で削除する必要があります。 ジョブを削除すると、Kubernetes のログも削除されます。 ジョブを削除しない場合、ジョブの名前と、ポッドのセレクターを変更しない限り、今後のフェールオーバー ジョブは失敗します。 詳細については、次を参照してください。 [- ジョブが完了するまで実行](https://kubernetes.io/docs/concepts/workloads/controllers/jobs-run-to-completion/)します。

## <a name="rotate-credentials"></a>資格情報を交換します。

SA と、マスター _ キーを更新する資格情報を交換します。

コピー、[回転 creds.yaml](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-deployment-script)ローカルを使用して、`kubectl`クラスターに適用します。

```azurecli
kubectl apply -f rotate-creds.yaml
```

## <a name="next-steps"></a>次の手順

[Azure Kubernetes Service (AKS) での Kubernetes ダッシュ ボードにアクセスします。](https://docs.microsoft.com/azure/aks/kubernetes-dashboard)

[Kubernetes クラスター上の SQL Server 可用性グループ](sql-server-ag-kubernetes.md)
