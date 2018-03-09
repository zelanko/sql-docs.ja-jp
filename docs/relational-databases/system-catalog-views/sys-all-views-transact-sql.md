---
title: "sys.all_views (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
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
- sys.all_views_TSQL
- sys.all_views
- all_views
- all_views_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.all_views catalog view
ms.assetid: d8829213-fce2-41c6-9ab2-aaab5836c941
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7cd9b1ea568222bc0309048d6c785833f03f14b7
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sysallviews-transact-sql"></a>sys.all_views (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  すべてのユーザー定義ビューとシステム ビューの UNION を表示します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**\<継承された列 >**||このビューが継承する列の一覧は、次を参照してください。 [sys.objects &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).|  
|**is_replicated**|**bit**|1 = ビューはレプリケートされます。|  
|**has_replication_filter**|**bit**|1 = ビューにレプリケーション フィルターがあります。|  
|**has_opaque_metadata**|**bit**|1 = ビューに VIEW_METADATA オプションが指定されています。 詳細については、「[CREATE VIEW &#40;Transact-SQL&#41;](../../t-sql/statements/create-view-transact-sql.md)」を参照してください。|  
|**has_unchecked_assembly_data**|**bit**|1 = テーブルに、前回の ALTER ASSEMBLY で定義が変更されたアセンブリに依存する、持続データが含まれています。 このデータは、DBCC CHECKDB または DBCC CHECKTABLE が次回正常に終了した後、0 にリセットされます。|  
|**with_check_option**|**bit**|1 = WITH CHECK OPTION がビュー定義に指定されています。|  
|**is_date_correlation_view**|**bit**|1 = システムによって、datetime 列間の相関関係情報を格納するビューが自動的に作成されました。 このビューの作成が DATE_CORRELATION_OPTIMIZATION に設定して有効になっている**ON**です。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [DBCC CHECKDB &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)   
 [アセンブリの変更 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-assembly-transact-sql.md)   
 [DBCC CHECKTABLE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checktable-transact-sql.md)  
  
  
