---
title: sysmail_help_account_sp (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_help_account_sp_TSQL
- sysmail_help_account_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_help_account_sp
ms.assetid: 87c7c39c-8e05-4e68-9272-45f908809c3b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0798359bedc959e792f56b3d81507329b618f217
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47781330"
---
# <a name="sysmailhelpaccountsp-transact-sql"></a>sysmail_help_account_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベース メール アカウントに関する、パスワード以外の情報を一覧表示します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sysmail_help_account_sp [ [ @account_id = ] account_id | [ @account_name = ] 'account_name' ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@account_id** =] *account_id*  
 情報を一覧表示するアカウントのアカウント ID を指定します。 *account_id*は**int**、既定値は NULL です。  
  
 [ **@account_name** =] **'***account_name***'**  
 情報を一覧表示するアカウントの名前を指定します。 *account_name*は**sysname**、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 次の列を含む結果セットを返します。  
  
||||  
|-|-|-|  
|列名|データ型|説明|  
|**account_id**|**int**|アカウントの ID。|  
|**name**|**sysname**|アカウントの名前。|  
|**description**|**nvarchar (256)**|アカウントの説明。|  
|**email_address**|**nvarchar(128)**|メッセージ送信元の電子メール アドレス。|  
|**display_name**|**nvarchar(128)**|アカウントの表示名。|  
|**replyto_address**|**nvarchar(128)**|このアカウントからのメッセージに対する返信アドレス。|  
|**servertype**|**sysname**|アカウントで使用されている電子メール サーバーの種類。|  
|**servername**|**sysname**|アカウントで使用されている電子メール サーバーの名前。|  
|**port**|**int**|電子メール サーバーで使用されているポート番号。|  
|**username**|**nvarchar(128)**|電子メール サーバーで認証が使用されている場合に、電子メール サーバーへのサインインに使用するユーザー名。 ときに**username**が null の場合、データベース メールは、このアカウントの認証を使用しません。|  
|**use_default_credentials**|**bit**|資格情報を使用して SMTP サーバーにメールを送信するかどうかを指定します、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]します。 **use_default_credentials**ビットは、既定値はありません。 データベース メールでの資格情報を使用してこのパラメーターが 1 の場合、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]サービス。 データベース メールを使用してこのパラメーターが 0 の場合、 **@username**と**@password** SMTP サーバーでの認証。 場合**@username**と**@password** NULL の場合は、データベース メールで匿名認証を使用します。 このパラメーターを指定する前に、SMTP 管理者に問い合わせてください。|  
|**enable_ssl**|**bit**|データベース メールで SSL (Secure Sockets Layer) を使用して通信を暗号化するかどうかを指定します。 SMTP サーバーで SSL が必要な場合はこのオプションを使用します。 **enable_ssl**ビットは、既定値はありません。 1 の場合、データベース メールでは SSL を使用して通信を暗号化することを示します。 0 の場合、データベース メールでは SSL 暗号化を使用せずにメールを送信することを示します。|  
  
## <a name="remarks"></a>コメント  
 ない場合*account_id*または*account_name*が提供される、 **sysmail_help_account** Microsoft SQL Server インスタンス内のすべてのデータベース メール アカウント情報を一覧表示します。  
  
 ストアド プロシージャ**sysmail_help_account_sp**では、 **msdb**が所有するデータベースにあり、 **dbo**スキーマ。 現在のデータベースがない場合、3 つの部分の名前を持つプロシージャを実行する必要があります**msdb**します。  
  
## <a name="permissions"></a>アクセス許可  
 このプロシージャの既定のメンバーへのアクセス許可を実行、 **sysadmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
 **A.すべてのアカウント情報を一覧表示**  
  
 次の例では、インスタンス内のすべてのアカウントについて、アカウント情報を一覧表示します。  
  
```  
EXECUTE msdb.dbo.sysmail_help_account_sp ;  
```  
  
 次に結果セットを示します。行の長さは編集されています。  
  
```  
account_id  name                         description                             email_address             display_name                     replyto_address servertype servername                port        username use_default_credentials enable_ssl  
----------- ---------------------------- --------------------------------------- ------------------------- -------------------------------- --------------- ---------- ------------------------- ----------- -------- ----------------------- ----------  
148         AdventureWorks Administrator Mail account for administrative e-mail. dba@Adventure-Works.com   AdventureWorks Automated Mailer  NULL            SMTP       smtp.Adventure-Works.com  25          NULL 0                          0        
149         Audit Account                Account for audit e-mail.               audit@Adventure-Works.com Automated Mailer (Audit)         NULL            SMTP       smtp.Adventure-Works.com  25          NULL 0                          0        
```  
  
 **B.特定のアカウント情報を一覧表示**  
  
 次の例では、`AdventureWorks Administrator` というアカウントについて、アカウント情報を一覧表示します。  
  
```  
EXECUTE msdb.dbo.sysmail_help_account_sp  
    @account_name = 'AdventureWorks Administrator' ;  
```  
  
 次に結果セットを示します。行の長さは編集されています。  
  
```  
account_id  name                         description                             email_address             display_name                     replyto_address servertype servername                port        username use_default_credentials enable_ssl  
----------- ---------------------------- ------------------------------------------------------ ------------------------- ---------------- ---------- ------------------------- ----------- -------- ----------------------- ----------  
148         AdventureWorks Administrator Mail account for administrative e-mail. dba@Adventure-Works.com   AdventureWorks Automated Mailer  NULL            SMTP       smtp.Adventure-Works.com  25          NULL     0                       0       
```  
  
## <a name="see-also"></a>参照  
 [データベース メール](../../relational-databases/database-mail/database-mail.md)   
 [データベース メール アカウントを作成します。](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [データベース メール ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
