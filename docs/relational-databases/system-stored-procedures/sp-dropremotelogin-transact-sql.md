---
title: "sp_dropremotelogin (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sp_dropremotelogin
- sp_dropremotelogin_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_dropremotelogin
ms.assetid: 9f097652-a286-40b2-be73-568d77ada698
caps.latest.revision: "30"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cd2ef0424aea68d4d770ddeda9909c9c1a81f4a9
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spdropremotelogin-transact-sql"></a>sp_dropremotelogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行中のローカル サーバーに対してリモート ストアド プロシージャを実行する場合に使用される、ローカル ログインにマップされているリモート ログインを削除します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)]代わりに、リンク サーバーとリンク サーバー ストアド プロシージャを使用します。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_dropremotelogin [ @remoteserver = ] 'remoteserver'   
     [ , [ @loginame = ] 'login' ]   
     [ , [ @remotename = ] 'remote_name' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@remoteserver =** ] **'***remoteserver***'**  
 削除するリモート ログインにマップされているリモート サーバーの名前を指定します。 *remoteserver*は**sysname**、既定値はありません。 *remoteserver*既に存在する必要があります。  
  
 [  **@loginame =** ] **'***ログイン***'**  
 リモート サーバーに関連付けられているローカル サーバー上のログイン名を指定します (省略可能)。 *ログイン*は**sysname**、既定値は NULL です。 *ログイン*指定されている場合に既に存在する必要があります。  
  
 [  **@remotename =** ] **'***remote_name***'**  
 マップされているリモート ログインの名前を省略可能な*ログイン*リモート サーバーからにログインします。 *remote_name*は**sysname**、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 だけの場合*remoteserver*を指定すると、そのリモート サーバーのすべてのリモート ログインは、ローカル サーバーから削除されます。 場合*ログイン*から指定すると、すべてのリモート ログインも*remoteserver*をその特定のマップされたローカル ログインは、ローカル サーバーから削除されます。 場合*remote_name*も指定すると、そのリモート ユーザーからのリモート ログインだけ*remoteserver*がローカル サーバーから削除します。  
  
 ローカル サーバー ユーザーを追加する**sp_addlogin**です。 ローカル サーバー ユーザーを削除する使用**sp_droplogin**です。  
  
 リモート ログインは、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用する場合にのみ必要です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Version 7.0 以降では、代わりにリンク サーバー ログインを使用します。 使用して**sp_addlinkedsrvlogin**と**sp_droplinkedsrvlogin**を追加およびリンク サーバー ログインを削除します。  
  
 **sp_dropremotelogin**ユーザー定義のトランザクション内で実行することはできません。  
  
## <a name="permissions"></a>Permissions  
 メンバーシップが必要、 **sysadmin**または**securityadmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-dropping-all-remote-logins-for-a-remote-server"></a>A. リモート サーバーのすべてのリモート ログインを削除する  
 次の例では、リモート サーバーのエントリを削除する`ACCOUNTS`、および、そのため、すべてのローカル サーバー上のログインとリモート サーバー上のリモート ログインの間のマッピングを削除します。  
  
```  
EXEC sp_dropremotelogin 'ACCOUNTS';  
```  
  
### <a name="b-dropping-a-login-mapping"></a>B. ログインのマッピングを削除する  
 次の例では、リモート サーバー `ACCOUNTS` からのリモート ログインとローカル ログイン `Albert` をマップしているエントリを削除します。  
  
```  
EXEC sp_dropremotelogin 'ACCOUNTS', 'Albert';  
```  
  
### <a name="c-dropping-a-remote-user"></a>C. リモート ユーザーを削除する  
 次の例では、リモート ログインのログインを削除する`Chris`、リモート サーバーで`ACCOUNTS`ローカル ログインにマップされている`salesmgr`です。  
  
```  
EXEC sp_dropremotelogin 'ACCOUNTS', 'salesmgr', 'Chris';  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addlinkedsrvlogin &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)   
 [sp_addlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md)   
 [sp_addremotelogin &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addremotelogin-transact-sql.md)   
 [sp_addserver &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)   
 [sp_droplinkedsrvlogin &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-droplinkedsrvlogin-transact-sql.md)   
 [sp_droplogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droplogin-transact-sql.md)   
 [sp_helpremotelogin &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helpremotelogin-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
