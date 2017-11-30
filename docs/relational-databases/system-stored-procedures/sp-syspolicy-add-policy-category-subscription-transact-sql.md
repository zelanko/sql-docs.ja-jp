---
title: "sp_syspolicy_add_policy_category_subscription (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sp_syspolicy_add_policy_category_subscription
- sp_syspolicy_add_policy_category_subscription_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_syspolicy_add_policy_category_subscription
ms.assetid: 4284f550-9a3f-4726-8181-15e407fbf08f
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ec357296ce840bad84b6a0f1985858684f610a2b
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="spsyspolicyaddpolicycategorysubscription-transact-sql"></a>sp_syspolicy_add_policy_category_subscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ポリシー カテゴリのサブスクリプションを、指定したデータベースに追加します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_syspolicy_add_policy_category_subscription [ @target_type = ] 'target_type'  
    , [ @target_object = ] 'target_object'  
    , [ @policy_category = ] 'policy_category'  
    [ , [ @policy_category_subscription_id = ] policy_category_subscription_id OUTPUT ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@target_type=** ] **'***target_type***'**  
 カテゴリ サブスクリプションの対象の種類を指定します。 *target_type*は**sysname**が必要であり、'DATABASE' に設定する必要があります。  
  
 [  **@target_object=** ] **'***target_object***'**  
 カテゴリをサブスクライブするデータベースの名前です。 *target_object*は**sysname**が必要とします。  
  
 [  **@policy_category=** ] **'***policy_category***'**  
 サブスクライブするポリシー カテゴリの名前です。 *policy_category*は**sysname**が必要とします。  
  
 値を取得する*policy_category*、msdb.dbo.syspolicy_policy_categories システム ビューにクエリします。  
  
 [  **@policy_category_subscription_id=** ] *policy_category_subscription_id*  
 カテゴリ サブスクリプションの識別子を指定します。 *policy_category_subscription_id*は**int**、出力として返されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 sp_syspolicy_add_policy_category_subscription は msdb システム データベースのコンテキストで実行する必要があります。  
  
 存在しないポリシー カテゴリを指定すると、新しいポリシー カテゴリが作成され、ストアド プロシージャの実行時にすべてのデータベースに対してサブスクリプションが要求されます。 新しいカテゴリに要求されたサブスクリプションをクリアすると、そのサブスクリプションは、*target_object* で指定したデータベースにのみ適用されます。 要求されたサブスクリプションの設定を変更する方法の詳細については、「[sp_syspolicy_update_policy_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-update-policy-category-transact-sql.md)」を参照してください。  
  
## <a name="permissions"></a>Permissions  
 このストアド プロシージャは、ストアド プロシージャの現在の所有者のコンテキストで実行されます。  
  
## <a name="examples"></a>使用例  
 次の例では、'Table Naming Policies' という名前のポリシー カテゴリをサブスクライブするように指定したデータベースを構成します。  
  
```  
EXEC msdb.dbo.sp_syspolicy_add_policy_category_subscription @target_type = N'DATABASE'  
, @target_object = N'AdventureWorks2012'  
, @policy_category = N'Table Naming Policies';  
  
GO  
```  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理ストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)   
 [sp_syspolicy_update_policy_category_subscription &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-syspolicy-update-policy-category-subscription-transact-sql.md)   
 [sp_syspolicy_unsubscribe_from_policy_category は &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-syspolicy-unsubscribe-from-policy-category-transact-sql.md)  
  
  
