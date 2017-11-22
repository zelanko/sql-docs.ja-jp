---
title: "sysmail_add_account_sp (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysmail_add_account_sp
- sysmail_add_account_sp_TSQL
dev_langs: TSQL
helpviewer_keywords: sysmail_add_account_sp
ms.assetid: 65e15e2e-107c-49c3-b12c-f4edf0eb1617
caps.latest.revision: "40"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1dd46ec4c54cb70c37a8d37d9273b490fa1008ee
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysmailaddaccountsp-transact-sql"></a>sysmail_add_account_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  SMTP アカウントの情報を保持する新しいデータベース メール アカウントを作成します。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|  
  
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
 [  **@account_name**  =] **'***account_name***'**  
 追加するアカウントの名前を指定します。 *account_name*は**sysname**、既定値はありません。  
  
 [  **@email_address**  =] **'***email_address***'**  
 メッセージ送信元の電子メール アドレスを指定します。 このアドレスにはインターネット電子メール アドレスを指定する必要があります。 *email_address*は**nvarchar (128)**、既定値はありません。 たとえば、アカウントを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェントは、アドレスから電子メールを送信することがあります **SqlAgent@Adventure-Works.com**です。  
  
 [  **@display_name**  =] **'***display_name***'**  
 このアカウントから送信する電子メール メッセージの表示名を指定します。 *display_name*は**nvarchar (128)**、既定値は NULL です。 たとえば、アカウントを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェントは、名前を表示できます**SQL Server Agent Automated Mailer**電子メール メッセージにします。  
  
 [  **@replyto_address**  =] **'***replyto_address***'**  
 このアカウントから送信するメッセージに対する返信アドレスを指定します。 *replyto_address*は**nvarchar (128)**、既定値は NULL です。 アカウントへの返信など[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェントは、データベース管理者になる可能性がある **danw@Adventure-Works.com**です。  
  
 [  **@description**  =] **'***説明***'**  
 アカウントの説明を指定します。 *説明*は**nvarchar (256)**、既定値は NULL です。  
  
 [  **@mailserver_name**  =] **'***server_name***'**  
 このアカウントで使用する SMTP メール サーバーの名前または IP アドレスを指定します。 実行するコンピューター[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]解決できる必要があります、 *server_name* IP アドレス。 *server_name*は**sysname**、既定値はありません。  
  
 [  **@mailserver_type**  =] '*server_type*'  
 電子メール サーバーの種類を指定します。 *server_type*は**sysname**、既定値は**'SMTP'**.  
  
 [  **@port**  =] *port_number*  
 電子メール サーバーのポート番号を指定します。 *port_number*は**int**、既定値は 25 です。  
  
 [  **@username**  =] **'***username***'**  
 電子メール サーバーへのログオンに使用するユーザー名を指定します。 *ユーザー名*は**nvarchar (128)**、既定値は NULL です。 このパラメーターが NULL の場合、データベース メールではこのアカウントに対して認証が使用されません。 メール サーバーが認証を必要としない場合、ユーザー名には NULL を使用します。  
  
 [  **@password**  =] **'***パスワード***'**  
 子メール サーバーへのログオンに使用するパスワードを指定します。 *パスワード*は**nvarchar (128)**、既定値は NULL です。 ユーザー名を指定しない場合、パスワードを設定する必要はありません。  
  
 [  **@use_default_credentials**  =] use_default_credentials  
 資格情報を使用して SMTP サーバーにメールを送信するかどうかを指定します、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]です。 **use_default_credentials**は bit で、既定値は 0 です。 データベース メールがの資格情報を使用してこのパラメーターが 1 の場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)]です。 このパラメーターが 0 の場合は、データベース メールを送信、  **@username** と **@password** 存在する場合、パラメーターなしでメールが送信 **@username** と **@password** パラメーター。  
  
 [  **@enable_ssl**  =] enable_ssl  
 データベース メールで Secure Sockets Layer を使用して通信を暗号化するかどうかを指定します。 **Enable_ssl**は bit で、既定値は 0 です。  
  
 [  **@account_id**  =] *account_id*出力  
 新しいアカウントのアカウント ID を返します。 *account_id*は**int**、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 データベース メールを使用する個別のパラメーター  **@email_address** 、  **@display_name** 、および **@replyto_address**です。 **@email_address** パラメーターは、メッセージの送信元となるアドレスです。 **@display_name** パラメーターは、名前に示すように、**から:**電子メール メッセージのフィールドです。 **@replyto_address** パラメーターは、アドレス、電子メール メッセージに返信が送信されます。 たとえば、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントで使用するアカウントでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントでのみ使用される電子メール アドレスから電子メール メッセージを送信できます。 受信者が容易に判別するため、そのアドレスからのメッセージはフレンドリ名を表示する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェントは、メッセージを送信します。 受信者がメッセージに返信した場合、その返信は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントで使用されるアドレスではなくデータベース管理者に送られます。 このシナリオでは、アカウントが使用する **SqlAgent@Adventure-Works.com** として電子メール アドレス。 表示名に設定されている**SQL Server Agent Automated Mailer**です。 アカウントが使用する **danw@Adventure-Works.com** として、返信先アドレスでは、このアカウントから送信されたメッセージへの返信それでの電子メール アドレスではなく、データベース管理者に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェントです。 データベース メールではこれら 3 つのパラメーターに対して個別の値を設定できるため、ユーザーの必要に応じてメッセージを構成できます。  
  
 **@mailserver_type** パラメーター値をサポートする**'SMTP'**です。  
  
 ときに **@use_default_credentials** の資格情報を使用して SMTP サーバーに 1 のメールが送信されるは、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]です。 ときに **@use_default_credentials**  0 は、および **@username** と **@password** が指定されて、アカウントのアカウントは、SMTP 認証を使用します。 **@username** と **@password** アカウントが、SMTP サーバーのない資格情報を使用する資格情報は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]またはコンピューター上にあるネットワークです。  
  
 ストアド プロシージャ**sysmail_add_account_sp**では、 **msdb**が所有するデータベースにあり、 **dbo**スキーマです。 現在のデータベースがない場合は、3 部構成の名前を持つプロシージャを実行する必要があります**msdb**です。  
  
## <a name="permissions"></a>Permissions  
 メンバーにこのプロシージャの既定の実行権限、 **sysadmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
 次の例は、という名前のアカウントを作成`AdventureWorks Administrator`です。 アカウントが使用する電子メール アドレス`dba@Adventure-Works.com`SMTP メール サーバーにメールを送信および`smtp.Adventure-Works.com`です。 このアカウントのスライド ショーから送信された電子メール メッセージ`AdventureWorks Automated Mailer`上、**から:**メッセージの行。 メッセージへの返信は `danw@Adventure-Works.com` に転送されます。  
  
```  
EXECUTE msdb.dbo.sysmail_add_account_sp  
    @account_name = 'AdventureWorks Administrator',  
    @description = 'Mail account for administrative e-mail.',  
    @email_address = 'dba@Adventure-Works.com',  
    @display_name = 'AdventureWorks Automated Mailer',  
    @mailserver_name = 'smtp.Adventure-Works.com' ;  
```  
  
## <a name="see-also"></a>参照  
 [データベース メール](../../relational-databases/database-mail/database-mail.md)   
 [データベース メール アカウントを作成します。](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [データベース メールのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
