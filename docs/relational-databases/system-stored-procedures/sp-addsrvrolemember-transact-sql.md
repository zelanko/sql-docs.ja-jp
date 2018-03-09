---
title: "sp_addsrvrolemember (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/20/2017
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
- sp_addsrvrolemember
- sp_addsrvrolemember_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addsrvrolemember
ms.assetid: 777f0e09-8ee5-4cb2-a3ac-939d02c3cd22
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c8159218d405cbd09861938393fd054ab8aea6e9
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="spaddsrvrolemember-transact-sql"></a>sp_addsrvrolemember (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ログインを固定サーバー ロールのメンバーとして追加します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]使用して[ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md)代わりにします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_addsrvrolemember [ @loginame= ] 'login'   
    , [ @rolename = ] 'role'  
```  
  
## <a name="arguments"></a>引数  
 [ @loginame  **=**  ] **'***ログイン***'**  
 固定サーバー ロールに追加するログインの名前を指定します。 *ログイン*は**sysname**、既定値はありません。 *ログイン*できます、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインまたは Windows ログインします。 Windows ログインに対して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] へのアクセスが許可されていない場合は、アクセスが自動的に許可されます。  
  
 [ @rolename  **=**  ] **'***ロール***'**  
 ログインを追加する固定サーバー ロールの名前を指定します。 *ロール*は**sysname**NULL の場合、既定値は次の値のいずれかを指定する必要があります。  
  
-   sysadmin  
  
-   securityadmin  
  
-   serveradmin  
  
-   setupadmin  
  
-   processadmin  
  
-   diskadmin  
  
-   dbcreator  
  
-   bulkadmin  

## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 ログインを固定サーバー ロールに追加すると、そのロールに関係付けられている権限がログインに与えられます。  
  
 Sa ログインのあること、およびパブリックのロールのメンバーシップを変更することはできません。  
  
 Sp_addrolemember を使用して、メンバー、固定データベース ロールまたはユーザー定義ロールを追加します。  
  
 ログインは、ユーザー定義のトランザクション内で実行できません。  
  
## <a name="permissions"></a>Permissions  
 新しいメンバーを追加するロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例は、Windows ログインを追加`Corporate\HelenS`を`sysadmin`固定サーバー ロール。  
  
```  
EXEC sp_addsrvrolemember 'Corporate\HelenS', 'sysadmin';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sp_dropsrvrolemember &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-dropsrvrolemember-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [セキュリティ関数 &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)   
 [SERVER ROLE &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-server-role-transact-sql.md)   
 [DROP SERVER ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-server-role-transact-sql.md)  
  
  
