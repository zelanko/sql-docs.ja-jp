---
title: sys.dm_exec_sql_text (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 10/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_exec_sql_text
- sys.dm_exec_sql_text
- sys.dm_exec_sql_text_TSQL
- dm_exec_sql_text_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_sql_text dynamic management function
ms.assetid: 61b8ad6a-bf80-490c-92db-58dfdff22a24
caps.latest.revision: 36
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 946ae4dd52cc02d835ad00ba040c9bbb399ea683
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43067915"
---
# <a name="sysdmexecsqltext-transact-sql"></a>sys.dm_exec_sql_text (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  SQL のテキストがされているバッチを返しますが、指定した識別*sql_handle*します。 このテーブル値関数は、システム関数を置き換える**fn_get_sql**します。  
  
 
## <a name="syntax"></a>構文  
  
```  
sys.dm_exec_sql_text(sql_handle | plan_handle)  
```  
  
## <a name="arguments"></a>引数  
*sql_handle*  
検索するバッチの SQL ハンドルを指定します。 *sql_handle*は**varbinary (64)** します。 *sql_handle*次の動的管理オブジェクトから取得できます。  
  
-   [sys.dm_exec_query_stats](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
  
-   [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
-   [sys.dm_exec_cursors](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cursors-transact-sql.md)  
  
-   [sys.dm_exec_xml_handles](../../relational-databases/system-dynamic-management-views/sys-dm-exec-xml-handles-transact-sql.md)  
  
-   [sys.dm_exec_query_memory_grants](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-memory-grants-transact-sql.md)  
  
-   [sys.dm_exec_connections](../../relational-databases/system-dynamic-management-views/sys-dm-exec-connections-transact-sql.md)  
  
*plan_handle*  
キャッシュ内または現在実行中のバッチのクエリ プランを一意に識別します。 *plan_handle*は**varbinary (64)** します。 *plan_handle*次の動的管理オブジェクトから取得できます。  
  
-   [sys.dm_exec_cached_plans](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)  
  
-   [sys.dm_exec_query_stats](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
  
-   [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)   
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**dbid**|**smallint**|データベースの ID。<br /><br /> アドホック SQL ステートメントおよび準備された SQL ステートメントの場合、ステートメントがコンパイルされたデータベースの ID。|  
|**objectid**|**int**|オブジェクトの ID。<br /><br /> アドホック SQL ステートメントおよび準備された SQL ステートメントの場合は NULL になります。|  
|**number**|**smallint**|番号付きストアド プロシージャの場合、ストアド プロシージャの番号。 詳細については、次を参照してください。 [sys.numbered_procedures &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-numbered-procedures-transact-sql.md)します。<br /><br /> アドホック SQL ステートメントおよび準備された SQL ステートメントの場合は NULL になります。|  
|**encrypted**|**bit**|1 = SQL テキストは暗号化されています。<br /><br /> 0 = SQL テキストは暗号化されていません。|  
|**text**|**nvarchar(max** **)**|SQL クエリのテキスト。<br /><br /> 暗号化されているオブジェクトの場合は NULL になります。|  
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する `VIEW SERVER STATE` 権限が必要です。  
  
## <a name="remarks"></a>コメント  
アドホック クエリでは、SQL ハンドルは、サーバーに送信されている SQL テキストに基づくハッシュ値と、任意のデータベースから取得できます。 

ストアド プロシージャ、トリガー、関数などのデータベース オブジェクトでは、SQL ハンドルはデータベース ID、オブジェクト ID、オブジェクト番号から取得します。 

プラン ハンドルは、バッチ全体のコンパイル済みプランから取得したハッシュ値です。 

> [!NOTE]
> **dbid**からは判断できない*sql_handle*アドホック クエリ。 決定**dbid** 、アドホック クエリを使用して*plan_handle*代わりにします。
  
## <a name="examples"></a>使用例 

### <a name="a-conceptual-example"></a>A. 概念の例
渡すことを示すために基本的な例を次に、 **sql_handle** 、直接または**CROSS APPLY**します。
  1.  アクティビティを作成します。  
新しいクエリ ウィンドウで次の T-SQL を実行[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]します。   
      ```sql
      -- Identify current spid (session_id)
      SELECT @@SPID;
      GO
  
      -- Create activity
        WAITFOR DELAY '00:02:00';
      ```
      
    2.  使用して**CROSS APPLY**します。  
    Sql_handle **sys.dm_exec_requests**に渡される**sys.dm_exec_sql_text**を使用して**CROSS APPLY**します。 新しいクエリ ウィンドウを開き、手順 1. で識別される、spid の値を渡します。 この例で、spid の値がある`59`します。

        ```sql
        SELECT t.*
        FROM sys.dm_exec_requests AS r
        CROSS APPLY sys.dm_exec_sql_text(r.sql_handle) AS t
        WHERE session_id = 59 -- modify this value with your actual spid
         ```      
 
    2.  渡す**sql_handle**直接します。  
取得、 **sql_handle**から**sys.dm_exec_requests**します。 次に、渡す、 **sql_handle**に直接**sys.dm_exec_sql_text**します。 新しいクエリ ウィンドウを開きを手順 1. で識別される、spid の値を渡す**sys.dm_exec_requests**します。 この例で、spid の値がある`59`します。 返された渡す**sql_handle**への引数として**sys.dm_exec_sql_text**します。

        ```sql
        -- acquire sql_handle
        SELECT sql_handle FROM sys.dm_exec_requests WHERE session_id = 59  -- modify this value with your actual spid
        
        -- pass sql_handle to sys.dm_exec_sql_text
        SELECT * FROM sys.dm_exec_sql_text(0x01000600B74C2A1300D2582A2100000000000000000000000000000000000000000000000000000000000000) -- modify this value with your actual sql_handle
         ```      
    
  
### <a name="b-obtain-information-about-the-top-five-queries-by-average-cpu-time"></a>B. 平均 CPU 時間の上位 5 クエリに関する情報を取得します。  
 次の例では、上位 5 つのクエリにかかった平均 CPU 時間と SQL ステートメントのテキストを返します。  
  
```sql  
SELECT TOP 5 total_worker_time/execution_count AS [Avg CPU Time],  
    SUBSTRING(st.text, (qs.statement_start_offset/2)+1,   
        ((CASE qs.statement_end_offset  
          WHEN -1 THEN DATALENGTH(st.text)  
         ELSE qs.statement_end_offset  
         END - qs.statement_start_offset)/2) + 1) AS statement_text  
FROM sys.dm_exec_query_stats AS qs  
CROSS APPLY sys.dm_exec_sql_text(qs.sql_handle) AS st  
ORDER BY total_worker_time/execution_count DESC;  
```  
  
### <a name="c-provide-batch-execution-statistics"></a>C. バッチ実行の統計情報を提供します。  
 次の例では、バッチで実行されている SQL クエリのテキストを返し、クエリに関する統計情報を提供します。  
  
```sql  
SELECT s2.dbid,   
    s1.sql_handle,    
    (SELECT TOP 1 SUBSTRING(s2.text,statement_start_offset / 2+1 ,   
      ( (CASE WHEN statement_end_offset = -1   
         THEN (LEN(CONVERT(nvarchar(max),s2.text)) * 2)   
         ELSE statement_end_offset END)  - statement_start_offset) / 2+1))  AS sql_statement,  
    execution_count,   
    plan_generation_num,   
    last_execution_time,     
    total_worker_time,   
    last_worker_time,   
    min_worker_time,   
    max_worker_time,  
    total_physical_reads,   
    last_physical_reads,   
    min_physical_reads,    
    max_physical_reads,    
    total_logical_writes,   
    last_logical_writes,   
    min_logical_writes,   
    max_logical_writes    
FROM sys.dm_exec_query_stats AS s1   
CROSS APPLY sys.dm_exec_sql_text(sql_handle) AS s2    
WHERE s2.objectid is null   
ORDER BY s1.sql_handle, s1.statement_start_offset, s1.statement_end_offset;  
```  
  
## <a name="see-also"></a>関連項目  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [実行関連の動的管理ビューおよび関数&#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_exec_query_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)   
 [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)   
 [sys.dm_exec_cursors &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cursors-transact-sql.md)   
 [sys.dm_exec_xml_handles &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-xml-handles-transact-sql.md)   
 [sys.dm_exec_query_memory_grants &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-memory-grants-transact-sql.md)   
 [使用します。](../../t-sql/queries/from-transact-sql.md#using-apply)   
 [sys.dm_exec_text_query_plan &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-text-query-plan-transact-sql.md)  

