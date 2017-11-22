---
title: "sysmail_update_principalprofile_sp (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
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
- sysmail_update_principalprofile_sp
- sysmail_update_principalprofile_sp_TSQL
dev_langs: TSQL
helpviewer_keywords: sysmail_update_principalprofile_sp
ms.assetid: 9fe96e9a-4758-4e4a-baee-3e1217c4426c
caps.latest.revision: "46"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b988aa656b4285218b51ce1bcd091f5381ffc411
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysmailupdateprincipalprofilesp-transact-sql"></a>sysmail_update_principalprofile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  プリンシパルとプロファイルの関連付けについての情報を更新します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sysmail_update_principalprofile_sp { @principal_id = principal_id | @principal_name = 'principal_name' } ,  
    { [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' } ,  
    [ @is_default = ] 'is_default'  
```  
  
## <a name="arguments"></a>引数  
 [  **@principal_id**  =] *principal_id*  
 データベース ユーザーまたはロールの ID、 **msdb**の関連付けを変更するデータベース。 *principal_id*は**int**、既定値は NULL です。 いずれか*principal_id*または*principal_name*指定する必要があります。  
  
 [  **@principal_name**  =] **'***principal_name***'**  
 データベース ユーザーまたはロールの名前、 **msdb**データベースの関連付けを更新します。 *principal_name*は**sysname**、既定値は NULL です。 いずれか*principal_id*または*principal_name*指定することがあります。  
  
 [  **@profile_id**  =] *profile_id*  
 関連付けを変更するプロファイルの ID を指定します。 *profile_id*は**int**、既定値は NULL です。 いずれか*profile_id*または*profile_name*指定する必要があります。  
  
 [  **@profile_name**  =] **'***profile_name***'**  
 関連付けを変更するプロファイルの名前を指定します。 *profile_name*は**sysname**、既定値は NULL です。 いずれか*profile_id*または*profile_name*指定する必要があります。  
  
 [  **@is_default**  =] **'***is_default***'**  
 このプロファイルがデータベース ユーザーの既定のプロファイルかどうかを指定します。 データベース ユーザーが持つことのできる既定のプロファイルは 1 つだけです。 *is_default*は**ビット**、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 このストアド プロシージャでは、指定したプロファイルを、データベース ユーザーの既定のプロファイルにするかどうかを変更します。 データベース ユーザーが持つことのできる既定のプライベート プロファイルは 1 つだけです。  
  
 アソシエーションのプリンシパルの名前は、いつ**パブリック**またはアソシエーションのプリンシパルの id は**0**、このストアド プロシージャは、パブリック プロファイルを変更します。 既定のパブリック プロファイルは 1 つしか存在できません。  
  
 ときに **@is_default** は '**1**' と、プリンシパルが複数のプロファイルに関連付けられた、指定されたプロファイルのプリンシパルの既定のプロファイルになります。 それまで既定のプロファイルであったプロファイルは、引き続きプリンシパルに関連付けられますが、既定のプロファイルではなくなります。  
  
 ストアド プロシージャ**sysmail_update_principalprofile_sp**では、 **msdb**が所有するデータベースにあり、 **dbo**スキーマです。 現在のデータベースがない場合は、3 部構成の名前を持つプロシージャを実行する必要があります**msdb**です。  
  
## <a name="permissions"></a>Permissions  
 メンバーにこのプロシージャの既定の実行権限、 **sysadmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
 **A.データベースの既定のパブリック プロファイルに、プロファイルの設定**  
  
 次の例と、プロファイル設定`General Use Profile`内のユーザーの既定のパブリック プロファイルに、 **msdb**データベース。  
  
```  
EXECUTE msdb.dbo.sysmail_update_principalprofile_sp  
    @principal_name = 'public',  
    @profile_name = 'General Use Profile',  
    @is_default = '1';  
```  
  
 **B.ユーザーの既定のプライベート プロファイルに、プロファイルの設定**  
  
 次の例と、プロファイル設定`AdventureWorks Administrator`プリンシパルの既定のプロファイルに`ApplicationUser`で、 **msdb**データベース。 このプロファイルはプリンシパルに既に関連付けられている必要があります。 それまで既定のプロファイルであったプロファイルは、引き続きプリンシパルに関連付けられますが、既定のプロファイルではなくなります。  
  
```  
EXECUTE msdb.dbo.sysmail_update_principalprofile_sp  
    @principal_name = 'ApplicationUser',  
    @profile_name = 'AdventureWorks Administrator',  
    @is_default = '1' ;  
```  
  
## <a name="see-also"></a>参照  
 [データベース メール](../../relational-databases/database-mail/database-mail.md)   
 [データベース メール構成オブジェクト](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [データベース メールのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
