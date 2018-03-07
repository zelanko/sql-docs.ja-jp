---
title: "サーバー プリンシパル アクセス許可の付与 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- impersonate [SQL Server], granting
- granting permissions [SQL Server], logins
- permissions [SQL Server], impersonate
- permissions [SQL Server], logins
- GRANT statement, impersonation
- GRANT statement, logins
- logins [SQL Server], granting access
- granting permissions [SQL Server], impersonation
ms.assetid: 4cbed281-5e1e-4d8b-b410-4c18a6cd0205
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 9dfd348b6e19f289e41217df4b35dd4cf6e90712
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="grant-server-principal-permissions-transact-sql"></a>GRANT (サーバー プリンシパルの権限の許可) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  に対する権限を許可、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
GRANT permission [ ,...n ] }   
    ON   
    { [ LOGIN :: SQL_Server_login ]  
      | [ SERVER ROLE :: server_role ] }   
    TO <server_principal> [ ,...n ]  
    [ WITH GRANT OPTION ]  
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
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインで許可できる権限を指定します。 権限の一覧については、後の「解説」を参照してください。  
  
 ログイン**::** *SQL_Server_login*  
 指定します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログイン権限が許可されています。 スコープ修飾子 (**::**) が必要です。  
  
 サーバーの役割**::** *server_role*  
 権限を許可するユーザー定義のサーバー ロールを指定します。 スコープ修飾子 (**::**) が必要です。  
  
 \<Server_principal > を指定します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインまたはサーバー ロールの権限が許可されています。  
  
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
  
 WITH GRANT OPTION  
 権限が許可されたプリンシパルが、この権限を他のプリンシパルにも許可できることを示します。  
  
 AS *SQL_Server_login*  
 指定します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]このクエリを実行するプリンシパルが権限を許可する権利の派生元となるログインします。  
  
## <a name="remarks"></a>解説  
 サーバー スコープの権限を許可できるのは、現在のデータベースが master のときだけです。  
  
 サーバー権限に関する情報は、 [sys.server_permissions](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md)カタログ ビューです。 サーバー プリンシパルに関する情報は、 [sys.server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)カタログ ビューです。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインとサーバーの役割は、サーバー レベルのセキュリティ保護可能なです。 次の表に、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインまたはサーバー ロールで許可できる権限のうち最も限定的なものを、それらを暗黙的に含む一般的な権限と共に示します。  
  
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
  
### <a name="a-granting-impersonate-permission-on-a-login"></a>A. ログインの IMPERSONATE 権限を許可する  
 次の例では付与`IMPERSONATE`に対する権限、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログイン`WanidaBenshoof`を[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログイン、Windows のユーザーから作成された`AdvWorks\YoonM`です。  
  
```  
USE master;  
GRANT IMPERSONATE ON LOGIN::WanidaBenshoof to [AdvWorks\YoonM];  
GO  
```  
  
### <a name="b-granting-view-definition-permission-with-grant-option"></a>B. GRANT OPTION を指定して VIEW DEFINITION 権限を許可する  
 次の例`VIEW DEFINITION`上、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログイン`EricKurjan`を[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログイン`RMeyyappan`で`GRANT OPTION`です。  
  
```  
USE master;  
GRANT VIEW DEFINITION ON LOGIN::EricKurjan TO RMeyyappan   
    WITH GRANT OPTION;  
GO   
```  
  
### <a name="c-granting-view-definition-permission-on-a-server-role"></a>C. サーバー ロールの VIEW DEFINITION 権限を許可する  
 次の例では付与`VIEW DEFINITION`上、`Sales`サーバーの役割を`Auditors`サーバーの役割です。  
  
```  
USE master;  
GRANT VIEW DEFINITION ON SERVER ROLE::Sales TO Auditors ;  
GO   
```  
  
## <a name="see-also"></a>参照  
 [sys.server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [sys.server_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md)   
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [アクセス許可 &#40;データベース エンジン&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [セキュリティ関数 &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)   
 [セキュリティ ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)  
  
  

