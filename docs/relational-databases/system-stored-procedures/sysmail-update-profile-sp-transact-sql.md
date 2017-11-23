---
title: "sysmail_update_profile_sp (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sysmail_update_profile_sp
- sysmail_update_profile_sp_TSQL
dev_langs: TSQL
helpviewer_keywords: sysmail_update_profile_sp
ms.assetid: eaedf7ce-a8d5-4ab9-99e0-d77d5be19e90
caps.latest.revision: "29"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c8ac35d2b28b6a85759e322d0248da044452a46c
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysmailupdateprofilesp-transact-sql"></a>sysmail_update_profile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベース メール プロファイルの説明または名前を変更します。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sysmail_update_profile_sp [ [ @profile_id = ] profile_id , ] [ [ @profile_name = ] 'profile_name' , ]  
    [ [ @description = ] 'description' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@profile_id**  =] *profile_id*  
 更新するプロファイル ID を指定します。 *profile_id*は**int**、既定値は NULL です。 少なくとも 1 つの*profile_id*または*profile_name*指定する必要があります。 両方を指定した場合、プロシージャではプロファイルの名前が変更されます。  
  
 [  **@profile_name**  =] **'***profile_name***'**  
 更新するプロファイルの名前、またはプロファイルの新しい名前を指定します。 *profile_name*は**sysname**、既定値は NULL です。 少なくとも 1 つの*profile_id*または*profile_name*指定する必要があります。 両方を指定した場合、プロシージャではプロファイルの名前が変更されます。  
  
 [  **@description**  =] **'***説明***'**  
 プロファイルの新しい説明を指定します。 *説明*は**nvarchar (256)**、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 プロファイル ID とプロファイル名の両方を指定した場合、このプロシージャでは、プロファイルの名前が指定の名前に変更され、プロファイルの説明が更新されます。 一方の引数だけを指定した場合は、プロファイルの説明が更新されます。  
  
 ストアド プロシージャ**sysmail_update_profile_sp**では、 **msdb**が所有するデータベースにあり、 **dbo**スキーマです。 現在のデータベースがない場合は、3 部構成の名前を持つプロシージャを実行する必要があります**msdb**です。  
  
## <a name="permissions"></a>Permissions  
 メンバーにこのプロシージャの既定の実行権限、 **sysadmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
 **A.プロファイルの説明を変更します。**  
  
 次の例は、という名前のプロファイルの説明を変更`AdventureWorks Administrator`で、 **msdb**データベース。  
  
```  
EXECUTE msdb.dbo.sysmail_update_profile_sp  
    @profile_name = 'AdventureWorks Administrator'  
    ,@description = 'Administrative mail profile.';  
```  
  
 **B.プロファイルの説明と名前を変更します。**  
  
 次の例は、プロファイル id を持つプロファイルの説明と名前を変更`750`です。  
  
```  
EXECUTE msdb.dbo.sysmail_update_profile_sp  
    @profile_id = 750  
    ,@profile_name = 'Operator'  
    ,@description = 'Profile to send alert e-mail to operators.';  
```  
  
## <a name="see-also"></a>参照  
 [データベース メール](../../relational-databases/database-mail/database-mail.md)   
 [データベース メール構成オブジェクト](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [データベース メール アカウントを作成します。](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [データベース メールのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
