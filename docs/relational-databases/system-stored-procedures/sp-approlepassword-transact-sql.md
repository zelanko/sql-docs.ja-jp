---
title: sp_approlepassword (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_approlepassword
- sp_approlepassword_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_approlepassword
ms.assetid: 7967dc0b-bee2-4c63-b8e9-1c3ce2f5db2a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 201daf29a40d0d7c7a4f49539c75fdc07bad1e31
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68117759"
---
# <a name="sp_approlepassword-transact-sql"></a>sp_approlepassword (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のデータベースのアプリケーションロールのパスワードを変更します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]代わりに[ALTER APPLICATION ROLE](../../t-sql/statements/alter-application-role-transact-sql.md)を使用してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_approlepassword [ @rolename= ] 'role' , [ @newpwd = ] 'password'   
```  
  
## <a name="arguments"></a>引数  
`[ @rolename = ] 'role'`アプリケーションロールの名前を指定します。 *Role*の型は**sysname**で、既定値はありません。 *ロール*は現在のデータベースに存在している必要があります。  
  
`[ @newpwd = ] 'password'`アプリケーションロールの新しいパスワードを入力します。 *パスワード*は**sysname**,、既定値はありません。 *パスワード*を NULL にすることはできません。  
  
> [!IMPORTANT]  
>  NULL パスワードは使用しないでください。 強力なパスワードを使用してください。 詳細については、「 [強力なパスワード](../../relational-databases/security/strong-passwords.md)」を参照してください。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_approlepassword**は、ユーザー定義のトランザクション内では実行できません。  
  
## <a name="permissions"></a>アクセス許可  
 データベースに対する ALTER ANY APPLICATION ROLE 権限が必要です。  
  
## <a name="examples"></a>例  
 次の例では、 `PayrollAppRole`アプリケーションロールのパスワードを`B3r12-36`に設定します。  
  
```  
EXEC sp_approlepassword 'PayrollAppRole', '''B3r12-36';  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [アプリケーションロール](../../relational-databases/security/authentication-access/application-roles.md)   
 [sp_addapprole &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addapprole-transact-sql.md)   
 [sp_setapprole &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-setapprole-transact-sql.md)   
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
