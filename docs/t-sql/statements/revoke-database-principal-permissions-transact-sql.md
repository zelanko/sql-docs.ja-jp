---
title: "データベース プリンシパルの権限を REVOKE (TRANSACT-SQL) |Microsoft ドキュメント"
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
- database roles [SQL Server], permissions
- REVOKE statement, roles
- database user permissions [SQL Server]
- REVOKE statement, users
- application roles [SQL Server], permissions
ms.assetid: c45e1086-c25b-48bb-a764-4a893e983db2
caps.latest.revision: 30
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: eee64655f9ac49775692d88ff6bcd95fd7ff28f4
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="revoke-database-principal-permissions-transact-sql"></a>REVOKE (データベース プリンシパルの権限の取り消し) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  データベース ユーザー、データベース ロール、アプリケーション ロールに対して許可または拒否された権限を取り消します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
REVOKE [ GRANT OPTION FOR ] permission [ ,...n ]    
    ON   
    {  [ USER :: database_user ]  
       | [ ROLE :: database_role ]  
       | [ APPLICATION ROLE :: application_role ]  
    }  
    { FROM | TO } <database_principal> [ ,...n ]  
        [ CASCADE ]  
    [ AS <database_principal> ]  
  
<database_principal> ::=  
        Database_user   
    | Database_role   
    | Application_role   
    | Database_user_mapped_to_Windows_User   
    | Database_user_mapped_to_Windows_Group   
    | Database_user_mapped_to_certificate   
    | Database_user_mapped_to_asymmetric_key   
    | Database_user_with_no_login   
```  
  
## <a name="arguments"></a>引数  
 *アクセス許可*  
 データベース プリンシパルで取り消すことのできる権限を指定します。 権限の一覧については、後の「解説」を参照してください。  
  
 ユーザー::*database_user*  
 権限を取り消すユーザーのクラスと名前を指定します。 スコープ修飾子 (**::**) が必要です。  
  
 ロール::*database_role*  
 権限を取り消すロールのクラスと名前を指定します。 スコープ修飾子 (**::**) が必要です。  
  
 アプリケーション ロール::*application_role*  
**適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]
  
 権限を取り消すアプリケーション ロールのクラスと名前を指定します。 スコープ修飾子 (**::**) が必要です。  
  
 GRANT OPTION  
 指定した権限を他のプリンシパルに許可するための権利が、取り消されます。 その権限自体は失効しません。  
  
> [!IMPORTANT]  
>  指定した権限が GRANT オプションなしでプリンシパルに許可されている場合は、その権限自体が取り消されます。  
  
 CASCADE  
 このプリンシパルによって権限が許可または拒否されている他のプリンシパルからも、同じ権限が取り消されることを示します。  
  
> [!CAUTION]  
>  WITH GRANT OPTION で許可されている権限を CASCADE で取り消すと、その権限の GRANT および DENY の両方が取り消されます。  
  
 AS \<database_principal > このクエリを実行するプリンシパルの権限を取り消す権利の派生元のプリンシパルを指定します。  
  
 *Database_user*  
 データベース ユーザーを指定します。  
  
 *Database_role*  
 データベース ロールを指定します。  
  
 *Application_role*  
**適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]
  
 アプリケーション ロールを指定します。  
  
 *Database_user_mapped_to_Windows_User*  
**適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Windows ユーザーにマップされているデータベース ユーザーを指定します。  
  
 *Database_user_mapped_to_Windows_Group*  
**適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Windows グループにマップされているデータベース ユーザーを指定します。  
  
 *Database_user_mapped_to_certificate*  
**適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 証明書にマップされているデータベース ユーザーを指定します。  
  
 *Database_user_mapped_to_asymmetric_key*  
**適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 非対称キーにマップされているデータベース ユーザーを指定します。  
  
 *Database_user_with_no_login*  
 対応するサーバー レベルのプリンシパルがないデータベース ユーザーを指定します。  
  
## <a name="remarks"></a>解説  
  
## <a name="database-user-permissions"></a>データベース ユーザー権限  
 データベース ユーザーは、データベース レベルのセキュリティ保護可能なリソースで、権限の階層で親となっているデータベースに含まれています。 次の表に、データベース ユーザーで取り消すことができる権限のうち最も限定的なものを、それらを暗黙的に含む一般的な権限と共に示します。  
  
|データベース ユーザーのアクセス許可|権限が含まれるデータベース ユーザー権限|権限が含まれるデータベース権限|  
|------------------------------|-----------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|IMPERSONATE|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY USER|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="database-role-permissions"></a>データベース ロール権限  
 データベース ロールは、データベース レベルのセキュリティ保護可能なリソースで、権限の階層で親となっているデータベースに含まれています。 次の表に、データベース ロールで取り消すことができる権限のうち最も限定的なものを、それらを暗黙的に含む一般的な権限と共に示します。  
  
|データベース ロール権限|権限が含まれるデータベース ロール権限|権限が含まれるデータベース権限|  
|------------------------------|-----------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY ROLE|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="application-role-permissions"></a>アプリケーション ロールの権限  
 アプリケーション ロールは、データベース レベルのセキュリティ保護可能なリソースで、権限の階層で親となっているデータベースに含まれています。 次の表に、アプリケーション ロールで取り消すことのできる権限のうち最も限定的なものを、それらを暗黙的に含む一般的な権限と共に示します。  
  
|アプリケーション ロール権限|権限が含まれるアプリケーション ロール権限|権限が含まれるデータベース権限|  
|---------------------------------|--------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY APPLICATION ROLE|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 指定したプリンシパルに対する CONTROL 権限、または CONTROL 権限を暗黙的に含む上位の権限が必要です。  
  
 メンバーなど、データベースに対する CONTROL 権限の付与、 **db_owner**固定データベース ロールがいずれかに対する権限を許可できるデータベースのセキュリティ保護可能な。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-revoking-control-permission-on-a-user-from-another-user"></a>A. ユーザーに対する CONTROL 権限を別のユーザーから取り消す  
 次の例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] ユーザー `CONTROL` に対する `Wanida` 権限を、ユーザー `RolandX` から取り消します。  
  
```  
USE AdventureWorks2012;  
REVOKE CONTROL ON USER::Wanida FROM RolandX;  
GO  
```  
  
### <a name="b-revoking-view-definition-permission-on-a-role-from-a-user-to-which-it-was-granted-with-grant-option"></a>B. ロールに対する VIEW DEFINITION 権限を、WITH GRANT OPTION で権限が許可されたユーザーから取り消す  
 次の例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] ロール `VIEW DEFINITION` に対する `SammamishParking` 権限を、データベース ユーザー `JinghaoLiu` から取り消します。 `CASCADE`ためオプションが指定されてユーザー`JinghaoLiu`権限が許可された`VIEW DEFINITION`権限`WITH GRANT OPTION`です。  
  
```  
USE AdventureWorks2012;  
REVOKE VIEW DEFINITION ON ROLE::SammamishParking   
    FROM JinghaoLiu CASCADE;  
GO  
```  
  
### <a name="c-revoking-impersonate-permission-on-a-user-from-an-application-role"></a>C. ユーザーに対する IMPERSONATE 権限をアプリケーション ロールから取り消す  
 次の例では失効`IMPERSONATE`ユーザーに対する権限`HamithaL`から[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]アプリケーション ロール`AccountsPayable17`です。  
  
**適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]
  
```  
USE AdventureWorks2012;  
REVOKE IMPERSONATE ON USER::HamithaL FROM AccountsPayable17;  
GO    
```  
  
## <a name="see-also"></a>参照  
 [データベース プリンシパルの権限の GRANT & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/grant-database-principal-permissions-transact-sql.md)   
 [データベース プリンシパルの権限 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-database-principal-permissions-transact-sql.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [sys.database_permissions および #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)   
 [CREATE USER &#40;Transact-SQL&#41;](../../t-sql/statements/create-user-transact-sql.md)   
 [APPLICATION ROLE &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-application-role-transact-sql.md)   
 [ROLE &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-role-transact-sql.md)   
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [アクセス許可 &#40;データベース エンジン&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  


