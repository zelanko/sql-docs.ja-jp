---
title: SQL Server の Latches オブジェクト | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Latches object
- SQLServer:Latches
ms.assetid: 2393ea1c-2bf3-41c3-9f37-b9761144eeca
author: julieMSFT
ms.author: jrasnick
manager: craigg
ms.openlocfilehash: 3cd5db61a2a64f02f0e34b8c2d8fec9dd0c1fa9f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62649591"
---
# <a name="sql-server-latches-object"></a>SQL Server の Latches オブジェクト
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の **SQLServer:Latches** オブジェクトには、ラッチという内部 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] リソース ロックを監視するためのカウンターがあります。 ユーザーの利用状況とリソース使用率を調べるために行うラッチの監視は、パフォーマンスのボトルネックを特定するために役立つことがあります。  
  
 次の表では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Latches** カウンターについて説明します。  
  
|SQL Server Latches カウンター|[説明]|  
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
  
  
