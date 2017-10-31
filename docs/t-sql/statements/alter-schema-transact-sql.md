---
title: "ALTER スキーマ (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/01/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER SCHEMA
- ALTER_SCHEMA_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- objects [SQL Server], transferring
- transferring objects between schemas
- ALTER SCHEMA statement
- schemas [SQL Server], modifying
- modifying schemas
ms.assetid: 0a760138-460e-410a-a3c1-d60af03bf2ed
caps.latest.revision: 43
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ad157c7d4d7b92bc199c4a490d4387acc0af0908
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="alter-schema-transact-sql"></a>ALTER SCHEMA (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  スキーマ間でセキュリティ保護可能なリソースを移動します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
ALTER SCHEMA schema_name   
   TRANSFER [ <entity_type> :: ] securable_name   
[;]  
  
<entity_type> ::=  
    {  
    Object | Type | XML Schema Collection  
    }  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
ALTER SCHEMA schema_name   
   TRANSFER [ OBJECT :: ] securable_name   
[;]  
```  
  
## <a name="arguments"></a>引数  
 *schema_name*  
 現在のデータベース内にあるスキーマの名前を指定します。セキュリティ保護可能なリソースの移動先です。 SYS または INFORMATION_SCHEMA は指定できません。  
  
 \<entity_type >  
 所有者を変更するエンティティのクラスを指定します。 既定値はオブジェクトです。  
  
 *securable_name*  
 移動元のスキーマに含まれているセキュリティ保護可能なリソースの名前を指定します。このリソースが対象のスキーマに移動されます。名前を指定するときは、1 つまたは 2 つの要素で構成される名前を使用します。  
  
## <a name="remarks"></a>解説  
 ユーザーとスキーマは完全に分離されています。  
  
 ALTER SCHEMA は、セキュリティ保護可能なリソースを同じデータベース内のスキーマ間で移動する場合にのみ使用できます。 スキーマ内のセキュリティ保護可能なリソースを変更または削除するには、そのリソースに対応した ALTER または DROP ステートメントを使用します。  
  
 1 つの要素名が使用される場合*securable_name*、名前解決ルールに、現在有効に使用される、可能なリソースを検索します。  
  
 セキュリティ保護可能なリソースに関連付けられているすべての権限は、リソースが新しいスキーマに移動したときに削除されます。 セキュリティ保護可能なリソースの所有者が明示的に設定されている場合、所有者は変更されません。 セキュリティ保護可能なリソースの所有者が SCHEMA OWNER に設定されている場合、所有者は SCHEMA OWNER のままですが、移動後、SCHEMA OWNER は新しいスキーマの所有者に解決されます。 新しい所有者の principal_id は NULL になります。  
  
 使用して、テーブルまたはビューのスキーマを変更する[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]をオブジェクト エクスプ ローラーで、テーブルまたはビューを右クリックし、をクリックして**デザイン**です。 キーを押して**F4**プロパティ ウィンドウを開きます。 **スキーマ**ボックスで、新しいスキーマを選択します。  
  
> [!CAUTION]  
>  [!INCLUDE[ssCautionUserSchema](../../includes/sscautionuserschema-md.md)]  
  
## <a name="permissions"></a>Permissions  
 他のスキーマからセキュリティ保護可能なリソースを移動する場合、現在のユーザーには、(スキーマではなく) セキュリティ保護可能なリソースに対する CONTROL 権限と対象スキーマに対する ALTER 権限が必要です。  
  
 セキュリティ保護可能なリソースに EXECUTE AS OWNER の指定があり、所有者が SCHEMA OWNER に設定されている場合は、対象スキーマの所有者に対する IMPERSONATION 権限も必要です。  
  
 移動するセキュリティ保護可能なリソースに関連付けられているすべての権限は、移動時に削除されます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-transferring-ownership-of-a-table"></a>A. テーブルの所有権を譲渡する  
 次の例は、スキーマを変更`HumanResources`テーブルを転送することによって`Address`スキーマから`Person`スキーマにします。  
  
```  
USE AdventureWorks2012;  
GO  
ALTER SCHEMA HumanResources TRANSFER Person.Address;  
GO  
```  
  
### <a name="b-transferring-ownership-of-a-type"></a>B. 型の所有権を譲渡する  
 次の例では、`Production` スキーマに型を作成し、その型を `Person` スキーマに譲渡します。  
  
```  
USE AdventureWorks2012;  
GO  
  
CREATE TYPE Production.TestType FROM [varchar](10) NOT NULL ;  
GO  
  
-- Check the type owner.  
SELECT sys.types.name, sys.types.schema_id, sys.schemas.name  
    FROM sys.types JOIN sys.schemas   
        ON sys.types.schema_id = sys.schemas.schema_id   
    WHERE sys.types.name = 'TestType' ;  
GO  
  
-- Change the type to the Person schema.  
ALTER SCHEMA Person TRANSFER type::Production.TestType ;  
GO  
  
-- Check the type owner.  
SELECT sys.types.name, sys.types.schema_id, sys.schemas.name  
    FROM sys.types JOIN sys.schemas   
        ON sys.types.schema_id = sys.schemas.schema_id   
    WHERE sys.types.name = 'TestType' ;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-transferring-ownership-of-a-table"></a>C. テーブルの所有権を譲渡する  
 次の例は、テーブルを作成`Region`で、`dbo`スキーマを作成、`Sales`スキーマ、および、移動、`Region`からテーブル、`dbo`スキーマを`Sales`スキーマです。  
  
```  
CREATE TABLE dbo.Region   
    (Region_id int NOT NULL,  
    Region_Name char(5) NOT NULL)  
WITH (DISTRIBUTION = REPLICATE);  
GO  
  
CREATE SCHEMA Sales;  
GO  
  
ALTER SCHEMA Sales TRANSFER OBJECT::dbo.Region;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [スキーマ &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-schema-transact-sql.md)   
 [DROP SCHEMA &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-schema-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  


