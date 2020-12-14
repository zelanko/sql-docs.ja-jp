---
title: sys.pdw_permanent_table_mappings (Transact-sql)
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
monikerRange: = azure-sqldw-latest
ms.openlocfilehash: d832c11ccf2090454a11fa3c913455d38aff84e6
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/14/2020
ms.locfileid: "97404339"
---
# <a name="syspdw_permanent_table_mappings-transact-sql"></a>sys.pdw_permanent_table_mappings (Transact-sql)
[!INCLUDE [applies-to-version/asa](../../includes/applies-to-version/asa.md)]

  **Object_id** によって、永続的なユーザーテーブルを内部オブジェクト名に結び付けます。  
  
> [!NOTE]
> **sys.pdw_permanent_table_mappings** は、永続的なテーブルへのマッピングを保持し、一時テーブルまたは外部テーブルマッピングを含みません。

|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|physical_name|**nvarchar (36)**|テーブルの物理名。<br /><br /> このビューのキーは **physical_name** と **object_id** によって形成されます。||  
|object_id|**int**|テーブルのオブジェクト ID。 「 [Sys &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)」を参照してください。<br /><br /> このビューのキーは **physical_name** と **object_id** によって形成されます。||  
  
## <a name="see-also"></a>参照  
 [Azure Synapse Analytics と Parallel Data Warehouse のカタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [sys.pdw_index_mappings &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-pdw-index-mappings-transact-sql.md)  
  
  
