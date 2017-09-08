---
title: "データベース アクセス許可 (TRANSACT-SQL) |Microsoft ドキュメント"
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
- DENY statement, databases
- permissions [SQL Server], databases
- database permissions [SQL Server], denying
- denying permissions [SQL Server], databases
ms.assetid: 36cc4e2c-5a24-4975-9920-9305f12c6e7c
caps.latest.revision: 43
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bddab793d98b4c9ace1fc0af1cda69a81531bf26
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="deny-database-permissions-transact-sql"></a>DENY (データベースの権限の拒否) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータベースに対する権限を拒否します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
DENY <permission> [ ,...n ]    
    TO <database_principal> [ ,...n ] [ CASCADE ]  
    [ AS <database_principal> ]  
  
<permission> ::=    
    permission | ALL [ PRIVILEGES ]  
  
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
 データベースで取り消すことができる権限を指定します。 権限の一覧については、後の「解説」を参照してください。  
  
 ALL  
 このオプションでは、可能な権限がすべて拒否されるわけではありません。 ALL を指定した場合は、BACKUP DATABASE、BACKUP LOG、CREATE DATABASE、CREATE DEFAULT、CREATE FUNCTION、CREATE PROCEDURE、CREATE RULE、CREATE TABLE、および CREATE VIEW 権限を拒否することになります。  
  
 PRIVILEGES  
 ISO 準拠のために用意されています。 ALL の動作は変更されません。  
  
 CASCADE  
 指定したプリンシパルが権限を許可したプリンシパルに対しても、権限を拒否することを示します。  
  
 AS \<database_principal >  
 このクエリを実行するプリンシパルが権限を拒否する権利の派生元のプリンシパルを指定します。  
  
 *Database_user*  
 データベース ユーザーを指定します。  
  
 *Database_role*  
 データベース ロールを指定します。  
  
 *Application_role*  
 **適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]です。  
  
 アプリケーション ロールを指定します。  
  
 *Database_user_mapped_to_Windows_User*   
  Windows ユーザーにマップされているデータベース ユーザーを指定します。  
  
 *Database_user_mapped_to_Windows_Group*  
  Windows グループにマップされているデータベース ユーザーを指定します。  
  
 *Database_user_mapped_to_certificate*  
  証明書にマップされているデータベース ユーザーを指定します。  
  
 *Database_user_mapped_to_asymmetric_key*  
  非対称キーにマップされているデータベース ユーザーを指定します。  
  
 *Database_user_with_no_login*  
 対応するサーバー レベルのプリンシパルがないデータベース ユーザーを指定します。  
  
## <a name="remarks"></a>解説  
 データベースは、セキュリティ保護可能なリソースで、権限の階層で親となっているサーバーに含まれています。 次の表に、データベースで拒否できる権限のうち最も限定的なものを、それらを暗黙的に含む一般的な権限と共に示します。  
  
|データベース権限|権限が含まれるデータベース権限|権限が含まれるサーバー権限|  
|-------------------------|------------------------------------|----------------------------------|  
|ADMINISTER DATABASE BULK OPERATIONS<br/>**適用対象:** [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]」を参照してください。|CONTROL|CONTROL SERVER|
|ALTER|CONTROL|ALTER ANY DATABASE|  
|ALTER ANY APPLICATION ROLE|ALTER|CONTROL SERVER|  
|ALTER ANY ASSEMBLY|ALTER|CONTROL SERVER|  
|ALTER ANY ASYMMETRIC KEY|ALTER|CONTROL SERVER|  
|ALTER ANY CERTIFICATE|ALTER|CONTROL SERVER|  
|任意の列の暗号化キーを変更します。|ALTER|CONTROL SERVER|  
|すべての列のマスター_キーの定義を変更します。|ALTER|CONTROL SERVER|  
|ALTER ANY CONTRACT|ALTER|CONTROL SERVER|  
|ALTER ANY DATABASE AUDIT|ALTER|ALTER ANY SERVER AUDIT|  
|ALTER ANY DATABASE DDL TRIGGER|ALTER|CONTROL SERVER|  
|ALTER ANY DATABASE EVENT NOTIFICATION|ALTER|ALTER ANY EVENT NOTIFICATION|  
|ALTER ANY DATABASE EVENT SESSION<br /> **適用対象**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|ALTER|ALTER ANY EVENT SESSION|  
|ALTER ANY DATABASE SCOPED CONFIGURATION<br />  **適用されます**:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]です。|CONTROL|CONTROL SERVER|  
|ALTER ANY DATASPACE|ALTER|CONTROL SERVER|  
|すべての外部データ ソースを変更します。|ALTER|CONTROL SERVER|  
|任意の外部のファイル形式を変更します。|ALTER|CONTROL SERVER|  
|任意の外部ライブラリを変更します。 <br /> **適用対象**: [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]|CONTROL|CONTROL SERVER |    
|ALTER ANY FULLTEXT CATALOG|ALTER|CONTROL SERVER|  
|任意のマスクを変更します。|CONTROL|CONTROL SERVER|  
|ALTER ANY MESSAGE TYPE|ALTER|CONTROL SERVER|  
|ALTER ANY REMOTE SERVICE BINDING|ALTER|CONTROL SERVER|  
|ALTER ANY ROLE|ALTER|CONTROL SERVER|  
|ALTER ANY ROUTE|ALTER|CONTROL SERVER|  
|すべてのセキュリティ ポリシーを変更します。<br /> **適用されます**:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。|CONTROL|CONTROL SERVER|  
|ALTER ANY SCHEMA|ALTER|CONTROL SERVER|  
|ALTER ANY SERVICE|ALTER|CONTROL SERVER|  
|ALTER ANY SYMMETRIC KEY|ALTER|CONTROL SERVER|  
|ALTER ANY USER|ALTER|CONTROL SERVER|  
|AUTHENTICATE|CONTROL|AUTHENTICATE SERVER|  
|BACKUP DATABASE|CONTROL|CONTROL SERVER|  
|BACKUP LOG|CONTROL|CONTROL SERVER|  
|CHECKPOINT|CONTROL|CONTROL SERVER|  
|CONNECT|CONNECT REPLICATION|CONTROL SERVER|  
|CONNECT REPLICATION|CONTROL|CONTROL SERVER|  
|CONTROL|CONTROL|CONTROL SERVER|  
|CREATE AGGREGATE|ALTER|CONTROL SERVER|  
|CREATE ASSEMBLY|ALTER ANY ASSEMBLY|CONTROL SERVER|  
|CREATE ASYMMETRIC KEY|ALTER ANY ASYMMETRIC KEY|CONTROL SERVER|  
|CREATE CERTIFICATE|ALTER ANY CERTIFICATE|CONTROL SERVER|  
|CREATE CONTRACT|ALTER ANY CONTRACT|CONTROL SERVER|  
|CREATE DATABASE|CONTROL|CREATE ANY DATABASE|  
|CREATE DATABASE DDL EVENT NOTIFICATION|ALTER ANY DATABASE EVENT NOTIFICATION|CREATE DDL EVENT NOTIFICATION|  
|CREATE DEFAULT|ALTER|CONTROL SERVER|  
|CREATE FULLTEXT CATALOG|ALTER ANY FULLTEXT CATALOG|CONTROL SERVER|  
|CREATE FUNCTION|ALTER|CONTROL SERVER|  
|CREATE MESSAGE TYPE|ALTER ANY MESSAGE TYPE|CONTROL SERVER|  
|CREATE PROCEDURE|ALTER|CONTROL SERVER|  
|CREATE QUEUE|ALTER|CONTROL SERVER|  
|CREATE REMOTE SERVICE BINDING|ALTER ANY REMOTE SERVICE BINDING|CONTROL SERVER|  
|CREATE ROLE|ALTER ANY ROLE|CONTROL SERVER|  
|CREATE ROUTE|ALTER ANY ROUTE|CONTROL SERVER|  
|CREATE RULE|ALTER|CONTROL SERVER|  
|CREATE SCHEMA|ALTER ANY SCHEMA|CONTROL SERVER|  
|CREATE SERVICE|ALTER ANY SERVICE|CONTROL SERVER|  
|CREATE SYMMETRIC KEY|ALTER ANY SYMMETRIC KEY|CONTROL SERVER|  
|CREATE SYNONYM|ALTER|CONTROL SERVER|  
|CREATE TABLE|ALTER|CONTROL SERVER|  
|CREATE TYPE|ALTER|CONTROL SERVER|  
|CREATE VIEW|ALTER|CONTROL SERVER|  
|CREATE XML SCHEMA COLLECTION|ALTER|CONTROL SERVER|  
|DELETE|CONTROL|CONTROL SERVER|  
|CREATE ステートメントを実行する前に、|CONTROL|CONTROL SERVER|  
|EXECUTE ANY EXTERNAL SCRIPT <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)]|CONTROL|CONTROL SERVER|   
|INSERT|CONTROL|CONTROL SERVER|  
|KILL DATABASE CONNECTION<br /> **適用対象**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|CONTROL|ALTER ANY CONNECTION|  
|REFERENCES|CONTROL|CONTROL SERVER|  
|SELECT|CONTROL|CONTROL SERVER|  
|SHOWPLAN|CONTROL|ALTER TRACE|  
|SUBSCRIBE QUERY NOTIFICATIONS|CONTROL|CONTROL SERVER|  
|TAKE OWNERSHIP|CONTROL|CONTROL SERVER|  
|マスク解除します。|CONTROL|CONTROL SERVER|  
|UPDATE|CONTROL|CONTROL SERVER|  
|任意の列暗号化キーを表示します。|CONTROL|VIEW ANY DEFINITION|  
|任意のマスター_キーの定義の表示|CONTROL|VIEW ANY DEFINITION|  
|VIEW DATABASE STATE|CONTROL|VIEW SERVER STATE|  
|VIEW DEFINITION|CONTROL|VIEW ANY DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 このステートメントを実行するプリンシパル (または AS オプションで指定したプリンシパル) には、データベースに対する CONTROL 権限、またはデータベースに対する CONTROL 権限を暗黙的に許可する上位レベルの権限が与えられている必要があります。  
  
 AS オプションを使用する場合、指定するプリンシパルはデータベースを所有している必要があります。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-denying-permission-to-create-certificates"></a>A. 証明書を作成する権限を拒否する  
 次の例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースでの `CREATE CERTIFICATE` 権限を、ユーザー `MelanieK` に対して拒否します。  

```  
USE AdventureWorks2012;  
DENY CREATE CERTIFICATE TO MelanieK;  
GO  
```  
  
### <a name="b-denying-references-permission-to-an-application-role"></a>B. アプリケーション ロールに対して REFERENCES 権限を拒否する  
 次の例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースでの `REFERENCES` 権限を、アプリケーション ロール `AuditMonitor` に対して拒否します。  
  
**適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]です。  
  
```  
USE AdventureWorks2012;  
DENY REFERENCES TO AuditMonitor;  
GO  
```  
  
### <a name="c-denying-view-definition-with-cascade"></a>C. CASCADE を指定して VIEW DEFINITION を拒否する  
 次の例を拒否`VIEW DEFINITION`に対する権限、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベース ユーザー`CarmineEs`とすべてのプリンシパルに`CarmineEs`与え`VIEW DEFINITION`権限です。  
  
```  
USE AdventureWorks2012;  
DENY VIEW DEFINITION TO CarmineEs CASCADE;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sys.database_permissions および #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [アクセス許可 &#40;データベース エンジン&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  

