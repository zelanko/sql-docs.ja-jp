---
title: sys.pdw_nodes_pdw_physical_databases (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/09/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 70e0939d-4d97-4ae0-ba16-934e0a80e718
caps.latest.revision: 9
author: barbkess
ms.author: barbkess
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 6915b277a25cebfa54adb4a6112d84e83657ddd0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="syspdwnodespdwphysicaldatabases-transact-sql"></a>sys.pdw_nodes_pdw_physical_databases (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  コンピューティング ノードでの各物理データベースに 1 行が含まれています。 集計の物理的なデータベース情報を使用して、データベースに関する詳細情報を取得します。 情報を結合に参加させる、`sys.pdw_nodes_pdw_physical_databases`を`sys.pdw_database_mappings`と`sys.databases`テーブル。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|database_id|**int**|データベースのオブジェクト ID。 この値での database_id と同じことに注意してください、 [sys.databases &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)ビュー。|  
|physical_name|**sysname**|シェルとコンピューティング ノードで、データベースの物理名。 この値で physical_name 列の値と同じ、 [sys.pdw_database_mappings &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-catalog-views/sys-pdw-database-mappings-transact-sql.md)ビュー。|  
|pdw_node_id|**int**|ノードに関連付けられている一意の数値 id です。|  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] および [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-returning"></a>A. 返す  
 次のクエリは、名前と各データベースの ID をすべての計算ノードでマスター、および対応するデータベース名で返します。  
  
```  
SELECT D.database_id AS DBID_in_master, D.name AS UserDatabaseName,   
PD.pdw_node_id AS NodeID, DM.physical_name AS PhysDBName   
FROM sys.databases AS D  
JOIN sys.pdw_database_mappings AS DM  
    ON D.database_id = DM.database_id  
JOIN sys.pdw_nodes_pdw_physical_databases AS PD  
    ON DM.physical_name = PD.physical_name  
ORDER BY D.database_id, PD.pdw_node_ID;  
```  
  
### <a name="b-using-syspdwnodespdwphysicaldatabases-to-gather-detailed-object-information"></a>B. Sys.pdw_nodes_pdw_physical_databases を使用して、オブジェクトの詳細な情報を収集するには  
 次のクエリでは、インデックスに関する情報を表示し、データベース内のオブジェクトに、オブジェクトが属しているデータベースについての有用な情報が含まれています。  
  
```  
SELECT D.name AS UserDatabaseName, D.database_id AS DBIDinMaster,  
DM.physical_name AS PhysDBName, PD.pdw_node_id AS NodeID,   
IU.object_id, IU.index_id, IU.user_seeks, IU.user_scans, IU.user_lookups, IU.user_updates  
FROM sys.databases AS D  
JOIN sys.pdw_database_mappings AS DM  
    ON D.database_id = DM.database_id  
JOIN sys.pdw_nodes_pdw_physical_databases AS PD  
    ON DM.physical_name = PD.physical_name  
JOIN sys.dm_pdw_nodes_db_index_usage_stats AS IU  
    ON PD.database_id = IU.database_id  
ORDER BY D.database_id, IU.object_id, IU.index_id, PD.pdw_node_ID;  
```  
  
### <a name="c-using-syspdwnodespdwphysicaldatabases-to-determine-the-encryption-state"></a>C. Sys.pdw_nodes_pdw_physical_databases を使用して、暗号化の状態を確認するには  
 次のクエリでは、AdventureWorksPDW2012 データベースの暗号化の状態を提供します。  
  
```  
WITH dek_encryption_state AS   
(  
    SELECT ISNULL(db_map.database_id, dek.database_id) AS database_id, encryption_state  
    FROM sys.dm_pdw_nodes_database_encryption_keys AS dek  
        INNER JOIN sys.pdw_nodes_pdw_physical_databases AS node_db_map  
            ON dek.database_id = node_db_map.database_id AND dek.pdw_node_id = node_db_map.pdw_node_id  
        LEFT JOIN sys.pdw_database_mappings AS db_map  
            ON node_db_map .physical_name = db_map.physical_name  
        INNER JOIN sys.dm_pdw_nodes AS nodes  
            ON nodes.pdw_node_id = dek.pdw_node_id  
    WHERE dek.encryptor_thumbprint <> 0x  
)  
SELECT TOP 1 encryption_state  
       FROM  dek_encryption_state  
       WHERE dek_encryption_state.database_id = DB_ID('AdventureWorksPDW2012 ')  
       ORDER BY (CASE encryption_state WHEN 3 THEN -1 ELSE encryption_state END) DESC;  
```  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と並列データ ウェアハウスのカタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.pdw_database_mappings &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-database-mappings-transact-sql.md)  
  
  

