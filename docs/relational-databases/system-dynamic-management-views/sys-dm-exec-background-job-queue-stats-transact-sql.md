---
title: "sys.dm_exec_background_job_queue_stats (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_exec_background_job_queue_stats
- sys.dm_exec_background_job_queue_stats
- dm_exec_background_job_queue_stats_TSQL
- sys.dm_exec_background_job_queue_stats_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_exec_background_job_queue_stats dynamic management view
ms.assetid: 27f62ab5-46c4-417e-814d-8d6437034d1c
caps.latest.revision: "27"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f586e29f3c091bda3e35a5e46aabeeb8de094aae
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmexecbackgroundjobqueuestats-transact-sql"></a>sys.dm_exec_background_job_queue_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  非同期の (バックグラウンド) 実行に送信されたクエリ プロセッサのジョブごとに、集計統計を提供する 1 行のデータを返します。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して**sys.dm_pdw_nodes_exec_background_job_queue_stats**です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**queue_max_len**|**int**|キューの最大長。|  
|**enqueued_count**|**int**|キューに正常に送信された要求の数。|  
|**started_count**|**int**|実行を開始した要求の数。|  
|**ended_count**|**int**|成功または失敗のどちらかに処理された要求の数。|  
|**failed_lock_count**|**int**|ロックの競合またはデッドロックのために失敗した要求の数。|  
|**failed_other_count**|**int**|その他の理由で失敗した要求の数。|  
|**failed_giveup_count**|**int**|再試行の制限に達したために失敗した要求の数。|  
|**enqueue_failed_full_count**|**int**|キューがいっぱいのため、エンキューの試行に失敗した数。|  
|**enqueue_failed_duplicate_count**|**int**|重複したエンキューの試行の数。|  
|**elapsed_avg_ms**|**int**|要求の平均経過時間 (ミリ秒単位)。|  
|**elapsed_max_ms**|**int**|要求の最長経過時間 (ミリ秒単位)。|  
|**pdw_node_id**|**int**|**適用されます**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この分布はでは、ノードの識別子。|  
  
## <a name="remarks"></a>解説  
 このビューは、統計の非同期更新ジョブに関する情報のみを返します。 統計の非同期更新の詳細については、次を参照してください。[統計](../../relational-databases/statistics/statistics.md)です。  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Premium 階層には、データベースの VIEW DATABASE STATE 権限が必要です。 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Standard および Basic 階層が必要です、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]管理者アカウントです。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-determining-the-percentage-of-failed-background-jobs"></a>A. 失敗したバックグラウンド ジョブの割合を確認する  
 次の例では、実行されたすべてのクエリに対する失敗したバックグラウンド ジョブの割合を返します。  
  
```  
SELECT   
        CASE ended_count WHEN 0   
                THEN 'No jobs ended'   
                ELSE CAST((failed_lock_count + failed_giveup_count + failed_other_count) / CAST(ended_count AS float) * 100 AS varchar(20))   
        END AS [Percent Failed]  
FROM sys.dm_exec_background_job_queue_stats;  
GO  
```  
  
### <a name="b-determining-the-percentage-of-failed-enqueue-attempts"></a>B. 失敗したエンキューの試行の割合を確認する  
 次の例では、実行されたすべてのクエリに対する失敗したエンキューの試行の割合を返します。  
  
```  
SELECT   
        CASE enqueued_count WHEN 0   
                THEN 'No jobs posted'   
                ELSE CAST((enqueue_failed_full_count + enqueue_failed_duplicate_count) / CAST(enqueued_count AS float) * 100 AS varchar(20))   
        END AS [Percent Enqueue Failed]  
FROM sys.dm_exec_background_job_queue_stats;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [実行関連の動的管理ビューおよび関数 &#40;TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  


