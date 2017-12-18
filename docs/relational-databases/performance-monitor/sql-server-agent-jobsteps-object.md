---
title: "SQL Server エージェントの JobSteps オブジェクト | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JobSteps object
- SQLAgent:JobSteps
ms.assetid: 44f9983c-1753-4fe0-8475-973aa2460b3a
caps.latest.revision: "23"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e6d6953a342ab24540da33464962712ea43579f8
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sql-server-agent-jobsteps-object"></a>SQL Server エージェントの JobSteps オブジェクト
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの **JobSteps** パフォーマンス オブジェクトには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのジョブ ステップについての情報を報告するパフォーマンス カウンターが含まれています。 次の表は、このオブジェクトに含まれているカウンターを示します。  
  
 次の表は、 **SQLAgent:JobSteps** カウンターの一覧です。  
  
|名前|説明|  
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
|**Merge**|**Merge** サブシステムを使用するジョブ ステップの情報です。|  
|**PowerShell**|**PowerShell** サブシステムを使用するジョブ ステップの情報です。|  
|**QueueReader**|**QueueReader** サブシステムを使用するジョブ ステップの情報です。|  
|**スナップショット**|**Snapshot** サブシステムを使用するジョブ ステップの情報です。|  
|**TSQL**|[!INCLUDE[tsql](../../includes/tsql-md.md)]を実行するジョブ ステップの情報です。|  
  
## <a name="see-also"></a>参照  
 [ジョブ ステップの管理](http://msdn.microsoft.com/library/51352afc-a0a4-428b-8985-f9e58bb57c31)   
 [パフォーマンス オブジェクトの使用](http://msdn.microsoft.com/library/830b843a-6b2a-4620-a51b-98358e9fc54b)   
 [リソースの利用状況の監視 &#40;システム モニター&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
