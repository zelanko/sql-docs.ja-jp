---
title: "オブジェクト アクセス許可 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
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
- DENY statement, objects
- table permissions [SQL Server]
ms.assetid: 0b8d3ddc-38c0-4241-b7bb-ee654a5081aa
caps.latest.revision: 26
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2655a796d6d097cb635576313664ea6bfa7162db
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="deny-object-permissions-transact-sql"></a>DENY (オブジェクトの権限の拒否) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  セキュリティ保護可能なリソースの OBJECT クラスのメンバーに対する権限を拒否します。 OBJECT クラスのメンバーは、テーブル、ビュー、テーブル値関数、ストアド プロシージャ、拡張ストアド プロシージャ、スカラー関数、集計関数、サービス キュー、およびシノニムです。  

  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
DENY <permission> [ ,...n ] ON   
    [ OBJECT :: ][ schema_name ]. object_name [ ( column [ ,...n ] ) ]  
        TO <database_principal> [ ,...n ]   
    [ CASCADE ]  
        [ AS <database_principal> ]  
  
<permission> ::=  
    ALL [ PRIVILEGES ] | permission [ ( column [ ,...n ] ) ]  
  
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
 スキーマに含まれるオブジェクトで拒否できる権限を指定します。 権限の一覧については、後の「解説」を参照してください。  
  
 ALL  
 ALL を指定しても、可能な権限がすべて拒否されるわけではありません。 ALL を指定すると、指定したオブジェクトに適用されるすべての ANSI-92 権限を拒否することになります。 ALL の意味は、状況に応じて次のようになります。  
  
 - スカラー関数の権限の場合は、EXECUTE、REFERENCES。  
 - テーブル値関数の権限の場合は、DELETE、INSERT、REFERENCES、SELECT、UPDATE。  
 - ストアド プロシージャの権限: を実行します。  
 - テーブルの権限の場合は、DELETE、INSERT、REFERENCES、SELECT、UPDATE。  
 - ビューの権限の場合は、DELETE、INSERT、REFERENCES、SELECT、UPDATE。  
  
PRIVILEGES  
 ANSI-92 準拠のために用意されています。 ALL の動作は変更されません。  
  
*列*  
 権限を拒否するテーブル、ビュー、またはテーブル値関数内の列の名前を指定します。 かっこ**に関するページ ()**が必要です。 列で拒否できるのは、SELECT、REFERENCES、および UPDATE の各権限だけです。 *列*permissions 句内、またはセキュリティ保護可能な名前の後に指定することができます。  
  
> [!CAUTION]  
>  テーブル レベルの DENY ステートメントは列レベルの GRANT ステートメントよりも優先されません。 この動作は権限の階層内で一貫していませんが、旧バージョンとの互換性のために保持されています。  
  
 ON [オブジェクト**::** ] [ *schema_name* ]**です。** *object_name*  
 アクセス許可を拒否するオブジェクトを指定します。 OBJECT 句は省略可能な場合は*schema_name*を指定します。 OBJECT 句を使用する場合、スコープ修飾子 (**::**) が必要です。 場合*schema_name*が指定されていない、既定のスキーマを使用します。 場合*schema_name*が指定されているスキーマのスコープ修飾子 (**.**) が必要です。  
  
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
 オブジェクトに関する情報は、各種カタログ ビューに表示されます。 詳細については、次を参照してください。[オブジェクト カタログ ビュー & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md).  
  
 オブジェクトは、スキーマ レベルのセキュリティ保護可能なリソースで、権限の階層で親となっているスキーマに含まれています。 次の表に、オブジェクトで拒否できる権限のうち最も限定的なものを、それらを暗黙的に含む一般的な権限と共に示します。  
  
|オブジェクト権限|権限が含まれるオブジェクト権限|権限が含まれるスキーマ権限|  
|-----------------------|----------------------------------|----------------------------------|  
|ALTER|CONTROL|ALTER|  
|CONTROL|CONTROL|CONTROL|  
|DELETE|CONTROL|DELETE|  
|CREATE ステートメントを実行する前に、|CONTROL|CREATE ステートメントを実行する前に、|  
|INSERT|CONTROL|INSERT|  
|RECEIVE|CONTROL|CONTROL|  
|REFERENCES|CONTROL|REFERENCES|  
|SELECT|RECEIVE|SELECT|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|UPDATE|CONTROL|UPDATE|  
|VIEW CHANGE TRACKING|CONTROL|VIEW CHANGE TRACKING|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 オブジェクトに対する CONTROL 権限が必要です。  
  
 AS 句を使用する場合、指定されるプリンシパルは、権限が拒否されるオブジェクトを所有している必要があります。  
  
## <a name="examples"></a>使用例  
次の例では、AdventureWorks データベースを使用します。
  
### <a name="a-denying-select-permission-on-a-table"></a>A. テーブルの SELECT 権限を拒否する  
 次の例を拒否`SELECT`、ユーザーの権限を`RosaQdM`テーブルに`Person.Address`です。  
  
```  
DENY SELECT ON OBJECT::Person.Address TO RosaQdM;  
GO  
```  
  
### <a name="b-denying-execute-permission-on-a-stored-procedure"></a>B. ストアド プロシージャの EXECUTE 権限を拒否する  
 次の例では、ストアド プロシージャ `EXECUTE` の `HumanResources.uspUpdateEmployeeHireInfo` 権限を、アプリケーション ロール `Recruiting11` に対して拒否します。  
  
```  
DENY EXECUTE ON OBJECT::HumanResources.uspUpdateEmployeeHireInfo  
    TO Recruiting11;  
GO   
```  
  
### <a name="c-denying-references-permission-on-a-view-with-cascade"></a>C. CASCADE を指定してビューの REFERENCES 権限を拒否する  
 次の例を拒否`REFERENCES`列に対する権限`BusinessEntityID`ビューで`HumanResources.vEmployee`をユーザーに`Wanida`で`CASCADE`です。  
  
```  
DENY REFERENCES (BusinessEntityID) ON OBJECT::HumanResources.vEmployee   
    TO Wanida CASCADE;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [GRANT (オブジェクトの権限の許可) &#40;Transact-SQL&#41;](../../t-sql/statements/grant-object-permissions-transact-sql.md)   
 [REVOKE オブジェクト権限 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-object-permissions-transact-sql.md)   
 [オブジェクト カタログ ビュー & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [アクセス許可 &#40;データベース エンジン&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Securables](../../relational-databases/security/securables.md)   
 [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)   
 [HAS_PERMS_BY_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/has-perms-by-name-transact-sql.md)   
 [sys.fn_my_permissions & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/sys-fn-my-permissions-transact-sql.md)  
  
  

