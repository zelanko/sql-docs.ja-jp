---
title: sys.spatial_index_tessellations (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- spatial_index_tessellations
- sys.spatial_index_tessellations_TSQL
- spatial_index_tessellations_TSQL
- sys.spatial_index_tessellations
dev_langs:
- TSQL
helpviewer_keywords:
- sys.spatial_index_tessellations catalog view
ms.assetid: 8b17a9a4-b57f-4220-8138-fc73581b1670
caps.latest.revision: 30
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 766b756ab0b00c3e5239a2fe5063e22eed230861
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33221823"
---
# <a name="sysspatialindextessellations-transact-sql"></a>sys.spatial_index_tessellations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

 各空間インデックスのテセレーション スキームおよびパラメーターに関する情報を表します。  
  
> [!NOTE]  
>  テセレーションについて詳しくは、「[空間インデックスの概要](../../relational-databases/spatial/spatial-indexes-overview.md)」をご覧ください。  
  

|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|object_id|**int**|インデックスが定義されているオブジェクトの ID です。 各 (object_id、index_id) のペアが、対応するエントリ[sys.spatial_indexes](../../relational-databases/system-catalog-views/sys-spatial-indexes-transact-sql.md)です。|  
|index_id|**int**|インデックス列が定義されている空間インデックスの ID です。|  
|tessellation_scheme|**sysname**|いずれかのテセレーション スキームの名前: geometry_grid である、GEOGRAPHY_GRID|  
|bounding_box_xmin|**float(53)**|境界の左下隅の X 座標がボックスのいずれかの: NULL = 特定のテセレーション スキーム (GEOGRAPHY_GRID など) の適用不可*n* = tessellation_scheme が geometry_grid であると、x 座標の最小値の場合。                     **注:** 境界ボックスのパラメーターで定義された座標の解釈によると、各オブジェクトの[空間参照識別子 (SRID)](../../relational-databases/spatial/spatial-reference-identifiers-srids.md)です。|  
|bounding_box_ymin|**float(53)**|境界の左下隅の Y 座標がボックスのいずれかの: NULL = 特定のテセレーション スキーム (GEOGRAPHY_GRID など) の適用不可*n* = tessellation_scheme が geometry_grid であると、y 座標の最小値の場合|  
|bounding_box_xmax|**float(53)**|境界の右上隅の X 座標がボックスのいずれかの: NULL = 特定のテセレーション スキーム (GEOGRAPHY_GRID など) の適用不可*n* = tessellation_scheme が geometry_grid である x 座標の最大値の場合|  
|bounding_box_ymax|**float(53)**|境界の右上隅の Y 座標がボックスのいずれかの: NULL = 特定のテセレーション スキーム (GEOGRAPHY_GRID など) の適用不可*n* = tessellation_scheme が geometry_grid であると y 座標の最大値の場合|  
|level_1_grid|**smallint**|最上位レベルのグリッドのグリッド密度です。 Tessellation_scheme が GEOMETRY_GRID または GEOGRAPHY_GRID のいずれかの場合: 16 = 4 × 4 グリッド (LOW) 64 = 8 8 グリッド (MEDIUM) 256 = 16 × 16 グリッド (高) NULL = 特定の空間インデックスの種類またはテセレーション スキームの適用不可。  新しい SQL Server 11 のテセレーションを使用する場合は、NULL が返されます。|  
|level_1_grid_desc|**nvarchar(60)**|グリッドのグリッド密度で、最上位レベルのいずれかの: 低中高 NULL = 特定の空間インデックスの種類またはテセレーション スキームの適用不可。  新しい SQL Server 11 のテセレーションを使用する場合は、NULL が返されます。|  
|level_2_grid|**smallint**|第 2 レベルのグリッドのグリッド密度です。 Tessellation_scheme が GEOMETRY_GRID または GEOGRAPHY_GRID のいずれかの場合: 16 = 4 × 4 グリッド (LOW) 64 = 8 8 グリッド (MEDIUM) 256 = 16 × 16 グリッド (高) NULL = 特定の空間インデックスの種類またはテセレーション スキームの適用不可。  新しい SQL Server 11 のテセレーションを使用する場合は、NULL が返されます。|  
|level_2_grid_desc|**nvarchar(60)**|グリッドのグリッド密度で、第 2 レベルのいずれかの: 低中高 NULL = 特定の空間インデックスの種類またはテセレーション スキームの適用不可。  新しい SQL Server 11 のテセレーションを使用する場合は、NULL が返されます。|  
|level_3_grid|**smallint**|第 3 レベルのグリッドのグリッド密度です。   Tessellation_scheme が GEOMETRY_GRID または GEOGRAPHY_GRID のいずれかの場合: 16 = 4 × 4 グリッド (LOW) 64 = 8 8 グリッド (MEDIUM) 256 = 16 × 16 グリッド (高) NULL = 特定の空間インデックスの種類またはテセレーション スキームの適用不可。  新しい SQL Server 11 のテセレーションを使用する場合は、NULL が返されます。|  
|level_3_grid_desc|**nvarchar(60)**|グリッドのグリッド密度で、第 3 レベルのいずれかの: 低中高 NULL = 特定の空間インデックスの種類またはテセレーション スキームの適用不可。  新しい SQL Server 11 のテセレーションを使用する場合は、NULL が返されます。|  
|level_4_grid|**smallint**|第 4 レベルのグリッドのグリッド密度です。 Tessellation_scheme が GEOMETRY_GRID または GEOGRAPHY_GRID のいずれかの場合: 16 = 4 × 4 グリッド (LOW) 64 = 8 8 グリッド (MEDIUM) 256 = 16 × 16 グリッド (高) NULL = 特定の空間インデックスの種類またはテセレーション スキームの適用不可。  新しい SQL Server 11 のテセレーションを使用する場合は、NULL が返されます。|  
|level_4_grid_desc|**nvarchar(60)**|いずれかの第 4 レベルのグリッドのグリッド密度: < 低中高 NULL = 特定の空間インデックスの種類またはテセレーション スキームの適用不可。  新しい SQL Server 11 のテセレーションを使用する場合は、NULL が返されます。|  
|cells_per_object|**int**|1 つの空間オブジェクトごとのセルの数: tessellation_scheme が GEOMETRY_GRID または GEOGRAPHY_GRID 場合、 *n* NULL オブジェクトごとのセルの数を = = 特定の空間インデックスの種類またはテセレーション スキームの適用不可|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [空間インデックスの概要](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.spatial_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-spatial-indexes-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)  
  
  
