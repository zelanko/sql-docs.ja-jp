---
title: "sys.stats_columns (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 12/18/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- stats_columns_TSQL
- stats_columns
- sys.stats_columns
- sys.stats_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.stats_columns catalog view
ms.assetid: 93414d07-97e9-4501-8577-f35b8d68fbe9
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 13114155ad4820ee293acdd11b7833083dafd9fc
ms.sourcegitcommit: c4633058216bcf6748db0eaa0e815761dc98c24d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2017
---
# <a name="sysstatscolumns-transact-sql"></a>sys.stats_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  1 行の一部である各列のデータを含む**sys.stats**統計。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|この列がその一部を構成するオブジェクトの ID です。|  
|**stats_id**|**int**|この列がその一部を構成する統計の ID です。<br /><br />統計、インデックスに対応する場合、 *stats_id*値は同じで、 *index_id*値で、 [sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)カタログ ビューです。|  
|**stats_column_id**|**int**|統計列のセット内の 1 から始まる序数です。|  
|**column_id**|**int**|列の ID **sys.columns**です。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [SQL Server システム カタログに対するクエリに関してよくあるご質問](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
 [統計情報](../../relational-databases/statistics/statistics.md)    
 [sys.dm_db_stats_properties &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-properties-transact-sql.md)   
 [sys.dm_db_stats_histogram &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-histogram-transact-sql.md)   
 [sys.stats &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md)  
  
  
