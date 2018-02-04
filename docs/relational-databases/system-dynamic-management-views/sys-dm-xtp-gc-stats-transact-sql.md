---
title: "sys.dm_xtp_gc_stats (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_xtp_gc_stats
- dm_xtp_gc_stats_TSQL
- sys.dm_xtp_gc_stats_TSQL
- sys.dm_xtp_gc_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_xtp_gc_stats dynamic management view
ms.assetid: 8287d611-50e3-43e1-ba8d-3e3793d3ba0e
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 76269043863211bc0c531cea9ea9a75915e5f6d7
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmxtpgcstats-transact-sql"></a>sys.dm_xtp_gc_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  現在の動作に関する情報 (全体的な統計情報) を提供、[!INCLUDE[hek_2](../../includes/hek-2-md.md)]ガベージ コレクション プロセスです。  
  
 行のガベージ コレクションは、通常のトランザクション処理の一環として、またはガベージ コレクションのメイン スレッド (アイドル ワーカー) によって実行されます。 ガベージ コレクション キューから 1 つの作業項目をデキュー ユーザー トランザクションがコミットされたときに ([sys.dm_xtp_gc_queue_stats &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-xtp-gc-queue-stats-transact-sql.md)). ガベージ コレクションが可能であってもメイン ユーザー トランザクションでアクセスされなかった行のガベージ コレクションは、ダスティ コーナー スキャン (使用頻度が低いインデックスの領域のスキャン) の一環としてアイドル ワーカーによって実行されます。  
  
 詳細については、「[インメモリ OLTP &#40;インメモリ最適化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)」を参照してください。  
  
|列名|型|Description|  
|-----------------|----------|-----------------|  
|rows_examined|**bigint**|サーバーの起動後にガベージ コレクション サブシステムによって検査された行の数。|  
|rows_no_sweep_needed|**bigint**|ダスティ コーナー スキャンを実行せずに削除された行の数。|  
|rows_first_in_bucket|**bigint**|ガベージ コレクションによって検査された、ハッシュ バケットの最初の行であった行の数。|  
|rows_first_in_bucket_removed|**bigint**|ガベージ コレクションによって検査された、削除されているハッシュ バケットの最初の行であった行の数。|  
|rows_marked_for_unlink|**bigint**|ガベージ コレクションによって検査された、ref_count が =0 のインデックスで既に unlinked としてマークされていた行の数。|  
|parallel_assist_count|**bigint**|ユーザー トランザクションで処理された行の数。|  
|idle_worker_count|**bigint**|アイドル ワーカーによって処理されたガベージ行の数。|  
|sweep_scans_started|**bigint**|ガベージ コレクション サブシステムによって実行されたダスティ コーナー スキャンの数。|  
|sweep_scans_retries|**bigint**|ガベージ コレクション サブシステムによって実行されたダスティ コーナー スキャンの数。|  
|sweep_rows_touched|**bigint**|ダスティ コーナー処理によって読み取られた行。|  
|sweep_rows_expiring|**bigint**|ダスティ コーナー処理によって読み取られた、間もなく期限切れになる行。|  
|sweep_rows_expired|**bigint**|ダスティ コーナー処理によって読み取られた、期限切れの行。|  
|sweep_rows_expired_removed|**bigint**|ダスティ コーナー処理によって削除された、期限切れの行。|  
  
## <a name="permissions"></a>権限  
 インスタンスに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="usage-scenario"></a>使用シナリオ  
 以下に出力例を示します。  
  
```  
rows_examined        rows_no_sweep_needed rows_first_in_bucket rows_first_in_bucket_removed  
280085               209512               69905  
rows_first_in_bucket_removed rows_marked_for_unlink parallel_assist_count idle_worker_count  
69905                        0                      8953  
  
idle_worker_count    sweep_scans_started  sweep_scan_retries   sweep_rows_touched  
10306473             670                  0                    1343  
  
sweep_rows_expiring  sweep_rows_expired   sweep_rows_expired_removed  
               0                 673673  
```  
  
## <a name="see-also"></a>参照  
 [メモリ最適化テーブルの動的管理ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
