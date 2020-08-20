---
title: pdw_permanent_table_mappings (Transact-sql)
ms.custom: ''
ms.date: 07/24/2020
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
author: mstehrani
ms.author: emtehran
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 12261e8e38e75edf7dd596ca2b3499100cfff5ad
ms.sourcegitcommit: 331b8495e4ab37266945c81ff5b93d250bdaa6da
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/20/2020
ms.locfileid: "88646842"
---
# <a name="syspdw_permanent_table_mappings-transact-sql"></a>pdw_permanent_table_mappings (Transact-sql)
[!INCLUDE [applies-to-version/asa](../../includes/applies-to-version/asa.md)]

  **Object_id**によって、永続的なユーザーテーブルを内部オブジェクト名に結び付けます。 **Pdw_table_mappings**よりも優れたパフォーマンスを得られるようにすることをお勧めします。  
  
> [!NOTE]
> **pdw_permanent_table_mappings** は、永続的なテーブルへのマッピングを保持します。一時テーブルマッピングは含まれません。

|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|physical_name|**nvarchar (36)**|テーブルの物理名。<br /><br /> このビューのキーは**physical_name**と**object_id**によって形成されます。||  
|object_id|**int**|テーブルのオブジェクト ID。 「 [Sys &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)」を参照してください。<br /><br /> このビューのキーは**physical_name**と**object_id**によって形成されます。||  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse and Parallel Data Warehouse Catalog Views (SQL Data Warehouse および Parallel Data Warehouse のカタログ ビュー)](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [pdw_index_mappings &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-pdw-index-mappings-transact-sql.md)  
  
  
