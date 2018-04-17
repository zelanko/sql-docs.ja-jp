---
title: sys.server_event_sessions (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- server_event_sessions
- server_event_sessions_TSQL
- sys.server_event_sessions_TSQL
- sys.server_event_sessions
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_event_sessions catalog view
- xe
ms.assetid: 796f3093-6a3e-4d67-8da6-b9810ae9ef5b
caps.latest.revision: 15
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d667301ca24752c0ea7b723e630c0fe124b8cf6c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sysservereventsessions-transact-sql"></a>sys.server_event_sessions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に存在するすべてのイベント セッションの定義を一覧表示します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|event_session_id|**int**|イベント セッションの一意な ID。 NULL 値は許可されません。|  
|name|**sysname**|イベント セッションを識別するためのユーザー定義の名前。 名前は一意です。 NULL 値は許可されません。|  
|event_retention_mode|**nchar(1)**|イベントの削除の処理方法を決定します。 既定値は S です。NULL 値は許可されません。 次のいずれかを指定します。<br /><br /> S.  マップ event_retention_mode_desc = ALLOW_SINGLE_EVENT_LOSS<br /><br /> M. マップ event_retention_mode_desc = ALLOW_MULTIPLE_EVENT_LOSS<br /><br /> N. マップ event_retention_mode_desc = NO_EVENT_LOSS|  
|event_retention_mode_desc|**sysname**|イベントの削除の処理方法について説明します。 既定値は ALLOW_SINGLE_EVENT_LOSS です。 NULL 値は許可されません。 次のいずれかを指定します。<br /><br /> ALLOW_SINGLE_EVENT_LOSS。 セッションからイベントを削除できます。 1 つのイベントは、すべてのイベント バッファーがいっぱいになる場合にのみ削除されます。 イベント バッファーがいっぱいのときに単独のイベントを削除することで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のパフォーマンス特性が許容可能な状態になり、処理後のイベント ストリームでの損失を最小限に抑えることができます。<br /><br /> ALLOW_MULTIPLE_EVENT_LOSS。 いっぱいのイベント バッファーをセッションから削除できます。 削除されるイベントの数は、セッションに割り当てられているメモリ サイズ、メモリのパーティション分割、およびバッファー内のイベントのサイズによって異なります。 このオプションを使用すると、イベント バッファーがすぐにいっぱいになるときにサーバーのパフォーマンスに与える影響を最小限に抑えることができます。 ただし、多数のイベントがセッションから削除される可能性があります。<br /><br /> NO_EVENT_LOSS。 イベントの削除は許可されません。 このオプションを指定した場合、発生したすべてのイベントが保持されます。 このオプションを使用した場合、イベントを開始するすべてのタスクは、イベント バッファーに空きができるまで待機します。 その結果、イベント セッションがアクティブになっている間、検知できる程度のパフォーマンスの低下が発生する可能性があります。|  
|max_dispatch_latency|**int**|イベントをセッション ターゲットに渡す前にメモリにバッファリングする時間 (ミリ秒単位)。 有効な値は、1 ～ 2147483648 および -1 です。 値 -1 は、ディスパッチ待機時間が無制限であることを示します。 NULL 値が許可されます。|  
|max_memory|**int**|イベントのバッファリング用にセッションに割り当てるメモリの量。 既定値は、4 MB です。 NULL 値が許可されます。|  
|max_event_size|**int**|イベント セッション バッファーに収まらないイベント用に確保するメモリの量。 計算されたバッファー サイズを max_event_size が超える場合、サイズが max_event_size のバッファーが追加で 2 つイベント セッションに割り当てられます。 NULL 値が許可されます。|  
|memory_partition_mode|**nchar(1)**|イベント バッファーを作成するメモリ内の場所。 既定のパーティション モードは G です。NULL 値は許可されません。 memory_partition_mode では、いずれかです。<br /><br /> G : NONE<br /><br /> C : PER_CPU<br /><br /> N : PER_NODE|  
|memory_partition_mode_desc|**sysname**|既定値は NONE です。 NULL 値は許可されません。 次のいずれかを指定します。<br /><br /> NONE。 1 つのバッファー セットが SQL Server インスタンス内で作成されます。<br /><br /> PER_CPU。 各 CPU のバッファー セットが作成されます。<br /><br /> PER_NODE。 NUMA (non-uniform memory access) ノードごとに 1 つのバッファー セットが作成されます。|  
|track_causality|**bit**|因果関係の追跡を有効または無効にします。 1 (ON) に設定した場合、追跡が有効になり、異なるサーバー接続上の関連イベントを相関付けることができます。 既定の設定は 0 (OFF) です。 NULL 値は許可されません。|  
|startup_state|**bit**|サーバーの起動時にセッションを自動的に開始するかどうかを指定する値。 既定値は 0 です。 NULL 値は許可されません。 いずれかです。<br /><br /> 0 (OFF)。 サーバーの起動時にセッションは開始されません。<br /><br /> 1 (ON)。 サーバーの起動時にイベント セッションが開始されます。|  
  
## <a name="permissions"></a>権限  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Extended Events Catalog Views &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/extended-events-catalog-views-transact-sql.md)   
 [拡張イベント](../../relational-databases/extended-events/extended-events.md)  
  
  
