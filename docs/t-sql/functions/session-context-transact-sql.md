---
title: "SESSION_CONTEXT (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/22/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SESSION_CONTEXT
- sys.SESSION_CONTEXT
- SESSION_CONTEXT_TSQL
- sys.SESSION_CONTEXT_TSQL
helpviewer_keywords:
- SESSION_CONTEXT function
ms.assetid: b6bdbc54-331a-43cc-ab3d-3872d6a12100
caps.latest.revision: 11
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 23eea4b51009272ae06987ee2e9c1730750b3d6d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="sessioncontext-transact-sql"></a>SESSION_CONTEXT (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  現在のセッションのコンテキストでは、指定したキーの値を返します。 使用して、値を設定、 [sp_set_session_context & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-set-session-context-transact-sql.md)プロシージャです。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
SESSION_CONTEXT(N'key')  
```  
  
## <a name="arguments"></a>引数  
 ' key'  
 取得される値のキー (sysname 型)。  
  
## <a name="return-type"></a>戻り値の型  
 **sql_variant**  
  
## <a name="return-value"></a>戻り値  
 そのキーの値が設定されていない場合は、セッションのコンテキスト、または NULL で指定されたキーに関連付けられている値です。  
  
## <a name="permissions"></a>Permissions  
 すべてのユーザーは、そのセッションのセッションのコンテキストを読み取ることができます。  
  
## <a name="remarks"></a>解説  
 SESSION_CONTEXT の MARS 動作は CONTEXT_INFO するときと同様です。 場合は、MARS バッチでは、キーと値のペアを設定、新しい値がありません返されますその他の MARS バッチで、同じ接続で新しい値を設定したバッチの完了後に開始しません。 複数の MARS バッチが、接続でアクティブな場合は、値は"read_only"として設定できません。 これにより、競合状態や非決定論的"wins"どの値について  
  
## <a name="examples"></a>使用例  
 キーのセッション コンテキスト値を設定する単純な例を次`user_id`4、および、使用、 **SESSION_CONTEXT**値を取得する関数。  
  
```  
EXEC sp_set_session_context 'user_id', 4;  
SELECT SESSION_CONTEXT(N'user_id');  
```  
  
## <a name="see-also"></a>参照  
 [sp_set_session_context &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-set-session-context-transact-sql.md)   
 [CURRENT_TRANSACTION_ID & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/current-transaction-id-transact-sql.md)   
 [行レベルのセキュリティ](../../relational-databases/security/row-level-security.md)   
 [CONTEXT_INFO & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/context-info-transact-sql.md)   
 [SET CONTEXT_INFO & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-context-info-transact-sql.md)  
  
  

