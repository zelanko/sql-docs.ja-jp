---
title: SESSION_CONTEXT (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/22/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SESSION_CONTEXT
- sys.SESSION_CONTEXT
- SESSION_CONTEXT_TSQL
- sys.SESSION_CONTEXT_TSQL
helpviewer_keywords:
- SESSION_CONTEXT function
ms.assetid: b6bdbc54-331a-43cc-ab3d-3872d6a12100
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: d875024e6f227c6ba0d65ab0346092c02e860385
ms.sourcegitcommit: 83f061304fedbc2801d8d6a44094ccda97fdb576
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2019
ms.locfileid: "65945240"
---
# <a name="sessioncontext-transact-sql"></a>SESSION_CONTEXT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  現在のセッションのコンテキストで指定されたキーの値を返します。 値が、を使用して設定 [sp_set_session_context (& a) #40 です。TRANSACT-SQL と #41; ](../../relational-databases/system-stored-procedures/sp-set-session-context-transact-sql.md)プロシージャです。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
SESSION_CONTEXT(N'key')  
```  
  
## <a name="arguments"></a>引数  
 'key'  
 取得される値のキー (sysname 型)。  
  
## <a name="return-type"></a>戻り値の型  
 **sql_variant**  
  
## <a name="return-value"></a>戻り値  
 セッションのコンテキストで指定されたキーに関連付けられている値か、そのキーの値が設定されていない場合は NULL です。  
  
## <a name="permissions"></a>アクセス許可  
 すべてのユーザーは、そのセッションのセッションのコンテキストを読み取ることができます。  
  
## <a name="remarks"></a>Remarks  
 SESSION_CONTEXT の MARS の動作は CONTEXT_INFO の動作と同様です。 MARS バッチにキーと値のペアが設定された場合、新しい値を設定しているバッチが完了した後に他のバッチが開始された場合を除き、同じ接続上の他の MARS バッチで新しい値が返されることはありません。 接続上で複数の MARS バッチがアクティブな場合、値には "read_only" を設定できません。 これにより、どちらの値が "勝つ" かという観点での競合状態と非決定論を回避します。  
  
## <a name="examples"></a>使用例  
 次のような単純な例は、キーのセッション コンテキスト値を設定 `user_id` 4、および、使用する、 **SESSION_CONTEXT** 値を取得する関数。  
  
```  
EXEC sp_set_session_context 'user_id', 4;  
SELECT SESSION_CONTEXT(N'user_id');  
```  
  
## <a name="see-also"></a>参照  
 [sp_set_session_context &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-set-session-context-transact-sql.md)   
 [CURRENT_TRANSACTION_ID &#40;Transact-SQL&#41;](../../t-sql/functions/current-transaction-id-transact-sql.md)   
 [行レベルのセキュリティ](../../relational-databases/security/row-level-security.md)   
 [CONTEXT_INFO  &#40;Transact-SQL&#41;](../../t-sql/functions/context-info-transact-sql.md)   
 [SET CONTEXT_INFO &#40;Transact-SQL&#41;](../../t-sql/statements/set-context-info-transact-sql.md)  
  
  
