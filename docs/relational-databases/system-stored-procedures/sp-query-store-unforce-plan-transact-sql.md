---
title: "sp_query_store_unforce_plan (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/29/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SP_QUERY_STORE_UNFORCE_PLAN_TSQL
- SP_QUERY_STORE_UNFORCE_PLAN
- SYS.SP_QUERY_STORE_UNFORCE_PLAN
- SYS.SP_QUERY_STORE_UNFORCE_PLAN_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sys.sp_query_store_unforce_plan
- sp_query_store_unforce_plan
ms.assetid: a52f91d0-ff1e-46ad-ba36-b32d9623c9ab
caps.latest.revision: "8"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6808a3d05656f232076ea7d1f4321e136691babd
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spquerystoreunforceplan-transact-sql"></a>sp_query_store_unforce_plan (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  特定のクエリに対して、特定のプランを unforcing を有効にします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_query_store_unforce_plan [ @query_id = ] query_id , [ @plan_id = ] plan_id [;]  
```  
  
## <a name="arguments"></a>引数  
 [  **@query_id =** ] *query_id*  
 クエリの id です。 *query_id*は、 **bigint**、既定値はありません。  
  
 [  **@plan_id =** ] *plan_id*  
 適用されるクエリ プランの id です。 *plan_id*は、 **bigint**、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
  
## <a name="permissions"></a>Permissions  
 必要があります、 **EXECUTE** 、データベースに対する権限と**挿入**、**更新**、および**削除**クエリ ストアのカタログに対する権限表示モード。  
  
## <a name="examples"></a>使用例  
 次の例では、クエリのストアにクエリに関する情報を返します。  
  
```  
SELECT Txt.query_text_id, Txt.query_sql_text, Pl.plan_id, Qry.*  
FROM sys.query_store_plan AS Pl  
JOIN sys.query_store_query AS Qry  
    ON Pl.query_id = Qry.query_id  
JOIN sys.query_store_query_text AS Txt  
    ON Qry.query_text_id = Txt.query_text_id ;  
```  
  
 Query_id と unforce する plan_id を特定した後は、unforce、プランを次の例を使用します。  
  
```  
EXEC sp_query_store_unforce_plan 3, 3;  
```  
  
## <a name="see-also"></a>参照  
 [sp_query_store_force_plan &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql.md)   
 [sp_query_store_remove_plan &#40;です。。 Transct SQL &#41;](../../relational-databases/system-stored-procedures/sp-query-store-remove-plan-transct-sql.md)   
 [sp_query_store_remove_query &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-query-store-remove-query-transact-sql.md)   
 [sp_query_store_reset_exec_stats &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-query-store-reset-exec-stats-transact-sql.md)   
 [sp_query_store_flush_db &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-query-store-flush-db-transact-sql.md)   
 [クエリ ストアのカタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md)   
 [クエリのストアを使用した、パフォーマンスの監視](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)  
  
  
