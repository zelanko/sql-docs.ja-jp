---
title: sysmail_add_profile_sp (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_add_profile_sp_TSQL
- sysmail_add_profile_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_add_profile_sp
ms.assetid: a828e55c-633a-41cf-9769-a0698b446e6c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b00e0eed5a27c9d795de027f82b01763c44ab80e
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58526484"
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
`[ @profile_name = ] 'profile\_name'` 新しいプロファイルの名前。 *profile_name*は**sysname**、既定値はありません。  
  
`[ @description = ] 'description'` 新しいプロファイルのオプションの説明。 *説明*は**nvarchar (256)**、既定値はありません。  
  
`[ @profile_id = ] _new\_profile\_idOUTPUT` 新しいプロファイルの ID を返します。 *new_profile_id*は**int**、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 データベース メール プロファイルは、データベース メール アカウントの任意の数を保持します。 データベース メールのストアド プロシージャでは、このプロシージャで生成されたプロファイル名またはプロファイル ID によって、プロファイルを参照できます。 アカウントをプロファイルに追加する方法の詳細については、次を参照してください。 [sysmail_add_profileaccount_sp &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-add-profileaccount-sp-transact-sql.md)します。  
  
 プロファイルの名前と説明は、ストアド プロシージャで変更できます**sysmail_update_profile_sp**プロファイル id は変わらず、プロファイルの有効期間中に、します。  
  
 プロファイル名は、Microsoft に対して一意である必要があります[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]またはストアド プロシージャがエラーを返します。  
  
 ストアド プロシージャ**sysmail_add_profile_sp**では、 **msdb**が所有するデータベースにあり、 **dbo**スキーマ。 現在のデータベースがない場合、3 つの部分の名前を持つプロシージャを実行する必要があります**msdb**します。  
  
## <a name="permissions"></a>アクセス許可  
 このプロシージャの既定のメンバーへのアクセス許可を実行、 **sysadmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
 **A.新しいプロファイルを作成します。**  
  
 次の例では、`AdventureWorks Administrator` という新しいデータベース メール プロファイルを作成します。  
  
```  
EXECUTE msdb.dbo.sysmail_add_profile_sp  
       @profile_name = 'AdventureWorks Administrator',  
       @description = 'Profile used for administrative mail.' ;  
```  
  
 **B.プロファイル id を変数に保存、新しいプロファイルを作成します。**  
  
 次の例では、`AdventureWorks Administrator` という新しいデータベース メール プロファイルを作成します。 例では、プロファイル id 番号を変数に格納する`@profileId`し、新しいプロファイルのプロファイル id 番号を含む結果セットを返します。  
  
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
  
  
