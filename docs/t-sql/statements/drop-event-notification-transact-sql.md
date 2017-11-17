---
title: "DROP EVENT NOTIFICATION (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP EVENT NOTIFICATION
- DROP_EVENT_NOTIFICATION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- event notifications [SQL Server], removing
- deleting event notifications
- dropping event notifications
- DROP EVENT NOTIFICATION statement
- removing event notifications
ms.assetid: 0ffd8f47-4ea3-4238-9e73-c318df710cf7
caps.latest.revision: 33
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ab32a9ffadce83635e8ef987607af913fe0f2472
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="drop-event-notification-transact-sql"></a>DROP EVENT NOTIFICATION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のデータベースからイベント通知トリガーを削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
DROP EVENT NOTIFICATION notification_name [ ,...n ]  
ON { SERVER | DATABASE | QUEUE queue_name }  
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *notification_name*  
 削除するイベント通知の名前を指定します。 複数のイベント通知を指定できます。 現在作成されているイベント通知の一覧を表示する[sys.event_notifications & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-event-notifications-transact-sql.md).  
  
 SERVER  
 イベント通知のスコープが現在のサーバーに適用されることを示します。 イベント通知の作成時に SERVER を指定した場合は、SERVER を指定する必要があります。  
  
 DATABASE  
 イベント通知のスコープが現在のデータベースに適用されることを示します。 イベント通知の作成時に DATABASE を指定した場合は、DATABASE を指定する必要があります。  
  
 キュー *queue_name*  
 イベント通知のスコープが指定したキューに適用されることを示します*queue_name*です。 イベント通知の作成時に QUEUE を指定した場合は、QUEUE を指定する必要があります。 *queue_name*キューの名前を指定しても指定する必要があります。  
  
## <a name="remarks"></a>解説  
 イベント通知がトランザクションの中で発生し、同じトランザクションの中で削除された場合は、イベント通知のインスタンスが送信され、その後でイベント通知が削除されます。  
  
## <a name="permissions"></a>Permissions  
 データベース レベルのスコープを持つイベント通知を削除するには、少なくとも、イベント通知の所有者であるか、現在のデータベースに対する ALTER ANY DATABASE EVENT NOTIFICATION 権限を持っている必要があります。  
  
 サーバー レベルのスコープを持つイベント通知を削除するには、少なくとも、イベント通知の所有者であるか、そのサーバーに対する ALTER ANY EVENT NOTIFICATION 権限を持っている必要があります。  
  
 特定のキューのイベント通知を削除するには、少なくとも、イベント通知の所有者であるか、親キューに対する ALTER 権限を持っている必要があります。  
  
## <a name="examples"></a>使用例  
 次の例では、データベース スコープのイベント通知を作成し、削除します。  
  
```tsql  
USE AdventureWorks2012;  
GO  
CREATE EVENT NOTIFICATION NotifyALTER_T1  
ON DATABASE  
FOR ALTER_TABLE  
TO SERVICE 'NotifyService',  
    '8140a771-3c4b-4479-8ac0-81008ab17984';  
GO  
DROP EVENT NOTIFICATION NotifyALTER_T1  
ON DATABASE;  
```  
  
## <a name="see-also"></a>参照  
 [イベント通知 &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-event-notification-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sys.event_notifications & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-event-notifications-transact-sql.md)   
 [sys.events & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-events-transact-sql.md)  
  
  

