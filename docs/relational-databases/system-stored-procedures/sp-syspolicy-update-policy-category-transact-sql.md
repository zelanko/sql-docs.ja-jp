---
title: "sp_syspolicy_update_policy_category (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sp_syspolicy_update_policy_category_TSQL
- sp_syspolicy_update_policy_category
dev_langs: TSQL
helpviewer_keywords: sp_syspolicy_update_policy_category
ms.assetid: 6b6413c2-7a3b-4eff-91d9-5db2011869d6
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c3146a592bc55ee121de11f3a1c24102fcc10022
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="spsyspolicyupdatepolicycategory-transact-sql"></a>sp_syspolicy_update_policy_category (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ポリシー カテゴリをデータベースのサブスクリプションの要求に設定するかどうかを更新します。 サブスクリプションが必須の場合、ポリシー カテゴリはすべてのデータベースに適用されます。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_syspolicy_update_policy_category { [ @name = ] 'name' | [ @policy_category_id = ] policy_category_id }  
    , [ @mandate_database_subscriptions = ] mandate_database_subscriptions ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@name=** ] **'***名前***'**  
 ポリシー カテゴリの名前を指定します。 *名前*は**sysname**場合に、指定する必要があります*policy_category_id*は NULL です。  
  
 [  **@policy_category_id=** ] *policy_category_id*  
 ポリシー カテゴリの識別子を指定します。 *policy_category_id*は**int**場合に、指定する必要があります*名前*は NULL です。  
  
 [  **@mandate_database_subscriptions=** ] *mandate_database_subscriptions*  
 データベース サブスクリプションがポリシー カテゴリに対して必須であるかどうかを指定します。 *mandate_database_subscriptions*は、**ビット**値、既定値は NULL です。 次の値のいずれかの操作を行うこともできます。  
  
-   0 = 必須ではない  
  
-   1 = 必須  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 sp_syspolicy_update_policy_category は msdb システム データベースのコンテキストで実行する必要があります。  
  
 いずれかの値を指定する必要があります*名前*または*policy_category_id*です。 両方を NULL にすることはできません。 これらの値を取得するには、msdb.dbo.syspolicy_policy_categories システム ビューに対してクエリを実行します。  
  
## <a name="permissions"></a>Permissions  
 PolicyAdministratorRole 固定データベース ロールのメンバーシップが必要です。  
  
> [!IMPORTANT]  
>  資格情報が昇格される可能性について: PolicyAdministratorRole ロールに割り当てられているユーザーは、サーバー トリガーを作成して、[!INCLUDE[ssDE](../../includes/ssde-md.md)] インスタンスの動作に影響する可能性があるポリシーの実行をスケジュールできます。 たとえば、PolicyAdministratorRole ロールに割り当てられているユーザーは、ほとんどのオブジェクトが[!INCLUDE[ssDE](../../includes/ssde-md.md)]で作成されないようにすることができるポリシーを作成できます。 構成を制御について信頼できるユーザーにのみこの昇格される可能性の資格情報、ため PolicyAdministratorRole ロールを許可してください、[!INCLUDE[ssDE](../../includes/ssde-md.md)]です。  
  
## <a name="examples"></a>使用例  
 次の例では、'Finance' カテゴリ更新して、データベースのサブスクリプションが要求されるようにします。  
  
```  
EXEC msdb.dbo.sp_syspolicy_update_policy_category @name = N'Finance'  
, @mandate_database_subscriptions = 1;  
  
GO  
```  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理ストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)   
 [sp_syspolicy_add_policy_category &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-syspolicy-add-policy-category-transact-sql.md)   
 [sp_syspolicy_delete_policy_category &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-syspolicy-delete-policy-category-transact-sql.md)   
 [sp_syspolicy_rename_policy_category &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-syspolicy-rename-policy-category-transact-sql.md)  
  
  
