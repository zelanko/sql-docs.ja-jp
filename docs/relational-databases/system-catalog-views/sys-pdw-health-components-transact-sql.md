---
title: sys.pdw_health_components (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/04/2017
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
ms.assetid: d5c7589b-09b0-4f12-ab84-feb3ec3fbaaa
caps.latest.revision: 6
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: daa5d0c272125c9cb1b6e4a8821c807e13e0dcd8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="syspdwhealthcomponents-transact-sql"></a>sys.pdw_health_components (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  すべてのコンポーネントと、システムに存在するデバイスに関する情報を格納します。 これらには、ハードウェア、記憶域デバイス、およびネットワーク デバイスが含まれます。  
  
|列名|データ型|Description|範囲|  
|-----------------|---------------|-----------------|-----------|  
|component_id|**int**|コンポーネントまたはデバイスの一意の識別子。<br /><br /> このビューのキーです。|NOT NULL|  
|group_id|**Int**|このコンポーネントが属する論理コンポーネント グループ。 参照してください[sys.pdw_health_components (並列データ ウェアハウス)](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md)です。|NOT NULL|  
|component_name|**nvarchar (255)**|コンポーネント名。|NOT NULL|  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と並列データ ウェアハウスのカタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
