---
title: "REVOKE (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- REVOKE_TSQL
- REVOKE
dev_langs:
- TSQL
helpviewer_keywords:
- schema-level securables [SQL Server]
- REVOKE statement, Transact-SQL syntax
- removing permissions
- server-level securables [SQL Server]
- deleting permissions
- revoking permissions [SQL Server]
- REVOKE statement
- denying permissions [SQL Server], removing
- database-level securables [SQL Server]
- granting permissions [SQL Server], removing
- permissions [SQL Server], revoking
- dropping permissions
ms.assetid: 9d31d3e7-0883-45cd-bf0e-f0361bbb0956
caps.latest.revision: 41
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: aa08be63c0d792ed1e0422860b55a0c8f2abdc8b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="revoke-transact-sql"></a>REVOKE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  以前に許可または拒否した権限を取り消します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
-- Simplified syntax for REVOKE  
REVOKE [ GRANT OPTION FOR ]  
      {   
        [ ALL [ PRIVILEGES ] ]  
        |  
                permission [ ( column [ ,...n ] ) ] [ ,...n ]  
      }  
      [ ON [ class :: ] securable ]   
      { TO | FROM } principal [ ,...n ]   
      [ CASCADE] [ AS principal ]  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
REVOKE   
    <permission> [ ,...n ]  
    [ ON [ <class_type> :: ] securable ]   
    [ FROM | TO ] principal [ ,...n ]  
    [ CASCADE ]  
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
 GRANT OPTION FOR  
 指定した権限を与える許可を取り消します。 CASCADE 引数を使用する場合、この引数は必須です。  
  
> [!IMPORTANT]  
>  指定した権限が GRANT オプションなしでプリンシパルに許可されている場合は、その権限自体が取り消されます。  
  
 ALL  
**適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 このオプションでは、可能な権限がすべて取り消されるわけではありません。 ALL を指定すると、次の権限が取り消されます。  
  
-   セキュリティ保護可能なリソースがデータベースの場合、BACKUP DATABASE、BACKUP LOG、CREATE DATABASE、CREATE DEFAULT、CREATE FUNCTION、CREATE PROCEDURE、CREATE RULE、CREATE TABLE、および CREATE VIEW。  
  
-   セキュリティ保護可能なリソースがスカラー関数の場合、EXECUTE および REFERENCES。  
  
-   セキュリティ保護可能なリソースがテーブル値関数の場合、DELETE、INSERT、REFERENCES、SELECT、UPDATE。  
  
-   セキュリティ保護可能なリソースがストアド プロシージャの場合、EXECUTE。  
  
-   セキュリティ保護可能なリソースがテーブルの場合、DELETE、INSERT、REFERENCES、SELECT、UPDATE。  
  
-   セキュリティ保護可能なリソースがビューの場合、DELETE、INSERT、REFERENCES、SELECT、UPDATE。  
  
> [!NOTE]  
>  REVOKE ALL 構文は推奨されません。 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]代わりに、特定の権限を取り消します。  
  
 PRIVILEGES  
 ISO 準拠のために用意されています。 ALL の動作は変更されません。  
  
 *アクセス許可*  
 権限の名前を指定します。 セキュリティ保護可能な権限の有効な組み合わせがの各トピックで説明されている[Securable 固有の構文](#securable)このトピックで後述します。  
  
 *列*  
 権限を取り消すテーブルの列の名前を指定します。 かっこで囲む必要があります。  
  
 *クラス*  
 権限を取り消すセキュリティ保護可能なリソースのクラスを指定します。 スコープ修飾子**::**が必要です。  
  
 *セキュリティ保護可能です*  
 権限を取り消すセキュリティ保護可能なリソースを指定します。  
  
 |*プリンシパル*  
 プリンシパルの名前を指定します。 セキュリティ保護可能なリソースに対する権限を取り消すことのできるプリンシパルは、そのリソースによって異なります。 有効な組み合わせの詳細については、の各トピックを参照してください。 [Securable 固有の構文](#securable)このトピックで後述します。  
  
 CASCADE  
 取り消される権限を許可されているこのプリンシパルによって他のプリンシパルから取り消されてもことを示します。 CASCADE 引数を使用する場合は、GRANT OPTION FOR 引数も指定する必要があります。  
  
> [!CAUTION]  
>  WITH GRANT OPTION で許可されている権限を CASCADE で取り消すと、その権限の GRANT および DENY の両方が取り消されます。  
  
 AS*プリンシパル*  
 以外のプリンシパルによって付与された権限を取り消すことを示すために、AS プリンシパル句を使用します。 たとえば、ユーザー Mary は principal_id 12 とユーザー Raul はプリンシパルの 15 のことを推測します。 Mary と Raul の両方に、ユーザーという Steven 同じアクセス許可を付与します。 Sys.database_permissions テーブルでは、アクセス許可を 2 回示されますが、それぞれ異なる grantor_prinicpal_id 値。 Mary は、アクセス許可を使用して、取り消しでした、`AS RAUL`アクセス許可の Raul の許可を削除する句。
 
このステートメントで as の使用は、別のユーザーを偽装することを意味しません。  
  
## <a name="remarks"></a>解説  
 REVOKE ステートメントの完全な構文は複雑です。 前の構文ダイアグラムは、構造をわかりやすくするために簡略化されています。 特定のセキュリティ保護可能な権限の取り消しの完全な構文については、「」に示すトピック[Securable 固有の構文](#securable)このトピックで後述します。  
  
 許可された権限を取り消す場合は REVOKE ステートメントを使用します。また、GRANT ステートメントによってプリンシパルに特定の権限が許可されないようにするには DENY ステートメントを使用します。  
  
 権限を許可すると、指定したセキュリティ保護可能なリソースに対する権限の DENY または REVOKE は削除されます。 対象のセキュリティ保護可能なリソースの上位スコープで同じ権限が拒否されている場合は、その DENY ステートメントが優先されますが、 ただし、上位スコープで付与された権限を取り消すは優先されません。  
  
> [!CAUTION]  
>  テーブル レベルの DENY ステートメントは列レベルの GRANT ステートメントよりも優先されません。 この動作は権限の階層内で一貫していませんが、旧バージョンとの互換性のために保持されています。 将来のリリースでは削除される予定です。  
  
 Sp_helprotect システム ストアド プロシージャに対する権限がレポートで、データベース レベルのセキュリティ保護可能です  
  
 GRANT OPTION で権限が許可されたプリンシパルから権限を取り消すときに CASCADE を指定しない場合、REVOKE ステートメントは失敗します。  
  
## <a name="permissions"></a>Permissions  
 セキュリティ保護可能なリソースに対して CONTROL 権限があるプリンシパルは、そのリソースの権限を取り消すことができます。 オブジェクトの所有者は、所有するオブジェクトに対する権限を取り消すことができます。  
  
 sysadmin 固定サーバー ロールのメンバーなど、CONTROL SERVER 権限が許可されているユーザーは、サーバー内のセキュリティ保護可能なリソースに対する権限を取り消すことができます。 db_owner 固定データベース ロールのメンバーなど、データベースに対する CONTROL 権限が許可されているユーザーは、データベース内のセキュリティ保護可能なリソースに対する権限を取り消すことができます。 スキーマに対する CONTROL 権限が許可されているユーザーは、スキーマ内のオブジェクトに対する権限を取り消すことができます。  
  
##  <a name="securable"></a>セキュリティ保護可能な固有の構文  
 次の表は、セキュリティ保護可能なリソースと、その構文について説明しているトピックの一覧です。  
  
|セキュリティ保護可能|トピック|  
|---------------|-----------|  
|アプリケーション ロール|[データベース プリンシパルの権限 &#40; を取り消すTRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-database-principal-permissions-transact-sql.md)|  
|アセンブリ|[アセンブリの権限 &#40; を取り消すTRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-assembly-permissions-transact-sql.md)|  
|非対称キー|[非対称キーの権限を REVOKE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-asymmetric-key-permissions-transact-sql.md)|  
|可用性グループ|[REVOKE 可用性グループの権限 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-availability-group-permissions-transact-sql.md)|  
|Certificate|[証明書の権限 &#40; を取り消すTRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-certificate-permissions-transact-sql.md)|  
|コントラクト|[Service Broker の権限 &#40; を取り消すTRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-service-broker-permissions-transact-sql.md)|  
|データベース|[データベースのアクセス許可 &#40; を取り消すTRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-database-permissions-transact-sql.md)|  
|エンドポイント|[エンドポイントの権限 &#40; を取り消すTRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-endpoint-permissions-transact-sql.md)|  
|データベース スコープ資格情報|[REVOKE データベース スコープ資格情報 (TRANSACT-SQL)](../../t-sql/statements/revoke-database-scoped-credential-transact-sql.md)|  
|フルテキスト カタログ|[フルテキストの権限 &#40; を取り消すTRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-full-text-permissions-transact-sql.md)|  
|フルテキスト ストップリスト|[フルテキストの権限 &#40; を取り消すTRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-full-text-permissions-transact-sql.md)|  
|関数|[REVOKE オブジェクト権限 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-object-permissions-transact-sql.md)|  
|Login|[サーバー プリンシパルの権限 &#40; を取り消すTRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-server-principal-permissions-transact-sql.md)|  
|メッセージの種類|[Service Broker の権限 &#40; を取り消すTRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-service-broker-permissions-transact-sql.md)|  
|オブジェクト|[REVOKE オブジェクト権限 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-object-permissions-transact-sql.md)|  
|キュー|[REVOKE オブジェクト権限 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-object-permissions-transact-sql.md)|  
|リモート サービス バインド|[Service Broker の権限 &#40; を取り消すTRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-service-broker-permissions-transact-sql.md)|  
|ロール|[データベース プリンシパルの権限 &#40; を取り消すTRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-database-principal-permissions-transact-sql.md)|  
|Route|[Service Broker の権限 &#40; を取り消すTRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-service-broker-permissions-transact-sql.md)|  
|スキーマ|[スキーマの権限 &#40; を取り消すTRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-schema-permissions-transact-sql.md)|  
|検索プロパティ リスト|[検索プロパティ リスト権限 &#40; を取り消すTRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-search-property-list-permissions-transact-sql.md)|  
|[サーバー]|[サーバーのアクセス許可 &#40; を取り消すTRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-server-permissions-transact-sql.md)|  
|サービス|[Service Broker の権限 &#40; を取り消すTRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-service-broker-permissions-transact-sql.md)|  
|ストアド プロシージャ|[REVOKE オブジェクト権限 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-object-permissions-transact-sql.md)|  
|対称キー|[対称キーの権限を REVOKE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-symmetric-key-permissions-transact-sql.md)|  
|シノニム|[REVOKE オブジェクト権限 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-object-permissions-transact-sql.md)|  
|システム オブジェクト|[システム オブジェクトの権限 &#40; を取り消すTRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-system-object-permissions-transact-sql.md)|  
|テーブル|[REVOKE オブジェクト権限 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-object-permissions-transact-sql.md)|  
|型|[型の権限 &#40; を取り消すTRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-type-permissions-transact-sql.md)|  
|ユーザー|[データベース プリンシパルの権限 &#40; を取り消すTRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-database-principal-permissions-transact-sql.md)|  
|表示|[REVOKE オブジェクト権限 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-object-permissions-transact-sql.md)|  
|XML スキーマ コレクション|[XML スキーマ コレクションの権限を REVOKE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-xml-schema-collection-permissions-transact-sql.md)|  
  
## <a name="see-also"></a>参照  
 [権限の階層 &#40;データベース エンジン&#41;](../../relational-databases/security/permissions-hierarchy-database-engine.md)   
 [DENY &#40;Transact-SQL&#41;](../../t-sql/statements/deny-transact-sql.md)   
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [sp_addlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md)   
 [sp_adduser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adduser-transact-sql.md)   
 [sp_changedbowner & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-changedbowner-transact-sql.md)   
 [sp_dropuser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropuser-transact-sql.md)   
 [sp_helprotec &#40;TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helprotect-transact-sql.md)   
 [sp_helpuser & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)  
  
  

