---
title: "可用性グループの権限 (TRANSACT-SQL) の拒否 |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/15/2017
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
- Availability Groups [SQL Server], permissions
- permissions [SQL Server], availability group
- DENY statement, availability groups
- denying permissions, [SQL Server], availability groups
ms.assetid: bda60b36-a0b9-4c20-80c1-6a5cb1d638a5
caps.latest.revision: 12
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1d2e96c60c2811f0a0a87de3d50e3567cd8655cf
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="deny-availability-group-permissions-transact-sql"></a>可用性グループの権限の拒否 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  内の Always On 可用性グループに対する権限を拒否[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
DENY permission  [ ,...n ] ON AVAILABILITY GROUP :: availability_group_name  
        TO < server_principal >  [ ,...n ]  
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
 可用性グループに対して拒否できる権限を指定します。 権限の一覧については、後の「解説」を参照してください。  
  
 可用性グループに対する**::***availability_group_name*  
 権限を拒否する可用性グループを指定します。 スコープ修飾子 (**::**) が必要です。  
  
 \<Server_principal >  
 指定します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログイン権限を拒否します。  
  
 *SQL_Server_login*  
 名前を指定、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインします。  
  
 *SQL_Server_login_from_Windows_login*  
 名前を指定、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows ログインから作成されたログインします。  
  
 *SQL_Server_login_from_certificate*  
 名前を指定、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]証明書にマップされるログインです。  
  
 *SQL_Server_login_from_AsymKey*  
 名前を指定、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]非対称キーにマップされるログインです。  
  
 CASCADE  
 このプリンシパルによって権限が許可されている他のプリンシパルに対しても、同じ権限を拒否することを示します。  
  
 AS *SQL_Server_login*  
 指定します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]このクエリを実行するプリンシパルが権限を拒否する権利の派生元となるログインします。  
  
## <a name="remarks"></a>解説  
 現在のデータベースが場合にのみ、サーバー スコープの権限を拒否できる**マスター**です。  
  
 可用性グループに関する情報は、 [sys.availability_groups & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md)カタログ ビューです。 サーバー権限に関する情報は、 [sys.server_permissions](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md)カタログ ビュー、およびサーバー プリンシパルに関する情報に表示されて、 [sys.server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)カタログ ビューです。  
  
 可用性グループは、サーバー レベルのセキュリティ保護可能なリソースです。 次の表に、可用性グループで拒否できる権限のうち最も限定的なものを、それらを暗黙的に含む一般的な権限と共に示します。  
  
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
  
### <a name="a-denying-view-definition-permission-on-an-availability-group"></a>A. 可用性グループの VIEW DEFINITION 権限を拒否する  
 次の例を拒否`VIEW DEFINITION`可用性グループの権限`MyAg`に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログイン`ZArifin`です。  
  
```  
USE master;  
DENY VIEW DEFINITION ON AVAILABILITY GROUP::MyAg TO ZArifin;  
GO  
```  
  
### <a name="b-denying-take-ownership-permission-with-the-cascade-option"></a>B. CASCADE オプションを使用して TAKE OWNERSHIP 権限を拒否します。  
 次の例では、可用性グループ `TAKE OWNERSHIP` での `MyAg` 権限を、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーザー `PKomosinski` に対して拒否します。ここでは `CASCADE` オプションを使用します。  
  
```  
USE master;  
DENY TAKE OWNERSHIP ON AVAILABILITY GROUP::MyAg TO PKomosinski   
    CASCADE;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [REVOKE 可用性グループの権限 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-availability-group-permissions-transact-sql.md)   
 [GRANT 可用性グループの権限 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/grant-availability-group-permissions-transact-sql.md)   
 [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-availability-group-transact-sql.md)   
 [sys.availability_groups & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md)   
 [AlwaysOn 可用性グループのカタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)   
 [アクセス許可 &#40;データベース エンジン&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  

