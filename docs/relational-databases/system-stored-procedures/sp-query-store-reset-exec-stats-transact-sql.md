---
title: sp_query_store_reset_exec_stats (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_query_store_reset_exec_stats_TSQL
- sys.sp_query_store_reset_exec_stats_TSQL
- sys.sp_query_store_reset_exec_stats
- sp_query_store_reset_exec_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sp_query_store_reset_exec_stats
- sys.sp_query_store_reset_exec_stats
ms.assetid: 899df1ff-e871-44df-9361-f3b87ac3ea31
caps.latest.revision: 6
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 152a2de5b373c9130f5d2a579737a823b752e832
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33253753"
---
# <a name="spquerystoreresetexecstats-transact-sql"></a>sp_query_store_reset_exec_stats (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  クエリのストアからの特定のクエリ プランの実行時の統計情報をクリアします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_query_store_reset_exec_stats [ @plan_id = ] plan_id [;]  
```  
  
## <a name="arguments"></a>引数  
 [  **@plan_id =** ] *plan_id*  
 消去されているクエリ プランの id です。 *plan_id*は、 **bigint**、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
  
## <a name="permissions"></a>権限  
 必要があります、 **EXECUTE** 、データベースに対する権限と**削除**クエリ ストアのカタログ ビューに対する権限。  
  
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
  
 統計情報をクリアする plan_id を特定した後は、特定のクエリ プランの実行の統計を削除するのに次の例を使用します。 この例では、プラン番号 3 の実行の統計を削除します。  
  
```  
EXEC sp_query_store_reset_exec_stats 3;  
```  
  
## <a name="see-also"></a>参照  
 [sp_query_store_force_plan &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql.md)   
 [sp_query_store_remove_query &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-remove-query-transact-sql.md)   
 [sp_query_store_unforce_plan &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql.md)   
 [sp_query_store_remove_plan &#40;Transct SQL。&#41;](../../relational-databases/system-stored-procedures/sp-query-store-remove-plan-transct-sql.md)   
 [sp_query_store_flush_db &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-flush-db-transact-sql.md)   
 [クエリ ストアのカタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md)   
 [クエリのストアを使用した、パフォーマンスの監視](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)  
  
  
