---
title: sys.database_event_sessions (Azure SQL データベース) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: system-catalog-views
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: 02c2cd71-d35e-4d4c-b844-92b240f768f4
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 78ae6128ebfdb0b8e255f33fcf4f222d2ad04aa5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysdatabaseeventsessions-azure-sql-database"></a>sys.database_event_sessions (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  現在のデータベース内に存在するすべてのイベント セッション定義を一覧表示[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。  
  
> [!NOTE]  
>  という名前のようなカタログ ビュー`sys.server_event_sessions`にのみ適用されます[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
||  
|-|  
|**適用されます**: [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]、およびそれ以降のバージョンにします。|  
  
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
  
  
