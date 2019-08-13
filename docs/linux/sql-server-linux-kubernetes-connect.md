---
title: Kubernetes クラスターの SQL Server Always On 可用性グループに接続する
description: この記事では、Always On 可用性グループに接続する方法について説明します
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: f05bc51f587723414d3b0a4090fe2b27ad5fb837
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2019
ms.locfileid: "67952602"
---
# <a name="connect-to-a-sql-server-always-on-availability-group-on-kubernetes"></a>Kubernetes の SQL Server Always On 可用性グループに接続する

Kubernetes クラスターのコンテナー内の SQL Server インスタンスに接続するには、[ロード バランサー サービス](https://kubernetes.io/docs/concepts/services-networking/service/#loadbalancer)を作成します。 ロード バランサーはエンドポイントです。 IP アドレスを保持し、その IP アドレスの要求を、SQL Server インスタンスを実行しているポッドに転送します。

可用性グループ レプリカに接続するには、さまざまなレプリカの種類のサービスを作成します。 さまざまな種類のレプリカのサービス例については、[sql-server-samples/ag-services.yaml](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/high%20availability/Kubernetes/sample-manifest-files) を参照してください。

* `ag1-primary` はプライマリ レプリカを指します。
* `ag1-secondary` は任意のセカンダリ レプリカを指します。

複数のセカンダリ レプリカがある場合、Kubernetes ではラウンドロビン方式で異なるレプリカに接続をルーティングします。

## <a name="create-a-load-balancer-service"></a>ロード バランサー サービスを作成する

プライマリとレプリカのロード バランサー サービスを作成するには、[sql-server-samples](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-file) から [`ag1-services.yaml`](https://github.com/Microsoft/sql-server-samples/blob/master/samples/features/high%20availability/Kubernetes/sample-manifest-files/ag-services.yaml) をコピーし、可用性グループ用にそれを更新します。

次のコマンドでは、構成を `.yaml` ファイルからクラスターに適用します。

```kubectl
kubectl apply -f ag1-services.yaml --namespace ag1
```

## <a name="get-the-ip-address-for-your-load-balancer-service"></a>ロード バランサー サービスの IP アドレスを取得する

ロード バランサー サービスのロード バランサー IP アドレスを取得するには、以下を実行します。

```kubectl
kubectl get services
```

接続先のサービスの IP アドレスを特定します。

## <a name="connect-to-primary-replica"></a>プライマリ レプリカに接続する

SQL 認証を使用してプライマリ レプリカに接続するには、`sa` アカウント、作成したシークレットの `sapassword` の値、およびこの IP アドレスを使用します。

例:

```cmd
sqlcmd -S <0.0.0.0> -U sa -P "<MyC0m9l&xP@ssw0rd>"
```

## <a name="next-steps"></a>次の手順

[Kubernetes クラスターの SQL Server 可用性グループを管理する](sql-server-linux-kubernetes-manage.md)

[Kubernetes クラスターの SQL Server 可用性グループ](sql-server-ag-kubernetes.md)
