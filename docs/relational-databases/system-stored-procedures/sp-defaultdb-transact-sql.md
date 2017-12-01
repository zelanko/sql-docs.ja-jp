---
title: "sp_defaultdb (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sp_defaultdb_TSQL
- sp_defaultdb
dev_langs: TSQL
helpviewer_keywords: sp_defaultdb
ms.assetid: 663b859f-c6da-4942-95a6-60b93d05654e
caps.latest.revision: "29"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c44a3f1f26861e3e78e936aeb642e33ead4a4786
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="spdefaultdb-transact-sql"></a>sp_defaultdb (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  既定のデータベースを変更、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインします。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]使用して[ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md)代わりにします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_defaultdb [ @loginame = ] 'login', [ @defdb = ] 'database'   
```  
  
## <a name="arguments"></a>引数  
 [  **@loginame=**] **'***ログイン***'**  
 ログイン名です。 *ログイン*は**sysname**、既定値はありません。 *ログイン*既存できる[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインまたは Windows ユーザーまたはグループ。 Windows ユーザーまたはグループのログインが存在しない場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、自動的に追加します。  
  
 [  **@defdb=**] **'***データベース***'**  
 新しい既定のデータベースの名前です。 *データベース*は**sysname**、既定値はありません。 *データベース*既に存在する必要があります。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_defaultdb** ALTER LOGIN を呼び出します。 このステートメントでは追加オプションがサポートされます。 既定のデータベースを変更する方法の詳細については、次を参照してください。 [ALTER LOGIN &#40;です。TRANSACT-SQL と #41 です;](../../t-sql/statements/alter-login-transact-sql.md)。  
  
 **sp_defaultdb**ユーザー定義のトランザクション内で実行することはできません。  
  
## <a name="permissions"></a>Permissions  
 ALTER ANY LOGIN 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] ログイン `Victoria` の既定のデータベースとして [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を設定します。  
  
```  
EXEC sp_defaultdb 'Victoria', 'AdventureWorks2012';  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [ALTER LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md)   
 [sp_addlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md)   
 [sp_droplogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droplogin-transact-sql.md)   
 [sp_grantdbaccess &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
