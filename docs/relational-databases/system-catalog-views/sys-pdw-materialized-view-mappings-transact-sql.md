---
title: sys.pdw_materialized_view_mappings (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 07/03/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: d62b0e25-3226-4f87-a10a-b3a0d9555e19
author: XiaoyuL-Preview
ms.author: xiaoyul
manager: craigg
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 1dac4496a47b9b6b2beeef07e256805bc66b1e87
ms.sourcegitcommit: e4b241fd92689c2aa6e1f5e625874bd0b807dd01
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/04/2019
ms.locfileid: "67566644"
---
# <a name="syspdwmaterializedviewmappings-transact-sql-preview"></a>sys.pdw_materialized_view_mappings (TRANSACT-SQL) (プレビュー)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Object_id で内部オブジェクト名に具体化されたビューに結び付いています。

列 physical_name および object_id は、このカタログ ビューのキーを形成します。
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|physical_name |**nvarchar(36)**|具体化されたビューの物理名。|  
|object_id  |**int**|具体化されたビューのオブジェクト ID。 参照してください[sys.objects (TRANSACT-SQL)](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql?view=azure-sqldw-latest)します。| 

## <a name="permissions"></a>アクセス許可

VIEW DATABASE STATE 権限が必要です。
  
## <a name="see-also"></a>関連項目

[MATERIALIZED VIEW AS を SELECT 作成&#40;TRANSACT-SQL&#41;](/sql/t-sql/statements/create-materialized-view-as-select-transact-sql?view=azure-sqldw-latest)   
[ALTER MATERIALIZED VIEW &#40;TRANSACT-SQL&#41;](/sql/t-sql/statements/alter-materialized-view-transact-sql?view=azure-sqldw-latest)   
[説明&#40;TRANSACT-SQL&#41;](/sql/t-sql/queries/explain-transact-sql?view=azure-sqldw-latest)   
[sys.pdw_materialized_view_column_distribution_properties &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-pdw-materialized-view-column-distribution-properties-transact-sql?view=azure-sqldw-latest)   
[sys.pdw_materialized_view_distribution_properties &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-pdw-materialized-view-distribution-properties-transact-sql?view=azure-sqldw-latest)   
[DBCC PDW_SHOWMATERIALIZEDVIEWOVERHEAD &#40;TRANSACT-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-pdw-showmaterializedviewoverhead-transact-sql?view=azure-sqldw-latest)   
[SQL Data Warehouse と Parallel Data Warehouse カタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
[Azure SQL Data Warehouse でサポートされるシステム ビュー](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-system-views)   
[Azure SQL Data Warehouse でサポートされる T-SQL ステートメント](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-statements) 