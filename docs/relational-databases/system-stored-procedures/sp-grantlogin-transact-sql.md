---
title: "sp_grantlogin (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
- sp_grantlogin_TSQL
- sp_grantlogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_grantlogin
ms.assetid: 0c873d99-c3bf-4eb1-948b-a46cb235ccd4
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a28ab1b1611a2beff1bdc3c9707baa25a9cbaa89
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="spgrantlogin-transact-sql"></a>sp_grantlogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  作成、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインします。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]使用して[CREATE LOGIN](../../t-sql/statements/create-login-transact-sql.md)代わりにします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_grantlogin [@loginame=] 'login'  
```  
  
## <a name="arguments"></a>引数  
 [  **@loginame =** ] **'***ログイン***'**  
 Windows ユーザーまたはグループの名前を指定します。 Windows ユーザーまたはグループをフォームでの Windows ドメイン名で修飾する必要があります*ドメイン*\\*ユーザー*。 たとえば、 **london \joeb**です。 *ログイン*は**sysname**、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_grantlogin**追加のオプションをサポートする CREATE LOGIN を呼び出します。 SQL Server ログインを作成する方法については、次を参照してください。 [CREATE LOGIN &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-login-transact-sql.md)  
  
 **sp_grantlogin**ユーザー定義のトランザクション内で実行することはできません。  
  
## <a name="permissions"></a>Permissions  
 サーバーに対する ALTER ANY LOGIN 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例で`CREATE LOGIN`を作成する、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows ユーザーのログイン`Corporate\BobJ.`推奨される方法です。  
  
```  
CREATE LOGIN [Corporate\BobJ] FROM WINDOWS;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
