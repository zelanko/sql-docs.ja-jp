---
ms.openlocfilehash: 0cdc343bf4ea6866d1a55672187451a3b6d95ec1
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2019
ms.locfileid: "68215571"
---

## <a name="add-a-database-to-the-availability-group"></a>可用性グループにデータベースを追加する

可用性グループに追加するデータベースが、完全回復モードであり、有効なログ バックアップがあることを確認します。 テスト データベースまたは新しく作成されたデータベースの場合は、データベース バックアップを実行します。 プライマリ SQL Server で、次の Transact-SQL スクリプトを実行し、`db1` という名前のデータベースを作成してバックアップします。

```sql
CREATE DATABASE [db1];
ALTER DATABASE [db1] SET RECOVERY FULL;
BACKUP DATABASE [db1] 
   TO DISK = N'/var/opt/mssql/data/db1.bak';
```

プライマリ SQL Server レプリカで、次の Transact-SQL スクリプトを実行して、`db1` という名前のデータベースを `ag1` という名前の可用性グループに追加します。

```sql
ALTER AVAILABILITY GROUP [ag1] ADD DATABASE [db1];
```

### <a name="verify-that-the-database-is-created-on-the-secondary-servers"></a>セカンダリ サーバーにデータベースが作成されたことを確認する

各セカンダリ SQL Server レプリカで次のクエリを実行して、`db1` データベースが作成されて同期されているかどうかを確認します。

```sql
SELECT * FROM sys.databases WHERE name = 'db1';
GO
SELECT DB_NAME(database_id) AS 'database', synchronization_state_desc FROM sys.dm_hadr_database_replica_states;
```
