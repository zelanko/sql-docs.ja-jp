---
title: pdw_index_mappings (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: d62b0e25-3226-4f87-a10a-b3a0d9555e19
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 3e51acd0ef179d4bb9bf85bed34593f9676db063
ms.sourcegitcommit: 01297f2487fe017760adcc6db5d1df2c1234abb4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2020
ms.locfileid: "86196790"
---
# <a name="syspdw_index_mappings-transact-sql"></a>pdw_index_mappings (Transact-sql)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  は、インデックスを保持するテーブルとそのテーブル内の特定のインデックスの**index_id**の**object_id**の一意の組み合わせによって反映される、計算ノードで使用される物理名に論理インデックスをマップします。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|object_id|**int**|このインデックスが存在する論理テーブルのオブジェクト ID。 「 [Sys &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)」を参照してください。<br /><br /> このビューのキーは**physical_name**と**object_id**によって形成されます。||  
|index_id|**nvarchar(32)**|インデックスの ID。 「 [SQL&#41;&#40;transact-sql ](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)」を参照してください。||  
|physical_name|**nvarchar (36)**|計算ノード上のデータベース内のインデックスの名前。<br /><br /> このビューのキーは**physical_name**と**object_id**によって形成されます。||  
  
## <a name="see-also"></a>関連項目  
 [SQL Data Warehouse and Parallel Data Warehouse Catalog Views (SQL Data Warehouse および Parallel Data Warehouse のカタログ ビュー)](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [pdw_table_mappings &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-pdw-table-mappings-transact-sql.md)   
 [pdw_database_mappings &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-pdw-database-mappings-transact-sql.md)  
  
  
