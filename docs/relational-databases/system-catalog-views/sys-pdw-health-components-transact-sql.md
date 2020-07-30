---
title: pdw_health_components (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
ms.assetid: d5c7589b-09b0-4f12-ab84-feb3ec3fbaaa
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 83bea79a009e25d54f9d0ae589936de7fed7d94a
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/29/2020
ms.locfileid: "87396041"
---
# <a name="syspdw_health_components-transact-sql"></a>pdw_health_components (Transact-sql)
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  システムに存在するすべてのコンポーネントとデバイスに関する情報を格納します。 これには、ハードウェア、記憶装置、およびネットワークデバイスが含まれます。  
  
|列名|データ型|説明|Range|  
|-----------------|---------------|-----------------|-----------|  
|component_id|**int**|コンポーネントまたはデバイスの一意識別子。<br /><br /> このビューのキー。|NOT NULL|  
|group_id|**Int**|このコンポーネントが属する論理コンポーネントグループ。 「 [Pdw_health_components (並列データウェアハウス)](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md)」を参照してください。|NOT NULL|  
|component_name|**nvarchar (255)**|コンポーネント名。|NOT NULL|  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse and Parallel Data Warehouse Catalog Views (SQL Data Warehouse および Parallel Data Warehouse のカタログ ビュー)](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
