---
title: sysmail_delete_mailitems_sp (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysmail_delete_mailitems_sp_TSQL
- sysmail_delete_mailitems_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_delete_mailitems_sp
ms.assetid: f87c9f4a-bda1-4bce-84b2-a055a3229ecd
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ca730dc633f8aad10aa79fd34bb7e94870a48076
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
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
 [ **@sent_before=** ] **'***sent_before***'**  
 として指定した日時まで電子メールを削除、 *@sent_before*引数。 *@sent_before*は**datetime**で、既定値としては NULL です。 NULL はすべての日付を表します。  
  
 [ **@sent_status=** ] **'***sent_status***'**  
 指定された型の電子メールを削除*sent_status*です。 *sent_status*は**varchar (8)** 既定値はありません。 有効なエントリは**送信**、**未送信**、**再試行**と**失敗**です。 NULL はすべての状態を表します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 データベース メール メッセージとその添付ファイルに格納されて、 **msdb**データベース。 メッセージを防ぐために定期的に削除する**msdb**が増え、予想よりも大きいと、組織のドキュメント保有期間のプログラムに準拠します。 使用して、 **sysmail_delete_mailitems_sp**ストアド プロシージャをデータベース メールのテーブルから電子メール メッセージを完全に削除します。 日時を指定する引数を使用すると、古い電子メールだけを削除できます。 この場合、引数で指定した日時より前の電子メールが削除されます。 他の省略可能な引数では、特定の型のとして指定した電子メールだけを削除することができます、 **sent_status**引数。 いずれかに引数を指定する必要があります**@sent_before**または **@sent_status**です。 すべてのメッセージを削除するには使用 **@sent_before = getdate()** です。  
  
 電子メールを削除すると、そのメッセージに関係する添付ファイルも削除されます。 電子メールを削除しても、対応するエントリは削除されません**sysmail_event_log**です。 使用して[sysmail_delete_log_sp](../../relational-databases/system-stored-procedures/sysmail-delete-log-sp-transact-sql.md)ログから項目を削除します。  
  
## <a name="permissions"></a>権限  
 既定では、このストアド プロシージャが実行のメンバーに与えられますオフ、 **sysadmin**固定サーバー ロールと**DatabaseMailUserRole**です。 メンバー、 **sysadmin**をすべてのユーザーから送信された電子メールを削除するには、この手順を実行できるは、固定サーバー ロール。 メンバー **DatabaseMailUserRole**のみ、そのユーザーが送信された電子メールを削除できます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-deleting-all-e-mails"></a>A. すべての電子メールを削除する  
 次の例では、データベース メール システムにあるすべての電子メールを削除します。  
  
```  
DECLARE @GETDATE datetime  
SET @GETDATE = GETDATE();  
EXECUTE msdb.dbo.sysmail_delete_mailitems_sp @sent_before = @GETDATE;  
GO  
```  
  
### <a name="b-deleting-the-oldest-e-mails"></a>B. 古い電子メールを削除する  
 次の例よりも古いデータベース メール ログに電子メールを削除する`October 9, 2005`です。  
  
```  
EXECUTE msdb.dbo.sysmail_delete_mailitems_sp   
    @sent_before = 'October 9, 2005' ;  
GO  
```  
  
### <a name="c-deleting-all-e-mails-of-a-certain-type"></a>C. 特定の種類のすべての電子メールを削除する  
 次の例では、データベース メール ログにある失敗した電子メールをすべて削除します。  
  
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
  
  
