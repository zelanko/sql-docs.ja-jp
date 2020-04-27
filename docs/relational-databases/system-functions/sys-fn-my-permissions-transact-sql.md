---
title: fn_my_permissions (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 0a64db42ba04e864752559bb2d2b895625f2c9f5
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "68122634"
---
# <a name="sysfn_my_permissions-transact-sql"></a>sys.fn_my_permissions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  セキュリティ保護可能なリソースに対して、プリンシパルに対して効果的に付与された権限の一覧を返します。 関連する関数が[HAS_PERMS_BY_NAME](../../t-sql/functions/has-perms-by-name-transact-sql.md)。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
fn_my_permissions ( securable , 'securable_class' )  
```  
  
## <a name="arguments"></a>引数  
 *セキュリティ保護可能なリソース (securable)*  
 セキュリティ保護可能なリソースの名前を指定します。 セキュリティ保護可能なリソースがサーバーまたはデータベースの場合、この値は NULL に設定する必要があります。 *securable* には **sysname** 型のスカラー式を指定します。 *セキュリティ保護*可能なマルチパート名を指定できます。  
  
 '*securable_class*'  
 権限を一覧表示する、セキュリティ保護可能なリソースのクラスの名前を指定します。 *securable_class*は**sysname**です。 *securable_class*は、アプリケーションロール、アセンブリ、非対称キー、証明書、コントラクト、データベース、エンドポイント、フルテキストカタログ、ログイン、メッセージの種類、オブジェクト、リモートサービスバインド、ロール、ルート、スキーマ、サーバー、サービス、対称キー、種類、ユーザー、XML スキーマコレクションのいずれかである必要があります。  
  
## <a name="columns-returned"></a>返される列  
 次の表に、 **fn_my_permissions**が返す列を示します。 返される各行によって、セキュリティ保護可能なリソースについて、現在のセキュリティ コンテキストで保持されている権限の詳細が示されます。 クエリが失敗した場合は NULL を返します。  
  
|列名|種類|説明|  
|-----------------|----------|-----------------|  
|entity_name へのアイテムの追加|**sysname**|リストされたアクセス許可が実質的に付与される、セキュリティ保護可能なリソースの名前。|  
|subentity_name|**sysname**|セキュリティ保護可能な列に列がある場合は列名、それ以外の場合は NULL です。|  
|permission_name|**nvarchar**|アクセス許可の名前。|  
  
## <a name="remarks"></a>Remarks  
 このテーブル値関数は、指定されたセキュリティ保護可能なリソースについて、呼び出し元のプリンシパルが保持している有効な権限の一覧を返します。 有効な権限は、次のいずれかになります。  
  
-   プリンシパルに直接許可されており、拒否されていない権限。  
  
-   プリンシパルが保持する上位レベルの権限に暗黙的に含まれており、拒否されていない権限。  
  
-   プリンシパルがメンバーとなっているロールまたはグループに許可されており、拒否されていない権限。  
  
-   プリンシパルがメンバーとなっているロールまたはグループが保持しており、拒否されていない権限。  
  
 権限の評価は、常に呼び出し元のセキュリティ コンテキストで実行されます。 プリンシパルに有効な権限があるかどうかを評価するには、呼び出し元に、そのプリンシパルに対する IMPERSONATE 権限が必要です。  
  
 スキーマ レベルのエンティティの場合、1 部、2 部、または 3 部構成の、NULL でない名前を使用できます。 データベースレベルのエンティティの場合は、1部構成の名前を使用できます。 null 値は "*現在のデータベース*" を意味します。 リソースがサーバー自体の場合は、"現在のサーバー" を表す NULL 値を使用する必要があります。 **fn_my_permissions**は、リンクサーバーの権限を確認できません。  
  
 次のクエリでは、セキュリティ保護可能な組み込みクラスの一覧が返されます。  
  
```  
SELECT DISTINCT class_desc FROM fn_builtin_permissions(default)  
    ORDER BY class_desc;  
GO  
```  
  
 既定値が*セキュリティ保護*可能な値または*securable_class*の値として指定されている場合、値は NULL として解釈されます。  
  
## <a name="examples"></a>例  
  
### <a name="a-listing-effective-permissions-on-the-server"></a>A. サーバーの有効な権限を一覧表示する  
 次の例では、サーバーについて、呼び出し元が保持している有効な権限の一覧を返します。  
  
```  
SELECT * FROM fn_my_permissions(NULL, 'SERVER');  
GO  
```  
  
### <a name="b-listing-effective-permissions-on-the-database"></a>B. データベースの有効な権限を一覧表示する  
 次の例では、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベースに対する呼び出し元の有効な権限の一覧を返します。  
  
```  
USE AdventureWorks2012;  
SELECT * FROM fn_my_permissions (NULL, 'DATABASE');  
GO  
```  
  
### <a name="c-listing-effective-permissions-on-a-view"></a>C. ビューに対する有効な権限を一覧表示する  
 次の例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースの `vIndividualCustomer` スキーマにある `Sales` ビューについて、呼び出し元が保持している有効な権限の一覧を返します。  
  
```  
USE AdventureWorks2012;  
SELECT * FROM fn_my_permissions('Sales.vIndividualCustomer', 'OBJECT')   
    ORDER BY subentity_name, permission_name ;   
GO   
```  
  
### <a name="d-listing-effective-permissions-of-another-user"></a>D. 別のユーザーの有効な権限を一覧表示する  
 次の例`Wanida`では、 `Employee` `HumanResources` [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベースのスキーマにあるテーブルに対するデータベースユーザーの有効な権限の一覧を返します。 呼び出し元には、ユーザー `Wanida`に対する IMPERSONATE 権限が必要です。  
  
```  
EXECUTE AS USER = 'Wanida';  
SELECT * FROM fn_my_permissions('HumanResources.Employee', 'OBJECT')   
    ORDER BY subentity_name, permission_name ;    
REVERT;  
GO  
```  
  
### <a name="e-listing-effective-permissions-on-a-certificate"></a>E. 証明書に対する有効な権限を一覧表示する  
 次の例では、現在のデータベースにあるという名前`Shipping47`の証明書に対する呼び出し元の有効な権限の一覧を返します。  
  
```  
SELECT * FROM fn_my_permissions('Shipping47', 'CERTIFICATE');  
GO  
```  
  
### <a name="f-listing-effective-permissions-on-an-xml-schema-collection"></a>F. XML スキーマコレクションに対する有効な権限を一覧表示する  
 次の例では、 `ProductDescriptionSchemaCollection` [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベース内のという名前の XML スキーマコレクションに対する呼び出し元の有効な権限の一覧を返します。  
  
```  
USE AdventureWorks2012;  
SELECT * FROM fn_my_permissions('ProductDescriptionSchemaCollection',  
    'XML SCHEMA COLLECTION');  
GO  
```  
  
### <a name="g-listing-effective-permissions-on-a-database-user"></a>G. データベース ユーザーの有効な権限を一覧表示する  
 次の例では、現在のデータベース内のという名前`MalikAr`のユーザーについて、呼び出し元の有効な権限の一覧を返します。  
  
```  
SELECT * FROM fn_my_permissions('MalikAr', 'USER');  
GO  
```  
  
### <a name="h-listing-effective-permissions-of-another-login"></a>H. 別のログインの有効な権限を一覧表示する  
 次の例では[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、 `WanidaBenshoof` `Employee` `HumanResources` [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベースのスキーマ内のテーブルに対するログインの有効な権限の一覧を返します。 呼び出し元には、ログイン[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `WanidaBenshoof`に対する IMPERSONATE 権限が必要です。  
  
```  
EXECUTE AS LOGIN = 'WanidaBenshoof';  
SELECT * FROM fn_my_permissions('AdventureWorks2012.HumanResources.Employee', 'OBJECT')   
    ORDER BY subentity_name, permission_name ;    
REVERT;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティ関数 &#40;Transact-sql&#41;](../../t-sql/functions/security-functions-transact-sql.md)   
 [アクセス許可 &#40;データベースエンジン&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Securables](../../relational-databases/security/securables.md)   
 [権限の階層 &#40;データベースエンジン&#41;](../../relational-databases/security/permissions-hierarchy-database-engine.md)   
 [fn_builtin_permissions &#40;Transact-sql&#41;](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)   
 [セキュリティカタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [EXECUTE AS &#40;Transact-SQL&#41;](../../t-sql/statements/execute-as-transact-sql.md)  
  
  
