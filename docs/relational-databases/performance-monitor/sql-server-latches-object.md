---
title: "SQL Server の Latches オブジェクト | Microsoft Docs"
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
- Latches object
- SQLServer:Latches
ms.assetid: 2393ea1c-2bf3-41c3-9f37-b9761144eeca
caps.latest.revision: "23"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c2436c5bc7dc7e4c9acad39acf1697fae5cf3425
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="sql-server-latches-object"></a>SQL Server の Latches オブジェクト
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の **SQLServer:Latches** オブジェクトには、ラッチという内部 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] リソース ロックを監視するためのカウンターがあります。 ユーザーの利用状況とリソース使用率を調べるために行うラッチの監視は、パフォーマンスのボトルネックを特定するために役立つことがあります。  
  
 次の表では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Latches** カウンターについて説明します。  
  
|SQL Server Latches カウンター|Description|  
|---------------------------------|-----------------|  
|**Average Latch Wait Time (ms)**|待機しなければならなかったラッチ要求の平均ラッチ待ち時間 (ミリ秒)。|  
|**Average Latch Wait Time Base**|内部使用のみです。| 
|**Latch Waits/sec**|直ちに許可できなかったラッチ要求の数。|  
|**Number of SuperLatches**|現在の SuperLatch であるラッチの数。|  
|**SuperLatch Demotions/sec**|最後の 1 秒間に通常のラッチに降格された SuperLatch の数。|  
|**SuperLatch Demotions/sec**|最後の 1 秒間に SuperLatch に昇格されたラッチの数。|  
|**Total Latch Wait Time (ms)**|直前のラッチ要求の合計ラッチ待ち時間 (ミリ秒)。|  
  
## <a name="see-also"></a>参照  
 [リソースの利用状況の監視 &#40;システム モニター&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
