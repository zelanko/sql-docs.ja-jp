---
title: "sys.dm_io_virtual_file_stats (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/11/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_io_virtual_file_stats
- sys.dm_io_virtual_file_stats_TSQL
- sys.dm_io_virtual_file_stats
- dm_io_virtual_file_stats_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_io_virtual_file_stats dynamic management function
ms.assetid: fa3e321f-6fe5-45ff-b397-02a0dd3d6b7d
caps.latest.revision: "37"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: deec9ee56fe129b77e130276c22b24c415ddc473
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmiovirtualfilestats-transact-sql"></a>sys.dm_io_virtual_file_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

  データとログ ファイルの I/O 統計を返します。 この動的管理ビューは、 [fn_virtualfilestats](../../relational-databases/system-functions/sys-fn-virtualfilestats-transact-sql.md)関数。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、名前を使用して**sys.dm_pdw_nodes_io_virtual_file_stats**です。 

## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server and Azure SQL Database

sys.dm_io_virtual_file_stats (   
    { database_id | NULL },  
    { file_id | NULL }  
)  
```  

```  
-- Syntax for Azure SQL Data Warehouse

sys.dm_pdw_nodes_io_virtual_file_stats
```
  
## <a name="arguments"></a>引数  


 *database_id* |NULL

 **適用対象:** SQL Server (2008年以降)、Azure SQL Database

 データベースの ID です。 *database_id* int で既定値はありません。 有効な入力値は、データベースの ID 番号または NULL です。 NULL を指定した場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス内のすべてのデータベースが返されます。  
  
 組み込み関数は、 [DB_ID](../../t-sql/functions/db-id-transact-sql.md)を指定できます。  
  
*file_id* |NULL

**適用対象:** SQL Server (2008年以降)、Azure SQL Database
 
ファイルの ID です。 *file_id* int で既定値はありません。 有効な入力値は、ファイルの ID 番号または NULL です。 NULL を指定した場合、データベース上のすべてのファイルが返されます。  
  
 組み込み関数は、 [FILE_IDEX](../../t-sql/functions/file-idex-transact-sql.md)指定できますが、および現在のデータベース内のファイルを参照します。  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**database_name**|**sysname**|データベース名。</br></br>SQL Data Warehouse、これは、pdw_node_id により識別されるノードに格納されているデータベースの名前です。 各ノードは、13 のファイルを持つ 1 つの tempdb データベースを持ちます。 各ノードも配布、あたり 1 つのデータベースあり、各ディストリビューション データベース 5 つのファイルです。 たとえば、各ノードに 4 つのディストリビューションが含まれている場合、結果は、pdw_node_id あたり 20 のディストリビューション データベース ファイルを示しています。 
|**database_id**|**smallint**|データベースの ID。|  
|**file_id**|**smallint**|ファイルの ID。|  
|**sample_ms**|**bigint**|コンピューターの起動後に経過した時間 (ミリ秒単位)。 この列は、この関数からのさまざまな出力を比較する際に使用できます。</br></br>データ型は**int**の[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|**num_of_reads**|**bigint**|ファイルで実行された読み取りの数。|  
|**num_of_bytes_read**|**bigint**|ファイルで読み込まれた総バイト数。|  
|**io_stall_read_ms**|**bigint**|ファイルでの読み取りをユーザーが待機した総時間 (ミリ秒単位)。|  
|**num_of_writes**|**bigint**|ファイルで実行された書き込みの数。|  
|**num_of_bytes_written**|**bigint**|ファイルに書き込まれた総バイト数。|  
|**io_stall_write_ms**|**bigint**|ファイルでの書き込み完了をユーザーが待機した総時間 (ミリ秒単位)。|  
|**io_stall**|**bigint**|ファイルでの I/O 完了をユーザーが待機した総時間 (ミリ秒単位)。|  
|**に対して**|**bigint**|ファイルに対して使用されているディスク上のバイト数。 スパース ファイルの場合、この数値は、データベース スナップショットに使用されているディスク上の実際のバイト数になります。|  
|**file_handle**|**varbinary**|ファイルの Windows ファイル ハンドル。|  
|**io_stall_queued_read_ms**|**bigint**|**適用されません。**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)]です。<br /><br /> 読み取りの IO リソース管理によって発生した IO 待機時間の合計。 NULL 値は許可されません。 詳細については、次を参照してください。 [sys.dm_resource_governor_resource_pools &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md).|  
|**io_stall_queued_write_ms**|**bigint**|**適用されません。**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssSQL12](../../includes/sssql11-md.md)]です。<br /><br />  書き込みの IO リソース管理によって発生した IO 待機時間の合計。 NULL 値は許可されません。|
|**pdw_node_id**|**int**|**適用されます:**[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]</br></br>分布のノードの識別子。
 
  
## <a name="permissions"></a>Permissions  
 VIEW SERVER STATE 権限が必要です。 詳細については、次を参照してください[動的管理ビューおよび関数 &#40;。TRANSACT-SQL と #41 です。](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md).  
  
## <a name="examples"></a>使用例  

### <a name="a-return-statistics-for-a-log-file"></a>A. ログ ファイルの統計情報を返す

**適用されます:** SQL Server (2008年以降)、Azure SQL Database

 次の例では、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベースのログ ファイルに関するすべての統計を返します。  
  
```tsql  
SELECT * FROM sys.dm_io_virtual_file_stats(DB_ID(N'AdventureWorks2012'), 2);  
GO  
```  
  
### <a name="b-return-statistics-for-file-in-tempdb"></a>B. Tempdb のファイルの統計情報を返す

**適用されます:** Azure SQL Data Warehouse

```tsql
SELECT * FROM sys.dm_pdw_nodes_io_virtual_file_stats 
WHERE database_name = ‘tempdb’ AND file_id = 2;

```

## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [関連する動的管理ビューおよび関数 &#40; I、OTRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/i-o-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
  

