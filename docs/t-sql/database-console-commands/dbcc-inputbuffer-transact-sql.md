---
title: "DBCC INPUTBUFFER (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|database-console-commands
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DBCC INPUTBUFFER
- INPUTBUFFER
- DBCC_INPUTBUFFER_TSQL
- INPUTBUFFER_TSQL
dev_langs: TSQL
helpviewer_keywords:
- input buffers [SQL Server]
- last statement from client
- displaying last statement sent
- statements [SQL Server], last statement
- DBCC INPUTBUFFER statement
ms.assetid: a44d702b-b3fb-4950-8c8f-1adcf3f514ba
caps.latest.revision: "51"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 0d36f0e25c0f5959053e028cdfc95babf69c4e48
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="dbcc-inputbuffer-transact-sql"></a>DBCC INPUTBUFFER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

インスタンスに、クライアントから送信された最後のステートメントが表示されます[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
DBCC INPUTBUFFER ( session_id [ , request_id ])  
[WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>引数  
*session_id*  
アクティブな各プライマリ接続に関連付けられているセッション ID を指定します。  
  
*request_id*  
現在のセッション内で検索する具体的な要求 (バッチ) を指定します。  

次のクエリを返します*request_id*:  
```sql
SELECT request_id   
FROM sys.dm_exec_requests   
WHERE session_id = @@spid;  
```  
のすべてのメンションを  
オプションを指定可能にします。  
  
NO_INFOMSGS  
重大度レベル 0 から 10 のすべての情報メッセージを表示しないようにします。  
  
## <a name="result-sets"></a>結果セット  
DBCC INPUTBUFFER では、次の列を含む結果セットが返されます。
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**EventType**|**nvarchar(30)**|イベントの種類。 これは、 **RPC イベント**または**言語イベント**です。 出力になります**No Event**と最後のイベントは検出されませんでした。|  
|**パラメーター**|**smallint**|0 = テキスト<br /><br /> 1-  *n* パラメーターを =|  
|**EventInfo**|**nvarchar (4000)**|**EventType** RPC の場合、 **EventInfo**はプロシージャ名だけが含まれています。 **EventType**言語のイベントの最初の 4,000 文字だけが表示されます。|  
  
たとえば、DBCC INPUTBUFFER では、バッファー内の最後のイベントが DBCC INPUTBUFFER(11) である場合、次の結果セットが返されます。
  
```
EventType      Parameters EventInfo               
-------------- ---------- ---------------------   
Language Event 0          DBCC INPUTBUFFER (11)  
  
(1 row(s) affected)  
  
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  

> [!NOTE]
> 以降で[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]SP2 では、使用[sys.dm_exec_input_buffer](../../relational-databases/system-dynamic-management-views/sys-dm-exec-input-buffer-transact-sql.md)のインスタンスに送信されたステートメントに関する情報を返す[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。

## <a name="permissions"></a>権限  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]次のいずれかが必要です。
-   ユーザーのメンバーである必要があります、 **sysadmin**固定サーバー ロール。  
-   ユーザーには VIEW SERVER STATE 権限が必要です。  
-   *session_id*コマンドを実行するセッション ID と同じである必要があります。 セッション ID を特定するには、次のクエリを実行します。  
  
```sql
SELECT @@spid;  
```
  
[!INCLUDE[ssSDS](../../includes/sssds-md.md)] Premium 階層には、データベースの VIEW DATABASE STATE 権限が必要です。 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Standard および Basic 階層が必要です、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]管理者アカウントです。
  
## <a name="examples"></a>使用例  
次の例では、前の接続で長いトランザクションが実行されている間に、2 番目の接続で `DBCC INPUTBUFFER` を実行します。
  
```sql
CREATE TABLE dbo.T1 (Col1 int, Col2 char(3));  
GO  
DECLARE @i int = 0;  
BEGIN TRAN  
SET @i = 0;  
WHILE (@i < 100000)  
BEGIN  
INSERT INTO dbo.T1 VALUES (@i, CAST(@i AS char(3)));  
SET @i += 1;  
END;  
COMMIT TRAN;  
--Start new connection #2.  
DBCC INPUTBUFFER (52);  
```  

## <a name="see-also"></a>参照  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[sp_who &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md)  
[sys.dm_exec_input_buffer &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-input-buffer-transact-sql.md)
  
  
