---
title: pdw_table_distribution_properties (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 12/03/2019
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
ms.openlocfilehash: b0e93eebd56579785a2673f4a38846350c737c3f
ms.sourcegitcommit: 01297f2487fe017760adcc6db5d1df2c1234abb4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2020
ms.locfileid: "86196817"
---
# <a name="syspdw_table_distribution_properties-transact-sql"></a>pdw_table_distribution_properties (Transact-sql)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  テーブルの分布情報を保持します。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|**object_id**|**int**|プロパティが指定されたテーブルの ID。||  
|**distribution_policy**|**tinyint**|0 = 未定義<br /><br /> 1 = なし<br /><br /> 2 = ハッシュ<br /><br /> 3 = レプリケート<br /><br /> 4 = ROUND_ROBIN||  
|**distribution_policy_desc**|**nvarchar(60)**|UNDEFINED、NONE、HASH、REPLICATE、ROUND_ROBIN|[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]ハッシュ、ROUND_ROBIN、またはレプリケートを返します。|  
  
## <a name="see-also"></a>関連項目  
 [SQL Data Warehouse and Parallel Data Warehouse Catalog Views (SQL Data Warehouse および Parallel Data Warehouse のカタログ ビュー)](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
