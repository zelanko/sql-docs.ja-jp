---
title: "sys.pdw_table_distribution_properties (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 639a7475-7c92-41e0-a8ab-ad630eb5aea3
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a192bc274c3d2bc6485c4642882809ee7f375035
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="syspdwtabledistributionproperties-transact-sql"></a>sys.pdw_table_distribution_properties (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  テーブルの情報の配布を保持します。  
  
|列名|データ型|Description|範囲|  
|-----------------|---------------|-----------------|-----------|  
|**object_id**|**int**|プロパティが指定されている前提とするテーブルの ID。||  
|**distribution_policy**|**tinyint**|0 = UNDEFINED<br /><br /> 1 = なし<br /><br /> 2 = HASH<br /><br /> 3 = REPLICATE<br /><br /> 4 = ROUND_ROBIN|REPLICATE にのみ適用されます[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]です。|  
|**distribution_policy_desc**|**nvarchar(60)**|定義されていないなしでは、ハッシュ、複製、SEGMENTED_HEAP|[!INCLUDE[ssSDW](../../includes/sssdw-md.md)] ハッシュまたは複製を返します。|  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と並列データ ウェアハウスのカタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
