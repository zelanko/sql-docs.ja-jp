---
title: SQL Server エージェントの JobSteps オブジェクト | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- JobSteps object
- SQLAgent:JobSteps
ms.assetid: 44f9983c-1753-4fe0-8475-973aa2460b3a
caps.latest.revision: 23
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 4746f6d8cdc836f98d8f2d33369e65af2d111a81
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/16/2018
ms.locfileid: "40411849"
---
# <a name="sql-server-agent-jobsteps-object"></a>SQL Server エージェントの JobSteps オブジェクト
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの **JobSteps** パフォーマンス オブジェクトには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのジョブ ステップについての情報を報告するパフォーマンス カウンターが含まれています。 次の表は、このオブジェクトに含まれているカウンターを示します。  
  
 次の表は、 **SQLAgent:JobSteps** カウンターの一覧です。  
  
|[オブジェクト名]|[説明]|  
|----------|-----------------|  
|**Active steps**|このカウンターは、現在実行中のジョブ ステップの数を報告します。|  
|**Queued steps**|このカウンターは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントで実行する準備が整っているジョブ ステップで、まだ実行が開始されていないジョブ ステップの数を報告します。|  
|**Total Step Retries**|このカウンターは、サーバーを前回再起動してから [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がジョブ ステップを再試行した合計回数を報告します。|  
  
 オブジェクトの各カウンターには、次のインスタンスが含まれています。  
  
|Instance|[説明]|  
|--------------|-----------------|  
|**_Total**|すべてのジョブ ステップの情報です。|  
|**ActiveScripting**|**ActiveScripting** サブシステムを使用するジョブ ステップの情報です。|  
|**ANALYSISCOMMAND**|ANALYSISCOMMAND サブシステムを使用するジョブ ステップの情報です。|  
|**ANALYSISQUERY**|ANALYSISQUERY サブシステムを使用するジョブ ステップの情報です。|  
|**CmdExec**|**CmdExec** サブシステムを使用するジョブ ステップの情報です。|  
|**Distribution**|**Distribution** サブシステムを使用するジョブ ステップの情報です。|  
|**Dts**|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サブシステムを使用するジョブ ステップの情報です。|  
|**LogReader**|**LogReader** サブシステムを使用するジョブ ステップの情報です。|  
|**Merge**|**Merge** サブシステムを使用するジョブ ステップの情報です。|  
|**PowerShell**|**PowerShell** サブシステムを使用するジョブ ステップの情報です。|  
|**QueueReader**|**QueueReader** サブシステムを使用するジョブ ステップの情報です。|  
|**スナップショット**|**Snapshot** サブシステムを使用するジョブ ステップの情報です。|  
|**TSQL**|[!INCLUDE[tsql](../../includes/tsql-md.md)]を実行するジョブ ステップの情報です。|  
  
## <a name="see-also"></a>参照  
 [ジョブ ステップの管理](../../ssms/agent/manage-job-steps.md)   
 [パフォーマンス オブジェクトの使用](../../ssms/agent/use-performance-objects.md)   
 [リソースの利用状況の監視 &#40;システム モニター&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
