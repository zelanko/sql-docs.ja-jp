---
title: "sp_syspolicy_set_log_on_success (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/09/2016
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
- sp_syspolicy_set_log_on_success_TSQL
- sp_syspolicy_set_log_on_success
dev_langs: TSQL
helpviewer_keywords: sp_syspolicy_set_log_on_success
ms.assetid: 6b33383b-5949-488a-a911-59299a270f46
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 95d79dfcd1e4942cb5604df98b8edc49eb4dc2da
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="spsyspolicysetlogonsuccess-transact-sql"></a>sp_syspolicy_set_log_on_success (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  成功したポリシー評価を、ポリシー ベースの管理のポリシー履歴ログに記録するかどうかを指定します。  
  
 
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_syspolicy_set_log_on_success [ @value = ] value  
```  
  
## <a name="arguments"></a>引数  
 [  **@value=** ]*値*  
 成功したポリシー評価をログに記録するかどうかを示します。 *値*は**sqlvariant**値は次のいずれかを指定できます。  
  
-   0 または 'false' = 成功したポリシー評価はログに記録されません。  
  
-   1 または 'true' = 成功したポリシー評価がログに記録されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 msdb システム データベースのコンテキストで sp_syspolicy_set_log_on_success を実行する必要があります。  
  
 ときに*値*は 0 または 'false' が失敗したのみポリシーの評価がログに記録されます。  
  
## <a name="permissions"></a>Permissions  
 PolicyAdministratorRole 固定データベース ロールのメンバーシップが必要です。  
  
> **重要!!** 資格情報が昇格される可能性について: PolicyAdministratorRole ロールに割り当てられているユーザーは、サーバー トリガーを作成して、[!INCLUDE[ssDE](../../includes/ssde-md.md)] インスタンスの動作に影響する可能性があるポリシーの実行をスケジュールできます。 たとえば、PolicyAdministratorRole ロールに割り当てられているユーザーは、ほとんどのオブジェクトが[!INCLUDE[ssDE](../../includes/ssde-md.md)]で作成されないようにすることができるポリシーを作成できます。 構成を制御について信頼できるユーザーにのみこの昇格される可能性の資格情報、ため PolicyAdministratorRole ロールを許可してください、[!INCLUDE[ssDE](../../includes/ssde-md.md)]です。  
  
## <a name="examples"></a>使用例  
 次の例では、成功したポリシー評価のログ記録を有効にします。  
  
```  
EXEC msdb.dbo.sp_syspolicy_set_log_on_success @value = 1;  
  
GO  
```  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理ストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)   
 [sp_syspolicy_configure &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-syspolicy-configure-transact-sql.md)  
  
  
