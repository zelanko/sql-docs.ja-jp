---
title: sys.dm_sql_referencing_entities (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_sql_referencing_entities
- dm_sql_referencing_entities_TSQL
- sys.dm_sql_referencing_entities_TSQL
- dm_sql_referencing_entities
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_sql_referencing_entities dynamic management function
ms.assetid: c16f8f0a-483f-4feb-842e-da90426045ae
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: b5bd5257e06b784418625616c71cfb7d3e5510a8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68090661"
---
# <a name="sysdmsqlreferencingentities-transact-sql"></a>sys.dm_sql_referencing_entities (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  別のユーザー定義エンティティを名前で参照される現在のデータベース内には、エンティティごとに 1 つの行を返します。 1 つのエンティティが呼び出されたときに、2 つのエンティティ間の依存関係が作成された、*エンティティを参照*と呼ばれる別のエンティティの永続化された SQL 式で名前が、*エンティティを参照する*します。 たとえば、ユーザー定義型 (UDT) が、参照先エンティティとして指定されてこの関数は名前の定義でその型を参照する各ユーザー定義エンティティを返します。 関数では、指定されたエンティティを参照していた他のデータベース内のエンティティは返されません。 この関数は、サーバー レベルの DDL トリガーが参照元エンティティとして返す master データベースのコンテキストで実行する必要があります。  
  
 この動的管理関数に参照先エンティティを指定すると、現在のデータベース内で、そのエンティティを参照する次の種類のエンティティをレポートできます。  
  
-   スキーマ バインドまたは非スキーマ バインド エンティティ  
  
-   データベース レベルの DDL トリガー  
  
-   サーバー レベル DDL トリガー  
  
**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])、[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
sys.dm_sql_referencing_entities (  
    ' schema_name.referenced_entity_name ' , ' <referenced_class> ' )  
  
<referenced_class> ::=  
{  
    OBJECT  
  | TYPE  
  | XML_SCHEMA_COLLECTION  
  | PARTITION_FUNCTION  
}  
```  
  
## <a name="arguments"></a>引数  
 *schema_name.referenced*_*entity_name*  
 参照先エンティティの名前です。  
  
 *schema_name*参照先のクラスが PARTITION_FUNCTION である場合を除くが必要です。  
  
 *schema_name.referenced_entity_name*は**nvarchar (517)** します。  
  
 *< Referenced_class >* :: = {オブジェクト |種類 |XML_SCHEMA_COLLECTION |PARTITION_FUNCTION}  
 参照先エンティティのクラスです。 クラスは 1 つのステートメントに 1 つだけ指定できます。  
  
 *< referenced_class >* は**nvarchar**(60)。  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|referencing_schema_name|**sysname**|参照元エンティティが属しているスキーマ。 NULL 値が許可されます。<br /><br /> データベース レベルおよびサーバー レベルの DDL トリガーの場合は NULL です。|  
|referencing_entity_name|**sysname**|参照元エンティティの名前。 NULL 値は許可されません。|  
|referencing_id|**int**|参照元エンティティの ID。 NULL 値は許可されません。|  
|referencing_class|**tinyint**|参照元エンティティのクラス。 NULL 値は許可されません。<br /><br /> 1 = オブジェクト<br /><br /> 12 = データベース レベル DDL トリガー<br /><br /> 13 = サーバー レベル DDL トリガー|  
|referencing_class_desc|**nvarchar(60)**|参照元エンティティのクラスの説明です。<br /><br /> OBJECT<br /><br /> DATABASE_DDL_TRIGGER<br /><br /> SERVER_DDL_TRIGGER|  
|is_caller_dependent|**bit**|参照先エンティティが呼び出し元のスキーマに依存するため、参照先エンティティ ID の解決は実行時に行われることを示します。<br /><br /> 1 = 参照エンティティ、エンティティを参照する可能性がありますただし、参照先エンティティ ID の解決は呼び出し元に依存であり、決定することはできません。 これは、ストアド プロシージャ、拡張ストアド プロシージャ、または EXECUTE ステートメントで呼び出されるユーザー定義関数への非スキーマ バインド参照に対してのみ発生します。<br /><br /> この値が 0 の場合、参照先エンティティは呼び出し元に依存しません。|  
  
## <a name="exceptions"></a>例外  
 次のいずれかの条件に該当した場合は、空の結果セットが返されます。  
  
-   システム オブジェクトが指定されている。  
  
-   指定されたエンティティが現在のデータベースに存在しない。  
  
-   指定されたエンティティがいずれのエンティティも参照しない。  
  
-   無効なパラメーターが渡される。  
  
 番号付きストアド プロシージャの指定したエンティティを参照する場合はエラーを返します。  
  
## <a name="remarks"></a>コメント  
 次の表に、依存関係情報が作成および管理されるエンティティの種類を示します。 ルール、既定値、一時テーブル、一時ストアド プロシージャ、またはシステム オブジェクトについては、依存関係情報は作成も管理もされません。  
  
|エンティティの種類|参照元エンティティ|参照先エンティティ|  
|-----------------|------------------------|-----------------------|  
|テーブル|可*|はい|  
|表示|はい|はい|  
|[!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャ**|はい|はい|  
|CLR ストアド プロシージャ (CLR stored procedure)|いいえ|はい|  
|[!INCLUDE[tsql](../../includes/tsql-md.md)] ユーザー定義関数|はい|はい|  
|CLR ユーザー定義関数|いいえ|はい|  
|CLR トリガー (DML および DDL)|いいえ|いいえ|  
|[!INCLUDE[tsql](../../includes/tsql-md.md)] DML トリガー|はい|いいえ|  
|[!INCLUDE[tsql](../../includes/tsql-md.md)] データベース レベルの DDL トリガー|はい|いいえ|  
|[!INCLUDE[tsql](../../includes/tsql-md.md)] サーバー レベルの DDL トリガー|はい|いいえ|  
|拡張ストアド プロシージャ|いいえ|はい|  
|キュー|いいえ|はい|  
|シノニム|いいえ|はい|  
|型 (別名および CLR ユーザー定義型)|いいえ|はい|  
|XML スキーマ コレクション|いいえ|はい|  
|パーティション関数|いいえ|はい|  
  
 \* テーブルは、参照する場合にのみ、参照元エンティティとして追跡を[!INCLUDE[tsql](../../includes/tsql-md.md)]モジュール、ユーザー定義型、または計算列、CHECK 制約、または既定の制約の定義の XML スキーマ コレクションです。  
  
 ** 1 より大きな整数値を持つ番号付きストアド プロシージャは、参照元エンティティとしても、参照先エンティティとしても追跡されません。  
  
## <a name="permissions"></a>アクセス許可  
  
### <a name="includesskatmaiincludessskatmai-mdmd---includesssql11includessssql11-mdmd"></a>[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] - [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
-   参照先オブジェクトに対する CONTROL 権限が必要です。 参照先エンティティがパーティション関数である場合、データベースに対する CONTROL 権限が必要です。  
  
-   Sys.dm_sql_referencing_entities に対する SELECT 権限が必要です。 既定では、SELECT 権限が public に与えられます。  
  
### <a name="includesssql14includessssql14-mdmd---includesscurrentincludessscurrent-mdmd"></a>[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] - [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
-   参照先オブジェクトに対する権限は必要ありません。 ユーザーに VIEW DEFINITION がある場合は、参照元エンティティの一部のみで部分的な結果が返されます。  
  
-   参照元エンティティがオブジェクトの場合、オブジェクトに対する VIEW DEFINITION が必要です。  
  
-   参照元エンティティがデータベース レベルの DDL トリガーである場合、データベースに対する VIEW DEFINITION が必要です。  
  
-   参照元エンティティがサーバー レベルの DDL トリガーの場合、サーバーの VIEW ANY DEFINITION が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-returning-the-entities-that-refer-to-a-given-entity"></a>A. 特定のエンティティを参照するエンティティを取得する  
 次の例では、現在のデータベース内で、指定したテーブルを参照するエンティティを取得します。  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT referencing_schema_name, referencing_entity_name, referencing_id, referencing_class_desc, is_caller_dependent  
FROM sys.dm_sql_referencing_entities ('Production.Product', 'OBJECT');  
GO  
```  
  
### <a name="b-returning-the-entities-that-refer-to-a-given-type"></a>B. 指定された型を参照するエンティティを取得します。  
 次の例は、別名型を参照するエンティティを返します`dbo.Flag`します。 結果セット、2 つのストアド プロシージャがこの種類を使用することがわかります。 `dbo.Flag`で複数の列の定義で型を使用しても、`HumanResources.Employee`テーブルただし、計算列、CHECK 制約、またはテーブルの既定の制約の定義で型がないため、行は返されず、 `HumanResources.Employee`。テーブル。  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT referencing_schema_name, referencing_entity_name, referencing_id, referencing_class_desc, is_caller_dependent  
FROM sys.dm_sql_referencing_entities ('dbo.Flag', 'TYPE');  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 referencing_schema_name referencing_entity_name   referencing_id referencing_class_desc is_caller_dependent  
 ----------------------- -------------------------  ------------- ---------------------- -------------------  
 HumanResources          uspUpdateEmployeeHireInfo  1803153469    OBJECT_OR_COLUMN       0  
 HumanResources          uspUpdateEmployeeLogin     1819153526    OBJECT_OR_COLUMN       0  
 (2 row(s) affected)`  
 ``` 
 
## <a name="see-also"></a>関連項目  
 [sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql.md)   
 [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)  
  
  
