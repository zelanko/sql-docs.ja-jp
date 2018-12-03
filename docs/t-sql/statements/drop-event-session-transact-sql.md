---
title: DROP EVENT SESSION (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP_EVENT_SESSION_TSQL
- DROP EVENT SESSION
dev_langs:
- TSQL
helpviewer_keywords:
- event sessions [SQL Server]
- DROP EVENT SESSION statement
ms.assetid: 92eabe4b-24e2-43b1-978c-31a199964b90
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: a1edffab8e94c9ee171b3be4203d08b23df83452
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2018
ms.locfileid: "52404447"
---
# <a name="drop-event-session-transact-sql"></a>DROP EVENT SESSION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  イベント セッションを削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```    
DROP EVENT SESSION event_session_name  
ON SERVER  
```  
  
## <a name="arguments"></a>引数  
 *event_session_name*  
 既存のイベント セッションの名前を指定します。  
  
## <a name="remarks"></a>Remarks  
 イベント セッションを削除すると、ターゲットやセッション パラメーターなどの構成情報がすべて完全に削除されます。  
  
## <a name="permissions"></a>アクセス許可  
 `ALTER ANY EVENT SESSION` アクセス許可が必要です。  
  
## <a name="examples"></a>使用例  
イベント セッションを削除する方法を次の例に示します。  
  
```sql  
DROP EVENT SESSION evt_spin_lock_diagnosis ON SERVER;
GO
```  
  
## <a name="see-also"></a>参照  
 [CREATE EVENT SESSION &#40;Transact-SQL&#41;](../../t-sql/statements/create-event-session-transact-sql.md)   
 [ALTER EVENT SESSION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-event-session-transact-sql.md)   
 [sys.server_event_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-event-sessions-transact-sql.md)  
  
  
