---
title: sysmail_update_account_sp (トランザクション-SQL) |マイクロソフトドキュメント
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
ms.openlocfilehash: 3dd772a1519ea856cac0302d31be9eb7d0f9d782
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283191"
---
# <a name="sysmail_update_account_sp-transact-sql"></a>sysmail_update_account_sp (Transact-SQL)
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
`[ @account_id = ] account_id`更新するアカウント ID。 *account_id*は**int**で、デフォルトは NULL です。 account_idまたは*account_name*の*account_id*少なくとも 1 つを指定する必要があります。 両方を指定すると、アカウントの名前が変更されます。  
  
`[ @account_name = ] 'account_name'`更新するアカウントの名前。 *account_name*は**sysname**で、デフォルトは NULL です。 account_idまたは*account_name*の*account_id*少なくとも 1 つを指定する必要があります。 両方を指定すると、アカウントの名前が変更されます。  
  
`[ @email_address = ] 'email_address'`メッセージの送信元の新しい電子メール アドレス。 このアドレスはインターネットの電子メール アドレスである必要があります。 アドレス内のサーバー名は、データベース メールがこのアカウントからメールを送信するために使用するサーバーです。 *email_address*は**nvarchar(128) で**、デフォルトは NULL です。  
  
`[ @display_name = ] 'display_name'`このアカウントからの電子メール メッセージに使用する新しい表示名。 *display_name*は**nvarchar(128) で**、デフォルトはありません。  
  
`[ @replyto_address = ] 'replyto_address'`このアカウントからの電子メール メッセージの返信先ヘッダーで使用する新しいアドレス。 *replyto_address*は**nvarchar(128) で**、デフォルトはありません。  
  
`[ @description = ] 'description'`アカウントの新しい説明。 *説明*は**nvarchar(256) で**、デフォルトは NULL です。  
  
`[ @mailserver_name = ] 'server_name'`このアカウントに使用する SMTP メール サーバーの新しい名前。 実行[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]するコンピュータは *、server_name*を IP アドレスに解決できる必要があります。 *server_name*は**sysname**で、デフォルトはありません。  
  
`[ @mailserver_type = ] 'server_type'`メール サーバーの新しい種類。 *server_type*は**sysname**で、デフォルトはありません。 **'SMTP'** の値のみがサポートされます。  
  
`[ @port = ] port_number`メール サーバーの新しいポート番号。 *port_number*は**int**で、デフォルトはありません。  
  
`[ @timeout = ] 'timeout'`単一の電子メール メッセージの SmtpClient.Send のタイムアウト パラメーター。 *タイムアウト*は秒**単位で**、デフォルトはありません。  
  
`[ @username = ] 'username'`メール サーバーへのログオンに使用する新しいユーザー名。 *ユーザー名*は**sysname**で、デフォルトはありません。  
  
`[ @password = ] 'password'`メール サーバーへのログオンに使用する新しいパスワード。 *パスワード*は**sysname**で、デフォルトはありません。  
  
`[ @use_default_credentials = ] use_default_credentials`サービスの資格情報を使用して SMTP サーバーにメールを送信するかどうかを指定[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]します。 **use_default_credentials**ビットで、デフォルトはありません。 このパラメーターが 1 の場合、データベース メールは[!INCLUDE[ssDE](../../includes/ssde-md.md)]の資格情報を使用します。 このパラメータが 0 の場合、データベース メールは SMTP サーバーでの認証に**\@ユーザー名**と**\@パスワード**を使用します。 **\@ユーザー名**と**\@パスワード**が NULL の場合、匿名認証が使用されます。 このパラメータを指定する前に、SMTP 管理者に相談する  
  
`[ @enable_ssl = ] enable_ssl`以前はセキュア ソケット レイヤ (SSL) と呼ばれていたトランスポート層セキュリティ (TLS) を使用して、データベース メールが通信を暗号化するかどうかを指定します。 SMTP サーバーで TLS が必要な場合は、このオプションを使用します。 **enable_ssl**はビットで、デフォルトはありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 アカウント名とアカウント ID の両方を指定すると、ストアド プロシージャはアカウントの情報を更新するだけでなく、アカウント名も変更します。 アカウント名の変更は、アカウント名のエラーを修正する場合に利用できます。  
  
 ストアド プロシージャ**sysmail_update_account_sp**は**msdb**データベースにあり **、dbo**スキーマによって所有されます。 現在のデータベースが**msdb**でない場合、プロシージャは 3 部構成の名前で実行する必要があります。  
  
## <a name="permissions"></a>アクセス許可  
 **sysadmin** 固定サーバー ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>例  
  
### <a name="a-changing-the-information-for-an-account"></a>A. アカウントの情報を変更する  
 次の例では`AdventureWorks Administrator`**、msdb**データベースのアカウントを更新します。 アカウントの情報は、提供された値に設定されます。  
  
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
  
### <a name="b-changing-the-name-of-an-account-and-the-information-for-an-account"></a>B. アカウントの名前とアカウントの情報の変更  
 次の例では、アカウント ID `125` の名前を変更し、アカウント情報を更新します。 アカウントの新しい名前は`Backup Mail Server`です。  
  
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
 [データベース メール アカウントの作成](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [データベース メール ストアド プロシージャ&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
