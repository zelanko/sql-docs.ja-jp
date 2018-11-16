---
title: sys.dm_exec_query_plan (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 08/02/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_exec_query_plan_TSQL
- sys.dm_exec_query_plan
- dm_exec_query_plan
- sys.dm_exec_query_plan_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_plan dynamic management function
ms.assetid: e26f0867-9be3-4b2e-969e-7f2840230770
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1167762e9d623aa3de04db38f67ee02f3551763d
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51671198"
---
# <a name="sysdmexecqueryplan-transact-sql"></a>sys.dm_exec_query_plan (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  プラン ハンドルで指定されたバッチのプラン表示を XML 形式で返します。 プラン ハンドルで指定するプランは、キャッシュ内のもの、または現在実行中のものを指定できます。  
  
 プラン表示の XML スキーマは公開されてで使用可能な[この Microsoft Web サイト](https://go.microsoft.com/fwlink/?linkid=43100&clcid=0x409)します。 また、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がインストールされているディレクトリからも入手できます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.dm_exec_query_plan ( plan_handle )  
```  
  
## <a name="arguments"></a>引数  
 *plan_handle*  
 キャッシュ内または現在実行中のバッチのクエリ プランを一意に識別します。  
  
 *plan_handle*は**varbinary (64)** します。 *plan_handle*次の動的管理オブジェクトから取得できます。  
  
 [sys.dm_exec_cached_plans](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)  
  
 [sys.dm_exec_query_stats](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
  
 [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**dbid**|**smallint**|このプランに対応する [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントがコンパイルされたときに有効であったコンテキスト データベースの ID。 アドホック SQL ステートメントおよび準備された SQL ステートメントの場合、ステートメントがコンパイルされたデータベースの ID。<br /><br /> 列が null 値を許容します。|  
|**objectid**|**int**|ストアド プロシージャやユーザー定義関数など、クエリ プランのオブジェクトの ID。 アドホックおよび準備されたバッチでは、この列は**null**します。<br /><br /> 列が null 値を許容します。|  
|**number**|**smallint**|ストアド プロシージャに付けられた番号 (整数)。 ための手順のグループなど、**注文**アプリケーションが付けられて**orderproc; 1**、 **orderproc; 2**など。 アドホックおよび準備されたバッチでは、この列は**null**します。<br /><br /> 列が null 値を許容します。|  
|**encrypted**|**bit**|対応するプロシージャが暗号化されているかどうか。<br /><br /> 0 = 暗号化されていません。<br /><br /> 1 = 暗号化<br /><br /> 列値が許容されません。|  
|**query_plan**|**xml**|指定されているクエリの実行プランのコンパイル時のプラン表示形式を格納して*plan_handle*します。 プラン表示は XML 形式です。 アドホック [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメント、ストアド プロシージャ コール、ユーザー定義関数コールなどを含むバッチごとに、1 つのプランが生成されます。<br /><br /> 列が null 値を許容します。|  
  
## <a name="remarks"></a>コメント  
 次の条件では、プラン表示出力が返されない、 **query_plan**の返されたテーブルの列**sys.dm_exec_query_plan**:  
  
-   場合は、クエリ プランを使用して指定*plan_handle*がプラン キャッシュから削除された、 **query_plan**返されるテーブルの列が null です。 プラン ハンドルがキャプチャされた、と共に使用された場合との間の遅延時間がある場合にこの状態が発生するなど、 **sys.dm_exec_query_plan**します。  
  
-   一括操作ステートメントや、8 KB よりも大きなサイズの文字列リテラルを含むステートメントなど、キャッシュされない [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントがいくつかあります。 使用してこのようなステートメントの XML プラン表示を取得することはできません**sys.dm_exec_query_plan**バッチは、キャッシュが存在しないために現在実行している場合を除き、します。  
  
-   場合、[!INCLUDE[tsql](../../includes/tsql-md.md)]バッチまたはストアド プロシージャは、ユーザー定義関数への呼び出しやたとえば EXEC を使用して、動的 SQL への呼び出しが含まれます (*文字列*)、XML プラン表示の表に、ユーザー定義関数が含まれていないコンパイルによって返される**sys.dm_exec_query_plan**バッチやストアド プロシージャ。 代わりに、別の呼び出しを行う必要があります**sys.dm_exec_query_plan**ユーザー定義関数に対応するプラン ハンドル。  
  
 アドホック クエリは、簡易または強制パラメーター化を使用する場合、 **query_plan**ステートメント テキストのみと実際のクエリ プランではない列が含まれます。 クエリ プランを返すを呼び出す**sys.dm_exec_query_plan**準備されたパラメーター化されたクエリのプラン ハンドル。 参照することによって、クエリがパラメーター化されたかどうかを指定できます、 **sql**の列、 [sys.syscacheobjects](../../relational-databases/system-compatibility-views/sys-syscacheobjects-transact-sql.md)ビューまたはの text 列、 [sys.dm_exec_sql_text](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)動的管理ビュー。  
  
 許可される入れ子のレベルの数の制限により、 **xml**データ型、 **sys.dm_exec_query_plan**を満たす、または入れ子になった要素のレベルが 128 を超えるクエリ プランを返すことはできません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の以前のバージョンでは、この条件が原因でクエリ プランが返されず、エラー 6335 が生成されます。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2 および以降のバージョンで、 **query_plan**列は NULL を返します。 使用することができます、 [sys.dm_exec_text_query_plan &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-text-query-plan-transact-sql.md)動的管理関数をテキスト形式でクエリ プランの出力を返します。  
  
## <a name="permissions"></a>アクセス許可  
 実行する**sys.dm_exec_query_plan**、ユーザーのメンバーである必要があります、 **sysadmin**固定サーバー ロールまたはサーバーの VIEW SERVER STATE 権限があります。  
  
## <a name="examples"></a>使用例  
 次の例を使用する方法を示して、 **sys.dm_exec_query_plan**動的管理ビュー。  
  
 XML プラン表示を表示するクエリを実行、次のクエリ エディターで[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、 をクリックし、 **ShowPlanXML**で、 **query_plan**によって返されるテーブルの列**sys.dm_exec_query_plan**します。 XML プラン表示は、[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] の概要ペインに表示されます。 XML プラン表示をファイルに保存するを右クリックして**ShowPlanXML**で、 **query_plan**列で、をクリックして**結果に名前を付けて**の形式でファイルの名前\< *file_name*> .sqlplan。 たとえば、MyXMLShowplan.sqlplan します。  
  
### <a name="a-retrieve-the-cached-query-plan-for-a-slow-running-transact-sql-query-or-batch"></a>A. 実行速度の遅い Transact-SQL クエリまたは Transact-SQL バッチに対して、キャッシュされたクエリ プランを取得する  
 アドホック バッチ、ストアド プロシージャ、ユーザー定義関数などの各種 [!INCLUDE[tsql](../../includes/tsql-md.md)] バッチのクエリ プランは、プラン キャッシュと呼ばれるメモリ領域にキャッシュされます。 キャッシュされたそれぞれのクエリ プランは、プラン ハンドルと呼ばれる一意識別子で識別されます。 このプラン ハンドルを指定することができます、 **sys.dm_exec_query_plan**特定の実行プランを取得する動的管理ビュー[!INCLUDE[tsql](../../includes/tsql-md.md)]クエリまたはバッチです。  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリまたは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バッチが、特定の  との接続において長時間実行されている場合は、このクエリやバッチの実行プランを取得して、遅延の原因を調べることができます。 次の例では、実行速度の遅いクエリまたはバッチに対して XML プラン表示を取得する方法を示します。  
  
> [!NOTE]  
>  この例を実行するには、値を置き換えます*session_id*と*plan_handle*サーバーに特定の値を使用します。  
  
 まず、`sp_who` ストアド プロシージャを使用して、クエリまたはバッチを実行しているプロセスのサーバー プロセス ID (SPID) を取得します。  
  
```  
USE master;  
GO  
exec sp_who;  
GO  
```  
  
 `sp_who` によって返される結果セットでは、SPID の値が `54` であることが示されます。 `sys.dm_exec_requests` 動的管理ビューで、この SPID を使用して次のクエリを実行すると、プラン ハンドルを取得できます。  
  
```  
USE master;  
GO  
SELECT * FROM sys.dm_exec_requests  
WHERE session_id = 54;  
GO  
```  
  
 によって返されるテーブル**sys.dm_exec_requests**実行速度の遅いクエリまたはバッチのプラン ハンドルがあることを示します`0x06000100A27E7C1FA821B10600`、として指定できますが、 *plan_handle* 引数`sys.dm_exec_query_plan`を次のように XML 形式での実行プランを取得します。 実行速度の遅いクエリまたはバッチの XML 形式での実行プランに含まれている、 **query_plan**によって返されるテーブルの列`sys.dm_exec_query_plan`します。  
  
```  
USE master;  
GO  
SELECT * FROM sys.dm_exec_query_plan (0x06000100A27E7C1FA821B10600);  
GO  
```  
  
### <a name="b-retrieve-every-query-plan-from-the-plan-cache"></a>B. すべてのクエリ プランをプラン キャッシュから取得します。  
 プラン キャッシュにあるすべてのクエリ プランのスナップショットを取得するには、`sys.dm_exec_cached_plans` 動的管理ビューに対してクエリを実行し、キャッシュにあるすべてのクエリ プランのプラン ハンドルを取得します。 プラン ハンドルは、`plan_handle` の `sys.dm_exec_cached_plans` 列に格納されます。 その後、次のように CROSS APPLY 演算子を使用して、プラン ハンドルを `sys.dm_exec_query_plan` に渡します。 現在プラン キャッシュにある各プランの XML プラン表示の出力は、返されるテーブルの `query_plan` 列に格納されます。  
  
```  
USE master;  
GO  
SELECT * FROM sys.dm_exec_cached_plans cp CROSS APPLY sys.dm_exec_query_plan(cp.plan_handle);  
GO  
```  
  
### <a name="c-retrieve-every-query-plan-for-which-the-server-has-gathered-query-statistics-from-the-plan-cache"></a>C. 対象のサーバーは、プラン キャッシュからクエリの統計情報を収集がすべてのクエリ プランを取得します。  
 現在プラン キャッシュにあるクエリ プランのうち、サーバーで統計情報が収集されたすべてのクエリ プランのスナップショットを取得するには、`sys.dm_exec_query_stats` 動的管理ビューに対してクエリを実行し、キャッシュにあるこれらのプランのプラン ハンドルを取得します。 プラン ハンドルは、`plan_handle` の `sys.dm_exec_query_stats` 列に格納されます。 その後、次のように CROSS APPLY 演算子を使用して、プラン ハンドルを `sys.dm_exec_query_plan` に渡します。 現在プラン キャッシュにある、収集された統計情報に関連する各プランの XML プラン表示の出力は、返されるテーブルの `query_plan` 列に格納されます。  
  
```  
USE master;  
GO  
SELECT * FROM sys.dm_exec_query_stats qs CROSS APPLY sys.dm_exec_query_plan(qs.plan_handle);  
GO  
```  
  
### <a name="d-retrieve-information-about-the-top-five-queries-by-average-cpu-time"></a>D. 平均 CPU 時間に基づく上位 5 つのクエリに関する情報を取得する  
 次の例では、上位 5 つのクエリにかかった平均 CPU 時間とプランを返します。  
  
```  
SELECT TOP 5 total_worker_time/execution_count AS [Avg CPU Time],  
Plan_handle, query_plan   
FROM sys.dm_exec_query_stats AS qs  
CROSS APPLY sys.dm_exec_query_plan(qs.plan_handle)  
ORDER BY total_worker_time/execution_count DESC;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [sys.dm_exec_cached_plans &#40です。TRANSACT-SQL と&#41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)   
 [sys.dm_exec_query_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)   
 [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)   
 [sp_who &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md)   
 [プラン表示の論理操作と物理操作のリファレンス](../../relational-databases/showplan-logical-and-physical-operators-reference.md)   
 [sys.dm_exec_text_query_plan &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-text-query-plan-transact-sql.md)  
  
  

