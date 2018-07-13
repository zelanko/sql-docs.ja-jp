---
title: sys.pdw_index_mappings (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.service: sql-data-warehouse
ms.component: system-objects
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: d62b0e25-3226-4f87-a10a-b3a0d9555e19
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 3dc440c4ab814b83d4398733ae9629e6639f0be7
ms.sourcegitcommit: abd71294ebc39695d403e341c4f77829cb4166a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2018
ms.locfileid: "36772027"
---
# <a name="syspdwindexmappings-transact-sql"></a>sys.pdw_index_mappings (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  一意の組み合わせによって反映されるように、コンピューティング ノードで使用する物理名に、論理インデックスをマップ**object_id**のインデックスを保持するテーブルと**index_id**内で特定のインデックスのテーブルです。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|object_id|**int**|このインデックスが存在する論理テーブルのオブジェクトの ID。 参照してください[sys.objects &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)します。<br /><br /> **physical_name**と**object_id**このビューのキーを形成します。||  
|index_id|**nvarchar(32)**|インデックスの ID。 参照してください[sys.indexes &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)します。||  
|physical_name|**nvarchar(36)**|計算ノード上のデータベース内のインデックスの名前。<br /><br /> **physical_name**と**object_id**このビューのキーを形成します。||  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と Parallel Data Warehouse カタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [sys.pdw_table_mappings &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-table-mappings-transact-sql.md)   
 [sys.pdw_database_mappings &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-database-mappings-transact-sql.md)  
  
  
