---
title: "sysmail_add_profileaccount_sp (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
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
- sysmail_add_profileaccount_sp
- sysmail_add_profileaccount_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_add_profileaccount_sp
ms.assetid: 7cbf430f-1997-45ea-9707-0086184de744
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a7755f8285ad6a9afcab7a79ce1eecc777fd4e1f
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysmailaddprofileaccountsp-transact-sql"></a>sysmail_add_profileaccount_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベース メール プロファイルにデータベース メール アカウントを追加します。 実行**sysmail_add_profileaccount_sp**データベース アカウントの作成後[sysmail_add_account_sp (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sysmail-add-account-sp-transact-sql.md)でデータベース プロファイルを作成および[sysmail_add_profile_sp &#40;です。TRANSACT-SQL と #41 です](../../relational-databases/system-stored-procedures/sysmail-add-profile-sp-transact-sql.md)。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sysmail_add_profileaccount_sp { [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' } ,  
    { [ @account_id = ] account_id | [ @account_name = ] 'account_name' }  
    [ , [ @sequence_number = ] sequence_number ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@profile_id** = ] *profile_id*  
 アカウントを追加するプロファイル ID を指定します。 *profile_id*は**int**、既定値は NULL です。 いずれか、 *profile_id*または*profile_name*指定する必要があります。  
  
 [ **@profile_name** = ] **'***profile_name***'**  
 アカウントを追加するプロファイル名を指定します。 *profile_name*は**sysname**、既定値は NULL です。 いずれか、 *profile_id*または*profile_name*指定する必要があります。  
  
 [ **@account_id** = ] *account_id*  
 プロファイルに追加するアカウント ID を指定します。 *account_id*は**int**、既定値は NULL です。 いずれか、 *account_id*または*account_name*指定する必要があります。  
  
 [  **@account_name**  =] **'***account_name***'**  
 プロファイルに追加するアカウント名を指定します。 *account_name*は**sysname**、既定値は NULL です。 いずれか、 *account_id*または*account_name*指定する必要があります。  
  
 [ **@sequence_number** = ] *sequence_number*  
 プロファイ内のアカウントのシーケンス番号。 *sequence_number*は**int**、既定値はありません。 シーケンス番号によって、プロファイルで使用されるアカウントの順番が決まります。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 プロファイルとアカウントの両方が既に存在している必要があります。 両方またはいずれかが存在しないと、このストアド プロシージャはエラーを返します。  
  
 このストアド プロシージャでは、指定したプロファイルに既に関連付けられているアカウントのシーケンス番号は変更されないことに注意してください。 アカウントのシーケンス番号の更新の詳細については、次を参照してください。 [sysmail_update_profileaccount_sp (& a) #40 です。TRANSACT-SQL と #41 です](../../relational-databases/system-stored-procedures/sysmail-update-profileaccount-sp-transact-sql.md)。  
  
 シーケンス番号によって、データベース メールではプロファイル内のアカウントがどの順番で使用されるかが決まります。 新しい電子メール メッセージの場合、データベース メールでは、一番小さなシーケンス番号の付いたアカウントから処理が開始されます。 そのアカウントが失敗すると、データベース メールでは、このアカウントよりも大きいシーケンス番号を持つアカウントに処理が移ります。このように、データベース メールによってメッセージが正常に送信されるか、一番大きなシーケンス番号のアカウントが失敗するまで順に処理されます。 最も番号が大きいアカウントで失敗した場合、 *sysmail_configure_sp* の **AccountRetryDelay**パラメーターで構成した時間、メールの送信が一時停止されます。その後、最も番号が小さいアカウントからメールの送信プロセスが再開されます。 *sysmail_configure_sp* の **AccountRetryAttempts**パラメーターは、指定されたプロファイルの各アカウントを使用して外部メール プロセスが電子メール メッセージを送信する回数を構成します。  
  
 同じシーケンス番号を持つ複数のアカウントが存在する場合は、データベース メールはに対してのみ使用それらのアカウントのいずれかの指定された電子メール メッセージ。 この場合、そのシーケンス番号に対してどのアカウントが使用されるか、またメッセージごとに同じアカウントが使用されるかついては、データベース メールでは保証されません。  
  
 ストアド プロシージャ**sysmail_add_profileaccount_sp**では、 **msdb**が所有するデータベースにあり、 **dbo**スキーマです。 現在のデータベースがない場合は、3 部構成の名前を持つプロシージャを実行する必要があります**msdb**です。  
  
## <a name="permissions"></a>権限  
 メンバーにこのプロシージャの既定の実行権限、 **sysadmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
 次の例は、プロファイルを関連付ける`AdventureWorks Administrator`アカウントを使用して`Audit Account`です。 監査アカウントのシーケンス番号は 1 です。  
  
```  
EXECUTE msdb.dbo.sysmail_add_profileaccount_sp  
    @profile_name = 'AdventureWorks Administrator',  
    @account_name = 'Audit Account',  
    @sequence_number = 1 ;  
```  
  
## <a name="see-also"></a>参照  
 [データベース メール](../../relational-databases/database-mail/database-mail.md)   
 [データベース メール アカウントを作成します。](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [データベース メール構成オブジェクト](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [データベース メールのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
