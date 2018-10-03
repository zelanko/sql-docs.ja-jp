---
title: sys.dm_pdw_component_health_active_alerts (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
ms.assetid: c53e4a36-b841-424a-b8e2-255b1878deb6
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: bb050494a71d897f49bf00a9aca37af7dbcf97c4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47617960"
---
# <a name="sysdmpdwcomponenthealthactivealerts-transact-sql"></a>sys.dm_pdw_component_health_active_alerts (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  上のアクティブなアラートを格納[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]コンポーネント。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|一意の識別子、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]ノード。<br /><br /> pdw_node_id、component_id、component_instance_id、alert_id、および alert_instance_id は、このビューのキーを形成します。|NOT NULL|  
|component_id|**int**|コンポーネントの ID。 参照してください[sys.pdw_health_components &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md)します。<br /><br /> pdw_node_id、component_id、component_instance_id、alert_id、および alert_instance_id は、このビューのキーを形成します。|NOT NULL|  
|component_instance_id|**nvarchar (255)**|pdw_node_id、component_id、component_instance_id、alert_id、および alert_instance_id は、このビューのキーを形成します。|NOT NULL|  
|alert_id|**int**|アラートの種類の ID。 参照してください[sys.pdw_health_alerts &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md)します。<br /><br /> pdw_node_id、component_id、component_instance_id、alert_id、および alert_instance_id は、このビューのキーを形成します。|NOT NULL|  
|alert_instance_id|**nvarchar(36)**|指定された警告のインスタンスを識別します。<br /><br /> pdw_node_id、component_id、component_instance_id、alert_id、および alert_instance_id は、このビューのキーを形成します。|NOT NULL|  
|current_value|**nvarchar (255)**|型 StatusChange、アラートがある場合に使用されます。 これは、現在のコンポーネントのステータスです。 値は、しきい値の種類のアラートの NULL です。 参照してください[sys.pdw_health_alerts &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md)アラートの種類の一覧についてはします。|NULL|  
|previous_value|**nvarchar (255)**|型 StatusChange、アラートがある場合に使用されます。 これは、前のコンポーネントのステータスです。 値は、しきい値の種類のアラートの NULL です。 参照してください[sys.pdw_health_alerts &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md)アラートの種類の一覧についてはします。|NULL|  
|create_time|**datetime**|アラートが生成された日付と時刻。|NOT NULL|  
  
 このビューで保持される最大行数については、「最小値と最大値」を参照してください、[!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]します。  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と Parallel Data Warehouse の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
