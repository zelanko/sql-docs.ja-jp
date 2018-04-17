---
title: sysmail_delete_account_sp (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
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
- sysmail_delete_account_sp
- sysmail_delete_account_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_delete_account_sp
ms.assetid: 2adcac78-4a4a-407e-9666-1d9c43c73cc2
caps.latest.revision: 40
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a103d5e5c5127e65fdfd103ade26a0ce298159d0
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sysmaildeleteaccountsp-transact-sql"></a>sysmail_delete_account_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベース メールの SMTP アカウントを削除します。 データベース メール構成ウィザードを使用してアカウントを削除することもできます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sysmail_delete_account_sp { [ @account_id = ] account_id | [ @account_name = ] 'account_name' }   
```  
  
## <a name="arguments"></a>引数  
 [ **@account_id** =] *account_id*  
 削除するアカウントの ID 番号を指定します。 *account_id*は**int**、既定値はありません。 いずれか*account_id*または*account_name*指定する必要があります。  
  
 [ **@account_name** =] **'***account_name***'**  
 削除するアカウントの名前を指定します。 *account_name*は**sysname**、既定値はありません。 いずれか*account_id*または*account_name*指定する必要があります。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 このプロシージャでは、アカウントがプロファイルによって使用されているかどうかに関係なく、指定したアカウントが削除されます。 アカウントを含まないプロファイルでは、正常に電子メールを送信できません。  
  
 ストアド プロシージャ**sysmail_delete_account_sp**では、 **msdb**が所有するデータベースにあり、 **dbo**スキーマです。 現在のデータベースがない場合は、3 部構成の名前を持つプロシージャを実行する必要があります**msdb**です。  
  
## <a name="permissions"></a>権限  
 メンバーにこのプロシージャの既定の実行権限、 **sysadmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
 次の例は、という名前のデータベース メール アカウントを削除する`AdventureWorks Administrator`です。  
  
```  
EXECUTE msdb.dbo.sysmail_delete_account_sp  
    @account_name = 'AdventureWorks Administrator' ;  
```  
  
## <a name="see-also"></a>参照  
 [データベース メール](../../relational-databases/database-mail/database-mail.md)   
 [データベース メール アカウントを作成します。](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [データベース メール構成オブジェクト](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [sysmail_add_account_sp &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-add-account-sp-transact-sql.md)   
 [sysmail_delete_profile_sp &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-delete-profile-sp-transact-sql.md)   
 [sysmail_delete_profileaccount_sp &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-delete-profileaccount-sp-transact-sql.md)   
 [sysmail_help_account_sp &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-help-account-sp-transact-sql.md)   
 [sysmail_help_profile_sp &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-help-profile-sp-transact-sql.md)   
 [sysmail_help_profileaccount_sp &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-help-profileaccount-sp-transact-sql.md)   
 [sysmail_update_profileaccount_sp &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-update-profileaccount-sp-transact-sql.md)  
  
  
