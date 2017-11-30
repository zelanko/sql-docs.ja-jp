
## <a name="add-a-database-to-the-availability-group"></a>可用性グループにデータベースを追加する

可用性グループに追加するデータベースが完全復旧モードでは、され、有効なログ バックアップを持つことを確認します。 テスト データベース、または新しく作成されたデータベースの場合は、データベース バックアップを実行します。 プライマリ SQL Server で次の TRANSACT-SQL スクリプトを作成し、という名前のデータベースをバックアップを実行`db1`:

```Transact-SQL
CREATE DATABASE [db1];
ALTER DATABASE [db1] SET RECOVERY FULL;
BACKUP DATABASE [db1] 
   TO DISK = N'/var/opt/mssql/data/db1.bak';
```

SQL Server のプライマリ レプリカでという名前のデータベースを追加する次の TRANSACT-SQL スクリプトを実行`db1`を可用性グループと呼ばれる`ag1`:

```Transact-SQL
ALTER AVAILABILITY GROUP [ag1] ADD DATABASE [db1];
```

### <a name="verify-that-the-database-is-created-on-the-secondary-servers"></a>セカンダリ サーバーにデータベースが作成されたことを確認する

各セカンダリ SQL Server レプリカでかどうかを次のクエリを実行、`db1`データベースが作成されが同期されています。

```Transact-SQL
SELECT * FROM sys.databases WHERE name = 'db1';
GO
SELECT DB_NAME(database_id) AS 'database', synchronization_state_desc FROM sys.dm_hadr_database_replica_states;
```
