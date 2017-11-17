---
title: "GRANT Endpoint アクセス許可 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/17/2017
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
- endpoints [SQL Server], permissions
- granting permissions [SQL Server], endpoints
- GRANT statement, endpoints
- permissions [SQL Server], endpoints
ms.assetid: 9eda885c-fc3a-4c9d-8de6-ce07fb35a934
caps.latest.revision: 16
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6f89febc7d63bcf36c947aacd90337e7f9478c96
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="grant-endpoint-permissions-transact-sql"></a>GRANT (エンドポイントの権限の許可) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  エンドポイントに対する権限を許可します。  

  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
GRANT permission  [ ,...n ] ON ENDPOINT :: endpoint_name  
        TO < server_principal >  [ ,...n ]  
    [ WITH GRANT OPTION ]  
    [ AS SQL_Server_login ]   
  
<server_principal> ::=   
        SQL_Server_login  
    | SQL_Server_login_from_Windows_login   
    | SQL_Server_login_from_certificate   
    | SQL_Server_login_from_AsymKey  
```  
  
## <a name="arguments"></a>引数  
 *アクセス許可*  
 エンドポイントで許可できる権限を指定します。 権限の一覧については、後の「解説」を参照してください。  
  
 エンドポイントで**::***endpoint_name*  
 権限を許可するエンドポイントを指定します。 スコープ修飾子 (**::**) が必要です。  
  
 \<Server_principal >  
 指定します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログイン権限を許可します。  
  
 *SQL_Server_login*  
 名前を指定、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインします。  
  
 *SQL_Server_login_from_Windows_login*  
 名前を指定、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows ログインから作成されたログインします。  
  
 *SQL_Server_login_from_certificate*  
 名前を指定、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]証明書にマップされるログインです。  
  
 *SQL_Server_login_from_AsymKey*  
 名前を指定、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]非対称キーにマップされるログインです。  
  
 WITH GRANT OPTION  
 権限が許可されたプリンシパルが、この権限を他のプリンシパルにも許可できることを示します。  
  
 AS *SQL_Server_login*  
 指定します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]このクエリを実行するプリンシパルが権限を許可する権利の派生元となるログインします。  
  
## <a name="remarks"></a>解説  
 現在のデータベースが場合にのみ、サーバー スコープの権限を許可できる**マスター**です。  
  
 エンドポイントに関する情報は、 [sys.endpoints](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md)カタログ ビューです。 サーバー権限に関する情報は、 [sys.server_permissions](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md)カタログ ビュー、およびサーバー プリンシパルに関する情報に表示されて、 [sys.server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)カタログ ビューです。  
  
 エンドポイントは、サーバー レベルのセキュリティ保護可能なリソースです。 次の表に、エンドポイントで許可できる権限のうち最も限定的なものを、それらを暗黙的に含む一般的な権限と共に示します。  
  
|エンドポイント権限|権限が含まれるエンドポイント権限|権限が含まれるサーバー権限|  
|-------------------------|------------------------------------|----------------------------------|  
|ALTER|CONTROL|ALTER ANY ENDPOINT|  
|CONNECT|CONTROL|CONTROL SERVER|  
|CONTROL|CONTROL|CONTROL SERVER|  
|TAKE OWNERSHIP|CONTROL|CONTROL SERVER|  
|VIEW DEFINITION|CONTROL|VIEW ANY DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 エンドポイントに対する CONTROL 権限、またはサーバーに対する ALTER ANY ENDPOINT 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-granting-view-definition-permission-on-an-endpoint"></a>A. エンドポイントの VIEW DEFINITION 権限を許可する  
 次の例では付与`VIEW DEFINITION`エンドポイントに対する権限`Mirror7`に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログイン`ZArifin`です。  
  
```  
USE master;  
GRANT VIEW DEFINITION ON ENDPOINT::Mirror7 TO ZArifin;  
GO  
```  
  
### <a name="b-granting-take-ownership-permission-with-the-grant-option"></a>B. GRANT OPTION を指定して TAKE OWNERSHIP 権限を許可する  
 次の例では付与`TAKE OWNERSHIP`エンドポイントに対する権限`Shipping83`に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ユーザー`PKomosinski`で、`GRANT OPTION`です。  
  
```  
USE master;  
GRANT TAKE OWNERSHIP ON ENDPOINT::Shipping83 TO PKomosinski   
    WITH GRANT OPTION;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [エンドポイントの権限 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-endpoint-permissions-transact-sql.md)   
 [エンドポイントの権限 &#40; を取り消すTRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-endpoint-permissions-transact-sql.md)   
 [CREATE ENDPOINT &#40;Transact-SQL&#41;](../../t-sql/statements/create-endpoint-transact-sql.md)   
 [エンドポイントのカタログ ビュー & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)   
 [sys.endpoints & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md)   
 [アクセス許可 &#40;データベース エンジン&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  

