---
title: "SQL Server on Linux の読み取りのスケールの可用性グループの構成 |Microsoft ドキュメント"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 10/20/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 
ms.workload: Inactive
ms.openlocfilehash: bd3fa34a4fbfe40dfe184f7d5cf0e1f64372c8f2
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="configure-read-scale-availability-group-for-sql-server-on-linux"></a>SQL Server on Linux の読み取りのスケールの可用性グループを構成します。

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

SQL Server on Linux の読み取りのスケールの可用性グループを構成できます。 可用性グループの 2 つのアーキテクチャがあります。 A*高可用性*アーキテクチャでは、クラスター マネージャーを使用して、ビジネス継続性を提供します。 このアーキテクチャでは、読み取りスケール レプリカを含めることもできます。 高可用性アーキテクチャを作成するを参照してください。[構成 Always On 可用性グループの SQL Server on Linux](sql-server-linux-availability-group-configure-ha.md)です。

このドキュメントを作成する方法を説明します、*読み取りスケール*クラスター マネージャーがない可用性グループです。 このアーキテクチャは、のみ読み取り-小数点以下桁数のみを提供します。 高可用性は提供されません。

[!INCLUDE [Create prerequisites](../includes/ss-linux-cluster-availability-group-create-prereq.md)]

## <a name="create-the-availability-group"></a>可用性グループを作成します。

可用性グループを作成します。 Set `CLUSTER_TYPE = NONE`. さらに、各レプリカを設定`FAILOVER_MODE = NONE`です。 分析を実行するか、ワークロードをレポートできますを直接クライアント アプリケーションは、セカンダリ データベースに接続します。 読み取り専用ルーティング リストを作成することもできます。 転送用のプライマリ レプリカへの接続は、ラウンド ロビン形式でルーティング リストから、各セカンダリ レプリカに接続要求を読み取る。

次の TRANSACT-SQL スクリプトを作成、可用性グループ名`ag1`です。 スクリプトは、構成、可用性グループ レプリカと`SEEDING_MODE = AUTOMATIC`です。 この設定は、可用性グループに追加された後に、各セカンダリ サーバーでデータベースを自動的に作成する SQL Server をによりします。 環境内の次のスクリプトを更新します。 置換、`**<node1>**`と`**<node2>**`レプリカをホストする SQL Server インスタンスの名前を持つ値です。 置換、`**<5022>**`ポートのエンドポイント用に設定するとします。 SQL Server のプライマリ レプリカでは、次の TRANSACT-SQL を実行します。

```SQL
CREATE AVAILABILITY GROUP [ag1]
    WITH (CLUSTER_TYPE = NONE)
    FOR REPLICA ON
        N'**<node1>**' WITH (
            ENDPOINT_URL = N'tcp://**<node1>:**<5022>**',
            AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
            FAILOVER_MODE = MANUAL,
            SEEDING_MODE = AUTOMATIC,
                    SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL)
            ),
        N'**<node2>**' WITH ( 
            ENDPOINT_URL = N'tcp://**<node2>**:**<5022>**', 
            AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
            FAILOVER_MODE = MANUAL,
            SEEDING_MODE = AUTOMATIC,
            SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL)
            );
        
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

### <a name="join-secondary-sql-servers-to-the-availability-group"></a>可用性グループにセカンダリ SQL サーバーを参加させる

次の TRANSACT-SQL スクリプトは、という名前の可用性グループにサーバーを参加`ag1`です。 環境内で使用するスクリプトを更新します。 各セカンダリ SQL Server レプリカでは、可用性グループに参加する次の TRANSACT-SQL を実行します。

```SQL
ALTER AVAILABILITY GROUP [ag1] JOIN WITH (CLUSTER_TYPE = NONE);
         
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

[!INCLUDE [Create Post](../includes/ss-linux-cluster-availability-group-create-post.md)]

これは高可用性構成ではなく、高可用性を実現する場合は、ある手順に従って[構成 Always On 可用性グループの SQL Server on Linux](sql-server-linux-availability-group-configure-ha.md)です。 具体的には、可用性グループを作成`CLUSTER_TYPE=WSFC`(Windows) のまたは`CLUSTER_TYPE=EXTERNAL`(Linux) 内およびクラスター マネージャーの Windows での WSFC または Linux のペースのいずれかと統合します。

## <a name="connect-to-read-only-secondary-replicas"></a>読み取り専用のセカンダリ レプリカに接続します。

読み取り専用セカンダリ レプリカに接続する 2 つの方法ができます。 アプリケーションが、セカンダリ レプリカをホストする SQL Server インスタンスに直接接続して、データベースのクエリ実行または、読み取り専用ルーティングを使用できるようにします。 読み取り専用ルーティングには、リスナーが必要です。

[読み取り可能なセカンダリ レプリカ](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)

[読み取り専用ルーティング](../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md#ConnectToSecondary)

## <a name="fail-over-primary-replica-on-read-scale-availability-group"></a>読み取りのスケールの可用性グループ上のプライマリ レプリカのフェールオーバーします。

[!INCLUDE[Force Failover](../includes/ss-force-failover-read-scale-out.md)]

## <a name="next-steps"></a>次の手順

[分散型可用性グループを構成する](..\database-engine\availability-groups\windows\distributed-availability-groups-always-on-availability-groups.md)

[可用性グループの詳細を表示します](..\database-engine\availability-groups\windows\overview-of-always-on-availability-groups-sql-server.md)

[強制手動フェールオーバーを実行](../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)です。

