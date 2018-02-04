---
title: "sys.dm_exec_input_buffer (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/13/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_input_buffer
- sys.dm_exec_input_buffer _tsql
- dm_exec_input_buffer
- dm_exec_input_buffer_tsql
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_input_buffer dynamic management function
ms.assetid: fb34a560-bde9-4ad9-aa96-0d4baa4fc104
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 456ae8af5d366f8fb5be006f944f1f704e382488
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmexecinputbuffer-transact-sql"></a>sys.dm_exec_input_buffer (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-2014sp2-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-2014sp2-asdb-xxxx-xxx-md.md)]

  インスタンスに送信されたステートメントに関する情報を返します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
## <a name="syntax"></a>構文  
  
```  
sys.dm_exec_input_buffer ( session_id , request_id )
```  
  
## <a name="arguments"></a>引数  
*session_id*  
セッション id がルックアップするバッチを実行します。 *session_id*は**smallint**です。 *session_id*次の動的管理オブジェクトから取得できます。  
  
-   [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
-   [sys.dm_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)  
  
-   [sys.dm_exec_connections](../../relational-databases/system-dynamic-management-views/sys-dm-exec-connections-transact-sql.md)   
  
*request_id*  
Request_id [sys.dm_exec_requests](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)です。 *request_id*は**int**です。  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**event_type**|**nvarchar (256)**|特定の spid を入力バッファー内のイベントの種類。|  
|**parameters**|**smallint**|ステートメントに指定されたパラメーターは任意です。|  
|**event_info**|**nvarchar(max)**|特定の spid の入力バッファー内のステートメントのテキスト。|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、ユーザーがのインスタンスで実行中のすべてのセッションを参照して、ユーザーに VIEW SERVER STATE 権限がある場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、それ以外のユーザーは、現在のセッションのみを参照してください。  
  
 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]、ユーザーが実行中のすべてのセッションを参照して、ユーザーがデータベースの所有者である場合、 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]、それ以外のユーザーは、現在のセッションのみを参照してください。  
  
## <a name="remarks"></a>解説  
 この動的管理関数は、これによって sys.dm_exec_sessions または sys.dm_exec_requests と組み合わせて使用できる**CROSS APPLY**です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-simple-example"></a>A. 簡単な例  
 次の例では、セッション id (SPID) と要求 id を関数に渡す方法を示します。  
  
```sql  
SELECT * FROM sys.dm_exec_input_buffer (52, 0);
GO
```  
  
### <a name="b-using-cross-apply-to-additional-information"></a>B. 追加情報への適用間を使用  
 次の例では、セッション id が 50 より大きいセッションについて、入力バッファーが一覧表示します。  
  
```sql  
SELECT es.session_id, ib.event_info   
FROM sys.dm_exec_sessions AS es  
CROSS APPLY sys.dm_exec_input_buffer(es.session_id, NULL) AS ib  
WHERE es.session_id > 50;
GO
```  
  
## <a name="see-also"></a>参照  
 [実行関連の動的管理ビューおよび関数 &#40;TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_exec_sessions &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)   
 [sys.dm_exec_requests &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)   
 [DBCC INPUTBUFFER &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-inputbuffer-transact-sql.md)  
