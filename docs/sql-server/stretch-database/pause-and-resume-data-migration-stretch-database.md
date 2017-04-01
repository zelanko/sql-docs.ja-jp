---
title: "データ移行の一時停止と再開 (Stretch Database) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "06/14/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.service: "sql-server-stretch-database"
ms.suite: ""
ms.technology: 
  - "dbe-stretch"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Stretch Database, 一時停止と再開"
  - "Stretch Database の一時停止"
  - "Stretch Database の再開"
ms.assetid: 65d6a990-b295-41b2-97f9-7b6bf3000e4d
caps.latest.revision: 23
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 23
---
# データ移行の一時停止と再開 (Stretch Database)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Azure へのデータ移行を一時停止または再開するには、SQL Server Management Studio でテーブルに対して **[Stretch]** を選択し、 **[一時停止]** (データの移行を一時停止する場合) または **[再開]** (データの移行を再開する場合) を選択します。 また、Transact-SQL を使用してデータ移行を一時停止または再開することもできます。  
  
 ローカル サーバー上の問題のトラブルシューティングを行う場合やネットワーク帯域幅を最大限に利用する場合は、個々のテーブルに対してデータ移行を一時停止します。  

## データ移行の一時停止  
  
### SQL Server Management Studio を使用してデータ移行を一時停止する  
  
1.  SQL Server Management Studio のオブジェクト エクスプローラーで、データ移行を一時停止する、Stretch が有効なテーブルを選択します。  
  
2.  右クリックして **[ストレッチ]** を選択し、**[一時停止]** を選択します。  
  
### Transact-SQL を使用してデータ移行を一時停止する  
 次のコマンドを実行します。  
  
```tsql  
USE <Stretch-enabled database name>;
GO
ALTER TABLE <Stretch-enabled table name>  
    SET ( REMOTE_DATA_ARCHIVE ( MIGRATION_STATE = PAUSED ) ) ;  
GO 
```  
  
## データ移行の再開  
  
### SQL Server Management Studio を使用してデータ移行を再開する  
  
1.  SQL Server Management Studio のオブジェクト エクスプローラーで、データ移行を再開する、Stretch が有効なテーブルを選択します。  
  
2.  右クリックして **[ストレッチ]** を選択し、**[再開]** を選択します。  
  
### Transact-SQL を使用してデータ移行を再開する  
 次のコマンドを実行します。  
  
```tsql  
USE <Stretch-enabled database name>;
GO
ALTER TABLE <Stretch-enabled table name>   
    SET ( REMOTE_DATA_ARCHIVE ( MIGRATION_STATE = OUTBOUND ) ) ;  
 GO
```  

## 移行がアクティブまたは一時停止かどうかを確認する

### SQL Server Management Studio を使用して、移行がアクティブまたは一時停止かどうかを確認する
SQL Server Management Studio で **Stretch Database モニター**を開き、**移行状態**の列の値を確認します。 詳細については、「[データ移行の監視とトラブルシューティング](../../sql-server/stretch-database/monitor-and-troubleshoot-data-migration-stretch-database.md)」を参照してください。

### TRANSACT-SQL を使用して、移行がアクティブまたは一時停止かどうかを確認する
カタログ ビュー **sys.remote_data_archive_tables** にクエリを実行し、**is_migration_paused** 列の値を確認します。 詳細については、「[sys.remote_data_archive_tables](sys.remote_data_archive_tables%20\(Transact-SQL\).md)」を参照してください。

## 参照  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[データ移行の監視とトラブルシューティング](../../sql-server/stretch-database/monitor-and-troubleshoot-data-migration-stretch-database.md) 
  