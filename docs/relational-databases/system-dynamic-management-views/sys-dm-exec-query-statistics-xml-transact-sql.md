---
title: sys.dm_exec_query_statistics_xml (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 11/16/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sys.dm_exec_query_statistics_xml
- sys.dm_exec_query_statistics_xml_TSQL
- dm_exec_query_statistics_xml_TSQL
- dm_exec_query_statistics_xml
helpviewer_keywords:
- sys.dm_exec_query_statistics_xml management view
ms.assetid: fdc7659e-df41-488e-b2b5-0d79734dfecb
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 63e1d22670929448110083c31e9900e462d576bc
ms.sourcegitcommit: 671370ec2d49ed0159a418b9c9ac56acf43249ad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2019
ms.locfileid: "58072306"
---
# <a name="sysdmexecquerystatisticsxml-transact-sql"></a>sys.dm_exec_query_statistics_xml (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

クエリの実行中の要求の実行プランを返します。 この DMV を使用して、一時的な統計情報の XML プラン表示を取得します。 

## <a name="syntax"></a>構文

```
sys.dm_exec_query_statistics_xml(session_id)  
``` 

## <a name="arguments"></a>引数 
*session_id*  
 セッション id がルックアップするバッチを実行します。 *session_id*は**smallint**します。 *session_id*次の動的管理オブジェクトから取得できます。  
  
-   [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
-   [sys.dm_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)  
  
-   [sys.dm_exec_connections](../../relational-databases/system-dynamic-management-views/sys-dm-exec-connections-transact-sql.md)  

## <a name="table-returned"></a>返されるテーブル

|列名|データ型|説明|  
|-----------------|---------------|-----------------|
|session_id|**smallint**|セッションの ID。 Null を許容しません。|
|request_id|**int**|要求の ID。 Null を許容しません。|
|sql_handle|**varbinary(64)**|要求の SQL テキストのハッシュ マップ。 Null 値を許容します。|
|plan_handle|**varbinary(64)**|クエリ プランのハッシュ マップ。 Null 値を許容します。|
|query_plan|**xml**|Showplan XML 部分の統計を使用します。 Null 値を許容します。|

## <a name="remarks"></a>コメント
このシステム関数は [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 以降で利用可能です。 サポート技術情報を参照してください[3190871。](https://support.microsoft.com/en-us/help/3190871)

このシステム関数が両方の下で動作**標準**と**軽量**実行統計プロファイリング インフラストラクチャをクエリします。 詳細については、「[クエリ プロファイリング インフラストラクチャ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-statistics-xml-transact-sql.md)」を参照してください。  

## <a name="permissions"></a>アクセス許可  
 サーバーに対する `VIEW SERVER STATE` 権限が必要です。  

## <a name="examples"></a>使用例  
  
### <a name="a-looking-at-live-query-plan-and-execution-statistics-for-a-running-batch"></a>A. 実行中のバッチのライブ クエリ プランと実行の統計情報を見る  
 次の例では、**sys.dm_exec_requests** を照会して興味深いクエリを検索し、出力からその `session_id` をコピーします。  
  
```sql  
SELECT * FROM sys.dm_exec_requests;  
GO  
```  
  
 次に、システム関数 **sys.dm_exec_query_statistics_xml** でコピーした `session_id` を使って、ライブ クエリ プランと実行の統計情報を取得します。  
  
```sql  
--Run this in a different session than the session in which your query is running.
SELECT * FROM sys.dm_exec_query_statistics_xml(< copied session_id >);  
GO  
```   

 または、実行中のすべての要求を結合します。  
  
```sql  
--Run this in a different session than the session in which your query is running.
SELECT * FROM sys.dm_exec_requests
CROSS APPLY sys.dm_exec_query_statistics_xml(session_id);  
GO  
```   
  
## <a name="see-also"></a>参照
  [トレース フラグ](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [データベース関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  

