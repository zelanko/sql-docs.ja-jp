---
title: sp_approlepassword (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_approlepassword
- sp_approlepassword_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_approlepassword
ms.assetid: 7967dc0b-bee2-4c63-b8e9-1c3ce2f5db2a
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 51ccbeb8487739d69e31c39d7bad9a0d8d11233d
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38049599"
---
# <a name="spapprolepassword-transact-sql"></a>sp_approlepassword (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のデータベース内にあるアプリケーション ロールのパスワードを変更します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 使用[ALTER APPLICATION ROLE](../../t-sql/statements/alter-application-role-transact-sql.md)代わりにします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_approlepassword [ @rolename= ] 'role' , [ @newpwd = ] 'password'   
```  
  
## <a name="arguments"></a>引数  
 [  **@rolename =** ] **'***ロール***'**  
 アプリケーション ロールの名前を指定します。 *ロール*は**sysname**、既定値はありません。 *ロール*現在のデータベースに存在する必要があります。  
  
 [  **@newpwd =** ] **'***パスワード***'**  
 アプリケーション ロールの新しいパスワードを指定します。 *パスワード*は**sysname**、既定値はありません。 *パスワード*NULL にすることはできません。  
  
> [!IMPORTANT]  
>  パスワードは NULL にせず、 強力なパスワードを使用してください。 詳細については、「 [Strong Passwords](../../relational-databases/security/strong-passwords.md)」を参照してください。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_approlepassword**ユーザー定義のトランザクション内で実行することはできません。  
  
## <a name="permissions"></a>アクセス許可  
 データベースに対する ALTER ANY APPLICATION ROLE 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例のパスワードの設定、`PayrollAppRole`するアプリケーション ロール`B3r12-36`します。  
  
```  
EXEC sp_approlepassword 'PayrollAppRole', '''B3r12-36';  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティ ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [アプリケーション ロール](../../relational-databases/security/authentication-access/application-roles.md)   
 [sp_addapprole &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addapprole-transact-sql.md)   
 [sp_setapprole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-setapprole-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
