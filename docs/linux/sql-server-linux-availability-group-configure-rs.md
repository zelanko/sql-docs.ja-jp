---
title: "SQL Server on Linux の読み取りのスケールの可用性グループを構成する |Microsoft ドキュメント"
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
ms.openlocfilehash: 84fe8851a6ff3ad71e9ad9007bddc8715efc8829
ms.sourcegitcommit: c41e1bf5a53e96855b4424de4e0897153070bb28
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2017
---
# <a name="configure-a-read-scale-availability-group-for-sql-server-on-linux"></a>SQL Server on Linux の読み取りのスケールの可用性グループを構成します。

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

SQL Server on Linux の読み取りのスケールの可用性グループを構成できます。 可用性グループの 2 つのアーキテクチャがあります。 高可用性アーキテクチャでは、クラスター マネージャーを使用して、ビジネス継続性を提供します。 このアーキテクチャは、読み取りスケール レプリカも含めることができます。 高可用性アーキテクチャを作成するを参照してください。 [Linux に SQL Server の AlwaysOn 可用性グループを構成する](sql-server-linux-availability-group-configure-ha.md)です。

このドキュメントでは、クラスター マネージャーがない読み取りスケール可用性グループを作成する方法について説明します。 このアーキテクチャでは、読み取り-小数点以下桁数のみを提供します。 高可用性を実現をしていません。

[!INCLUDE [Create prerequisites](../includes/ss-linux-cluster-availability-group-create-prereq.md)]

## <a name="create-the-availability-group"></a>可用性グループを作成します。

可用性グループを作成します。 Set `CLUSTER_TYPE = NONE`. さらに、各レプリカを設定`FAILOVER_MODE = NONE`です。 分析を実行するか、ワークロードをレポートできますを直接クライアント アプリケーションは、セカンダリ データベースに接続します。 また、読み取り専用ルーティング リストを作成することもできます。 転送用のプライマリ レプリカへの接続は、ラウンド ロビン方式で、ルーティング リストから各セカンダリ レプリカに接続要求を読み取る。

次の TRANSACT-SQL スクリプトは、という名前の可用性グループを作成`ag1`です。 スクリプトは、構成、可用性グループ レプリカと`SEEDING_MODE = AUTOMATIC`です。 この設定は、可用性グループに追加された後に、各セカンダリ サーバーでデータベースを自動的に作成する SQL Server をによりします。 環境内の次のスクリプトを更新します。 置換、`**<node1>**`と`**<node2>**`レプリカをホストする SQL Server インスタンスの名前を持つ値です。 置換、`**<5022>**`エンドポイント用に設定するポートを持つ値です。 SQL Server のプライマリ レプリカでは、次の TRANSACT-SQL スクリプトを実行します。

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

次の TRANSACT-SQL スクリプトは、という名前の可用性グループにサーバーを参加`ag1`です。 環境内で使用するスクリプトを更新します。 各セカンダリ SQL Server レプリカでは、可用性グループに参加する次の TRANSACT-SQL スクリプトを実行します。

```SQL
ALTER AVAILABILITY GROUP [ag1] JOIN WITH (CLUSTER_TYPE = NONE);
         
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

[!INCLUDE [Create post](../includes/ss-linux-cluster-availability-group-create-post.md)]

この可用性グループには、高可用性構成がありません。 高可用性を実現する場合は、ある手順に従って[Linux に SQL Server の AlwaysOn 可用性グループを構成する](sql-server-linux-availability-group-configure-ha.md)です。 具体的には、可用性グループを作成`CLUSTER_TYPE=WSFC`(Windows) にまたは`CLUSTER_TYPE=EXTERNAL`(Linux) にします。 いずれかの Windows Server フェールオーバー クラスタ リング Windows または Linux のペースを使用して、クラスター マネージャーを統合し。

## <a name="connect-to-read-only-secondary-replicas"></a>読み取り専用のセカンダリ レプリカに接続します。

これには読み取り専用のセカンダリ レプリカに接続する 2 つの方法があります。 アプリケーションでは、セカンダリ レプリカをホストする SQL Server インスタンスに直接接続でき、データベースのクエリを実行することができます。 これらもルーティングを使用して読み取り専用、リスナーを作成する必要があります。

* [読み取り可能なセカンダリ レプリカ](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)
* [読み取り専用ルーティング](../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md#ConnectToSecondary)

## <a name="fail-over-the-primary-replica-on-a-read-scale-availability-group"></a>読み取りのスケールの可用性グループで、プライマリ レプリカのフェールオーバーします。

[!INCLUDE[Force failover](../includes/ss-force-failover-read-scale-out.md)]

## <a name="next-steps"></a>次の手順

* [分散型可用性グループを構成します。](..\database-engine\availability-groups\windows\distributed-availability-groups-always-on-availability-groups.md)
* [可用性グループの詳細を表示します](..\database-engine\availability-groups\windows\overview-of-always-on-availability-groups-sql-server.md)
* [強制手動フェールオーバーの実行](../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)

