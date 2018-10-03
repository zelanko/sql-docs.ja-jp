---
title: sysmail_add_account_sp (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_add_account_sp
- sysmail_add_account_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_add_account_sp
ms.assetid: 65e15e2e-107c-49c3-b12c-f4edf0eb1617
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a388fb39082ec936b473afd7fc96ff99e7d92350
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47830020"
---
# <a name="sysmailaddaccountsp-transact-sql"></a>sysmail_add_account_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  SMTP アカウントの情報を保持する新しいデータベース メール アカウントを作成します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sysmail_add_account_sp  [ @account_name = ] 'account_name',  
    [ @email_address = ] 'email_address' ,  
    [ [ @display_name = ] 'display_name' , ]  
    [ [ @replyto_address = ] 'replyto_address' , ]  
    [ [ @description = ] 'description' , ]  
    [ @mailserver_name = ] 'server_name'   
    [ , [ @mailserver_type = ] 'server_type' ]  
    [ , [ @port = ] port_number ]  
    [ , [ @username = ] 'username' ]  
    [ , [ @password = ] 'password' ]  
    [ , [ @use_default_credentials = ] use_default_credentials ]  
    [ , [ @enable_ssl = ] enable_ssl ]  
    [ , [ @account_id = ] account_id OUTPUT ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@account_name** =] **'***account_name***'**  
 追加するアカウントの名前を指定します。 *account_name*は**sysname**、既定値はありません。  
  
 [ **@email_address** =] **'***email_address***'**  
 メッセージ送信元の電子メール アドレスを指定します。 このアドレスにはインターネット電子メール アドレスを指定する必要があります。 *email_address*は**nvarchar (128)**、既定値はありません。 たとえば、アカウントを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェントは、アドレスから電子メールを送信することがあります **SqlAgent@Adventure-Works.com**します。  
  
 [ **@display_name** =] **'***display_name***'**  
 このアカウントから送信する電子メール メッセージの表示名を指定します。 *display_name*は**nvarchar (128)**、既定値は NULL です。 たとえば、アカウントを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェントは、名前を表示できます**SQL Server Agent Automated Mailer**送信する電子メール メッセージ。  
  
 [ **@replyto_address** =] **'***replyto_address***'**  
 このアカウントから送信するメッセージに対する返信アドレスを指定します。 *replyto_address*は**nvarchar (128)**、既定値は NULL です。 などのアカウントへの返信[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェントは、データベース管理者に進んでください **danw@Adventure-Works.com**します。  
  
 [ **@description** =] **'***説明***'**  
 アカウントの説明を指定します。 *説明*は**nvarchar (256)**、既定値は NULL です。  
  
 [ **@mailserver_name** =] **'***server_name***'**  
 このアカウントで使用する SMTP メール サーバーの名前または IP アドレスを指定します。 実行するコンピューター[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]解決できる必要があります、 *server_name* IP アドレス。 *server_name*は**sysname**、既定値はありません。  
  
 [ **@mailserver_type** =] '*server_type*'  
 電子メール サーバーの種類を指定します。 *server_type*は**sysname**、既定値は **'SMTP'**.  
  
 [ **@port** =] *port_number*  
 電子メール サーバーのポート番号を指定します。 *port_number*は**int**、既定値は 25 です。  
  
 [ **@username** =] **'***username***'**  
 電子メール サーバーへのログオンに使用するユーザー名を指定します。 *ユーザー名*は**nvarchar (128)**、既定値は NULL です。 このパラメーターが NULL の場合、データベース メールではこのアカウントに対して認証が使用されません。 メール サーバーが認証を必要としない場合、ユーザー名には NULL を使用します。  
  
 [ **@password** =] **'***パスワード***'**  
 子メール サーバーへのログオンに使用するパスワードを指定します。 *パスワード*は**nvarchar (128)**、既定値は NULL です。 ユーザー名を指定しない場合、パスワードを設定する必要はありません。  
  
 [ **@use_default_credentials** =] use_default_credentials  
 資格情報を使用して SMTP サーバーにメールを送信するかどうかを指定します、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]します。 **use_default_credentials**ビットは、既定値は 0。 データベース メールでの資格情報を使用してこのパラメーターが 1 の場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)]します。 データベース メールではこのパラメーターが 0 の場合、 **@username**と**@password**存在する場合は、パラメーターなしのメールが送信されます**@username**と**@password**パラメーター。  
  
 [ **@enable_ssl** =] enable_ssl  
 データベース メールで Secure Sockets Layer を使用して通信を暗号化するかどうかを指定します。 **Enable_ssl**ビットは、既定値は 0。  
  
 [ **@account_id** =] *account_id*出力  
 新しいアカウントのアカウント ID を返します。 *account_id*は**int**、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>Remarks  
 データベース メールは、個別のパラメーターを提供します。 **@email_address**、 **@display_name**、および **@replyto_address**します。 **@email_address**パラメーターは、メッセージの送信元アドレス。 **@display_name**パラメーターは、名前に示すように、**から:** 電子メール メッセージのフィールド。 **@replyto_address**パラメーターは、アドレス、電子メール メッセージに返信が送信されます。 たとえば、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントで使用するアカウントでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントでのみ使用される電子メール アドレスから電子メール メッセージを送信できます。 受信者が簡単に判断するため、そのアドレスからのメッセージは、フレンドリ名を表示する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェントは、メッセージを送信します。 受信者がメッセージに返信した場合、その返信は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントで使用されるアドレスではなくデータベース管理者に送られます。 このシナリオで、アカウントを使用して**SqlAgent@Adventure-Works.com**として電子メール アドレス。 表示名に設定されて**SQL Server Agent Automated Mailer**します。 アカウントが使用する**danw@Adventure-Works.com**として、返信先アドレスでは、このアカウントから送信されたメッセージに返信ですからの電子メール アドレスではなく、データベース管理者に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント。 データベース メールではこれら 3 つのパラメーターに対して個別の値を設定できるため、ユーザーの必要に応じてメッセージを構成できます。  
  
 **@mailserver_type**パラメーターに値がサポートしている **'SMTP'** します。  
  
 ときに**@use_default_credentials**の資格情報を使用して SMTP サーバーに 1 のメールが送信されるは、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]します。 ときに**@use_default_credentials**は 0 です。 と**@username**と**@password**アカウント SMTP 認証を使用するアカウントに指定されます。 **@username**と**@password**アカウントがない資格情報、SMTP サーバーを使用する資格情報を[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]またはコンピューター上にあるネットワークです。  
  
 ストアド プロシージャ**sysmail_add_account_sp**では、 **msdb**が所有するデータベースにあり、 **dbo**スキーマ。 現在のデータベースがない場合、3 つの部分の名前を持つプロシージャを実行する必要があります**msdb**します。  
  
## <a name="permissions"></a>アクセス許可  
 このプロシージャの既定のメンバーへのアクセス許可を実行、 **sysadmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
 次の例では、という名前のアカウントを作成する`AdventureWorks Administrator`します。 アカウントの電子メール アドレスを使用する`dba@Adventure-Works.com`SMTP メール サーバーにメールを送信および`smtp.Adventure-Works.com`します。 このアカウントのスライド ショーから送信された電子メール メッセージ`AdventureWorks Automated Mailer`上、**から:** メッセージの行。 メッセージへの返信は `danw@Adventure-Works.com` に転送されます。  
  
```  
EXECUTE msdb.dbo.sysmail_add_account_sp  
    @account_name = 'AdventureWorks Administrator',  
    @description = 'Mail account for administrative e-mail.',  
    @email_address = 'dba@Adventure-Works.com',  
    @display_name = 'AdventureWorks Automated Mailer',  
    @mailserver_name = 'smtp.Adventure-Works.com' ;  
```  
  
## <a name="see-also"></a>関連項目  
 [データベース メール](../../relational-databases/database-mail/database-mail.md)   
 [データベース メール アカウントを作成します。](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [データベース メール ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
