---
title: sys.pdw_table_distribution_properties (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 639a7475-7c92-41e0-a8ab-ad630eb5aea3
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 8e90ef2298241dd9e59917f2ad6877a6a92b0960
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68001099"
---
# <a name="syspdwtabledistributionproperties-transact-sql"></a>sys.pdw_table_distribution_properties (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  テーブルの情報の配布を保持します。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|**object_id**|**int**|プロパティが指定されている前提とするテーブルの ID。||  
|**distribution_policy**|**tinyint**|0 = 定義されていません。<br /><br /> 1 = なし<br /><br /> 2 = ハッシュ<br /><br /> 3 = レプリケート<br /><br /> 4 = ROUND_ROBIN|REPLICATE にのみ適用されます[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]します。|  
|**distribution_policy_desc**|**nvarchar(60)**|未定義、NONE、ハッシュ、複製、SEGMENTED_HEAP|[!INCLUDE[ssSDW](../../includes/sssdw-md.md)] ハッシュまたは複製を返します。|  
  
## <a name="see-also"></a>関連項目  
 [SQL Data Warehouse と Parallel Data Warehouse カタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
