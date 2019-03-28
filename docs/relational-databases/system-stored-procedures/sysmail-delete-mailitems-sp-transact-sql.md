---
title: sysmail_delete_mailitems_sp (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_delete_mailitems_sp_TSQL
- sysmail_delete_mailitems_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_delete_mailitems_sp
ms.assetid: f87c9f4a-bda1-4bce-84b2-a055a3229ecd
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3a8549d33b000744f4d8430ee306e0083455894c
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58531764"
---
# <a name="sysmaildeletemailitemssp-transact-sql"></a>sysmail_delete_mailitems_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベース メールの内部テーブルから電子メール メッセージを完全に削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sysmail_delete_mailitems_sp  [ [ @sent_before = ] 'sent_before' ]  
    [ , [ @sent_status = ] 'sent_status' ]  
```  
  
## <a name="arguments"></a>引数  
`[ @sent_before = ] 'sent_before'` として指定された日時まで電子メールを削除、 *@sent_before*引数。 *@sent_before*は**datetime**で、既定値は NULL です。 NULL はすべての日付を表します。  
  
`[ @sent_status = ] 'sent_status'` 指定された型の電子メールを削除*sent_status*します。 *sent_status*は**varchar (8)** 既定値はありません。 有効なエントリは**送信**、**未送信**、**再試行**と**失敗**します。 NULL はすべての状態を表します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 データベース メール メッセージと添付ファイルに格納されます、 **msdb**データベース。 メッセージを防ぐために定期的に削除する**msdb**が予想よりも大きくと、組織のドキュメント保有期間のプログラムに準拠するようにします。 使用して、 **sysmail_delete_mailitems_sp**ストアド プロシージャをデータベース メールのテーブルから電子メール メッセージを完全に削除します。 日時を指定する引数を使用すると、古い電子メールだけを削除できます。 この場合、引数で指定した日時より前の電子メールが削除されます。 もう 1 つの省略可能な引数を使用すると、特定の種類、として指定した電子メールだけを削除、 **sent_status**引数。 いずれかの引数を指定する必要があります**@sent_before**または **@sent_status**します。 すべてのメッセージを削除する使用 **@sent_before = getdate()** します。  
  
 電子メールを削除すると、そのメッセージに関係する添付ファイルも削除されます。 電子メールを削除しても、対応するエントリは削除されません**sysmail_event_log**します。 使用[sysmail_delete_log_sp](../../relational-databases/system-stored-procedures/sysmail-delete-log-sp-transact-sql.md)ログからアイテムを削除します。  
  
## <a name="permissions"></a>アクセス許可  
 既定では、このストアド プロシージャの実行のメンバーに許可されてオフ、 **sysadmin**固定サーバー ロールと**DatabaseMailUserRole**します。 メンバー、 **sysadmin**すべてのユーザーが送信した電子メールを削除するには、この手順を実行できるは、固定サーバー ロール。 メンバーの**DatabaseMailUserRole**のみ、そのユーザーが送信した電子メールを削除できます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-deleting-all-e-mails"></a>A. すべての電子メールを削除する  
 次の例では、データベース メール システムにあるすべての電子メールを削除します。  
  
```  
DECLARE @GETDATE datetime  
SET @GETDATE = GETDATE();  
EXECUTE msdb.dbo.sysmail_delete_mailitems_sp @sent_before = @GETDATE;  
GO  
```  
  
### <a name="b-deleting-the-oldest-e-mails"></a>B. 最も古い電子メールを削除します。  
 次の例よりも古いデータベース メール ログに電子メールを削除します。`October 9, 2005`します。  
  
```  
EXECUTE msdb.dbo.sysmail_delete_mailitems_sp   
    @sent_before = 'October 9, 2005' ;  
GO  
```  
  
### <a name="c-deleting-all-e-mails-of-a-certain-type"></a>C. 特定の種類のすべての電子メールを削除します。  
 次の例では、データベース メール ログに失敗した電子メールをすべて削除します。  
  
```  
EXECUTE msdb.dbo.sysmail_delete_mailitems_sp   
    @sent_status = 'failed' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sysmail_allitems &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-allitems-transact-sql.md)   
 [sysmail_event_log &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-event-log-transact-sql.md)   
 [sysmail_mailattachments &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-mailattachments-transact-sql.md)   
 [データベース メール メッセージやイベント ログをアーカイブする SQL Server エージェント ジョブの作成](../../relational-databases/database-mail/create-a-sql-server-agent-job-to-archive-database-mail-messages-and-event-logs.md)  
  
  
