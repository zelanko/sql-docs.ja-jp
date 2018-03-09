---
title: "SQL Server のExternal Scripts オブジェクト | Microsoft Docs"
ms.custom: 
ms.date: 03/21/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- External Scripts object
- SQLServer:External Scripts
ms.assetid: 8a75ccce-b174-4937-bc92-8e413b55afe1
caps.latest.revision: "7"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fa53d84e29b23d73f73c93641306b11a328fc2e1
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="sql-server-external-scripts-object"></a>SQL Server のExternal Scripts オブジェクト
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  **の** SQLServer:External Scripts [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトは、外部スクリプトの実行に関連付けられたアクションを監視するカウンターを提供します。 外部スクリプトの実行の詳細については、「[sp_execute_external_script &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)」を参照してください。  
  
 この表では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **External Scripts** のカウンターについて説明します。  
  
|SQL Server External Scripts のカウンター|Description|  
|------------------------------------------|-----------------|  
|**Execution Errors**|実行中の外部スクリプトのエラー数。|  
|**Implied Auth.Logins**|黙示的な認証を使用して認証されたサテライトプロセスからのログイン数。|  
|**Parallel Executions**|@parallel = 1 で実行された外部スクリプトの数。|  
|**SQL CC Executions**|SQL Compute Context を使用して実行された外部スクリプトの数。|  
|**Streaming Executions**|@r_rowsPerRead パラメーターで実行された外部スクリプトの数。|  
|**Total Execution Time (ms)**|外部スクリプトの実行にかかった合計時間。|  
|**Total Executions**|実行された外部スクリプトの数。|  
  
## <a name="see-also"></a>参照  
 [リソースの利用状況の監視 &#40;System Monitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [sys.resource_governor_external_resource_pools &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md)   
 [sys.dm_resource_governor_external_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md)  
  
  
