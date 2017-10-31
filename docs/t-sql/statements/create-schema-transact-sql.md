---
title: "スキーマ (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 12/01/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_SCHEMA_TSQL
- SCHEMA
- CREATE SCHEMA
- SCHEMA_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- owners [SQL Server], schemas
- table creation [SQL Server], CREATE SCHEMA statement
- permissions [SQL Server], schemas
- schemas [SQL Server], creating
- CREATE SCHEMA statement
ms.assetid: df74fc36-20da-4efa-b412-c4e191786695
caps.latest.revision: 60
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 58eaf0c325ab4884dfe1e67ae0b0889a2ca6769a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-schema-transact-sql"></a>CREATE SCHEMA (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  現在のデータベースにスキーマを作成します。 CREATE SCHEMA トランザクションでは、新しいスキーマにテーブルとビューを作成し、それらのオブジェクトに GRANT、DENY、または REVOKE 権限を設定することもできます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
CREATE SCHEMA schema_name_clause [ <schema_element> [ ...n ] ]  
  
<schema_name_clause> ::=  
    {  
    schema_name  
    | AUTHORIZATION owner_name  
    | schema_name AUTHORIZATION owner_name  
    }  
  
<schema_element> ::=   
    {   
        table_definition | view_definition | grant_statement |   
        revoke_statement | deny_statement   
    }  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
CREATE SCHEMA schema_name [ AUTHORIZATION owner_name ] [;]  
```  
  
## <a name="arguments"></a>引数  
 *schema_name*  
 データベース内でスキーマを識別する名前を指定します。  
  
 承認*owner_name*  
 スキーマを所有するデータベース レベルのプリンシパルの名前を指定します。 このプリンシパルは他のスキーマを所有できますが、現在のスキーマを既定のスキーマとして使用することはできません。  
  
 *table_definition*  
 スキーマ内のテーブルを作成する CREATE TABLE ステートメントを指定します。 このステートメントを実行するプリンシパルには、現在のデータベースに対する CREATE TABLE 権限が必要です。  
  
 *view_definition*  
 スキーマ内でビューを作成する CREATE VIEW ステートメントを指定します。 このステートメントを実行するプリンシパルには、現在のデータベースに対する CREATE VIEW 権限が必要です。  
  
 *grant_statement*  
 セキュリティ保護可能なリソース (ただし新しいスキーマを除く) に対する権限を与える GRANT ステートメントを指定します。  
  
 *revoke_statement*  
 セキュリティ保護可能なリソース (ただし新しいスキーマを除く) に対する権限を取り消す REVOKE ステートメントを指定します。  
  
 *deny_statement*  
 セキュリティ保護可能なリソース (ただし新しいスキーマを除く) に対する権限を拒否する DENY ステートメントを指定します。  
  
## <a name="remarks"></a>解説  
  
> [!NOTE]  
>  CREATE SCHEMA authorization が、名前を指定しないステートメントは、旧バージョンとの互換性のためにだけ許可されます。 ステートメントでエラーは発生しませんが、スキーマは作成されません。  
  
 CREATE SCHEMA を使用すると、スキーマとそれに含まれるテーブルおよびビューを作成できます。また、単一のステートメントで、セキュリティ保護可能なリソースに対する権限を許可 (GRANT)、取り消し (REVOKE)、または拒否 (DENY) することもできます。 このステートメントは個別のバッチとして実行する必要があります。 CREATE SCHEMA ステートメントでは、作成するスキーマ内にオブジェクトが作成されます。  
  
 CREATE SCHEMA トランザクションはアトミックです。 CREATE SCHEMA ステートメントの実行中にエラーが発生した場合、指定したセキュリティ保護可能なリソースは作成されず、権限は与えられません。  
  
 CREATE SCHEMA により作成されるセキュリティ保護可能なリソースは、他のビューを参照するビューを除き、任意の順序で一覧表示できます。 この場合、参照先のビューは参照元のビューより前に作成しておく必要があります。  
  
 したがって、オブジェクト自体の作成前に GRANT ステートメントでそのオブジェクトに対する権限を許可したり、CREATE TABLE ステートメントでビューの参照先テーブルを作成する前に CREATE VIEW ステートメントを記述することができます。 また、CREATE TABLE ステートメントでは、CREATE SCHEMA ステートメントで後から定義するテーブルに対して外部キーを宣言できます。  
  
> [!NOTE]  
>  CREATE SCHEMA ステートメント内で DENY および REVOKE を使用できます。 DENY および REVOKE 句は、CREATE SCHEMA ステートメントで指定した順序に従って実行されます。  
  
 CREATE SCHEMA を実行するプリンシパルは、作成するスキーマの所有者として別のデータベース プリンシパルを指定できます。 これには、後の「権限」で示す追加の権限が必要になります。  
  
 新しいスキーマは、データベース ユーザー、データベース ロール、またはアプリケーション ロールのいずれかのデータベース レベルのプリンシパルが所有します。 スキーマ内に作成されるオブジェクトはスキーマの所有者が所有し、 **sys.objects** 内の **principal_id**は NULL になります。 スキーマが含まれるオブジェクトの所有権は、データベース レベルのプリンシパルに譲渡できますが、スキーマ内のオブジェクトに対する CONTROL 権限は常にスキーマ所有者が保持します。  
  
> [!CAUTION]  
>  [!INCLUDE[ssCautionUserSchema](../../includes/sscautionuserschema-md.md)]  
  
 **スキーマおよび暗黙的なユーザーの作成**  
  
 データベース ユーザー アカウント (データベース内のデータベース プリンシパル) がなくても、ユーザーがデータベースを使用できる場合があります。 このことは、次の状況で発生します。  
  
-   ログインが**CONTROL SERVER**特権です。  
  
-   Windows ユーザーに個別のデータベース ユーザー アカウント (データベース内のデータベース プリンシパル) はないが、データベース ユーザー アカウント (Windows グループのデータベース プリンシパル) を持つ Windows グループのメンバーとしてデータベースにアクセスする。  
  
 データベース ユーザー アカウントを持たないユーザーが既存のスキーマを指定せずにオブジェクトを作成すると、そのユーザーに対してデータベース内にデータベース プリンシパルおよび既定のスキーマが自動的に作成されます。 作成されるデータベース プリンシパルおよびスキーマは、ユーザーが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続するときに使用した名前と同じ名前を持ちます ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証ログイン名または Windows ユーザー名)。  
  
 この動作が必要なのは、ユーザーが Windows グループに基づいてオブジェクトを作成および所有できるようにするためです。 ただし、スキーマおよびユーザーが誤って作成される可能性があります。 ユーザーおよびスキーマが暗黙的に作成されないように、可能な限り、明示的にデータベース プリンシパルを作成して既定のスキーマを割り当てます。 または、データベース内にオブジェクトを作成するときに、2 部または 3 部構成のオブジェクト名を使用して既存のスキーマを明示的に指定します。  

>  [!NOTE]
>  Azure Active Directory ユーザーの暗黙的な作成はできません[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]です。 ユーザーの作成がエラー 2760 で失敗外部プロバイダーから、Azure AD ユーザーを作成すると、AAD でユーザー状態を確認する必要があります、ため:**指定したスキーマ名"\<user_name@domain>"存在しないかまたはしていません使用する権限です。** してエラー 2759:**直前のエラーにより CREATE SCHEMA に失敗しました。** これらのエラーを回避するには、Azure AD ユーザー外部プロバイダーから最初作成し、オブジェクトを作成するステートメントを再実行します。
 
  
## <a name="deprecation-notice"></a>今後のバージョンでの使用  
 スキーマ名を指定しない CREATE SCHEMA ステートメントは、現在では旧バージョンとの互換性のためにのみサポートされています。 このようなステートメントは実際には、データベース内のスキーマを作成できませんが、テーブルやビューを作成し、アクセス許可を付与する操作を行います。 スキーマが作成されないので、以前の形式の CREATE SCHEMA を実行する際、プリンシパルには CREATE SCHEMA 権限は必要ありません。 この機能は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の今後のリリースでは削除される予定です。  
  
## <a name="permissions"></a>Permissions  
 データベースに対する CREATE SCHEMA 権限が必要です。  
  
 CREATE SCHEMA ステートメント内で指定するオブジェクトを作成するには、ユーザーは、オブジェクトに対応する CREATE 権限を持っている必要があります。  
  
 別のユーザーを、作成されるスキーマの所有者として指定する場合、呼び出し元は、そのユーザーに対する IMPERSONATE 権限を持っている必要があります。 データベース ロールを所有者として指定する場合、呼び出し元は、データベース ロールのメンバーシップまたはデータベース ロールに対する ALTER 権限のいずれかを持っている必要があります。  
  
> [!NOTE]  
>  旧バージョンとの互換性のための構文では、スキーマが作成されないので、CREATE SCHEMA に対する権限はチェックされません。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-creating-a-schema-and-granting-permissions"></a>A. スキーマを作成して、権限の付与  
 次の例では、スキーマ`Sprockets`所有`Annik`テーブルを含む`NineProngs`です。 このステートメントでは、`SELECT` に対して `Mandar` を許可し、`SELECT` に対して `Prasanna` を拒否します。 なお`Sprockets`と`NineProngs`単一のステートメントで作成されます。  
  
```  
USE AdventureWorks2012;  
GO  
CREATE SCHEMA Sprockets AUTHORIZATION Annik  
    CREATE TABLE NineProngs (source int, cost int, partnumber int)  
    GRANT SELECT ON SCHEMA::Sprockets TO Mandar  
    DENY SELECT ON SCHEMA::Sprockets TO Prasanna;  
GO   
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-creating-a-schema-and-a-table-in-the-schema"></a>B. スキーマのスキーマとテーブルを作成します。  
 次の例では、スキーマ`Sales`テーブルを作成および`Sales.Region`そのスキーマでします。  
  
```  
CREATE SCHEMA Sales;  
GO;  
  
CREATE TABLE Sales.Region   
(Region_id int NOT NULL,  
Region_Name char(5) NOT NULL)  
WITH (DISTRIBUTION = REPLICATE);  
GO  
```  
  
### <a name="c-setting-the-owner-of-a-schema"></a>C. スキーマの所有者の設定  
 次の例では、スキーマ`Production`所有`Mary`です。  
  
```  
CREATE SCHEMA Production AUTHORIZATION [Contoso\Mary];  
GO  
```  
  
## <a name="see-also"></a>参照  
 [ALTER SCHEMA &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-schema-transact-sql.md)   
 [DROP SCHEMA &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-schema-transact-sql.md)   
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [DENY &#40;Transact-SQL&#41;](../../t-sql/statements/deny-transact-sql.md)   
 [REVOKE &#40;Transact-SQL&#41;](../../t-sql/statements/revoke-transact-sql.md)   
 [CREATE VIEW &#40;Transact-SQL&#41;](../../t-sql/statements/create-view-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sys.schemas & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/schemas-catalog-views-sys-schemas.md)   
 [データベース スキーマの作成](../../relational-databases/security/authentication-access/create-a-database-schema.md)  
  
  



