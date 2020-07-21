---
title: pdw_health_component_groups (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
ms.assetid: 5ba27432-7a29-4420-b73d-def621c0b3ac
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 5362c1f441c3b5afee22e8cac75290b476ef8263
ms.sourcegitcommit: 1be90e93980a8e92275b5cc072b12b9e68a3bb9a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84627052"
---
# <a name="syspdw_health_component_groups-transact-sql"></a>pdw_health_component_groups (Transact-sql)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  コンポーネントとデバイスの論理グループに関する情報を格納します。  
  
|列名|データ型|説明|Range|  
|-----------------|---------------|-----------------|-----------|  
|group_id|**int**|コンポーネントとデバイスの一意の識別子。<br /><br /> このビューのキー。|NOT NULL|  
|group_name|**nvarchar(255)**|コンポーネントとデバイスの論理グループ名。|NOT NULL|  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse and Parallel Data Warehouse Catalog Views (SQL Data Warehouse および Parallel Data Warehouse のカタログ ビュー)](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
