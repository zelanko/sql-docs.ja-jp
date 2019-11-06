---
title: sys.dm_pdw_component_health_active_alerts (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: c53e4a36-b841-424a-b8e2-255b1878deb6
author: stevestein
ms.author: sstein
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 7378b5f4f87c2511909aef6b75c412b6043e8c71
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67899546"
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
  
## <a name="see-also"></a>関連項目  
 [SQL Data Warehouse と Parallel Data Warehouse の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
