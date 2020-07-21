---
title: dm_xtp_transaction_stats (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 9d238313d97ff3e509803d284efa3cfd9b8d6a9f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85647977"
---
# <a name="sysdm_xtp_transaction_stats-transact-sql"></a>sys.dm_xtp_transaction_stats (Transact-SQL)
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  サーバーが起動してから実行されたトランザクションに関する統計を報告します。  
  
 詳細については、「[インメモリ OLTP &#40;インメモリ最適化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)」を参照してください。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|total_count|**bigint**|インメモリ OLTP データベースエンジンで実行されたトランザクションの合計数。|  
|read_only_count|**bigint**|読み取り専用トランザクションの数。|  
|total_aborts|**bigint**|ユーザーまたはシステムの中止によって中止されたトランザクションの総数。|  
|user_aborts|**bigint**|システムによって開始された中止の回数。 たとえば、書き込みの競合、検証の失敗、依存関係のエラーなどがあります。|  
|validation_failures|**bigint**|検証エラーによってトランザクションが中止された回数。|  
|dependencies_taken|**bigint**|内部使用のみです。|  
|dependencies_failed|**bigint**|トランザクションが依存していたトランザクションが中止されたためにトランザクションが中止された回数。|  
|savepoint_create|**bigint**|作成されたセーブポイントの数。 ATOMIC ブロックごとに新しいセーブポイントが作成されます。|  
|savepoint_rollbacks|**bigint**|前のセーブポイントにロールバックする回数。|  
|savepoint_refreshes|**bigint**|内部使用のみです。|  
|log_bytes_written|**bigint**|インメモリ OLTP ログレコードに書き込まれた合計バイト数。|  
|log_IO_count|**bigint**|ログ IO を必要とするトランザクションの総数。 持続性のあるテーブルのトランザクションのみを考慮します。|  
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
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="see-also"></a>関連項目  
 [メモリ最適化テーブルの動的管理ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
