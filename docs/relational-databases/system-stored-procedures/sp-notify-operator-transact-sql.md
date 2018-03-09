---
title: "sp_notify_operator (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_notify_operator_TSQL
- sp_notify_operator
dev_langs:
- TSQL
helpviewer_keywords:
- sp_notify_operator
ms.assetid: c440f5c9-9884-4196-b07c-55d87afb17c3
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7683e0150c41810c14981e0c6b6364c59ae19ae3
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="spnotifyoperator-transact-sql"></a>sp_notify_operator (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベース メールを使用して、オペレーターに電子メール メッセージを送信します。  
  
 
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_notify_operator  
    [ @profile_name = ] 'profilename' ,  
    [ @id = ] id ,  
    [ @name = ] 'name' ,  
    [ @subject = ] 'subject' ,  
    [ @body = ] 'message' ,  
    [ @file_attachments = ] 'attachment'  
    [ @mail_database = ] 'mail_host_database'  
```  
  
## <a name="arguments"></a>引数  
 [ **@profile_name=** ] **'***profilename***'**  
 メッセージの送信に使用するデータベース メール プロファイルの名前を指定します。 *profilename*は**nvarchar (128)**です。 場合*profilename*が指定されていない、既定のデータベース メール プロファイルを使用します。  
  
 [ **@id=** ] *id*  
 メッセージ送信先のオペレーターの ID を指定します。 *id*は**int**、既定値は NULL です。 いずれかの*id*または*名前*指定する必要があります。  
  
 [ **@name=** ] **'***name***'**  
 メッセージ送信先のオペレーターの名前を指定します。 *名前*は**nvarchar (128)**、既定値は NULL です。 いずれかの*id*または*名前*指定する必要があります。  
  
> **注:**メッセージを受信する前に、オペレーターの電子メール アドレスを定義する必要があります。  
  
 [ **@subject=** ] **'***subject***'**  
 電子メール メッセージの件名です。 *サブジェクト*は**nvarchar (256)**既定値はありません。  
  
 [ **@body=** ] **'***message***'**  
 電子メール メッセージの本文です。 *メッセージ*は**nvarchar (max)**既定値はありません。  
  
 [ **@file_attachments=** ] **'***attachment***'**  
 電子メール メッセージに添付するファイルの名前を指定します。 *添付ファイル*は**nvarchar (512)**、既定値はありません。  
  
 [ **@mail_database=** ] **'***mail_host_database***'**  
 メール ホスト データベースの名前を指定します。 *mail_host_database* is **nvarchar(128)**. ない場合は*mail_host_database*が指定されている、 **msdb**データベースは既定で使用します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 ここでは、指定したメッセージが、指定したオペレーターの電子メール アドレスに送信されます。 オペレーターに電子メール アドレスが構成されていない場合、エラーが返されます。  
  
 通知をオペレーターに送信するには、データベース メールとメール ホスト データベースを構成する必要があります。  
  
## <a name="permissions"></a>権限  
 既定では、このストアド プロシージャを実行できるのは、 **sysadmin** 固定サーバー ロールのメンバーです。 他のユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **データベースの次のいずれかの** エージェント固定データベース ロールが許可されている必要があります。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 これらのロールの権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79)」を参照してください。  
  
## <a name="examples"></a>使用例  
 次の例では、データベース メール プロファイル `François Ajenstat` を使用して、電子メールをオペレーター `AdventureWorks Administrator` に送信します。 電子メールの件名は`Test Notification`します。 電子メール メッセージには、"This is a test of notification via e-mail." という文が記載されています。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_notify_operator  
   @profile_name = N'AdventureWorks Administrator',  
   @name = N'François Ajenstat',  
   @subject = N'Test Notification',  
   @body = N'This is a test of notification via e-mail.' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [SQL Server エージェント ストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_operator &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-add-operator-transact-sql.md)   
 [sp_help_operator &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-help-operator-transact-sql.md)   
 [sp_delete_operator &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-delete-operator-transact-sql.md)  
  
  
