---
title: Kubernetes クラスター上の SQL Server Always On 可用性グループに接続します。
description: この記事は、Always On 可用性グループに接続する方法を説明します
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6092f15fe64c96ed004d352408ae6cdac034def9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47852160"
---
# <a name="connect-to-a-sql-server-always-on-availability-group-on-kubernetes"></a>SQL Server Always On Kubernetes 上の可用性グループへの接続します。

Kubernetes クラスター上のコンテナー内の SQL Server インスタンスに接続するには、作成、[ロード バランサー サービス](http://kubernetes.io/docs/concepts/services-networking/service/#loadbalancer)します。 ロード バランサーは、SQL Server インスタンスを実行して、ポッドに IP アドレスの要求を転送します。

可用性グループ レプリカに接続するには、別のレプリカの種類のサービスを作成します。 内のレプリカのさまざまな種類のサービスの例を参照できます[sql server のサンプル](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/ag-services.yaml)します。

* `ag1-primary` プライマリ レプリカへのポインター。
* `ag1-secondary-sync` 同期セカンダリ レプリカへのポインター。
* `ag1-secondary-async` 非同期のセカンダリ レプリカへのポインター。

同じ型の 1 つ以上のセカンダリ レプリカが存在する場合は、Kubernetes は、ラウンド ロビン方式で異なるレプリカに接続をルーティングします。

## <a name="create-a-load-balancer-service"></a>ロード バランサーのサービスを作成します。

プライマリ レプリカのロード バランサーのサービスを作成するには、コピー`ag1-primary.yaml`から[sql server のサンプル]()可用性グループを更新します。

次のコマンドでは、クラスターに .yaml ファイルが適用されます。

```kubectl
kubectl apply -f ag1-primary.yaml
```

## <a name="get-the-ip-address-for-your-load-balancer-service"></a>ロード バランサーのサービスの IP アドレスを取得します。

ロード バランサーのサービスのロード バランサーの IP アドレスを取得するには、次のように実行します。

```kubectl
kubectl get services
```

接続するサービスの IP アドレスを特定します。

## <a name="connect-to-primary-replica"></a>プライマリ レプリカに接続します。

SQL 認証を使用してプライマリ レプリカに接続するには、使用、`sa`アカウントの値は、`sapassword`から作成したシークレットとこの IP アドレス。

以下に例を示します。

```cmd
sqlcmd -S <0.0.0.0> -U sa -P "<MyC0m9l&xP@ssw0rd>"
```

## <a name="next-steps"></a>次の手順

[Kubernetes クラスター上の SQL Server 可用性グループを管理します。](sql-server-linux-kubernetes-manage.md)

[Kubernetes クラスター上の SQL Server 可用性グループ](sql-server-ag-kubernetes.md)
