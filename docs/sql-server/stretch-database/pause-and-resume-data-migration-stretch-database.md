---
title: "データ移行の一時停止と再開 (Stretch Database) | Microsoft Docs"
ms.custom: 
ms.date: 06/14/2016
ms.prod: stretch-database
ms.prod_service: sql-non-specified
ms.service: database-engine
ms.component: 
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-stretch
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Stretch Database, pausing and resuming
- pausing Stretch Database
- resuming Stretch Database
ms.assetid: 65d6a990-b295-41b2-97f9-7b6bf3000e4d
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 0fef9c7f912cb824b3f1fcf8653a82fa99a35561
ms.openlocfilehash: a291fd543d572fc621e7b59e968e7ca69d79552e
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="pause-and-resume-data-migration-stretch-database"></a>データ移行の一時停止と再開 (Stretch Database)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Azure へのデータ移行を一時停止または再開するには、SQL Server Management Studio でテーブルに対して **[Stretch]** を選択し、 **[一時停止]** (データの移行を一時停止する場合) または **[再開]** (データの移行を再開する場合) を選択します。 また、Transact-SQL を使用してデータ移行を一時停止または再開することもできます。  
  
 ローカル サーバー上の問題のトラブルシューティングを行う場合やネットワーク帯域幅を最大限に利用する場合は、個々のテーブルに対してデータ移行を一時停止します。  

## <a name="pause-data-migration"></a>データ移行の一時停止  
  
### <a name="use-sql-server-management-studio-to-pause-data-migration"></a>SQL Server Management Studio を使用してデータ移行を一時停止する  
  
1.  SQL Server Management Studio のオブジェクト エクスプローラーで、データ移行を一時停止する、Stretch が有効なテーブルを選択します。  
  
2.  右クリックして **[ストレッチ]**を選択し、 **[一時停止]**を選択します。  
  
### <a name="use-transact-sql-to-pause-data-migration"></a>Transact-SQL を使用してデータ移行を一時停止する  
 次のコマンドを実行します。  
  
```sql  
USE <Stretch-enabled database name>;
GO
ALTER TABLE <Stretch-enabled table name>  
    SET ( REMOTE_DATA_ARCHIVE ( MIGRATION_STATE = PAUSED ) ) ;  
GO 
```  
  
## <a name="resume-data-migration"></a>データ移行の再開  
  
### <a name="use-sql-server-management-studio-to-resume-data-migration"></a>SQL Server Management Studio を使用してデータ移行を再開する  
  
1.  SQL Server Management Studio のオブジェクト エクスプローラーで、データ移行を再開する、Stretch が有効なテーブルを選択します。  
  
2.  右クリックして **[ストレッチ]**を選択し、 **[再開]**を選択します。  
  
### <a name="use-transact-sql-to-resume-data-migration"></a>Transact-SQL を使用してデータ移行を再開する  
 次のコマンドを実行します。  
  
```sql  
USE <Stretch-enabled database name>;
GO
ALTER TABLE <Stretch-enabled table name>   
    SET ( REMOTE_DATA_ARCHIVE ( MIGRATION_STATE = OUTBOUND ) ) ;  
 GO
```  

## <a name="check-whether-migration-is-active-or-paused"></a>移行がアクティブまたは一時停止かどうかを確認する

### <a name="use-sql-server-management-studio-to-check-whether-migration-is-active-or-paused"></a>SQL Server Management Studio を使用して、移行がアクティブまたは一時停止かどうかを確認する
SQL Server Management Studio で **Stretch Database モニター** を開き、 **移行状態** の列の値を確認します。 詳細については、「 [データ移行の監視とトラブルシューティング](../../sql-server/stretch-database/monitor-and-troubleshoot-data-migration-stretch-database.md)」を参照してください。

### <a name="use-transact-sql-to-check-whether-migration-is-active-or-paused"></a>TRANSACT-SQL を使用して、移行がアクティブまたは一時停止かどうかを確認する
カタログ ビュー **sys.remote_data_archive_tables** にクエリを実行し、 **is_migration_paused** 列の値を確認します。 詳細については、「 [sys.remote_data_archive_tables](../../relational-databases/system-catalog-views/stretch-database-catalog-views-sys-remote-data-archive-tables.md)」を参照してください。

## <a name="see-also"></a>参照  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[データ移行の監視とトラブルシューティング](../../sql-server/stretch-database/monitor-and-troubleshoot-data-migration-stretch-database.md) 
  

