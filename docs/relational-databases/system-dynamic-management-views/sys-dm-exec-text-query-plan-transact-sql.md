---
title: "sys.dm_exec_text_query_plan (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/20/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_exec_text_query_plan
- sys.dm_exec_text_query_plan_TSQL
- dm_exec_text_query_plan_TSQL
- sys.dm_exec_text_query_plan
dev_langs: TSQL
helpviewer_keywords: sys.dm_exec_text_query_plan dynamic management function
ms.assetid: 9d5e5f59-6973-4df9-9eb2-9372f354ca57
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 1bd975dbb78b502df209a6763c6198284f1f5dea
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2018
---
# <a name="sysdmexectextqueryplan-transact-sql"></a>sys.dm_exec_text_query_plan (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  プラン表示のテキストの形式で返します、[!INCLUDE[tsql](../../includes/tsql-md.md)]バッチまたはバッチ内の特定のステートメント。 クエリ プランに指定プラン ハンドルでいずれかのキャッシュまたは現在実行中です。 このテーブル値関数がに似ていますが[sys.dm_exec_query_plan &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md)が次の点で異なります。  
  
-   クエリ プランの出力がテキスト形式で返される。  
  
-   クエリ プランの出力のサイズに制限がない。  
  
-   バッチ内の個々のステートメントを指定できる。  
  
**適用対象:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョンまで](http://go.microsoft.com/fwlink/p/?LinkId=299658))、 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
sys.dm_exec_text_query_plan   
(   
    plan_handle   
    , { statement_start_offset | 0 | DEFAULT }  
        , { statement_end_offset | -1 | DEFAULT }  
)  
```  
  
## <a name="arguments"></a>引数  
*plan_handle*  
キャッシュ内または現在実行中のバッチのクエリ プランを一意に識別します。 *plan_handle*は**varbinary (64)**です。  
  
次の動的管理オブジェクトからプラン ハンドルを取得できます。  
  
-  [sys.dm_exec_cached_plans](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)  
  
-  [sys.dm_exec_query_stats](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
  
-  [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
*statement_start_offset* | 0 |既定値  
バッチまたは保存されるオブジェクトのテキスト内での、行が示すクエリの開始位置 (バイト単位) を示します。 *statement_start_offset*は**int**です。値 0 はバッチの先頭を表します。 既定値は 0 です。  
  
ステートメントの開始オフセットは、次の動的管理オブジェクトから取得できます。  
  
-  [sys.dm_exec_query_stats](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
  
-  [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
*statement_end_offset* |-1 |既定値  
バッチまたは保存されるオブジェクトのテキスト内での、行が示すクエリの終了位置 (バイト単位) を示します。  
  
*statement_start_offset*は**int**です。  
  
値 -1 はバッチの最後を表します。 既定値は、-1 です。  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**dbid**|**smallint**|このプランに対応する [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントがコンパイルされたときに有効であったコンテキスト データベースの ID。 アドホック SQL ステートメントおよび準備された SQL ステートメントの場合、ステートメントがコンパイルされたデータベースの ID。<br /><br /> 列は、null 値は。|  
|**objectid**|**int**|ストアド プロシージャやユーザー定義関数など、クエリ プランのオブジェクトの ID。 アドホックおよび準備されたバッチでは、この列は**null**です。<br /><br /> 列は、null 値は。|  
|**数**|**smallint**|ストアド プロシージャに付けられた番号 (整数)。 用のプロシージャのグループなど、 **orders**アプリケーションが付けられて**orderproc; 1**、 **orderproc; 2**のようにします。 アドホックおよび準備されたバッチでは、この列は**null**です。<br /><br /> 列は、null 値は。|  
|**暗号化**|**bit**|対応するプロシージャが暗号化されているかどうか。<br /><br /> 0 = 暗号化されていません。<br /><br /> 1 = 暗号化<br /><br /> 列値が許容されません。|  
|**query_plan**|**nvarchar(max)**|指定されたクエリ実行プランのコンパイル時のプラン表示を含む*plan_handle*です。 プラン表示はテキスト形式です。 含む、たとえばアドホック バッチごとの 1 つのプランが生成された[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメント、ストアド プロシージャの呼び出し、およびユーザー定義関数の呼び出しです。<br /><br /> 列は、null 値は。|  
  
## <a name="remarks"></a>解説  
 次の条件では、プラン表示出力は返されません内、**プラン**返されるテーブルの列**sys.dm_exec_text_query_plan**:  
  
-   使用して指定したクエリ プランする場合*plan_handle*がプラン キャッシュから削除された、 **query_plan**返されるテーブルの列が null です。 プラン ハンドルがキャプチャされ、と共に使用された場合の間の遅延時間がある場合にこの状態が発生するなど、 **sys.dm_exec_text_query_plan**です。  
  
-   いくつか[!INCLUDE[tsql](../../includes/tsql-md.md)]一括操作ステートメントや文字列リテラルのサイズは 8 KB を超えるを含むステートメントなど、ステートメントはキャッシュされません。 使用してこのようなステートメントのプラン表示を取得できません**sys.dm_exec_text_query_plan**キャッシュが存在しないためです。  
  
-   場合、[!INCLUDE[tsql](../../includes/tsql-md.md)]バッチまたはストアド プロシージャは、ユーザー定義関数への呼び出しやたとえば EXEC を使用して、動的 SQL への呼び出しが含まれます (*文字列*) では、XML プラン表示の表に、ユーザー定義関数が含まれていないに関するコンパイル済みのによって返される**sys.dm_exec_text_query_plan**バッチやストアド プロシージャのです。 代わりに、別の呼び出しを行う必要があります**sys.dm_exec_text_query_plan**の*plan_handle*ユーザー定義関数に対応します。  
  
アドホック クエリを使用する場合[単純](../../relational-databases/query-processing-architecture-guide.md#SimpleParam)または[強制パラメーター化](../../relational-databases/query-processing-architecture-guide.md#ForcedParam)、 **query_plan**ステートメント テキストのみと、実際のクエリ プランではない列が含まれます。 クエリ プランを返すを呼び出す**sys.dm_exec_text_query_plan**の準備されたパラメーター化クエリのプラン ハンドル。 参照することによって、クエリがパラメーター化されたかどうかを決定できます、 **sql**の列、 [sys.syscacheobjects](../../relational-databases/system-compatibility-views/sys-syscacheobjects-transact-sql.md)ビューまたはの text 列、 [sys.dm_exec_sql_text](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)動的管理ビュー。  
  
## <a name="permissions"></a>アクセス許可  
 実行する**sys.dm_exec_text_query_plan**、ユーザーのメンバーである必要があります、 **sysadmin**固定サーバー ロールまたはサーバーの VIEW SERVER STATE 権限を持っています。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-retrieving-the-cached-query-plan-for-a-slow-running-transact-sql-query-or-batch"></a>A. キャッシュされたクエリ プランの実行速度の遅い TRANSACT-SQL クエリまたはバッチを取得します。  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリまたは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バッチが、特定の  との接続において長時間実行されている場合は、このクエリやバッチの実行プランを取得して、遅延の原因を調べることができます。 次の例では、実行速度の遅いクエリまたはバッチのプラン表示を取得する方法を示します。  
  
> [!NOTE]  
> 実行するには次の例の値に置き換えて*session_id*と*plan_handle*をサーバーに固有の値にします。  
  
 まず、`sp_who` ストアド プロシージャを使用して、クエリまたはバッチを実行しているプロセスのサーバー プロセス ID (SPID) を取得します。  
  
```sql  
USE master;  
GO  
EXEC sp_who;  
GO  
```  
  
 によって返される結果セットは`sp_who`、spid の値があることを示します`54`です。 `sys.dm_exec_requests` 動的管理ビューで、この SPID を使用して次のクエリを実行すると、プラン ハンドルを取得できます。  
  
```sql  
USE master;  
GO  
SELECT * FROM sys.dm_exec_requests  
WHERE session_id = 54;  
GO  
```  
  
 によって返されるテーブル**sys.dm_exec_requests**実行速度の遅いクエリまたはバッチのプラン ハンドルがあることを示します`0x06000100A27E7C1FA821B10600`です。 次の例は、指定したプラン ハンドルのクエリ プランを返し、既定値 0 および -1 を使用してクエリまたはバッチ内のすべてのステートメントを返します。  
  
```sql  
USE master;  
GO  
SELECT query_plan   
FROM sys.dm_exec_text_query_plan (0x06000100A27E7C1FA821B10600,0,-1);  
GO  
```  
  
### <a name="b-retrieving-every-query-plan-from-the-plan-cache"></a>B. プラン キャッシュからすべてのクエリ プランを取得する  
 プラン キャッシュにあるすべてのクエリ プランのスナップショットを取得するには、`sys.dm_exec_cached_plans` 動的管理ビューに対してクエリを実行し、キャッシュにあるすべてのクエリ プランのプラン ハンドルを取得します。 プラン ハンドルは、`plan_handle` の `sys.dm_exec_cached_plans` 列に格納されます。 CROSS APPLY 演算子を使用して、プラン ハンドルを渡す`sys.dm_exec_text_query_plan`次のようにします。 プラン表示の出力は、現在プラン キャッシュにある各プランは、`query_plan`返されるテーブルの列です。  
  
```sql  
USE master;  
GO  
SELECT *   
FROM sys.dm_exec_cached_plans AS cp   
CROSS APPLY sys.dm_exec_text_query_plan(cp.plan_handle, DEFAULT, DEFAULT);  
GO  
```  
  
### <a name="c-retrieving-every-query-plan-for-which-the-server-has-gathered-query-statistics-from-the-plan-cache"></a>C. サーバーで収集されたクエリ統計情報に関連するすべてのクエリ プランをプラン キャッシュから取得する  
 現在プラン キャッシュにあるクエリ プランのうち、サーバーで統計情報が収集されたすべてのクエリ プランのスナップショットを取得するには、`sys.dm_exec_query_stats` 動的管理ビューに対してクエリを実行し、キャッシュにあるこれらのプランのプラン ハンドルを取得します。 プラン ハンドルは、`plan_handle` の `sys.dm_exec_query_stats` 列に格納されます。 CROSS APPLY 演算子を使用して、プラン ハンドルを渡す`sys.dm_exec_text_query_plan`次のようにします。 各プランのプラン表示出力は、返されるテーブルの `query_plan` 列に格納されます。  
  
```sql  
USE master;  
GO  
SELECT * FROM sys.dm_exec_query_stats AS qs   
CROSS APPLY sys.dm_exec_text_query_plan(qs.plan_handle, qs.statement_start_offset, qs.statement_end_offset);  
GO  
```  
  
### <a name="d-retrieving-information-about-the-top-five-queries-by-average-cpu-time"></a>D. 平均 CPU 時間ごとの上位 5 つのクエリに関する情報を取得します。  
 次の例では、上位 5 つのクエリにかかった平均 CPU 時間とクエリ プランを返します。 **Sys.dm_exec_text_query_plan**関数は、既定値 0 およびクエリ プランのバッチ内のすべてのステートメントを返すには-1 を指定します。  
  
```sql  
SELECT TOP 5 total_worker_time/execution_count AS [Avg CPU Time],  
Plan_handle, query_plan   
FROM sys.dm_exec_query_stats AS qs  
CROSS APPLY sys.dm_exec_text_query_plan(qs.plan_handle, 0, -1)  
ORDER BY total_worker_time/execution_count DESC;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sys.dm_exec_query_plan &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md)  
