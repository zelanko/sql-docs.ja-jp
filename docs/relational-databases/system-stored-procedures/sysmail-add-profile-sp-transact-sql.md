---
title: sysmail_add_profile_sp (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
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
- sysmail_add_profile_sp_TSQL
- sysmail_add_profile_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_add_profile_sp
ms.assetid: a828e55c-633a-41cf-9769-a0698b446e6c
caps.latest.revision: 37
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: aabeb2d0ed5230679e3e8605f415aceb3255f5a5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysmailaddprofilesp-transact-sql"></a>sysmail_add_profile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  新しいデータベース メール プロファイルを作成します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sysmail_add_profile_sp [ @profile_name = ] 'profile_name'  
    [ , [ @description = ] 'description' ]  
    [ , [ @profile_id = ] new_profile_id OUTPUT ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@profile_name** =] **'***profile_name***'**  
 新しいプロファイルの名前を指定します。 *profile_name*は**sysname**、既定値はありません。  
  
 [ **@description** =] **'***説明***'**  
 新しいプロファイルの説明を指定します (省略可能)。 *説明*は**nvarchar (256)**、既定値はありません。  
  
 [ **@profile_id** = ] *new_profile_id***OUTPUT**  
 新しいプロファイルの ID を返します。 *new_profile_id*は**int**、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 データベース メール プロファイルにはデータベース メール アカウントをいくつでも保持できます。 データベース メールのストアド プロシージャでは、このプロシージャで生成されたプロファイル名またはプロファイル ID によって、プロファイルを参照できます。 プロファイルにアカウントを追加する方法の詳細については、次を参照してください。 [sysmail_add_profileaccount_sp &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-add-profileaccount-sp-transact-sql.md)です。  
  
 ストアド プロシージャで、プロファイル名と説明を変更することができます**sysmail_update_profile_sp**プロファイル id は、プロファイルの有効期間中に、します。  
  
 プロファイル名は、Microsoft に対して一意である必要があります[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]か、ストアド プロシージャがエラーを返します。  
  
 ストアド プロシージャ**sysmail_add_profile_sp**では、 **msdb**が所有するデータベースにあり、 **dbo**スキーマです。 現在のデータベースがない場合は、3 部構成の名前を持つプロシージャを実行する必要があります**msdb**です。  
  
## <a name="permissions"></a>権限  
 メンバーにこのプロシージャの既定の実行権限、 **sysadmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
 **A.新しいプロファイルを作成します。**  
  
 次の例では、`AdventureWorks Administrator` という新しいデータベース メール プロファイルを作成します。  
  
```  
EXECUTE msdb.dbo.sysmail_add_profile_sp  
       @profile_name = 'AdventureWorks Administrator',  
       @description = 'Profile used for administrative mail.' ;  
```  
  
 **B.プロファイルの id を変数に保存、新しいプロファイルを作成します。**  
  
 次の例では、`AdventureWorks Administrator` という新しいデータベース メール プロファイルを作成します。 例では、プロファイル id 番号、変数に格納`@profileId`し、新しいプロファイルのプロファイル id 番号を含む結果セットを返します。  
  
```  
DECLARE @profileId INT ;  
  
EXECUTE msdb.dbo.sysmail_add_profile_sp  
       @profile_name = 'AdventureWorks Administrator',  
       @description = 'Profile used for administrative mail.',  
       @profile_id = @profileId OUTPUT ;  
  
SELECT @profileId ;  
```  
  
## <a name="see-also"></a>参照  
 [データベース メール](../../relational-databases/database-mail/database-mail.md)   
 [データベース メール アカウントを作成します。](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [データベース メール構成オブジェクト](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [データベース メール ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
