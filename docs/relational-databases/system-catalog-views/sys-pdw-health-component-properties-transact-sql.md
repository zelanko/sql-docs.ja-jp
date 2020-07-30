---
title: pdw_health_component_properties (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
ms.assetid: 66999c0c-dc43-4327-99fb-8366f465e69d
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 7c0366492dbf22364b04bc436262f7cb83fe8505
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/29/2020
ms.locfileid: "87396046"
---
# <a name="syspdw_health_component_properties-transact-sql"></a>pdw_health_component_properties (Transact-sql)
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  デバイスを記述するプロパティを格納します。 一部のプロパティにはデバイスの状態が表示され、一部のプロパティはデバイス自体について説明します。  
  
|列名|データ型|説明|Range|  
|-----------------|---------------|-----------------|-----------|  
|property_id|**int**|コンポーネントのプロパティを表す一意の識別子。<br /><br /> このビューのキーは property_id と component_id によって形成されます。|NOT NULL|  
|component_id|**int**|コンポーネントの ID。 「 [Sys. pdw_health_components &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md)」を参照してください。<br /><br /> このビューのキーは property_id と component_id によって形成されます。|NOT NULL|  
|property_name|**nvarchar (255)**|プロパティ名。|NOT NULL|  
|physical_name|**nvarchar(32)**|製造元によって定義されたプロパティ名。|NOT NULL|  
|is_key|**bit**|デバイスインスタンスが一意であるかどうかを判断します。|NOT NULL<br /><br /> 0-デバイスインスタンスは一意です。<br /><br /> 1-デバイスインスタンスが一意ではありません。|  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse and Parallel Data Warehouse Catalog Views (SQL Data Warehouse および Parallel Data Warehouse のカタログ ビュー)](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
