---
title: "DBCC FREEPROCCACHE (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FREEPROCCACHE_TSQL
- FREEPROCCACHE
- DBCC_FREEPROCCACHE_TSQL
- DBCC FREEPROCCACHE
dev_langs:
- TSQL
helpviewer_keywords:
- freeing procedure cache
- removing procedure cache elements
- deleting procedure cache elements
- DBCC FREEPROCCACHE statement
- procedure cache [SQL Server]
- clearing procedure cache
ms.assetid: 0e09d210-6f23-4129-aedb-3d56b2980683
caps.latest.revision: 61
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: bc1321dd91a0fcb7ab76b207301c6302bb3a5e64
ms.openlocfilehash: b91dcf6191f6ec3336c9bf3d3588e8f1daad0867
ms.contentlocale: ja-jp
ms.lasthandoff: 10/06/2017

---
# <a name="dbcc-freeproccache-transact-sql"></a>DBCC FREEPROCCACHE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

プラン キャッシュからすべての要素を削除するか、プラン ハンドルまたは SQL ハンドルを指定して特定のプランを削除するか、指定したリソース プールに関連付けられたすべてのキャッシュ エントリを削除します。

>[!NOTE]
>DBCC FREEPROCCACHE では、ネイティブ コンパイル ストアド プロシージャの実行統計は消去されません。 プロシージャ キャッシュには、ネイティブ コンパイル ストアド プロシージャに関する情報は含まれていません。 プロシージャの実行から収集された実行統計は、実行統計の Dmv に表示されます: [sys.dm_exec_procedure_stats & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md)と[sys.dm_exec_query_plan & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md).  
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
SQL Server の構文:

```sql
DBCC FREEPROCCACHE [ ( { plan_handle | sql_handle | pool_name } ) ] [ WITH NO_INFOMSGS ]  
```  

Azure SQL Data Warehouse と並列データ ウェアハウスの構文:
  
```sql
DBCC FREEPROCCACHE [ ( COMPUTE | ALL ) ] 
     [ WITH NO_INFOMSGS ]   
[;]  
```  
  
## <a name="arguments"></a>引数  
 ({ *plan_handle* | *sql_handle* | *pool_name* })  
 *plan_handle*を既に実行されていて、そのプランがプラン キャッシュに存在するバッチのクエリ プランを一意に識別します。 *plan_handle*は**varbinary (64)**され、次の動的管理オブジェクトから取得できます。  
 -   [sys.dm_exec_cached_plans](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)  
 -   [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
 -   [sys.dm_exec_query_memory_grants](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-memory-grants-transact-sql.md)  
 -   [sys.dm_exec_query_stats](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  

 *sql_handle*が消去されるバッチの SQL ハンドルです。 *sql_handle*は**varbinary (64)**され、次の動的管理オブジェクトから取得できます。  
 -   [sys.dm_exec_query_stats](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
 -   [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
 -   [sys.dm_exec_cursors](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cursors-transact-sql.md)  
 -   [sys.dm_exec_xml_handles](../../relational-databases/system-dynamic-management-views/sys-dm-exec-xml-handles-transact-sql.md)  
 -   [sys.dm_exec_query_memory_grants](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-memory-grants-transact-sql.md)  

 *pool_name*リソース ガバナー リソース プールの名前を指定します。 *pool_name*は**sysname**とクエリを実行して取得できます、 [sys.dm_resource_governor_resource_pools](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md)動的管理ビュー。  
 関連付けるには、リソース ガバナー ワークロード グループをリソース プールに、クエリ、 [sys.dm_resource_governor_workload_groups](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-workload-groups-transact-sql.md)動的管理ビュー。 セッションのワークロード グループについては、クエリ、 [sys.dm_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)動的管理ビュー。  

  
 WITH NO_INFOMSGS  
 すべての情報メッセージを表示しないようにします。  
  
 COMPUTE  
 すべての計算ノードには、クエリ プランのキャッシュを削除します。 これが既定値です。  
  
 ALL  
 各計算ノードおよび [管理] ノードからは、クエリ プランのキャッシュを消去します。  
  
## <a name="remarks"></a>解説  
DBCC FREEPROCCACHE を使用してプラン キャッシュをクリアする際には注意が必要です。 たとえば、プラン キャッシュを解放すると、ストアド プロシージャはキャッシュから再利用されるのではなく、再コンパイルされます。 

これにより、クエリ パフォーマンスが一時的に急激に低下する場合があります。 各キャッシュ ストアが消去、プラン キャッシュ内の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エラー ログには、次の情報メッセージにが含まれます"[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]キャッシュ ストアのために '%s' キャッシュ ストア (プラン キャッシュの一部) のフラッシュを %d 個検出が発生しました ' DBCC。FREEPROCCACHE' または ' DBCC FREESYSTEMCACHE' 操作です"。 このメッセージは、5 分以内にキャッシュがフラッシュされる限り、5 分間隔でログに記録されます。

次の再構成操作でもプロシージャ キャッシュはクリアされます。
-   access check cache bucket count  
-   access check cache quota  
-   clr enabled  
-   cost threshold for parallelism  
-   cross db ownership chaining  
-   index create memory  
-   max degree of parallelism  
-   max server memory  
-   max text repl size  
-   max worker threads  
-   min memory per query  
-   min server memory  
-   query governor cost limit  
-   query wait  
-   remote query timeout  
-   user options  
  
## <a name="result-sets"></a>結果セット  
WITH NO_INFOMSGS 句が指定されていない場合、DBCC FREEPROCCACHE を返します:"DBCC の実行が完了しました。 DBCC がエラー メッセージを出力した場合は、システム管理者に相談してください。"
  
## <a name="permissions"></a>Permissions  
適用されます SQL Server、並列データ ウェアハウス。 

- サーバーに対する ALTER SERVER STATE 権限が必要です。  

適用対象: Azure SQL Data Warehouse
- DB_OWNER 固定サーバー ロールのメンバーシップが必要です。  

## <a name="general-remarks-for-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>全般的な解説[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
複数の DBCC FREEPROCCACHE コマンドは、同時に実行することができます。
[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、クエリ プランのキャッシュをクリアする場合がありますクエリのパフォーマンスの一時的な低下クエリが再コンパイルします。 

DBCC FREEPROCCACHE (コンピューティング) でのみ発生[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンピューティング ノードで実行された場合は、クエリを再コンパイルします。 行われません[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]コントロールのノードで生成される並列クエリ プランを再コンパイルします。
実行中には、DBCC FREEPROCCACHE をキャンセルできます。
  
## <a name="limitations-and-restrictions-for-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>制限事項と制約の[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
DBCC FREEPROCCACHE をトランザクション内で実行できません。
説明文では、DBCC FREEPROCCAHCE はサポートされていません。
  
## <a name="metadata-for-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>メタデータを[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
DBCC FREEPROCCACHE を実行すると、新しい行が sys.pdw_exec_requests システム ビューに追加されます。
  
## <a name="examples-includessnoversionincludesssnoversion-mdmd"></a>例:[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
### <a name="a-clearing-a-query-plan-from-the-plan-cache"></a>A. プラン キャッシュから特定のクエリ プランを削除する  
次の例では、クエリ プラン ハンドルを指定して、プラン キャッシュから特定のクエリ プランを削除します。 まず、この例のクエリがプラン キャッシュに含まれるようにするために、クエリを実行します。 `sys.dm`_`exec` \_ `cached_plans`と`sys.dm` \_ `exec` \_ `sql` \_ `text`動的管理ビューを返すクエリを実行しますクエリのプラン ハンドル。 

結果セットからプラン ハンドルの値が、挿入、`DBCC FREEPROCACHE`プラン キャッシュからそのプランのみを削除するステートメント。
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT * FROM Person.Address;  
GO  
SELECT plan_handle, st.text  
FROM sys.dm_exec_cached_plans   
CROSS APPLY sys.dm_exec_sql_text(plan_handle) AS st  
WHERE text LIKE N'SELECT * FROM Person.Address%';  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]

```
plan_handle                                         text  
--------------------------------------------------  -----------------------------  
0x060006001ECA270EC0215D05000000000000000000000000  SELECT * FROM Person.Address;  
  
(1 row(s) affected)
 ```
 
```sql  
-- Remove the specific plan from the cache.  
DBCC FREEPROCCACHE (0x060006001ECA270EC0215D05000000000000000000000000);  
GO  
```  
  
### <a name="b-clearing-all-plans-from-the-plan-cache"></a>B. プラン キャッシュからすべてのプランを削除する  
次の例では、プラン キャッシュからすべての要素を削除します。 WITH`NO_INFOMSGS`を情報メッセージが表示されていることを防ぐために句を指定します。
  
```sql  
DBCC FREEPROCCACHE WITH NO_INFOMSGS;  
```  
  
### <a name="c-clearing-all-cache-entries-associated-with-a-resource-pool"></a>C. リソース プールに関連付けられたすべてのキャッシュ エントリを削除する  
次の例では、指定したリソース プールに関連付けられているすべてのキャッシュ エントリを削除します。 `sys.dm_resource_governor_resource_pools`ビューが最初の値を取得するクエリを実行*pool_name*です。
  
```sql  
SELECT * FROM sys.dm_resource_governor_resource_pools;  
GO  
DBCC FREEPROCCACHE ('default');  
GO  
```  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-dbcc-freeproccache-basic-syntax-examples"></a>D. DBCC FREEPROCCACHE の基本的な構文の例  
次の例では、コンピューティング ノードからすべての既存のクエリ プラン キャッシュを削除します。 コンテキストを UserDbSales に設定すると、すべてのデータベースのコンピューティング ノードのクエリ プラン キャッシュが削除されます。 WITH NO_INFOMSGS 句では、情報メッセージが結果に表示されることを防ぎます。  
  
```sql
USE UserDbSales;  
DBCC FREEPROCCACHE (COMPUTE) WITH NO_INFOMSGS;  
```  
  
 次の例は、前の例と同じ結果が結果に情報メッセージが表示されます。  
  
```sql
USE UserDbSales;  
DBCC FREEPROCCACHE (COMPUTE);  
```  
  
情報メッセージが要求した、実行が成功したときに、クエリの結果は、コンピューティング ノードごとに 1 行があります。
  
### <a name="e-granting-permission-to-run-dbcc-freeproccache"></a>E. DBCC FREEPROCCACHE を実行する権限を許可します。  
次の例では、David DBCC FREEPROCCACHE を実行するためのアクセス許可のログインを使用できます。  
  
```sql
GRANT ALTER SERVER STATE TO David;  
```  
  
## <a name="see-also"></a>参照  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md)
  
  

