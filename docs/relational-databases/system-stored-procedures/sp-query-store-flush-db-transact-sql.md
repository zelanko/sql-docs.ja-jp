---
title: "sp_query_store_flush_db (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_query_store_flush_db_TSQL
- sys.sp_query_store_flush_db_TSQL
- sp_query_store_flush_db
- sys.sp_query_store_flush_db
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_query_store_flush_db
- sp_query_store_flush_db
ms.assetid: 580c03ae-57fc-4562-a6bb-5ec89521e38c
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b64f6ccf12dbcf4912fccb374e7efe64c1664bf1
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spquerystoreflushdb-transact-sql"></a>sp_query_store_flush_db (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  クエリのストアのデータのメモリ内の部分をディスクにフラッシュします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_query_store_flush_db [;]  
```  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
  
## <a name="permissions"></a>Permissions  
 必要があります、 **EXECUTE** 、データベースに対する権限と**削除**クエリ ストアのカタログ ビューに対する権限。  
  
## <a name="examples"></a>使用例  
 次の例では、クエリのストアのデータのメモリ内の部分をディスクにフラッシュします。  
  
```  
EXEC sp_query_store_flush_db;  
```  
  
## <a name="see-also"></a>参照  
 [sp_query_store_force_plan &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql.md)   
 [sp_query_store_remove_query &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-query-store-remove-query-transact-sql.md)   
 [sp_query_store_unforce_plan &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql.md)   
 [sp_query_store_reset_exec_stats &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-query-store-reset-exec-stats-transact-sql.md)   
 [sp_query_store_remove_plan &#40;です。。 Transct SQL &#41;](../../relational-databases/system-stored-procedures/sp-query-store-remove-plan-transct-sql.md)   
 [sp_query_store_reset_exec_stats &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-query-store-reset-exec-stats-transact-sql.md)   
 [クエリ ストアのカタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md)   
 [クエリのストアを使用した、パフォーマンスの監視](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)  
  
  
