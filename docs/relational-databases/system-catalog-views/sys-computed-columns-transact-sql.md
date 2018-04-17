---
title: sys.computed_columns (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
caps.latest.revision: 48
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: e2f0a4113c1688d0fd796945760bdb42e2dcd6de
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="syscomputedcolumns-transact-sql"></a>sys.computed_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  各列内の行が含まれます**sys.columns**は、計算列です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**\<継承された列 >**||**Sys.computed_columns**ビューのすべての列が返されます、 **sys.columns**ビュー。 また、次に示す追加の列も返します。 詳細については、列を**sys.computed_columns**ビューが継承**sys.columns**を参照してください[sys.columns &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)です。 値、 **is_computed**列は常に 1 に設定、 **sys.computed_columns**ビュー。|  
|**definition**|**nvarchar(max)**|計算列を定義する SQL テキスト。|  
|**uses_database_collation**|**bit**|列定義の正しい評価がデータベースの既定の照合順序に依存する場合は 1 になります。それ以外の場合は 0 になります。 このような依存関係は、データベースの既定の照合順序を変更しないようにします。|  
|**is_persisted**|**bit**|計算列が保存されるかどうかを示します。|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
