---
title: "SQL Server の Latches オブジェクト | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Latches object
- SQLServer:Latches
ms.assetid: 2393ea1c-2bf3-41c3-9f37-b9761144eeca
caps.latest.revision: 23
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 9a0135aa8d77f14a779d1ecd2325d06efcae5ca8
ms.lasthandoff: 04/11/2017

---
# <a name="sql-server-latches-object"></a>SQL Server の Latches オブジェクト
  Microsoft **の** SQLServer:Latches [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトには、ラッチという内部 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] リソース ロックを監視するためのカウンターがあります。 ユーザーの利用状況とリソース使用率を調べるために行うラッチの監視は、パフォーマンスのボトルネックを特定するために役立つことがあります。  
  
 次の表では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Latches** カウンターについて説明します。  
  
|SQL Server Latches カウンター|説明|  
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
  
  
