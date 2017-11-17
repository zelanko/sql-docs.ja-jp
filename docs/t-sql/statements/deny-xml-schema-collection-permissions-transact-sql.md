---
title: "XML スキーマ コレクション権限 (TRANSACT-SQL) の拒否 |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/09/2017
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
applies_to:
- Azure SQL Database
- SQL Server (starting with 2008)
dev_langs:
- TSQL
helpviewer_keywords:
- denying permissions [SQL Server], XML schema collections
- XML schema collections [SQL Server], permissions
- DENY statement, XML schema collections
- schema collections [SQL Server], permissions
ms.assetid: 159969a7-8313-41bc-bb19-c55af76597e6
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d50f055c6dbc419c8a979160f45a884f46f795d6
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="deny-xml-schema-collection-permissions-transact-sql"></a>DENY (XML スキーマ コレクションの権限の拒否) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  XML スキーマ コレクションに対する権限を拒否します。  
  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
DENY permission  [ ,...n ] ON   
    XML SCHEMA COLLECTION :: [ schema_name . ]  
    XML_schema_collection_name  
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
 XML スキーマ コレクションで拒否できる権限を指定します。 権限の一覧については、後の「解説」を参照してください。  
  
 XML スキーマ コレクションの ON:: [ *schema_name***です。** *XML_schema_collection_name*  
 権限を拒否する XML スキーマ コレクションを指定します。 スコープ修飾子 (::) が必要です。 場合*schema_name*が指定されていない、既定のスキーマを使用します。 場合*schema_name*を指定すると、スキーマ スコープ修飾子 (.) が必要です。  
  
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
 XML スキーマ コレクションに関する情報は、 [sys.xml_schema_collections](../../relational-databases/system-catalog-views/sys-xml-schema-collections-transact-sql.md)カタログ ビューです。  
  
 XML スキーマ コレクションは、スキーマ レベルのセキュリティ保護可能なリソースで、権限の階層で親となっているスキーマに含まれています。 次の表に、XML スキーマ コレクションで拒否できる権限のうち最も限定的なものを、それらを暗黙的に含む一般的な権限と共に示します。  
  
|XML スキーマ コレクション権限|権限が含まれる XML スキーマ コレクション権限|権限が含まれるスキーマ権限|  
|--------------------------------------|-------------------------------------------------|----------------------------------|  
|ALTER|CONTROL|ALTER|  
|CONTROL|CONTROL|CONTROL|  
|CREATE ステートメントを実行する前に、|CONTROL|CREATE ステートメントを実行する前に、|  
|REFERENCES|CONTROL|REFERENCES|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 XML スキーマ コレクションに対する CONTROL 権限が必要です。 AS オプションを使用する場合は、指定したプリンシパルが XML スキーマ コレクションを所有している必要があります。  
  
## <a name="examples"></a>使用例  
 次の例を拒否`EXECUTE`XML スキーマ コレクションに対する権限`Invoices4`をユーザーに`Wanida`です。 XML スキーマ コレクション`Invoices4`内にある、`Sales`のスキーマ、`AdventureWorks2012`データベース。  
  
```  
USE AdventureWorks2012;  
DENY EXECUTE ON XML SCHEMA COLLECTION::Sales.Invoices4 TO Wanida;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [XML スキーマ コレクションの権限 &#40; を許可します。TRANSACT-SQL と #41 です。](../../t-sql/statements/grant-xml-schema-collection-permissions-transact-sql.md)   
 [XML スキーマ コレクションの権限を REVOKE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-xml-schema-collection-permissions-transact-sql.md)   
 [sys.xml_schema_collections & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-xml-schema-collections-transact-sql.md)   
 [XML スキーマ コレクション &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-xml-schema-collection-transact-sql.md)   
 [アクセス許可 &#40;データベース エンジン&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  

