---
title: sys.dm_tran_database_transactions (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/09/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_tran_database_transactions
- sys.dm_tran_database_transactions_TSQL
- dm_tran_database_transactions_TSQL
- sys.dm_tran_database_transactions
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_tran_database_transactions dynamic management view
ms.assetid: 82a44295-4cbc-4a5b-891a-8ebaf307b8f5
caps.latest.revision: 33
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 311dcb091fe7198bc52794b3a7212ed3d8e812c7
ms.sourcegitcommit: 8b332c12850c283ae413e0b04b2b290ac2edb672
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/05/2018
---
# <a name="sysdmtrandatabasetransactions-transact-sql"></a>sys.dm_tran_database_transactions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  データベース レベルのトランザクションに関する情報を返します。  
  
> [!NOTE]  
>  この DMV からの呼び出しに[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して**sys.dm_pdw_nodes_tran_database_transactions**です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|transaction_id|**bigint**|データベース レベルではなくインスタンス レベルのトランザクションの ID。 これはのみインスタンス内のすべてのデータベース間で一意であるが、すべてのサーバー インスタンス間で一意ではありません。|  
|database_id|**int**|トランザクションが関連付けられているデータベースの ID。|  
|database_transaction_begin_time|**datetime**|データベースがトランザクションに参加した時刻。 具体的には、トランザクションのデータベース内にある先頭のログ レコードの時刻になります。|  
|database_transaction_type|**int**|1 = 読み取り/書き込みトランザクション<br /><br /> 2 = 読み取り専用トランザクション<br /><br /> 3 = システム トランザクション|  
|database_transaction_state|**int**|1 = トランザクションは初期化されていません。<br /><br /> 3 =  トランザクションは初期化されていますが、ログ レコードが生成されていません。<br /><br /> 4 = トランザクションではログ レコードが生成されています。<br /><br /> 5 = トランザクションは準備済みです。<br /><br /> 10 = トランザクションはコミットされました。<br /><br /> 11 = トランザクションはロールバックされました。<br /><br /> 12 = トランザクションはコミット中です。 (ログ レコードを生成中ですがいない具体化されたり永続化します。)|  
|database_transaction_status|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|database_transaction_status2|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|database_transaction_log_record_count|**bigint**|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> トランザクションのデータベース内で生成されたログ レコードの数。|  
|database_transaction_replicate_record_count|**int**|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> レプリケートされたトランザクションのデータベースで生成されたログ レコードの数。|  
|database_transaction_log_bytes_used|**bigint**|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> トランザクションのデータベース ログ内でこれまでに使用されたバイト数。|  
|database_transaction_log_bytes_reserved|**bigint**|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> トランザクションのデータベース ログ内で使用するために予約されたバイト数。|  
|database_transaction_log_bytes_used_system|**int**|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> トランザクションの代用となるシステム トランザクションのデータベース ログ内でこれまでに使用されたバイト数。|  
|database_transaction_log_bytes_reserved_system|**int**|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> トランザクションの代用となるシステム トランザクションのデータベース ログ内で使用するために予約されたバイト数。|  
|database_transaction_begin_lsn|**numeric(25,0)**|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> データベース ログ内のトランザクションに対する、開始レコードのログ シーケンス番号 (LSN)。|  
|database_transaction_last_lsn|**numeric(25,0)**|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> データベース ログ内のトランザクションに対して、最後に記録されたレコードの LSN。|  
|database_transaction_most_recent_savepoint_lsn|**numeric(25,0)**|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> データベース ログ内のトランザクションに対する、最後のセーブポイントの LSN。|  
|database_transaction_commit_lsn|**numeric(25,0)**|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> データベース ログ内のトランザクションに対する、コミット ログ レコードの LSN。|  
|database_transaction_last_rollback_lsn|**numeric(25,0)**|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 最後にロールバックされた LSN。 ロールバックが行われていない場合、値は MaxLSN です。|  
|database_transaction_next_undo_lsn|**numeric(25,0)**|**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 元に戻す、次のレコードの LSN。|  
|pdw_node_id|**int**|**適用されます**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この分布はでは、ノードの識別子。|  
  
## <a name="permissions"></a>権限

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限です。   

## <a name="see-also"></a>参照  
 [sys.dm_tran_active_transactions &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-tran-active-transactions-transact-sql.md)   
 [sys.dm_tran_session_transactions &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-tran-session-transactions-transact-sql.md)   
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [トランザクション関連の動的管理ビューおよび関数  &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  


