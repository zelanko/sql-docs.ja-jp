---
title: sys.dm_exec_text_query_plan (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 10/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_exec_text_query_plan
- sys.dm_exec_text_query_plan_TSQL
- dm_exec_text_query_plan_TSQL
- sys.dm_exec_text_query_plan
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_text_query_plan dynamic management function
ms.assetid: 9d5e5f59-6973-4df9-9eb2-9372f354ca57
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 5016f6f556967fa45364460280080ca829e521b8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67936882"
---
# <a name="sysdmexectextqueryplan-transact-sql"></a>sys.dm_exec_text_query_plan (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

プラン表示をテキスト形式で返します、[!INCLUDE[tsql](../../includes/tsql-md.md)]バッチまたはバッチ内の特定のステートメント。 クエリ プランでは、プラン ハンドルでできますキャッシュまたは現在実行されているを指定します。 このテーブル値関数に似ています[sys.dm_exec_query_plan &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md)が、次の相違点。  
  
-   クエリ プランの出力がテキスト形式で返される。  
-   クエリ プランの出力は、サイズの制限はありません。  
-   バッチ内の個々 のステートメントを指定することができます。  
  
**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。
  
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
実行されるバッチのクエリ実行プランを一意に識別するトークンと、そのプランがプラン キャッシュ内に存在または現在実行しています。 *plan_handle*は**varbinary (64)** します。   

*Plan_handle*次の動的管理オブジェクトから取得できます。 
  
-   [sys.dm_exec_cached_plans &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)  
  
-   [sys.dm_exec_query_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
  
-   [sys.dm_exec_requests &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  

-   [sys.dm_exec_procedure_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md)  

-   [sys.dm_exec_trigger_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-trigger-stats-transact-sql.md)  
  
*statement_start_offset* | 0 | DEFAULT  
バッチまたは保存されるオブジェクトのテキスト内での、行が示すクエリの開始位置 (バイト単位) を示します。 *statement_start_offset*は**int**します。値 0 は、バッチの先頭を示します。 既定値は 0 です。  
  
ステートメントの開始オフセットは、次の動的管理オブジェクトから取得できます。  
  
-  [sys.dm_exec_query_stats](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
  
-  [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
*statement_end_offset* | -1 | DEFAULT  
バッチまたは保存されるオブジェクトのテキスト内で、行が示すクエリの終了位置をバイト単位で示します。  
  
*statement_start_offset*は**int**します。  
  
値 -1 はバッチの最後を表します。 既定値は -1 です。  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**dbid**|**smallint**|このプランに対応する [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントがコンパイルされたときに有効であったコンテキスト データベースの ID。 アドホック SQL ステートメントおよび準備された SQL ステートメントの場合、ステートメントがコンパイルされたデータベースの ID。<br /><br /> 列が null 値を許容します。|  
|**objectid**|**int**|このクエリ プランのオブジェクト (たとえば、ストアド プロシージャまたはユーザー定義関数) の ID。 アドホックおよび準備されたバッチでは、この列は**null**します。<br /><br /> 列が null 値を許容します。|  
|**number**|**smallint**|番号付きストアド プロシージャの整数。 ための手順のグループなど、**注文**アプリケーションが付けられて**orderproc; 1**、 **orderproc; 2**など。 アドホックおよび準備されたバッチでは、この列は**null**します。<br /><br /> 列が null 値を許容します。|  
|**encrypted**|**bit**|対応するストアド プロシージャを暗号化するかどうかを示します。<br /><br /> 0 = 暗号化されていません。<br /><br /> 1 = 暗号化<br /><br /> 列値が許容されません。|  
|**query_plan**|**nvarchar(max)**|指定されているクエリの実行プランのコンパイル時のプラン表示形式を格納して*plan_handle*します。 プラン表示はテキスト形式です。 含まれているなどのアドホック バッチごとに 1 つのプランが生成された[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメント、ストアド プロシージャの呼び出し、およびユーザー定義関数の呼び出し。<br /><br /> 列が null 値を許容します。|  
  
## <a name="remarks"></a>コメント  
 次の条件では、プラン表示出力が返されない、**プラン**の返されたテーブルの列**sys.dm_exec_text_query_plan**:  
  
-   場合は、クエリ プランを使用して指定*plan_handle*がプラン キャッシュから削除された、 **query_plan**返されるテーブルの列が null です。 プラン ハンドルがキャプチャされた、と共に使用された場合との間の遅延時間がある場合にこの状態が発生するなど、 **sys.dm_exec_text_query_plan**します。  
  
-   いくつか[!INCLUDE[tsql](../../includes/tsql-md.md)]一括操作ステートメントや 8 KB のサイズより大きい文字列リテラルを含むステートメントなど、ステートメントはキャッシュされません。 使用してこのようなステートメントのプラン表示を取得することはできません**sys.dm_exec_text_query_plan**キャッシュが存在しないためです。  
  
-   場合、[!INCLUDE[tsql](../../includes/tsql-md.md)]バッチまたはストアド プロシージャは、ユーザー定義関数への呼び出しやたとえば EXEC を使用して、動的 SQL への呼び出しが含まれます (*文字列*)、XML プラン表示の表に、ユーザー定義関数が含まれていないコンパイルによって返される**sys.dm_exec_text_query_plan**バッチやストアド プロシージャ。 代わりに、別の呼び出しを行う必要があります**sys.dm_exec_text_query_plan**の*plan_handle*ユーザー定義関数に対応します。  
  
アドホック クエリを使用する場合[単純](../../relational-databases/query-processing-architecture-guide.md#SimpleParam)または[強制パラメーター化](../../relational-databases/query-processing-architecture-guide.md#ForcedParam)、 **query_plan**ステートメント テキストのみと実際のクエリ プランではない列が含まれます。 クエリ プランを返すを呼び出す**sys.dm_exec_text_query_plan**準備されたパラメーター化されたクエリのプラン ハンドル。 参照することによって、クエリがパラメーター化されたかどうかを指定できます、 **sql**の列、 [sys.syscacheobjects](../../relational-databases/system-compatibility-views/sys-syscacheobjects-transact-sql.md)ビューまたはの text 列、 [sys.dm_exec_sql_text](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)動的管理ビュー。  
  
## <a name="permissions"></a>アクセス許可  
 実行する**sys.dm_exec_text_query_plan**、ユーザーのメンバーである必要があります、 **sysadmin**固定サーバー ロールまたはサーバーの VIEW SERVER STATE 権限があります。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-retrieving-the-cached-query-plan-for-a-slow-running-transact-sql-query-or-batch"></a>A. 実行速度の遅い TRANSACT-SQL クエリまたはバッチに対するキャッシュされたクエリ プランを取得します。  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリまたは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バッチが、特定の  との接続において長時間実行されている場合は、このクエリやバッチの実行プランを取得して、遅延の原因を調べることができます。 次の例では、実行速度の遅いクエリまたはバッチに対する実行プランを取得する方法を示します。  
  
> [!NOTE]  
> この例を実行するには、値を置き換えます*session_id*と*plan_handle*サーバーに特定の値を使用します。  
  
 まず、`sp_who` ストアド プロシージャを使用して、クエリまたはバッチを実行しているプロセスのサーバー プロセス ID (SPID) を取得します。  
  
```sql  
USE master;  
GO  
EXEC sp_who;  
GO  
```  
  
 によって返される結果セット`sp_who`、spid の値があることを示します`54`します。 `sys.dm_exec_requests` 動的管理ビューで、この SPID を使用して次のクエリを実行すると、プラン ハンドルを取得できます。  
  
```sql  
USE master;  
GO  
SELECT * FROM sys.dm_exec_requests  
WHERE session_id = 54;  
GO  
```  
  
 によって返されるテーブル**sys.dm_exec_requests**実行速度の遅いクエリまたはバッチのプラン ハンドルがあることを示します`0x06000100A27E7C1FA821B10600`します。 次の例は、指定したプラン ハンドルのクエリ プランを返し、既定値 0 および -1 を使用してクエリまたはバッチ内のすべてのステートメントを返します。  
  
```sql  
USE master;  
GO  
SELECT query_plan   
FROM sys.dm_exec_text_query_plan (0x06000100A27E7C1FA821B10600,0,-1);  
GO  
```  
  
### <a name="b-retrieving-every-query-plan-from-the-plan-cache"></a>B. すべてのクエリ プランをプラン キャッシュから取得します。  
 プラン キャッシュにあるすべてのクエリ プランのスナップショットを取得するには、`sys.dm_exec_cached_plans` 動的管理ビューに対してクエリを実行し、キャッシュにあるすべてのクエリ プランのプラン ハンドルを取得します。 プラン ハンドルは、`plan_handle` の `sys.dm_exec_cached_plans` 列に格納されます。 CROSS APPLY 演算子を使用し、プラン ハンドルを渡す`sys.dm_exec_text_query_plan`次のようにします。 プラン表示の出力は、現在プラン キャッシュ内の各プランは、`query_plan`返されるテーブルの列。  
  
```sql  
USE master;  
GO  
SELECT *   
FROM sys.dm_exec_cached_plans AS cp   
CROSS APPLY sys.dm_exec_text_query_plan(cp.plan_handle, DEFAULT, DEFAULT);  
GO  
```  
  
### <a name="c-retrieving-every-query-plan-for-which-the-server-has-gathered-query-statistics-from-the-plan-cache"></a>C. 対象のサーバーは、プラン キャッシュからクエリの統計情報を収集がすべてのクエリ プランを取得します。  
 現在プラン キャッシュにあるクエリ プランのうち、サーバーで統計情報が収集されたすべてのクエリ プランのスナップショットを取得するには、`sys.dm_exec_query_stats` 動的管理ビューに対してクエリを実行し、キャッシュにあるこれらのプランのプラン ハンドルを取得します。 プラン ハンドルは、`plan_handle` の `sys.dm_exec_query_stats` 列に格納されます。 CROSS APPLY 演算子を使用し、プラン ハンドルを渡す`sys.dm_exec_text_query_plan`次のようにします。 各プランのプラン表示出力は、返されるテーブルの `query_plan` 列に格納されます。  
  
```sql  
USE master;  
GO  
SELECT * FROM sys.dm_exec_query_stats AS qs   
CROSS APPLY sys.dm_exec_text_query_plan(qs.plan_handle, qs.statement_start_offset, qs.statement_end_offset);  
GO  
```  
  
### <a name="d-retrieving-information-about-the-top-five-queries-by-average-cpu-time"></a>D. 平均 CPU 時間の上位 5 クエリに関する情報の取得  
 次の例では、上位 5 つのクエリの平均 CPU 時間とクエリ プランを返します。 **Sys.dm_exec_text_query_plan**関数は、既定値 0 およびクエリ プランで、バッチ内のすべてのステートメントを返すには-1 を指定します。  
  
```sql  
SELECT TOP 5 total_worker_time/execution_count AS [Avg CPU Time],  
Plan_handle, query_plan   
FROM sys.dm_exec_query_stats AS qs  
CROSS APPLY sys.dm_exec_text_query_plan(qs.plan_handle, 0, -1)  
ORDER BY total_worker_time/execution_count DESC;  
GO  
```  
  
## <a name="see-also"></a>関連項目  
 [sys.dm_exec_query_plan &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md)  
