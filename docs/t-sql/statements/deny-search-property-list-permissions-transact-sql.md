---
title: "検索プロパティ リスト権限 (TRANSACT-SQL) の拒否 |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
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
dev_langs:
- TSQL
helpviewer_keywords:
- full-text search [SQL Server], permissions
- DENY statement, search property list permissions
- denying permissions [SQL Server], search property lists
- search property lists [SQL Server], permissions
ms.assetid: 96513cb4-a9c0-4834-97a4-ddc0777b8415
caps.latest.revision: 10
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6c7db64ebf313a13227797fba7ec222dcbdeafad
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="deny-search-property-list-permissions-transact-sql"></a>DENY (検索プロパティ リスト権限の拒否) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  検索プロパティ リストに対する権限を拒否します。  
 
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
DENY permission [ ,...n ] ON  
        SEARCH PROPERTY LIST :: search_property_list_name  
    TO database_principal [ ,...n ] [ CASCADE ]  
    [ AS denying_principal ]  
```  
  
## <a name="arguments"></a>引数  
 *アクセス許可*  
 権限の名前を指定します。 権限とセキュリティ保護可能なリソースの有効な組み合わせについては、後の「解説」を参照してください。  
  
検索プロパティ リストで**::***search_property_list_name*  
 権限を拒否する検索プロパティ リストを指定します。 スコープ修飾子 :: が必要です。  
  
*database_principal*  
 アクセス許可を拒否するプリンシパルを指定します。 プリンシパルは次のいずれかです。  
  
-   データベース ユーザー  
-   データベース ロール (database role)  
-   アプリケーション ロール (application role)  
-   Windows ログインにマップされるデータベース ユーザー  
-   Windows グループにマップされるデータベース ユーザー  
-   証明書にマップされるデータベース ユーザー  
-   非対称キーにマップされているデータベース ユーザー  
-   データベース ユーザーが、サーバー プリンシパルにマップされていません。  
  
CASCADE  
 このプリンシパルによって権限が許可されている他のプリンシパルに対しても、同じ権限を拒否することを示します。  
  
*denying_principal*  
 このクエリを実行するプリンシパルが権限を拒否する権利の派生元のプリンシパルを指定します。 プリンシパルは次のいずれかです。  
  
-   データベース ユーザー  
-   データベース ロール (database role)  
-   アプリケーション ロール (application role)  
-   Windows ログインにマップされるデータベース ユーザー  
-   Windows グループにマップされるデータベース ユーザー  
-   証明書にマップされるデータベース ユーザー  
-   非対称キーにマップされているデータベース ユーザー  
-   データベース ユーザーが、サーバー プリンシパルにマップされていません。  
  
## <a name="remarks"></a>解説  
  
## <a name="search-property-list-permissions"></a>SEARCH PROPERTY LIST 権限  
 検索プロパティ リストは、データベース レベルのセキュリティ保護可能なリソースで、権限の階層で親となっているデータベースに含まれています。 次の表に、検索プロパティ リストで拒否できる権限のうち最も限定的なものを、それらを暗黙的に含む一般的な権限と共に示します。  
  
|検索プロパティ リスト権限|権限が含まれる検索プロパティ リスト権限|権限が含まれるデータベース権限|  
|-------------------------------------|------------------------------------------------|------------------------------------|  
|ALTER|CONTROL|ALTER ANY FULLTEXT CATALOG|  
|CONTROL|CONTROL|CONTROL|  
|REFERENCES|CONTROL|REFERENCES|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 フルテキスト カタログに対する CONTROL 権限が必要です。 AS オプションを使用する場合、指定するプリンシパルはフルテキスト カタログを所有している必要があります。  
  
## <a name="see-also"></a>参照  
 [APPLICATION ROLE &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-application-role-transact-sql.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [SEARCH PROPERTY LIST &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-search-property-list-transact-sql.md)   
 [DENY &#40;Transact-SQL&#41;](../../t-sql/statements/deny-transact-sql.md)   
 [暗号化階層](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [sys.fn_my_permissions & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/sys-fn-my-permissions-transact-sql.md)   
 [許可の検索プロパティ リスト権限 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/grant-search-property-list-permissions-transact-sql.md)   
 [HAS_PERMS_BY_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/has-perms-by-name-transact-sql.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [検索プロパティ リスト権限 &#40; を取り消すTRANSACT-SQL と #41 です。](../../t-sql/statements/revoke-search-property-list-permissions-transact-sql.md)   
 [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)   
 [sys.registered_search_property_lists & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql.md)   
 [検索プロパティ リストを使用したドキュメント プロパティの検索](../../relational-databases/search/search-document-properties-with-search-property-lists.md)  
  
  

