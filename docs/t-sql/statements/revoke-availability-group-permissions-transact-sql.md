---
title: "REVOKE 可用性グループの権限 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
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
- Availability Groups [SQL Server], permissions
- REVOKE statement, availability groups
- revoking permissions, [SQL Server], availability groups
- permissions [SQL Server], availability group
ms.assetid: 02c77378-a36d-4286-9235-d8867a2b92ad
caps.latest.revision: 10
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1573f866cec3105cde4eeab59c230ede46144ac3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="revoke-availability-group-permissions-transact-sql"></a>可用性グループの権限の取り消し (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Always On 可用性グループに対する権限を取り消します。 
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
REVOKE [ GRANT OPTION FOR ] permission  [ ,...n ]   
    ON AVAILABILITY GROUP :: availability_group_name  
    { FROM | TO } < server_principal >  [ ,...n ]  
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
 可用性グループに対して取り消すことができる権限を指定します。 権限の一覧については、後の「解説」を参照してください。  
  
 可用性グループに対する**::***availability_group_name*  
 権限を取り消す可用性グループを指定します。 スコープ修飾子 (**::**) が必要です。  
  
 {から |} \<Server_principal > を指定します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]権限を取り消すログインします。  
  
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
  
> [!IMPORTANT]  
>  WITH GRANT OPTION で許可されている権限を CASCADE で取り消すと、その権限の GRANT および DENY の両方が取り消されます。  
  
 AS *SQL_Server_login*  
 指定します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]このクエリを実行するプリンシパルの権限を取り消す権利の派生元となるログインします。  
  
## <a name="remarks"></a>解説  
 現在のデータベースが場合にのみ、サーバー スコープの権限を取り消すことができます**マスター**です。  
  
 可用性グループに関する情報は、 [sys.availability_groups & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md)カタログ ビューです。 サーバー権限に関する情報は、 [sys.server_permissions](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md)カタログ ビュー、およびサーバー プリンシパルに関する情報に表示されて、 [sys.server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)カタログ ビューです。  
  
 可用性グループは、サーバー レベルのセキュリティ保護可能なリソースです。 次の表に、可用性グループで取り消すことができる権限のうち最も限定的なものを、それらを暗黙的に含む一般的な権限と共に示します。  
  
|可用性グループの権限|権限が含まれる可用性グループ権限|権限が含まれるサーバー権限|  
|-----------------------------------|----------------------------------------------|----------------------------------|  
|ALTER|CONTROL|ALTER ANY AVAILABILITY GROUP|  
|CONNECT|CONTROL|CONTROL SERVER|  
|CONTROL|CONTROL|CONTROL SERVER|  
|TAKE OWNERSHIP|CONTROL|CONTROL SERVER|  
|VIEW DEFINITION|CONTROL|VIEW ANY DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 可用性グループに対する CONTROL 権限、またはサーバーに対する ALTER ANY AVAILABILTIY GROUP 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-revoking-view-definition-permission-on-an-availability-group"></a>A. 可用性グループの VIEW DEFINITION 権限を取り消す  
 次の例では失効`VIEW DEFINITION`可用性グループの権限`MyAg`に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログイン`ZArifin`です。  
  
```  
USE master;  
REVOKE VIEW DEFINITION ON AVAILABILITY GROUP::MyAg TO ZArifin;  
GO  
```  
  
### <a name="b-revoking-take-ownership-permission-with-the-cascade"></a>B. CASCADE を指定して TAKE OWNERSHIP 権限を取り消す  
 次の例では失効`TAKE OWNERSHIP`可用性グループの権限`MyAg`に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ユーザー`PKomosinski`とすべてのプリンシパルから`PKomosinski`MyAg の TAKE ownership 権限を付与します。  
  
```  
USE master;  
REVOKE TAKE OWNERSHIP ON AVAILABILITY GROUP::MyAg TO PKomosinski   
    CASCADE;  
GO  
```  
  
### <a name="c-revoking-a-previously-granted-with-grant-option-clause"></a>C. 以前に許可した WITH GRANT OPTION 句を取り消す  
 WITH GRANT OPTION を使用してアクセス許可が付与された場合は、REVOKE GRANT OPTION FOR を使用してください. WITH GRANT OPTION を削除します。 次の例では、権限を許可し、その権限の WITH GRANT の部分を取り消します。  
  
```  
USE master;  
GRANT CONTROL ON AVAILABILITY GROUP::MyAg TO PKomosinski   
    WITH GRANT OPTION;  
GO  
REVOKE GRANT OPTION FOR CONTROL ON AVAILABILITY GROUP::MyAg TO PKomosinski  
CASCADE  
GO  
```  
  
## <a name="see-also"></a>参照  
 [GRANT 可用性グループの権限 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/grant-availability-group-permissions-transact-sql.md)   
 [可用性グループの権限 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-availability-group-permissions-transact-sql.md)   
 [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-availability-group-transact-sql.md)   
 [sys.availability_groups & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md)   
 [AlwaysOn 可用性グループのカタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)   
 [アクセス許可 &#40;データベース エンジン&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  


