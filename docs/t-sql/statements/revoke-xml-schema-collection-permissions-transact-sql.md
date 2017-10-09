---
title: "XML スキーマ コレクション権限 (TRANSACT-SQL) を取り消す |Microsoft ドキュメント"
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
- REVOKE statement, XML schema collections
- XML schema collections [SQL Server], permissions
- schema collections [SQL Server], permissions
ms.assetid: 8ca0973c-30b2-4633-a165-c09b13cc81ae
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a4d7d530e89bdd3dcb320c4a08c340071b7faba3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="revoke-xml-schema-collection-permissions-transact-sql"></a>REVOKE (XML スキーマ コレクションの権限の取り消し) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  XML スキーマ コレクションに対して許可または拒否された権限を取り消します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
REVOKE [ GRANT OPTION FOR ] permission [ ,...n ] ON   
    XML SCHEMA COLLECTION :: [ schema_name . ]  
    XML_schema_collection_name  
    { TO | FROM } <database_principal> [ ,...n ]  
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
 XML スキーマ コレクションで取り消すことができる権限を指定します。 権限の一覧については、後の「解説」を参照してください。  
  
 XML スキーマ コレクションの ON:: [ *schema_name***です。** *XML_schema_collection_name*  
 権限を取り消す XML スキーマ コレクションを指定します。 スコープ修飾子 (::) が必要です。 場合*schema_name*が指定されていない、既定のスキーマが使用されます。 場合*schema_name*を指定すると、スキーマ スコープ修飾子 (.) が必要です。  
  
 GRANT OPTION  
 指定した権限を他のプリンシパルに許可するための権利が、取り消されます。 その権限自体は失効しません。  
  
> [!IMPORTANT]  
>  指定した権限が GRANT オプションなしでプリンシパルに許可されている場合は、その権限自体が取り消されます。  
  
 CASCADE  
 このプリンシパルによって権限が許可または拒否されている他のプリンシパルからも、同じ権限が取り消されることを示します。  
  
> [!CAUTION]  
>  WITH GRANT OPTION で許可されている権限を CASCADE で取り消すと、その権限の GRANT および DENY の両方が取り消されます。  
  
 {に |FROM} \< *database_principal*>  
 権限を取り消すプリンシパルを指定します。  
  
 AS \<database_principal > このクエリを実行するプリンシパルの権限を取り消す権利の派生元のプリンシパルを指定します。  
  
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
  
 GRANT OPTION で権限が許可されたプリンシパルから権限を取り消すときに CASCADE を指定しない場合、ステートメントは失敗します。  
  
 XML スキーマ コレクションは、スキーマ レベルのセキュリティ保護可能なリソースで、権限の階層で親となっているスキーマに含まれています。 次の表に、XML スキーマ コレクションで取り消すことができる権限のうち最も限定的なものを、それらを暗黙的に含む一般的な権限と共に示します。  
  
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
 次の例では失効`EXECUTE`XML スキーマ コレクションに対する権限`Invoices4`ユーザーから`Wanida`です。 XML スキーマ コレクション`Invoices4`内にある、`Sales`のスキーマ、`AdventureWorks2012`データベース。  
  
 ```
 USE AdventureWorks2012;  
 REVOKE EXECUTE ON XML SCHEMA COLLECTION::Sales.Invoices4 FROM Wanida;  
 GO
 ```  
  
## <a name="see-also"></a>参照  
 [XML スキーマ コレクションの権限 &#40; を許可します。TRANSACT-SQL と #41 です。](../../t-sql/statements/grant-xml-schema-collection-permissions-transact-sql.md)   
 [XML スキーマ コレクションの権限 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-xml-schema-collection-permissions-transact-sql.md)   
 [sys.xml_schema_collections & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-xml-schema-collections-transact-sql.md)   
 [XML スキーマ コレクション &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-xml-schema-collection-transact-sql.md)   
 [アクセス許可 &#40;データベース エンジン&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  


