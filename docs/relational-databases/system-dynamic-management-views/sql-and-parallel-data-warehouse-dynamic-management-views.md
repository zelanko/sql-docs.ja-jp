---
title: SQL および並列データウェアハウスの動的管理ビュー |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: e713365e-d44c-4b66-84c9-81a1bcc32414
author: stevestein
ms.author: sstein
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 481896da6b53189a7b54f2cb770b0c3a29031d37
ms.sourcegitcommit: af6f66cc3603b785a7d2d73d7338961a5c76c793
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73142739"
---
# <a name="sql-and-parallel-data-warehouse-dynamic-management-views"></a>SQL および Parallel Data Warehouse の動的管理ビュー
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

このトピックでは、[!INCLUDE[ssSDW](../../includes/sssdw-md.md)] および [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] の動的管理ビュー (Dmv) の一覧を示します。  
  
 すべての [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] および [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] Dmv は、 **sys pdw**から開始します。  
  
## <a name="includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd-dynamic-management-views"></a>動的管理ビューの [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] と [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の動的管理ビューは、[!INCLUDE[ssSDW](../../includes/sssdw-md.md)] と [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]の両方に適用されます。  
  
 [_pdw_dms_cores &#40;transact-sql (dm)&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-dms-cores-transact-sql.md)  
  
 [_pdw_dms_external_work &#40;transact-sql (dm)&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-dms-external-work-transact-sql.md)  
  
 [_pdw_dms_workers &#40;transact-sql (dm)&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-dms-workers-transact-sql.md)  
  
 [_pdw_errors &#40;transact-sql (dm)&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md)  
  
 [_pdw_exec_connections &#40;transact-sql (dm)&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-connections-transact-sql.md)  
  
 [_pdw_exec_requests &#40;transact-sql (dm)&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md)  
  
 [_pdw_exec_sessions &#40;transact-sql (dm)&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md)  
  
 [_pdw_hadoop_operations &#40;transact-sql (dm)&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-hadoop-operations-transact-sql.md)  
  
 [_pdw_lock_waits &#40;transact-sql (dm)&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-lock-waits-transact-sql.md)  
  
 [_pdw_nodes &#40;transact-sql (dm)&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md)  
  
 [_pdw_nodes_database_encryption_keys &#40;transact-sql (dm)&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-database-encryption-keys-transact-sql.md)  
  
 [_pdw_os_threads &#40;transact-sql (dm)&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-os-threads-transact-sql.md)  
  
 [_pdw_request_steps &#40;transact-sql (dm)&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md)  
  
 [_pdw_resource_waits &#40;transact-sql (dm)&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-resource-waits-transact-sql.md)  
  
 [_pdw_sql_requests &#40;transact-sql (dm)&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-sql-requests-transact-sql.md)  
  
 [_pdw_sys_info &#40;transact-sql (dm)&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-sys-info-transact-sql.md)  
  
 [_pdw_wait_stats &#40;transact-sql (dm)&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-wait-stats-transact-sql.md)  
  
 [_pdw_waits &#40;transact-sql (dm)&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-waits-transact-sql.md)  

## <a name="sql-data-warehouse-dynamic-management-views"></a>動的管理ビューの SQL Data Warehouse
[_pdw_nodes_exec_query_plan &#40;transact-sql (dm)&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-exec-query-plan-transact-sql.md)  

[_pdw_nodes_exec_query_profiles &#40;transact-sql (dm)&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-exec-query-profiles-transact-sql.md)  

[_pdw_nodes_exec_query_statistics_xml &#40;transact-sql (dm)&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-exec-query-statistics-xml-transact-sql.md)  

[_pdw_nodes_exec_sql &#40;transact-sql (dm)&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-exec-sql-text-transact-sql.md)  

[_pdw_nodes_exec_text_query_plan &#40;transact-sql (dm)&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-exec-text-query-plan-transact-sql.md)  


## <a name="includesspdwincludessspdw-mdmd-dynamic-management-views"></a>動的管理ビューの [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の動的管理ビューは [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] にのみ適用されます。  
  
 [_pdw_component_health_active_alerts &#40;transact-sql (dm)&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-active-alerts-transact-sql.md)  
  
 [_pdw_component_health_alerts &#40;transact-sql (dm)&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-alerts-transact-sql.md)  
  
 [_pdw_component_health_status &#40;transact-sql (dm)&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-status-transact-sql.md)  
  
 [_pdw_diag_processing_stats &#40;transact-sql (dm)&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-diag-processing-stats-transact-sql.md)  
  
 [_pdw_network_credentials &#40;transact-sql (dm)&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-network-credentials-transact-sql.md)  
  
 [_pdw_node_status &#40;transact-sql (dm)&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-node-status-transact-sql.md)  
  
 [_pdw_os_event_logs &#40;transact-sql (dm)&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-os-event-logs-transact-sql.md)  
  
 [_pdw_os_performance_counters &#40;transact-sql (dm)&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-os-performance-counters-transact-sql.md)  
  
 [_pdw_query_stats_xe &#40;transact-sql (dm)&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-query-stats-xe-transact-sql.md)  
  
 [_pdw_query_stats_xe_file &#40;transact-sql (dm)&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-query-stats-xe-file-transact-sql.md)  
  
## <a name="see-also"></a>「  
 [動的管理ビューおよび関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  
