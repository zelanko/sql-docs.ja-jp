---
title: "sys.pdw_replicated_table_cache_state (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/03/2017
ms.prod: 
ms.prod_service: sql-data-warehouse
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
author: ronortloff
ms.author: rortloff;barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 700ebe6ee06ebbcccf9c1388cb3a4f8015a26669
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="syspdwreplicatedtablecachestate-transact-sql"></a>sys.pdw_replicated_table_cache_state (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

  レプリケートされたテーブルに関連付けられているキャッシュの状態を返す**object_id**です。  
  
|列名|データ型|Description|範囲|  
|-----------------|---------------|-----------------|-----------|  
|object_id|**int**|テーブルのオブジェクト ID。 参照してください[sys.objects &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).<br /><br /> **object_id**はこのビューのキーです。||  
|state|**nvarchar (40)**|このテーブルのレプリケートされたテーブルのキャッシュの状態。|' 準備不完了 '、'準備完了'|  
  
## <a name="example"></a>例
この例では、テーブル名と、レプリケートされたテーブルのキャッシュの状態を取得する sys.tables で sys.pdw_replicated_table_cache_state を結合します。

```sql
SELECT t.[name], p.[object_id], p.[state]
  FROM sys.pdw_replicated_table_cache_state p 
  JOIN sys.tables t ON t.object_id = p.object_id
```



## <a name="next-steps"></a>次の手順  
 SQL Data Warehouse と並列データ ウェアハウスのすべてのカタログ ビューの一覧は、次を参照してください。 [SQL Data Warehouse と並列データ ウェアハウスのカタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)です。   
  
