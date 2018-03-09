---
title: "sys.identity_columns (TRANSACT-SQL) |Microsoft ドキュメント"
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
- identity_columns
- sys.identity_columns
- sys.identity_columns_TSQL
- identity_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.identity_columns catalog view
ms.assetid: 97ee01e6-9c9e-4fd9-884b-68b4084669d5
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2669f1373bedec1256d3071b9fe1f85b7c8dab8f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sysidentitycolumns-transact-sql"></a>sys.identity_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  ID 列ごとに 1 行のデータを保持します。  
  
 **Sys.identity_columns**ビューから行を継承する、 **sys.columns**ビュー。 **Sys.identity_columns**ビュー内の列が返されます、 **sys.columns**ビューと**seed_value**、 **increment_value**、 **last_value**、および**is_not_for_replication**列です。 詳細については、「[カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)」を参照してください。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**\<sys.columns から継承された列 >**||**Sys.identity_columns**ビューのすべての列が返されます、 **sys.columns**ビュー。 また、次に示す追加の列も返します。 詳細については、列を**sys.identity_columns**ビューが継承**sys.columns**を参照してください[sys.columns &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md).|  
|**seed_value**|**sql_variant**|この ID 列に対するシード値です。 シード値のデータ型は、列自体のデータ型と同じです。|  
|**increment_value**|**sql_variant**|この ID 列に対する増分値です。 シード値のデータ型は、列自体のデータ型と同じです。|  
|**last_value**|**sql_variant**|この ID 列に対して生成された最後の値です。 シード値のデータ型は、列自体のデータ型と同じです。|  
|**is_not_for_replication**|**bit**|ID 列は NOT FOR REPLICATION と宣言されます。|  
  
> [!NOTE]  
>  複数のテーブルで使用できる自動的に増分する番号、またはテーブルを参照せずにアプリケーションから呼び出すことができる自動的に増分する番号を作成するには、「[シーケンス番号](../../relational-databases/sequence-numbers/sequence-numbers.md)」を参照してください。  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [SQL Server システム カタログに対するクエリに関してよくあるご質問](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
