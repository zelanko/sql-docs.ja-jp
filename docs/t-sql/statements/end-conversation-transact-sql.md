---
title: "END CONVERSATION (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- END DIALOG
- END CONVERSATION
- END_DIALOG_TSQL
- END_CONVERSATION_TSQL
dev_langs: TSQL
helpviewer_keywords:
- errors [Service Broker], conversations
- dialogs [Service Broker], ending
- closing conversations
- END CONVERSATION statement
- conversations [Service Broker], ending
- ending conversations [SQL Server]
ms.assetid: 4415a126-cd22-4a5e-b84a-d8c68515c83b
caps.latest.revision: "35"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: d68dcecf84cb24b0c06876d40742c8f5ffe8124d
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="end-conversation-transact-sql"></a>END CONVERSATION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  既存のメッセージ交換の一方の側を終了します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
END CONVERSATION conversation_handle  
   [   [ WITH ERROR = failure_code DESCRIPTION = 'failure_text' ]  
     | [ WITH CLEANUP ]  
    ]  
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *conversation_handle*  
 終了するメッセージ交換のメッセージ交換ハンドルを指定します。  
  
 WITH ERROR =*failure_code*  
 エラー コードを指定します。 *Failure_code*の種類は**int**です。このエラー コードはユーザー定義のコードで、メッセージ交換の相手側に送信するエラー メッセージの一部となります。 このエラー コードは 0 よりも大きい値にする必要があります。  
  
 DESCRIPTION =*failure_text*  
 エラー メッセージです。 *Failure_text*の種類は**nvarchar (3000)**です。 このエラー テキストはユーザー定義のテキストで、メッセージ交換の相手側に送信するエラー メッセージの一部となります。  
  
 WITH CLEANUP  
 正常に完了できなかったメッセージ交換の一方の側のメッセージとカタログ ビュー エントリをすべて削除します。 メッセージ交換の相手側にはクリーンアップは通知されません。 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サービス キューのメッセージ交換のエンドポイント、転送キューにメッセージ交換のすべてのメッセージおよびメッセージ交換のすべてのメッセージを削除します。 管理者は、このオプションを使用して、正常に完了できなかったメッセージ交換のメッセージを削除できます。 たとえば、リモート サービスが永久的に削除された場合、管理者は WITH CLEANUP を使ってこのサービスに対するメッセージを削除できます。 コードでは WITH CLEANUP を使用しない、[!INCLUDE[ssSB](../../includes/sssb-md.md)]アプリケーションです。 受信エンドポイントでメッセージの受信を確認する前に END CONVERSATION WITH CLEANUP が実行されると、送信エンドポイントからそのメッセージが再び送信されます。 これにより、ダイアログが再実行される可能性があります。  
  
## <a name="remarks"></a>解説  
 メッセージ交換のロックを終了、メッセージ交換グループを指定した*conversation_handle*に属しています。 メッセージ交換の終了時に[!INCLUDE[ssSB](../../includes/sssb-md.md)]サービス キューからメッセージ交換のすべてのメッセージを削除します。  
  
 メッセージ交換が終了した後、アプリケーションではそのメッセージ交換のメッセージを送受信できなくなります。 メッセージ交換を完了するには、メッセージ交換の両方の参加者が END CONVERSATION を呼び出す必要があります。 [!INCLUDE[ssSB](../../includes/sssb-md.md)] が、メッセージ交換の相手側から終了ダイアログ メッセージまたはエラー メッセージを受信しなかった場合は、[!INCLUDE[ssSB](../../includes/sssb-md.md)] から相手側に、メッセージ交換が終了したことが通知されます。 この場合、このメッセージ交換のメッセージ交換ハンドルが無効になる一方、メッセージ交換のエンドポイントはアクティブなまま残り、この状態はリモート サービスをホストするインスタンスからメッセージの受信確認が返されるまで継続されます。  
  
 場合[!INCLUDE[ssSB](../../includes/sssb-md.md)]がまだ処理されていない、終了ダイアログ メッセージまたは error メッセージ、メッセージ交換の[!INCLUDE[ssSB](../../includes/sssb-md.md)]メッセージ交換が終了したメッセージ交換のリモート側に通知します。 [!INCLUDE[ssSB](../../includes/sssb-md.md)] からリモート サービスに送信されるメッセージは、指定されるオプションによって異なります。  
  
-   リモート サービスがアクティブである場合は、メッセージ交換がエラー、およびへのメッセージ交換が終了[!INCLUDE[ssSB](../../includes/sssb-md.md)]型のメッセージを送信`http://schemas.microsoft.com/SQL/ServiceBroker/EndDialog`リモート サービスにします。 [!INCLUDE[ssSB](../../includes/sssb-md.md)]このメッセージをメッセージ交換の順に転送キューに追加します。 現在転送キューにあるメッセージ交換のすべてのメッセージは、このメッセージが送信されるよりも前に、[!INCLUDE[ssSB](../../includes/sssb-md.md)] によって送信されます。  
  
-   メッセージ交換をエラーで終了し、リモート サービスへのメッセージ交換がアクティブである場合[!INCLUDE[ssSB](../../includes/sssb-md.md)]型のメッセージを送信`http://schemas.microsoft.com/SQL/ServiceBroker/Error`リモート サービスにします。 現在転送キューに残っているメッセージ交換のメッセージはすべて、[!INCLUDE[ssSB](../../includes/sssb-md.md)] によって削除されます。  
  
-   データベース管理者は WITH CLEANUP 句を使用して、正常に完了しなかったメッセージ交換のメッセージを削除できます。 このオプションでは、メッセージ交換のすべてのメッセージとカタログ ビュー エントリが削除されます。 この場合、メッセージ交換のリモート側にはメッセージ交換が終了したことが通知されません。また、アプリケーションでは送信されたが、ネットワーク経由では転送されていなかったメッセージは受信できないことがあります。 メッセージ交換が正常に完了できない場合にのみ、このオプションを使用してください。  
  
 メッセージ交換が終了した後、[!INCLUDE[tsql](../../includes/tsql-md.md)] SEND ステートメントでそのメッセージ交換ハンドルが指定されると、[!INCLUDE[tsql](../../includes/tsql-md.md)] エラーが発生します。 メッセージ交換の相手側からメッセージを受信した場合、これらのメッセージは [!INCLUDE[ssSB](../../includes/sssb-md.md)] によって破棄されます。  
  
 メッセージ交換が終了し、そのメッセージ交換の未送信のメッセージがリモート サービス側に残っている場合、未送信のメッセージはリモート サービスによって削除されます。 これはエラーとして扱われないため、リモート サービスはメッセージの削除に関する通知を受信しません。  
  
 WITH ERROR 句のエラー コードは、正の数値で指定する必要があります。 負の数値は、[!INCLUDE[ssSB](../../includes/sssb-md.md)] のエラー メッセージ用に予約されています。  
  
 END CONVERSATION は、ユーザー定義の関数では無効です。  
  
## <a name="permissions"></a>権限  
 アクティブなメッセージ交換を終了するには、そのメッセージ交換の所有者であるか、sysadmin 固定サーバー ロールまたは db_owner 固定データベース ロールのメンバーであることが必要です。  
  
 sysadmin 固定サーバー ロールまたは db_owner 固定データベース ロールのメンバーであれば、WITH CLEANUP を使用して、既に完了したメッセージ交換のメタデータを削除できます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-ending-a-conversation"></a>A. メッセージ交換を終了する  
 次の例で指定したダイアログを終了する`@dialog_handle`です。  
  
```  
END CONVERSATION @dialog_handle ;  
```  
  
### <a name="b-ending-a-conversation-with-an-error"></a>B. メッセージ交換を終了し、エラーを返す  
 次の例で指定したダイアログを終了する`@dialog_handle`処理中のステートメントがエラーを報告する場合はエラーです。 これは簡単なエラー処理であり、アプリケーションによってはこの方法が適切でない場合があります。  
  
```  
DECLARE @dialog_handle UNIQUEIDENTIFIER,  
        @ErrorSave INT,  
        @ErrorDesc NVARCHAR(100) ;  
BEGIN TRANSACTION ;  
  
<receive and process message>  
  
SET @ErrorSave = @@ERROR ;  
  
IF (@ErrorSave <> 0)  
  BEGIN  
      ROLLBACK TRANSACTION ;  
      SET @ErrorDesc = N'An error has occurred.' ;  
      END CONVERSATION @dialog_handle   
      WITH ERROR = @ErrorSave DESCRIPTION = @ErrorDesc ;  
  END  
ELSE  
  
COMMIT TRANSACTION ;  
```  
  
### <a name="c-cleaning-up-a-conversation-that-cannot-complete-normally"></a>C. 正常に完了しなかったメッセージ交換をクリーンアップする  
 次の例で指定したダイアログを終了する`@dialog_handle`です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]リモート サービスを通知することがなくサービス キューと転送キューからすべてのメッセージをすぐに削除します。 ダイアログのクリーンアップを終了するリモート サービスに通知しません、ためにのみ使用このリモート サービスが受信可能にできない場合、 **EndDialog**または**エラー**メッセージ。  
  
```  
END CONVERSATION @dialog_handle WITH CLEANUP ;  
```  
  
## <a name="see-also"></a>参照  
 [BEGIN CONVERSATION TIMER &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/begin-conversation-timer-transact-sql.md)   
 [BEGIN DIALOG CONVERSATION &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/begin-dialog-conversation-transact-sql.md)   
 [sys.conversation_endpoints &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-conversation-endpoints-transact-sql.md)  
  
  
