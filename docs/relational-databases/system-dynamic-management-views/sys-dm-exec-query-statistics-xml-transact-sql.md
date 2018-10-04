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
ms.openlocfilehash: 9fdcbb6bec46043f030172d794cb5238d99a151e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47784666"
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
|session_id|**smallint**|セッションの ID を指定します。 Null を許容しません。|
|request_id|**int**|要求の ID。 Null を許容しません。|
|sql_handle|**varbinary(64)**|要求の SQL テキストのハッシュ マップ。 Null 値を許容します。|
|plan_handle|**varbinary(64)**|クエリ プランのハッシュ マップ。 Null 値を許容します。|
|query_plan|**xml**|Showplan XML 部分の統計を使用します。 Null 値を許容します。|

## <a name="remarks"></a>コメント
このシステム関数は [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 以降で利用可能です。

このシステム関数が両方の下で動作**標準**と**軽量**実行統計プロファイリング インフラストラクチャをクエリします。  
  
**標準**を使用して、統計プロファイリング インフラストラクチャを有効にすることができます。
  -  [SET STATISTICS XML](../../t-sql/statements/set-statistics-xml-transact-sql.md)
  -  [統計プロファイルの設定](../../t-sql/statements/set-statistics-profile-transact-sql.md)
  -  `query_post_execution_showplan`拡張イベント。  
  
**ライトウェイト**統計プロファイリング インフラストラクチャが表示されます。 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP2 と[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]と有効にすることができます。
  -  グローバルにトレースを使用して 7412 フラグを設定します。
  -  [*query_thread_profile*](http://support.microsoft.com/kb/3170113) 拡張イベント を使用します。
  
> [!NOTE]
> クエリ実行統計の DMV などの標準的なプロファイルではなくインフラストラクチャをプロファイリングのすべてのコンシューマーに軽量プロファイリングを有効、トレース フラグ 7412 を有効にすると[sys.dm_exec_query_profiles](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-profiles-transact-sql.md)します。
> ただし、標準的なプロファイルは引き続き使用 SET STATISTICS XML を*実際のプランを含める*アクション[!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)]、および`query_post_execution_showplan`xEvent。

> [!IMPORTANT]
> TPC c ワークロードのテストと同様に、軽量版統計プロファイリング インフラストラクチャを有効にすると、1.5 ~ 2% オーバーヘッドを追加します。 これに対し、標準的な統計プロファイル インフラストラクチャでは、同じワークロード シナリオのオーバーヘッドを最大 90% を追加できます。

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

