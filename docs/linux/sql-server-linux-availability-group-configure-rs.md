---
title: "SQL Server on Linux の読み取りのスケール アウト可用性グループの構成 |Microsoft ドキュメント"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 06/14/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: cf249ff8e6d2e82d1cf413bdec0272e3796b72cb
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="configure-read-scale-out-availability-group-for-sql-server-on-linux"></a>SQL Server on Linux の読み取りのスケール アウト可用性グループを構成します。

[!INCLUDE[tsql-appliesto-sslinux-only](../../docs/includes/tsql-appliesto-sslinux-only.md)]

Linux に SQL Server の読み取りのスケール アウト可用性グループを構成することができます。 可用性グループの 2 つのアーキテクチャがあります。 A*高可用性*アーキテクチャでは、クラスター マネージャーを使用して、ビジネス継続性を提供します。 このアーキテクチャでは、読み取りのスケール アウト レプリカを含めることもできます。 高可用性アーキテクチャを作成するを参照してください。[構成 Always On 可用性グループの SQL Server on Linux](sql-server-linux-availability-group-configure-ha.md)です。

このドキュメントを作成する方法を説明します、*読み取りのスケール アウト*クラスター マネージャーがない可用性グループです。 このアーキテクチャは、スケール アウトののみ読み取りのみを提供します。 高可用性は提供されません。

[!INCLUDE [Create prerequisites](../includes/ss-linux-cluster-availability-group-create-prereq.md)]

## <a name="create-the-availability-group"></a>可用性グループを作成します。

可用性グループを作成します。 Set `CLUSTER_TYPE = NONE`. さらに、各レプリカを設定`FAILOVER_MODE = NONE`です。 分析を実行するか、ワークロードをレポートできますを直接クライアント アプリケーションは、セカンダリ データベースに接続します。 読み取り専用ルーティング リストを作成することもできます。 転送用のプライマリ レプリカへの接続は、ラウンド ロビン形式でルーティング リストから、各セカンダリ レプリカに接続要求を読み取る。

次の TRANSACT-SQL スクリプトを作成、可用性グループ名`ag1`です。 スクリプトは、構成、可用性グループ レプリカと`SEEDING_MODE = AUTOMATIC`です。 この設定は、可用性グループに追加された後に、各セカンダリ サーバーでデータベースを自動的に作成する SQL Server をによりします。 環境内の次のスクリプトを更新します。 置換、`**<node1>**`と`**<node2>**`レプリカをホストする SQL Server インスタンスの名前を持つ値です。 置換、`**<5022>**`ポートのエンドポイント用に設定するとします。 SQL Server のプライマリ レプリカでは、次の TRANSACT-SQL を実行します。

```Transact-SQL
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

```Transact-SQL
ALTER AVAILABILITY GROUP [ag1] JOIN WITH (CLUSTER_TYPE = NONE);
         
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

[!INCLUDE [Create Post](../includes/ss-linux-cluster-availability-group-create-post.md)]

これは高可用性構成ではなく、高可用性を実現する場合は、ある手順に従って[構成 Always On 可用性グループの SQL Server on Linux](sql-server-linux-availability-group-configure-ha.md)です。 具体的には、可用性グループを作成`CLUSTER_TYPE=WSFC`(Windows) のまたは`CLUSTER_TYPE=EXTERNAL`(Linux) 内およびクラスター マネージャーの Windows での WSFC または Linux のペースのいずれかと統合します。

## <a name="connect-to-read-only-secondary-replicas"></a>読み取り専用のセカンダリ レプリカに接続します。

読み取り専用セカンダリ レプリカに接続する 2 つの方法ができます。 アプリケーションが、セカンダリ レプリカをホストする SQL Server インスタンスに直接接続して、データベースのクエリ実行または、読み取り専用ルーティングを使用できるようにします。 読み取り専用ルーティングには、リスナーが必要です。

[読み取り可能なセカンダリ レプリカ](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)

[読み取り専用ルーティング](../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md#ConnectToSecondary)

## <a name="fail-over-primary-replica-on-read-scale-out-availability-group"></a>読み取りのスケール アウト可用性グループのプライマリ レプリカのフェールオーバーします。

各可用性グループは、1 つだけのプライマリ レプリカを持っています。 プライマリ レプリカは読み取りは許可し、書き込みます。 レプリカがプライマリを変更するには、フェールオーバーを実行できます。 高可用性の可用性グループで、フェールオーバー プロセスで、クラスター マネージャーを自動化します。 読み取りのスケール アウト可用性グループのフェールオーバー プロセスは手動です。 読み取りのスケールの可用性グループのプライマリ レプリカのフェールオーバーに 2 つの方法ができます。

- 経由でデータ損失の手動フェールオーバーを強制

- データを失わずに手動をフェールオーバーします。

### <a name="forced-fail-over-with-data-loss"></a>データ損失の強制フェールオーバー

プライマリ レプリカを使用できないは復旧できない場合は、このメソッドを使用します。 詳細については、強制フェールオーバーでデータ損失が見つかります[の強制手動フェールオーバーを実行](../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)です。

強制的にフェールオーバー データが失われると、対象のセカンダリ レプリカをホストする SQL インスタンスに接続し、実行します。
```Transact-SQL
ALTER AVAILABILITY GROUP [ag1] FORCE_FAILOVER_ALLOW_DATA_LOSS;
```

### <a name="manual-fail-over-without-data-loss"></a>データを失わずに手動をフェールオーバーします。

このメソッド、プライマリ レプリカが、使用可能な場合は一時的または完全構成を変更しをホストする SQL Server インスタンスを変更する必要があります、プライマリ レプリカを使います。 経由で手動の失敗を発行する前にデータ損失の可能性がないように、ターゲット セカンダリ レプリカが最新の状態であることを確認します。 

次の手順では、データを失わずに手動でフェールオーバーする方法について説明します。

1. ターゲット セカンダリ レプリカの同期コミットを確認します。

   ```Transact-SQL
   ALTER AVAILABILITY GROUP [ag1] MODIFY REPLICA ON N'**<node2>*' WITH (AVAILABILITY_MODE = SYNCHRONOUS_COMMIT);
   ```
1. 更新`required_synchronized_secondaries_to_commit`を 1 にします。

   この設定により、すべてのアクティブなトランザクションが、プライマリ レプリカと少なくとも 1 つの同期セカンダリにコミットされます。 可用性グループが、synchronization_state_desc を同期するときにフェールオーバーする準備があり、sequence_number 両方のプライマリと同じ対象のセカンダリ レプリカ。 確認するには、このクエリを実行します。

   ```Transact-SQL
   SELECT ag.name, 
      drs.database_id, 
      drs.group_id, 
      drs.replica_id, 
      drs.synchronization_state_desc, 
      ag.sequence_number
   FROM sys.dm_hadr_database_replica_states drs, sys.availability_groups ag
   WHERE drs.group_id = ag.group_id; 
   ```

1. セカンダリ レプリカにプライマリ レプリカを降格します。 プライマリ レプリカを降格した後は読み取り専用です。 ロールを更新する、セカンダリにプライマリ レプリカをホストしている SQL インスタンスでこのコマンドを実行します。

   ```Transact-SQL
   ALTER AVAILABILITY GROUP [ag1] SET (ROLE = SECONDARY); 
   ```

1. 対象のセカンダリ レプリカをプライマリに昇格します。 

   ```Transact-SQL
   ALTER AVAILABILITY GROUP distributedag FORCE_FAILOVER_ALLOW_DATA_LOSS; 
   ```  

   > [!NOTE] 
   > 可用性グループ使用を削除する[DROP AVAILABILITY GROUP](https://docs.microsoft.com/en-us/sql/t-sql/statements/drop-availability-group-transact-sql)です。 CLUSTER_TYPE NONE または外部で作成された可用性グループで、コマンドにすべてのレプリカが可用性グループの一部で実行するのには。

## <a name="next-steps"></a>次の手順

[分散型可用性グループを構成します。](..\database-engine\availability-groups\windows\distributed-availability-groups-always-on-availability-groups.md)

[可用性グループの詳細を表示します](..\database-engine\availability-groups\windows\overview-of-always-on-availability-groups-sql-server.md)


