---
title: sys.dm_xtp_transaction_stats (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_xtp_transaction_stats_TSQL
- dm_xtp_transaction_stats
- sys.dm_xtp_transaction_stats_TSQL
- sys.dm_xtp_transaction_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_xtp_transaction_stats dynamic management view
ms.assetid: 9389f48d-0de5-47bd-9821-4db8f04504e4
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4bf4a371e65a6457453d6a98d37e88a5f8878ba8
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmxtptransactionstats-transact-sql"></a>sys.dm_xtp_transaction_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  サーバーが開始されてから実行されたトランザクションに関する統計を報告します。  
  
 詳細については、「[インメモリ OLTP &#40;インメモリ最適化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)」を参照してください。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|total_count|**bigint**|インメモリ OLTP データベース エンジンで実行されたトランザクションの総数。|  
|read_only_count|**bigint**|読み取り専用トランザクションの数。|  
|total_aborts|**bigint**|ユーザーまたはシステムの中止によって中止されたトランザクションの総数。|  
|user_aborts|**bigint**|システムによって行われた中止の数。 中止の原因には書き込みの競合、検証の失敗、依存関係の失敗などがあります。|  
|validation_failures|**bigint**|検証エラーによるトランザクションの中止の回数。|  
|dependencies_taken|**bigint**|内部使用のみです。|  
|dependencies_failed|**bigint**|依存対象のトランザクションが中止されたことによるトランザクションの中止の回数。|  
|savepoint_create|**bigint**|作成されたセーブポイントの数。 ATOMIC ブロックごとに新しいセーブポイントが作成されます。|  
|savepoint_rollbacks|**bigint**|前のセーブポイントへのロールバックの数。|  
|savepoint_refreshes|**bigint**|内部使用のみです。|  
|log_bytes_written|**bigint**|インメモリ OLTP ログ レコードに書き込まれたバイト数の合計。|  
|log_IO_count|**bigint**|ログ IO を必要とするトランザクションの総数。 持続性のあるテーブルに対するトランザクションのみが考慮されます。|  
|phantom_scans_started|**bigint**|内部使用のみです。|  
|phatom_scans_retries|**bigint**|内部使用のみです。|  
|phantom_rows_touched|**bigint**|内部使用のみです。|  
|phantom_rows_expiring|**bigint**|内部使用のみです。|  
|phantom_rows_expired|**bigint**|内部使用のみです。|  
|phantom_rows_expired_removed|**bigint**|内部使用のみです。|  
|scans_started|**bigint**|内部使用のみです。|  
|scans_retried|**bigint**|内部使用のみです。|  
|rows_returned|**bigint**|内部使用のみです。|  
|rows_touched|**bigint**|内部使用のみです。|  
|rows_expiring|**bigint**|内部使用のみです。|  
|rows_expired|**bigint**|内部使用のみです。|  
|rows_expired_removed|**bigint**|内部使用のみです。|  
|rows_inserted|**bigint**|内部使用のみです。|  
|rows_updated|**bigint**|内部使用のみです。|  
|rows_deleted|**bigint**|内部使用のみです。|  
|write_conflicts|**bigint**|内部使用のみです。|  
|unique_constraint_violations|**bigint**|UNIQUE 制約の違反の総数。|  
  
## <a name="permissions"></a>権限  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [メモリ最適化テーブルの動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
