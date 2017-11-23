---
title: "GRANT (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/12/2017
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
- GRANT_TSQL
- GRANT
dev_langs: TSQL
helpviewer_keywords:
- granting permissions [SQL Server], GRANT statement
- schema-level securables [SQL Server]
- GRANT statement
- cross-database permissions
- GRANT statement, about GRANT statement
- server-level securables [SQL Server]
- database-level securables [SQL Server]
- permissions [SQL Server], granting
ms.assetid: a760c16a-4d2d-43f2-be81-ae9315f38185
caps.latest.revision: "64"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 618e2068c1b1e9b99a68d0216c17c66e9b2cf3d1
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="grant-transact-sql"></a>GRANT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  セキュリティ保護可能なリソースに対する権限をプリンシパルに許可します。  一般的な概念は GRANT を\<権限 > ON \<、一部のオブジェクト > TO\<いくつかのユーザー、ログイン、またはグループ >。 アクセス許可の概要については、次を参照してください。[アクセス許可 &#40;データベース エンジン&#41;](../../relational-databases/security/permissions-database-engine.md)です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
-- Simplified syntax for GRANT  
GRANT { ALL [ PRIVILEGES ] }  
      | permission [ ( column [ ,...n ] ) ] [ ,...n ]  
      [ ON [ class :: ] securable ] TO principal [ ,...n ]   
      [ WITH GRANT OPTION ] [ AS principal ]  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
GRANT   
    <permission> [ ,...n ]  
    [ ON [ <class_type> :: ] securable ]   
    TO principal [ ,...n ]  
    [ WITH GRANT OPTION ]  
[;]  
  
<permission> ::=  
{ see the tables below }  
  
<class_type> ::=  
{  
      LOGIN  
    | DATABASE  
    | OBJECT  
    | ROLE  
    | SCHEMA  
    | USER  
}  
```  
  
## <a name="arguments"></a>引数  
 ALL  
 このオプションは旧バージョンとの互換性のためだけに保持されており、使用は推奨されません。 実際にはすべての権限が許可されるわけではありません。 ALL を指定すると、次の権限が許可されます。  
  
-   セキュリティ保護可能なリソースがデータベースの場合、BACKUP DATABASE、BACKUP LOG、CREATE DATABASE、CREATE DEFAULT、CREATE FUNCTION、CREATE PROCEDURE、CREATE RULE、CREATE TABLE、および CREATE VIEW。  
  
-   セキュリティ保護可能なリソースがスカラー関数の場合、EXECUTE および REFERENCES。  
  
-   セキュリティ保護可能なリソースがテーブル値関数の場合、DELETE、INSERT、REFERENCES、SELECT、UPDATE。  
  
-   セキュリティ保護可能なリソースがストアド プロシージャの場合、EXECUTE。  
  
-   セキュリティ保護可能なリソースがテーブルの場合、DELETE、INSERT、REFERENCES、SELECT、UPDATE。  
  
-   セキュリティ保護可能なリソースがビューの場合、DELETE、INSERT、REFERENCES、SELECT、UPDATE。  
  
PRIVILEGES  
 ISO 準拠のために用意されています。 ALL の動作は変更されません。  
  
*アクセス許可*  
 権限の名前を指定します。 権限とセキュリティ保護可能なリソースの有効な組み合わせについては、後のトピックを参照してください。  
  
*列*  
 権限を許可するテーブルの列の名前を指定します。 かっこ () で囲む必要があります。  
  
*クラス*  
 権限を許可するセキュリティ保護可能なリソースのクラスを指定します。 スコープ修飾子**::**が必要です。  
  
*セキュリティ保護可能です*  
 権限を許可するセキュリティ保護可能なリソースを指定します。  
  
*プリンシパル*  
 プリンシパルの名前を指定します。 セキュリティ保護可能なリソースに対する権限を許可できるプリンシパルは、そのリソースによって異なります。 有効な組み合わせについては、後のトピックを参照してください。  
  
GRANT OPTION  
 権限を許可されたプリンシパルが、この権限を他のプリンシパルにも許可できることを示します。  
  
AS*プリンシパル*  
 AS プリンシパル句を使用して、プリンシパルが権限の許可者が、ステートメントを実行しているユーザー以外のプリンシパルにする必要があります、記録されているを指定します。 たとえば、ユーザー Mary は principal_id 12 とユーザー Raul はプリンシパルの 15 のことを推測します。 Mary が実行される`GRANT SELECT ON OBJECT::X TO Steven WITH GRANT OPTION AS Raul;`sys.database_permissions テーブルは、grantor_prinicpal_id が 15 (Raul)、ステートメントが 13 (Mary) のユーザーが実際に実行される場合でもを示すようになりました。

AS 句を使用して通常しないで、アクセス許可のチェーンを明示的に定義する必要があります。 詳細については、次を参照してください。、**権限チェック アルゴリズムの概要**のセクション[権限 (データベース エンジン)](../../relational-databases/security/permissions-database-engine.md)です。

このステートメントで as の使用は、別のユーザーを偽装することを意味しません。 
  
## <a name="remarks"></a>解説  
 GRANT ステートメントの完全な構文は複雑です。 前の構文ダイアグラムは、構造をわかりやすくするために簡略化されています。 セキュリティ保護可能なリソースに対する権限を許可するための完全な構文については、後のトピックを参照してください。  
  
 許可された権限を取り消す場合は REVOKE ステートメントを使用します。また、GRANT ステートメントによってプリンシパルに特定の権限が許可されないようにするには DENY ステートメントを使用します。  
  
 権限を許可すると、指定したセキュリティ保護可能なリソースに対する権限の DENY または REVOKE は削除されます。 対象のセキュリティ保護可能なリソースの上位スコープで同じ権限が拒否されている場合は、その DENY ステートメントが優先されますが、 上位スコープで許可されている権限を取り消そうとしても、その REVOKE ステートメントは優先されません。  
  
 データベース レベルの権限は、指定されたデータベースのスコープ内で許可されます。 ユーザーが別のデータベースのオブジェクトに対する権限を必要とする場合、そのデータベースにユーザー アカウントを作成するか、または現在のデータベースへのアクセス権と同様に、そのデータベースへのアクセス権もユーザー アカウントに与えます。  
  
> [!CAUTION]  
>  テーブル レベルの DENY ステートメントは列レベルの GRANT ステートメントよりも優先されません。 この矛盾権限の階層では、旧バージョンと互換性のために維持されています。 将来のリリースでは削除される予定です。  
  
 システム ストアド プロシージャ sp_helprotect では、データベース レベルのセキュリティ保護可能なリソースに対する権限がレポートされます。  
  
## <a name="with-grant-option"></a>WITH GRANT OPTION  
 **GRANT**しています. **GRANT OPTION で**アクセス許可で、セキュリティ プリンシパルは他のセキュリティ アカウントを指定した権限を許可する権限を与えられているを指定します。 権限を与えられるプリンシパルが、ロールまたは Windows グループ、 **AS**オブジェクトの権限をさらグループまたはロールのメンバーではないユーザーに付与する必要がある場合、句を使用する必要があります。 ユーザーだけではなくグループまたはロールを実行できるため、 **GRANT**ステートメントでは、特定のグループまたはロールのメンバーを使用する必要があります、 **AS**句を許可するときに、役割またはグループのメンバーシップを明示的に呼び出すアクセス許可。 例を次にどのように**WITH GRANT OPTION**ロールまたは Windows グループに許可されるときに使用します。  
  
```  
-- Execute the following as a database owner  
GRANT EXECUTE ON TestProc TO TesterRole WITH GRANT OPTION;  
EXEC sp_addrolemember TesterRole, User1;  
-- Execute the following as User1  
-- The following fails because User1 does not have the permission as the User1  
GRANT EXECUTE ON TestMe TO User2;  
-- The following succeeds because User1 invokes the TesterRole membership  
GRANT EXECUTE ON TestMe TO User2 AS TesterRole;  
```  
  
## <a name="chart-of-sql-server-permissions"></a>SQL Server 権限の一覧表  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のすべての権限を示した pdf 形式のポスター サイズの一覧表については、 [http://go.microsoft.com/fwlink/?LinkId=229142](http://go.microsoft.com/fwlink/?LinkId=229142)を参照してください。  
  
## <a name="permissions"></a>Permissions  
 権限の許可者 (または AS オプションで指定されたプリンシパル) は、GRANT OPTION によって与えられた権限を保持しているか、権限が暗黙的に与えられる上位の権限を保持している必要があります。 AS オプションを使用する場合は、追加の要件を満たす必要があります。 詳細については、セキュリティ保護可能なリソース別のトピックを参照してください。  
  
 オブジェクトの所有者は、所有するオブジェクトの権限を許可できます。 セキュリティ保護可能なリソースに対して CONTROL 権限があるプリンシパルは、そのリソースの権限を許可できます。  
  
 sysadmin 固定サーバー ロールのメンバーなど、CONTROL SERVER 権限が許可されているユーザーは、サーバー内のセキュリティ保護可能なリソースに対する権限を許可できます。 db_owner 固定データベース ロールのメンバーなど、データベースに対する CONTROL 権限が許可されているユーザーは、データベース内のセキュリティ保護可能なリソースに対する権限を許可できます。 スキーマに対する CONTROL 権限が許可されているユーザーは、スキーマ内のオブジェクトに対する権限を許可できます。  
  
## <a name="examples"></a>使用例  
 次の表は、セキュリティ保護可能なリソースと、その構文について説明しているトピックの一覧です。  
  
|||  
|-|-|  
|アプリケーション ロール|[データベース プリンシパルの権限の GRANT &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/grant-database-principal-permissions-transact-sql.md)|  
|アセンブリ|[アセンブリの権限 &#40; を許可します。TRANSACT-SQL と #41 です。](../../t-sql/statements/grant-assembly-permissions-transact-sql.md)|  
|非対称キー|[非対称キーの権限の GRANT &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/grant-asymmetric-key-permissions-transact-sql.md)|  
|可用性グループ|[GRANT 可用性グループの権限 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/grant-availability-group-permissions-transact-sql.md)|  
|Certificate|[GRANT 証明書の権限 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/grant-certificate-permissions-transact-sql.md)|  
|コントラクト|[GRANT Service Broker の権限 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/grant-service-broker-permissions-transact-sql.md)|  
|データベース|[データベース権限の許可 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/grant-database-permissions-transact-sql.md)|
|データベース スコープ資格情報|[GRANT データベース スコープ資格情報 (TRANSACT-SQL)](../../t-sql/statements/grant-database-scoped-credential-transact-sql.md)|  
|エンドポイント|[GRANT Endpoint Permissions &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/grant-endpoint-permissions-transact-sql.md)|  
|フルテキスト カタログ|[GRANT、フルテキストの権限 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/grant-full-text-permissions-transact-sql.md)|  
|フルテキスト ストップリスト|[GRANT、フルテキストの権限 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/grant-full-text-permissions-transact-sql.md)|  
|関数|[GRANT オブジェクトのアクセス許可 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/grant-object-permissions-transact-sql.md)|  
|Login|[サーバー プリンシパルの権限の GRANT &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/grant-server-principal-permissions-transact-sql.md)|  
|メッセージの種類|[GRANT Service Broker の権限 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/grant-service-broker-permissions-transact-sql.md)|  
|オブジェクト|[GRANT オブジェクトのアクセス許可 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/grant-object-permissions-transact-sql.md)|  
|キュー|[GRANT オブジェクトのアクセス許可 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/grant-object-permissions-transact-sql.md)|  
|リモート サービス バインド|[GRANT Service Broker の権限 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/grant-service-broker-permissions-transact-sql.md)|  
|ロール|[データベース プリンシパルの権限の GRANT &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/grant-database-principal-permissions-transact-sql.md)|  
|Route|[GRANT Service Broker の権限 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/grant-service-broker-permissions-transact-sql.md)|  
|スキーマ|[スキーマの権限 &#40; を許可します。TRANSACT-SQL と #41 です。](../../t-sql/statements/grant-schema-permissions-transact-sql.md)|  
|検索プロパティ リスト|[許可の検索プロパティ リスト権限 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/grant-search-property-list-permissions-transact-sql.md)|  
|[サーバー]|[GRANT (サーバーの権限の許可) &#40;Transact-SQL&#41;](../../t-sql/statements/grant-server-permissions-transact-sql.md)|  
|サービス|[GRANT Service Broker の権限 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/grant-service-broker-permissions-transact-sql.md)|  
|ストアド プロシージャ|[GRANT オブジェクトのアクセス許可 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/grant-object-permissions-transact-sql.md)|  
|対称キー|[対称キーの権限の GRANT &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/grant-symmetric-key-permissions-transact-sql.md)|  
|シノニム|[GRANT オブジェクトのアクセス許可 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/grant-object-permissions-transact-sql.md)|  
|システム オブジェクト|[GRANT (システム オブジェクトの権限の許可) &#40;Transact-SQL&#41;](../../t-sql/statements/grant-system-object-permissions-transact-sql.md)|  
|テーブル|[GRANT オブジェクトのアクセス許可 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/grant-object-permissions-transact-sql.md)|  
|型|[アクセス許可の付与の種類 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/grant-type-permissions-transact-sql.md)|  
|ユーザー|[データベース プリンシパルの権限の GRANT &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/grant-database-principal-permissions-transact-sql.md)|  
|表示|[GRANT オブジェクトのアクセス許可 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/grant-object-permissions-transact-sql.md)|  
|XML スキーマ コレクション|[XML スキーマ コレクションの権限 &#40; を許可します。TRANSACT-SQL と #41 です。](../../t-sql/statements/grant-xml-schema-collection-permissions-transact-sql.md)|  
  
## <a name="see-also"></a>参照  
 [DENY &#40;Transact-SQL&#41;](../../t-sql/statements/deny-transact-sql.md)   
 [REVOKE &#40;Transact-SQL&#41;](../../t-sql/statements/revoke-transact-sql.md)   
 [sp_addlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md)   
 [sp_adduser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adduser-transact-sql.md)   
 [sp_changedbowner &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-changedbowner-transact-sql.md)   
 [sp_dropuser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropuser-transact-sql.md)   
 [sp_helprotec &#40;TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helprotect-transact-sql.md)   
 [sp_helpuser &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)  
  
  
