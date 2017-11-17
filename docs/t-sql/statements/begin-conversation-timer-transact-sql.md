---
title: "BEGIN CONVERSATION TIMER (TRANSACT-SQL) |Microsoft ドキュメント"
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
- CONVERSATION
- BEGIN_CONVERSATION_TSQL
- TIMER_TSQL
- TIMER
- CONVERSATION TIMER
- CONVERSATION_TIMER_TSQL
- BEGIN CONVERSATION TIMER
- BEGIN_CONVERSATION_TIMER_TSQL
- CONVERSATION_TSQL
- BEGIN CONVERSATION
dev_langs:
- TSQL
helpviewer_keywords:
- BEGIN CONVERSATION TIMER statement
- DialogTimer message
- dialogs [Service Broker], beginning
- timeouts [Service Broker]
- timer messages [Service Broker]
- conversations [Service Broker], timers
- starting timers [Service Broker]
- http://schemas.microsoft.com/SQL/ServiceBroker/DialogTimer message
ms.assetid: 98e49b3f-a38f-4180-8171-fa9cb30db4cb
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b70228860699b3fefe9a1b5adcfc0250ce5d34e1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="begin-conversation-timer-transact-sql"></a>BEGIN CONVERSATION TIMER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  タイマーを開始します。 タイムアウトを過ぎると、[!INCLUDE[ssSB](../../includes/sssb-md.md)]メッセージを格納する型の`http://schemas.microsoft.com/SQL/ServiceBroker/DialogTimer`メッセージ交換のローカル キューにします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
BEGIN CONVERSATION TIMER ( conversation_handle )  
   TIMEOUT = timeout   
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 BEGIN CONVERSATION TIMER **(***conversation_handle***)**  
 メッセージ交換を定刻に指定します。 *Conversation_handle*型でなければなりません**uniqueidentifier**です。  
  
 TIMEOUT  
 メッセージをキューに配置する前に待機する時間を、秒単位で指定します。  
  
## <a name="remarks"></a>解説  
 メッセージ交換タイマーによって、特定の時間が経過すると、メッセージ交換でメッセージを受信する方法がアプリケーションに提供されます。 タイマーが時間切れになる前にメッセージ交換で BEGIN CONVERSATION TIMER を呼び出すと、タイムアウトが新しい値に設定されます。 メッセージ交換の有効期間とは異なり、メッセージ交換の送信側と受信側に個別のメッセージ交換タイマーがあります。 **DialogTimer**メッセージ交換のリモート側に影響を与えずにローカル キューでのメッセージが到着するとします。 したがって、タイマー メッセージはアプリケーションでどのような目的にも使用できます。  
  
 たとえばメッセージ交換タイマーを使用すると、アプリケーションで、期限の切れた応答に対する待機時間を短くすることができます。 アプリケーションが 30 秒以内にダイアログを完了するようにする場合、そのダイアログのメッセージ交換タイマーを 60 秒 (30 秒に 30 秒の猶予時間を加えたもの) に設定できます。 ダイアログが 60 秒後もまだ開いている場合、アプリケーションはそのダイアログのキューでタイムアウト メッセージを受信します。  
  
 また、アプリケーションはメッセージ交換タイマーを使用して、特定の時間にアクティブ化を要求できます。 たとえば、数分ごとにアクティブな接続数を報告するサービス、またはオープンな予約発注数を毎晩報告するサービスを作成できます。 サービスは、目的の時間に期限切れにするメッセージ交換タイマーを設定します。タイマーの期限が切れると、[!INCLUDE[ssSB](../../includes/sssb-md.md)]送信、 **DialogTimer**メッセージ。 **DialogTimer**メッセージにより[!INCLUDE[ssSB](../../includes/sssb-md.md)]ストアド プロシージャ、キューのアクティブ化を開始します。 このストアド プロシージャによって、メッセージがリモート サービスに送信され、メッセージ交換タイマーが再開します。  
  
 BEGIN CONVERSATION TIMER は、ユーザー定義の関数では無効です。  
  
## <a name="permissions"></a>Permissions  
 メッセージ交換のメンバーに対するサービスの SEND 権限を持つユーザーにメッセージ交換タイマーの既定値を設定するためのアクセス許可、 **sysadmin**固定サーバー ロールのメンバー、 **db_owner**固定データベース ロール。  
  
## <a name="examples"></a>使用例  
 次の例では、2 分のタイムアウトを設定で指定されるダイアログで`@dialog_handle`です。  
  
```  
-- @dialog_handle is of type uniqueidentifier and  
-- contains a valid conversation handle.  
  
BEGIN CONVERSATION TIMER (@dialog_handle)  
TIMEOUT = 120 ;  
```  
  
## <a name="see-also"></a>参照  
 [BEGIN DIALOG CONVERSATION & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/begin-dialog-conversation-transact-sql.md)   
 [END CONVERSATION & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/end-conversation-transact-sql.md)   
 [受信 (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/receive-transact-sql.md)  
  
  

