---
title: SQL Server エージェントの JobSteps オブジェクト | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- JobSteps object
- SQLAgent:JobSteps
ms.assetid: 44f9983c-1753-4fe0-8475-973aa2460b3a
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: b3d0c8197f275801140bec48ab05dc6bc19324eb
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85787387"
---
# <a name="sql-server-agent-jobsteps-object"></a>SQL Server エージェントの JobSteps オブジェクト
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの **JobSteps** パフォーマンス オブジェクトには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのジョブ ステップについての情報を報告するパフォーマンス カウンターが含まれています。 次の表は、このオブジェクトに含まれているカウンターを示します。  
  
 次の表は、 **SQLAgent:JobSteps** カウンターの一覧です。  
  
|Name|説明|  
|----------|-----------------|  
|**Active steps**|このカウンターは、現在実行中のジョブ ステップの数を報告します。|  
|**Queued steps**|このカウンターは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントで実行する準備が整っているジョブ ステップで、まだ実行が開始されていないジョブ ステップの数を報告します。|  
|**Total Step Retries**|このカウンターは、サーバーを前回再起動してから [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がジョブ ステップを再試行した合計回数を報告します。|  
  
 オブジェクトの各カウンターには、次のインスタンスが含まれています。  
  
|インスタンス|説明|  
|--------------|-----------------|  
|**_Total**|すべてのジョブ ステップの情報です。|  
|**ActiveScripting**|**ActiveScripting** サブシステムを使用するジョブ ステップの情報です。|  
|**ANALYSISCOMMAND**|ANALYSISCOMMAND サブシステムを使用するジョブ ステップの情報です。|  
|**ANALYSISQUERY**|ANALYSISQUERY サブシステムを使用するジョブ ステップの情報です。|  
|**CmdExec**|**CmdExec** サブシステムを使用するジョブ ステップの情報です。|  
|**Distribution**|**Distribution** サブシステムを使用するジョブ ステップの情報です。|  
|**Dts**|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サブシステムを使用するジョブ ステップの情報です。|  
|**LogReader**|**LogReader** サブシステムを使用するジョブ ステップの情報です。|  
|**[マージ]**|**Merge** サブシステムを使用するジョブ ステップの情報です。|  
|**PowerShell**|**PowerShell** サブシステムを使用するジョブ ステップの情報です。|  
|**QueueReader**|**QueueReader** サブシステムを使用するジョブ ステップの情報です。|  
|**スナップショット**|**Snapshot** サブシステムを使用するジョブ ステップの情報です。|  
|**TSQL**|[!INCLUDE[tsql](../../includes/tsql-md.md)]を実行するジョブ ステップの情報です。|  
  
## <a name="see-also"></a>参照  
 [ジョブ ステップの管理](../../ssms/agent/manage-job-steps.md)   
 [パフォーマンス オブジェクトの使用](../../ssms/agent/use-performance-objects.md)   
 [リソースの利用状況の監視 &#40;システム モニター&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
