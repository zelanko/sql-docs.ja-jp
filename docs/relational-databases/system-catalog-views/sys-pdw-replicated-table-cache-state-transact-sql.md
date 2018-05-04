---
title: sys.pdw_replicated_table_cache_state (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 07/03/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: barbkess
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 02c228a15c76a791ab3abd2558d63ed71d403471
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="syspdwreplicatedtablecachestate-transact-sql"></a>sys.pdw_replicated_table_cache_state (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

  レプリケートされたテーブルに関連付けられているキャッシュの状態を返す**object_id**です。  
  
|列名|データ型|Description|範囲|  
|-----------------|---------------|-----------------|-----------|  
|object_id|**int**|テーブルのオブジェクト ID。 参照してください[sys.objects &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)です。<br /><br /> **object_id**はこのビューのキーです。||  
|state|**nvarchar(40)**|このテーブルのレプリケートされたテーブルのキャッシュの状態。|'NotReady','Ready'|  
  
## <a name="example"></a>例
この例では、テーブル名と、レプリケートされたテーブルのキャッシュの状態を取得する sys.tables で sys.pdw_replicated_table_cache_state を結合します。

```sql
SELECT t.[name], p.[object_id], p.[state]
  FROM sys.pdw_replicated_table_cache_state p 
  JOIN sys.tables t ON t.object_id = p.object_id
```



## <a name="next-steps"></a>次の手順  
 SQL Data Warehouse と並列データ ウェアハウスのすべてのカタログ ビューの一覧は、次を参照してください。 [SQL Data Warehouse と並列データ ウェアハウスのカタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)です。   
  
