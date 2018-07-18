---
title: sys.dm_pdw_component_health_status (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 68cc3f7a-693c-4d5d-a76b-455352af8d7f
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: f711cc87308f4987c72fec75822b10502c013016
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37968404"
---
# <a name="sysdmpdwcomponenthealthstatus-transact-sql"></a>sys.dm_pdw_component_health_status (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  アプライアンス コンポーネントの現在の正常性に関する情報を保持します。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**||NULL でないです。|  
|component_id|ssNoversion|コンポーネントの ID。 参照してください[sys.pdw_health_components &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md)します。<br /><br /> pdw_node_id、component_id、property_id、および component_instance_id は、このビューのキーを形成します。|NULL でないです。|  
|property_id|**int**|プロパティの ID。 参照してください[sys.pdw_health_component_properties &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-component-properties-transact-sql.md)します。|NOT NULL|  
|component_instance_id|**nvarchar (255)**|コンポーネントのインスタンスを識別します。 Component_instance_id によって特定されます、CPU のインスタンス。 たとえば、'CPU1' を = です。<br /><br /> pdw_node_id、component_id、property_id、および component_instance_id は、このビューのキーを形成します。|NOT NULL|  
|property_value|**nvarchar (255)**|現在のプロパティの値。|NULL|  
|update_time|**datetime**|最後に、メトリックが更新されました。|NOT NULL|  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と Parallel Data Warehouse の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
