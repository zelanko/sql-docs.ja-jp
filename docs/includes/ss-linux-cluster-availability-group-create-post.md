
## <a name="add-a-database-to-the-availability-group"></a>可用性グループにデータベースを追加する

可用性グループに追加するデータベースが、完全回復モードであり、有効なログ バックアップがあることを確認します。 テスト データベースまたは新規作成データベースの場合は、データベース バックアップを実行します。 プライマリ SQL Server で、次の Transact-SQL を実行して、`db1` という名前のデータベースを作成してバックアップします。

```Transact-SQL
CREATE DATABASE [db1];
ALTER DATABASE [db1] SET RECOVERY FULL;
BACKUP DATABASE [db1] 
   TO DISK = N'/var/opt/mssql/data/db1.bak';
```

SQL Server のプライマリ レプリカで、次の Transact-SQL を実行して、`db1` という名前のデータベースを `ag1` という名前の可用性グループに追加します。

```Transact-SQL
ALTER AVAILABILITY GROUP [ag1] ADD DATABASE [db1];
```

### <a name="verify-that-the-database-is-created-on-the-secondary-servers"></a>セカンダリ サーバーにデータベースが作成されたことを確認する

各セカンダリ SQL Server レプリカで次のクエリを実行して、`db1` データベースが作成されて同期されているかどうかを確認します。

```Transact-SQL
SELECT * FROM sys.databases WHERE name = 'db1';
GO
SELECT DB_NAME(database_id) AS 'database', synchronization_state_desc FROM sys.dm_hadr_database_replica_states;
```
