---
title: "アクセス許可の付与タイプ (TRANSACT-SQL) |Microsoft ドキュメント"
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
- permissions [SQL Server], types
- granting permissions [SQL Server], types
- GRANT statement, types
- type permissions [SQL Server]
ms.assetid: 14bd2fb3-1446-49c0-be87-c6a670317ed0
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1e29ede5580418d1cbcb55d5a877196c3cabab92
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="grant-type-permissions-transact-sql"></a>GRANT (型の権限の許可) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  型に対する権限を許可します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
GRANT permission  [ ,...n ] ON TYPE :: [ schema_name . ] type_name  
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
 型で許可できる権限を指定します。 権限の一覧については、後の「解説」を参照してください。  
  
 型に**::** [ *schema_name***です。** *type_name*  
 権限を許可する型を指定します。 スコープ修飾子 (**::**) が必要です。 場合*schema_name*が指定されていない、既定のスキーマが使用されます。 場合*schema_name*が指定されているスキーマのスコープ修飾子 (**.**) が必要です。  
  
 \<Database_principal > 権限を許可するプリンシパルを指定します。  
  
 WITH GRANT OPTION  
 権限が許可されたプリンシパルが、この権限を他のプリンシパルにも許可できることを示します。  
  
 AS \<database_principal > このクエリを実行するプリンシパルが権限を許可する権利の派生元のプリンシパルを指定します。  
  
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
 型は、スキーマ レベルのセキュリティ保護可能なリソースで、権限の階層で親となっているスキーマに含まれています。  
  
> [!IMPORTANT]  
>  **GRANT**、 **DENY、**と**取り消す**システム型にアクセス許可は適用されません。 ユーザー定義型には権限を許可できます。 ユーザー定義型の詳細については、次を参照してください。 [SQL Server のユーザー定義型の使用](../../relational-databases/clr-integration-database-objects-user-defined-types/working-with-user-defined-types-in-sql-server.md)です。  
  
 次の表に、型で許可できる権限のうち最も限定的なものを、それらを暗黙的に含む一般的な権限と共に示します。  
  
|型権限|権限が含まれる型権限|権限が含まれるスキーマ権限|  
|---------------------|--------------------------------|----------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|CREATE ステートメントを実行する前に、|CONTROL|CREATE ステートメントを実行する前に、|  
|REFERENCES|CONTROL|REFERENCES|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 権限の許可者 (または AS オプションで指定されたプリンシパル) は、GRANT OPTION によって与えられた権限を保持しているか、権限が暗黙的に与えられる上位の権限を保持している必要があります。  
  
 AS オプションを使用している場合は、次の追加要件が適用されます。  
  
|AS|必要な追加権限|  
|--------|------------------------------------|  
|データベース ユーザー|メンバーシップ ユーザーに対する IMPERSONATE 権限、 **db_securityadmin**固定データベース ロール、メンバーシップ、 **db_owner**固定データベース ロールのメンバーシップまたは、 **sysadmin**固定サーバー ロール。|  
|Windows ログインにマップされているデータベース ユーザー|メンバーシップ ユーザーに対する IMPERSONATE 権限、 **db_securityadmin**固定データベース ロール、メンバーシップ、 **db_owner**固定データベース ロールのメンバーシップまたは、 **sysadmin**固定サーバー ロール。|  
|Windows グループにマップされているデータベース ユーザー|メンバーシップである Windows グループのメンバーシップ、 **db_securityadmin**固定データベース ロール、メンバーシップ、 **db_owner**固定データベース ロールのメンバーシップまたは、 **sysadmin**固定サーバー ロール。|  
|証明書にマップされているデータベース ユーザー|メンバーシップ、 **db_securityadmin**固定データベース ロール、メンバーシップ、 **db_owner**固定データベース ロールのメンバーシップまたは、 **sysadmin**固定サーバー ロール。|  
|非対称キーにマップされるデータベース ユーザー|メンバーシップ、 **db_securityadmin**固定データベース ロール、メンバーシップ、 **db_owner**固定データベース ロールのメンバーシップまたは、 **sysadmin**固定サーバー ロール。|  
|任意のサーバー プリンシパルにマップされていないデータベース ユーザー|メンバーシップ ユーザーに対する IMPERSONATE 権限、 **db_securityadmin**固定データベース ロール、メンバーシップ、 **db_owner**固定データベース ロールのメンバーシップまたは、 **sysadmin**固定サーバー ロール。|  
|データベース ロール|メンバーシップ、ロールに対する ALTER 権限、 **db_securityadmin**固定データベース ロール、メンバーシップ、 **db_owner**固定データベース ロールのメンバーシップまたは、 **sysadmin**固定サーバー ロール。|  
|アプリケーション ロール|メンバーシップ、ロールに対する ALTER 権限、 **db_securityadmin**固定データベース ロール、メンバーシップ、 **db_owner**固定データベース ロールのメンバーシップまたは、 **sysadmin**固定サーバー ロール。|  
  
## <a name="examples"></a>使用例  
 次の例では、ユーザー `VIEW DEFINITION` に対し、ユーザー定義型 `GRANT OPTION` の `PhoneNumber` 権限を、`KhalidR` を指定して許可します。 `PhoneNumber`スキーマ内にある`Telemarketing`です。  
  
```  
GRANT VIEW DEFINITION ON TYPE::Telemarketing.PhoneNumber   
    TO KhalidR WITH GRANT OPTION;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [型の権限 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-type-permissions-transact-sql.md)   
 [型の権限 &#40; を取り消すTRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-type-permissions-transact-sql.md)   
 [CREATE TYPE &#40;Transact-SQL&#41;](../../t-sql/statements/create-type-transact-sql.md)   
 [アクセス許可 &#40;データベース エンジン&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Securables](../../relational-databases/security/securables.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  


