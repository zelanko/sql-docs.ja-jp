---
title: "DROP BROKER PRIORITY (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP_BROKER_PRIORITY_TSQL
- DROP BROKER PRIORITY
dev_langs:
- TSQL
helpviewer_keywords:
- DROP BROKER PRIORITY statement
ms.assetid: 09ee6c5b-af94-4a4b-a0e2-f9eac50e43aa
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 254914f3b92289faf19a37b4651e7c95804ac791
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="drop-broker-priority-transact-sql"></a>DROP BROKER PRIORITY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のデータベースからメッセージ交換の優先度を削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
DROP BROKER PRIORITY ConversationPriorityName  
[;]  
```  
  
## <a name="arguments"></a>引数  
 *ConversationPriorityName*  
 削除するメッセージ交換の優先度の名前を指定します。  
  
## <a name="remarks"></a>解説  
 メッセージ交換の優先度を削除した場合、既存のメッセージ交換では、そのメッセージ交換の優先度から割り当てられた優先順位で操作が続行されます。  
  
## <a name="permissions"></a>Permissions  
 メッセージ交換の優先度を作成する権限は、既定では db_ddladmin 固定データベース ロールまたは db_owner 固定データベース ロールのメンバー、および sysadmin 固定サーバー ロールのメンバーに与えられています。 データベースに対する ALTER 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例は、という名前のメッセージ交換の優先度を削除`InitiatorAToTargetPriority`です。  
  
```  
DROP BROKER PRIORITY InitiatorAToTargetPriority;  
  
```  
  
## <a name="see-also"></a>参照  
 [ALTER BROKER PRIORITY & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-broker-priority-transact-sql.md)   
 [ブローカーの優先順位 &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-broker-priority-transact-sql.md)   
 [sys.conversation_priorities & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-conversation-priorities-transact-sql.md)  
  
  

