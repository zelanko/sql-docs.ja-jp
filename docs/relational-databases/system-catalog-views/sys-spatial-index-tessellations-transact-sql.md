---
title: sys.spatial_index_tessellations (TRANSACT-SQL) |Microsoft Docs
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 61dec5024cbc368de0f4ed53570bd6c13d157777
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43018021"
---
# <a name="sysspatialindextessellations-transact-sql"></a>sys.spatial_index_tessellations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

 各空間インデックスのテセレーション スキームおよびパラメーターに関する情報を表します。  
  
> [!NOTE]  
>  テセレーションについて詳しくは、「[空間インデックスの概要](../../relational-databases/spatial/spatial-indexes-overview.md)」をご覧ください。  
  

|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|object_id|**int**|インデックスが定義されているオブジェクトの ID です。 各 (object_id、index_id) ペア対応するエントリを持つ[sys.spatial_indexes](../../relational-databases/system-catalog-views/sys-spatial-indexes-transact-sql.md)します。|  
|index_id|**int**|インデックス列が定義されている空間インデックスの ID です。|  
|tessellation_scheme|**sysname**|いずれかのテセレーション スキームの名前: geometry_grid である、geography_grid の場合|  
|bounding_box_xmin|**float(53)**|境界の左下隅の X 座標がボックスのいずれかの: NULL = 特定のテセレーション スキーム (GEOGRAPHY_GRID など) の適用不可*n* = tessellation_scheme が geometry_grid であると、x 座標の最小値。                     **注:** に従って、各オブジェクトの境界ボックスのパラメーターで定義されている座標が解釈される、[空間参照識別子 (SRID)](../../relational-databases/spatial/spatial-reference-identifiers-srids.md)します。|  
|bounding_box_ymin|**float(53)**|境界の左下隅の Y 座標がボックスのいずれかの: NULL = 特定のテセレーション スキーム (GEOGRAPHY_GRID など) の適用不可*n* = tessellation_scheme が geometry_grid であると、y 座標の最小値|  
|bounding_box_xmax|**float(53)**|境界の右上隅の X 座標がボックスのいずれかの: NULL = 特定のテセレーション スキーム (GEOGRAPHY_GRID など) の適用不可*n* = tessellation_scheme が geometry_grid である x 座標の最大値|  
|bounding_box_ymax|**float(53)**|境界の右上隅の Y 座標がボックスのいずれかの: NULL = 特定のテセレーション スキーム (GEOGRAPHY_GRID など) の適用不可*n* = tessellation_scheme が geometry_grid である y 座標の最大値|  
|level_1_grid|**smallint**|最上位レベルのグリッドのグリッド密度です。 Tessellation_scheme が GEOMETRY_GRID または geography_grid の場合、いずれかの場合: 16 = 4 × 4 グリッド (LOW) 64 = 8 8 のグリッド (MEDIUM) 256 = 16 × 16 グリッド (高) NULL = 特定の空間インデックスの種類またはテセレーション スキームの適用不可。  新しい SQL Server 11 のテセレーションを使用する場合は、NULL が返されます。|  
|level_1_grid_desc|**nvarchar(60)**|いずれかの最上位レベルのグリッドのグリッド密度: 低 MEDIUM 高 NULL = 特定の空間インデックスの種類またはテセレーション スキームの適用不可。  新しい SQL Server 11 のテセレーションを使用する場合は、NULL が返されます。|  
|level_2_grid|**smallint**|第 2 レベルのグリッドのグリッド密度です。 Tessellation_scheme が GEOMETRY_GRID または geography_grid の場合、いずれかの場合: 16 = 4 × 4 グリッド (LOW) 64 = 8 8 のグリッド (MEDIUM) 256 = 16 × 16 グリッド (高) NULL = 特定の空間インデックスの種類またはテセレーション スキームの適用不可。  新しい SQL Server 11 のテセレーションを使用する場合は、NULL が返されます。|  
|level_2_grid_desc|**nvarchar(60)**|第 2 レベルのグリッドのいずれかのグリッド密度: 低 MEDIUM 高 NULL = 特定の空間インデックスの種類またはテセレーション スキームの適用不可。  新しい SQL Server 11 のテセレーションを使用する場合は、NULL が返されます。|  
|level_3_grid|**smallint**|第 3 レベルのグリッドのグリッド密度です。   Tessellation_scheme が GEOMETRY_GRID または geography_grid の場合、いずれかの場合: 16 = 4 × 4 グリッド (LOW) 64 = 8 8 のグリッド (MEDIUM) 256 = 16 × 16 グリッド (高) NULL = 特定の空間インデックスの種類またはテセレーション スキームの適用不可。  新しい SQL Server 11 のテセレーションを使用する場合は、NULL が返されます。|  
|level_3_grid_desc|**nvarchar(60)**|第 3 レベルのグリッドのいずれかのグリッド密度: 低 MEDIUM 高 NULL = 特定の空間インデックスの種類またはテセレーション スキームの適用不可。  新しい SQL Server 11 のテセレーションを使用する場合は、NULL が返されます。|  
|level_4_grid|**smallint**|第 4 レベルのグリッドのグリッド密度です。 Tessellation_scheme が GEOMETRY_GRID または geography_grid の場合、いずれかの場合: 16 = 4 × 4 グリッド (LOW) 64 = 8 8 のグリッド (MEDIUM) 256 = 16 × 16 グリッド (高) NULL = 特定の空間インデックスの種類またはテセレーション スキームの適用不可。  新しい SQL Server 11 のテセレーションを使用する場合は、NULL が返されます。|  
|level_4_grid_desc|**nvarchar(60)**|いずれかの第 4 レベルのグリッドのグリッド密度: < 低 MEDIUM 高 NULL = 特定の空間インデックスの種類またはテセレーション スキームの適用不可。  新しい SQL Server 11 のテセレーションを使用する場合は、NULL が返されます。|  
|cells_per_object|**int**|1 つの空間オブジェクトごとのセルの数: tessellation_scheme が GEOMETRY_GRID または geography_grid の場合場合、 *n* NULL オブジェクトごとのセルの数を = = 特定の空間インデックスの種類またはテセレーション スキームの適用不可|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [空間インデックスの概要](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.spatial_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-spatial-indexes-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)  
  
  
