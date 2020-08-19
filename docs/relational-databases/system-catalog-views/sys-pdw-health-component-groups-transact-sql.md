---
description: pdw_health_component_groups (Transact-sql)
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
ms.openlocfilehash: a327506fbfe71aa7473669bd63f7c4aec147fd7f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88490285"
---
# <a name="syspdw_health_component_groups-transact-sql"></a>pdw_health_component_groups (Transact-sql)
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  コンポーネントとデバイスの論理グループに関する情報を格納します。  
  
|列名|データ型|説明|Range|  
|-----------------|---------------|-----------------|-----------|  
|group_id|**int**|コンポーネントとデバイスの一意の識別子。<br /><br /> このビューのキー。|NOT NULL|  
|group_name|**nvarchar (255)**|コンポーネントとデバイスの論理グループ名。|NOT NULL|  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse and Parallel Data Warehouse Catalog Views (SQL Data Warehouse および Parallel Data Warehouse のカタログ ビュー)](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
