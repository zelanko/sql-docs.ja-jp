---
title: "エンドポイントの権限 (TRANSACT-SQL) を取り消す |Microsoft ドキュメント"
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
- endpoints [SQL Server], permissions
- REVOKE statement, endpoints
- permissions [SQL Server], endpoints
ms.assetid: 826f513e-9ad0-46b9-87ad-7525713638c8
caps.latest.revision: 24
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ad8770d584c82fc6c5de12104059717030d21f87
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="revoke-endpoint-permissions-transact-sql"></a>REVOKE (エンドポイントの権限の取り消し) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  エンドポイントに対して許可または拒否された権限を取り消します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
REVOKE [ GRANT OPTION FOR ] permission [ ,...n ]   
    ON ENDPOINT :: endpoint_name  
    { FROM | TO } <server_principal> [ ,...n ]  
    [ CASCADE ]  
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
  
 {から |} \<Server_principal > を指定します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]アクセス許可の失効してログインします。  
  
 *SQL_Server_login*  
 名前を指定、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインします。  
  
 *SQL_Server_login_from_Windows_login*  
 名前を指定、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows ログインから作成されたログインします。  
  
 *SQL_Server_login_from_certificate*  
 名前を指定、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]証明書にマップされるログインです。  
  
 *SQL_Server_login_from_AsymKey*  
 名前を指定、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]非対称キーにマップされるログインです。  
  
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
 現在のデータベースが場合にのみ、サーバー スコープの権限を取り消すことができます**マスター**です。  
  
 エンドポイントに関する情報は、 [sys.endpoints](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md)カタログ ビューです。 サーバー権限に関する情報は、 [sys.server_permissions](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md)カタログ ビュー、およびサーバー プリンシパルに関する情報に表示されて、 [sys.server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)カタログ ビューです。  
  
 エンドポイントは、サーバー レベルのセキュリティ保護可能なリソースです。 次の表に、エンドポイントで取り消すことができる権限のうち最も限定的なものを、それらを暗黙的に含む一般的な権限と共に示します。  
  
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
  
### <a name="a-revoking-view-definition-permission-on-an-endpoint"></a>A. エンドポイントの VIEW DEFINITION 権限を取り消す  
 次の例では、エンドポイント `VIEW DEFINITION` での `Mirror7` 権限を、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログイン `ZArifin` から取り消します。  
  
```  
USE master;  
REVOKE VIEW DEFINITION ON ENDPOINT::Mirror7 FROM ZArifin;  
GO  
```  
  
### <a name="b-revoking-take-ownership-permission-with-the-cascade-option"></a>B. CASCADE オプションを指定して TAKE OWNERSHIP 権限を取り消す  
 次の例では失効`TAKE OWNERSHIP`エンドポイントに対する権限`Shipping83`から、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ユーザー`PKomosinski`とすべてのプリンシパルから`PKomosinski`付与`TAKE OWNERSHIP`で`Shipping83`です。  
  
```  
USE master;  
REVOKE TAKE OWNERSHIP ON ENDPOINT::Shipping83 FROM PKomosinski   
    CASCADE;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [GRANT (エンドポイントのアクセス許可の許可) &#40;Transact-SQL&#41;](../../t-sql/statements/grant-endpoint-permissions-transact-sql.md)   
 [エンドポイントの権限 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-endpoint-permissions-transact-sql.md)   
 [CREATE ENDPOINT &#40;Transact-SQL&#41;](../../t-sql/statements/create-endpoint-transact-sql.md)   
 [エンドポイントのカタログ ビュー & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)   
 [sys.endpoints & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md)   
 [アクセス許可 &#40;データベース エンジン&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  


