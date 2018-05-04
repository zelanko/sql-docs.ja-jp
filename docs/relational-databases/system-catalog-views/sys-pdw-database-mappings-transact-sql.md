---
title: sys.pdw_database_mappings (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 10/17/2017
ms.prod: sql
ms.prod_service: pdw
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 4ae2c71e-dd56-41ea-a16b-64936175b459
caps.latest.revision: 9
author: barbkess
ms.author: barbkess
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: cea6982fadef5679d4f79e73d15a8286a3136a13
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="syspdwdatabasemappings-transact-sql"></a>sys.pdw_database_mappings (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  マップ、 **database_id**物理名にデータベースの s が、コンピューティング ノードで使用され、提供、**プリンシパル id**システム上のデータベースの所有者のです。 参加**sys.pdw_database_mappings**に**sys.databases**と**sys.pdw_nodes_pdw_physical_databases**です。  
  
|列名|データ型|Description|範囲|  
|-----------------|---------------|-----------------|-----------|  
|physical_name|**nvarchar(36)**|コンピューティング ノードで、データベースの物理名。<br /><br /> **physical_name**と**database_id**このビューのキーを形成します。||  
|database_id|**int**|データベースのオブジェクト ID。 参照してください[sys.databases &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)です。<br /><br /> **physical_name**と**database_id**このビューのキーを形成します。||  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>例: [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例では、sys.pdw_database_mappings をデータベースにマップする方法を表示するには、他のシステム テーブルに結合します。  
  
```  
SELECT DB.database_id, DB.name, Map.*, Phys.*   
FROM sys.databases AS DB  
JOIN sys.pdw_database_mappings AS Map  
    ON DB.database_id = Map.database_id  
JOIN sys.pdw_nodes_pdw_physical_databases AS Phys  
    ON Map.physical_name = Phys.physical_name  
ORDER BY DB.database_id, Phys.pdw_node_id;  
```  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と並列データ ウェアハウスのカタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [sys.pdw_index_mappings &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-index-mappings-transact-sql.md)   
 [sys.pdw_table_mappings &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-table-mappings-transact-sql.md)   
 [sys.pdw_nodes_pdw_physical_databases &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-pdw-physical-databases-transact-sql.md)  
  
  

