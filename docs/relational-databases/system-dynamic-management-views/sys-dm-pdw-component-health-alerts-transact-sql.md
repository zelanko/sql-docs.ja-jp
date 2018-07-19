---
title: sys.dm_pdw_component_health_alerts (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 88f05392-1e97-4693-ba60-a4910af3c000
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: d1ced797c989bbda28b411b7a0639c2101b81dbd
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38003256"
---
# <a name="sysdmpdwcomponenthealthalerts-transact-sql"></a>sys.dm_pdw_component_health_alerts (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  アプライアンスのコンポーネントにアラートを発行したを保存します。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|一意の識別子、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]ノード。<br /><br /> pdw_node_id、component_id、component_instance_id、alert_id、および alert_instance_id は、このビューのキーを形成します。|NOT NULL|  
|component_id|**int**|コンポーネントの ID。 参照してください[sys.pdw_health_components &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md)します。<br /><br /> pdw_node_id、component_id、component_instance_id、alert_id、および alert_instance_id は、このビューのキーを形成します。|NOT NULL|  
|component_instance_id|**nvarchar (255)**|pdw_node_id、component_id、component_instance_id、alert_id、および alert_instance_id は、このビューのキーを形成します。|NOT NULL|  
|alert_id|**int**|アラートの種類の ID。 参照してください[sys.pdw_health_alerts &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md)します。<br /><br /> pdw_node_id、component_id、component_instance_id、alert_id、および alert_instance_id は、このビューのキーを形成します。|NOT NULL|  
|alert_instance_id|**nvarchar(36)**|指定された警告のインスタンスを識別します。<br /><br /> pdw_node_id、component_id、component_instance_id、alert_id、および alert_instance_id は、このビューのキーを形成します。|NOT NULL|  
|previous_value|**nvarchar (255)**|型 StatusChange、アラートがある場合に使用されます。 これは、前のコンポーネントのステータスです。 値は、しきい値の種類のアラートの NULL です。 参照してください[sys.pdw_health_alerts &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md)アラートの種類の一覧についてはします。|NULL|  
|current_value|**nvarchar (255)**|型 StatusChange、アラートがある場合に使用されます。 これは、現在のコンポーネントのステータスです。 値は、しきい値の種類のアラートの NULL です。 参照してください[sys.pdw_health_alerts &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md)アラートの種類の一覧についてはします。|NULL|  
|create_time|**datetime**|アラートが生成された日付と時刻。|NOT NULL|  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と Parallel Data Warehouse の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
