---
title: sysmail_add_principalprofile_sp (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_add_principalprofile_sp_TSQL
- sysmail_add_principalprofile_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_add_principalprofile_sp
ms.assetid: b2a0b313-abb9-4c23-8511-db77ca8172b3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 794a7c9013fff188500c26232a597a7dd4c6283d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47756278"
---
# <a name="sysmailaddprincipalprofilesp-transact-sql"></a>sysmail_add_principalprofile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベース ユーザーやロールに対して、データベース メール プロファイルを使用する権限を与えます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sysmail_add_principalprofile_sp  { [ @principal_id = ] principal_id | [ @principal_name = ] 'principal_name' } ,  
    { [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' }  
    [ , [ @is_default ] = 'is_default' ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@principal_id** =] *principal_id*  
 データベース ユーザーまたはロールの ID、 **msdb**アソシエーションのデータベースです。 *principal_id*は**int**、既定値は NULL です。 いずれか*principal_id*または*principal_name*指定する必要があります。 A *principal_id*の**0**使用するこのプロファイルはパブリック プロファイルをデータベース内のすべてのプリンシパルにアクセスを許可します。  
  
 [ **@principal_name** =] **'***principal_name***'**  
 データベース ユーザーまたはロールの名前、 **msdb**アソシエーションのデータベースです。 *principal_name*は**sysname**、既定値は NULL です。 いずれか*principal_id*または*principal_name*指定する必要があります。 A *principal_name*の **'public'** 使用するこのプロファイルはパブリック プロファイルをデータベース内のすべてのプリンシパルにアクセスを許可します。  
  
 [ **@profile_id** = ] *profile_id*  
 関連付けに使用するプロファイルの ID を指定します。 *profile_id*は**int**、既定値は NULL です。 いずれか*profile_id*または*profile_name*指定する必要があります。  
  
 [ **@profile_name** =] **'***profile_name***'**  
 関連付けに使用するプロファイルの名前を指定します。 *profile_name*は**sysname**、既定値はありません。 いずれか*profile_id*または*profile_name*指定する必要があります。  
  
 [ **@is_default** =] *is_default*  
 このプロファイルをプリンシパルの既定のプロファイルとするかどうかを指定します。 プリンシパルは既定のプロファイルを 1 つだけ持つ必要があります。 *is_default*は**ビット**、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 プロファイルをパブリックにするために、指定、 **@principal_id**の**0**または**@principal_name**の**パブリック**します。 パブリック プロファイルは、すべてのユーザーに使用可能な**msdb**データベース、ユーザーは、のメンバーでもある必要がありますが**DatabaseMailUserRole**を実行する**sp_send_dbmail**します。  
  
 データベース ユーザーが持つことのできる既定のプロファイルは 1 つだけです。 ときに**@is_default**は '**1**' し、ユーザーは、既に 1 つまたは複数のプロファイルに関連付け、指定されたプロファイルがユーザーの既定のプロファイルになります。 それまで既定のプロファイルであったプロファイルは、引き続きこのユーザーに関連付けられますが、既定のプロファイルではなくなります。  
  
 ときに**@is_default**は '**0**' とその他の関連付けがない場合、ストアド プロシージャには、エラーが返されます。  
  
 ストアド プロシージャ**sysmail_add_principalprofile_sp**では、 **msdb**が所有するデータベースにあり、 **dbo**スキーマ。 現在のデータベースがない場合、3 つの部分の名前を持つプロシージャを実行する必要があります**msdb**します。  
  
## <a name="permissions"></a>アクセス許可  
 このプロシージャの既定のメンバーへのアクセス許可を実行、 **sysadmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
 **A.既定のプロファイルを設定して、アソシエーションの作成**  
  
 次の例では、という名前のプロファイル間のアソシエーションを作成する`AdventureWorks Administrator Profile`と**msdb**データベース ユーザー`ApplicationUser`します。 このプロファイルは、このユーザーの既定のプロファイルです。  
  
```  
EXECUTE msdb.dbo.sysmail_add_principalprofile_sp  
    @principal_name = 'ApplicationUser',  
    @profile_name = 'AdventureWorks Administrator Profile',  
    @is_default = 1 ;  
```  
  
 **B.プロファイルの既定のパブリック プロファイルを作成します。**  
  
 次の例では、プロファイル`AdventureWorks Public Profile`内のユーザーの既定のパブリック プロファイル、 **msdb**データベース。  
  
```  
EXECUTE msdb.dbo.sysmail_add_principalprofile_sp  
    @principal_name = 'public',  
    @profile_name = 'AdventureWorks Public Profile',  
    @is_default = 1 ;  
```  
  
## <a name="see-also"></a>参照  
 [データベース メール](../../relational-databases/database-mail/database-mail.md)   
 [データベース メール構成オブジェクト](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [データベース メール ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
