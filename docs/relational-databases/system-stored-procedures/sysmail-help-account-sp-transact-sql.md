---
title: sysmail_help_account_sp (トランザクション-SQL) |マイクロソフトドキュメント
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
ms.openlocfilehash: ccb5cfd245148c97288a34b1857955f48f3efc73
ms.sourcegitcommit: 1a96abbf434dfdd467d0a9b722071a1ca1aafe52
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81528416"
---
# <a name="sysmail_help_account_sp-transact-sql"></a>sysmail_help_account_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベース メール アカウントに関する、パスワード以外の情報を一覧表示します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sysmail_help_account_sp [ [ @account_id = ] account_id | [ @account_name = ] 'account_name' ]  
```  
  
## <a name="arguments"></a>引数  
`[ @account_id = ] account_id`情報を一覧表示するアカウントのアカウント ID。 *account_id*は**int**で、デフォルトは NULL です。  
  
`[ @account_name = ] 'account_name'`情報を一覧表示するアカウントの名前。 *account_name*は**sysname**で、デフォルトは NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 以下にリストされている列を含む結果セットを返します。  
  
||||  
|-|-|-|  
|列名|データ型|説明|  
|**account_id**|**int**|アカウントの ID。|  
|**name**|**sysname**|アカウントの名前。|  
|**説明**|**nvarchar(256)**|アカウントの説明。|  
|**email_address**|**nvarchar(128)**|メッセージの送信先の電子メール アドレス。|  
|**display_name**|**nvarchar(128)**|アカウントの表示名。|  
|**replyto_address**|**nvarchar(128)**|このアカウントからのメッセージに対する返信アドレス。|  
|**サーバーの種類**|**sysname**|アカウントの電子メール サーバーの種類。|  
|**Servername**|**sysname**|アカウントの電子メール サーバーの名前。|  
|**ポート**|**int**|電子メール サーバーが使用するポート番号。|  
|**username**|**nvarchar(128)**|電子メール サーバーが認証を使用する場合に、電子メール サーバーへのサインインに使用するユーザー名。 **ユーザー名**が NULL の場合、データベース メールはこのアカウントの認証を使用しません。|  
|**use_default_credentials**|**bit**|の資格情報を使用して SMTP サーバーにメールを送信するかどうかを指定します[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]。 **use_default_credentials**ビットで、デフォルトはありません。 このパラメーターが 1 の場合、データベース メールはサービス[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]の資格情報を使用します。 このパラメータが 0 の場合、データベース メールは SMTP サーバーでの認証に**\@ユーザー名**と**\@パスワード**を使用します。 **\@ユーザー名**と**\@パスワード**が NULL の場合、データベース メールは匿名認証を使用します。 このパラメータを指定する前に、SMTP 管理者に相談してください。|  
|**enable_ssl**|**bit**|以前はセキュア ソケット レイヤ (SSL) と呼ばれていたトランスポート層セキュリティ (TLS) を使用して、データベース メールが通信を暗号化するかどうかを指定します。 SMTP サーバーで TLS が必要な場合は、このオプションを使用します。 **enable_ssl**はビットで、デフォルトはありません。 1 は、データベース メールが TLS を使用して通信を暗号化する場合を示します。 0 は、データベース メールが TLS 暗号化なしでメールを送信したことを示します。|  
  
## <a name="remarks"></a>解説  
 *account_id*または*account_name*が提供されていない場合 **、sysmail_help_account**は、Microsoft SQL Server インスタンス内のすべてのデータベース メール アカウントに関する情報を一覧表示します。  
  
 ストアド プロシージャ**sysmail_help_account_sp**は**msdb**データベースにあり **、dbo**スキーマによって所有されます。 現在のデータベースが**msdb**でない場合、プロシージャは 3 部構成の名前で実行する必要があります。  
  
## <a name="permissions"></a>アクセス許可  
 この手順の実行アクセス許可は、既定で**sysadmin**固定サーバー ロールのメンバに設定されます。  
  
## <a name="examples"></a>例  
 **A. すべてのアカウントの情報を一覧表示する**  
  
 次の例は、インスタンス内のすべてのアカウントのアカウント情報を一覧表示します。  
  
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
  
 **B. 特定のジョブに関する情報を一覧表示する**  
  
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
 [データベース メール アカウントの作成](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [データベース メール ストアド プロシージャ&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
