---
title: sysmail_delete_log_sp (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysmail_delete_log_sp_TSQL
- sysmail_delete_log_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_delete_log_sp
ms.assetid: e94b37a1-70ad-46a5-86c0-721892156f7c
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 09c9ebf289e6ecc73afeea6a9370bf32696cf0bf
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysmaildeletelogsp-transact-sql"></a>sysmail_delete_log_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベース メール ログからイベントを削除します。 ログ内のすべてのイベントを削除するか、日付または種類の条件に該当するイベントを削除することができます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sysmail_delete_log_sp  [ [ @logged_before = ] 'logged_before' ]  
    [, [ @event_type = ] 'event_type' ]  
  
```  
  
## <a name="arguments"></a>引数  
 [ **@logged_before** =] **'***logged_before***'**  
 日付と時刻で指定されたエントリを削除、 *logged_before*引数。 *logged_before*は**datetime**で、既定値としては NULL です。 NULL はすべての日付を表します。  
  
 [ **@event_type** =] **'***event_type***'**  
 ログとして指定された型のエントリを削除、 *event_type*です。 *event_type*は**varchar (15)** 既定値はありません。 有効なエントリは**成功**、**警告**、**エラー**、および**情報**です。 NULL はすべてのイベントの種類を表します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 使用して、 **sysmail_delete_log_sp**ストアド プロシージャをデータベース メール ログからエントリを完全に削除します。 日時を指定する引数を使用すると、古い記録だけを削除できます。 この場合、引数で指定した日時より前のイベントが削除されます。 省略可能な引数では、特定の型のとして指定されたイベントのみを削除することができます、 **event_type**引数。  
  
 データベース メール ログのエントリを削除しても、データベース メールのテーブルから電子メールのエントリは削除されません。 使用して[sysmail_delete_mailitems_sp](../../relational-databases/system-stored-procedures/sysmail-delete-mailitems-sp-transact-sql.md)をデータベース メールのテーブルから電子メールを削除します。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールは、このプロシージャを使用できます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-deleting-all-events"></a>A. すべてのイベントを削除する  
 次の例では、データベース メール ログにあるすべてのイベントを削除します。  
  
```  
EXECUTE msdb.dbo.sysmail_delete_log_sp ;  
GO  
```  
  
### <a name="b-deleting-the-oldest-events"></a>B. 古いイベントを削除する  
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
 [sysmail_event_log &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sysmail-event-log-transact-sql.md)   
 [sysmail_delete_mailitems_sp &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-delete-mailitems-sp-transact-sql.md)   
 [データベース メール メッセージやイベント ログをアーカイブする SQL Server エージェント ジョブの作成](../../relational-databases/database-mail/create-a-sql-server-agent-job-to-archive-database-mail-messages-and-event-logs.md)  
  
  
