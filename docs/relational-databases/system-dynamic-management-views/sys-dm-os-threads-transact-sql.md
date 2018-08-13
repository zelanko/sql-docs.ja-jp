---
title: sys.dm_os_threads (TRANSACT-SQL) |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_os_threads_TSQL
- sys.dm_os_threads
- dm_os_threads
- sys.dm_os_threads_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_threads dynamic management view
ms.assetid: a5052701-edbf-4209-a7cb-afc9e65c41c1
caps.latest.revision: 35
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 2109830ba21d60fa67eb33b1b1e5e8b5cb14a8aa
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39543212"
---
# <a name="sysdmosthreads-transact-sql"></a>sys.dm_os_threads (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセスで実行されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オペレーティング システム スレッドの一覧を返します。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して、 **sys.dm_pdw_nodes_os_threads**します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|thread_address|**varbinary(8)**|スレッドのメモリ アドレス (主キー)。|  
|started_by_sqlservr|**bit**|スレッドの開始元。<br /><br /> 1 = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によってスレッドが開始されました。<br /><br /> 0 = 別コンポーネント内から拡張ストアド プロシージャなど、スレッドの開始[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。|  
|os_thread_id|**int**|オペレーティング システムによって割り当てられたスレッドの ID。|  
|status|**int**|内部状態フラグ。|  
|instruction_address|**varbinary(8)**|現在実行されている命令のアドレス。|  
|creation_time|**datetime**|スレッドが作成された日時。|  
|kernel_time|**bigint**|スレッドで使用されたカーネル時間。|  
|usermode_time|**bigint**|スレッドで使用されたユーザー時間。|  
|stack_base_address|**varbinary(8)**|スレッドにおける最上位のスタック アドレスのメモリ アドレス。|  
|stack_end_address|**varbinary(8)**|スレッドにおける最下位のスタック アドレスのメモリ アドレス。|  
|stack_bytes_committed|**int**|スタックでコミットされたバイト数。|  
|stack_bytes_used|**int**|スレッドでアクティブに使用されているバイト数。|  
|affinity|**bigint**|このスレッドが実行されている CPU マスク。 これで構成される値によって異なります、 **ALTER SERVER CONFIGURATION SET PROCESS AFFINITY**ステートメント。 ソフト アフィニティの場合は、スケジューラと異なることがあります。|  
|[Priority]|**int**|スレッドの優先度値。|  
|ロケール|**int**|スレッド用にキャッシュされているロケール LCID。|  
|トークン|**varbinary(8)**|スレッド用にキャッシュされている権限借用トークン ハンドル。|  
|is_impersonating|**int**|スレッドで Win32 権限借用が使用されているかどうかを示します。<br /><br /> 1 = スレッドではプロセスの既定値と異なるセキュリティ資格情報が使用されています。 これは、プロセスを作成したエンティティとは異なるエンティティの権限をスレッドで借用していることを示します。|  
|is_waiting_on_loader_lock|**int**|スレッドでローダー ロックを待機中かどうかを示す、オペレーティング システムの状態。|  
|fiber_data|**varbinary(8)**|スレッドで実行されている現在の Win32 ファイバー。 これは該当する場合に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]簡易プーリング用に構成されています。|  
|thread_handle|**varbinary(8)**|内部使用のみです。|  
|event_handle|**varbinary(8)**|内部使用のみです。|  
|scheduler_address|**varbinary(8)**|スレッドに関連付けられているスケジューラのメモリ アドレス。 詳細については、次を参照してください。 [sys.dm_os_schedulers &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-schedulers-transact-sql.md)します。|  
|worker_address|**varbinary(8)**|スレッドにバインドしているワーカーのメモリ アドレス。 詳細については、次を参照してください。 [sys.dm_os_workers &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md)します。|  
|fiber_context_address|**varbinary(8)**|内部ファイバー コンテキスト アドレス。 これは該当する場合に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]簡易プーリング用に構成されています。|  
|self_address|**varbinary(8)**|内部一貫性ポインター。|  
|processor_group|**smallint**|**適用対象**: [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> プロセッサ グループ ID。|  
|pdw_node_id|**int**|**適用対象**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この配布であるノードの識別子。|  
  
## <a name="permissions"></a>アクセス許可

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]、必要があります`VIEW SERVER STATE`権限。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限。   

## <a name="examples"></a>使用例  
 起動時に、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のスレッドを開始し、それらのスレッドでワーカーを関連付けます。 ただし、拡張ストアド プロシージャなどの外部コンポーネントがでスレッドを開始できます、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]プロセス。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] これらのスレッドの制御できません。 sys.dm_os_threads でリソースを消費する悪意のあるスレッドに関する情報を提供できます、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]プロセス。  
  
 次のクエリはによって開始されなかったスレッドを実行するいると、実行するために使用される時間のワーカーの検索に使用される[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  
  
> [!NOTE]  
>  次のクエリでは、簡略化のため `*` ステートメントでアスタリスク (`SELECT`) を使用していますが、 特にカタログ ビュー、動的管理ビュー、およびシステム テーブル値関数では、アスタリスク (*) を使用しないようにしてください。 将来のアップグレードおよびリリースの[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]列を追加し、これらのビューおよび関数を列の順序を変更する可能性があります。 このような変更により、特定の順序および列数を必要とするアプリケーションが機能しなくなる場合があります。  
  
```  
SELECT *  
  FROM sys.dm_os_threads  
  WHERE started_by_sqlservr = 0;  
```  
  
## <a name="see-also"></a>参照  
  [sys.dm_os_workers &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md)   
 [SQL Server オペレーティング システム関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


