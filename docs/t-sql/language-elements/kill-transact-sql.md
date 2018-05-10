---
title: KILL (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/31/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: t-sql|language-elements
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- KILL_TSQL
- KILL
dev_langs:
- TSQL
helpviewer_keywords:
- WITH STATUSONLY option
- terminating distributed transactions
- distributed transactions [SQL Server], terminating
- in-doubt transactions
- IDs [SQL Server], user processes
- ending distributed transactions [SQL Server]
- stopping distributed transactions
- session IDs [SQL Server]
- system process termination [SQL Server]
- stopping processes
- ending processes [SQL Server]
- UOW [SQL Server]
- orphaned transactions [SQL Server]
- unit of work [SQL Server]
- process termination [SQL Server]
- KILL statement
- terminating process
ms.assetid: 071cf260-c794-4b45-adc0-0e64097938c0
caps.latest.revision: 61
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: d2cf23ffc6cceaf92f80eb75dbe9da1179e9e4a0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="kill-transact-sql"></a>KILL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  セッション ID または作業単位 (UOW) に基づき、ユーザーのプロセスを終了します。 指定したセッション ID または UOW に元に戻す作業が多く含まれている場合など、長いトランザクションをロールバックする場合は、KILL ステートメントの実行に時間がかかることがあります。  
  
 KILL を使用して通常の接続を終了することにより、指定したセッション ID に関連付けられたトランザクションを内部的に終了できます。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 分散トランザクション コーディネーター (MS DTC) を使用している場合は、このステートメントを使用して、状態が不明な孤立したトランザクションをすべて終了することもできます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server  
  
KILL { session ID | UOW } [ WITH STATUSONLY ]   
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
KILL 'session_id'  
[;]   
```  
  
## <a name="arguments"></a>引数  
 *セッション ID*  
 終了するプロセスのセッション ID です。 *セッション ID* は、接続されたときに各ユーザー接続に割り当てられる一意の整数 (**int** 型) です。 セッション ID の値は、接続の間、接続に関連付けられます。 接続が終了すると、この整数値は解放され、新しい接続に再度割り当てることができます。  
次のクエリを使用して、強制終了する `session_id` を識別できます。  
 ```sql  
 SELECT conn.session_id, host_name, program_name,
     nt_domain, login_name, connect_time, last_request_end_time 
FROM sys.dm_exec_sessions AS sess
JOIN sys.dm_exec_connections AS conn
    ON sess.session_id = conn.session_id;
```  
  
*UOW*  
**適用対象**: ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 分散トランザクションの作業単位 ID (UOW) を指定します。 *UOW* は、sys.dm_tran_locks 動的管理ビューの request_owner_guid column から取得できる GUID です。 *UOW* は、エラー ログや MS DTC モニターからも取得できます。 分散トランザクションの監視の詳細については、MS DTC のドキュメントを参照してください。  
  
 KILL *UOW* は、孤立した分散トランザクションを終了する場合に使用できます。 これらのトランザクションは、実際のどのセッション ID にも関連付けられていませんが、見かけ上のセッション ID = '-2' に関連付けられています。 sys.dm_tran_locks、sys.dm_exec_sessions、または sys.dm_exec_requests  のいずれかの動的管理ビューのセッション ID 列を照会すれば、孤立したトランザクションをこのセッション ID で容易に識別できます。  
  
 WITH STATUSONLY  
 以前の KILL ステートメントに従ってロールバックされている、指定した*セッション ID* または *UOW* についての進行状況レポートを生成します。 KILL WITH STATUSONLY は、*セッション ID* や *UOW* を終了またはロールバックしません。ロールバックの現在の進行状況を表示するだけです。  
  
## <a name="remarks"></a>Remarks  
 通常 KILL は、他の重要なプロセスをロックしているプロセスを終了するときに使用されます。また、クエリが重要なシステム リソースを使用しており、プロセスがこのようなクエリを実行している場合、そのプロセスを終了するときにも使用されます。 システム プロセスと拡張ストアド プロシージャを実行しているプロセスは終了できません。  
  
 重要なプロセスが実行している場合は特に、KILL の使用には注意してください。 ユーザー自身のプロセスは終了できません。 また、次のプロセスも終了できません。  
  
-   AWAITING COMMAND  
-   CHECKPOINT SLEEP  
-   LAZY WRITER  
-   LOCK MONITOR  
-   SIGNAL HANDLER  
  
現在のセッションのセッション ID 値を表示するには、@@SPID を使用します。  
  
 使用中のセッション ID 値に関するレポートを取得するには、sys.dm_tran_locks、sys.dm_exec_sessions、および sys.dm_exec_requests  の各動的管理ビューで session_id 列にクエリを実行します。 sp_who システム ストアド プロシージャが返す SPID 列を表示することもできます。 特定の SPID のロールバックが進行中である場合、その SPID に関する sp_who 結果セット内の cmd 列には、KILLED/ROLLBACK が示されます。  
  
 特定の接続がデータベース リソースをロックして別の接続の進行を妨げている場合、`sys.dm_exec_requests` の `blocking_session_id` 列、または `sp_who` が返す `blk` 列に、ブロックしている接続のセッション ID が示されます。  
  
 KILL コマンドは、状態が不明な分散トランザクションの解決にも使用できます。 これらのトランザクションは、データベース サーバーまたは MS DTC コーディネーターを予定外に再起動したために生じた未解決の分散トランザクションです。 未確定トランザクションの詳細については、「[マークされたトランザクションを使用して関連するデータベースを一貫した状態に復元する方法 &#40;完全復旧モデル&#41;](../../relational-databases/backup-restore/use-marked-transactions-to-recover-related-databases-consistently.md)」の「2 フェーズ コミット」を参照してください。  
  
## <a name="using-with-statusonly"></a>WITH STATUSONLY を使用する  
 KILL WITH STATUSONLY は、以前の KILL *session ID*|*UOW* ステートメントに従ってセッション ID または UOW が現在ロールバックされている場合にのみ、レポートを生成します。 進行状況レポートは、次の形式で、完了したロールバックの進行状況 (% 単位) と予想残り時間 (秒単位) を示します。  
  
 `Spid|UOW <xxx>: Transaction rollback in progress. Estimated rollback completion: <yy>% Estimated time left: <zz> seconds`  
  
 KILL *session ID*|*UOW* WITH STATUSONLY ステートメントの実行時にセッション ID または UOW のロールバックが完了している場合、あるいはロールバックするセッション ID または UOW が存在しない場合、KILL *session ID*|*UOW* WITH STATUSONLY は次のエラー メッセージを返します。  
  
 ```
"Msg 6120, Level 16, State 1, Line 1"  
"Status report cannot be obtained. Rollback operation for Process ID <session ID> is not in progress."
```  
  
 WITH STATUSONLY オプションを設定しない状態で同じ KILL  *ID*|*UOW* ステートメントを繰り返すことによって、同じ状態レポートを取得できますが、このような操作は、お勧めできません。 ロールバックが完了しており、新しい KILL ステートメントが実行される前にセッション ID が新しいタスクに再度割り当てられた場合、KILL  *ID* ステートメントの繰り返しによって、新しいプロセスが終了する可能性があります。 WITH STATUSONLY を指定すると、このような状況が発生しなくなります。  
  
## <a name="permissions"></a>アクセス許可  
 **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:** ALTER ANY CONNECTION 権限が必要です。 ALTER ANY CONNECTION は、固定サーバー ロール sysadmin または processadmin のメンバーシップに含まれています。  
  
 **[!INCLUDE[ssSDS](../../includes/sssds-md.md)]:** KILL DATABASE CONNECTION 権限が必要です。 サーバー レベル プリンシパル ログインが、KILL DATABASE CONNECTION です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-kill-to-terminate-a-session"></a>A. KILL を使用してセッションを終了する  
 次の例では、セッション ID が `53` のプロセスを終了します。  
  
```sql  
KILL 53;  
GO  
```  
  
### <a name="b-using-kill-session-id-with-statusonly-to-obtain-a-progress-report"></a>B. KILL セッション ID WITH STATUSONLY を使用して進行状況レポートを取得する  
 次の例では、特定のセッション ID に対するロールバック プロセスの状態を取得します。  
  
```sql  
KILL 54;  
KILL 54 WITH STATUSONLY;  
GO  
  
--This is the progress report.  
spid 54: Transaction rollback in progress. Estimated rollback completion: 80% Estimated time left: 10 seconds.  
```  
  
### <a name="c-using-kill-to-terminate-an-orphaned-distributed-transaction"></a>C. KILL を使用して、孤立した分散トランザクションを終了する  
 次の例では、`D5499C66-E398-45CA-BF7E-DC9C194B48CF` の *UOW* で、孤立した分散トランザクション (セッション ID = -2) を終了する例を示します。  
  
```sql  
KILL 'D5499C66-E398-45CA-BF7E-DC9C194B48CF';  
```  

  
## <a name="see-also"></a>参照  
 [KILL STATS JOB &#40;Transact-SQL&#41;](../../t-sql/language-elements/kill-stats-job-transact-sql.md)   
 [KILL QUERY NOTIFICATION SUBSCRIPTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/kill-query-notification-subscription-transact-sql.md)   
 [組み込み関数 &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [SHUTDOWN &#40;Transact-SQL&#41;](../../t-sql/language-elements/shutdown-transact-sql.md)   
 [@@SPID &#40;Transact-SQL&#41;](../../t-sql/functions/spid-transact-sql.md)   
 [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)   
 [sys.dm_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)   
 [sys.dm_tran_locks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql.md)   
 [sp_lock &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-lock-transact-sql.md)   
 [sp_who &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md)  
  
  
