---
title: "ALTER AUTHORIZATION (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_AUTHORIZATION_TSQL
- ALTER AUTHORIZATION
dev_langs: TSQL
helpviewer_keywords:
- owners [SQL Server], transferring
- modifying entity ownership
- full-text search [SQL Server], permissions
- owners [SQL Server], entities
- ALTER AUTHORIZATION statement
- entity ownership [SQL Server]
- transferring ownership
- search property lists [SQL Server], permissions
- TAKE OWNERSHIP
ms.assetid: 8c805ae2-91ed-4133-96f6-9835c908f373
caps.latest.revision: "84"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: f992d085f8c9b282be4288488cf872d99b426f48
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="alter-authorization-transact-sql"></a>ALTER AUTHORIZATION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  セキュリティ保護可能なエンティティの所有権を変更します。    
    
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)    
    
## <a name="syntax"></a>構文    
    
```    
-- Syntax for SQL Server  
ALTER AUTHORIZATION    
   ON [ <class_type>:: ] entity_name    
   TO { principal_name | SCHEMA OWNER }    
[;]    
    
<class_type> ::=    
    {    
        OBJECT | ASSEMBLY | ASYMMETRIC KEY | AVAILABILITY GROUP | CERTIFICATE     
      | CONTRACT | TYPE | DATABASE | ENDPOINT | FULLTEXT CATALOG     
      | FULLTEXT STOPLIST | MESSAGE TYPE | REMOTE SERVICE BINDING    
      | ROLE | ROUTE | SCHEMA | SEARCH PROPERTY LIST | SERVER ROLE     
      | SERVICE | SYMMETRIC KEY | XML SCHEMA COLLECTION    
    }    
```    

```
-- Syntax for SQL Database  
  
ALTER AUTHORIZATION    
   ON [ <class_type>:: ] entity_name    
   TO { principal_name | SCHEMA OWNER }    
[;]    
    
<class_type> ::=    
    {    
      OBJECT | ASSEMBLY | ASYMMETRIC KEY | CERTIFICATE     
    | TYPE | DATABASE | FULLTEXT CATALOG     
    | FULLTEXT STOPLIST     
    | ROLE | SCHEMA | SEARCH PROPERTY LIST     
    | SYMMETRIC KEY | XML SCHEMA COLLECTION    
    }    
```    

    
```    
-- Syntax for Azure SQL Data Warehouse  
  
ALTER AUTHORIZATION ON    
    [ <class_type> :: ] <entity_name>     
    TO { principal_name | SCHEMA OWNER }    
[;]    
    
<class_type> ::= {    
      SCHEMA     
    | OBJECT     
}    
    
<entity_name> ::=    
{    
      schema_name    
    | [ schema_name. ] object_name    
}    
```    
    
```    
-- Syntax for Parallel Data Warehouse  
  
ALTER AUTHORIZATION ON    
    [ <class_type> :: ] <entity_name>     
    TO { principal_name | SCHEMA OWNER }    
[;]    
    
<class_type> ::= {    
      DATABASE     
    | SCHEMA     
    | OBJECT     
}    
    
<entity_name> ::=    
{    
      database_name 
    | schema_name    
    | [ schema_name. ] object_name    
}    
```    
    
## <a name="arguments"></a>引数    
\<class_type > 所有者が変更されているエンティティのセキュリティ保護可能なクラスです。 既定値は OBJECT です。    
    
|||    
|-|-|    
|OBJECT|**適用対象**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]、Azure SQL Data Warehouse、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]です。|    
|ASSEMBLY|**適用対象**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。|    
|ASYMMETRIC KEY|**適用対象**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。|    
|AVAILABILITY GROUP |**適用対象**: を介して SQL Server 2012[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]です。|
|CERTIFICATE|**適用対象**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。|    
|CONTRACT|**適用対象**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]です。|    
|DATABASE|**適用対象**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。 詳細については、次を参照してください。[承認の ALTER データベース](#AlterDB)以下のセクションです。|    
|ENDPOINT|**適用対象**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]です。|    
|FULLTEXT CATALOG|**適用対象**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。|    
|FULLTEXT STOPLIST|**適用対象**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。|    
|MESSAGE TYPE|**適用対象**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]です。|    
|REMOTE SERVICE BINDING|**適用対象**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]です。|    
|ROLE|**適用対象**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。|    
|ROUTE|**適用対象**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]です。|    
|SCHEMA|**適用対象**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]、Azure SQL Data Warehouse、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]です。|    
|SEARCH PROPERTY LIST|**適用対象**:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。|    
|SERVER ROLE|**適用対象**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]です。|    
|SERVICE|**適用対象**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]です。|    
|SYMMETRIC KEY|**適用対象**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。|    
|TYPE|**適用対象**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。|    
|XML SCHEMA COLLECTION|**適用対象**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。|    
    
 *entity_name*    
 エンティティの名前を指定します。    
    
 *principal_name* |スキーマの所有者    
 エンティティの所有者となるセキュリティ プリンシパルの名前。 データベース オブジェクトはデータベース プリンシパル (データベース ユーザーまたはデータベース ロール) が所有する必要があります。 サーバー オブジェクト (データベースなど) はサーバー プリンシパル (ログイン) が所有する必要があります。 指定**スキーマの所有者**として、 *principal_name*を示すオブジェクトのスキーマを所有するプリンシパルによって、オブジェクトを所有する必要があります。    
    
## <a name="remarks"></a>解説    
 ALTER AUTHORIZATION は、所有者が存在するエンティティの所有権を変更するときに使用できます。 データベースに含まれるエンティティの所有権は、データベース レベルのプリンシパルに譲渡できます。 サーバー レベルのエンティティの所有権は、サーバー レベルのプリンシパルだけに譲渡できます。    
    
> [!IMPORTANT]    
>  以降で[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、オブジェクトまたは別のデータベース ユーザーが所有するスキーマが含まれている型、ユーザーが所有できます。 これは、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の動作から変更されています。 詳細については、次を参照してください。 [OBJECTPROPERTY (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/objectproperty-transact-sql.md)と[TYPEPROPERTY (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/typeproperty-transact-sql.md).    
    
 スキーマに含まれるエンティティのうち、種類が "オブジェクト" のエンティティ (テーブル、ビュー、関数、プロシージャ、キュー、およびシノニム) の所有権は譲渡できます。    
    
 リンク サーバー、統計、制約、ルール、デフォルト、トリガー、[!INCLUDE[ssSB](../../includes/sssb-md.md)] キュー、資格情報、パーティション関数、パーティション構成、データベース マスター キー、サービス マスター キー、およびイベント通知の各エンティティの所有権は譲渡できません。    
    
 セキュリティ保護可能なリソース クラス (サーバー、ログイン、ユーザー、アプリケーション ロール、および列) のメンバーの所有権は譲渡できません。    
    
 SCHEMA OWNER オプションは、スキーマに含まれるエンティティの所有権を譲渡する場合にのみ有効です。 SCHEMA OWNER を使用すると、エンティティの所有権は、所属するスキーマの所有者に譲渡されます。 スキーマに含まれるのは、OBJECT、TYPE、または XML SCHEMA COLLECTION クラスのエンティティだけです。    
    
 対象のエンティティがデータベース以外であり、エンティティを新しい所有者に譲渡する場合は、すべての権限が削除されます。    
    
> [!CAUTION]    
>  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、スキーマの動作が以前のバージョンの動作から変更[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 コードで、スキーマがデータベース ユーザーと同じであることが前提となっている場合、正しい結果が返されない場合があります。 CREATE SCHEMA、ALTER SCHEMA、DROP SCHEMA、CREATE USER、ALTER USER、DROP USER、CREATE ROLE、ALTER ROLE、DROP ROLE、CREATE APPROLE、ALTER APPROLE、DROP APPROLE、ALTER AUTHORIZATION のいずれかの DDL ステートメントが使用されたことのあるデータベースでは、sysobjects を含む以前のカタログ ビューを使用しないでください。 このようなデータベースでは、新しいカタログ ビューを使用する必要があります。 新しいカタログ ビューでは、プリンシパルとで導入されたスキーマの分離を考慮に入れて[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]です。 カタログ ビューの詳細については、「[カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)」を参照してください。    
    
 また、次の点も注意してください。    
    
> [!IMPORTANT]    
>  オブジェクトの所有者を調べる唯一信頼できる方法が、クエリ、 **sys.objects**カタログ ビューです。 型の所有者を調べる唯一の信頼性のある方法は、TYPEPROPERTY 関数を使用する方法です。    
    
## <a name="special-cases-and-conditions"></a>特殊ケースと条件    
 次の表は、権限を変更する際の特殊ケースと例外、および条件の一覧です。    
    
|クラス|条件|    
|-----------|---------------|    
|OBJECT|トリガー、制約、ルール、デフォルト、統計、システム オブジェクト、キュー、インデックス付きビュー、またはインデックス付きビューのあるテーブルの所有権は変更できません。|    
|SCHEMA|所有権を譲渡すると、スキーマに含まれるオブジェクトの所有者が明示的に指定されていない場合は、そのオブジェクトに対する権限が削除されます。 sys、dbo、または information_schema の所有者は変更できません。|    
|TYPE|sys または information_schema に属する TYPE の所有権は変更できません。|    
|CONTRACT、MESSAGE TYPE、SERVICE|システム エンティティの所有権は変更できません。|    
|SYMMETRIC KEY|グローバル一時キーの所有権は変更できません。|    
|CERTIFICATE または ASYMMETRIC KEY|これらのエンティティの所有権をロールまたはグループに譲渡することはできません。|    
|ENDPOINT|プリンシパルは、ログインであることが必要です。|    
  
## <a name="AlterDB"></a>データベースの ALTER AUTHORIZATION  
**適用対象**: [!INCLUDE[ssSQL15](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。  
### <a name="for-sql-server"></a>SQL server:  
**新しい所有者の要件:**   
新しい所有者のプリンシパルは、次のいずれかにする必要があります。  
-   SQL Server 認証ログインです。  
-   Windows ユーザー (グループではなく) を表す Windows 認証ログインです。  
-   Windows グループを表す Windows 認証ログインを認証する Windows ユーザーです。  
  
**ALTER AUTHORIZATION ステートメントを実行しているユーザーの要件:**  
メンバーではない場合、 **sysadmin**固定サーバー ロール、する必要がありますには、少なくとも、データベースに対する TAKE OWNERSHIP 権限と、新しい所有者のログインに対する IMPERSONATE 権限が必要です。   

### <a name="for-azure-sql-database"></a>Azure SQL データベース。  
**新しい所有者の要件:**   
新しい所有者のプリンシパルは、次のいずれかにする必要があります。  
-   SQL Server 認証ログインです。  
-   フェデレーション ユーザー (グループではなく) Azure AD 内に存在します。  
-   マネージ ユーザー (グループではなく) または、アプリケーションを Azure AD 内に存在します。    

> [!NOTE]  
> 新しい所有者が Azure Active Directory ユーザーの場合は、新しい所有者が新しい DBO になりますが、データベース内のユーザーとして存在できません。 このような Azure AD ユーザーは、新しいユーザーにデータベースの所有権を変更する ALTER AUTHORIZATION ステートメントを実行する前にデータベースからまず削除してください。 SQL データベースと Azure Active Directory ユーザーの構成に関する詳細については、次を参照してください。 [SQL データベースまたは SQL データ ウェアハウス認証を使用して Azure Active Directory に接続する](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/)です。   
  
**ALTER AUTHORIZATION ステートメントを実行しているユーザーの要件:**  
そのデータベースの所有者を変更する対象データベースに接続する必要があります。  

次の種類のアカウントには、データベースの所有者を変更できます。 
* サービス レベルのプリンシパル ログインします。 (論理サーバーが作成されたときにプロビジョニングされて SQL Azure 管理者。)  
* Azure の SQL Server 用 Azure Active Directory 管理者。   
* データベースの現在の所有者。   
 
  
次の表は、要件をまとめたもの。  
  
実行子  |移行先  |結果    
---------|---------|---------  
SQL Server 認証ログイン     |SQL Server 認証ログイン         |Success  
SQL Server 認証ログイン     |Azure AD のユーザー         |失敗します。           
Azure AD のユーザー     |SQL Server 認証ログイン         |Success           
Azure AD のユーザー     |Azure AD のユーザー         |Success           
  
確認するデータベースの Azure AD 所有者がユーザー データベースでは、次の TRANSACT-SQL コマンドを実行 (この例では`testdb`)。  
    
```    
SELECT CAST(owner_sid as uniqueidentifier) AS Owner_SID   
FROM sys.databases   
WHERE name = 'testdb';  
```    
    
出力は Azure AD のオブジェクト Id に割り当てるに対応するの識別子 (6D8B81F6-7C79-444C-8858-4AF896C03C67) などになります`richel@cqclinic.onmicrosoft.com`  
SQL Server 認証ログイン ユーザーがデータベース所有者の場合、データベースの所有者を確認する master データベースで次のステートメントを実行します。  
    
```    
SELECT d.name, d.owner_sid, sl.name   
FROM sys.databases AS d  
JOIN sys.sql_logins AS sl  
ON d.owner_sid = sl.sid;  
    
```    
  
### <a name="best-practice"></a>ベスト プラクティス  
  
を使う代わりに Azure AD ユーザーがデータベースの個別の所有者としてのメンバーとして、Azure AD グループを使用して、 **db_owner**固定データベース ロール。 次の手順では、データベース所有者では、無効なログインを構成して、Azure Active Directory グループを作成する方法を表示する (`mydbogroup`) のメンバー、 **db_owner**ロール。 
1.  Azure AD 管理者、および無効化された SQL Server 認証ログインにデータベースの所有者の変更として SQL Server にログインします。 たとえば、ユーザー データベースから次のように実行します。  
  ```    
  ALTER AUTHORIZATION ON database::testdb TO DisabledLogin;  
  ```    
2.  データベースを所有し、ユーザー データベースへのユーザーとして追加する必要がありますを Azure AD グループを作成します。 例:  
  ```    
  CREATE USER [mydbogroup] FROM EXTERNAL PROVIDER;  
  ```    
3.  ユーザー データベース内に、Azure AD グループを表す、ユーザーの追加、 **db_owner**固定データベース ロール。 例:  
  ```    
  ALTER ROLE db_owner ADD MEMBER mydbogroup;  
  ```    
  
これで、`mydbogroup`メンバーは、のメンバーとしてのデータベースを一元的に管理、 **db_owner**ロール。  
- このグループのメンバーは、Azure AD グループから削除され、ときに、自動的にこのデータベースの dbo アクセス許可は失われます。  
- 同様に新しいメンバーを追加する場合`mydbogroup`Azure AD のグループに自動的に取得するこのデータベースの dbo アクセスします。  
  
確認するには、特定のユーザーが、有効な dbo アクセス許可を持つかどうか、次のステートメントを実行するユーザーがあります。  
    
```    
SELECT IS_MEMBER ('db_owner');  
```    
  
戻り値 1 は、ユーザーは、ロールのメンバーを示します。  
   
    
## <a name="permissions"></a>Permissions    
 エンティティに対する TAKE OWNERSHIP 権限が必要です。 新しい所有者がステートメントを実行するユーザーではない場合は、次の条件に応じた権限が必要になります。1) 新しい所有者がユーザーまたはログインの場合は、新しい所有者に対する IMPERSONATE 権限。2) 新しい所有者がロールまたはロールのメンバーシップの場合は、ロールに対する ALTER 権限。3) 新しい所有者がアプリケーション ロールの場合は、アプリケーション ロールに対する ALTER 権限。    
    
## <a name="examples"></a>使用例    
    
### <a name="a-transfer-ownership-of-a-table"></a>A. テーブルの所有権を譲渡    
 次の例は、テーブルの所有権を譲渡`Sprockets`ユーザーに`MichikoOsada`です。 テーブルがスキーマ内にある`Parts`です。    
    
```    
ALTER AUTHORIZATION ON OBJECT::Parts.Sprockets TO MichikoOsada;    
GO    
```    
    
 クエリは次のようにもできます。    
    
```    
ALTER AUTHORIZATION ON Parts.Sprockets TO MichikoOsada;    
GO    
```    
    
 オブジェクトのスキーマは、ステートメントの一部として含めるがない場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)]はユーザーの既定のスキーマ内のオブジェクトを検索します。 例:    
    
```    
ALTER AUTHORIZATION ON Sprockets TO MichikoOsada;    
ALTER AUTHORIZATION ON OBJECT::Sprockets TO MichikoOsada;    
```    
    
### <a name="b-transfer-ownership-of-a-view-to-the-schema-owner"></a>B. ビューの所有権をスキーマの所有者に譲渡する    
 次の例は、ビュー所有権を譲渡`ProductionView06`それを含むスキーマの所有者にします。 ビューがスキーマ内にある`Production`です。    
    
```    
ALTER AUTHORIZATION ON OBJECT::Production.ProductionView06 TO SCHEMA OWNER;    
GO    
```    
    
### <a name="c-transfer-ownership-of-a-schema-to-a-user"></a>C. スキーマの所有権をユーザーに譲渡する    
 次の例は、スキーマの所有権を譲渡`SeattleProduction11`ユーザーに`SandraAlayo`です。    
    
```    
ALTER AUTHORIZATION ON SCHEMA::SeattleProduction11 TO SandraAlayo;    
GO    
```    
    
### <a name="d-transfer-ownership-of-an-endpoint-to-a-sql-server-login"></a>D. エンドポイントの所有権を SQL Server ログインに譲渡する    
 次の例は、エンドポイントの所有権を譲渡`CantabSalesServer1`に`JaePak`です。 エンドポイントはサーバー レベルのセキュリティ保護可能なリソースであるため、エンドポイントを譲渡できるのはサーバー レベルのプリンシパルだけです。    
    
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]    
    
```    
ALTER AUTHORIZATION ON ENDPOINT::CantabSalesServer1 TO JaePak;    
GO    
```    
    
### <a name="e-changing-the-owner-of-a-table"></a>E. テーブルの所有者を変更します。    
 所有者を変更、次の例の各、`Sprockets`テーブルに、`Parts`データベース ユーザーにデータベース`MichikoOsada`です。    
```    
ALTER AUTHORIZATION ON Sprockets TO MichikoOsada;    
ALTER AUTHORIZATION ON dbo.Sprockets TO MichikoOsada;    
ALTER AUTHORIZATION ON OBJECT::Sprockets TO MichikoOsada;    
ALTER AUTHORIZATION ON OBJECT::dbo.Sprockets TO MichikoOsada;    
```    
    
### <a name="f-changing-the-owner-of-a-database"></a>F. データベースの所有者を変更します。    
 **適用対象**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]です。    
    
 次の例の所有者を変更する、`Parts`ログインにデータベース`MichikoOsada`です。    
    
```    
ALTER AUTHORIZATION ON DATABASE::Parts TO MichikoOsada;    
```    
  
### <a name="g-changing-the-owner-of-a-sql-database-to-an-azure-ad-user"></a>G. Azure AD のユーザーに SQL データベースの所有者を変更します。  
次の例では、SQL Server 用 Azure Active Directory 管理者という active directory と組織で`cqclinic.onmicrosoft.com`、データベースの現在の所有権を変更できる`targetDB`して、AAD ユーザー`richel@cqclinic.onmicorsoft.com`新しいデータベース次のコマンドを使用する所有者:  
    
```    
ALTER AUTHORIZATION ON database::targetDB TO [rachel@cqclinic.onmicrosoft.com];   
```    
    
 Azure AD ユーザーのユーザー名を囲む角かっこを使用する必要がありますに注意してください。  
  
    
## <a name="see-also"></a>参照    
 [OBJECTPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/objectproperty-transact-sql.md)     
 [TYPEPROPERTY &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/typeproperty-transact-sql.md)     
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)    
 
