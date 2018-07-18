---
title: SQL Server、Memory Node | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 55b28ba9-b6d5-4ea9-8103-db8a72f42982
caps.latest.revision: 9
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 59b84d9f1a1f0d305af3c6b522a2b1475eeb1fc9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37211022"
---
# <a name="sql-server-memory-node"></a>SQL Server、Memory Node
  Microsoft **の** Memory Node [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトには、NUMA ノードのサーバー メモリの使用状況を監視するためのカウンターが用意されています。  
  
## <a name="memory-node-counters"></a>Memory Node カウンター  
 次の表では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Memory Node** カウンターについて説明します。  
  
|SQL Server Memory Manager カウンター|説明|  
|----------------------------------------|-----------------|  
|**Database Node Memory (KB)**|このノードでデータベース ページに現在使用しているメモリの量を指定します。|  
|**Free Node Memory (KB)**|このノードの未使用のメモリの量を指定します。|  
|**Foreign Node Memory (KB)**|このノードの NUMA ローカル メモリ以外のメモリの量を指定します。|  
|**Stolen Memory Node (KB)**|このノードでデータベース ページ以外に使用しているメモリの量を指定します。|  
|**Target Node Memory**|このノードの理想的なメモリの量を指定します。|  
|**Total Node Memory**|サーバーがこのノードでコミットしているメモリの総容量を示します。|  
  
## <a name="see-also"></a>参照  
 [リソースの利用状況の監視 &#40;System Monitor&#41;](monitor-resource-usage-system-monitor.md)   
 [SQL Server: Buffer Manager オブジェクト](sql-server-buffer-manager-object.md)   
 [sys.dm_os_performance_counters &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql)  
  
  
