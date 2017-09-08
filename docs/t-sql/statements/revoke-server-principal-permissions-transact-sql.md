---
title: "サーバー プリンシパルの権限を REVOKE (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- REVOKE statement, impersonation
- permissions [SQL Server], impersonation
- permissions [SQL Server], logins
- impersonate [SQL Server], revoking
- logins [SQL Server], revoking
- REVOKE statement, logins
ms.assetid: 75409024-f150-4326-af16-9d60e900df18
caps.latest.revision: 30
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 13dca8052ad8bc74491136c941677606ccecbe3c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="revoke-server-principal-permissions-transact-sql"></a>REVOKE (サーバー プリンシパルの権限の取り消し) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインに対して許可または拒否された権限を取り消します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
REVOKE [ GRANT OPTION FOR ] permission [ ,...n ] }   
    ON   
    { [ LOGIN :: SQL_Server_login ]  
      | [ SERVER ROLE :: server_role ] }   
    { FROM | TO } <server_principal> [ ,...n ]  
    [ CASCADE ]  
    [ AS SQL_Server_login ]   
  
<server_principal> ::=   
    SQL_Server_login  
    | SQL_Server_login_from_Windows_login   
    | SQL_Server_login_from_certificate   
    | SQL_Server_login_from_AsymKey     
    | server_role  
```  
  
## <a name="arguments"></a>引数  
 *アクセス許可*  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインで取り消せる権限を指定します。 権限の一覧については、後の「解説」を参照してください。  
  
 ログイン**::** *SQL_Server_login*  
 指定します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]いる、権限を取り消すログインします。 スコープ修飾子 (**::**) が必要です。  
  
 サーバーの役割**::** *server_role*  
 権限を取り消すサーバー ロールを指定します。 スコープ修飾子 (**::**) が必要です。  
  
 {から |} \<Server_principal > を指定します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインまたはサーバー ロールのアクセス許可の失効しています。  
  
 *SQL_Server_login*  
 名前を指定、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインします。  
  
 *SQL_Server_login_from_Windows_login*  
 名前を指定、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows ログインから作成されたログインします。  
  
 *SQL_Server_login_from_certificate*  
 名前を指定、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]証明書にマップされるログインです。  
  
 *SQL_Server_login_from_AsymKey*  
 名前を指定、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]非対称キーにマップされるログインです。  
  
 *server_role*  
 ユーザー定義サーバー ロールの名前を指定します。  
  
 GRANT OPTION  
 指定した権限を他のプリンシパルに許可するための権利が、取り消されます。 その権限自体は失効しません。  
  
> [!IMPORTANT]  
>  指定した権限が GRANT オプションなしでプリンシパルに許可されている場合は、その権限自体が取り消されます。  
  
 CASCADE  
 このプリンシパルによって権限が許可または拒否されている他のプリンシパルからも、同じ権限が取り消されることを示します。  
  
> [!CAUTION]  
>  WITH GRANT OPTION で許可されている権限を CASCADE で取り消すと、その権限の GRANT および DENY の両方が取り消されます。  
  
 AS *SQL_Server_login*  
 指定します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]このクエリを実行するプリンシパルの権限を取り消す権利の派生元となるログインします。  
  
## <a name="remarks"></a>解説  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインとサーバーの役割は、サーバー レベルのセキュリティ保護可能なです。 次の表に、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインまたはサーバー ロールで取り消すことができる権限のうち最も限定的なものを、それらを暗黙的に含む一般的な権限と共に示します。  
  
|SQL Server ログインまたはサーバー ロールの権限|権限が含まれる SQL Server ログインまたはサーバー ロールの権限|権限が含まれるサーバー権限|  
|------------------------------------------------|-----------------------------------------------------------|----------------------------------|  
|CONTROL|CONTROL|CONTROL SERVER|  
|IMPERSONATE|CONTROL|CONTROL SERVER|  
|VIEW DEFINITION|CONTROL|VIEW ANY DEFINITION|  
|ALTER|CONTROL|ALTER ANY LOGIN<br /><br /> ALTER ANY SERVER ROLE|  
  
## <a name="permissions"></a>Permissions  
 ログインの場合、ログインに対する CONTROL 権限、またはサーバーに対する ALTER ANY LOGIN 権限が必要です。  
  
 サーバー ロールの場合、サーバー ロールに対する CONTROL 権限、またはサーバーに対する ALTER ANY SERVER ROLE 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-revoking-impersonate-permission-on-a-login"></a>A. ログインの IMPERSONATE 権限を取り消す  
 次の例では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログイン `IMPERSONATE` の `WanidaBenshoof` 権限を、Windows ユーザー `AdvWorks\YoonM` を基に作成された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインから取り消します。  
  
```  
USE master;  
REVOKE IMPERSONATE ON LOGIN::WanidaBenshoof FROM [AdvWorks\YoonM];  
GO  
```  
  
### <a name="b-revoking-view-definition-permission-with-cascade"></a>B. CASCADE を指定して VIEW DEFINITION 権限を取り消す  
 次の例では失効`VIEW DEFINITION`に対する権限、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログイン`EricKurjan`から、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログイン`RMeyyappan`です。 ここでは `CASCADE` オプションを使用して、`VIEW DEFINITION` がこの権限を許可したプリンシパルに対しても、`EricKurjan` の `RMeyyappan` 権限を取り消すことを指定します。  
  
```  
USE master;  
REVOKE VIEW DEFINITION ON LOGIN::EricKurjan FROM RMeyyappan   
    CASCADE;  
GO   
```  
  
### <a name="c-revoking-view-definition-permission-on-a-server-role"></a>C. サーバー ロールの VIEW DEFINITION 権限を取り消す  
 次の例では、`VIEW DEFINITION` サーバー ロールに対する `Sales` サーバー ロールの `Auditors` を取り消します。  
  
```  
USE master;  
REVOKE VIEW DEFINITION ON SERVER ROLE::Sales TO Auditors ;  
GO   
```  
  
## <a name="see-also"></a>参照  
 [sys.server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [sys.server_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md)   
 [GRANT (サーバー プリンシパルの権限の許可) &#40;Transact-SQL&#41;](../../t-sql/statements/grant-server-principal-permissions-transact-sql.md)   
 [DENY (サーバー プリンシパルの権限の拒否) &#40;Transact-SQL&#41;](../../t-sql/statements/deny-server-principal-permissions-transact-sql.md)   
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [アクセス許可 &#40;データベース エンジン&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [セキュリティ関数 &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)   
 [セキュリティ ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)  
  
  


