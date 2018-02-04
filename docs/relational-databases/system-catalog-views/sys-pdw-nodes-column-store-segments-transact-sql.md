---
title: "sys.pdw_nodes_column_store_segments (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: e2fdf8e9-1b74-4682-b2d4-c62aca053d7f
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c5982fa99effc211d23c7e92557d96e20d131ad4
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="syspdwnodescolumnstoresegments-transact-sql"></a>sys.pdw_nodes_column_store_segments (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  列ストア インデックスに各列の行を格納します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**partition_id**|**bigint**|パーティション ID を示します。 データベース内で一意です。|  
|**hobt_id**|**bigint**|この列ストア インデックスを保持するテーブルのヒープまたは B ツリー インデックス (hobt) の ID。|  
|**column_id**|**int**|列ストアの列の ID。|  
|**segment_id**|**int**|列セグメントの ID。|  
|**version**|**int**|列セグメント形式のバージョン。|  
|**encoding_type**|**int**|そのセグメントに使用されるエンコーディングの種類。|  
|**row_count**|**int**|行グループ内の行の数。|  
|**has_nulls**|**int**|列セグメントに NULL 値がある場合は 1。|  
|**base_id**|**bigint**|エンコードの種類 1 が使用されている場合は、id をベース値です。  エンコードの種類 1 が、使用されていない場合、base_id は 1 に設定します。|  
|**magnitude**|**float**|エンコードの種類 1 が使用されている場合は大きさ。  エンコードの種類 1 が、使用されていない場合は、絶対値が 1 に設定されます。|  
|**primary__dictionary_id**|**int**|プライマリ辞書の ID。|  
|**secondary_dictionary_id**|**int**|セカンダリ辞書の ID。 セカンダリ辞書が定義されていない場合は、-1 を返します。|  
|**min_data_id**|**bigint**|列セグメントの最小データ ID。|  
|**max_data_id**|**bigint**|列セグメントの最大データ ID。|  
|**null_value**|**bigint**|NULL を表すために使用される値。|  
|**on_disk_size**|**bigint**|セグメントのサイズ (バイト単位)。|  
|**pdw_node_id**|**int**|一意の識別子、[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]注意してください。|  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次のクエリは、列ストア インデックスのセグメントに関する情報を返します。  
  
```sql  
SELECT i.name, p.object_id, p.index_id, i.type_desc,   
    COUNT(*) AS number_of_segments  
FROM sys.column_store_segments AS s   
INNER JOIN sys.partitions AS p   
    ON s.hobt_id = p.hobt_id   
INNER JOIN sys.indexes AS i   
    ON p.object_id = i.object_id  
WHERE i.type = 6  
GROUP BY i.name, p.object_id, p.index_id, i.type_desc ;  
```  
  
 Sys.pdw_nodes_column_store_segments と行の数を決定し、ディスク上のセグメントのサイズには、他のシステム テーブルを結合します。  
  
```  
SELECT o.name, css.hobt_id, css. column_id, css.pdw_node_id, css.row_count, css.on_disk_size  
FROM sys.pdw_nodes_column_store_segments AS css  
JOIN sys.pdw_nodes_partitions AS pnp  
    ON css.partition_id = pnp.partition_id  
JOIN sys.pdw_nodes_tables AS part  
    ON pnp.object_id = part.object_id   
    AND pnp.pdw_node_id = part.pdw_node_id  
JOIN sys.pdw_table_mappings AS TMap  
    ON part.name = TMap.physical_name  
JOIN sys.objects AS o  
    ON TMap.object_id = o.object_id  
ORDER BY css.hobt_id, css.column_id;  
```  
  
## <a name="permissions"></a>権限  
 必要があります**VIEW SERVER STATE**権限です。  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と並列データ ウェアハウスのカタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [COLUMNSTORE INDEX &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-columnstore-index-transact-sql.md)   
 [sys.pdw_nodes_column_store_row_groups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-row-groups-transact-sql.md)   
 [sys.pdw_nodes_column_store_dictionaries &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-dictionaries-transact-sql.md)  
  
  

