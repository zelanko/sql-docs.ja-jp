---
title: "ALTER SERVER ROLE (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/06/2016
ms.prod: sql-non-specified
ms.prod_service: pdw, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_SERVER_ROLE_TSQL
- ALTER SERVER ROLE
dev_langs:
- TSQL
helpviewer_keywords:
- SERVER ROLE, ALTER
- ALTER SERVER ROLE statement
ms.assetid: 7a4db7bb-c442-4e12-9a8a-114da5bc7710
caps.latest.revision: 19
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5f88c9aaf3e541d4213a3adeb77a0e457deb7c06
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="alter-server-role-transact-sql"></a>ALTER SERVER ROLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-pdw-md.md)]

サーバー ロールのメンバーシップを変更、またはユーザー定義のサーバー ロールの名前を変更します。 固定サーバー ロールの名前は変更できません。  
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server  
  
ALTER SERVER ROLE server_role_name   
{  
    [ ADD MEMBER server_principal ]  
  | [ DROP MEMBER server_principal ]  
  | [ WITH NAME = new_server_role_name ]  
} [ ; ]  
```  
  
```  
-- Syntax for Parallel Data Warehouse  
  
ALTER SERVER ROLE  server_role_name  ADD MEMBER login;  
  
ALTER SERVER ROLE  server_role_name  DROP MEMBER login;  
```  
  
## <a name="arguments"></a>引数  
*server_role_name*  
変更するサーバー ロールの名前を指定します。  
  
メンバーの追加*server_principal*  
指定されたサーバー プリンシパルをサーバー ロールに追加します。 *server_principal*ログインまたはユーザー定義サーバー ロールを指定できます。 *server_principal*固定サーバー ロール、データベース ロール、または sa にすることはできません。  
  
DROP MEMBER *server_principal*  
指定されたサーバー プリンシパルをサーバー ロールから削除します。 *server_principal*ログインまたはユーザー定義サーバー ロールを指定できます。 *server_principal*固定サーバー ロール、データベース ロール、または sa にすることはできません。  
  
名前を持つ **=**  *new_server_role_name*  
ユーザー定義サーバー ロールの新しい名前を指定します。 サーバー内に存在しない名前を指定してください。  
  
## <a name="remarks"></a>解説  
ユーザー定義サーバー ロールの名前を変更しても、ロールの ID 番号、所有者、権限は変わりません。  
  
ロールのメンバーシップを変更するため`ALTER SERVER ROLE`sp_addsrvrolemember および sp_dropsrvrolemember が置き換えられます。 これらのストアド プロシージャは非推奨です。  
  
サーバーの役割を表示するにはクエリを実行して、`sys.server_role_members`と`sys.server_principals`カタログ ビューです。  
  
ユーザー定義サーバー ロールの所有者を変更するには、使用[ALTER AUTHORIZATION & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-authorization-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
必要があります`ALTER ANY SERVER ROLE`サーバーに対する権限がユーザー定義サーバー ロールの名前を変更します。  
  
**固定サーバー ロール**  
  
固定サーバー ロールにメンバーを追加するには、その固定サーバー ロールのメンバーであるか、`sysadmin` 固定サーバー ロールのメンバーである必要があります。  
  
> [!NOTE]  
>  `CONTROL SERVER`と`ALTER ANY SERVER ROLE`を実行するための十分なアクセス許可されない`ALTER SERVER ROLE`固定サーバー ロールの場合と`ALTER`固定サーバー ロールの権限を許可することはできません。  
  
**ユーザー定義サーバー ロール**  
  
ユーザー定義サーバー ロールにメンバーを追加する、`sysadmin`固定サーバー ロールまたは`CONTROL SERVER`または`ALTER ANY SERVER ROLE`権限です。 必要がありますまたは`ALTER`そのロールに対する権限。  
  
> [!NOTE]  
>  固定サーバー ロールとは異なり、ユーザー定義サーバー ロールのメンバーは、同じロールにメンバーを追加する権限がもともとありません。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-changing-the-name-of-a-server-role"></a>A. サーバー ロールの名前を変更する  
次の例は、という名前のサーバー ロールを作成`Product`、し、サーバー ロールの名前を変更`Production`です。  
  
```  
CREATE SERVER ROLE Product ;  
ALTER SERVER ROLE Product WITH NAME = Production ;  
GO  
```  
  
### <a name="b-adding-a-domain-account-to-a-server-role"></a>B. ドメイン アカウントをサーバー ロールに追加する  
次の例は、という名前のドメイン アカウントを追加`adventure-works\roberto0`という名前のユーザー定義サーバー ロールに`Production`です。  
  
```  
ALTER SERVER ROLE Production ADD MEMBER [adventure-works\roberto0] ;  
```  
  
### <a name="c-adding-a-sql-server-login-to-a-server-role"></a>C. SQL Server ログインをサーバー ロールに追加する  
次の例では追加、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]という名前のログイン`Ted`を`diskadmin`固定サーバー ロール。  
  
```  
ALTER SERVER ROLE diskadmin ADD MEMBER Ted ;  
GO  
```  
  
### <a name="d-removing-a-domain-account-from-a-server-role"></a>D. サーバー ロールからドメイン アカウントを削除する  
次の例では、という名前のドメイン アカウントを削除する`adventure-works\roberto0`という名前のユーザー定義サーバー ロールから`Production`です。  
  
```  
ALTER SERVER ROLE Production DROP MEMBER [adventure-works\roberto0] ;  
```  
  
### <a name="e-removing-a-sql-server-login-from-a-server-role"></a>E. サーバー ロールから SQL Server ログインを削除する  
次の例では、削除、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログイン`Ted`から、`diskadmin`固定サーバー ロール。  
  
```  
ALTER SERVER ROLE Production DROP MEMBER Ted ;  
GO  
```  
  
### <a name="f-granting-a-login-the-permission-to-add-logins-to-a-user-defined-server-role"></a>F. ログインをユーザー定義サーバー ロールに追加する権限をログインに許可する  
次の例では`Ted`という名前のユーザー定義サーバー ロールに他のログインを追加する`Production`です。  
  
```  
GRANT ALTER ON SERVER ROLE::Production TO Ted ;  
GO  
```  
  
### <a name="g-to-view-role-membership"></a>G. ロールのメンバーシップを表示するには  
表示するにはロールのメンバーシップを使用して、**サーバーの役割 (メンバー)**ページ[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]または次のクエリを実行します。  
  
```  
SELECT SRM.role_principal_id, SP.name AS Role_Name,   
SRM.member_principal_id, SP2.name  AS Member_Name  
FROM sys.server_role_members AS SRM  
JOIN sys.server_principals AS SP  
    ON SRM.Role_principal_id = SP.principal_id  
JOIN sys.server_principals AS SP2   
    ON SRM.member_principal_id = SP2.principal_id  
ORDER BY  SP.name,  SP2.name  
```  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="h-basic-syntax"></a>H. 基本構文  
次の例は、ログインを追加`Anna`を`LargeRC`サーバーの役割です。  
  
```  
ALTER SERVER ROLE LargeRC ADD MEMBER Anna;  
```  
  
### <a name="i-remove-a-login-from-a-resource-class"></a>I. リソース クラスからログインを削除します。  
次の例では、Anna のメンバーシップを削除、`LargeRC`サーバーの役割です。  
  
```  
ALTER SERVER ROLE LargeRC DROP MEMBER Anna;  
```  
  
## <a name="see-also"></a>参照  
[SERVER ROLE &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-server-role-transact-sql.md)   
[DROP SERVER ROLE &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-server-role-transact-sql.md)   
[ROLE &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-role-transact-sql.md)   
[ALTER ROLE &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-role-transact-sql.md)   
[DROP ROLE &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-role-transact-sql.md)   
[セキュリティのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
[セキュリティ関数 &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)   
[プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
[sys.server_role_members & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md)   
[sys.server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)  
  

