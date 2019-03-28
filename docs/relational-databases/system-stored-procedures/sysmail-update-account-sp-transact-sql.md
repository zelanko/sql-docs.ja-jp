---
title: sysmail_update_account_sp (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 11/17/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_update_account_sp
- sysmail_update_account_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_update_account_sp
ms.assetid: ba2fdccc-5ed4-40ef-a479-79497b4d61aa
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 09af9a0190b8ba3b01c72cfa29e0647ad6d6b74d
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58528434"
---
# <a name="sysmailupdateaccountsp-transact-sql"></a>sysmail_update_account_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  既存のデータベース メール アカウントの情報を変更します。  
 
 
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sysmail_update_account_sp [ [ @account_id = ] account_id ] [ , ] [ [ @account_name = ] 'account_name' ] ,  
    [ @email_address = ] 'email_address' ,   
    [ @display_name = ] 'display_name' ,   
    [ @replyto_address = ] 'replyto_address' ,  
    [ @description = ] 'description' ,   
    [ @mailserver_name = ] 'server_name' ,   
    [ @mailserver_type = ] 'server_type' ,   
    [ @port = ] port_number ,   
    [ @timeout = ] 'timeout' ,  
    [ @username = ] 'username' ,  
    [ @password = ] 'password' ,  
    [ @use_default_credentials = ] use_default_credentials ,  
    [ @enable_ssl = ] enable_ssl   
```  
  
## <a name="arguments"></a>引数  
`[ @account_id = ] account_id` 更新するアカウント ID。 *account_id*は**int**、既定値は NULL です。 少なくとも 1 つの*account_id*または*account_name*指定する必要があります。 両方が指定されている場合、手順は、アカウントの名前を変更します。  
  
`[ @account_name = ] 'account_name'` 更新するアカウントの名前。 *account_name*は**sysname**、既定値は NULL です。 少なくとも 1 つの*account_id*または*account_name*指定する必要があります。 両方が指定されている場合、手順は、アカウントの名前を変更します。  
  
`[ @email_address = ] 'email_address'` メッセージを送信する新しい電子メール アドレス。 このアドレスは、インターネットの電子メール アドレスを指定する必要があります。 アドレスでサーバー名とは、データベース メールを使用してこのアカウントからメールを送信するサーバーです。 *email_address*は**nvarchar (128)**、既定値は NULL です。  
  
`[ @display_name = ] 'display_name'` このアカウントから電子メール メッセージで使用する新しい表示名。 *display_name*は**nvarchar (128)**、既定値はありません。  
  
`[ @replyto_address = ] 'replyto_address'` このアカウントから電子メール メッセージの返信先 ヘッダーで使用する新しいアドレス。 *replyto_address*は**nvarchar (128)**、既定値はありません。  
  
`[ @description = ] 'description'` アカウントの新しい説明します。 *説明*は**nvarchar (256)**、既定値は NULL です。  
  
`[ @mailserver_name = ] 'server_name'` このアカウントを使用する SMTP メール サーバーの新しい名前。 実行するコンピューター[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]解決できる必要があります、 *server_name* IP アドレス。 *server_name*は**sysname**、既定値はありません。  
  
`[ @mailserver_type = ] 'server_type'` メール サーバーの新しい型。 *server_type*は**sysname**、既定値はありません。 値しか **'SMTP'** はサポートされています。  
  
`[ @port = ] port_number` メール サーバーの新しいポート番号。 *port_number*は**int**、既定値はありません。  
  
`[ @timeout = ] 'timeout'` 1 つの電子メール メッセージの SmtpClient.Send のタイムアウト パラメーター。 *タイムアウト*は**int** (秒) で、既定値はありません。  
  
`[ @username = ] 'username'` メール サーバーへのログオンに使用する新しいユーザー名。 *ユーザー名*は**sysname**、既定値はありません。  
  
`[ @password = ] 'password'` メール サーバーへのログオンに使用する新しいパスワード。 *パスワード*は**sysname**、既定値はありません。  
  
`[ @use_default_credentials = ] use_default_credentials` 資格情報を使用して SMTP サーバーにメールを送信するかどうかを指定します、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]サービス。 **use_default_credentials**ビットは、既定値はありません。 データベース メールでの資格情報を使用してこのパラメーターが 1 の場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)]します。 データベース メールを使用してこのパラメーターが 0 の場合、 **@username**と**@password** SMTP サーバーでの認証。 場合**@username**と**@password** NULL は、匿名認証が使用されます。 このパラメーターを指定する前に、SMTP 管理者に問い合わせてください。  
  
`[ @enable_ssl = ] enable_ssl` データベース メールで Secure Sockets Layer (SSL) を使用して通信を暗号化するかどうかを指定します。 SMTP サーバーで SSL が必要な場合はこのオプションを使用します。 **enable_ssl**ビットは、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 アカウント名とアカウント id の両方を指定すると、ストアド プロシージャは、アカウントの情報の更新だけでなく、アカウント名を変更します。 アカウント名の変更は、アカウント名のエラーを修正する場合に利用できます。  
  
 ストアド プロシージャ**sysmail_update_account_sp**では、 **msdb**が所有するデータベースにあり、 **dbo**スキーマ。 現在のデータベースがない場合、3 つの部分の名前を持つプロシージャを実行する必要があります**msdb**します。  
  
## <a name="permissions"></a>アクセス許可  
 **sysadmin** 固定サーバー ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-changing-the-information-for-an-account"></a>A. アカウントの情報を変更する  
 次の例は、アカウントを更新`AdventureWorks Administrator`で、 **msdb**データベース。 アカウントの情報は、指定された値に設定されます。  
  
```  
EXECUTE msdb.dbo.sysmail_update_account_sp  
     @account_name = 'AdventureWorks Administrator'  
    ,@description = 'Mail account for administrative e-mail.'  
    ,@email_address = 'dba@Adventure-Works.com'  
    ,@display_name = 'AdventureWorks Automated Mailer'  
    ,@replyto_address = NULL  
    ,@mailserver_name = 'smtp.Adventure-Works.com'  
    ,@mailserver_type = 'SMTP'  
    ,@port = 25  
    ,@timeout = 60  
    ,@username = NULL  
    ,@password = NULL  
    ,@use_default_credentials = 0  
    ,@enable_ssl = 0;  
```  
  
### <a name="b-changing-the-name-of-an-account-and-the-information-for-an-account"></a>B. アカウントとアカウントの情報の名前を変更します。  
 次の例では、アカウント ID `125` の名前を変更し、アカウント情報を更新します。 アカウントの新しい名前が`Backup Mail Server`します。  
  
```  
EXECUTE msdb.dbo.sysmail_update_account_sp  
     @account_id = 125  
    ,@account_name = 'Backup Mail Server'  
    ,@description = 'Mail account for administrative e-mail.'  
    ,@email_address = 'dba@Adventure-Works.com'  
    ,@display_name = 'AdventureWorks Automated Mailer'  
    ,@replyto_address = NULL  
    ,@mailserver_name = 'smtp-backup.Adventure-Works.com'  
    ,@mailserver_type = 'SMTP'  
    ,@port = 25  
    ,@timeout = 60  
    ,@username = NULL  
    ,@password = NULL  
    ,@use_default_credentials = 0  
    ,@enable_ssl = 0;  
```  
  
## <a name="see-also"></a>参照  
 [データベース メール](../../relational-databases/database-mail/database-mail.md)   
 [データベース メール アカウントを作成します。](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [データベース メール ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
