---
title: SQL Server、Memory Node | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 55b28ba9-b6d5-4ea9-8103-db8a72f42982
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 32a2296fdb68e640ce8ebfc8dd9cdb351666b337
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63250577"
---
# <a name="sql-server-memory-node"></a>SQL Server、Memory Node
  Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の**Memory Node**オブジェクトには、NUMA ノードのサーバーメモリ使用量を監視するためのカウンターが用意されています。  
  
## <a name="memory-node-counters"></a>Memory Node カウンター  
 次の表では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Memory Node** カウンターについて説明します。  
  
|SQL Server Memory Manager カウンター|[説明]|  
|----------------------------------------|-----------------|  
|**データベースノードメモリ (KB)**|このノードでデータベース ページに現在使用しているメモリの量を指定します。|  
|**空きノードメモリ (KB)**|このノードの未使用のメモリの量を指定します。|  
|**外部ノードメモリ (KB)**|このノードの NUMA ローカル メモリ以外のメモリの量を指定します。|  
|**流用メモリノード (KB)**|このノードでデータベース ページ以外に使用しているメモリの量を指定します。|  
|**ターゲットノードのメモリ**|このノードの理想的なメモリの量を指定します。|  
|**ノードメモリの合計**|サーバーがこのノードでコミットしているメモリの総容量を示します。|  
  
## <a name="see-also"></a>参照  
 [リソース使用状況の監視 &#40;システムモニタ&#41;](monitor-resource-usage-system-monitor.md)   
 [SQL Server、Buffer Manager オブジェクト](sql-server-buffer-manager-object.md)   
 [dm_os_performance_counters &#40;Transact-sql&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql)  
  
  
