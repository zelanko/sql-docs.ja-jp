各可用性グループにはプライマリ レプリカが 1 つだけあります。 プライマリ レプリカは読み書きができます。 プライマリになっているレプリカの変更は、フェールオーバーで行うことができます。 高可用性の可用性グループでは、クラスター マネージャーによってフェールオーバー プロセスが自動化されます。 読み取りスケール可用性グループでは、フェールオーバー プロセスは手動です。 読み取りスケール可用性グループのプライマリ レプリカをフェールオーバーするには、2 つの方法があります。

- データ損失のある強制的な手動フェールオーバー

- データ損失のない手動フェールオーバー

### <a name="forced-fail-over-with-data-loss"></a>データ損失のある強制的なフェールオーバー

プライマリ レプリカを使うことができず、復旧できない場合は、この方法を使います。 

データ損失のあるフェールオーバーを強制的に行うには、ターゲット セカンダリ レプリカをホストしている SQL インスタンスに接続して、以下を実行します。

```SQL
ALTER AVAILABILITY GROUP [ag1] FORCE_FAILOVER_ALLOW_DATA_LOSS;
```

### <a name="manual-fail-over-without-data-loss"></a>データ損失のない手動フェールオーバー

プライマリ レプリカを使うことができても、一時的または完全に構成を変更し、プライマリ レプリカをホストする SQL Server インスタンスを変更する必要がある場合は、この方法を使います。 手動フェールオーバーを実行する前に、データ損失の可能性がないように、ターゲット セカンダリ レプリカが最新の状態であることを確認します。 

以下の手順では、データを失わずに手動でフェールオーバーを行う方法について説明します。

1. ターゲット セカンダリ レプリカを同期コミットにします。

   ```SQL
   ALTER AVAILABILITY GROUP [ag1] 
        MODIFY REPLICA ON N'**<node2>*' 
        WITH (AVAILABILITY_MODE = SYNCHRONOUS_COMMIT);
   ```

1. 次のクエリを実行して、アクティブなトランザクションが、プライマリ レプリカと少なくとも 1 つの同期セカンダリ レプリカにコミットされていることを確認します。 

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

1. `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` を 1 に更新します。

   次の例のスクリプトは、`ag1` という名前の可用性グループで `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` を 1 に設定します。 実行する前に、`ag1` を実際の可用性グループの名前に置き換えます。

   ```SQL
   ALTER AVAILABILITY GROUP [ag1] 
        SET REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT = 1;
   ```

   この設定により、すべてのアクティブなトランザクションが、プライマリ レプリカと少なくとも 1 つの同期セカンダリにコミットされます。 

1. プライマリ レプリカをセカンダリ レプリカに降格させます。 降格された後のプライマリ レプリカは読み取り専用になります。 プライマリ レプリカをホストしている SQL インスタンスで次のコマンドを実行して、ロールを SECONDARY に更新します。

   ```SQL
   ALTER AVAILABILITY GROUP [ag1] 
        SET (ROLE = SECONDARY); 
   ```

1. ターゲット セカンダリ レプリカをプライマリに昇格させます。 

   ```SQL
   ALTER AVAILABILITY GROUP ag1 FORCE_FAILOVER_ALLOW_DATA_LOSS; 
   ```  

   > [!NOTE] 
   > 可用性グループを削除するには、[DROP AVAILABILITY GROUP](https://docs.microsoft.com/en-us/sql/t-sql/statements/drop-availability-group-transact-sql) を使います。 CLUSTER_TYPE NONE または EXTERNAL で作成された可用性グループでは、可用性グループに含まれるすべてのレプリカでコマンドを実行する必要があります。