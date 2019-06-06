---
title: Kubernetes クラスター上の SQL Server Always On 可用性グループに接続します。
description: この記事は、Always On 可用性グループに接続する方法を説明します
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 1afe2f33ec49f734e97a24a98d62c17b638e38cf
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66713316"
---
# <a name="connect-to-a-sql-server-always-on-availability-group-on-kubernetes"></a>SQL Server Always On Kubernetes 上の可用性グループへの接続します。

Kubernetes クラスター上のコンテナー内の SQL Server インスタンスに接続するには、作成、[ロード バランサー サービス](https://kubernetes.io/docs/concepts/services-networking/service/#loadbalancer)します。 ロード バランサーは、エンドポイントです。 IP アドレスを保持し、SQL Server インスタンスを実行して、ポッドに IP アドレスに対する要求を転送します。

可用性グループ レプリカに接続するには、別のレプリカの種類のサービスを作成します。 内のレプリカのさまざまな種類のサービスの例を参照できます[sql-サーバー-サンプル/ag-services.yaml](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files)します。

* `ag1-primary` プライマリ レプリカへのポインター。
* `ag1-secondary` 任意のセカンダリ レプリカへのポインター。

数より多い場合、1 つのセカンダリ レプリカは Kubernetes はラウンド ロビン方式で異なるレプリカに接続をルーティングします。

## <a name="create-a-load-balancer-service"></a>ロード バランサーのサービスを作成します。

プライマリとレプリカのロード バランサーのサービスを作成するには、コピー [ `ag1-services.yaml` ](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/ag-services.yaml)から[sql server のサンプル](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-file)可用性グループを更新します。

次のコマンドからの構成の適用、`.yaml`クラスターへのファイル。

```kubectl
kubectl apply -f ag1-services.yaml --namespace ag1
```

## <a name="get-the-ip-address-for-your-load-balancer-service"></a>ロード バランサーのサービスの IP アドレスを取得します。

ロード バランサーのサービスのロード バランサーの IP アドレスを取得するには、次のように実行します。

```kubectl
kubectl get services
```

接続するサービスの IP アドレスを特定します。

## <a name="connect-to-primary-replica"></a>プライマリ レプリカに接続します。

SQL 認証を使用してプライマリ レプリカに接続するには、使用、`sa`アカウントの値は、`sapassword`から作成したシークレットとこの IP アドレス。

例 :

```cmd
sqlcmd -S <0.0.0.0> -U sa -P "<MyC0m9l&xP@ssw0rd>"
```

## <a name="next-steps"></a>次のステップ

[Kubernetes クラスター上の SQL Server 可用性グループを管理します。](sql-server-linux-kubernetes-manage.md)

[Kubernetes クラスター上の SQL Server 可用性グループ](sql-server-ag-kubernetes.md)
