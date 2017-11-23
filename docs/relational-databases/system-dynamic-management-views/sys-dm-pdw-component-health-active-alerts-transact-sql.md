---
title: "sys.dm_pdw_component_health_active_alerts (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c53e4a36-b841-424a-b8e2-255b1878deb6
caps.latest.revision: "8"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c88fd88a8545e5fa375732377f0afdbf92b70f96
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmpdwcomponenthealthactivealerts-transact-sql"></a>sys.dm_pdw_component_health_active_alerts (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  上のアクティブなアラートを格納[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]コンポーネントです。  
  
|列名|データ型|Description|範囲|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|一意の識別子、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]ノード。<br /><br /> pdw_node_id、component_id、component_instance_id、alert_id、および alert_instance_id は、このビューのキーを形成します。|NOT NULL|  
|component_id|**int**|コンポーネントの ID。 参照してください[sys.pdw_health_components &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> pdw_node_id、component_id、component_instance_id、alert_id、および alert_instance_id は、このビューのキーを形成します。|NOT NULL|  
|component_instance_id|**nvarchar (255)**|pdw_node_id、component_id、component_instance_id、alert_id、および alert_instance_id は、このビューのキーを形成します。|NOT NULL|  
|alert_id|**int**|アラートの種類の ID。 参照してください[sys.pdw_health_alerts &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md).<br /><br /> pdw_node_id、component_id、component_instance_id、alert_id、および alert_instance_id は、このビューのキーを形成します。|NOT NULL|  
|alert_instance_id|**nvarchar (36)**|指定された警告のインスタンスを識別します。<br /><br /> pdw_node_id、component_id、component_instance_id、alert_id、および alert_instance_id は、このビューのキーを形成します。|NOT NULL|  
|current_value|**nvarchar (255)**|アラートが種類状況のときに使用します。 これは、現在のコンポーネントのステータスです。 しきい値の種類のアラートに使用される値は NULL です。 参照してください[sys.pdw_health_alerts &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md)アラートの種類の一覧についてはします。|NULL|  
|previous_value|**nvarchar (255)**|アラートが種類状況のときに使用します。 これは、以前のコンポーネントのステータスです。 しきい値の種類のアラートに使用される値は NULL です。 参照してください[sys.pdw_health_alerts &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-pdw-health-alerts-transact-sql.md)アラートの種類の一覧についてはします。|NULL|  
|create_time|**datetime**|アラートが生成された日付と時刻。|NOT NULL|  
  
 このビューで保持される最大行数のについては、「最小値と最大値」を参照してください、[!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]です。  
  
## <a name="see-also"></a>参照  
 [SQL データ ウェアハウスと並列データ ウェアハウスの動的管理ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
