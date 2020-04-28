---
title: pdw_health_component_status_mappings (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.technology: system-objects
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 4272cfad-5ad7-493d-9edd-d9111619bda0
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: ec631e9008cc37a7b4f91ed3f530e5388bdf9c0d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68127500"
---
# <a name="syspdw_health_component_status_mappings-transact-sql"></a>pdw_health_component_status_mappings (Transact-sql)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  [!INCLUDE[ssDW](../../includes/ssdw-md.md)]コンポーネントのステータスと製造元が定義したコンポーネントの名前との間のマッピングを定義します。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|property_id|**int**|プロパティの一意識別子。<br /><br /> property_id、component_id、および physical_name は、このビューのキーを形成します。|NOT NULL|  
|component_id|**int**|コンポーネントの ID。 「 [Sys. pdw_health_components &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md)」を参照してください。<br /><br /> property_id、component_id、および physical_name は、このビューのキーを形成します。|NOT NULL|  
|physical_name|**nvarchar(32)**|製造元によって定義されたプロパティ名。<br /><br /> property_id、component_id、および physical_name は、このビューのキーを形成します。|NOT NULL|  
|logical_name|**nvarchar(255)**|によっ[!INCLUDE[ssDW](../../includes/ssdw-md.md)]て定義されたプロパティ名。|NOT NULL<br /><br /> 0-デバイスインスタンスは一意です。<br /><br /> 1-デバイスインスタンスが一意ではありません。|  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse and Parallel Data Warehouse Catalog Views (SQL Data Warehouse および Parallel Data Warehouse のカタログ ビュー)](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
