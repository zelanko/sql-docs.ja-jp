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
ms.openlocfilehash: 2b31baacea8d4754fbc81e1c1c747a2c95b1402b
ms.sourcegitcommit: 1be90e93980a8e92275b5cc072b12b9e68a3bb9a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84627058"
---
# <a name="syspdw_health_component_properties-transact-sql"></a>pdw_health_component_properties (Transact-sql)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  デバイスを記述するプロパティを格納します。 一部のプロパティにはデバイスの状態が表示され、一部のプロパティはデバイス自体について説明します。  
  
|列名|データ型|説明|Range|  
|-----------------|---------------|-----------------|-----------|  
|property_id|**int**|コンポーネントのプロパティを表す一意の識別子。<br /><br /> このビューのキーは property_id と component_id によって形成されます。|NOT NULL|  
|component_id|**int**|コンポーネントの ID。 「 [Sys. pdw_health_components &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md)」を参照してください。<br /><br /> このビューのキーは property_id と component_id によって形成されます。|NOT NULL|  
|property_name|**nvarchar(255)**|プロパティ名。|NOT NULL|  
|physical_name|**nvarchar(32)**|製造元によって定義されたプロパティ名。|NOT NULL|  
|is_key|**bit**|デバイスインスタンスが一意であるかどうかを判断します。|NOT NULL<br /><br /> 0-デバイスインスタンスは一意です。<br /><br /> 1-デバイスインスタンスが一意ではありません。|  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse and Parallel Data Warehouse Catalog Views (SQL Data Warehouse および Parallel Data Warehouse のカタログ ビュー)](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
