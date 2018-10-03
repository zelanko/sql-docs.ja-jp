---
title: Linux 上の読み取りスケールの SQL Server 可用性グループの構成 |Microsoft Docs
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 02/14/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: ''
ms.openlocfilehash: bbacb8630acf10b5c9d20c50ad40cfba3f036a7c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47677462"
---
# <a name="configure-a-sql-server-availability-group-for-read-scale-on-linux"></a>Linux 上の読み取りスケールの SQL Server 可用性グループの構成します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Linux で、SQL Server 常にで可用性グループ (AG) の読み取りスケール ワークロードを構成できます。 AG には 2 種類のアーキテクチャがあります。 高可用性のアーキテクチャでは、クラスター マネージャーを使用して、改善されたビジネス継続性を提供します。 このアーキテクチャは、読み取りスケール レプリカも含めることができます。 高可用性アーキテクチャを作成するを参照してください。[を構成する SQL Server Always On 可用性グループの Linux での高可用性](sql-server-linux-availability-group-configure-ha.md)します。 その他のアーキテクチャでは、読み取りスケール ワークロードのみをサポートします。 この記事では、読み取りスケール ワークロードの場合で、クラスター マネージャーがない AG を作成する方法について説明します。 このアーキテクチャは、読み取りスケールのみを提供します。 高可用性は提供されません。

>[!NOTE]
>`CLUSTER_TYPE = NONE` による可用性グループには、さまざまなオペレーティング システム プラットフォームでホストされているレプリカを含めることができます。 高可用性はサポートできません。 

[!INCLUDE [Create prerequisites](../includes/ss-linux-cluster-availability-group-create-prereq.md)]

## <a name="create-the-ag"></a>AG を作成する

AG を作成します。 `CLUSTER_TYPE = NONE` を設定します。 さらに、`FAILOVER_MODE = MANUAL` で各レプリカを設定します。 分析やレポートのワークロードを実行するクライアント アプリケーションは、セカンダリ データベースに直接接続できます。 また、読み取り専用ルーティング リストを作成できます。 プライマリ レプリカへの接続によって、ルーティング リストに基づき、ラウンドロビン方式で各セカンダリ レプリカに読み取り接続要求を転送します。

次の Transact-SQL スクリプトによって `ag1` という名前の AG が作成されます。 このスクリプトでは、`SEEDING_MODE = AUTOMATIC` で AG レプリカが構成されます。 この設定によって、SQL Server は AG にセカンダリ サーバーが追加されるたびに、そのセカンダリ サーバーでデータベースを自動作成します。 ご利用の環境に合わせて次のスクリプトを変更してください。 `<node1>` 値と `<node2>` 値を、レプリカをホストする SQL Server インスタンスの名前に置き換えます。 `<5022>` 値を、エンドポイントに設定したポートに置き換えます。 プライマリ SQL Server レプリカで次の Transact-SQL スクリプトを実行します。

```SQL
CREATE AVAILABILITY GROUP [ag1]
    WITH (CLUSTER_TYPE = NONE)
    FOR REPLICA ON
        N'<node1>' WITH (
            ENDPOINT_URL = N'tcp://<node1>:<5022>',
            AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
            FAILOVER_MODE = MANUAL,
            SEEDING_MODE = AUTOMATIC,
                    SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL)
            ),
        N'<node2>' WITH ( 
            ENDPOINT_URL = N'tcp://<node2>:<5022>', 
            AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
            FAILOVER_MODE = MANUAL,
            SEEDING_MODE = AUTOMATIC,
            SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL)
            );
        
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

### <a name="join-secondary-sql-servers-to-the-ag"></a>セカンダリ SQL Server を AG に参加させる

次の Transact-SQL スクリプトにより、`ag1` という名前の AG にサーバーが参加します。 ご利用の環境に合わせてスクリプトを変更してください。 各セカンダリ SQL Server レプリカで次の Transact-SQL スクリプトを実行し、AG に参加させます。

```SQL
ALTER AVAILABILITY GROUP [ag1] JOIN WITH (CLUSTER_TYPE = NONE);
         
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

[!INCLUDE [Create post](../includes/ss-linux-cluster-availability-group-create-post.md)]

この AG は高可用性構成ではありません。 高可用性を必要がある場合は」の手順に従ってください[Linux 上の SQL Server の Always On 可用性グループを構成する](sql-server-linux-availability-group-configure-ha.md)します。 含む AG を具体的には、作成`CLUSTER_TYPE=WSFC`(Windows) でまたは`CLUSTER_TYPE=EXTERNAL`(Linux) にします。 クラスタ リング Windows または Linux 上の Pacemaker をいずれかの Windows Server フェールオーバーを使用して、クラスター マネージャーと統合します。

## <a name="connect-to-read-only-secondary-replicas"></a>読み取り専用セカンダリ レプリカに接続する

読み取り専用セカンダリ レプリカには 2 つの方法で接続できます。 アプリケーションは、セカンダリ レプリカをホストする SQL Server インスタンスに直接接続し、データベースにクエリを実行できます。 リスナーを要求する読み取り専用ルーティングも利用できます。

* [読み取り可能なセカンダリ レプリカ](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)
* [読み取り専用ルーティング](../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md#ConnectToSecondary)

## <a name="fail-over-the-primary-replica-on-a-read-scale-availability-group"></a>読み取りスケール可用性グループのプライマリ レプリカをフェールオーバーする

[!INCLUDE[Force failover](../includes/ss-force-failover-read-scale-out.md)]

## <a name="next-steps"></a>次の手順

* [分散型可用性グループを構成する](..\database-engine\availability-groups\windows\distributed-availability-groups-always-on-availability-groups.md)
* [可用性グループの詳細](..\database-engine\availability-groups\windows\overview-of-always-on-availability-groups-sql-server.md)
* [強制手動フェールオーバーの実行](../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)

