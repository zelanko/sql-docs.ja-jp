---
title: sys.pdw_health_component_status_mappings (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: pdw
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4272cfad-5ad7-493d-9edd-d9111619bda0
caps.latest.revision: 7
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 00837177a25110063966208442d03392365b7db6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="syspdwhealthcomponentstatusmappings-transact-sql"></a>sys.pdw_health_component_status_mappings (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  間のマッピングを定義、[!INCLUDE[ssDW](../../includes/ssdw-md.md)]コンポーネントのステータスとコンポーネントの製造元定義名。  
  
|列名|データ型|Description|範囲|  
|-----------------|---------------|-----------------|-----------|  
|property_id|**int**|プロパティの一意の識別子。<br /><br /> property_id、< と physical_name は、このビューのキーを形成します。|NOT NULL|  
|component_id|**int**|コンポーネントの ID。 参照してください[sys.pdw_health_components &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md)です。<br /><br /> property_id、< と physical_name は、このビューのキーを形成します。|NOT NULL|  
|physical_name|**nvarchar(32)**|プロパティ名、製造元によって定義されています。<br /><br /> property_id、< と physical_name は、このビューのキーを形成します。|NOT NULL|  
|logical_name|**nvarchar (255)**|プロパティ名で定義されている[!INCLUDE[ssDW](../../includes/ssdw-md.md)]です。|NOT NULL<br /><br /> 0 - デバイスのインスタンスは一意です。<br /><br /> 1 のデバイス インスタンスは一意ではありません。|  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と並列データ ウェアハウスのカタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
