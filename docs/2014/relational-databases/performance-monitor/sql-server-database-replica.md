---
title: SQL Server、Database Replica | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- SQLServer:Database Replica
- performance counters [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], performance counters
ms.assetid: a5f6bdce-2b13-4924-aaeb-b50b57d624d8
caps.latest.revision: 25
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ff7159adceda1953433b2869fd5d5e05a0b91b94
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37233112"
---
# <a name="sql-server-database-replica"></a>SQL Server、データベース レプリカ
  **SQLServer:Database Replica** パフォーマンス オブジェクトには、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の AlwaysOn 可用性グループのセカンダリ データベースに関する情報を報告するパフォーマンス カウンターが含まれています。 このオブジェクトは、セカンダリ レプリカをホストする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスでのみ有効です。  
  
|カウンター名|説明|表示|  
|------------------|-----------------|--------------|  
|**受信ファイル バイト数/秒**|セカンダリ データベースのセカンダリ レプリカが最近 1 秒間に受信した FILESTREAM データの量。|セカンダリ レプリカ|  
|**受信ログ バイト数/秒**|データベースのセカンダリ レプリカが最近 1 秒間に受信したログ レコードの量。|セカンダリ レプリカ|  
|**Log remaining for undo**|元に戻すフェーズを完了するためのログの残量 (KB 単位)。|セカンダリ レプリカ|  
|**Log Send Queue**|まだセカンダリ レプリカに送信されていない、プライマリ データベースのログ ファイル内のログ レコードの量 (KB 単位)。 この値は、プライマリ レプリカからセカンダリ レプリカに送信されます。 セカンダリに送信される FILESTREAM ファイルはキューのサイズに含まれません。|セカンダリ レプリカ|  
|**Mirrored Write Transaction/sec**|最後の 1 秒間に、プライマリ データベースに書き込まれたトランザクションのうち、ログがセカンダリ データベースに送信されるまでコミットを待機したトランザクションの数。|プライマリ レプリカ|  
|**Recovery Queue**|まだ再実行されていないセカンダリ レプリカのログ ファイル内のログ レコードの量。|セカンダリ レプリカ|  
|**Redo blocked/sec**|再実行スレッドがデータベースのリーダーで保持されているロックでブロックされる回数。|セカンダリ レプリカ|  
|**Redo Bytes Remaining**|元に戻すフェーズを完了するために再実行されるログの残量 (KB 単位)。|セカンダリ レプリカ|  
|**再適用バイト数/秒**|セカンダリ データベースで最近 1 秒間に再実行されたログ レコードの量。|セカンダリ レプリカ|  
|**Total Log requiring undo**|元に戻す必要のあるログの合計 KB 数。|セカンダリ レプリカ|  
|**Transaction Delay**|終了していないコミットの確認を待機中に生じた遅延 (ミリ秒単位)。|プライマリ レプリカ|  
  
## <a name="see-also"></a>参照  
 [リソースの利用状況の監視 &#40;System Monitor&#41;](monitor-resource-usage-system-monitor.md)   
 [SQL Server、Availability Replica](sql-server-availability-replica.md)   
 [SQL Server、Databases オブジェクト](sql-server-databases-object.md)   
 [AlwaysOn 可用性グループ (SQL Server)](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  
