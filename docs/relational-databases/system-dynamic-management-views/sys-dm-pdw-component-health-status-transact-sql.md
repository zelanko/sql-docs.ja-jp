---
title: "sys.dm_pdw_component_health_status (TRANSACT-SQL) |Microsoft ドキュメント"
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
ms.assetid: 68cc3f7a-693c-4d5d-a76b-455352af8d7f
caps.latest.revision: "6"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d87c8ef38185e3194da1d13f8a9732991023f0ab
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmpdwcomponenthealthstatus-transact-sql"></a>sys.dm_pdw_component_health_status (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  アプライアンス コンポーネントの現在の状態に関する情報を保持します。  
  
|列名|データ型|Description|範囲|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**||NULL でないです。|  
|component_id|int|コンポーネントの ID。 参照してください[sys.pdw_health_components &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> pdw_node_id、component_id、property_id、および component_instance_id は、このビューのキーを形成します。|NULL でないです。|  
|property_id|**int**|プロパティの ID です。 参照してください[sys.pdw_health_component_properties &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-pdw-health-component-properties-transact-sql.md).|NOT NULL|  
|component_instance_id|**nvarchar (255)**|コンポーネントのインスタンスを識別します。 Component_instance_id によって CPU のインスタンスを識別可能性があります、'CPU1' を = です。<br /><br /> pdw_node_id、component_id、property_id、および component_instance_id は、このビューのキーを形成します。|NOT NULL|  
|property_value|**nvarchar (255)**|現在のプロパティ値。|NULL|  
|update_time|**datetime**|最後に、メトリックが更新されました。|NOT NULL|  
  
## <a name="see-also"></a>参照  
 [SQL データ ウェアハウスと並列データ ウェアハウスの動的管理ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
