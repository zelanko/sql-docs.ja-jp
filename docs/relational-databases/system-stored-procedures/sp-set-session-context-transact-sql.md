---
title: sp_set_session_context (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 08/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_set_session_context
- sp_set_session_context_TSQL
- sys.sp_set_session_context
- sys.sp_set_session_context_TSQL
helpviewer_keywords:
- sp_set_session_context
ms.assetid: 7a3a3b2a-1408-4767-a376-c690e3c1fc5b
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d278e7540ef27e4c6041406bc7c4011976a5a213
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47832760"
---
# <a name="spsetsessioncontext-transact-sql"></a>sp_set_session_context (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

セッションのコンテキストでは、キー値のペアを設定します。  
  

 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
sp_set_session_context [ @key= ] 'key', [ @value= ] 'value'  
    [ , [ @read_only = ] { 0 | 1 } ]  
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 [ @key=] 'key'  
 型の設定されているキー **sysname**します。 キーの最大サイズは、128 バイトです。  
  
 [ @value=] 'value'  
 型の指定したキーの値は、 **sql_variant**します。 NULL 値の設定、メモリを解放します。 最大サイズは 8,000 バイトです。  
  
 [ @read_only= ] { 0 | 1 }  
 型のフラグ**ビット**します。 1 の場合、し、指定されたキーの値変更できませんもう一度この論理接続で。 場合は 0 (既定値) の場合、その値を変更できます。  
  
## <a name="permissions"></a>アクセス許可  
 すべてのユーザーは、そのセッションのセッションのコンテキストを設定できます。  
  
## <a name="remarks"></a>コメント  
 その他のストアド プロシージャでは、ように唯一のリテラルと変数 (not 式または関数の呼び出し)、パラメーターとして渡すことができます。  
  
 セッション コンテキストの合計サイズは、256 kb に制限されます。 この制限を超える原因となる値の設定、ステートメントが失敗したかどうか。 全体のメモリ使用量を監視する[sys.dm_os_memory_objects &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-objects-transact-sql.md)します。  
  
 全体的なメモリの使用状況を監視するにはクエリを実行して[sys.dm_os_memory_cache_counters &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-cache-counters-transact-sql.md)次のようにします。 `SELECT * FROM sys.dm_os_memory_cache_counters WHERE type = 'CACHESTORE_SESSION_CONTEXT';`  
  
## <a name="examples"></a>使用例  
 次の例では、設定および英語の値を持つ言語の名前付きセッションのコンテキスト キーを取得する方法を示します。  
  
```  
EXEC sp_set_session_context 'language', 'English';  
SELECT SESSION_CONTEXT(N'language');  
```  
  
 次の例では、省略可能な読み取り専用フラグの使用を示します。  
  
```  
EXEC sp_set_session_context 'user_id', 4, @read_only = 1;  
```  
  
## <a name="see-also"></a>参照  
 [CURRENT_TRANSACTION_ID &#40;Transact-SQL&#41;](../../t-sql/functions/current-transaction-id-transact-sql.md)   
 [SESSION_CONTEXT &#40;Transact-SQL&#41;](../../t-sql/functions/session-context-transact-sql.md)   
 [行レベルのセキュリティ](../../relational-databases/security/row-level-security.md)   
 [CONTEXT_INFO  &#40;Transact-SQL&#41;](../../t-sql/functions/context-info-transact-sql.md)   
 [SET CONTEXT_INFO &#40;Transact-SQL&#41;](../../t-sql/statements/set-context-info-transact-sql.md)  
  
  
