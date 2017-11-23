---
title: "sys.spatial_reference_systems (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- spatial_reference_systems_TSQL
- sys.spatial_reference_systems_TSQL
- sys.spatial_reference_systems
- spatial_reference_systems
dev_langs: TSQL
helpviewer_keywords:
- sys.spatial_reference_systems catalog view
- spatial_reference_systems
ms.assetid: 3c9bc120-67c3-463f-9e24-29fd623f25a0
caps.latest.revision: "11"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a4490cc6d28ee06193436de8b57cde8e7ac04402
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sysspatialreferencesystems-transact-sql"></a>sys.spatial_reference_systems (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でサポートされている空間参照系 (SRID) の一覧を表示します。  

  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|spatial_reference_id|**int**|サポートされている SRID[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。|  
|authority_name|**nvarchar (128)**|SRID の機関。|  
|authorized_spatial_reference_id|**int**|指定された証明機関によって与え SRID **authority_name**です。|  
|well_known_text|**nvarchar (4000)**|SRID の WKT 表現。|  
|unit_of_measure|**nvarchar (128)**|メジャーの単位の名前。|  
|unit_conversion_factor|**float**|メートル単位の長さ。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
  
