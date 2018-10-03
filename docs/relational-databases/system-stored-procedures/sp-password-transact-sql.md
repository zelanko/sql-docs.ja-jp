---
title: sp_password (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_password
- sp_password_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_password
ms.assetid: 0ecbec81-e637-44a9-a61e-11bf060ef084
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 0bef77291c0a719b9cdc96106d3c173dff652da1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47644680"
---
# <a name="sppassword-transact-sql"></a>sp_password (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  追加または変更するためのパスワードを[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインします。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 使用[ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md)代わりにします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_password [ [ @old = ] 'old_password' , ]  
     { [ @new =] 'new_password' }  
     [ , [ @loginame = ] 'login' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@old=** ] **'***old_password***'**  
 古いパスワードを指定します。 *old_password*は**sysname**、既定値は NULL です。  
  
 [  **@new=** ] **'***新しい _ パスワード***'**  
 新しいパスワードです。 *新しい _ パスワード*は**sysname**、既定値はありません。 *old_password*名前付きパラメーターを使用しないかどうかは指定する必要があります。  
  
> [!IMPORTANT]  
>  パスワードは NULL にせず、 強力なパスワードを使用してください。 詳細については、「 [Strong Passwords](../../relational-databases/security/strong-passwords.md)」を参照してください。  
  
 [  **@loginame=** ] **'***ログイン***'**  
 パスワード変更の対象となるログインの名前を指定します。 *login* のデータ型は **sysname** で、既定値は NULL です。 *ログイン*が既に存在しのメンバーでのみ指定できます、 **sysadmin**または**securityadmin**固定サーバー ロール。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_password**は ALTER LOGIN を呼び出します。 このステートメントでは追加オプションがサポートされます。 パスワードを変更する方法の詳細については、次を参照してください。 [ALTER LOGIN &#40;TRANSACT-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md)します。  
  
 **sp_password**ユーザー定義のトランザクション内で実行することはできません。  
  
## <a name="permissions"></a>アクセス許可  
 ALTER ANY LOGIN 権限が必要です。 古いパスワードを指定しないでパスワードをリセットする場合、または変更されるログインに CONTROL SERVER 権限がある場合は、CONTROL SERVER 権限も必要です。  
  
 プリンシパルは自分のパスワードを変更できます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-changing-the-password-of-a-login-without-knowing-the-old-password"></a>A. 古いパスワードがわからない場合にログインのパスワードを変更する  
 次の例では、`ALTER LOGIN` を使って、`Victoria` ログイン用のパスワードを `B3r1000d#2-36` に変更します。 これは推奨される方法です。 このコマンドを実行するユーザーには、CONTROL SERVER 権限が必要です。  
  
```  
ALTER LOGIN Victoria WITH PASSWORD = 'B3r1000d#2-36';  
GO  
```  
  
### <a name="b-changing-a-password"></a>B. パスワードの変更  
 次の例は、使用する方法を示します`ALTER LOGIN`ログインのパスワードを変更する`Victoria`から`B3r1000d#2-36`に`V1cteAmanti55imE`します。 これは推奨される方法です。 ユーザー `Victoria` は、追加の権限を取得しなくてもこのコマンドを実行できます。 他のユーザーには ALTER ANY LOGIN 権限が必要です。  
  
```  
ALTER LOGIN Victoria WITH   
     PASSWORD = 'V1cteAmanti55imE'   
     OLD_PASSWORD = 'B3r1000d#2-36';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティ ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [ALTER LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md)   
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [sp_addlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md)   
 [sp_adduser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adduser-transact-sql.md)   
 [sp_grantlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [sp_revokelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
