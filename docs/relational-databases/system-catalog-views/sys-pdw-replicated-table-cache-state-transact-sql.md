---
title: sys.pdw_replicated_table_cache_state (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 07/03/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 41d1cbf37418804ef3a39efc268c818f6966c5f8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47835470"
---
# <a name="syspdwreplicatedtablecachestate-transact-sql"></a>sys.pdw_replicated_table_cache_state (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

  レプリケートされたテーブルに関連付けられたキャッシュの状態を返します**object_id**します。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|object_id|**int**|テーブルのオブジェクト ID。 参照してください[sys.objects &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)します。<br /><br /> **object_id**はこのビューのキーです。||  
|state|**nvarchar(40)**|このテーブルのレプリケートされたテーブルのキャッシュの状態。|'NotReady','Ready'|  
  
## <a name="example"></a>例
この例では、テーブル名と、レプリケートされたテーブルのキャッシュの状態を取得する sys.tables sys.pdw_replicated_table_cache_state を結合します。

```sql
SELECT t.[name], p.[object_id], p.[state]
  FROM sys.pdw_replicated_table_cache_state p 
  JOIN sys.tables t ON t.object_id = p.object_id
```



## <a name="next-steps"></a>次の手順  
 SQL Data Warehouse と Parallel Data Warehouse のすべてのカタログ ビューの一覧は、次を参照してください。 [SQL Data Warehouse と並列データ ウェアハウスのカタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)します。   
  
