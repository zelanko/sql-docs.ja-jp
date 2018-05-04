---
title: sp_grant_login_to_proxy (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_grant_login_to_proxy
- sp_grant_login_to_proxy_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_grant_login_to_proxy
ms.assetid: 90e1a6d5-a692-4462-a163-4b0709d83150
caps.latest.revision: 32
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 913c86bce2b9e003c3e5c9f701ba5824611459d8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spgrantlogintoproxy-transact-sql"></a>sp_grant_login_to_proxy (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  プロキシに対するアクセス権をセキュリティ プリンシパルに与えます。  

  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_grant_login_to_proxy   
     { [ @login_name = ] 'login_name'   
     | [ @fixed_server_role = ] 'fixed_server_role'   
     | [ @msdb_role = ] 'msdb_role' } ,   
     { [ @proxy_id = ] id | [ @proxy_name = ] 'proxy_name' }  
```  
  
## <a name="arguments"></a>引数  
 [ **@login_name** =] **'***login_name***'**  
 アクセス権を与えるログイン名を指定します。 *Login_name*は**nvarchar (256)**、既定値は NULL です。 いずれかの**@login_name**、 **@fixed_server_role**、または**@msdb_role**指定する必要がストアド プロシージャは失敗します。  
  
 [ **@fixed_server_role**=] **'***fixed_server_role***'**  
 アクセス権を与える固定サーバー ロールを指定します。 *Fixed_server_role*は**nvarchar (256)**、既定値は NULL です。 いずれかの**@login_name**、 **@fixed_server_role**、または**@msdb_role**指定する必要がストアド プロシージャは失敗します。  
  
 [ **@msdb_role**=] '*msdb_role*'  
 データベース ロール、 **msdb**へのアクセスを許可するデータベース。 *Msdb_role*は**nvarchar (256)**、既定値は NULL です。 いずれかの**@login_name**、 **@fixed_server_role**、または**@msdb_role**指定する必要がストアド プロシージャは失敗します。  
  
 [ **@proxy_id**=] *id*  
 アクセス権の対象となるプロキシの識別子を指定します。 *Id*は**int**、既定値は NULL です。 いずれかの**@proxy_id**または**@proxy_name**を指定してください、ストアド プロシージャは失敗します。  
  
 [ **@proxy_name**= ] **'***proxy_name***'**  
 アクセス権の対象となるプロキシの名前を指定します。 *Proxy_name*は**nvarchar (256)**、既定値は NULL です。 いずれかの**@proxy_id**または**@proxy_name**を指定してください、ストアド プロシージャは失敗します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_grant_login_to_proxy**から実行する必要があります、 **msdb**データベース。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールを実行**sp_grant_login_to_proxy**です。  
  
## <a name="examples"></a>使用例  
 次の例では、ログイン `adventure-works\terrid` に対してプロキシ `Catalog application proxy` の使用を許可します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_grant_login_to_proxy  
    @login_name = N'adventure-works\terrid',  
    @proxy_name = N'Catalog application proxy' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [sp_add_proxy &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md)   
 [sp_revoke_login_from_proxy &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revoke-login-from-proxy-transact-sql.md)  
  
  
