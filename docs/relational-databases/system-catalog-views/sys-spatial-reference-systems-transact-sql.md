---
title: sys.spatial_reference_systems (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- spatial_reference_systems_TSQL
- sys.spatial_reference_systems_TSQL
- sys.spatial_reference_systems
- spatial_reference_systems
dev_langs:
- TSQL
helpviewer_keywords:
- sys.spatial_reference_systems catalog view
- spatial_reference_systems
ms.assetid: 3c9bc120-67c3-463f-9e24-29fd623f25a0
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c2ab77dbaf90edf1421a0d15073258c370de4c7d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62856962"
---
# <a name="sysspatialreferencesystems-transact-sql"></a>sys.spatial_reference_systems (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でサポートされている空間参照系 (SRID) の一覧を表示します。  

  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|spatial_reference_id|**int**|サポートされている SRID[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。|  
|authority_name|**nvarchar(128)**|SRID の機関。|  
|authorized_spatial_reference_id|**int**|指定された証明機関によって与え SRID **authority_name**します。|  
|well_known_text|**nvarchar (4000)**|SRID の WKT 表現です。|  
|unit_of_measure|**nvarchar(128)**|測定単位の名前。|  
|unit_conversion_factor|**float**|メートル単位の長さ。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
  
