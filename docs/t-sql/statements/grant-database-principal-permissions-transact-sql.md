---
title: "データベース プリンシパル アクセス許可の付与 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/12/2017
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
- database roles [SQL Server], permissions
- permissions [SQL Server], database roles
- granting permissions [SQL Server], database users
- granting permissions [SQL Server], application roles
- granting permissions [SQL Server], database roles
- database user permissions [SQL Server]
- permissions [SQL Server], application roles
- permissions [SQL Server], database users
- GRANT statement, users
- GRANT statement, roles
- application roles [SQL Server], permissions
ms.assetid: 012588a2-cbe1-48f0-a731-b4a2b83203d5
caps.latest.revision: 24
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a2d78167459a509d788e65ad31d4660298107558
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="grant-database-principal-permissions-transact-sql"></a>GRANT (データベース プリンシパルの権限の許可) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータベース ユーザー、データベース ロール、またはアプリケーション ロールに対する権限を許可します。  
  

 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
GRANT permission [ ,...n ]    
    ON   
    {  [ USER :: database_user ]  
     | [ ROLE :: database_role ]  
     | [ APPLICATION ROLE :: application_role ]  
    }  
    TO <database_principal> [ ,...n ]  
       [ WITH GRANT OPTION ]  
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
 データベース プリンシパルに対して許可できる権限を指定します。 権限の一覧については、後の「解説」を参照してください。  
  
 ユーザー::*database_user*  
 権限を許可するユーザーのクラスと名前を指定します。 スコープ修飾子 (::) が必要です。  
  
 ロール::*database_role*  
 権限を許可するロールのクラスと名前を指定します。 スコープ修飾子 (::) が必要です。  
  
 アプリケーション ロール::*application_role*  
   
 権限を許可するアプリケーション ロールのクラスと名前を指定します。 スコープ修飾子 (::) が必要です。  
  
 WITH GRANT OPTION  
 権限が許可されたプリンシパルが、この権限を他のプリンシパルにも許可できることを示します。  
  
 AS \<database_principal >  
 このクエリを実行するプリンシパルが権限を許可する権利を取得した、元のプリンシパルを指定します。  
  
 *Database_user*  
 データベース ユーザーを指定します。  
  
 *Database_role*  
 データベース ロールを指定します。  
  
 *Application_role*  
 **適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]です。  
  
 アプリケーション ロールを指定します。  
  
 *Database_user_mapped_to_Windows_User*  
 Windows ユーザーにマップされるデータベース ユーザーを指定します。  
  
 *Database_user_mapped_to_Windows_Group*  
  
 Windows グループにマップされているデータベース ユーザーを指定します。  
  
 *Database_user_mapped_to_certificate*  
  
 証明書にマップされているデータベース ユーザーを指定します。  
  
 *Database_user_mapped_to_asymmetric_key*  
  
 非対称キーにマップされているデータベース ユーザーを指定します。  
  
 *Database_user_with_no_login*  
 対応するサーバー レベルのプリンシパルがないデータベース ユーザーを指定します。  
  
## <a name="remarks"></a>解説  
 データベース プリンシパルに関する情報は、 [sys.database_principals](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)カタログ ビューです。 データベース レベルの権限に関する情報は、 [sys.database_permissions](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)カタログ ビューです。  
  
## <a name="database-user-permissions"></a>データベース ユーザー権限  
 データベース ユーザーは、データベース レベルのセキュリティ保護可能なリソースで、権限の階層で親となっているデータベースに含まれています。 次の表に、データベース ユーザーで許可できる権限のうち最も限定的なものを、それらを暗黙的に含む一般的な権限と共に示します。  
  
|データベース ユーザーのアクセス許可|権限が含まれるデータベース ユーザー権限|権限が含まれるデータベース権限|  
|------------------------------|-----------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|IMPERSONATE|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY USER|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="database-role-permissions"></a>データベース ロール権限  
 データベース ロールは、データベース レベルのセキュリティ保護可能なリソースで、権限の階層で親となっているデータベースに含まれています。 次の表に、データベース ロールで許可できる権限のうち最も限定的なものを、それらを暗黙的に含む一般的な権限と共に示します。  
  
|データベース ロール権限|権限が含まれるデータベース ロール権限|権限が含まれるデータベース権限|  
|------------------------------|-----------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY ROLE|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="application-role-permissions"></a>アプリケーション ロールの権限  
 アプリケーション ロールは、データベース レベルのセキュリティ保護可能なリソースで、権限の階層で親となっているデータベースに含まれています。 次の表に、アプリケーション ロールで許可できる権限のうち最も限定的なものを、それらを暗黙的に含む一般的な権限と共に示します。  
  
|アプリケーション ロール権限|権限が含まれるアプリケーション ロール権限|権限が含まれるデータベース権限|  
|---------------------------------|--------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY APPLICATION ROLE|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 権限の許可者 (または AS オプションで指定されたプリンシパル) は、GRANT OPTION によって与えられた権限を保持しているか、権限が暗黙的に与えられる上位の権限を保持している必要があります。  
  
 AS オプションを使用している場合は、次の追加要件が適用されます。  
  
|AS *granting_principal*|必要な追加権限|  
|------------------------------|------------------------------------|  
|データベース ユーザー|ユーザーに対する IMPERSONATE 権限、db_securityadmin 固定データベース ロールのメンバーシップ、db_owner 固定データベース ロールのメンバーシップ、または sysadmin 固定サーバー ロールのメンバーシップ。|  
|Windows ユーザーにマップされているデータベース ユーザー|ユーザーに対する IMPERSONATE 権限、db_securityadmin 固定データベース ロールのメンバーシップ、db_owner 固定データベース ロールのメンバーシップ、または sysadmin 固定サーバー ロールのメンバーシップ。|  
|Windows グループにマップされるデータベース ユーザー|Windows グループのメンバーシップ、db_securityadmin 固定データベース ロールのメンバーシップ、db_owner 固定データベース ロールのメンバーシップ、または sysadmin 固定サーバー ロールのメンバーシップ。|  
|証明書にマップされているデータベース ユーザー|db_securityadmin 固定データベース ロールのメンバーシップ、db_owner 固定データベース ロールのメンバーシップ、または sysadmin 固定サーバー ロールのメンバーシップ。|  
|非対称キーにマップされるデータベース ユーザー|Db_securityadminfixed データベース ロールのメンバーシップ、db_owner 固定データベース ロール、またはメンバーシップが sysadmin 固定サーバー ロール。|  
|任意のサーバー プリンシパルにマップされていないデータベース ユーザー|ユーザーに対する IMPERSONATE 権限、db_securityadmin 固定データベース ロールのメンバーシップ、db_owner 固定データベース ロールのメンバーシップ、または sysadmin 固定サーバー ロールのメンバーシップ。|  
|データベース ロール|役割、db_securityadminfixed データベース ロールのメンバーシップ、db_owner 固定データベース ロールのメンバーシップ、または sysadmin 固定サーバー ロールのメンバーシップに対する ALTER 権限。|  
|アプリケーション ロール|ロールに対する ALTER 権限、db_securityadmin 固定データベース ロールのメンバーシップ、db_owner 固定データベース ロールのメンバーシップ、または sysadmin 固定サーバー ロールのメンバーシップ。|  
  
 セキュリティ保護可能なことができますの CONTROL 権限を持っているプリンシパルのアクセス許可を付与するセキュリティ保護可能な。  
  
 db_owner 固定データベース ロールのメンバーなど、データベースに対する CONTROL 権限が許可されているユーザーは、データベース内のセキュリティ保護可能なリソースに対する権限を許可できます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-granting-control-permission-on-a-user-to-another-user"></a>A. ユーザーに対する CONTROL 権限を別のユーザーに許可する  
 次の例では、`CONTROL` のユーザー `AdventureWorks2012` に対する `Wanida` 権限を、ユーザー `RolandX` に許可します。  
  
```  
GRANT CONTROL ON USER::Wanida TO RolandX;  
GO  
```  
  
### <a name="b-granting-view-definition-permission-on-a-role-to-a-user-with-grant-option"></a>B. ロールに対する VIEW DEFINITION 権限を、GRANT OPTION を指定してユーザーに許可する  
 次の例では付与`VIEW DEFINITION`に対する権限`AdventureWorks2012`ロール`SammamishParking`と共に`GRANT OPTION`データベース ユーザーに`JinghaoLiu`です。  
  
```  
GRANT VIEW DEFINITION ON ROLE::SammamishParking   
    TO JinghaoLiu WITH GRANT OPTION;  
GO  
```  
  
### <a name="c-granting-impersonate-permission-on-a-user-to-an-application-role"></a>C. ユーザーに対する IMPERSONATE 権限をアプリケーション ロールに許可する  
 次の例では付与`IMPERSONATE`ユーザーに対する権限`HamithaL`に`AdventureWorks2012`アプリケーション ロール`AccountsPayable17`です。  
  
**適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]です。  
  
```  
GRANT IMPERSONATE ON USER::HamithaL TO AccountsPayable17;  
GO    
```  
  
## <a name="see-also"></a>参照  
 [データベース プリンシパルの権限 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-database-principal-permissions-transact-sql.md)   
 [データベース プリンシパルの権限 &#40; を取り消すTRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-database-principal-permissions-transact-sql.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [sys.database_permissions および #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)   
 [CREATE USER &#40;Transact-SQL&#41;](../../t-sql/statements/create-user-transact-sql.md)   
 [APPLICATION ROLE &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-application-role-transact-sql.md)   
 [ROLE &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-role-transact-sql.md)   
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [アクセス許可 &#40;データベース エンジン&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  

