---
title: "メッセージ型 (TRANSACT-SQL) を削除 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP_MESSAGE_TYPE_TSQL
- DROP MESSAGE TYPE
dev_langs:
- TSQL
helpviewer_keywords:
- message types [Service Broker], removing
- deleting message types
- dropping message types
- DROP MESSAGE TYPE statement
- removing message types
ms.assetid: 805e8ad5-8a93-49f0-88e5-e6fca8814dd5
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 859419b6809d1c44486130eadaf30c1411a03b97
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="drop-message-type-transact-sql"></a>DROP MESSAGE TYPE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  既存のメッセージ型を削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
DROP MESSAGE TYPE message_type_name  
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *message_type_name*  
 削除するメッセージ型の名前を指定します。 サーバー名、データベース名、スキーマ名は指定できません。  
  
## <a name="permissions"></a>Permissions  
 メッセージ型を削除する権限は、既定ではメッセージ型の所有者、db_ddladmin 固定データベース ロールまたは db_owner 固定データベース ロールのメンバー、および sysadmin 固定サーバー ロールのメンバーに与えられています。  
  
## <a name="remarks"></a>解説  
 いずれかのコントラクトがメッセージ型を参照する場合は、そのメッセージ型を削除できません。  
  
## <a name="examples"></a>使用例  
 次の例では、データベースからメッセージ型 `//Adventure-Works.com/Expenses/SubmitExpense` を削除します。  
  
```  
DROP MESSAGE TYPE [//Adventure-Works.com/Expenses/SubmitExpense] ;  
```  
  
## <a name="see-also"></a>参照  
 [メッセージの種類 &#40; を ALTER します。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-message-type-transact-sql.md)   
 [メッセージの種類 &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-message-type-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
