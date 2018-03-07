---
title: "KILL (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/31/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: a96601a65e413d4990e9acb77f49c4724bf7b85c
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="kill-transact-sql"></a>KILL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  セッション ID または作業単位 (UOW) に基づき、ユーザーのプロセスを終了します。 指定したセッション ID または UOW の多くの作業量を元に戻す場合は、KILL ステートメントには、特にときに関係する長いトランザクションのロールバックを完了する時間がかかる場合があります。  
  
 KILL を使用して通常の接続を終了することにより、指定したセッション ID に関連付けられたトランザクションを内部的に終了できます。 ステートメントこともでき、不明な孤立した分散トランザクションを終了するときに[!INCLUDE[msCoName](../../includes/msconame-md.md)]分散トランザクション コーディネーター (MS DTC) が使用されています。  
  
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
 終了するプロセスのセッション ID です。 *セッション ID*一意の整数 (**int**) 接続が行われたときに各ユーザー接続に割り当てられています。 セッション ID の値は、接続の間、接続に関連付けられます。 接続が終了すると、この整数値は解放され、新しい接続に再度割り当てることができます。  
次のクエリを使用して、特定できます、`session_id`を強制終了します。  
 ```sql  
 SELECT conn.session_id, host_name, program_name,
     nt_domain, login_name, connect_time, last_request_end_time 
FROM sys.dm_exec_sessions AS sess
JOIN sys.dm_exec_connections AS conn
    ON sess.session_id = conn.session_id;
```  
  
*UOW*  
**適用されます**: ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 分散トランザクションの作業単位 ID (UOW) を指定します。 *UOW* sys.dm_tran_locks 動的管理ビューの request_owner_guid 列から取得できる GUID です。 *UOW*も取得できます、エラー ログからや MS DTC モニター。 分散トランザクションの監視の詳細については、MS DTC のドキュメントを参照してください。  
  
 KILL を使用して*UOW*を孤立した分散トランザクションを終了します。 これらのトランザクションは、実際のどのセッション ID にも関連付けられていませんが、見かけ上のセッション ID = '-2' に関連付けられています。 sys.dm_tran_locks、sys.dm_exec_sessions、または sys.dm_exec_requests  のいずれかの動的管理ビューのセッション ID 列を照会すれば、孤立したトランザクションをこのセッション ID で容易に識別できます。  
  
 WITH STATUSONLY  
 指定したについての進行状況レポートを生成*セッション ID*または*UOW*をロールバックされて以前の KILL ステートメントです。 KILL WITH STATUSONLY が終了またはロールバックしていない、*セッション ID*または*UOW*;、コマンドには、ロールバックの現在の進行状況のみが表示されます。  
  
## <a name="remarks"></a>解説  
 通常 KILL は、他の重要なプロセスをロックしているプロセスを終了するときに使用されます。また、クエリが重要なシステム リソースを使用しており、プロセスがこのようなクエリを実行している場合、そのプロセスを終了するときにも使用されます。 システム プロセスと拡張ストアド プロシージャを実行しているプロセスは終了できません。  
  
 重要なプロセスを実行している場合は特に、KILL を慎重に使用します。 ユーザー自身のプロセスは終了できません。 他のプロセスを強制終了する必要があります、次のとおりです。  
  
-   AWAITING COMMAND  
-   CHECKPOINT SLEEP  
-   LAZY WRITER  
-   LOCK MONITOR  
-   SIGNAL HANDLER  
  
を使用して@SPIDを現在のセッションのセッション ID 値を表示します。  
  
 使用中のセッション ID 値に関するレポートを取得するには、sys.dm_tran_locks、sys.dm_exec_sessions、および sys.dm_exec_requests  の各動的管理ビューで session_id 列にクエリを実行します。 sp_who システム ストアド プロシージャが返す SPID 列を表示することもできます。 場合、ロールバックが実行中の特定の SPID sp_who 結果内の cmd 列設定の SPID が KILLED/ROLLBACK を示します。  
  
 特定の接続は、データベースのリソースのロックを保持し、別の接続の進行状況をブロック、ブロックしている接続のセッション ID に表示、`blocking_session_id`の列`sys.dm_exec_requests`または`blk`列によって返される`sp_who`です。  
  
 KILL コマンドは、状態が不明な分散トランザクションの解決にも使用できます。 これらのトランザクションは、データベース サーバーまたは MS DTC コーディネーターを予定外に再起動したために生じた未解決の分散トランザクションです。 イン ダウト トランザクションの詳細については、「2 フェーズ コミット」セクションを参照して[関連のデータベースを一貫して復旧 &#40; を使用してマークされたトランザクション完全復旧モデル &#41;](../../relational-databases/backup-restore/use-marked-transactions-to-recover-related-databases-consistently.md).  
  
## <a name="using-with-statusonly"></a>WITH STATUSONLY を使用する  
 KILL WITH STATUSONLY は、セッション ID または UOW が現在ロールバックされている以前の kill 場合にのみにレポートを生成*セッション ID*|*UOW*ステートメントです。 進行状況レポートは、次の形式で、完了したロールバックの進行状況 (% 単位) と予想残り時間 (秒単位) を示します。  
  
 `Spid|UOW <xxx>: Transaction rollback in progress. Estimated rollback completion: <yy>% Estimated time left: <zz> seconds`  
  
 場合は、セッション ID または UOW のロールバックが完了した場合、KILL*セッション ID*|*UOW* WITH STATUSONLY ステートメントを実行すると、セッション ID または UOW がロールバックされていない、KILL場合または*セッション ID*|*UOW* WITH STATUSONLY は、次のエラーを返します。  
  
 ```
"Msg 6120, Level 16, State 1, Line 1"  
"Status report cannot be obtained. Rollback operation for Process ID <session ID> is not in progress."
```  
  
 同じ状態レポートは、同じ KILL を繰り返すことで取得できます*セッション ID*|*UOW* ; WITH STATUSONLY オプションを使用することがなくステートメントただし、お勧めしませんこれを行います。 強制終了を繰り返し*セッション ID*ロールバックが完了すると、新しい KILL ステートメントの実行前にセッション ID は、新しいタスクに再割り当てされました、ステートメントが新しいプロセスを終了する可能性があります。 WITH STATUSONLY を指定すると、このような状況が発生しなくなります。  
  
## <a name="permissions"></a>権限  
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
 次の例は、孤立した分散トランザクションを終了する方法を示しています (セッション ID =-2) で、 *UOW*の`D5499C66-E398-45CA-BF7E-DC9C194B48CF`します。  
  
```sql  
KILL 'D5499C66-E398-45CA-BF7E-DC9C194B48CF';  
```  

  
## <a name="see-also"></a>参照  
 [KILL STATS JOB と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/kill-stats-job-transact-sql.md)   
 [KILL QUERY NOTIFICATION SUBSCRIPTION &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/kill-query-notification-subscription-transact-sql.md)   
 [組み込み関数 &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [シャット ダウン &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/shutdown-transact-sql.md)   
 [@@SPID &#40;Transact-SQL&#41;](../../t-sql/functions/spid-transact-sql.md)   
 [sys.dm_exec_requests &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)   
 [sys.dm_exec_sessions &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)   
 [sys.dm_tran_locks &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql.md)   
 [sp_lock &#40;です。TRANSACT-SQL と&#41;です。](../../relational-databases/system-stored-procedures/sp-lock-transact-sql.md)   
 [sp_who &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md)  
  
  
