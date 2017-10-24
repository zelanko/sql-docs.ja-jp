---
title: "GRANT オブジェクト権限 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/10/2017
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
- granting permissions [SQL Server], objects
- GRANT statement, objects
ms.assetid: c001c2e7-d092-43d4-8fa6-693b3ec4c3ea
caps.latest.revision: 40
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5a9ec92d52fde6fd180cb2b62c8fffdfb03eecc6
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="grant-object-permissions-transact-sql"></a>オブジェクト アクセス許可 (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  テーブル、ビュー、テーブル値関数、ストアド プロシージャ、拡張ストアド プロシージャ、スカラー関数、集計関数、サービス キュー、またはシノニムに対する権限を許可します。  
  

  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
GRANT <permission> [ ,...n ] ON   
    [ OBJECT :: ][ schema_name ]. object_name [ ( column [ ,...n ] ) ]  
    TO <database_principal> [ ,...n ]   
    [ WITH GRANT OPTION ]  
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
 スキーマに含まれるオブジェクトで許可できる権限を指定します。 権限の一覧については、後の「解説」を参照してください。  
  
 ALL  
 ALL を指定しても、可能な権限がすべて許可されるわけではありません。 ALL を all に相当[!INCLUDE[vcpransi](../../includes/vcpransi-md.md)]指定したオブジェクトに適用できる-92 権限を許可します。 ALL の意味は、状況に応じて次のようになります。  
  
- スカラー関数の権限の場合は、EXECUTE、REFERENCES。  
- テーブル値関数の権限の場合は、DELETE、INSERT、REFERENCES、SELECT、UPDATE。  
- ストアド プロシージャの権限の場合は、EXECUTE。  
- テーブルの権限の場合は、DELETE、INSERT、REFERENCES、SELECT、UPDATE。  
- ビューの権限の場合は、DELETE、INSERT、REFERENCES、SELECT、UPDATE。  
  
PRIVILEGES  
 含まれる[!INCLUDE[vcpransi](../../includes/vcpransi-md.md)]-92 準拠。 ALL の動作は変更されません。  
  
*列*  
 権限を許可するテーブル、ビュー、またはテーブル値関数内の列の名前を指定します。 かっこ () は、必要があります。 列で許可できるのは、SELECT、REFERENCES、および UPDATE の各権限だけです。 *列*permissions 句内、またはセキュリティ保護可能な名前の後に指定することができます。  
  
> [!CAUTION]  
>  テーブル レベルの DENY ステートメントは列レベルの GRANT ステートメントよりも優先されません。 この動作は権限の階層内で一貫していませんが、旧バージョンとの互換性のために保持されています。  
  
 ON [オブジェクト::] [ *schema_name* ] です。 *object_name*  
 権限を許可するオブジェクトを指定します。 OBJECT 句は省略可能な場合は*schema_name*を指定します。 OBJECT 句を使用する場合は、スコープ修飾子 (::) が必要です。 場合*schema_name*が指定されていない、既定のスキーマを使用します。 場合*schema_name*を指定すると、スキーマ スコープ修飾子 (.) が必要です。  
  
 \<Database_principal >  
 権限を許可するプリンシパルを指定します。  
  
 WITH GRANT OPTION  
 権限が許可されたプリンシパルが、この権限を他のプリンシパルにも許可できることを示します。  
  
 AS \<database_principal > このクエリを実行するプリンシパルが権限を許可する権利の派生元のプリンシパルを指定します。  
  
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
  
> [!IMPORTANT]  
>  権限許可対象ユーザーは、ALTER 権限と REFERENCE 権限を組み合わせて使用することで、データを表示したり、許可されていない関数を実行できる場合があります。 たとえば、テーブルの ALTER 権限と関数の REFERENCE 権限を持つユーザーは、関数を介した計算列を作成して実行できます。 この場合、ユーザーには計算列の SELECT 権限も必要です。  
  
 オブジェクトに関する情報は、各種カタログ ビューに表示されます。 詳細については、次を参照してください。[オブジェクト カタログ ビュー & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md).  
  
 オブジェクトは、スキーマ レベルのセキュリティ保護可能なリソースで、権限の階層で親となっているスキーマに含まれています。 次の表に、オブジェクトで許可できる権限のうち最も限定的なものを、それらを暗黙的に含む一般的な権限と共に示します。  
  
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
 権限の許可者 (または AS オプションで指定されたプリンシパル) は、GRANT OPTION によって与えられた権限を保持しているか、権限が暗黙的に与えられる上位の権限を保持している必要があります。  
  
 AS オプションを使用している場合は、次の追加要件が適用されます。  
  
|AS|必要な追加権限|  
|--------|------------------------------------|  
|データベース ユーザー|ユーザーに対する IMPERSONATE 権限、db_securityadmin 固定データベース ロールのメンバーシップ、db_owner 固定データベース ロールのメンバーシップ、または sysadmin 固定サーバー ロールのメンバーシップ。|  
|Windows ログインにマップされているデータベース ユーザー|ユーザーに対する IMPERSONATE 権限、db_securityadmin 固定データベース ロールのメンバーシップ、db_owner 固定データベース ロールのメンバーシップ、または sysadmin 固定サーバー ロールのメンバーシップ。|  
|Windows グループにマップされるデータベース ユーザー|Windows グループのメンバーシップ、db_securityadmin 固定データベース ロールのメンバーシップ、db_owner 固定データベース ロールのメンバーシップ、または sysadmin 固定サーバー ロールのメンバーシップ。|  
|証明書にマップされているデータベース ユーザー|db_securityadmin 固定データベース ロールのメンバーシップ、db_owner 固定データベース ロールのメンバーシップ、または sysadmin 固定サーバー ロールのメンバーシップ。|  
|非対称キーにマップされるデータベース ユーザー|db_securityadmin 固定データベース ロールのメンバーシップ、db_owner 固定データベース ロールのメンバーシップ、または sysadmin 固定サーバー ロールのメンバーシップ。|  
|任意のサーバー プリンシパルにマップされていないデータベース ユーザー|ユーザーに対する IMPERSONATE 権限、db_securityadmin 固定データベース ロールのメンバーシップ、db_owner 固定データベース ロールのメンバーシップ、または sysadmin 固定サーバー ロールのメンバーシップ。|  
|データベース ロール|ロールに対する ALTER 権限、db_securityadmin 固定データベース ロールのメンバーシップ、db_owner 固定データベース ロールのメンバーシップ、または sysadmin 固定サーバー ロールのメンバーシップ。|  
|アプリケーション ロール|ロールに対する ALTER 権限、db_securityadmin 固定データベース ロールのメンバーシップ、db_owner 固定データベース ロールのメンバーシップ、または sysadmin 固定サーバー ロールのメンバーシップ。|  
  
## <a name="examples"></a>使用例  
  
### <a name="a-granting-select-permission-on-a-table"></a>A. テーブルの SELECT 権限を許可する  
 次の例では付与`SELECT`ユーザーの権限を`RosaQdM`テーブルで`Person.Address`で、`AdventureWorks2012`データベース。  
  
```  
GRANT SELECT ON OBJECT::Person.Address TO RosaQdM;  
GO  
```  
  
### <a name="b-granting-execute-permission-on-a-stored-procedure"></a>B. ストアド プロシージャの EXECUTE 権限を許可する  
 次の例では付与`EXECUTE`ストアド プロシージャに対する権限`HumanResources.uspUpdateEmployeeHireInfo`をアプリケーション ロールと呼ばれる`Recruiting11`です。  
  
```  
USE AdventureWorks2012;   
GRANT EXECUTE ON OBJECT::HumanResources.uspUpdateEmployeeHireInfo  
    TO Recruiting11;  
GO   
```  
  
### <a name="c-granting-references-permission-on-a-view-with-grant-option"></a>C. GRANT OPTION を指定してビューの REFERENCES 権限を許可する  
 次の例では、`REFERENCES` を指定して、ビュー `BusinessEntityID` にある列 `HumanResources.vEmployee` での `Wanida` 権限を、ユーザー `GRANT OPTION` に対して許可します。  
  
```  
GRANT REFERENCES (BusinessEntityID) ON OBJECT::HumanResources.vEmployee   
    TO Wanida WITH GRANT OPTION;  
GO  
```  
  
### <a name="d-granting-select-permission-on-a-table-without-using-the-object-phrase"></a>D. OBJECT 句を使用せずにテーブルの SELECT 権限を許可する  
 次の例では付与`SELECT`ユーザーの権限を`RosaQdM`テーブルで`Person.Address`で、`AdventureWorks2012`データベース。  
  
```  
GRANT SELECT ON Person.Address TO RosaQdM;  
GO  
```  
  
### <a name="e-granting-select-permission-on-a-table-to-a-domain-account"></a>E. テーブルの SELECT 権限をドメイン アカウントに許可する  
 次の例では付与`SELECT`ユーザーの権限を`AdventureWorks2012\RosaQdM`テーブルで`Person.Address`で、`AdventureWorks2012`データベース。  
  
```  
GRANT SELECT ON Person.Address TO [AdventureWorks2012\RosaQdM];  
GO  
```  
  
### <a name="f-granting-execute-permission-on-a-procedure-to-a-role"></a>F. プロシージャの EXECUTE 権限をロールに許可する  
 次の例は、ロールを作成し、そして付与`EXECUTE`プロシージャに対するロールの権限`uspGetBillOfMaterials`で、`AdventureWorks2012`データベース。  
  
```  
CREATE ROLE newrole ;  
GRANT EXECUTE ON dbo.uspGetBillOfMaterials TO newrole ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [DENY (オブジェクトの権限の拒否) &#40;Transact-SQL&#41;](../../t-sql/statements/deny-object-permissions-transact-sql.md)   
 [REVOKE オブジェクト権限 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-object-permissions-transact-sql.md)   
 [オブジェクト カタログ ビュー & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [アクセス許可 &#40;データベース エンジン&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Securables](../../relational-databases/security/securables.md)   
 [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)   
 [HAS_PERMS_BY_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/has-perms-by-name-transact-sql.md)   
 [sys.fn_my_permissions & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/sys-fn-my-permissions-transact-sql.md)  
  
  


