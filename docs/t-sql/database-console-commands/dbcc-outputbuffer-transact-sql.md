---
title: "DBCC OUTPUTBUFFER (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/16/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|database-console-commands
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DBCC OUTPUTBUFFER
- OUTPUTBUFFER_TSQL
- OUTPUTBUFFER
- DBCC_OUTPUTBUFFER_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DBCC OUTPUTBUFFER statement
- output buffers
- current output buffer
ms.assetid: e912a06d-9fde-4e26-b057-801255d79504
caps.latest.revision: 37
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: de51ee1a87f37e8fcdf97e23be0d2fb9701e9433
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-outputbuffer-transact-sql"></a>DBCC OUTPUTBUFFER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

現在の出力バッファーを 16 進数と、指定された ASCII 形式で返します*session_id*です。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
```sql
DBCC OUTPUTBUFFER ( session_id [ , request_id ])  
[ WITH NO_INFOMSGS ]  
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
 オプションを指定できます。  
  
 NO_INFOMSGS  
 重大度レベル 0 から 10 のすべての情報メッセージを表示しないようにします。  
  
## <a name="remarks"></a>解説  
DBCC OUTPUTBUFFER には、指定したクライアントに送信される結果が表示されます (*session_id*)。 ただし、出力ストリームを含まないプロセスでは、エラー メッセージが返されます。
  
DBCC OUTPUTBUFFER で表示される結果を返したステートメントを表示するには、DBCC INPUTBUFFER を実行します。
  
## <a name="result-sets"></a>結果セット  
DBCC OUTPUTBUFFER では次の結果セットが返されます (値は変わることがあります)。
  
```sql
Output Buffer                                                              
------------------------------------------------------------------------   
01fb8028:  04 00 01 5f 00 00 00 00 e3 1b 00 01 06 6d 00 61  ..._.........m.a  
01fb8038:  00 73 00 74 00 65 00 72 00 06 6d 00 61 00 73 00  .s.t.e.r..m.a.s.  
'...'  
01fb8218:  04 17 00 00 00 00 00 d1 04 18 00 00 00 00 00 d1  ................  
01fb8228:   .  
  
(33 row(s) affected)  
  
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
## <a name="permissions"></a>Permissions  
**sysadmin** 固定サーバー ロールのメンバーシップが必要です。
  
## <a name="examples"></a>使用例  
次の例は、セッションの ID が現在の出力バッファー情報を返します`52`です。
  
```sql
DBCC OUTPUTBUFFER (52);  
```  
  
## <a name="see-also"></a>参照  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[sp_who &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md)  
[トレース フラグ &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)
  
  

