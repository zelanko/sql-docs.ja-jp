---
title: sys.computed_columns (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f518ac42aa976b6ef99cdcdf91e5d6b7a92fbb4d
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43097074"
---
# <a name="syscomputedcolumns-transact-sql"></a>sys.computed_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  各列内の行が含まれています**sys.columns**は、計算列です。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**\<列を継承 >**||**Sys.computed_columns**ビューは、すべての列を返します、 **sys.columns**ビュー。 また、次に示す追加の列も返します。 列の説明を**sys.computed_columns**ビューが継承**sys.columns**を参照してください[sys.columns &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)します。 値、 **is_computed**列は、常に 1 に設定、 **sys.computed_columns**ビュー。|  
|**definition**|**nvarchar(max)**|計算列を定義する SQL テキスト。|  
|**uses_database_collation**|**bit**|列定義の正しい評価がデータベースの既定の照合順序に依存する場合は 1 になります。それ以外の場合は 0 になります。 このような依存関係は、データベースの既定の照合順序を変更できないようにします。|  
|**is_persisted**|**bit**|計算列が保存されるかどうかを示します。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
