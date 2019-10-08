---
title: sysmail_add_account_sp (Transact-sql) |Microsoft Docs
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
ms.openlocfilehash: 32b8c8b1bbac53b099afc64f06a0eb5137292555
ms.sourcegitcommit: 454270de64347db917ebe41c081128bd17194d73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72006093"
---
# <a name="sysmail_add_account_sp-transact-sql"></a>sysmail_add_account_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  SMTP アカウントに関する情報を保持する新しいデータベースメールアカウントを作成します。  
  
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
`[ @account_name = ] 'account_name'` 追加するアカウントの名前。 *account_name*は**sysname**,、既定値はありません。  
  
`[ @email_address = ] 'email_address'` メッセージの送信元の電子メールアドレス。 このアドレスは、インターネット電子メールアドレスである必要があります。 *email_address*は**nvarchar (128)** ,、既定値はありません。 たとえば、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのアカウントは、アドレス **SqlAgent@Adventure-Works.com** から電子メールを送信できます。  
  
`[ @display_name = ] 'display_name'` このアカウントからの電子メールメッセージに使用する表示名。 *display_name*は**nvarchar (128)** ,、既定値は NULL です。 たとえば、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのアカウントには、電子メールメッセージに**自動メーラー SQL Server エージェント**名前が表示される場合があります。  
  
`[ @replyto_address = ] 'replyto_address'` このアカウントからのメッセージに対する応答の送信先アドレス。 *replyto_address*は**nvarchar (128)** ,、既定値は NULL です。 たとえば、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのアカウントへの返信は、データベース管理者である **danw@Adventure-Works.com** に送られる場合があります。  
  
`[ @description = ] 'description'` は、アカウントの説明です。 *説明*は**nvarchar (256)** ,、既定値は NULL です。  
  
`[ @mailserver_name = ] 'server_name'` には、このアカウントに使用する SMTP メールサーバーの名前または IP アドレスを指定します。 @No__t-0 を実行するコンピューターは、 *server_name*を IP アドレスに解決できる必要があります。 *server_name*は**sysname**,、既定値はありません。  
  
`[ @mailserver_type = ] 'server_type'` 電子メールサーバーの種類。 *server_type*は**sysname**,、既定値は **' SMTP '** . です。  
  
`[ @port = ] port_number` 電子メールサーバーのポート番号。 *port_number*は**int**,、既定値は25です。  
  
`[ @username = ] 'username'` 電子メールサーバーへのログオンに使用するユーザー名。 *username*は**nvarchar (128)** ,、既定値は NULL です。 このパラメーターが NULL の場合、データベースメールはこのアカウントに対して認証を使用しません。 メールサーバーで認証を必要としない場合は、ユーザー名に NULL を使用します。  
  
`[ @password = ] 'password'` は、電子メールサーバーへのログオンに使用するパスワードです。 *パスワード*は**nvarchar (128)** ,、既定値は NULL です。 ユーザー名を指定しない限り、パスワードを入力する必要はありません。  
  
`[ @use_default_credentials = ] use_default_credentials` @no__t の資格情報を使用して SMTP サーバーにメールを送信するかどうかを指定します。 **use_default_credentials**はビット,、既定値は0です。 このパラメーターが1の場合、データベースメールは [!INCLUDE[ssDE](../../includes/ssde-md.md)] の資格情報を使用します。 このパラメーターが0の場合、データベースメールは **\@username**と **\@password**パラメーターが存在する場合はそれを送信し、それ以外の場合は **\@username**パラメーターと **\@password**パラメーターを指定せずにメールを送信します。  
  
`[ @enable_ssl = ] enable_ssl` データベースメール Secure Sockets Layer を使用して通信を暗号化するかどうかを指定します。 **Enable_ssl**はビット,、既定値は0です。  
  
`[ @account_id = ] account_id OUTPUT` は、新しいアカウントのアカウント id を返します。 *account_id*は**int**,、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 データベースメールには、 **@no__t 1email_address**、 **\@display_name**、および **\@replyto_address**に個別のパラメーターが用意されています。 **@No__t 1email_address**パラメーターは、メッセージの送信元のアドレスです。 **@No__t 1display_name**パラメーターは、電子メールメッセージの **[差出人]** フィールドに表示される名前です。 **@No__t 1replyto_address**パラメーターは、電子メールメッセージへの返信が送信されるアドレスです。 たとえば、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントで使用するアカウントでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントでのみ使用される電子メール アドレスから電子メール メッセージを送信できます。 そのアドレスからのメッセージにはフレンドリ名が表示されるので、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントがメッセージを送信したことを受信者が簡単に判断できます。 受信者がメッセージに返信した場合、その返信は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントで使用されるアドレスではなくデータベース管理者に送られます。 このシナリオでは、アカウントは電子メールアドレスとして **SqlAgent@Adventure-Works.com** を使用します。 表示名は**SQL Server エージェント自動メーラ**に設定されます。 アカウントは **danw@Adventure-Works.com** を返信アドレスとして使用するので、このアカウントから送信されたメッセージへの返信は、@no__t エージェントの電子メールアドレスではなく、データベース管理者に送られます。 これら3つのパラメーターに個別の設定を指定することにより、データベースメールによって、必要に応じてメッセージを構成できます。  
  
 1mailserver_type パラメーターは、値 **' SMTP '** をサポートし **@no__t**ています。  
  
 1use_default_credentials が1の **@no__t**場合、@no__t の資格情報を使用して SMTP サーバーにメールが送信されます。 **@No__t**が0で、アカウントに **\@username**と **\@password**が指定されている場合、アカウントは SMTP 認証を使用します。 **@No__t-1 ユーザー名**と **\@password**は、アカウントが SMTP サーバーに使用する資格情報であり、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] またはコンピューターがあるネットワークの資格情報ではありません。  
  
 ストアドプロシージャ**sysmail_add_account_sp**は**msdb**データベースにあり、 **dbo**スキーマが所有しています。 現在のデータベースが**msdb**でない場合は、3つの部分で構成される名前を使用してプロシージャを実行する必要があります。  
  
## <a name="permissions"></a>アクセス許可  
 このプロシージャの実行権限は、既定では**sysadmin**固定サーバーロールのメンバーに与えています。  
  
## <a name="examples"></a>使用例  
 次の例では、`AdventureWorks Administrator` という名前のアカウントを作成します。 アカウントは、電子メールアドレス `dba@Adventure-Works.com` を使用し、SMTP メールサーバー `smtp.Adventure-Works.com` にメールを送信します。 このアカウントから送信された電子メールメッセージは、メッセージの **[差出人]** 行に `AdventureWorks Automated Mailer` と表示されます。 メッセージへの返信は `danw@Adventure-Works.com` に転送されます。  
  
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
 [データベースメールアカウント   を作成し](../../relational-databases/database-mail/create-a-database-mail-account.md)ます。  
 [ストアドプロシージャ&#40;のデータベースメール transact-sql&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
