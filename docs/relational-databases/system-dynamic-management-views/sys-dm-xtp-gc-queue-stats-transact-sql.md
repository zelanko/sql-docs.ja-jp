---
title: sys.dm_xtp_gc_queue_stats (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/02/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_xtp_gc_stats
- dm_xtp_gc_stats_TSQL
- sys.dm_xtp_gc_stats_TSQL
- sys.dm_xtp_gc_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_xtp_gc_stats dynamic management view
ms.assetid: addef774-318d-46a7-85df-f93168a800cb
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 893a7208566b727b20a89bae63ac86b3a063e6b8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmxtpgcqueuestats-transact-sql"></a>sys.dm_xtp_gc_queue_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  サーバー上の各ガベージ コレクション ワーカー キューに関する情報およびそれぞれに関する各種統計を出力します。 これは、論理 CPU ごとの 1 つのキューです。  
  
 ガベージ コレクションのメイン スレッド (アイドル スレッド) は、ガベージ コレクションのメイン スレッドが前回呼び出されてから完了したすべてのトランザクションについて、更新、削除、および挿入された行を追跡します。 ガベージ コレクション スレッドは、起動すると、最も古いアクティブなトランザクションのタイムスタンプが変化しているかどうかを判断します。 最も古いアクティブなトランザクションが変化した場合は、アイドル スレッドにより、書き込みセットが不要になったトランザクションの作業項目が (16 行ごとのチャンクで) エンキューされます。 たとえば、1,024 行を削除すると、64 のガベージ コレクション作業項目がエンキューされます (1 つの作業項目には削除された 16 行が含まれています)。  ユーザー トランザクションがコミットされると、スケジューラでエンキューされたすべての項目が選択されます。 スケジューラにエンキューされた項目がない場合、ユーザー トランザクションは、現在の NUMA ノードでキューを検索します。  
  
 sys.dm_xtp_gc_queue_stats を実行してエンキューされた作業が処理されているかどうかを確認することにより、削除された行についてガベージ コレクションでメモリが解放されるかどうかを確認できます。 Current_queue_depth のエントリが処理されていない場合、または current_queue_depth を新しい作業項目を追加しない場合は、これはガベージ コレクションがメモリを解放していないことを示します。 たとえば、実行時間が長いトランザクションが存在する場合、ガベージ コレクションは実行できません。  
  
 詳細については、「[インメモリ OLTP &#40;インメモリ最適化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)」を参照してください。  
  

|列名|型|Description|  
|-----------------|----------|-----------------|  
|queue_id|**int**|キューの一意の識別子。|  
|total_enqueues|**bigint**|サーバーが起動してからこのキューにエンキューされたガベージ コレクションの作業項目の総数。|  
|total_dequeues|**bigint**|サーバーが起動してからこのキューからデキューされたガベージ コレクションの作業項目の総数。|  
|current_queue_depth|**bigint**|現在このキューにあるガベージ コレクションの作業項目の数。 このアイテムは場合によっては 1 つ以上がガベージ コレクションの対象であることを示します。|  
|maximum_queue_depth|**bigint**|このキューに同時に存在した最大項目数。|  
|last_service_ticks|**bigint**|キューが最後に処理された時点における CPU のティック。|  
  
## <a name="permissions"></a>権限  
 VIEW SERVER STATE 権限が必要です。  
  
## <a name="user-scenario"></a>ユーザー シナリオ  
 この出力は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が 4 コアで実行中か、または、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスが 4 コアに関連付けられていることを示しています。  
  
 この出力は、処理する作業項目がキューにないことを示しています。 キュー 0 の場合、SQL の起動後、キューから削除された作業項目が合計 15625 で、キューの最大項目数は 215625 に設定されています。  
  
```  
queue_id total_enqueues total_dequeues current_queue_depth  maximum_queue_depth  last_service_ticks  
----------------------------------------------------------------------------------------------------  
0        15625                15625    0                    15625                1233573168347  
1        15625                15625    0                    15625                1234123295566  
2        15625                15625    0                    15625                1233569418146  
3        15625                15625    0                    15625                1233571605761  
```  
  
## <a name="see-also"></a>参照  
 [メモリ最適化テーブルの動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
