---
title: "sysmail_help_account_sp (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sysmail_help_account_sp_TSQL
- sysmail_help_account_sp
dev_langs: TSQL
helpviewer_keywords: sysmail_help_account_sp
ms.assetid: 87c7c39c-8e05-4e68-9272-45f908809c3b
caps.latest.revision: "48"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b586334d1b725922ec38b3ed63e6cfc8eb0847a7
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysmailhelpaccountsp-transact-sql"></a>sysmail_help_account_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベース メール アカウントに関する、パスワード以外の情報を一覧表示します。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sysmail_help_account_sp [ [ @account_id = ] account_id | [ @account_name = ] 'account_name' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@account_id**  =] *account_id*  
 情報を一覧表示するアカウントのアカウント ID を指定します。 *account_id*は**int**、既定値は NULL です。  
  
 [  **@account_name**  =] **'***account_name***'**  
 情報を一覧表示するアカウントの名前を指定します。 *account_name*は**sysname**、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 次の列を含む結果セットを返します。  
  
||||  
|-|-|-|  
|列名|データ型|Description|  
|**account_id**|**int**|アカウントの ID。|  
|**name**|**sysname**|アカウントの名前。|  
|**説明**|**nvarchar (256)**|アカウントの説明。|  
|**email_address**|**nvarchar (128)**|メッセージ送信元の電子メール アドレス。|  
|**display_name**|**nvarchar (128)**|アカウントの表示名。|  
|**replyto_address**|**nvarchar (128)**|このアカウントからのメッセージに対する返信アドレス。|  
|**servertype**|**sysname**|アカウントで使用されている電子メール サーバーの種類。|  
|**サーバー名**|**sysname**|アカウントで使用されている電子メール サーバーの名前。|  
|**port**|**int**|電子メール サーバーで使用されているポート番号。|  
|**ユーザー名**|**nvarchar (128)**|電子メール サーバーで認証が使用されている場合に、電子メール サーバーへのサインインに使用するユーザー名。 ときに**username**が NULL の場合、データベース メールは、このアカウントの認証を使用しません。|  
|**use_default_credentials**|**bit**|資格情報を使用して SMTP サーバーにメールを送信するかどうかを指定します、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]です。 **use_default_credentials**は bit で、既定値はありません。 データベース メールがの資格情報を使用してこのパラメーターが 1 の場合、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]サービス。 データベース メールを使用してこのパラメーターが 0 の場合、  **@username** と **@password**  SMTP サーバーでの認証にします。 場合 **@username** と **@password**  NULL の場合は、データベース メールで匿名認証を使用します。 このパラメーターを指定する前に、SMTP 管理者に問い合わせてください。|  
|**enable_ssl**|**bit**|データベース メールで SSL (Secure Sockets Layer) を使用して通信を暗号化するかどうかを指定します。 SMTP サーバーで SSL が必要な場合はこのオプションを使用します。 **enable_ssl**は bit で、既定値はありません。 1 の場合、データベース メールでは SSL を使用して通信を暗号化することを示します。 0 の場合、データベース メールでは SSL 暗号化を使用せずにメールを送信することを示します。|  
  
## <a name="remarks"></a>解説  
 ない場合*account_id*または*account_name*が提供される、 **sysmail_help_account** Microsoft SQL Server インスタンス内のすべてのデータベース メール アカウント情報を一覧表示します。  
  
 ストアド プロシージャ**sysmail_help_account_sp**では、 **msdb**が所有するデータベースにあり、 **dbo**スキーマです。 現在のデータベースがない場合は、3 部構成の名前を持つプロシージャを実行する必要があります**msdb**です。  
  
## <a name="permissions"></a>Permissions  
 メンバーにこのプロシージャの既定の実行権限、 **sysadmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
 **A.すべてのアカウントの情報を一覧表示します。**  
  
 次の例では、インスタンス内のすべてのアカウントについて、アカウント情報を一覧表示します。  
  
```  
EXECUTE msdb.dbo.sysmail_help_account_sp ;  
```  
  
 行の長さの編集、サンプルの結果セットを次に示します。  
  
```  
account_id  name                         description                             email_address             display_name                     replyto_address servertype servername                port        username use_default_credentials enable_ssl  
----------- ---------------------------- --------------------------------------- ------------------------- -------------------------------- --------------- ---------- ------------------------- ----------- -------- ----------------------- ----------  
148         AdventureWorks Administrator Mail account for administrative e-mail. dba@Adventure-Works.com   AdventureWorks Automated Mailer  NULL            SMTP       smtp.Adventure-Works.com  25          NULL 0                          0        
149         Audit Account                Account for audit e-mail.               audit@Adventure-Works.com Automated Mailer (Audit)         NULL            SMTP       smtp.Adventure-Works.com  25          NULL 0                          0        
```  
  
 **B.特定のアカウントの情報を一覧表示します。**  
  
 次の例では、`AdventureWorks Administrator` というアカウントについて、アカウント情報を一覧表示します。  
  
```  
EXECUTE msdb.dbo.sysmail_help_account_sp  
    @account_name = 'AdventureWorks Administrator' ;  
```  
  
 行の長さの編集、サンプルの結果セットを次に示します。  
  
```  
account_id  name                         description                             email_address             display_name                     replyto_address servertype servername                port        username use_default_credentials enable_ssl  
----------- ---------------------------- ------------------------------------------------------ ------------------------- ---------------- ---------- ------------------------- ----------- -------- ----------------------- ----------  
148         AdventureWorks Administrator Mail account for administrative e-mail. dba@Adventure-Works.com   AdventureWorks Automated Mailer  NULL            SMTP       smtp.Adventure-Works.com  25          NULL     0                       0       
```  
  
## <a name="see-also"></a>参照  
 [データベース メール](../../relational-databases/database-mail/database-mail.md)   
 [データベース メール アカウントを作成します。](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [データベース メールのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
