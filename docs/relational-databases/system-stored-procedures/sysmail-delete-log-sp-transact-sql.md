---
title: sysmail_delete_log_sp (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_delete_log_sp_TSQL
- sysmail_delete_log_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_delete_log_sp
ms.assetid: e94b37a1-70ad-46a5-86c0-721892156f7c
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1aa837168c5aaff963a0b475596f4e6a4d3ff85f
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82807583"
---
# <a name="sysmail_delete_log_sp-transact-sql"></a>sysmail_delete_log_sp (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベースメールログからイベントを削除します。 ログ内のすべてのイベント、または日付または種類の条件を満たすイベントを削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sysmail_delete_log_sp  [ [ @logged_before = ] 'logged_before' ]  
    [, [ @event_type = ] 'event_type' ]  
  
```  
  
## <a name="arguments"></a>引数  
`[ @logged_before = ] 'logged_before'`*Logged_before*引数で指定された日付と時刻までのエントリを削除します。 *logged_before*は**datetime**で、既定値は NULL です。 NULL はすべての日付を表します。  
  
`[ @event_type = ] 'event_type'`*Event_type*として指定された種類のログエントリを削除します。 *event_type*は**varchar (15)** で、既定値はありません。 有効なエントリは、**成功**、**警告**、**エラー**、および**情報**です。 NULL はすべてのイベントの種類を表します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>Remarks  
 データベースメールログからエントリを完全に削除するには、 **sysmail_delete_log_sp**ストアドプロシージャを使用します。 日時を指定する引数を使用すると、古い記録だけを削除できます。 この場合、引数で指定した日時より前のイベントが削除されます。 省略可能な引数を使用すると、 **event_type**引数として指定された特定の種類のイベントのみを削除できます。  
  
 データベース メール ログのエントリを削除しても、データベース メールのテーブルから電子メールのエントリは削除されません。 [Sysmail_delete_mailitems_sp](../../relational-databases/system-stored-procedures/sysmail-delete-mailitems-sp-transact-sql.md)を使用して、データベースメールテーブルから電子メールを削除します。  
  
## <a name="permissions"></a>アクセス許可  
 このプロシージャにアクセスできるのは、 **sysadmin**固定サーバーロールのメンバーだけです。  
  
## <a name="examples"></a>例  
  
### <a name="a-deleting-all-events"></a>A. すべてのイベントを削除しています  
 次の例では、データベースメールログ内のすべてのイベントを削除します。  
  
```  
EXECUTE msdb.dbo.sysmail_delete_log_sp ;  
GO  
```  
  
### <a name="b-deleting-the-oldest-events"></a>B. 最も古いイベントを削除する  
 次の例では、データベース メール ログにあるイベントのうち、2005 年 10 月 9 日より前のイベントを削除します。  
  
```  
EXECUTE msdb.dbo.sysmail_delete_log_sp  
    @logged_before = 'October 9, 2005' ;  
GO  
```  
  
### <a name="c-deleting-all-events-of-a-certain-type"></a>C. 特定の種類のすべてのイベントを削除する  
 次の例では、データベース メール ログにある成功メッセージを削除します。  
  
```  
EXECUTE msdb.dbo.sysmail_delete_log_sp  
    @event_type = 'success' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sysmail_event_log &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sysmail-event-log-transact-sql.md)   
 [sysmail_delete_mailitems_sp &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sysmail-delete-mailitems-sp-transact-sql.md)   
 [データベース メール メッセージやイベント ログをアーカイブする SQL Server エージェント ジョブの作成](../../relational-databases/database-mail/create-a-sql-server-agent-job-to-archive-database-mail-messages-and-event-logs.md)  
  
  
