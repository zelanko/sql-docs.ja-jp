---
title: "型の権限 (TRANSACT-SQL) の拒否 |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/09/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- DENY statement, types
- permissions [SQL Server], types
- type permissions [SQL Server]
- denying permissions [SQL Server], types
ms.assetid: 564e3500-c567-43dc-993b-9ab50e99cf3f
caps.latest.revision: "28"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 369d9bbce84881936d8c77f52807121cbb763b18
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="deny-type-permissions-transact-sql"></a>DENY (型の権限の拒否) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で型に対する権限を拒否します。  

 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
DENY permission  [ ,...n ] ON TYPE :: [ schema_name . ] type_name  
        TO <database_principal> [ ,...n ]  
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
 型で拒否できる権限を指定します。 権限の一覧については、後の「解説」を参照してください。  
  
 型に**::** [ *schema_name***です。** *type_name*  
 権限を拒否する型を指定します。 スコープ修飾子 (**::**) が必要です。 場合*schema_name*が指定されていない、既定のスキーマを使用します。 場合*schema_name*が指定されているスキーマのスコープ修飾子 (**.**) が必要です。  
  
 \<Database_principal >  
 アクセス許可を拒否するプリンシパルを指定します。  
  
 CASCADE  
 このプリンシパルによって権限が許可されている他のプリンシパルに対しても、同じ権限を拒否することを示します。  
  
 AS \<database_principal >  
 このクエリを実行するプリンシパルが権限を拒否する権利の派生元のプリンシパルを指定します。  
  
 *Database_user*  
 データベース ユーザーを指定します。  
  
 *Database_role*  
 データベース ロールを指定します。  
  
 *Application_role*  
   
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
 型は、スキーマ レベルのセキュリティ保護可能なリソースで、権限の階層で親となっているスキーマに含まれています。  
  
> [!IMPORTANT]  
>  **GRANT**、 **DENY、**と**取り消す**システム型にアクセス許可は適用されません。 ユーザー定義型には権限を許可できます。 ユーザー定義型の詳細については、次を参照してください。 [SQL Server のユーザー定義型の使用](../../relational-databases/clr-integration-database-objects-user-defined-types/working-with-user-defined-types-in-sql-server.md)です。  
  
 次の表に、型で拒否できる権限のうち最も限定的なものを、それらを暗黙的に含む一般的な権限と共に示します。  
  
|型権限|権限が含まれる型権限|権限が含まれるスキーマ権限|  
|---------------------|--------------------------------|----------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|CREATE ステートメントを実行する前に、|CONTROL|CREATE ステートメントを実行する前に、|  
|REFERENCES|CONTROL|REFERENCES|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 型に対する CONTROL 権限が必要です。 AS 句を使用する場合、指定されるプリンシパルは、権限が拒否される型を所有している必要があります。  
  
## <a name="examples"></a>使用例  
 次の例では、`VIEW DEFINITION` に対し、ユーザー定義型 `CASCADE` の `PhoneNumber` 権限を、`KhalidR` を指定して拒否します。 `PhoneNumber`スキーマ内にある`Telemarketing`です。  
  
```  
DENY VIEW DEFINITION ON TYPE::Telemarketing.PhoneNumber   
    TO KhalidR CASCADE;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [アクセス許可の付与の種類 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/grant-type-permissions-transact-sql.md)   
 [型の権限 &#40; を取り消すTRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-type-permissions-transact-sql.md)   
 [CREATE TYPE &#40;Transact-SQL&#41;](../../t-sql/statements/create-type-transact-sql.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [アクセス許可 &#40;データベース エンジン&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [セキュリティ保護可能](../../relational-databases/security/securables.md)  
  
  
