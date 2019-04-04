---
title: sys.dm_exec_query_plan_stats (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/27/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sys.dm_exec_query_plan_stats
- sys.dm_exec_query_plan_stats_TSQL
- dm_exec_query_plan_stats_TSQL
- dm_exec_query_plan_stats
helpviewer_keywords:
- sys.dm_exec_query_plan_stats management view
ms.assetid: fdc7659e-df41-488e-b2b5-0d79734dfacb
author: pmasl
ms.author: pelopes
manager: amitban
ms.openlocfilehash: 0bef01ab6b4ecf1a9f05b1c7b40e2767aaae0db3
ms.sourcegitcommit: c60784d1099875a865fd37af2fb9b0414a8c9550
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2019
ms.locfileid: "58645354"
---
# <a name="sysdmexecqueryplanstats-transact-sql"></a>sys.dm_exec_query_plan_stats (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

以前にキャッシュされたクエリ プランの最後の既知の実際の実行プランのと同じを返します。 

## <a name="syntax"></a>構文

```
sys.dm_exec_query_plan_stats(plan_handle)  
``` 

## <a name="arguments"></a>引数 
*plan_handle*  
実行されるバッチのクエリ実行プランを一意に識別するトークンと、そのプランがプラン キャッシュ内に存在または現在実行しています。 *plan_handle*は**varbinary (64)** します。   

*Plan_handle*次の動的管理オブジェクトから取得できます。  
  
-   [sys.dm_exec_cached_plans &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)  
  
-   [sys.dm_exec_query_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
  
-   [sys.dm_exec_requests (&) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  

-   [sys.dm_exec_procedure_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md)  

-   [sys.dm_exec_trigger_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-trigger-stats-transact-sql.md)  

## <a name="table-returned"></a>返されるテーブル

|列名|データ型|説明|  
|-----------------|---------------|-----------------|
|**dbid**|**smallint**|このプランに対応する [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントがコンパイルされたときに有効であったコンテキスト データベースの ID。 アドホックおよび準備された SQL ステートメントのステートメントがコンパイルされたデータベースの ID。<br /><br /> 列が null 値を許容します。|  
|**objectid**|**int**|このクエリ プランのオブジェクト (たとえば、ストアド プロシージャまたはユーザー定義関数) の ID。 アドホックおよび準備されたバッチでは、この列は**null**します。<br /><br /> 列が null 値を許容します。|  
|**number**|**smallint**|番号付きストアド プロシージャの整数。 ための手順のグループなど、**注文**アプリケーションが付けられて**orderproc; 1**、 **orderproc; 2**など。 アドホックおよび準備されたバッチでは、この列は**null**します。<br /><br /> 列が null 値を許容します。|  
|**encrypted**|**bit**|対応するストアド プロシージャを暗号化するかどうかを示します。<br /><br /> 0 = 暗号化されていません。<br /><br /> 1 = 暗号化<br /><br /> 列値が許容されません。|  
|**query_plan**|**xml**|最後の既知のランタイムで指定されている実際のクエリ実行プランのプラン表示の表現が含まれて*plan_handle*します。 プラン表示は XML 形式です。 含まれているなどのアドホック バッチごとに 1 つのプランが生成された[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメント、ストアド プロシージャの呼び出し、およびユーザー定義関数の呼び出し。<br /><br /> 列が null 値を許容します。| 

## <a name="remarks"></a>コメント
このシステム関数では、以降で利用できる[!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)]CTP 2.4 します。

これはオプトイン機能である必要があります[トレース フラグ](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)2451 を有効にします。   

このシステム関数は、の下で動作、**軽量**実行統計プロファイリング インフラストラクチャをクエリします。 詳細については、「[クエリ プロファイリング インフラストラクチャ](../../relational-databases/performance/query-profiling-infrastructure.md)」を参照してください。  

次の条件下で、Showplan の出力**実際の実行プランに相当**で返される、 **query_plan**の返されたテーブルの列**sys.dm_exec_query_plan_stats**:  

-   プランが見つかりません[sys.dm_exec_cached_plans](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)します。     
    **AND**    
-   実行中のクエリは、複合型またはリソース消費しています。

次の条件下で、**簡略化された<sup>1</sup>** でプラン表示出力が返される、 **query_plan**の返されたテーブルの列**sys.dm_exec_query_plan_stats**:  

-   プランが見つかりません[sys.dm_exec_cached_plans](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)します。     
    **AND**    
-   クエリが単純で、通常は OLTP ワークロードの一部として分類します。

<sup>1</sup>これはルート ノードの演算子 (選択) のみを含む実行プランを示します。 [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] CTP 2.4 がこれだけは sys.dm_exec_cached_plans を通じて利用可能なキャッシュされたプランを指します。

次の条件下で**出力は返されません**から**sys.dm_exec_query_plan_stats**:

-   クエリ プランを使用して指定されている*plan_handle*がプラン キャッシュから削除されています。     
    **OR**    
-   クエリ プランが最初にキャッシュ可能されません。 詳細については、[実行プランのキャッシュと再利用](../../relational-databases/query-processing-architecture-guide.md#execution-plan-caching-and-reuse)を参照してください。
  
> [!NOTE] 
> 許可される入れ子のレベルの数の制限により、 **xml**データ型、 **sys.dm_exec_query_plan**を満たす、または入れ子になった要素のレベルが 128 を超えるクエリ プランを返すことはできません。 以前のバージョンの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、この条件は、クエリ プランを返すことを禁止し、生成[エラー 6335](../../relational-databases/errors-events/database-engine-events-and-errors.md#errors-6000-to-6999)します。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2 および以降のバージョンで、 **query_plan**列は NULL を返します。  

## <a name="permissions"></a>アクセス許可  
 サーバーに対する `VIEW SERVER STATE` 権限が必要です。  

## <a name="examples"></a>使用例  
  
### <a name="a-looking-at-last-known-actual-query-execution-plan-for-a-specific-cached-plan"></a>A. 特定のキャッシュされたプランを最後に既知の実際のクエリ実行プランを検索  
 次の例のクエリ**sys.dm_exec_cached_plans**興味深いプランとコピーを検索するその`plan_handle`出力からします。  
  
```sql  
SELECT * FROM sys.dm_exec_cached_plans;  
GO  
```  
  
次に、最後の既知の実際のクエリ実行プランを取得するには、使用、コピーした`plan_handle`をシステム関数**sys.dm_exec_query_plan_stats**します。  
  
```sql  
SELECT * FROM sys.dm_exec_query_plan_stats(< copied plan_handle >);  
GO  
```   

### <a name="b-looking-at-last-known-actual-query-execution-plan-for-all-cached-plans"></a>B. すべてのキャッシュされたプランの最後に既知の実際のクエリ実行プランを探す
  
```sql  
SELECT *   
FROM sys.dm_exec_cached_plans AS cp
CROSS APPLY sys.dm_exec_sql_text(plan_handle) AS st
CROSS APPLY sys.dm_exec_query_plan_stats(plan_handle) AS qps;  
GO  
```   

### <a name="c-looking-at-last-known-actual-query-execution-plan-for-a-specific-cached-plan-and-query-text"></a>C. 特定のキャッシュされたプランとクエリのテキストの最後に既知の実際のクエリ実行プランを探す

```sql  
SELECT *   
FROM sys.dm_exec_cached_plans AS cp
CROSS APPLY sys.dm_exec_sql_text(plan_handle) AS st
CROSS APPLY sys.dm_exec_query_plan_stats(plan_handle) AS qps
WHERE st.text LIKE 'SELECT * FROM Person.Person%';  
GO  
```   

## <a name="see-also"></a>参照
  [トレース フラグ](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [実行関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  

