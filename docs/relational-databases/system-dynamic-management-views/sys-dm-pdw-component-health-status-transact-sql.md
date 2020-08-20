---
description: dm_pdw_component_health_status (Transact-sql)
title: dm_pdw_component_health_status (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 68cc3f7a-693c-4d5d-a76b-455352af8d7f
author: CarlRabeler
ms.author: carlrab
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: e68972138ece8587c81be1de3d9f3cf66b998022
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88481876"
---
# <a name="sysdm_pdw_component_health_status-transact-sql"></a>dm_pdw_component_health_status (Transact-sql)
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  アプライアンスコンポーネントの現在の正常性に関する情報を保持します。  
  
|列名|データ型|説明|Range|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**||NULL 以外|  
|component_id|INT|コンポーネントの ID。 「 [Sys. pdw_health_components &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md)」を参照してください。<br /><br /> pdw_node_id、component_id、property_id、および component_instance_id は、このビューのキーを形成します。|NULL 以外|  
|property_id|**int**|プロパティの ID。 「 [Sys. pdw_health_component_properties &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-component-properties-transact-sql.md)」を参照してください。|NOT NULL|  
|component_instance_id|**nvarchar (255)**|コンポーネントのインスタンスを識別します。 たとえば、CPU のインスタンスが component_instance_id = ' CPU1 ' によって識別される場合があります。<br /><br /> pdw_node_id、component_id、property_id、および component_instance_id は、このビューのキーを形成します。|NOT NULL|  
|property_value|**nvarchar (255)**|現在のプロパティ値。|NULL|  
|update_time|**datetime**|メトリックが最後に更新された時刻。|NOT NULL|  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse および並列データウェアハウスの動的管理ビュー &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
