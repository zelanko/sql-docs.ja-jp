---
title: "sp_password (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sp_password
- sp_password_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_password
ms.assetid: 0ecbec81-e637-44a9-a61e-11bf060ef084
caps.latest.revision: "28"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: be3ecac772f6ce7f3138d8330d85fe54f4aca5b8
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sppassword-transact-sql"></a>sp_password (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  追加または変更するためのパスワード、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインします。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]使用して[ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md)代わりにします。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|  
  
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
 パスワード変更の対象となるログインの名前を指定します。 *ログイン*は**sysname**、既定値は NULL です。 *ログイン*は既に存在してのメンバーでのみ指定することができます、 **sysadmin**または**securityadmin**固定サーバー ロール。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_password** ALTER LOGIN を呼び出します。 このステートメントでは追加オプションがサポートされます。 パスワードを変更する方法については、次を参照してください。 [ALTER LOGIN &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-login-transact-sql.md).  
  
 **sp_password**ユーザー定義のトランザクション内で実行することはできません。  
  
## <a name="permissions"></a>Permissions  
 ALTER ANY LOGIN 権限が必要です。 古いパスワードを指定しないでパスワードをリセットする場合、または変更されるログインに CONTROL SERVER 権限がある場合は、CONTROL SERVER 権限も必要です。  
  
 プリンシパルは自分のパスワードを変更できます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-changing-the-password-of-a-login-without-knowing-the-old-password"></a>A. 古いパスワードがわからない場合にログインのパスワードを変更する  
 次の例では、`ALTER LOGIN` を使って、`Victoria` ログイン用のパスワードを `B3r1000d#2-36` に変更します。 これは推奨される方法です。 このコマンドを実行するユーザーには、CONTROL SERVER 権限が必要です。  
  
```  
ALTER LOGIN Victoria WITH PASSWORD = 'B3r1000d#2-36';  
GO  
```  
  
### <a name="b-changing-a-password"></a>B. パスワードを変更します。  
 次の例は、使用する方法を示しています。`ALTER LOGIN`ログインのパスワードを変更する`Victoria`から`B3r1000d#2-36`に`V1cteAmanti55imE`です。 これは推奨される方法です。 ユーザー `Victoria` は、追加の権限を取得しなくてもこのコマンドを実行できます。 他のユーザーには ALTER ANY LOGIN 権限が必要です。  
  
```  
ALTER LOGIN Victoria WITH   
     PASSWORD = 'V1cteAmanti55imE'   
     OLD_PASSWORD = 'B3r1000d#2-36';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [ALTER LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md)   
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [sp_addlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md)   
 [sp_adduser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adduser-transact-sql.md)   
 [sp_grantlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [sp_revokelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
