---
title: "SQL Server: Memory Manager オブジェクト | Microsoft Docs"
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
- SQLServer:Memory Manager
- Memory Manager object
ms.assetid: dbf49000-eeb0-4e9c-a361-5092363920dc
caps.latest.revision: 29
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 884e6d05db70f9978b84a3423bdfad748f50b29c
ms.lasthandoff: 04/11/2017

---
# <a name="sql-server-memory-manager-object"></a>SQL Server: Memory Manager オブジェクト
  Microsoft **の** Memory Manager [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトには、全体的なサーバー メモリの使用状況を監視するためのカウンターが用意されています。 全体的なサーバー メモリの使用状況を監視して、ユーザーの利用状況やリソースの使用状況を計測すると、パフォーマンスのボトルネックを突き止めるのに役立つ可能性があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスで使用されるメモリを監視すると、次のことを判断する際に役立ちます。  
  
-   ボトルネックの発生原因が、頻繁にアクセスされるデータをキャッシュに格納するための物理メモリ不足によるものかどうか。 メモリが不足している場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではディスクからデータを取得する必要があります。  
  
-   メモリを増設したり、データ キャッシュや [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の内部構造により多くのメモリを使用できるように設定することで、クエリのパフォーマンスを向上できるかどうか。  
  
## <a name="memory-manager-counters"></a>Memory Manager カウンター  
 次の表では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Memory Manager** カウンターについて説明します。  
  
|SQL Server Memory Manager カウンター|説明|  
|----------------------------------------|-----------------|  
|**Connection Memory (KB)**|接続を維持するためにサーバーが使用している動的メモリの合計サイズを指定します。|  
|**Database Cache Memory (KB)**|サーバーがデータベース ページ キャッシュに現在使用しているメモリの量を指定します。|  
|**メモリの外部の利点**|メモリの外部の値 (ミリ秒/ページ/ミリ秒単位の値に 100 億を掛けて小数点以下を切り捨てたもの)。| 
|**Free Memory (KB)**|サーバーによって使用されていないコミット済みのメモリの量を指定します。|  
|**Granted Workspace Memory (KB)**|ハッシュ、並べ替え、一括コピー、インデックス作成などの操作を実行しているプロセスに現在割り当てられているメモリの合計サイズを指定します。|  
|**Lock Blocks**|サーバーで使用中のロック ブロックの現在数 (定期的に更新されます) を指定します。 ロック ブロックは、テーブル、ページ、行など、ロックされている個々のリソースを表します。|  
|**Lock Blocks Allocated**|現在割り当てられているロック ブロック数を指定します。 サーバー起動時に割り当てられるロック ブロック数と、割り当てられるロック所有者ブロックの数は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Locks** 構成オプションによって決まります。 より多くのロック ブロックが必要な場合は、値が大きくなります。|  
|**Lock Memory (KB)**|ロックのためにサーバーが使用している動的メモリの合計サイズを指定します。|  
|**Lock Owner Blocks**|サーバーで使用中のロック所有者ブロックの現在数 (定期的に更新されます) を指定します。 ロック所有者ブロックは、各スレッドがオブジェクトに設定したロックの所有権を表します。 たとえば、3 つのスレッドがそれぞれ、ページに共有 (S) ロックを所有している場合は、3 つのロック所有者ブロックがあります。|  
|**Lock Owner Blocks Allocated**|現在割り当てられているロック所有者ブロック数を指定します。 サーバー起動時に割り当てられるロック所有者ブロック数と、割り当てられるロック ブロック数は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Locks** 構成オプションによって決まります。 より多くのロック所有者ブロックが必要な場合は、値が動的に大きくなります。|  
|**Log Pool Memory (KB)**|サーバーがログ プールに使用している動的メモリの総容量。| 
|**Maximum Workspace Memory (KB)**|ハッシュ、並べ替え、一括コピー、インデックス作成などの操作を実行しているプロセスが使用できるメモリの最大サイズを示します。|  
|**Memory Grants Outstanding**|ワークスペース メモリを取得できたプロセスの総数を指定します。|  
|**Memory Grants Pending**|ワークスペース メモリ許可を待機しているプロセスの総数を指定します。|  
|**Optimizer Memory (KB)**|サーバーがクエリの最適化のために使用している動的メモリの合計サイズを指定します。|  
|**Reserved Server Memory (KB)**|将来の使用のためにサーバーが予約しているメモリの量を示します。 このカウンターは、 **[Granted Workspace Memory (KB)]**に表示される、最初に許可された現在の未使用メモリ量を示します。|  
|**SQL Cache Memory (KB)**|サーバーが動的 SQL キャッシュのために使用している動的メモリの合計サイズを指定します。|  
|**Stolen Server Memory (KB)**|サーバーがデータベース ページ以外に使用しているメモリの量を指定します。|  
|**Target Server Memory (KB)**|サーバーが使用できるメモリの最適な量を示します。|  
|**Total Server Memory (KB)**|Memory Manager を使用してサーバーがコミットしたメモリの量を指定します。|  
  
## <a name="see-also"></a>参照  
 [リソースの利用状況の監視 &#40;システム モニター&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [SQL Server: Buffer Manager オブジェクト](../../relational-databases/performance-monitor/sql-server-buffer-manager-object.md)   
[sys.dm_os_performance_counters (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql.md)  
  
