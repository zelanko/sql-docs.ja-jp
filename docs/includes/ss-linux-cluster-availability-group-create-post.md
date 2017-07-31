
## <a name="add-a-database-to-the-availability-group"></a>データベースを可用性グループに追加します。

可用性グループに追加するデータベースは、完全復旧モードではあり、有効なログ バックアップを確認します。 テスト データベースまたは作成された新しいデータベースの場合は、データベース バックアップを実行します。 プライマリ SQL サーバーで実行を作成し、という名前のデータベースをバックアップの次の TRANSACT-SQL`db1`です。

```Transact-SQL
CREATE DATABASE [db1];
ALTER DATABASE [db1] SET RECOVERY FULL;
BACKUP DATABASE [db1] 
   TO DISK = N'/var/opt/mssql/data/db1.bak';
```

SQL Server のプライマリ レプリカで実行をという名前のデータベースを追加する次の TRANSACT-SQL`db1`を可用性グループと呼ばれる`ag1`です。

```Transact-SQL
ALTER AVAILABILITY GROUP [ag1] ADD DATABASE [db1];
```

### <a name="verify-that-the-database-is-created-on-the-secondary-servers"></a>セカンダリ サーバー上のデータベースが作成されたことを確認してください。

各セカンダリ SQL Server レプリカでかどうかを次のクエリを実行、`db1`データベースが作成されが同期されています。

```Transact-SQL
SELECT * FROM sys.databases WHERE name = 'db1';
GO
SELECT DB_NAME(database_id) AS 'database', synchronization_state_desc FROM sys.dm_hadr_database_replica_states;
```
