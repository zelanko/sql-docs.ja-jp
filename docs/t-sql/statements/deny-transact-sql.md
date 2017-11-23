---
title: "DENY (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/15/2017
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
- DENY
- DENY_TSQL
dev_langs: TSQL
helpviewer_keywords:
- schema-level securables [SQL Server]
- security [SQL Server], denying access
- DENY statement
- permissions [SQL Server], denying
- server-level securables [SQL Server]
- inherited security settings [SQL Server]
- denying permissions [SQL Server], DENY statement
- principal security [SQL Server]
- database-level securables [SQL Server]
- denying permissions [SQL Server]
ms.assetid: c32d1e01-9ee9-4665-a516-fcfece58078e
caps.latest.revision: "48"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 78bf8698ac1b567abdf4ec0d340d972e2e33002f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="deny-transact-sql"></a>DENY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  プリンシパルに対する権限を拒否します。 プリンシパルが、そのグループまたはロールのメンバーシップから権限を継承しないようにします。 DENY は、オブジェクトの所有者または sysadmin 固定サーバー ロールのメンバーには当てはまりませんする点を除いて、すべての権限が優先されますを拒否します。
  **セキュリティに関する注意**固定サーバー ロール sysadmin のメンバーと、オブジェクトの所有者が権限を拒否することはできません"。
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
-- Simplified syntax for DENY  
DENY   { ALL [ PRIVILEGES ] } 
     | <permission>  [ ( column [ ,...n ] ) ] [ ,...n ]  
    [ ON [ <class> :: ] securable ] 
    TO principal [ ,...n ]   
    [ CASCADE] [ AS principal ]  
[;]

<permission> ::=  
{ see the tables below }  
  
<class> ::=  
{ see the tables below }  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
DENY   
    <permission> [ ,...n ]  
    [ ON [ <class_> :: ] securable ]   
    TO principal [ ,...n ]  
    [ CASCADE ]  
[;]  
  
<permission> ::=  
{ see the tables below }  
  
<class> ::=  
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
 このオプションでは、可能な権限がすべて拒否されるわけではありません。 ALL を指定すると、次の権限が拒否されます。  
  
-   セキュリティ保護可能なリソースがデータベースの場合、BACKUP DATABASE、BACKUP LOG、CREATE DATABASE、CREATE DEFAULT、CREATE FUNCTION、CREATE PROCEDURE、CREATE RULE、CREATE TABLE、および CREATE VIEW。  
  
-   セキュリティ保護可能なリソースがスカラー関数の場合、EXECUTE および REFERENCES。  
  
-   セキュリティ保護可能なリソースがテーブル値関数の場合、DELETE、INSERT、REFERENCES、SELECT、UPDATE。  
  
-   セキュリティ保護可能なリソースがストアド プロシージャの場合、EXECUTE。  
  
-   セキュリティ保護可能なリソースがテーブルの場合、DELETE、INSERT、REFERENCES、SELECT、UPDATE。  
  
-   セキュリティ保護可能なリソースがビューの場合、DELETE、INSERT、REFERENCES、SELECT、UPDATE。  
  
> [!NOTE]  
>  DENY ALL 構文は推奨されません。 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]代わりに特定の権限を拒否してください。  
  
 PRIVILEGES  
 ISO 準拠のために用意されています。 ALL の動作は変更されません。  
  
 *アクセス許可*  
 権限の名前を指定します。 権限とセキュリティ保護可能なリソースの有効な組み合わせについては、後のトピックを参照してください。  
  
 *列*  
 権限を拒否するテーブルの列の名前を指定します。 かっこ () で囲む必要があります。  
  
 *クラス*  
 権限を拒否するセキュリティ保護可能なリソースのクラスを指定します。 スコープ修飾子**::**が必要です。  
  
 *セキュリティ保護可能です*  
 権限を拒否するセキュリティ保護可能なリソースを指定します。  
  
 *プリンシパル*  
 プリンシパルの名前を指定します。 セキュリティ保護可能なリソースに対する権限を拒否できるプリンシパルは、そのリソースによって異なります。 有効な組み合わせについては、後のセキュリティ保護可能なリソースごとのトピックを参照してください。  
  
 CASCADE  
 指定したプリンシパル、およびこのプリンシパルによって権限が許可されている他のすべてのプリンシパルに対しても、同じ権限を拒否することを示します。 このオプションは、GRANT OPTION を使用してプリンシパルに権限が与えられている場合に必要となります。  
  
 AS*プリンシパル*  
  AS プリンシパル句を使用して、アクセス許可の denier がステートメントを実行しているユーザー以外のプリンシパルにする必要がありますと、プリンシパルが記録されているを指定します。 たとえば、ユーザー Mary は principal_id 12 とユーザー Raul はプリンシパルの 15 のことを推測します。 Mary が実行される`DENY SELECT ON OBJECT::X TO Steven WITH GRANT OPTION AS Raul;`sys.database_permissions テーブルでは、ステートメントが 13 (Mary) のユーザーが実際に実行される場合でも、deny ステートメントの grantor_prinicpal_id が 15 (Raul) をされたことを示すはようになりました。
  
このステートメントで as の使用は、別のユーザーを偽装することを意味しません。  
  
## <a name="remarks"></a>解説  
 DENY ステートメントの完全な構文は複雑です。 前の構文ダイアグラムは、構造をわかりやすくするために簡略化されています。 セキュリティ保護可能なリソースに対する権限を拒否するための完全な構文については、後のトピックを参照してください。  
  
 GRANT OPTION で権限が許可されたプリンシパルに対しては、その権限を拒否するときに CASCADE を指定しないと、DENY は失敗します。  
  
 システム ストアド プロシージャ sp_helprotect では、データベース レベルのセキュリティ保護可能なリソースに対する権限がレポートされます。  
  
> [!CAUTION]  
>  テーブル レベルの DENY ステートメントは列レベルの GRANT ステートメントよりも優先されません。 この矛盾権限の階層では、旧バージョンと互換性のために維持されています。 将来のリリースでは削除される予定です。  
  
> [!CAUTION]  
>  データベースに対する CONTROL 権限を拒否すると、そのデータベースに対する CONNECT 権限が暗黙的に拒否されます。 データベースに対する CONTROL 権限を拒否されたプリンシパルは、そのデータベースに接続できません。  
  
> [!CAUTION]  
>  CONTROL SERVER 権限を拒否すると、そのサーバーに対する CONNECT SQL 権限が暗黙的に拒否されます。 サーバーに対する CONTROL SERVER 権限を拒否されたプリンシパルは、そのサーバーに接続できません。  
  
## <a name="permissions"></a>Permissions  
 呼び出し元 (または AS オプションで指定されたプリンシパル) は、セキュリティ保護可能なリソースに対する CONTROL 権限、またはセキュリティ保護可能なリソースに対する CONTROL 権限を暗黙的に与える上位の権限を保持している必要があります。 AS オプションを使用する場合、指定されたプリンシパルは、権限が拒否されるセキュリティ保護可能なリソースを所有している必要があります。  
  
 固定サーバー ロール sysadmin のメンバーなど、CONTROL SERVER 権限が許可されているユーザーは、サーバー内のセキュリティ保護可能なリソースに対する権限を拒否できます。 Db_owner 固定データベース ロールのメンバーなど、データベースに対する CONTROL 権限の権限付与対象ユーザーがいずれかに対する権限を拒否できる、データベースのセキュリティ保護可能な。 スキーマに対する CONTROL 権限が許可されているユーザーは、スキーマ内のオブジェクトに対する権限を拒否できます。 AS 句を使用する場合、指定されるプリンシパルは、権限の拒否対象となるセキュリティ保護可能なリソースを所有している必要があります。  
  
## <a name="examples"></a>使用例  
 次の表は、セキュリティ保護可能なリソースと、その構文について説明しているトピックの一覧です。  
  
|||  
|-|-|  
|アプリケーション ロール|[データベース プリンシパルの権限 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-database-principal-permissions-transact-sql.md)|  
|アセンブリ|[アセンブリの権限 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-assembly-permissions-transact-sql.md)|  
|非対称キー|[非対称キーの権限 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-asymmetric-key-permissions-transact-sql.md)|  
|可用性グループ|[可用性グループの権限 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-availability-group-permissions-transact-sql.md)|  
|Certificate|[証明書の権限 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-certificate-permissions-transact-sql.md)|  
|コントラクト|[Service Broker の権限 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-service-broker-permissions-transact-sql.md)|  
|データベース|[データベースのアクセス許可 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-database-permissions-transact-sql.md)|  
|データベース スコープ資格情報|[データベース スコープ資格情報 (TRANSACT-SQL) を拒否します。](../../t-sql/statements/deny-database-scoped-credential-transact-sql.md)|  
|エンドポイント|[エンドポイントの権限 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-endpoint-permissions-transact-sql.md)|  
|フルテキスト カタログ|[フルテキストの権限 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-full-text-permissions-transact-sql.md)|  
|フルテキスト ストップリスト|[フルテキストの権限 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-full-text-permissions-transact-sql.md)|  
|関数|[オブジェクトのアクセス許可 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-object-permissions-transact-sql.md)|  
|Login|[サーバー プリンシパルの権限 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-server-principal-permissions-transact-sql.md)|  
|メッセージの種類|[Service Broker の権限 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-service-broker-permissions-transact-sql.md)|  
|オブジェクト|[オブジェクトのアクセス許可 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-object-permissions-transact-sql.md)|  
|キュー|[オブジェクトのアクセス許可 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-object-permissions-transact-sql.md)|  
|リモート サービス バインド|[Service Broker の権限 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-service-broker-permissions-transact-sql.md)|  
|ロール|[データベース プリンシパルの権限 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-database-principal-permissions-transact-sql.md)|  
|Route|[Service Broker の権限 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-service-broker-permissions-transact-sql.md)|  
|スキーマ|[スキーマの権限 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-schema-permissions-transact-sql.md)|  
|検索プロパティ リスト|[検索プロパティ リスト権限 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-search-property-list-permissions-transact-sql.md)|  
|[サーバー]|[サーバーのアクセス許可 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-server-permissions-transact-sql.md)|  
|サービス|[Service Broker の権限 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-service-broker-permissions-transact-sql.md)|  
|ストアド プロシージャ|[オブジェクトのアクセス許可 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-object-permissions-transact-sql.md)|  
|対称キー|[対称キーの権限 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-symmetric-key-permissions-transact-sql.md)|  
|シノニム|[オブジェクトのアクセス許可 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-object-permissions-transact-sql.md)|  
|システム オブジェクト|[システム オブジェクトの権限 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-system-object-permissions-transact-sql.md)|  
|テーブル|[オブジェクトのアクセス許可 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-object-permissions-transact-sql.md)|  
|型|[型の権限 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-type-permissions-transact-sql.md)|  
|ユーザー|[データベース プリンシパルの権限 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-database-principal-permissions-transact-sql.md)|  
|表示|[オブジェクトのアクセス許可 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-object-permissions-transact-sql.md)|  
|XML スキーマ コレクション|[XML スキーマ コレクションの権限 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-xml-schema-collection-permissions-transact-sql.md)|  
  
## <a name="see-also"></a>参照  
 [REVOKE &#40;Transact-SQL&#41;](../../t-sql/statements/revoke-transact-sql.md)   
 [sp_addlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md)   
 [sp_adduser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adduser-transact-sql.md)   
 [sp_changedbowner &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-changedbowner-transact-sql.md)   
 [sp_dropuser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropuser-transact-sql.md)   
 [sp_helprotec &#40;TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helprotect-transact-sql.md)   
 [sp_helpuser &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)  
  
  
