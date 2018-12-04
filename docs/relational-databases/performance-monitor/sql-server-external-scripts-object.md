---
title: SQL Server のExternal Scripts オブジェクト | Microsoft Docs
ms.custom: ''
ms.date: 03/21/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
s.technology: performance
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- External Scripts object
- SQLServer:External Scripts
ms.assetid: 8a75ccce-b174-4937-bc92-8e413b55afe1
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 136abcc97e91424972e67c7e9f49fc872ca77865
ms.sourcegitcommit: ca038f1ef180e4e1b27910bbc5d87822cd1ed176
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2018
ms.locfileid: "52158780"
---
# <a name="sql-server-external-scripts-object"></a>SQL Server のExternal Scripts オブジェクト
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  **の** SQLServer:External Scripts [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトは、外部スクリプトの実行に関連付けられたアクションを監視するカウンターを提供します。 外部スクリプトの実行の詳細については、「[sp_execute_external_script &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)」を参照してください。  
  
 この表では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **External Scripts** のカウンターについて説明します。  
  
|SQL Server External Scripts のカウンター|[説明]|  
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
  
  
