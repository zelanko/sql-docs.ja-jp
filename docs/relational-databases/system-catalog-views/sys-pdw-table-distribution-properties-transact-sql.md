---
title: sys.pdw_table_distribution_properties (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/04/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 639a7475-7c92-41e0-a8ab-ad630eb5aea3
caps.latest.revision: 9
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 459e85209a2839f8bb83add2e595269fb3ef68f8
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="syspdwtabledistributionproperties-transact-sql"></a>sys.pdw_table_distribution_properties (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  テーブルの情報の配布を保持します。  
  
|列名|データ型|Description|範囲|  
|-----------------|---------------|-----------------|-----------|  
|**object_id**|**int**|プロパティが指定されている前提とするテーブルの ID。||  
|**distribution_policy**|**tinyint**|0 = 定義されていません。<br /><br /> 1 = なし<br /><br /> 2 = ハッシュ<br /><br /> 3 レプリケートを =<br /><br /> 4 = ROUND_ROBIN|REPLICATE にのみ適用されます[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]です。|  
|**distribution_policy_desc**|**nvarchar(60)**|定義されていないなしでは、ハッシュ、複製、SEGMENTED_HEAP|[!INCLUDE[ssSDW](../../includes/sssdw-md.md)] ハッシュまたは複製を返します。|  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と並列データ ウェアハウスのカタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
