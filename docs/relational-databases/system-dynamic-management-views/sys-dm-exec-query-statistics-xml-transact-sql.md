---
title: sys.dm_exec_query_statistics_xml (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/16/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sys.dm_exec_query_statistics_xml
- sys.dm_exec_query_statistics_xml_TSQL
- dm_exec_query_statistics_xml_TSQL
- dm_exec_query_statistics_xml
helpviewer_keywords:
- sys.dm_exec_query_statistics_xml management view
ms.assetid: fdc7659e-df41-488e-b2b5-0d79734dfecb
caps.latest.revision: 6
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: ba01e7876c174cc73697628c3b46219ff674f9a7
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmexecquerystatisticsxml-transact-sql"></a>sys.dm_exec_query_statistics_xml (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

インフライトの要求の実行プランがクエリを返します。 この DMV を使用して、一時的な統計を含む XML プラン表示を取得します。 

## <a name="syntax"></a>構文

```
sys.dm_exec_query_statistics_xml(session_id)  
``` 

## <a name="arguments"></a>引数 
*session_id*  
 セッション id がルックアップするバッチを実行します。 *session_id*は**smallint**です。 *session_id*次の動的管理オブジェクトから取得できます。  
  
-   [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
-   [sys.dm_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)  
  
-   [sys.dm_exec_connections](../../relational-databases/system-dynamic-management-views/sys-dm-exec-connections-transact-sql.md)  

## <a name="table-returned"></a>返されるテーブル
|列名|データ型|Description|  
|-----------------|---------------|-----------------|
|session_id|**smallint**|セッションの ID を指定します。 Null を許容しません。|
|request_id|**int**|要求の ID。 Null を許容しません。|
|sql_handle|**varbinary(64)**|要求の SQL テキストのハッシュ マップ。 Null 値を許容します。|
|plan_handle|**varbinary(64)**|クエリ プランのハッシュ マップ。 Null 値を許容します。|
|query_plan|**xml**|統計の部分的なプラン表示 XML です。 Null 値を許容します。|

## <a name="remarks"></a>解説
このシステム関数は [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 以降で利用可能です。

このシステム関数が両方動作**標準**と**軽量**インフラストラクチャをプロファイリング実行の統計をクエリします。  
  
**標準**を使用して、インフラストラクチャのプロファイル統計情報を有効にすることができます。
  -  [SET STATISTICS XML](../../t-sql/statements/set-statistics-xml-transact-sql.md)
  -  [SET STATISTICS PROFILE](../../t-sql/statements/set-statistics-profile-transact-sql.md)
  -  `query_post_execution_showplan`拡張イベント。  
  
**ライトウェイト**インフラストラクチャをプロファイル統計情報がで使用できる[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]SP2 および[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]有効にすることができます。
  -  グローバル トレースを使用して、7412 フラグを設定します。
  -  [ *query_thread_profile* ](http://support.microsoft.com/kb/3170113)拡張イベント を使用します。
  
> [!NOTE]
> トレース フラグ 7412 で有効にすると、軽量なプロファイルが有効になります、DMV などの標準的なプロファイルではなくインフラストラクチャのプロファイルのクエリ実行統計の任意のコンシューマー [sys.dm_exec_query_profiles](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-profiles-transact-sql.md)です。
> ただし、標準的なプロファイルがまだ使用 SET STATISTICS XML*実際のプランを含める*アクションで[!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)]、および`query_post_execution_showplan`xEvent です。

> [!IMPORTANT]
> TPC c ワークロードのテストと同様に、軽量の統計プロファイル インフラストラクチャを有効にする 1.5 ~ 2% のオーバーヘッドを追加します。 これに対し、標準的な統計プロファイル インフラストラクチャでは、同一のワークロードのシナリオのオーバーヘッドを最大 90% を追加できます。

## <a name="permissions"></a>権限  
 サーバーに対する `VIEW SERVER STATE` 権限が必要です。  

## <a name="examples"></a>使用例  
  
### <a name="a-looking-at-live-query-plan-and-execution-statistics-for-a-running-batch"></a>A. 実行中のバッチのライブ クエリ プランと実行の統計情報を見る  
 次の例のクエリ **sys.dm_exec_requests** は興味深いクエリを検索し、出力からその `session_id` をコピーします。
  
```sql  
SELECT * FROM sys.dm_exec_requests;  
GO  
```  
  
 次に、システム関数 **sys.dm_exec_query_statistics_xml** でコピーした`session_id` を使って、ライブ クエリ プランと実行の統計情報を取得します。
  
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

