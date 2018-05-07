---
title: sys.pdw_index_mappings (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: d62b0e25-3226-4f87-a10a-b3a0d9555e19
caps.latest.revision: 7
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: f4641d07b6222ee50183948e7730c01f93ac4fe4
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="syspdwindexmappings-transact-sql"></a>sys.pdw_index_mappings (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  一意の組み合わせによって反映されるように、コンピューティング ノードで使用する物理名に、論理インデックスをマップ**object_id**のインデックスを保持するテーブルと**index_id**内の特定のインデックスのテーブルです。  
  
|列名|データ型|Description|範囲|  
|-----------------|---------------|-----------------|-----------|  
|object_id|**int**|このインデックスが存在する論理テーブルのオブジェクトの ID。 参照してください[sys.objects &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)です。<br /><br /> **physical_name**と**object_id**このビューのキーを形成します。||  
|index_id|**nvarchar(32)**|インデックスの ID。 参照してください[sys.indexes &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)です。||  
|physical_name|**nvarchar(36)**|計算ノード上のデータベース内のインデックスの名前。<br /><br /> **physical_name**と**object_id**このビューのキーを形成します。||  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と並列データ ウェアハウスのカタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [sys.pdw_table_mappings &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-table-mappings-transact-sql.md)   
 [sys.pdw_database_mappings &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-database-mappings-transact-sql.md)  
  
  
