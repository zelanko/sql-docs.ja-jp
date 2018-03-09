---
title: "sys.computed_columns (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
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
- sys.computed_columns_TSQL
- sys.computed_columns
- computed_columns_TSQL
- computed_columns
dev_langs:
- TSQL
helpviewer_keywords:
- sys.computed_columns catalog view
ms.assetid: c962c619-e18f-4315-9251-8d9862462299
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d8614fe85f562c9b3ffdbbb10e5451464564b9e2
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="syscomputedcolumns-transact-sql"></a>sys.computed_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  各列内の行が含まれます**sys.columns**は、計算列です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**\<継承された列 >**||**Sys.computed_columns**ビューのすべての列が返されます、 **sys.columns**ビュー。 また、次に示す追加の列も返します。 詳細については、列を**sys.computed_columns**ビューが継承**sys.columns**を参照してください[sys.columns &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md). 値、 **is_computed**列は常に 1 に設定、 **sys.computed_columns**ビュー。|  
|**定義**|**nvarchar(max)**|計算列を定義する SQL テキスト。|  
|**uses_database_collation**|**bit**|列定義の正しい評価がデータベースの既定の照合順序に依存する場合は 1 になります。それ以外の場合は 0 になります。 このような依存関係は、データベースの既定の照合順序を変更しないようにします。|  
|**is_persisted**|**bit**|計算列が保存されるかどうかを示します。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
