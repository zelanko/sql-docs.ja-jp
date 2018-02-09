---
title: "SQL Server 可用性グループのフェールオーバーを強制します。"
description: "NONE のクラスターの種類を含む可用性グループの強制フェールオーバーを実行する."
services: 
author: MikeRayMSFT
ms.service: 
ms.topic: include
ms.date: 02/05/2018
ms.author: mikeray
ms.custom: include file
ms.openlocfilehash: 10a2af2cb5bc9e98605a3ee988439e3c3be60c1e
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
各可用性グループは、プライマリ レプリカが 1 つだけです。 プライマリ レプリカは読み書きができます。 レプリカがプライマリを変更するには、フェールオーバーすることができます。 高可用性の可用性グループは、クラスター マネージャーは、フェールオーバー プロセスを自動化します。 NONE 型のクラスターと可用性グループは、フェールオーバー プロセスは手動です。 

クラスターのタイプ NONE、AG のプライマリ レプリカのフェールオーバーに 2 つの方法があります。

- データの損失の強制手動フェールオーバー
- データを失わずに手動フェールオーバー

### <a name="forced-manual-failover-with-data-loss"></a>データの損失の強制手動フェールオーバー

プライマリ レプリカが利用できないと復旧できないときに、このメソッドを使用します。 

タスクを強制するには、データの損失をフェールオーバーするには、実行対象のセカンダリ レプリカをホストする SQL Server インスタンスに接続します。

```SQL
ALTER AVAILABILITY GROUP [ag1] FORCE_FAILOVER_ALLOW_DATA_LOSS;
```

### <a name="manual-failover-without-data-loss"></a>データを失わずに手動フェールオーバー

プライマリ レプリカを使うことができても、一時的または完全に構成を変更し、プライマリ レプリカをホストする SQL Server インスタンスを変更する必要がある場合は、この方法を使います。 手動フェールオーバーを実行する前に、対象のセカンダリ レプリカが最新の状態をデータ損失の可能性を回避することを確認します。 

手動でフェールオーバーするデータ損失なし。

1. 対象のセカンダリ レプリカを行う`SYNCHRONOUS_COMMIT`です。

   ```SQL
   ALTER AVAILABILITY GROUP [ag1] 
        MODIFY REPLICA ON N'<node2>' 
        WITH (AVAILABILITY_MODE = SYNCHRONOUS_COMMIT);
   ```

2. アクティブなトランザクションが、プライマリ レプリカと少なくとも 1 つの同期セカンダリ レプリカにコミットされることを特定する次のクエリを実行します。 

   ```SQL
   SELECT ag.name, 
      drs.database_id, 
      drs.group_id, 
      drs.replica_id, 
      drs.synchronization_state_desc, 
      ag.sequence_number
   FROM sys.dm_hadr_database_replica_states drs, sys.availability_groups ag
   WHERE drs.group_id = ag.group_id; 
   ```

   `synchronization_state_desc` が `SYNCHRONIZED` の場合、セカンダリ レプリカは同期されています。

3. 更新`REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT`を 1 にします。

   次のスクリプト セット`REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT`1 という、AG に`ag1`です。 次のスクリプトを実行する前に置き換える`ag1`可用性グループの名前に置き換えます。

   ```SQL
   ALTER AVAILABILITY GROUP [ag1] 
        SET REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT = 1;
   ```

   この設定により、すべてのアクティブなトランザクションが、プライマリ レプリカと少なくとも 1 つの同期セカンダリ レプリカにコミットされます。 

4. セカンダリ レプリカにプライマリ レプリカを降格します。 プライマリ レプリカを降格した後は読み取り専用です。 このコマンドを実行するロールを更新するプライマリ レプリカをホストする SQL Server インスタンスで`SECONDARY`:

   ```SQL
   ALTER AVAILABILITY GROUP [ag1] 
        SET (ROLE = SECONDARY); 
   ```

5. ターゲット セカンダリ レプリカをプライマリに昇格させます。 

   ```SQL
   ALTER AVAILABILITY GROUP ag1 FORCE_FAILOVER_ALLOW_DATA_LOSS; 
   ```  

   > [!NOTE] 
   > 使用して、可用性グループを削除する[DROP AVAILABILITY GROUP](https://docs.microsoft.com/en-us/sql/t-sql/statements/drop-availability-group-transact-sql)です。 クラスターで作成された、AG の [なし] を入力するか、外部、コマンドである必要があります、可用性グループの一部であるすべてのレプリカで実行します。