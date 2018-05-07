---
title: sys.fn_my_permissions (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.fn_my_permissions_TSQL
- fn_my_permissions_TSQL
- sys.fn_my_permissions
- fn_my_permissions
dev_langs:
- TSQL
helpviewer_keywords:
- fn_my_permissions function
- sys.fn_my_permissions function
ms.assetid: 30f97f00-03d8-443a-9de9-9ec420b7699b
caps.latest.revision: 21
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: b837943f16a7c8882b4e35aef3f769a3d731cd38
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sysfnmypermissions-transact-sql"></a>sys.fn_my_permissions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  セキュリティ保護可能なリソースについて、プリンシパルに許可されている有効な権限の一覧を返します。 関連する関数は[HAS_PERMS_BY_NAME](../../t-sql/functions/has-perms-by-name-transact-sql.md)です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
fn_my_permissions ( securable , 'securable_class' )  
```  
  
## <a name="arguments"></a>引数  
 *securable*  
 セキュリティ保護可能なリソースの名前を指定します。 セキュリティ保護可能なリソースがサーバーまたはデータベースの場合、この値は NULL に設定する必要があります。 *securable* には **sysname** 型のスカラー式を指定します。 *セキュリティ保護可能な*マルチパート名を指定できます。  
  
 '*securable_class*'  
 権限を一覧表示する、セキュリティ保護可能なリソースのクラスの名前を指定します。 *securable_class*は、 **sysname**です。 *securable_class*次のいずれかを指定する必要がありますアプリケーション ロール、アセンブリ、非対称キー、証明書、コントラクト、データベース、ENDPOINT、FULLTEXT CATALOG、ログイン、メッセージの種類、オブジェクト、REMOTE SERVICE BINDING、ロール、ルート、スキーマ、サーバー、サービス。、対称キー、型、ユーザー、XML スキーマ コレクションです。  
  
## <a name="columns-returned"></a>返される列  
 次の表に、列を**fn_my_permissions**を返します。 返される各行によって、セキュリティ保護可能なリソースについて、現在のセキュリティ コンテキストで保持されている権限の詳細が示されます。 クエリが失敗した場合は、NULL を返します。  
  
|列名|型|Description|  
|-----------------|----------|-----------------|  
|entity_name へのアイテムの追加|**sysname**|表示される有効な権限の対象となる、セキュリティ保護可能なリソースの名前。|  
|subentity_name|**sysname**|セキュリティ保護可能なリソースに列がある場合は列名、それ以外の場合は NULL。|  
|permission_name|**nvarchar**|アクセス許可の名前です。|  
  
## <a name="remarks"></a>解説  
 このテーブル値関数では、指定したセキュリティ保護可能なリソースについて、呼び出し元のプリンシパルが保持している有効な権限の一覧が返されます。 有効な権限とは、次のような権限です。  
  
-   プリンシパルに直接許可されており、拒否されていない権限。  
  
-   プリンシパルが保持する上位レベルの権限に暗黙的に含まれており、拒否されていない権限。  
  
-   プリンシパルがメンバーとなっているロールまたはグループに許可されており、拒否されていない権限。  
  
-   プリンシパルがメンバーとなっているロールまたはグループが保持しており、拒否されていない権限。  
  
 権限の評価は、常に呼び出し元のセキュリティ コンテキストで実行されます。 プリンシパルに有効な権限があるかどうかを評価するには、呼び出し元に、そのプリンシパルに対する IMPERSONATE 権限が必要です。  
  
 スキーマ レベルのエンティティの場合、1 部、2 部、または 3 部構成の、NULL でない名前を使用できます。 データベース レベルのエンティティの 1 部構成の名前が受け入れられたら、null 値の意味を持つ"*現在のデータベース*"です。 リソースがサーバー自体の場合は、"現在のサーバー" を表す NULL 値を使用する必要があります。 **fn_my_permissions**リンク サーバー上のアクセス許可を確認することはできません。  
  
 次のクエリでは、セキュリティ保護可能な組み込みクラスの一覧が返されます。  
  
```  
SELECT DISTINCT class_desc FROM fn_builtin_permissions(default)  
    ORDER BY class_desc;  
GO  
```  
  
 既定値は、の値として提供されている場合*セキュリティ保護可能な*または*securable_class*値は NULL として解釈されます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-listing-effective-permissions-on-the-server"></a>A. サーバーの有効な権限を一覧表示する  
 次の例では、サーバーについて、呼び出し元が保持している有効な権限の一覧を返します。  
  
```  
SELECT * FROM fn_my_permissions(NULL, 'SERVER');  
GO  
```  
  
### <a name="b-listing-effective-permissions-on-the-database"></a>B. データベースの有効な権限を一覧表示する  
 次の例では、呼び出し元の有効なアクセス許可の一覧を返します上、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベース。  
  
```  
USE AdventureWorks2012;  
SELECT * FROM fn_my_permissions (NULL, 'DATABASE');  
GO  
```  
  
### <a name="c-listing-effective-permissions-on-a-view"></a>C. ビューの有効な権限を一覧表示する  
 次の例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースの `vIndividualCustomer` スキーマにある `Sales` ビューについて、呼び出し元が保持している有効な権限の一覧を返します。  
  
```  
USE AdventureWorks2012;  
SELECT * FROM fn_my_permissions('Sales.vIndividualCustomer', 'OBJECT')   
    ORDER BY subentity_name, permission_name ;   
GO   
```  
  
### <a name="d-listing-effective-permissions-of-another-user"></a>D. 別のユーザーの有効な権限を一覧表示する  
 次の例は、データベース ユーザーの有効なアクセス許可の一覧を返します`Wanida`上、`Employee`テーブルに、`HumanResources`のスキーマ、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベース。 呼び出し元には、ユーザーに対する IMPERSONATE 権限が必要です`Wanida`です。  
  
```  
EXECUTE AS USER = 'Wanida';  
SELECT * FROM fn_my_permissions('HumanResources.Employee', 'OBJECT')   
    ORDER BY subentity_name, permission_name ;    
REVERT;  
GO  
```  
  
### <a name="e-listing-effective-permissions-on-a-certificate"></a>E. 証明書の有効な権限を一覧表示する  
 次の例では、呼び出し元の有効なアクセス許可の一覧を返しますという証明書で`Shipping47`現在のデータベースでします。  
  
```  
SELECT * FROM fn_my_permissions('Shipping47', 'CERTIFICATE');  
GO  
```  
  
### <a name="f-listing-effective-permissions-on-an-xml-schema-collection"></a>F. XML スキーマ コレクションの有効な権限を一覧表示する  
 次の例では、呼び出し元の有効なアクセス許可の一覧を返しますという名前の XML スキーマ コレクションに対して`ProductDescriptionSchemaCollection`で、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベース。  
  
```  
USE AdventureWorks2012;  
SELECT * FROM fn_my_permissions('ProductDescriptionSchemaCollection',  
    'XML SCHEMA COLLECTION');  
GO  
```  
  
### <a name="g-listing-effective-permissions-on-a-database-user"></a>G. データベース ユーザーの有効な権限を一覧表示する  
 次の例では、呼び出し元の有効なアクセス許可の一覧を返しますという名前のユーザーに`MalikAr`現在のデータベースでします。  
  
```  
SELECT * FROM fn_my_permissions('MalikAr', 'USER');  
GO  
```  
  
### <a name="h-listing-effective-permissions-of-another-login"></a>H. 別のログインの有効な権限を一覧表示する  
 次の例は、有効な権限の一覧を返します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログイン`WanidaBenshoof`上、`Employee`テーブルに、`HumanResources`のスキーマ、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベース。 呼び出し元の IMPERSONATE 権限を必要と[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログイン`WanidaBenshoof`です。  
  
```  
EXECUTE AS LOGIN = 'WanidaBenshoof';  
SELECT * FROM fn_my_permissions('AdventureWorks2012.HumanResources.Employee', 'OBJECT')   
    ORDER BY subentity_name, permission_name ;    
REVERT;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティ関数 &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)   
 [アクセス許可 &#40;データベース エンジン&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Securables](../../relational-databases/security/securables.md)   
 [権限の階層 &#40;データベース エンジン&#41;](../../relational-databases/security/permissions-hierarchy-database-engine.md)   
 [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)   
 [セキュリティ カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [EXECUTE AS &#40;Transact-SQL&#41;](../../t-sql/statements/execute-as-transact-sql.md)  
  
  
