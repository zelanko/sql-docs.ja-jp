---
title: pdw_health_component_status_mappings (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
ms.assetid: 4272cfad-5ad7-493d-9edd-d9111619bda0
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 32300b0f0ee89e2a135468a658bde49bb77f7c69
ms.sourcegitcommit: 1be90e93980a8e92275b5cc072b12b9e68a3bb9a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84627158"
---
# <a name="syspdw_health_component_status_mappings-transact-sql"></a>pdw_health_component_status_mappings (Transact-sql)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  コンポーネントのステータスと製造元が定義したコンポーネントの名前との間のマッピングを定義し [!INCLUDE[ssDW](../../includes/ssdw-md.md)] ます。  
  
|列名|データ型|説明|Range|  
|-----------------|---------------|-----------------|-----------|  
|property_id|**int**|プロパティの一意識別子。<br /><br /> property_id、component_id、および physical_name は、このビューのキーを形成します。|NOT NULL|  
|component_id|**int**|コンポーネントの ID。 「 [Sys. pdw_health_components &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md)」を参照してください。<br /><br /> property_id、component_id、および physical_name は、このビューのキーを形成します。|NOT NULL|  
|physical_name|**nvarchar(32)**|製造元によって定義されたプロパティ名。<br /><br /> property_id、component_id、および physical_name は、このビューのキーを形成します。|NOT NULL|  
|logical_name|**nvarchar(255)**|によって定義されたプロパティ名 [!INCLUDE[ssDW](../../includes/ssdw-md.md)] 。|NOT NULL<br /><br /> 0-デバイスインスタンスは一意です。<br /><br /> 1-デバイスインスタンスが一意ではありません。|  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse and Parallel Data Warehouse Catalog Views (SQL Data Warehouse および Parallel Data Warehouse のカタログ ビュー)](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
